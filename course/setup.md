# 🛠 Настройка среды Go — модуль «нулевой день» (с нуля до профи)

> Прежде чем учить язык — настройте среду один раз и правильно. Любой час, потраченный на нормальный gopls, делbug-конфиг и линтеры, экономит десятки часов на отладке и ревью потом. Этот модуль закрывает всё: установка Go, выбор IDE, отладка через Delve, линтеры, форматтеры, управление версиями Go, окружение для macOS/Linux/Windows/WSL, Docker dev-контейнеры и devcontainers для воспроизводимости.

**Длительность:** 1–2 дня (читать → делать сразу).
**Префикс по грейдам:** обязательно для всех. На Middle+ вы вернётесь сюда настроить gopls и Delve тоньше.

---

## 🎯 Чему вы научитесь

- Ставить Go так, чтобы потом не плакать (без `brew install go` поверх системного).
- Управлять несколькими версиями Go параллельно (`gvm`, `asdf`, нативный `go install golang.org/dl/go1.X.Y@latest`).
- Понимать переменные окружения: `GOROOT`, `GOPATH`, `GOBIN`, `GOPROXY`, `GOFLAGS`, `GOMODCACHE`, `GOTOOLCHAIN`.
- Настраивать VS Code / GoLand / Neovim под Go-разработку «как у сеньоров».
- Использовать `gopls` (Language Server) на полную: autocomplete, refactor, code lens, inlay hints.
- Отлаживать через Delve (`dlv`) — breakpoints, watch, conditional breakpoints, remote debug.
- Поднимать линтеры (`golangci-lint`), форматтеры (`gofumpt`, `gci`, `goimports`) и pre-commit-хуки.
- Работать в Docker dev-container / devcontainers / Nix для полностью воспроизводимой среды.
- Настраивать терминал, шеллы и Git так, чтобы Go-разработка была быстрой.

---

## 🗺 Дорожная карта модуля

| Шаг | Что делаем | Время |
|-----|-----------|-------|
| 1 | Ставим Go правильным способом под вашу ОС | 30 мин |
| 2 | Разбираемся с `GOROOT`/`GOPATH`/`GOBIN` и `GOTOOLCHAIN` | 30 мин |
| 3 | Выбираем и настраиваем IDE (VS Code / GoLand / Neovim) | 1 ч |
| 4 | Ставим `gopls`, `dlv`, `golangci-lint`, `gofumpt` | 30 мин |
| 5 | Настраиваем отладку и тестовый workflow | 1 ч |
| 6 | Делаем dev-container / devcontainer.json | 1 ч |
| 7 | Финальная проверка: «hello world» с тестами, отладкой и линтом | 30 мин |

---

## 🧰 Шаг 1 — установка Go

### 1.1 Правило №1: только официальный дистрибутив или менеджер версий

Самая частая ошибка новичков — `apt install golang`, `brew install go`, `yum install go`. Системные пакеты Go **отстают на 1–3 версии**, а в 2026 это значит — нет generics-улучшений 1.22+, нет `range over func` (1.23+), нет PGO. Не делайте так.

**Правильные способы:**

| Способ | Когда брать |
|--------|-------------|
| [go.dev/dl](https://go.dev/dl/) — официальный установщик | Один проект, одна версия Go. Самый простой путь. |
| [`gvm`](https://github.com/moovweb/gvm) | Linux/macOS, несколько проектов с разными версиями Go. |
| [`asdf`](https://asdf-vm.com/) + плагин `asdf-golang` | Универсальный менеджер версий (Go, Node, Python, и т.д.). |
| Нативно: `go install golang.org/dl/go1.X.Y@latest && go1.X.Y download` | Не нужен сторонний менеджер, и у вас уже стоит хотя бы один Go. |
| `GOTOOLCHAIN=go1.23.4` (Go 1.21+) | Магия: Go сам скачает нужную тулчейн-версию под `go.mod`. Идеально для CI и команд. |

### 1.2 Установка под macOS

```bash
# вариант А — официальный pkg
# скачайте go1.23.X.darwin-arm64.pkg с https://go.dev/dl/ и запустите

# вариант Б — Homebrew (если совсем лень)
brew install go

# вариант В — несколько версий через asdf
brew install asdf
asdf plugin add golang
asdf install golang 1.23.4
asdf global golang 1.23.4
```

### 1.3 Установка под Linux

```bash
# официальный архив (предпочтительно — всегда свежий)
GO_VERSION=1.23.4
curl -LO https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go${GO_VERSION}.linux-amd64.tar.gz

# добавьте в ~/.zshrc или ~/.bashrc:
export PATH=$PATH:/usr/local/go/bin
export PATH=$PATH:$HOME/go/bin
```

### 1.4 Установка под Windows

- Скачайте `go1.23.X.windows-amd64.msi` с [go.dev/dl](https://go.dev/dl/) и запустите.
- **Лучше: используйте WSL2 + Ubuntu 22.04** и ставьте Go как под Linux. Подавляющее большинство Go-туториалов, инструментов и docker-окружений рассчитаны на Unix-семантику путей. Windows-разработка на Go возможна, но даёт лишние боли с CRLF, `exec`, путями к бинарникам.

### 1.5 Проверка установки

```bash
go version          # должно вывести: go version go1.23.4 ...
go env              # печатает все переменные окружения Go
go env GOROOT       # путь к установке Go (обычно /usr/local/go или ~/go)
go env GOPATH       # путь к "рабочей области" (обычно ~/go)
go env GOBIN        # куда ставятся бинари go install (обычно $GOPATH/bin)
```

**Проверка работоспособности:** создайте `hello.go` и запустите.

```bash
mkdir -p ~/code/hello && cd ~/code/hello
go mod init hello
cat > main.go <<'EOF'
package main

import "fmt"

func main() {
	fmt.Println("привет, Go", "👋")
}
EOF
go run .
```

Если видите «привет, Go 👋» — установка ок.

---

## ⚙️ Шаг 2 — `GOROOT`, `GOPATH`, `GOBIN` и токсичные переменные

### 2.1 Что есть что

- **`GOROOT`** — куда установлен сам Go (`/usr/local/go`). **Не трогайте**, если не понимаете зачем.
- **`GOPATH`** — «рабочая папка» Go-инструментов. По умолчанию `~/go`. Хранит:
  - `~/go/bin` — бинари, поставленные через `go install`.
  - `~/go/pkg/mod` — кэш модулей (это **не** ваш код, не пугайтесь размера).
- **`GOBIN`** — куда ставить бинари из `go install`. По умолчанию `$GOPATH/bin`. Удобно: `export GOBIN=$HOME/.local/bin`.
- **`GOPROXY`** — прокси для скачивания модулей. По умолчанию `https://proxy.golang.org,direct`. В России может быть медленно — поставьте `GOPROXY=https://goproxy.cn,direct` (Китай) или поднимите свой Athens.
- **`GOSUMDB`** — checksum database. `off` если ходите за приватными модулями. Иначе не трогайте.
- **`GOFLAGS`** — глобальные флаги для всех команд go. Пример: `GOFLAGS="-count=1"` — отключает кэш тестов.
- **`GOMODCACHE`** — путь к кэшу модулей. Иногда выносят на быстрый SSD.
- **`GOTOOLCHAIN` (Go 1.21+)** — `auto` (default), `local`, или конкретная версия. С `auto` Go сам подтянет нужную версию по `go.mod` → команда не зависит от того, у кого какая Go установлена.
- **`CGO_ENABLED`** — `0` для статической линковки (любимый прод-режим), `1` — если нужны нативные либы.

### 2.2 Что положить в `~/.zshrc` / `~/.bashrc`

```bash
# Go
export GOPATH=$HOME/go
export GOBIN=$GOPATH/bin
export PATH=$PATH:/usr/local/go/bin:$GOBIN

# рекомендуемые настройки
export GOFLAGS='-mod=readonly'         # запрет неявных правок go.mod в командах
export GOTOOLCHAIN=auto                 # авто-подгрузка тулчейна по go.mod
export GOPROXY=https://proxy.golang.org,direct
```

После правки — `source ~/.zshrc` (или перезапустите терминал).

### 2.3 Антипаттерны окружения

- ❌ Класть свой код внутрь `$GOPATH/src/...` — это **legacy** до Go 1.11. Сейчас проекты живут где угодно, потому что модули.
- ❌ Хардкодить `GOROOT` в IDE — Go сам его знает через `go env GOROOT`.
- ❌ Ставить `GO111MODULE=off` или `auto` — в 2026 это всегда `on`, и переменная вообще не нужна.
- ❌ Запускать `sudo go install ...` — бинари должны жить в вашем `$GOBIN`, не в `/usr/local/bin`.

---

## 🖥 Шаг 3 — IDE: VS Code, GoLand, Neovim

### 3.1 VS Code (рекомендую для большинства)

**Плюсы:** бесплатно, легко, отличное расширение Go, devcontainers из коробки, миллионы туториалов.

**Установка:**

1. Поставьте [VS Code](https://code.visualstudio.com/).
2. Установите расширение **Go** (publisher: Go Team at Google).
3. Откройте папку с Go-кодом. VS Code предложит установить инструменты — соглашайтесь, он сам поставит `gopls`, `dlv`, `staticcheck` и т.д.
4. Откройте Command Palette (`Cmd/Ctrl+Shift+P`) → `Go: Install/Update Tools` → выбрать все → OK.

**Минимальный `settings.json` для Go (User или Workspace):**

```json
{
  "go.useLanguageServer": true,
  "go.lintTool": "golangci-lint",
  "go.lintOnSave": "workspace",
  "go.formatTool": "gofumpt",
  "go.testFlags": ["-race", "-count=1", "-v"],
  "go.testTimeout": "60s",
  "go.coverOnSave": false,
  "go.coverageDecorator": { "type": "gutter" },
  "[go]": {
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": { "source.organizeImports": "explicit" },
    "editor.tabSize": 4,
    "editor.insertSpaces": false
  },
  "gopls": {
    "ui.semanticTokens": true,
    "ui.inlayhint.hints": {
      "assignVariableTypes": true,
      "compositeLiteralFields": true,
      "constantValues": true,
      "functionTypeParameters": true,
      "parameterNames": true,
      "rangeVariableTypes": true
    },
    "ui.diagnostic.staticcheck": true,
    "build.experimentalWorkspaceModule": false
  }
}
```

**Полезные шорткаты:**

- `F12` — go to definition.
- `Shift+F12` — find all references.
- `F2` — rename symbol (работает по всему проекту).
- `Cmd+.` / `Ctrl+.` — quick fix / refactor.
- `Cmd+Shift+O` — symbol in file.
- `F5` — debug current file/test.

### 3.2 GoLand (для тех, кто любит JetBrains)

**Плюсы:** мощнейший рефакторинг, встроенный debugger, профайлер, бесшовные тесты, database tools, HTTP-клиент.
**Минусы:** платно (~$199/год после триала, есть бесплатные лицензии для студентов и OSS-мейнтейнеров).

После установки: `File → Settings → Go → GOROOT/GOPATH` — обычно подхватывает само. Включите `File Watchers` для `gofumpt` и `golangci-lint`.

### 3.3 Neovim / LunarVim / LazyVim (для хардкорщиков)

Минимальная конфигурация Neovim для Go (через [`lazy.nvim`](https://github.com/folke/lazy.nvim)):

```lua
{
  "ray-x/go.nvim",
  dependencies = { "ray-x/guihua.lua", "neovim/nvim-lspconfig", "nvim-treesitter/nvim-treesitter" },
  config = function()
    require("go").setup({
      lsp_cfg = true,
      lsp_gofumpt = true,
      lsp_inlay_hints = { enable = true },
      dap_debug = true,
      lsp_keymaps = true,
    })
  end,
  event = { "CmdlineEnter" },
  ft = { "go", "gomod", "gosum" },
  build = ':lua require("go.install").update_all_sync()',
}
```

Это даст: `gopls` LSP, debug через DAP+Delve, тесты, форматирование, импорты.

---

## 🧠 Шаг 4 — обязательные инструменты

Поставьте всё одной командой:

```bash
go install golang.org/x/tools/gopls@latest
go install github.com/go-delve/delve/cmd/dlv@latest
go install honnef.co/go/tools/cmd/staticcheck@latest
go install mvdan.cc/gofumpt@latest
go install github.com/daixiang0/gci@latest
go install golang.org/x/tools/cmd/goimports@latest
go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest
go install github.com/securego/gosec/v2/cmd/gosec@latest
go install golang.org/x/vuln/cmd/govulncheck@latest
go install github.com/go-task/task/v3/cmd/task@latest
```

Что это и зачем:

- **`gopls`** — официальный Go Language Server. Без него IDE — просто текстовый редактор.
- **`dlv`** (Delve) — отладчик. Breakpoints, watch, conditional, remote debug.
- **`staticcheck`** — самый качественный статический анализатор для Go.
- **`gofumpt`** — `gofmt` на стероидах. Стандарт в строгих командах.
- **`gci`** — сортировщик импортов с поддержкой групп (stdlib / external / local).
- **`goimports`** — добавляет и убирает импорты автоматически. Замена `gofmt`.
- **`golangci-lint`** — мета-линтер, запускает 50+ линтеров одной командой.
- **`gosec`** — security-линтер (hardcoded secrets, weak crypto, SQL injection).
- **`govulncheck`** — официальный сканер уязвимостей (CVE) в ваших зависимостях.
- **`task`** — современный аналог `make`, YAML-конфиг, кросс-платформенный.

Проверьте, что `$GOBIN` в `PATH`:

```bash
which gopls dlv golangci-lint
# должно показать пути в ~/go/bin/...
```

---

## 🐞 Шаг 5 — отладка через Delve

### 5.1 Базовая отладка из CLI

```bash
# отладить main-пакет
dlv debug .

# отладить конкретный тест
dlv test ./pkg/... -- -test.run TestParseConfig

# подключиться к запущенному процессу
dlv attach <PID>

# remote debug в Docker / Kubernetes
dlv exec --headless --listen=:40000 --api-version=2 ./mybinary
```

В `dlv` (REPL): `b main.main` — breakpoint, `c` — continue, `n` — next, `s` — step in, `p var` — print, `locals`, `stack`, `goroutines`, `gr <id>` — переключиться на goroutine.

### 5.2 `launch.json` для VS Code

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Launch package",
      "type": "go",
      "request": "launch",
      "mode": "auto",
      "program": "${workspaceFolder}",
      "env": { "LOG_LEVEL": "debug" },
      "args": []
    },
    {
      "name": "Debug current test",
      "type": "go",
      "request": "launch",
      "mode": "test",
      "program": "${fileDirname}",
      "args": ["-test.run", "${selectedText}", "-test.v"]
    },
    {
      "name": "Attach to remote",
      "type": "go",
      "request": "attach",
      "mode": "remote",
      "remotePath": "/app",
      "port": 40000,
      "host": "127.0.0.1"
    }
  ]
}
```

Поставьте breakpoint (F9 на строке) → F5 → пошагово через F10/F11.

### 5.3 Что должно «просто работать» после настройки

- ✅ Code completion (после точки и в импортах).
- ✅ Go to definition (`F12`).
- ✅ Hover показывает документацию и тип.
- ✅ Inlay hints для параметров и типов переменных.
- ✅ Auto-import: пишете `http.Get` — `net/http` добавляется сам.
- ✅ Format on save через `gofumpt` + `goimports`.
- ✅ Lint on save через `golangci-lint` (быстрый — `fast` пресет).
- ✅ Run и Debug тестов кнопкой над функцией `TestXxx`.

Если что-то из этого не работает — почти всегда виноват `gopls` или версия Go. Лечится: `Go: Install/Update Tools` → перезапуск IDE.

---

## 🐳 Шаг 6 — воспроизводимая среда: Docker + devcontainers

Чтобы любой человек (и CI) собирал ваш проект одинаково — заведите `devcontainer.json` или хотя бы dev-Dockerfile.

### 6.1 `.devcontainer/devcontainer.json` (VS Code / GitHub Codespaces)

```json
{
  "name": "Go Dev",
  "image": "mcr.microsoft.com/devcontainers/go:1.23-bookworm",
  "features": {
    "ghcr.io/devcontainers/features/docker-in-docker:2": {},
    "ghcr.io/devcontainers/features/git:1": {}
  },
  "postCreateCommand": "go install golang.org/x/tools/gopls@latest && go install github.com/go-delve/delve/cmd/dlv@latest && go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest && go install mvdan.cc/gofumpt@latest",
  "customizations": {
    "vscode": {
      "extensions": ["golang.go", "EditorConfig.EditorConfig", "redhat.vscode-yaml"],
      "settings": {
        "go.formatTool": "gofumpt",
        "go.lintTool": "golangci-lint",
        "[go]": { "editor.formatOnSave": true }
      }
    }
  },
  "remoteUser": "vscode"
}
```

Открываете проект → VS Code предлагает `Reopen in Container` → через 2 минуты у вас полностью настроенная Go-среда внутри контейнера. На другой машине / в Codespaces — то же самое.

### 6.2 Минимальный dev-Dockerfile (для команд без VS Code)

```dockerfile
FROM golang:1.23-bookworm

RUN apt-get update && apt-get install -y --no-install-recommends \
  git curl make ca-certificates \
  && rm -rf /var/lib/apt/lists/*

ENV GOFLAGS=-mod=readonly GOTOOLCHAIN=auto
RUN go install github.com/go-delve/delve/cmd/dlv@latest \
 && go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest \
 && go install mvdan.cc/gofumpt@latest

WORKDIR /workspace
```

```bash
docker build -t go-dev .
docker run --rm -it -v "$PWD":/workspace go-dev bash
```

### 6.3 Multi-stage production Dockerfile (для финального бинаря)

```dockerfile
# ---- builder ----
FROM golang:1.23-bookworm AS builder
WORKDIR /src
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -trimpath -ldflags="-s -w" -o /out/app ./cmd/app

# ---- runtime ----
FROM gcr.io/distroless/static:nonroot
COPY --from=builder /out/app /app
USER nonroot:nonroot
ENTRYPOINT ["/app"]
```

Финальный образ ~10–20 МБ, без шелла, не-root юзер. Стандарт production-сборок Go в 2026.

---

## ✅ Шаг 7 — финальная проверка («acceptance test» вашей среды)

Создайте папку `hello-setup/` и положите в неё:

`go.mod`:
```
module hello-setup

go 1.23
```

`main.go`:
```go
package main

import (
	"fmt"
	"os"
)

func greet(name string) string {
	if name == "" {
		name = "world"
	}
	return fmt.Sprintf("hello, %s 👋", name)
}

func main() {
	fmt.Println(greet(os.Getenv("USER")))
}
```

`main_test.go`:
```go
package main

import "testing"

func TestGreet(t *testing.T) {
	t.Parallel()
	cases := map[string]string{
		"":       "hello, world 👋",
		"alice":  "hello, alice 👋",
	}
	for in, want := range cases {
		in, want := in, want
		t.Run(in, func(t *testing.T) {
			t.Parallel()
			if got := greet(in); got != want {
				t.Fatalf("greet(%q) = %q, want %q", in, got, want)
			}
		})
	}
}
```

Прогоните чек-лист:

```bash
go run .                          # запуск
go test -race -v ./...            # тесты с детектором гонок
go vet ./...                      # встроенный анализатор
gofumpt -l .                      # форматирование
golangci-lint run                 # все линтеры
govulncheck ./...                 # уязвимости
go build -o bin/hello .           # собрать бинарь
```

Если **все 7 команд прошли зелёными** — поздравляю, среда настроена правильно. Можно идти в модуль 00.

В IDE поставьте breakpoint в `greet` и запустите тест через Debug — должно остановиться, должен показаться стек, переменные и goroutine 1. Это финальная проверка, что Delve и IDE дружат.

---

## 📦 Бонус — Taskfile, EditorConfig, базовый `.golangci.yml`

### `Taskfile.yml` — запуск всего одной командой

```yaml
version: '3'

tasks:
  default:
    cmds: [task --list]

  run:
    desc: run the app
    cmds: [go run ./cmd/app]

  test:
    desc: race-tests + cover
    cmds: [go test -race -coverprofile=coverage.out ./...]

  lint:
    desc: run golangci-lint
    cmds: [golangci-lint run ./...]

  fmt:
    desc: format with gofumpt + gci
    cmds:
      - gofumpt -w .
      - gci write --skip-generated -s standard -s default -s "prefix(github.com/me/myproj)" .

  vuln:
    desc: check vulnerabilities
    cmds: [govulncheck ./...]

  build:
    desc: build prod binary
    cmds:
      - CGO_ENABLED=0 go build -trimpath -ldflags="-s -w" -o bin/app ./cmd/app
```

`task test`, `task lint`, `task build` — у всей команды одинаковые команды, не нужно помнить флаги.

### `.editorconfig` — единый стиль для всех IDE

```ini
root = true

[*]
end_of_line = lf
insert_final_newline = true
charset = utf-8
trim_trailing_whitespace = true

[*.go]
indent_style = tab
indent_size = 4

[{*.yml,*.yaml,*.json,*.md}]
indent_style = space
indent_size = 2
```

### Базовый `.golangci.yml`

```yaml
run:
  timeout: 5m

linters:
  enable:
    - errcheck
    - govet
    - ineffassign
    - staticcheck
    - unused
    - gofumpt
    - goimports
    - gosec
    - revive
    - misspell
    - bodyclose
    - prealloc
    - unparam

issues:
  exclude-use-default: false
  max-same-issues: 0
```

---

## 📚 Бесплатные ресурсы

- [go.dev/doc/install](https://go.dev/doc/install) — официальная инструкция установки.
- [go.dev/doc/manage-install](https://go.dev/doc/manage-install) — установка нескольких версий через `go install golang.org/dl/...`.
- [pkg.go.dev — `cmd/go`](https://pkg.go.dev/cmd/go) — официальная документация по `go` CLI.
- [`gopls` settings](https://github.com/golang/tools/blob/master/gopls/doc/settings.md) — все настройки language server-а.
- [Delve docs](https://github.com/go-delve/delve/tree/master/Documentation) — мануал по отладчику.
- [VS Code Go extension docs](https://github.com/golang/vscode-go/blob/master/docs/settings.md) — все настройки расширения.
- [golangci-lint docs](https://golangci-lint.run/) — список линтеров и пресетов.
- [The Twelve-Factor App: III. Config](https://12factor.net/config) — почему конфиг через env-переменные, а не файл.
- [containers.dev](https://containers.dev/) — спецификация devcontainers.
- YouTube (RU): «Установка Go и настройка VS Code» — Николай Тузов; «Среда разработки Go с нуля» — Артём Матяшов.

---

## ⚠️ Частые проблемы и как чинить

| Симптом | Причина | Лечение |
|--------|---------|---------|
| `gopls: command not found` в IDE | `$GOBIN` не в `PATH` | Добавить `export PATH=$PATH:$(go env GOBIN)` в `~/.zshrc` |
| `go: command not found` | `/usr/local/go/bin` не в `PATH` | Добавить в shell rc-файл и `source` |
| `gopls` сильно тормозит | Гигантский `vendor/` или плохой кэш | `go clean -modcache`, удалить `vendor/` если не нужен, рестарт gopls (`Cmd+Shift+P → Go: Restart Language Server`) |
| Breakpoint не срабатывает | Сборка с оптимизациями | Запустите debug через `go build -gcflags="all=-N -l"` (IDE делает это сама в режиме debug) |
| `cannot find module providing package ...` | Не выполнен `go mod tidy` | `go mod tidy` |
| `checksum mismatch` | Кто-то подменил модуль в `go.sum` | `go mod verify`, удалить кэш: `go clean -modcache` |
| Долгая загрузка модулей в РФ | Прокси заблокирован | `export GOPROXY=https://goproxy.cn,direct` или поднять Athens-прокси |
| Windows: пути с обратными слешами ломают тесты | CRLF и `\\` в путях | Используйте WSL2 + Ubuntu, либо `filepath.ToSlash` в коде |
| `gofumpt` спорит с IDE | IDE форматирует через `gofmt` | Поставить `"go.formatTool": "gofumpt"` явно |
| `golangci-lint` ругается на чужой код | Лишние линтеры включены | Скопируйте проверенный `.golangci.yml` (см. выше) |

---

## 🔥 Чек-лист «среда настроена»

- [ ] `go version` показывает 1.23.x или выше.
- [ ] `go env GOPATH`, `GOBIN`, `GOROOT` — все корректные пути, `$GOBIN` в `PATH`.
- [ ] IDE подсвечивает синтаксис, делает autocomplete и go-to-definition.
- [ ] `gopls`, `dlv`, `golangci-lint`, `gofumpt`, `goimports`, `govulncheck` установлены и доступны из терминала.
- [ ] Format on save работает (через `gofumpt`), импорты сами добавляются.
- [ ] `golangci-lint run` отрабатывает на пустом проекте без ошибок.
- [ ] Breakpoint в тесте останавливает Delve, переменные видны.
- [ ] `go test -race -v ./...` зелёный.
- [ ] Есть `.editorconfig`, `.golangci.yml`, `Taskfile.yml` в шаблоне.
- [ ] Есть `.devcontainer/devcontainer.json` — среда воспроизводится одним кликом.

Когда все пункты ✅ — переходите к модулю 00. Дальше будет только код.
