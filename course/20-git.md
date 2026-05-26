# 20. Git & GitHub — продвинутый практический модуль (с нуля до профи)

> Git — это не «git add . && git commit -m fix». На Middle+ от вас ждут чистую историю, осознанные rebase, разрешение конфликтов, bisect, reflog, worktree, hooks, подписанные коммиты, trunk-based / GitHub Flow и качественные code review. Этот модуль идёт параллельно с любым другим: без него остальные проекты бессмысленно коммитить.

**Длительность:** 2–3 недели
**Префикс по грейдам:** Junior закрывает недели 1–2, Middle — все 3, Senior использует модуль как референс по workflow, hooks, релизам и работе с большими репозиториями.

---

## 🎯 Чему вы научитесь

- Понимать внутреннюю модель Git: объекты, refs, индекс, HEAD.
- Уверенно работать с ветками, merge, rebase, cherry-pick — и понимать, когда что брать.
- Переписывать историю осознанно: interactive rebase, autosquash, fixup, amend.
- Восстанавливать «потерянные» коммиты через `reflog` и не бояться `reset --hard`.
- Искать сломавший тесты коммит за O(log n) через `git bisect run`.
- Держать монорепо в worktree, sparse-checkout и partial clone.
- Настраивать pre-commit hooks, conventional commits, signed commits (Verified).
- Делать релизы по semver через goreleaser + release-please/git-cliff.
- Писать production-grade GitHub Actions для Go (matrix, кэш, race, coverage, govulncheck).
- Контрибьютить в open source: fork → upstream → PR → review → merge.

---

## 🗺 Дорожная карта модуля

| Неделя | Тема | Что закрываем |
|--------|------|---------------|
| 1 | Модель Git + базовые операции | объекты, ветки, merge, rebase, конфликты |
| 2 | Переписывание истории, восстановление, bisect, worktree | reflog, reset, rebase -i, bisect, stash |
| 3 | GitHub Flow, hooks, CI/CD, релизы, open source | gh CLI, Actions, signed commits, goreleaser |

---

## 📚 Неделя 1 — модель Git и ежедневная работа

### Урок 1.1 — модель Git «изнутри»

**Теория:** working tree → index (staging) → local repo → remote. Объекты Git: `blob`, `tree`, `commit`, `tag`. SHA-1/SHA-256. Refs (`refs/heads/*`, `refs/tags/*`, `refs/remotes/*`). `HEAD` — это указатель на ветку, а ветка — указатель на коммит. Коммит — это **снимок** дерева, а не diff.

**Практика:** `git init`, сделайте 3 коммита, посмотрите содержимое `.git/objects` через `git cat-file -p <sha>`. Найдите blob своего файла, tree, commit. Нарисуйте схему «коммит → tree → blobs».

### Урок 1.2 — `status`, `add`, `commit`, `log`, `diff`

**Теория:** `git status -sb`, `git add -p` (по частям), `git commit -v` (видеть diff при написании сообщения), `git log --oneline --graph --decorate --all`, `git diff` vs `git diff --staged` vs `git diff HEAD`.
**Анти-паттерн:** `git add .` без просмотра diff. Так в репо попадают `node_modules`, токены и отладочные `fmt.Println`.
**Практика:** настройте алиасы: `lg = log --oneline --graph --decorate --all`, `st = status -sb`, `cm = commit -v`. Используйте `git add -p` — после него вы перестанете коммитить мусор.

### Урок 1.3 — `.gitignore`, `.gitattributes`, `.mailmap`

**Теория:** глобальный `~/.gitignore_global` (IDE, OS), репо-локальный `.gitignore` (артефакты), `.gitattributes` (eol=lf, linguist-language, filter=lfs), `.mailmap` для нормализации авторов.
**Практика:** возьмите шаблон [github/gitignore — Go.gitignore](https://github.com/github/gitignore/blob/main/Go.gitignore), добавьте `/bin/`, `/dist/`, `coverage.out`, `.env`. Запретите CRLF через `.gitattributes`: `* text=auto eol=lf`.

### Урок 1.4 — ветки: `branch`, `switch`, `checkout`

**Теория:** ветка — это просто файл с SHA в `.git/refs/heads/`. `switch` (1.23-era) — для веток, `restore` — для файлов, `checkout` — legacy «и швец, и жнец». Detached HEAD — что это и почему не страшно.
**Практика:** создайте 3 ветки от main, переключайтесь, посмотрите граф через `git lg`.

### Урок 1.5 — merge vs rebase vs squash

**Теория:**
- `merge` — сохраняет историю как было, добавляет merge-коммит. Хорошо для long-lived release-веток.
- `rebase` — переписывает коммиты ветки поверх target. Линейная история. Стандарт для feature-веток.
- `squash merge` — все коммиты PR схлопываются в один. Дефолт GitHub Flow для маленьких PR.

**Правило:** rebase только **свою** ветку, которую никто не пуллил. Чужую общую — никогда.
**Практика:** одну и ту же фичу влейте тремя способами в три копии репо. Сравните `git lg`.

### Урок 1.6 — разрешение конфликтов

**Теория:** маркеры `<<<<<<<`, `=======`, `>>>>>>>`. `git config merge.conflictStyle diff3` — добавляет «base» секцию, в 90% случаев конфликт становится очевидным. `git mergetool` (vimdiff/meld/vscode). `git rerere` (reuse recorded resolution) — Git запоминает ваше решение и применяет его автоматически при повторном конфликте.
**Практика:** включите `rerere.enabled=true`, создайте конфликт, разрешите, отмените merge через `git merge --abort`, повторите merge — Git разрешит сам.

### Мини-проект недели 1

`gitlab-from-scratch` (учебный) — создайте локальный bare-репозиторий через `git init --bare`, добавьте его как remote к двум локальным клонам, имитируйте работу двух разработчиков: коммиты, push, pull, конфликт, разрешение через `diff3` и `rerere`. Зафиксируйте в README: «зачем нужен rebase» и «когда merge лучше».

---

## 🧬 Неделя 2 — переписывание истории, восстановление, поиск багов

### Урок 2.1 — `commit --amend`, `--fixup`, `--squash`

**Теория:** `amend` меняет последний коммит (сообщение или содержимое). `commit --fixup=<sha>` создаёт «технический» fixup-коммит, который `rebase -i --autosquash` автоматически приклеит к нужному.
**Практика:** сделайте 5 коммитов, два из них «забыли что-то» — добавьте через `--fixup`, потом `git rebase -i --autosquash main` — история станет идеальной.

### Урок 2.2 — `git rebase -i` глубоко

**Теория:** команды `pick`, `reword`, `edit`, `squash`, `fixup`, `drop`, `exec`. `exec go test ./...` после каждого коммита — проверка, что история «компилируется». Перенос коммита, разделение коммита через `edit` + `reset HEAD^` + два новых `commit`.
**Практика:** возьмите свою ветку с 10+ грязными коммитами, превратите в 3–4 осмысленных. Запустите `git rebase -i --exec 'go test ./...' main` — убедитесь, что каждый коммит зелёный.

### Урок 2.3 — `reset`, `restore`, `revert`

**Теория:**
- `reset --soft` — двигает HEAD, индекс и working tree остаются (хорошо для «переделать последний коммит»).
- `reset --mixed` (default) — двигает HEAD и индекс, working tree остаётся.
- `reset --hard` — двигает всё, изменения теряются (НО reflog знает).
- `restore` — современная замена `checkout -- <file>` для файлов.
- `revert` — создаёт **новый** коммит, отменяющий целевой. Единственно безопасный способ откатить уже запушенный коммит.

**Практика:** сделайте `reset --hard` и восстановите через reflog (следующий урок).

### Урок 2.4 — `reflog` — спасательный круг

**Теория:** `reflog` — журнал всех движений HEAD за 90 дней (по умолчанию). `git reflog`, `git reset --hard HEAD@{5}`, восстановление удалённой ветки через `git branch recovered <sha-из-reflog>`.
**Практика:** удалите ветку с важными коммитами, восстановите. После этого упражнения вы перестанете бояться Git.

### Урок 2.5 — `git stash`

**Теория:** `stash push -u -m "wip"` (с untracked файлами), `stash list`, `stash pop` vs `stash apply`, `stash branch <name>` — превращает стэш в новую ветку (полезно при конфликтах).
**Практика:** начали работу в неправильной ветке → `stash` → `switch` в правильную → `stash pop`.

### Урок 2.6 — `git bisect run` — двоичный поиск по истории

**Теория:** `git bisect start`, `bisect bad HEAD`, `bisect good v1.0.0`. Git за O(log n) шагов найдёт виновный коммит. Автоматизация через `bisect run go test ./...` — exit code 0 = good, 1–127 (кроме 125) = bad, 125 = skip.
**Практика:** сломайте тест 20 коммитов назад, запустите `git bisect run go test ./...` — Git найдёт виновника за 5 шагов.

### Урок 2.7 — `git worktree` — несколько веток одновременно

**Теория:** `git worktree add ../proj-fix bugfix-branch` — создаёт второй working tree без второго клона. Используется в монорепо и при срочных hotfix-ах, когда не хочется ломать незакоммиченные изменения в текущей ветке.
**Практика:** работайте над фичей в `~/proj`, одновременно сделайте hotfix в `~/proj-hotfix`, оба используют один `.git`.

### Урок 2.8 — `blame`, `log -S`, `log -L`, `log --follow`

**Теория:**
- `git blame -L 10,30 file.go` — кто и когда менял строки.
- `git log -S 'funcName'` (pickaxe) — коммит, где появилось/исчезло слово.
- `git log -L :funcName:file.go` — история конкретной функции.
- `git log --follow file.go` — история, пережившая переименование.

**Практика:** возьмите `net/http` из Go-репозитория, найдите коммит, который ввёл `ServeMux 1.22+ pattern matching`.

### Мини-проект недели 2

`git-detective` — учебное упражнение: возьмите любой публичный Go-проект (например, `chi` или `gin`), найдите три коммита по сценариям:
1. Коммит, который ввёл конкретную функцию (`log -S`).
2. Коммит, который сломал бы тест X, если бы он существовал (`bisect run`).
3. История переименованного файла (`log --follow`).

Оформите как `INVESTIGATION.md` в своём репо со скриншотами и SHA.

---

## 🚀 Неделя 3 — GitHub, CI/CD, релизы, open source

### Урок 3.1 — workflow: Git Flow vs GitHub Flow vs Trunk-Based

**Теория:**
- **Git Flow** — `develop` + `release/*` + `hotfix/*`. Хорошо для редко релизящихся продуктов (десктоп, прошивки). В вебе/сервисах — overkill в 2026.
- **GitHub Flow** — короткие feature-ветки от `main`, PR → review → squash merge → deploy. **Стандарт для backend в 2026.**
- **Trunk-Based Development** — все коммитят в `main`, фичи прячутся за feature flags. Требует зрелого CI и feature-flag платформы (Unleash, Flagsmith, LaunchDarkly).

**Практика:** выберите GitHub Flow для своих учебных проектов. Опишите в `CONTRIBUTING.md`: длительность веток ≤ 2 дня, PR ≤ 400 строк, squash merge, линейная история.

### Урок 3.2 — `gh` CLI: GitHub без браузера

**Теория:** `gh auth login`, `gh repo clone/fork/view`, `gh pr create/checkout/review/merge`, `gh issue create/list`, `gh run watch` (CI прямо в терминале), `gh api` (raw REST/GraphQL).
**Практика:** проведите полный цикл «фича → PR → ревью → merge» без открытия браузера.

### Урок 3.3 — pre-commit hooks: lefthook / pre-commit

**Теория:** `core.hooksPath`, нативные хуки (`.git/hooks/*`), `lefthook` (Go-friendly, YAML-конфиг), `pre-commit` (Python-фреймворк, огромный набор готовых хуков).
**Что вешать:**
- `pre-commit`: `gofmt -l`, `gofumpt -l`, `golangci-lint run --new-from-rev=HEAD~1`, `go test -race -short ./...`.
- `commit-msg`: commitlint с conventional commits (`feat:`, `fix:`, `refactor:`, `docs:`).
- `pre-push`: полный `go test -race ./...` + `govulncheck ./...`.

**Практика:** настройте `lefthook.yml`, попробуйте закоммитить отформатированный криво файл — хук остановит. Закоммитьте с сообщением `wip` — commitlint остановит.

### Урок 3.4 — Conventional Commits + автогенерация CHANGELOG

**Теория:** формат `<type>(<scope>): <subject>`. Типы: `feat`, `fix`, `perf`, `refactor`, `docs`, `test`, `build`, `ci`, `chore`. Footer `BREAKING CHANGE:` → мажорный релиз.
**Инструменты:** [`git-cliff`](https://git-cliff.org) (Rust, конфигурируемый), [`release-please`](https://github.com/googleapis/release-please) (Google, делает PR с релизом автоматически).
**Практика:** настройте release-please в Actions — он сам создаст PR `chore: release v0.2.0` с CHANGELOG-ом из ваших коммитов.

### Урок 3.5 — Signed commits (Verified badge)

**Теория:** GPG-подпись — классика, но муторная. **SSH-подпись (Git 2.34+) — современный стандарт.** Один SSH-ключ для push и подписи.

**Настройка:**

```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
git config --global tag.gpgsign true
```

Добавьте тот же ключ в GitHub → Settings → SSH and GPG keys → New SSH key → Key type: **Signing Key**.
**Практика:** все коммиты в учебном репо должны быть с зелёным «Verified» на GitHub.

### Урок 3.6 — GitHub Actions для Go (production-grade)

**Что в workflow:**

```yaml
name: ci
on: [push, pull_request]
jobs:
  test:
    strategy:
      matrix:
        go: ['1.22', '1.23']
        os: [ubuntu-latest, macos-latest]
    runs-on: ${{ matrix.os }}
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-go@v5
        with:
          go-version: ${{ matrix.go }}
          cache: true
      - run: go vet ./...
      - uses: golangci/golangci-lint-action@v6
      - run: go test -race -coverprofile=coverage.out ./...
      - uses: codecov/codecov-action@v4
      - run: go run golang.org/x/vuln/cmd/govulncheck@latest ./...
```

**Практика:** добавьте workflow к одному из своих проектов. Включите **branch protection** на `main`: require PR, require status `ci` green, require linear history, require signed commits.

### Урок 3.7 — релизы через goreleaser

**Теория:** `.goreleaser.yaml` описывает сборку под все ОС/архитектуры, создание GitHub Release, прикрепление бинарей, генерацию checksums, публикацию Homebrew tap, Docker-образа в ghcr.io.
**Практика:** настройте `goreleaser` для проекта модуля 00 (`gocount`): тег `v0.1.0` → автоматически собираются бинари под linux/darwin/windows × amd64/arm64, публикуются в Releases.

### Урок 3.8 — большие репо: partial clone, sparse-checkout, maintenance

**Теория:**
- `git clone --filter=blob:none --no-checkout` — клонирование без блобов, скачиваются по требованию.
- `git sparse-checkout init --cone` + `git sparse-checkout set src/ docs/` — рабочая копия только нужных папок.
- `git maintenance start` — фоновая оптимизация репо (gc, commit-graph, prefetch). Обязательно для монорепо размером > 1 ГБ.

**Практика:** склонируйте `kubernetes/kubernetes` через partial clone + sparse-checkout — получите рабочую копию только `staging/src/k8s.io/client-go/` за минуты вместо часа.

### Урок 3.9 — контрибьют в open source

**Сценарий:**
1. Форкнуть Go-проект на GitHub.
2. `git clone` форка, `git remote add upstream https://github.com/owner/repo`.
3. `git fetch upstream && git switch -c fix/typo upstream/main`.
4. Исправить мелочь (typo в docstring, забытый тест, fix в README).
5. `gh pr create --fill --web` → пройти ревью мейнтейнера.
6. После merge: `git switch main && git pull upstream main && git push origin main`.

**Практика:** реальный PR в реальный open-source Go-проект. Это и есть выпускной экзамен модуля.

---

## 🏁 Финальный капстоун модуля

**Возьмите свой лучший проект** (например, `gocount` из модуля 00 или `gocrawl` из модуля 19) и приведите его репозиторий к **production-виду**:

1. **История чистая и линейная** — squash merge везде, никаких «merge branch main into feature».
2. **Conventional commits** + автогенерируемый `CHANGELOG.md` через release-please или git-cliff.
3. **Signed commits** — все коммиты Verified.
4. **Pre-commit hooks** (lefthook): `gofmt`, `gofumpt`, `golangci-lint`, `go test -race -short`, commitlint.
5. **GitHub Actions**: lint + test + race + coverage + govulncheck + build matrix (Go 1.22/1.23 × linux/macos).
6. **Branch protection** на `main`: PR обязателен, ≥ 1 approve, CI зелёный, linear history, signed commits.
7. **Templates**: `.github/PULL_REQUEST_TEMPLATE.md`, `.github/ISSUE_TEMPLATE/{bug,feature}.yml`, `CODEOWNERS`.
8. **Релиз `v0.1.0`** через goreleaser: бинари под linux/darwin/windows × amd64/arm64, checksums, Docker-образ в `ghcr.io`.
9. **README с badges**: CI, coverage (codecov), Go Report Card, Go reference, license, latest release.
10. **CONTRIBUTING.md** + **CODE_OF_CONDUCT.md** + **SECURITY.md** — минимальный набор для open source.

После этого любой ревьюер, открывая ваш репозиторий, **за 30 секунд** видит уровень Middle+: чистая история, зелёный CI, релизы, документация, безопасность.

---

## 📚 Бесплатные ресурсы

### Книги и документация

- [Pro Git book](https://git-scm.com/book/ru/v2) (Scott Chacon, **есть на русском**) — must-read, особенно главы 7 и 10.
- [Git Reference](https://git-scm.com/docs) — официальная документация по командам.
- [GitHub Docs](https://docs.github.com/) — официальные гайды.
- [Conventional Commits](https://www.conventionalcommits.org/ru/v1.0.0/) — спецификация (RU).
- [Trunk Based Development](https://trunkbaseddevelopment.com/) — Paul Hammant.
- [Semantic Versioning 2.0.0](https://semver.org/lang/ru/) (RU).

### Интерактивные тренажёры

- [Learn Git Branching](https://learngitbranching.js.org/?locale=ru_RU) — лучший интерактив по ветвлениям (RU).
- [Oh My Git!](https://ohmygit.org/) — игра про Git.
- [GitHub Skills](https://skills.github.com/) — курсы прямо в issues вашего форка.

### Спасательные шпаргалки

- [Oh Shit, Git!?!](https://ohshitgit.com/) — как выбраться из любой Git-катастрофы.
- [Dangit, Git!?!](https://dangitgit.com/ru) — то же самое (RU).
- [GitHub Cheat Sheet](https://training.github.com/downloads/ru/github-git-cheat-sheet.pdf) (RU PDF).

### Статьи и доклады

- Linus Torvalds — *Tech Talk: Linus Torvalds on Git* (YouTube, классика).
- Scott Chacon — *Advanced Git tutorials* (видео).
- Julia Evans — Git zines (`wizardzines.com`) — иллюстрированные шпаргалки.
- Atlassian — [Advanced Git Tutorials](https://www.atlassian.com/git/tutorials/advanced-overview).

### Инструменты (всё OSS)

- **CLI:** [`gh`](https://cli.github.com/) — GitHub CLI, [`tig`](https://jonas.github.io/tig/) — TUI для логов и diff.
- **Hooks:** [`lefthook`](https://github.com/evilmartians/lefthook), [`pre-commit`](https://pre-commit.com/).
- **Commits:** [`commitlint`](https://commitlint.js.org/), [`czg`](https://github.com/Zhengqbbb/cz-git) — интерактивные conventional commits.
- **Changelog:** [`git-cliff`](https://git-cliff.org/), [`release-please`](https://github.com/googleapis/release-please).
- **Release:** [`goreleaser`](https://goreleaser.com/) — стандарт релизов для Go.
- **Безопасность:** [`gitleaks`](https://github.com/gitleaks/gitleaks), [`git-secrets`](https://github.com/awslabs/git-secrets) — ловят утечки секретов в коммитах.
- **GUI (если нужно):** [`lazygit`](https://github.com/jesseduffield/lazygit) — TUI, [`gitui`](https://github.com/extrawurst/gitui).
- **YouTube (RU):** ADV-IT — «Git и GitHub», Артём Матяшов — «Git для начинающих».

---

## ⚠️ Анти-паттерны и правила безопасности

1. **Никогда `git push --force` в общую ветку.** Только `--force-with-lease` (Git проверит, что вы не затёрли чужие коммиты).
2. **Никогда не коммитьте секреты.** Используйте `gitleaks` в pre-commit. Если уже закоммитили — ротируйте секрет немедленно (вычистить из истории через `git filter-repo` НЕ означает, что его никто не успел склонировать).
3. **`main` всегда зелёный.** Ломающие изменения — только через PR с зелёным CI.
4. **1 PR = 1 логическое изменение.** Рефактор и фича — два разных PR.
5. **Commit message в императиве**, ≤ 72 символа в заголовке: «add retry logic», не «added retries» и не «adding retry». Тело — *почему*, а не *что* (что видно из diff).
6. **Не делайте `git pull` без понимания.** По умолчанию это `fetch + merge` — плодит merge-коммиты. Настройте: `git config --global pull.rebase true` или `pull.ff only`.
7. **Если переписали историю** уже запушенной ветки — предупредите команду. Иначе у коллег будут расходящиеся графы.
8. **Не используйте `cherry-pick` как замену merge/rebase.** Он создаёт дубликаты коммитов с другими SHA — это путаница и боль в `git log`.
9. **Не работайте долго в одной ветке.** > 3 дней без `rebase main` → конфликты гарантированы. Маленькие PR — счастливая жизнь.
10. **Не игнорируйте `.gitattributes`.** В смешанных Win/Mac/Linux командах без `eol=lf` будут «diff-ы из 10 000 строк, я ничего не менял».

---

## 🔥 Чек-лист «я прошёл модуль»

- [ ] Объясняю модель Git (blob/tree/commit/refs/HEAD) и могу прочитать `.git/objects` руками.
- [ ] Уверенно делаю `rebase -i` с reword/squash/fixup/edit/drop, понимаю autosquash.
- [ ] Восстановил «удалённый» коммит через `reflog` хотя бы один раз.
- [ ] Нашёл реальный регресс через `git bisect run`.
- [ ] Использовал `worktree` для параллельной работы над двумя ветками.
- [ ] Настроил `lefthook` / `pre-commit` с gofmt, golangci-lint, go test -race, commitlint.
- [ ] Все мои коммиты Verified (SSH-подпись).
- [ ] Написал production-grade GitHub Actions workflow для Go (matrix + cache + race + coverage + govulncheck).
- [ ] Включил branch protection на `main`: PR + green CI + linear history + signed.
- [ ] Сделал релиз `v0.1.0` через goreleaser с бинарями под 3 ОС и Docker-образом в ghcr.io.
- [ ] Открыл PR в реальный open-source Go-проект и провёл его до merge.

После этого модуля вы перестанете бояться Git и начнёте писать историю, которой не стыдно показать тимлиду. Это один из тех навыков, которые **отличают Junior от Middle** на собеседовании сильнее, чем знание паттернов конкурентности.
