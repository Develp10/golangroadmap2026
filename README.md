<div align="center">

# 🚀 Golang Roadmap 2026

**Полный путь от нуля до Senior Go-разработчика на русском языке**

Реальные сроки · Бесплатные ресурсы · Проекты · Самопроверка

![Go](https://img.shields.io/badge/Go-1.23+-00ADD8?logo=go&logoColor=white)
![Level](https://img.shields.io/badge/Level-Junior%20→%20Senior-blueviolet)
![Time](https://img.shields.io/badge/Time-10–14%20months-orange)
![License](https://img.shields.io/badge/License-MIT-green)

</div>

---

## 🧭 Навигация

Roadmap разбит на отдельные файлы — так удобнее читать, отмечать прогресс и контрибьютить.

### 📘 Этапы обучения

| № | Этап | Срок | Уровень |
|---|------|------|---------|
| 0 | [Фундамент](./roadmap/00-foundation.md) | 2–3 недели | 🟢 |
| 1 | [Синтаксис и основы Go](./roadmap/01-go-basics.md) | 3–4 недели | 🟢 |
| 2 | [Глубокий Go](./roadmap/02-go-deep.md) | 4–6 недель | 🟡 |
| 3 | [Конкурентность](./roadmap/03-concurrency.md) | 3–4 недели | 🟡 |
| 4 | [Стандартная библиотека](./roadmap/04-stdlib.md) | 3 недели | 🟢 |
| 5 | [Базы данных](./roadmap/05-databases.md) | 3–4 недели | 🟡 |
| 6 | [Web и API](./roadmap/06-web-api.md) | 4–6 недель | 🟡 |
| 7 | [Тестирование](./roadmap/07-testing.md) | 2–3 недели | 🟢 |
| 8 | [Микросервисы и сети](./roadmap/08-microservices.md) | 6–8 недель | 🟠 |
| 9 | [DevOps минимум](./roadmap/09-devops.md) | 3–4 недели | 🟠 |
| 10 | [Архитектура и паттерны](./roadmap/10-architecture.md) | 4–6 недель | 🔴 |
| 11 | [Performance и production](./roadmap/11-performance.md) | 3–4 недели | 🔴 |
| 12 | [Подготовка к собесам](./roadmap/12-interview.md) | 3 недели | 🟣 |

### 📎 Дополнительные материалы

- 🧠 [Чек-листы по грейдам](./roadmap/checklists.md) — что должен уметь Junior, Middle, Senior
- ⚡ [Шпаргалка по командам Go](./roadmap/cheatsheet.md) — самые частые `go`-команды
- 🪤 [Типичные ошибки новичков](./roadmap/mistakes.md) — 10 классических граблей
- ❓ [FAQ](./roadmap/faq.md) — ответы на частые вопросы
- 🧰 [Полезные источники](./roadmap/resources.md) — подкасты, каналы, блоги, сообщества

---

## ⏱️ Длительность

| Грейд | Срок (2–3 ч/день) | Что умеешь |
|------|--------------------|-----------|
| 🟢 Junior | 4–6 месяцев | CRUD API, базовая работа с БД, простые горутины |
| 🟡 Middle | 8–12 месяцев | Архитектура сервиса, контекст, тесты, профилирование |
| 🔴 Senior | 2+ года практики | Дизайн систем, наставничество, глубокий runtime |

> Время — ориентир. Один проходит за 6 месяцев, другой за 14. Норм оба варианта.

---

## 📌 Как пользоваться роадмапом

Каждый этап построен по схеме:

```
что учим → зачем это нужно → где брать материал → какой проект → как проверить себя
```

**3 железных правила:**

1. **Не прыгай вперёд.** Go обманчиво простой — без фундамента упрёшься в потолок на собесах.
2. **Пиши код сам.** Подсмотреть можно только после часа борьбы с задачей.
3. **Делай проекты до конца.** Незаконченный проект учит хуже законченного «плохого».

---

## 🗺️ Как проходить

1. Открой [Этап 0](./roadmap/00-foundation.md) и пройди его до конца — отметь чекбоксы в [чек-листе](./roadmap/checklists.md).
2. Каждую неделю смотри [шпаргалку](./roadmap/cheatsheet.md) и [список ошибок](./roadmap/mistakes.md).
3. После каждого проекта сверяйся с чек-пойнтом в конце этапа.
4. Дошёл до конца Junior-блока — иди на первое собеседование, даже если страшно.
5. Не стесняйся возвращаться к ранним этапам — глубина приходит со вторым проходом.

---

## ⚠️ Чего избегать

- **Туториал-ада** — бесконечный просмотр курсов без написания кода.
- **Слепого Clean Architecture** в простом CRUD — оверинжиниринг.
- **Преждевременной оптимизации** — сначала измерь, потом оптимизируй.
- **Микросервисов** там, где хватает монолита.
- **ORM-магии** без понимания SQL.
- **Сравнения себя с другими** — у каждого свой темп. Сравнивай с собой вчерашним.

---

## 🤝 Контрибьют

Нашёл ошибку или хочешь добавить материал — открывай PR или issue. Roadmap живой, обновляется по мере выхода новых версий Go и инструментов.

---

<div align="center">

**⭐ Если roadmap помог — поставь звезду, это лучшая благодарность**

Made with ☕ and ❤️ для Go-сообщества

</div>


---

## 🔥 Подробный практический Roadmap

Ниже — детальный разбор каждого этапа с акцентом на **практику**: что кодить, какие проекты делать, как проверять себя.

---

### Этап 0. Фундамент (2–3 недели) 🟢

Прежде чем писать на Go, нужна база, иначе будешь упираться в стену уже на первом проекте.

**Что учим:**
- Основы работы с терминалом (bash/zsh): навигация, пайпы, grep, find, chmod.
- Git и GitHub: branch, merge, rebase, pull request, конфликты, `rebase -i`.
- Как работает HTTP (методы, статусы, заголовки), что такое REST, JSON.
- Структуры данных: массивы, словари, стек, очередь, дерево, граф — на уровне «знаю и могу нарисовать».
- Алгоритмы: бинарный поиск, сортировки, рекурсия, оценка O(n).
- Сети: TCP/UDP, DNS, TLS на уровне обзора.

**Практика:** настроить рабочую среду (VS Code или GoLand, golangci-lint), завести git-репо для каждой недели обучения, решить 20–30 задач LeetCode Easy на любом языке, поднять и закоммитить проект на GitHub с README.

**Чек-пойнт:** умеешь склонировать репозиторий, создать ветку, сделать PR; можешь объяснить, что происходит при вводе URL в браузере.

---

### Этап 1. Синтаксис и основы Go (3–4 недели) 🟢

**Что учим:**
- Установка Go, `go mod`, структура проекта, `GOPATH` vs модули.
- Типы: `int`, `string`, `bool`, `float64`, `byte`, `rune`, явные конверсии.
- Переменные, константы, `iota`.
- Управляющие конструкции: `if`, `for` (единственный цикл!), `switch` с типами.
- Функции, множественный возврат, именованные возвраты, `defer`.
- Указатели — без них дальше никуда.
- Слайсы (внутреннее устройство: cap, len, отличия от массивов), карты (`map`), строки и руны.
- Структуры и методы, value receiver vs pointer receiver.
- Ошибки: `error`, `errors.Is`, `errors.As`, обёртка `%w`.

**Проект:** CLI-калькулятор + менеджер задач (todo) с сохранением в JSON-файл. Подкоманды: `add`, `list`, `done`, `remove`.

**Самопроверка:** объясни, почему `append` иногда возвращает новый слайс; разница между `nil` map и пустой map; почему `defer` важен для закрытия файлов.

---

### Этап 2. Глубокий Go (4–6 недель) 🟡

**Что учим:**
- Интерфейсы: пустой интерфейс, type assertion, type switch, дизайн интерфейсов (маленькие — лучше).
- Композиция вместо наследования, эмбеддинг.
- Пакеты и видимость, циклические импорты, internal-пакеты.
- Generics (Go 1.18+): типовые параметры, constraints, когда дженерики уместны, а когда нет.
- Reflection (`reflect`) — на уровне «понимаю как читать, не злоупотребляю».
- Управление памятью: стек vs куча, escape analysis (`go build -gcflags="-m"`).
- Garbage Collector: как работает, что такое STW, как влияет на latency.

**Проект:** библиотека-калькулятор с расширяемыми операциями через интерфейсы + дженерик-контейнеры (`Stack[T]`, `Queue[T]`, `Set[T]`) с покрытием тестами.

**Самопроверка:** разница между интерфейсом-значением и интерфейсом-указателем; покажи escape analysis на коде; нарисуй устройство слайса в памяти.

---

### Этап 3. Конкурентность (3–4 недели) 🟡

Сердце Go. Без неё не возьмут даже на Junior+.

**Что учим:**
- Горутины: как стартовать, цена создания, runtime scheduler (G, M, P).
- Каналы: буферизированные/небуферизированные, направление, `close`, `range`.
- `select` и timeout-паттерны.
- `sync`: Mutex, RWMutex, WaitGroup, Once, Cond, Pool.
- `sync/atomic` — когда atomics, когда mutex.
- `context.Context`: cancellation, deadline, передача значений (только request-scoped!).
- Паттерны: worker pool, fan-in/fan-out, pipeline, semaphore, errgroup.
- Race detector (`go run -race`) — обязательно.

**Проект:** многопоточный crawler/parser сайтов — обходит N URL параллельно, имеет лимит одновременных запросов, корректно отменяется через `context`, собирает результаты без гонок.

**Самопроверка:** объясни «share memory by communicating, not communicate by sharing memory»; напиши rate limiter на каналах; найди race в чужом коде.

---

### Этап 4. Стандартная библиотека (3 недели) 🟢

**Что учим:**
- `net/http` (клиент и сервер), middleware-паттерн.
- `encoding/json`, `encoding/xml`, теги структур, кастомные Marshaler.
- `io`, `bufio`, `os`: чтение/запись, потоки.
- `time`: парсинг, форматирование, тикеры, таймауты.
- `log/slog` (структурированный логгер, стандарт с Go 1.21).
- `flag`, `os/signal`, graceful shutdown.

**Проект:** утилита `httpcheck` — принимает список URL, делает параллельные запросы, выводит таблицу со статусами и временем ответа, поддерживает Ctrl+C для корректного завершения.

---

### Этап 5. Базы данных (3–4 недели) 🟡

**Что учим:**
- SQL отдельно: SELECT, JOIN, GROUP BY, индексы, EXPLAIN, нормализация.
- `database/sql` + драйвер `pgx` для PostgreSQL.
- Транзакции, уровни изоляции, deadlock.
- Миграции: `goose` или `migrate`.
- Query builder `squirrel`, минимально — `sqlc` для генерации кода.
- ORM (`gorm`) — знать, но не злоупотреблять.
- Redis: использование как кэш, очередь, pub/sub через `go-redis`.

**Проект:** REST-сервис «библиотека книг» с CRUD, миграциями, поиском по тексту, пагинацией, кэшем популярных книг в Redis.

**Самопроверка:** покажи N+1 проблему и как её исправить; разница между Read Committed и Repeatable Read.

---

### Этап 6. Web и API (4–6 недель) 🟡

**Что учим:**
- Глубже `net/http`, роутеры: `http.ServeMux` (Go 1.22+), `chi`, `echo`, `gin`.
- Middleware: логирование, recover, CORS, аутентификация.
- JWT, OAuth2, сессии.
- Валидация (`go-playground/validator`).
- gRPC + Protocol Buffers: `.proto`-файлы, кодогенерация, streaming.
- WebSocket (`gorilla/websocket` или `nhooyr.io/websocket`).
- OpenAPI/Swagger, генерация клиентов.

**Проект:** соц-сервис мини-формат: REST + gRPC API, регистрация/логин с JWT, лента постов, чат через WebSocket. Документация в Swagger.

---

### Этап 7. Тестирование (2–3 недели) 🟢

**Что учим:**
- Стандартный `testing`, table-driven tests, subtests, `t.Run`.
- `testify/assert` и `testify/require`.
- Моки: `gomock` или `mockery`.
- Интеграционные тесты с `testcontainers-go` (Postgres/Redis в контейнере).
- HTTP-тесты через `httptest`.
- Бенчмарки (`go test -bench`), профилирование (`pprof`).
- Fuzzing (Go 1.18+).
- Покрытие кода (`go test -cover`).

**Практика:** покрой проект из Этапа 5 на 70%+ unit-тестами и минимум 5 интеграционными.

---

### Этап 8. Микросервисы и сети (6–8 недель) 🟠

**Что учим:**
- Принципы микросервисов: когда нужны, когда вредны.
- Message brokers: Kafka, RabbitMQ, NATS — хотя бы один на практике.
- Паттерны: Saga, Outbox, CQRS, Circuit Breaker, Retry с экспоненциальным backoff.
- Service discovery, API gateway.
- gRPC между сервисами, interceptors.
- Distributed tracing: OpenTelemetry, Jaeger.

**Проект:** мини-маркетплейс из 3–4 сервисов: `users`, `catalog`, `orders`, `notifier`. Коммуникация через gRPC + Kafka. Каждый сервис в своём контейнере.

---

### Этап 9. DevOps минимум (3–4 недели) 🟠

**Что учим:**
- Docker: Dockerfile, multi-stage builds, минимальные образы (distroless, scratch).
- docker-compose для локальной разработки.
- Kubernetes базово: Pod, Deployment, Service, ConfigMap, Secret, Ingress.
- Helm-чарты (читать и базово писать).
- CI/CD: GitHub Actions — линтер, тесты, сборка образа, push в registry.
- Мониторинг: Prometheus + Grafana, метрики через `prometheus/client_golang`.
- Структурированные логи в стиле production.

**Практика:** заверни маркетплейс из Этапа 8 в Docker, разверни в minikube/kind, добавь GitHub Actions с тестами и сборкой.

---

### Этап 10. Архитектура и паттерны (4–6 недель) 🔴

**Что учим:**
- SOLID применительно к Go (без фанатизма).
- Clean Architecture, Hexagonal/Ports & Adapters — критично понимать, когда применять.
- DDD: bounded context, агрегаты, value objects.
- Event-driven architecture, eventual consistency.
- Паттерны Go: functional options, builder, decorator через middleware.
- Антипаттерны: God package, anemic domain, преждевременная абстракция.

**Проект:** перепиши маркетплейс с чистой архитектурой, выдели domain слой, repository интерфейсы, разнеси HTTP- и gRPC-транспорты как адаптеры.

---

### Этап 11. Performance и production (3–4 недели) 🔴

**Что учим:**
- Профилирование: CPU, memory, goroutine, block, mutex profile через `pprof`.
- Бенчмарки и интерпретация результатов, `benchstat`.
- GC tuning: `GOGC`, `GOMEMLIMIT`.
- Оптимизация аллокаций, `sync.Pool`.
- Connection pooling для БД и HTTP.
- Graceful shutdown, health checks, readiness/liveness probes.
- Observability: метрики, логи, трейсы — три кита.

**Практика:** возьми один свой сервис, замеряй RPS через `wrk`/`k6`, найди узкое место через `pprof`, ускорь минимум в 2 раза, опиши процесс в README.

---

### Этап 12. Подготовка к собеседованиям (3 недели) 🟣

**Что учим:**
- Внутренности Go: устройство runtime, GMP-планировщик, GC, memory model.
- Типовые задачи на собесах: rate limiter, worker pool, LRU cache, `sync.Map` своими руками.
- System Design: спроектировать чат, ленту, шортнер ссылок, мессенджер.
- Алгоритмы: 100–150 задач LeetCode (Easy + Medium), упор на массивы, строки, хэш-таблицы, графы.
- Поведенческие вопросы (STAR-метод): рассказы о проектах, конфликтах, сложных решениях.

**Практика:** пройди 5–10 mock-интервью (pramp, друзья-разработчики); запиши свои ответы на видео и пересмотри.

---

## 🚀 Продвинутые этапы (Senior+ / Staff-level)

После Этапа 12 ты уже готов к собесам на Middle/Senior. Дальнейшие этапы — для тех, кто хочет расти в сторону Staff/Principal, идти в Open Source, в распределённые системы или строить инфраструктурные продукты. Не обязательны для трудоустройства, но именно они отделяют «крепкого сеньора» от инженера, который проектирует системы за миллионы запросов в секунду.

---

### Этап 13. Безопасность Go-приложений (3–4 недели) 🔴

**Зачем этап:** в проде security-баги стоят дороже всех остальных. Любой Senior должен уметь читать код через призму «как это сломают».

**Что учим:**
- OWASP Top 10 применительно к Go-веб-сервисам: SQL-инъекции, SSRF, XSS, CSRF, IDOR, deserialization.
- - Безопасная работа с криптографией: `crypto/*`, что использовать, чего избегать (никогда не пиши свой AES).
  - - Хеширование паролей: `bcrypt`, `argon2id`, почему нельзя SHA-256.
    - - TLS: настройка сервера, mTLS между сервисами, ротация сертификатов, Let's Encrypt через `autocert`.
      - - JWT — глубоко: алгоритмы (RS256 vs HS256), атаки `alg=none`, key confusion, JWE.
        - - Secrets management: Vault, AWS Secrets Manager, SOPS, как НЕ хранить секреты в git.
          - - Supply chain security: `go mod verify`, `govulncheck`, проверка зависимостей, SBOM.
            - - Статический анализ: `gosec`, `staticcheck`, `semgrep`-правила для Go.
              - - Rate limiting и защита от DDoS на уровне приложения.
                - - Container security: distroless-образы, non-root user, read-only filesystem, seccomp-профили.
                 
                  - **Проект:** возьми сервис из Этапа 6 и проведи полный security audit: запусти `govulncheck`, `gosec`, добавь rate limiter, перепиши аутентификацию на argon2id + refresh tokens, опиши threat model в `SECURITY.md`.
                 
                  - **Самопроверка:** объясни, почему `time.Now().Unix()` плохой источник случайности для токенов; покажи timing attack на сравнение HMAC и как от неё защищает `hmac.Equal`; нарисуй цепочку доверия TLS.
                 
                  - ---

                  ### Этап 14. Облачные технологии и Cloud-Native Go (4–5 недель) 🟠

                  **Зачем этап:** 80% Go-вакансий — это сервисы в облаке. Уметь нативно работать с AWS/GCP — must-have для Senior.

                  **Что учим:**
                  - AWS SDK for Go v2: S3, DynamoDB, SQS, SNS, Lambda, Secrets Manager.
                  - - GCP / Yandex Cloud SDK — базово, на уровне «прочитал доку и сделал».
                    - - Serverless на Go: AWS Lambda, Cloud Functions, холодный старт, тюнинг бинарника (`-ldflags="-s -w"`, UPX).
                      - - Infrastructure as Code: Terraform — как читать модули, писать ресурсы под свои сервисы, state management.
                        - - Pulumi — IaC прямо на Go (бонусом).
                          - - Service mesh: Istio/Linkerd на уровне «понимаю, что даёт, и могу настроить базовый сценарий».
                            - - Object storage паттерны: presigned URLs, мультипарт-загрузки, lifecycle policies.
                              - - Event-driven архитектура в облаке: SQS+Lambda, EventBridge, Pub/Sub.
                                - - Cost optimization: где утекают деньги в AWS, как мониторить через CloudWatch + Go-метрики.
                                 
                                  - **Проект:** разверни маркетплейс из Этапа 8 в AWS через Terraform: ECS Fargate для сервисов, RDS для БД, ElastiCache Redis, S3 для медиа, SQS для асинхронной обработки заказов, ALB + ACM для HTTPS. Опиши инфраструктуру одной командой `terraform apply`.
                                 
                                  - **Самопроверка:** объясни разницу между SQS Standard и FIFO; покажи, как идемпотентно обработать сообщение из очереди; рассчитай стоимость своего сервиса при 1M RPS в месяц.
                                 
                                  - ---

                                  ### Этап 15. Глубокий runtime и низкий уровень (5–6 недель) 🔴

                                  **Зачем этап:** уровень Staff-инженера и контрибьютора в стандартную библиотеку. Без этого ты пользователь Go, с этим — инженер, который понимает Go насквозь.

                                  **Что учим:**
                                  - Исходники runtime: `runtime/proc.go`, `runtime/mgc.go`, `runtime/chan.go` — читать и понимать.
                                  - - GMP-планировщик глубоко: work stealing, sysmon, preemption (signal-based с 1.14), goroutine parking.
                                    - - Garbage Collector: tri-color mark&sweep, write barriers, как GC влияет на хвост латенси, GOGC vs GOMEMLIMIT в проде.
                                      - - Memory model Go: happens-before, atomics, `sync/atomic.Value`, барьеры памяти.
                                        - - Go assembly (Plan 9 dialect): как читать, когда писать (горячие хот-пути, SIMD через ассемблер).
                                          - - `unsafe`: легальные кейсы, `unsafe.Pointer` правила, `reflect.SliceHeader` (устарел, но знать).
                                            - - cgo: как работает, цена вызова (~200ns), когда стоит, когда нет.
                                              - - Linker и build tags: cross-compile, статическая сборка, `CGO_ENABLED=0`, `-trimpath`.
                                                - - PGO (Profile-Guided Optimization, Go 1.21+) — реальный буст 5–15% на хот-путях.
                                                  - - WebAssembly: компиляция Go в wasm, TinyGo для embedded.
                                                   
                                                    - **Проект:** напиши кастомный `sync.Pool`-подобный объектный пул с lock-free fast path через `atomic`; сравни бенчмарками со стандартным; опиши escape analysis и аллокации в README. Бонус: реализуй one hot-path функцию на Plan 9 assembly и покажи ускорение.
                                                   
                                                    - **Самопроверка:** объясни, почему `for range channel` корректно завершается на `close`; нарисуй жизненный цикл горутины в планировщике; покажи на коде, как происходит escape переменной в кучу и как этого избежать.
                                                   
                                                    - ---

                                                    ### Этап 16. Распределённые системы (6–8 недель) 🔴

                                                    **Зачем этап:** именно здесь рождаются Staff/Principal. Любая большая система — распределённая, и Go — её любимый язык.

                                                    **Что учим:**
                                                    - CAP, PACELC, теорема FLP — на уровне «могу объяснить на собесе и применить в дизайне».
                                                    - - Consensus-алгоритмы: Paxos (на уровне идеи), Raft (глубоко), реализации `hashicorp/raft`, `etcd/raft`.
                                                      - - Распределённые транзакции: 2PC, 3PC, Saga (orchestration vs choreography), Outbox + CDC.
                                                        - - Eventual consistency и CRDT: G-Counter, OR-Set, LWW-Register, библиотека `automerge-go`.
                                                          - - Vector clocks, Lamport timestamps, гибридные логические часы (HLC).
                                                            - - Sharding и партиционирование: hash, range, consistent hashing (`hashicorp/memberlist`).
                                                              - - Репликация: leader-follower, multi-leader, leaderless (Dynamo-style), quorum reads/writes.
                                                                - - Распределённые блокировки: Redlock (и почему его критикуют), etcd, ZooKeeper.
                                                                  - - Gossip-протоколы (SWIM, HashiCorp Serf).
                                                                    - - Книги: «Designing Data-Intensive Applications» (Kleppmann) — прочитать целиком, обязательно.
                                                                     
                                                                      - **Проект:** реализуй упрощённый distributed key-value store на Raft (через `hashicorp/raft`): 3 ноды, leader election, репликация, snapshot, HTTP API для get/put/delete. Прогон через Jepsen-подобный тест на network partitions.
                                                                     
                                                                      - **Самопроверка:** объясни, почему «exactly-once delivery» — это миф, а «exactly-once processing» — реальность; нарисуй split-brain и как от него защищает кворум; покажи, как Saga компенсирует частичный отказ.
                                                                     
                                                                      - ---

                                                                      ### Этап 17. Streaming, Big Data и высоконагруженные пайплайны (4–6 недель) 🟠

                                                                      **Зачем этап:** Go активно используется в data engineering и стриминге — InfluxDB, Prometheus, TimescaleDB, Benthos, ClickHouse-tools написаны на Go.

                                                                      **Что учим:**
                                                                      - Kafka глубоко: партиции, consumer groups, exactly-once semantics, transactions, `franz-go` и `segmentio/kafka-go`.
                                                                      - - Kafka Streams-подобные пайплайны на Go: `benthos`/`bento`, собственные stream processors.
                                                                        - - ClickHouse: запись больших объёмов, batching, асинхронные вставки, `clickhouse-go` v2.
                                                                          - - Time-series данные: TSDB-внутренности, downsampling, retention.
                                                                            - - Колоночные форматы: Parquet, Arrow на Go (`apache/arrow`).
                                                                              - - ETL/ELT пайплайны: idempotency, backfill, replay, exactly-once на чек-поинтах.
                                                                                - - Backpressure-паттерны: bounded buffers, dropping, sampling.
                                                                                  - - NATS JetStream как альтернатива Kafka для Go-native пайплайнов.
                                                                                    - - CDC: Debezium → Kafka → Go consumer, паттерн Outbox.
                                                                                     
                                                                                      - **Проект:** построй real-time аналитический пайплайн: генератор событий → Kafka → Go-consumer с агрегацией в окнах (tumbling/sliding) → ClickHouse → Grafana-дашборд. Нагрузить 100k events/sec и измерить latency p50/p95/p99.
                                                                                     
                                                                                      - **Самопроверка:** объясни разницу between at-least-once, at-most-once и exactly-once; покажи, как ребалансировка consumer group ломает обработку и как с этим жить; нарисуй idempotent consumer.
                                                                                     
                                                                                      - ---

                                                                                      ### Этап 18. Open Source, менторство и инженерный бренд (бессрочно) 🟣

                                                                                      **Зачем этап:** Senior — это не только код. Это влияние, передача знаний и репутация. Этот этап делается параллельно остальным, начиная с Middle.

                                                                                      **Что учим и делаем:**
                                                                                      - Контрибьют в Go-проекты: начни с `good first issue` в `prometheus/prometheus`, `grafana/grafana`, `hashicorp/*`, `kubernetes/kubernetes` (контроллеры на Go).
                                                                                      - - Контрибьют в сам Go: процесс `golang.org/cl`, Gerrit, code review культура Go-команды.
                                                                                        - - Веди свой pet-проект как продукт: README, CONTRIBUTING.md, CI, релизы с semver, CHANGELOG, issue templates, GitHub Discussions.
                                                                                          - - Технические статьи: разбор сложной темы раз в месяц — Habr, Medium, dev.to, личный блог.
                                                                                            - - Публичные выступления: митапы (GoWay, GolangPiter, GopherCon), внутренние tech-talks.
                                                                                              - - Менторство: бери 1–2 джунов, делай code review их pet-проектов, отвечай в чатах сообщества.
                                                                                                - - Чтение чужого кода как практика: раз в неделю разбирай один популярный Go-репозиторий и пиши заметки.
                                                                                                  - - Книги и блоги уровня Senior+: Dave Cheney, Russ Cox, Bryan Mills, Bill Kennedy (ardanlabs).
                                                                                                    - - Английский на уровне «читаю RFC, пишу PR-описания, выступаю на англоязычных митапах».
                                                                                                     
                                                                                                      - **Практика:** замёрджь минимум 3 нетривиальных PR в публичные Go-проекты; собери 100+ звёзд на одном из своих репозиториев; проведи хотя бы один публичный доклад или внутренний tech-talk; стань ментором для 1 джуна и доведи его до первой работы.
                                                                                                     
                                                                                                      - **Самопроверка:** твой GitHub-профиль рассказывает о тебе больше, чем резюме; коллеги пингуют тебя за архитектурным советом; ты можешь объяснить любую тему из этапов 0–17 другому инженеру за 15 минут на whiteboard.
                                                                                                     
                                                                                                      - ---
                                                                                                      
                                                                                                      ## 🎯 Финальная карта роста
                                                                                                      
                                                                                                      | Грейд | Этапы | Срок суммарно | Что умеешь |
                                                                                                      |-------|-------|---------------|------------|
                                                                                                      | 🟢 Junior | 0–4 | 4–6 мес | CRUD API, простые горутины, базовая работа с БД |
                                                                                                      | 🟡 Middle | 5–9 | +6–8 мес | Микросервисы, тесты, Docker/k8s, понимание архитектуры |
                                                                                                      | 🔴 Senior | 10–12 | +6–12 мес | Проектирование систем, performance, ментор для джунов |
                                                                                                      | 🟣 Staff / Principal | 13–18 | +1–2 года | Безопасность, облако, runtime, distributed systems, влияние в сообществе |
                                                                                                      
                                                                                                      Не пытайся пройти всё подряд — после Этапа 12 выбирай 1–2 продвинутых направления под свой контекст работы. Backend-инженеру в финтехе важнее этапы 13 и 16, инженеру в data-платформе — 17, разработчику инфраструктурных тулзов — 15.

---
