# 🚀 Golang Roadmap 2026 — продвинутый курс на русском

![Go](https://img.shields.io/badge/Go-1.23%2B-00ADD8?logo=go&logoColor=white)
![Level](https://img.shields.io/badge/Level-Junior%E2%86%92Staff-success)
![Duration](https://img.shields.io/badge/Duration-12%E2%80%9318%20months-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Lang](https://img.shields.io/badge/Lang-Russian-red)

> **Полная программа для тех, кто хочет в 2026 году писать на Go в продакшене:** от `fmt.Println` до распределённых систем, observability, AI-агентов и масштабирования на миллионы RPS.

---

## 📌 О курсе

Это **бесплатный open-source roadmap** на русском языке. Внутри — 19 модулей, каждый со своей теорией, практикой, бесплатными ресурсами и финальным проектом. Программа собрана так, чтобы провести вас от **полного нуля до уровня Senior/Staff Go Engineer** за 12–18 месяцев при темпе 10–15 часов в неделю.

**Главный принцип курса — практика > видосы.** Каждую тему вы закрываете кодом: пишете, ломаете, чините, рефакторите. Любой модуль завершается мини-проектом, который можно положить в портфолио.

### 🎯 Кому подойдёт
- 🐹 **Новичкам в Go** — даже если до этого писали только на Python/JS/PHP
- 🛠 **Backend-разработчикам** с другого стека — хотите перейти на Go
- 📈 **Junior Go-разработчикам** — нужен путь до Middle/Senior
- 🚀 **Middle-инженерам** — закрыть пробелы в архитектуре, observability, distributed
- 🤖 **Тем, кто хочет писать AI-инфраструктуру** — модуль 18 специально про это

### 💡 Чем этот roadmap отличается
1. **Свежий стек 2026** — generics, fuzzing, structured logging `slog`, OpenTelemetry, eBPF, Wasm, GenAI.
2. **Никаких платных курсов** — только бесплатные ресурсы и официальная документация.
3. **Проект в каждом модуле** — на выходе у вас 19 готовых пет-проектов + 3 крупных капстоуна.
4. **Главный источник новостей по Go в Telegram** — [@Golang_google](https://t.me/Golang_google) и [папка каналов про Go](https://t.me/addlist/MUtJEeJSxeY2YTFi).

---

## 📑 Содержание

- [О курсе](#-о-курсе)
- [Программа курса](#-программа-курса)
- [Подробный разбор модулей](#-подробный-разбор-модулей)
- [Длительность по грейдам](#-длительность-по-грейдам)
- [Как проходить курс](#-как-проходить-курс)
- [Подробный план уроков](#-подробный-план-уроков-по-неделям)
- [Топ бесплатных ресурсов](#-топ-бесплатных-ресурсов)
- [Главный источник новостей по Go](#-главный-источник-новостей-по-go-telegram)
- [Красные флаги — типичные ошибки](#%EF%B8%8F-красные-флаги--типичные-ошибки-которые-тормозят-рост)
- [Лучшие практики Go](#-лучшие-практики-go--разбор-по-темам)
- [3 железных правила](#-3-железных-правила)
- [FAQ](#-faq)

---

## 🗺 Программа курса

### Базовая часть — фундамент языка и инструментов

| № | Модуль | Что внутри | Время |
|---|--------|-----------|-------|
| 00 | **Fundamentals** | Синтаксис, типы, управляющие конструкции, slices, maps, структуры, методы, интерфейсы, ошибки | 3–4 нед |
| 01 | **Tooling & Modules** | `go mod`, `go work`, линтеры, форматтеры, Makefile, Task, CI | 1 нед |
| 02 | **Concurrency** | Горутины, каналы, `select`, `sync`, `context`, race detector, паттерны | 3–4 нед |
| 03 | **Standard Library** | `io`, `os`, `net/http`, `encoding/json`, `time`, `bufio`, `errors`, `slog` | 2–3 нед |
| 04 | **Testing** | Unit, table-driven, fuzzing, benchmarking, моки, integration, testcontainers | 2 нед |
| 05 | **Web & API** | net/http, chi, gin, echo, REST, OpenAPI, валидация, middleware | 3 нед |
| 06 | **Databases** | SQL (PostgreSQL), pgx, sqlc, миграции (goose, atlas), Redis, транзакции | 3 нед |
| 07 | **gRPC & Protobuf** | Protobuf, кодогенерация, streaming, gRPC-Gateway, buf, gRPC reflection | 2 нед |
| 08 | **Architecture** | Clean / Hexagonal / Vertical Slice, DDD-lite, DI без магии (wire/fx) | 3 нед |

### Продвинутая часть — production-ready инженерия

| № | Модуль | Что внутри | Время |
|---|--------|-----------|-------|
| 09 | **Observability** | OpenTelemetry, Prometheus, Grafana, slog, traces, metrics, logs, profiling (pprof) | 2 нед |
| 10 | **Performance** | pprof, escape analysis, GC, бенчмарки, lock-free, sync.Pool, оптимизации памяти | 3 нед |
| 11 | **Security** | OWASP Top 10 для Go, JWT, OAuth2, TLS, secrets management, supply chain (govulncheck) | 2 нед |
| 12 | **Cloud & DevOps** | Docker, Kubernetes, Helm, ArgoCD, IaC (Terraform), GitOps, observability в k8s | 4 нед |
| 13 | **Messaging** | Kafka, NATS, RabbitMQ, outbox pattern, idempotency, sagas | 3 нед |
| 14 | **Distributed Systems** | CAP, consensus (Raft), event sourcing, CQRS, distributed locks, leader election | 4 нед |
| 15 | **Microservices** | service mesh (Istio/Linkerd), API gateway, circuit breaker, bulkhead, retries | 3 нед |
| 16 | **System Design** | Проектирование Twitter/Uber/WhatsApp на Go, capacity planning, шардирование, кэширование | 4 нед |
| 17 | **Advanced Topics** | eBPF, Wasm (`tinygo`), unsafe, plugin, cgo, FFI, Go internals (runtime, scheduler) | 3 нед |
| 18 | **AI & Data Engineering** | LLM-агенты на Go, vector DB, RAG, Ollama, langchaingo, потоковая обработка | 3 нед |

---

## 📚 Подробный разбор модулей

### 00. Fundamentals — фундамент языка
**Что изучаем:** `go run`, `go build`, переменные, типы, zero values, control flow, массивы vs срезы, maps, структуры, методы и receiver-ы, интерфейсы (implicit), ошибки и `errors.Is/As`, `defer`, `panic`/`recover`, generics (1.18+), iterators (1.23+).
**Бесплатные ресурсы:**
- [A Tour of Go](https://go.dev/tour/) — официальный интерактив
- [Effective Go](https://go.dev/doc/effective_go) — обязательно
- [Go by Example](https://gobyexample.com/) — рецепты на каждый день
- [Учебник Ushakov](https://ushakov-school.ru/golang) (бесплатный)
- YouTube: [Nikolay Tuzov — Golang с нуля](https://www.youtube.com/@nikolay_tuzov)
- Книга: [«The Go Programming Language»](https://www.gopl.io/) (Donovan, Kernighan) — главы 1–7
**Проект модуля:** CLI-утилита `gocount` — считает строки/слова/байты в файлах (аналог `wc`).

### 01. Tooling & Modules — экосистема
**Что изучаем:** `go mod init/tidy/why/graph`, `go work`, `replace`, vendoring, версионирование (semver), `golangci-lint`, `gofumpt`, `goimports`, `Taskfile.yml`, `Makefile`, pre-commit hooks, GitHub Actions для Go.
**Бесплатные ресурсы:**
- [Go Modules Reference](https://go.dev/ref/mod)
- [golangci-lint docs](https://golangci-lint.run/)
- [Task — современный Make](https://taskfile.dev/)
- Статья: [Go Workspaces by Robert Griesemer](https://go.dev/blog/get-familiar-with-workspaces)
**Проект модуля:** монорепо с 2 модулями, единый `Taskfile`, CI на GitHub Actions с линтером и тестами.

### 02. Concurrency — то, ради чего идут в Go
**Что изучаем:** горутины, `go`-statement, каналы (buffered/unbuffered), `select`, `for range ch`, `close`, `sync.Mutex/RWMutex`, `sync.WaitGroup`, `sync.Once`, `sync.Pool`, `atomic`, `context.Context` (cancel/timeout/value), race detector (`go run -race`), паттерны: worker pool, fan-in/fan-out, pipeline, semaphore, errgroup.
**Бесплатные ресурсы:**
- [Go Concurrency Patterns (Pike)](https://go.dev/blog/pipelines)
- Книга: [«Concurrency in Go» Katherine Cox-Buday](https://katherine.cox-buday.com/concurrency-in-go/) (главы в открытом доступе)
- [Курс Concurrency in Go — Ardan Labs](https://github.com/ardanlabs/gotraining) (open-source)
- YouTube: [Бакалавр Computer Science — конкурентность](https://www.youtube.com/@bbc_ru)
**Проект модуля:** многопоточный краулер сайтов с rate limiting, retries и graceful shutdown.

### 03. Standard Library — золото стандартной библиотеки
**Что изучаем:** `io.Reader/Writer` идиомы, `bufio`, `os` (env, signals, fs), `net/http` сервер и клиент, `encoding/json` + кастомные `MarshalJSON`, `encoding/xml`, `time` (часовые пояса, monotonic), `errors` (wrap, unwrap), `log/slog` (1.21+) — structured logging.
**Бесплатные ресурсы:**
- [pkg.go.dev/std](https://pkg.go.dev/std) — официальная документация
- [Go Blog — slog tutorial](https://go.dev/blog/slog)
- Статьи: [Dave Cheney — practical Go](https://dave.cheney.net/practical-go)
**Проект модуля:** HTTP-сервис-агрегатор RSS с structured logging через `slog`.

### 04. Testing — без тестов в прод не пускаем
**Что изучаем:** `testing.T`, table-driven tests, subtests, `t.Parallel()`, fuzzing (`testing.F`), benchmarking (`testing.B`), coverage, golden files, моки (gomock, mockery, testify/mock), `httptest`, `iotest`, integration через [testcontainers-go](https://golang.testcontainers.org/).
**Бесплатные ресурсы:**
- [Go Testing — официальный туториал](https://go.dev/doc/tutorial/add-a-test)
- [Learn Go with Tests](https://quii.gitbook.io/learn-go-with-tests/) — лучший бесплатный курс TDD на Go
- [Go Fuzzing](https://go.dev/security/fuzz/)
**Проект модуля:** библиотека для парсинга промокодов с 95%+ покрытием, fuzz-тестами и benchmark-ами.

### 05. Web & API — REST и HTTP-сервисы
**Что изучаем:** `net/http` + ServeMux (1.22+), роутеры [chi](https://github.com/go-chi/chi), [gin](https://gin-gonic.com/), [echo](https://echo.labstack.com/), middleware (auth, recover, rate limit, CORS), валидация ([go-playground/validator](https://github.com/go-playground/validator)), OpenAPI 3 ([oapi-codegen](https://github.com/oapi-codegen/oapi-codegen)), `huma`, `fiber`, graceful shutdown, server-timing, SSE и WebSocket.
**Бесплатные ресурсы:**
- [Alex Edwards — Let's Go (book, бесплатные главы)](https://lets-go.alexedwards.net/sample/)
- [chi docs](https://go-chi.io/)
- [OpenAPI Generator for Go](https://openapi-generator.tech/docs/generators/go/)
**Проект модуля:** REST API `linkshrt` (аналог bit.ly) с auth, rate-limit, OpenAPI и Docker.

### 06. Databases — данные навсегда
**Что изучаем:** `database/sql`, [pgx](https://github.com/jackc/pgx), [sqlc](https://sqlc.dev/), [squirrel](https://github.com/Masterminds/squirrel), миграции ([goose](https://github.com/pressly/goose), [atlas](https://atlasgo.io/)), индексы, `EXPLAIN ANALYZE`, транзакции и уровни изоляции, connection pool, [go-redis](https://github.com/redis/go-redis), кэширование (cache-aside, write-through), [ent](https://entgo.io/) и [bun](https://bun.uptrace.dev/).
**Бесплатные ресурсы:**
- [Use the Database Slow Query Log](https://wiki.postgresql.org/wiki/Logging_Difficult_Queries)
- [pgx tutorial](https://github.com/jackc/pgx/wiki)
- [PostgreSQL для разработчика — Postgres Pro (RU)](https://postgrespro.ru/education/books)
**Проект модуля:** сервис подписок с PostgreSQL (sqlc) + Redis (idempotency keys) + миграциями.

### 07. gRPC & Protobuf — межсервисные коммуникации
**Что изучаем:** protobuf 3, `buf` CLI, кодогенерация (`protoc-gen-go`, `protoc-gen-go-grpc`), unary/server-stream/client-stream/bidi-stream, deadlines, interceptors, [grpc-gateway](https://grpc-ecosystem.github.io/grpc-gateway/), reflection, [connect-go](https://connectrpc.com/), [twirp](https://twitchtv.github.io/twirp/).
**Бесплатные ресурсы:**
- [gRPC Basics — официальный туториал](https://grpc.io/docs/languages/go/basics/)
- [Buf docs](https://buf.build/docs/introduction)
- YouTube: [gRPC + Go — TechSchool](https://www.youtube.com/playlist?list=PLy_6D98if3ULEtXtNSY_2qN21VCKgoQAE)
**Проект модуля:** микросервис `user-svc` + `order-svc` через gRPC streaming, REST-фасад через gRPC-Gateway.

### 08. Architecture — пишем код, который не стыдно
**Что изучаем:** Clean Architecture, Hexagonal (ports & adapters), Vertical Slice, DDD-lite (entity, value object, repository, aggregate), DI без магии ([wire](https://github.com/google/wire), [fx](https://github.com/uber-go/fx)), функциональные опции, error wrapping стратегии, layered конфиг ([viper](https://github.com/spf13/viper), [koanf](https://github.com/knadh/koanf)).
**Бесплатные ресурсы:**
- [go-clean-template — Evrone](https://github.com/evrone/go-clean-template)
- [Standard Go Project Layout](https://github.com/golang-standards/project-layout) (с оговорками)
- Статьи: [Three Dots Labs — Wild Workouts](https://threedots.tech/post/introducing-clean-architecture/)
**Проект модуля:** рефакторинг проекта модуля 05 в чистую архитектуру + DI через wire.

### 09. Observability — без неё в проде слепой
**Что изучаем:** [OpenTelemetry для Go](https://opentelemetry.io/docs/languages/go/), structured logging (`slog` + correlation id), traces (Jaeger/Tempo), metrics (Prometheus), `pprof` через HTTP, `expvar`, dashboards в Grafana, алёрты в Alertmanager, log levels стратегия.
**Бесплатные ресурсы:**
- [OpenTelemetry Go SDK docs](https://opentelemetry.io/docs/languages/go/getting-started/)
- [Prometheus client_golang examples](https://github.com/prometheus/client_golang/tree/main/examples)
- [Grafana University (бесплатно)](https://grafana.com/about/team/grafanauniversity/)
**Проект модуля:** добавить полную observability к сервисам из 07: traces + metrics + structured logs + Grafana дашборд.

### 10. Performance — Go быстрый, но не сам собой
**Что изучаем:** `go test -bench`, `benchstat`, `pprof` (cpu, mem, goroutine, mutex, block), escape analysis (`-gcflags='-m'`), GOGC и GOMEMLIMIT (1.19+), `sync.Pool`, lock-free структуры, false sharing, prealloc slice/map, string interning, [PGO](https://go.dev/doc/pgo) (Profile-Guided Optimization).
**Бесплатные ресурсы:**
- [High Performance Go Workshop — Dave Cheney](https://dave.cheney.net/high-performance-go-workshop/dotgo-paris.html)
- [Go Performance Tuning — Bartosz Mika](https://github.com/dgryski/go-perfbook)
- [pprof tutorial — Julia Evans](https://jvns.ca/blog/2017/09/24/profiling-go-with-pprof/)
**Проект модуля:** оптимизировать REST API из модуля 05 — поднять RPS в 5–10 раз через профилирование.

### 11. Security — безопасность в Go
**Что изучаем:** OWASP Top 10 в контексте Go, JWT (RS256 vs HS256), OAuth2 / OIDC, TLS (mTLS), `crypto/*`, secrets management (Vault, SOPS), supply chain attacks, [govulncheck](https://go.dev/blog/govulncheck), [gosec](https://github.com/securego/gosec), CSRF, SQL injection, SSRF, RCE через unsafe deserialization.
**Бесплатные ресурсы:**
- [OWASP Go Secure Coding Practices](https://github.com/OWASP/Go-SCP)
- [Go Security Best Practices — Snyk](https://snyk.io/learn/go-security/)
- [govulncheck blog post](https://go.dev/blog/govulncheck)
**Проект модуля:** аудит безопасности проекта 05/08, внедрение JWT + mTLS между сервисами + govulncheck в CI.

### 12. Cloud & DevOps — куда деплоиться
**Что изучаем:** multi-stage `Dockerfile` (distroless), Docker Compose, Kubernetes (Pod/Deployment/Service/Ingress/ConfigMap/Secret), Helm charts, Kustomize, ArgoCD, Terraform для облака (AWS/GCP/Yandex), GitOps workflow, kubectl мастерство.
**Бесплатные ресурсы:**
- [Kubernetes Up & Running — free chapters](https://www.oreilly.com/library/view/kubernetes-up-and/9781098110192/)
- [Learn Kubernetes the Hard Way (Kelsey Hightower)](https://github.com/kelseyhightower/kubernetes-the-hard-way)
- [Helm docs](https://helm.sh/docs/)
- YouTube: [TechWorld with Nana — Kubernetes](https://www.youtube.com/@TechWorldwithNana)
**Проект модуля:** деплой 3-сервисов из модуля 09 в Kubernetes (kind/minikube) + Helm + ArgoCD.

### 13. Messaging — асинхронные коммуникации
**Что изучаем:** [Kafka](https://github.com/twmb/franz-go) (партиции, оффсеты, consumer groups, exactly-once), [NATS](https://nats.io/) (Core, JetStream, KV), RabbitMQ, outbox pattern, idempotency keys, retries с backoff, dead letter queue, sagas (orchestration vs choreography), event-driven архитектура.
**Бесплатные ресурсы:**
- [Kafka: The Definitive Guide — free O'Reilly](https://www.confluent.io/resources/kafka-the-definitive-guide-v2/)
- [NATS by Example](https://natsbyexample.com/)
- Watermill — [фреймворк для event-driven Go](https://watermill.io/)
**Проект модуля:** order-saga через NATS JetStream + outbox table в PostgreSQL.

### 14. Distributed Systems — теория и боль
**Что изучаем:** CAP, PACELC, consistency models (linearizable, sequential, eventual), Raft / Paxos (на уровне понимания), distributed locks ([etcd](https://etcd.io/), Redis Redlock), leader election, vector clocks, event sourcing + CQRS, Two-Generals, Byzantine fault tolerance (basics).
**Бесплатные ресурсы:**
- Книга [«Designing Data-Intensive Applications»](https://dataintensive.net/) (Kleppmann) — обязательно
- [MIT 6.824 Distributed Systems](https://pdos.csail.mit.edu/6.824/) — лекции бесплатно
- [The Raft paper](https://raft.github.io/raft.pdf) + [interactive visualisation](https://raft.github.io/)
**Проект модуля:** свой mini key-value store с Raft (на базе [hashicorp/raft](https://github.com/hashicorp/raft)) на 3 нодах.

### 15. Microservices — оркестрация и устойчивость
**Что изучаем:** service mesh (Istio, Linkerd), API Gateway (KrakenD, Kong), circuit breaker ([sony/gobreaker](https://github.com/sony/gobreaker)), retries, timeouts, bulkhead, [resilience-go](https://github.com/slok/goresilience), feature flags (Unleash), blue-green / canary deploys, contract testing (Pact).
**Бесплатные ресурсы:**
- [microservices.io patterns — Chris Richardson](https://microservices.io/patterns/)
- [Istio docs](https://istio.io/latest/docs/)
- [Release It! — Michael Nygard](https://pragprog.com/titles/mnee2/release-it-second-edition/) (главы в открытом доступе)
**Проект модуля:** добавить circuit breaker, retries, timeouts в проект 09; canary deploy через ArgoCD.

### 16. System Design — как собеседуют на Senior
**Что изучаем:** capacity planning (back-of-envelope), CDN, шардирование, репликация (sync vs async), кэширование (LRU, LFU, TinyLFU), очереди, consistent hashing, gossip protocols, geo-replication, multi-tenancy, мульти-регион, RTO/RPO.
**Бесплатные ресурсы:**
- [System Design Primer](https://github.com/donnemartin/system-design-primer) — must-have
- [ByteByteGo (бесплатные посты)](https://blog.bytebytego.com/)
- YouTube: [Hussein Nasser](https://www.youtube.com/@hnasser)
**Проект модуля:** письменный системный дизайн Twitter-clone на Go (можно как ADR-документ в репо).

### 17. Advanced Topics — внутрь Go
**Что изучаем:** Go runtime (GMP scheduler), garbage collector (tri-color, write barriers), `unsafe` (когда оправдано), `cgo` (и почему лучше без него), [tinygo](https://tinygo.org/) для Wasm и embedded, eBPF на Go ([cilium/ebpf](https://github.com/cilium/ebpf)), `plugin`, [Wazero](https://wazero.io/) для запуска Wasm на сервере.
**Бесплатные ресурсы:**
- [Go internals — Bartosz Mika](https://github.com/teh-cmc/go-internals)
- [Go scheduler — Ardan Labs deep dive](https://www.ardanlabs.com/blog/2018/08/scheduling-in-go-part1.html)
- [eBPF Tutorial — Cilium](https://docs.cilium.io/en/stable/bpf/)
**Проект модуля:** eBPF-программа на Go, считающая TCP-соединения по PID.

### 18. AI & Data Engineering — Go в 2026 ещё и про AI
**Что изучаем:** [Ollama](https://ollama.com/) клиент на Go, [langchaingo](https://github.com/tmc/langchaingo), RAG (Retrieval Augmented Generation), vector databases (pgvector, Qdrant, Weaviate), streaming-обработка ([benthos](https://www.benthos.dev/)), embeddings, function calling, MCP-серверы на Go.
**Бесплатные ресурсы:**
- [langchaingo examples](https://github.com/tmc/langchaingo/tree/main/examples)
- [Building LLM apps with Go — Eli Bendersky](https://eli.thegreenplace.net/tag/golang)
- [Qdrant Go SDK quickstart](https://qdrant.tech/documentation/quick-start/)
**Проект модуля:** RAG-чат-бот по документации Go (pgvector + Ollama + langchaingo + gRPC API).

---

## ⏱ Длительность по грейдам

| Цель | Срок | Часов в неделю | Что закрываем |
|------|------|----------------|---------------|
| 🟢 **Junior Go** | 3–4 мес | 10–15 | Модули 00–06 |
| 🟡 **Middle Go** | 7–9 мес | 12–18 | Модули 00–12 |
| 🟠 **Senior Go** | 12–14 мес | 15–20 | Модули 00–16 |
| 🔴 **Staff / Principal** | 16–18 мес | 20+ | Все 19 модулей + участие в open-source |

> Это не дедлайны, а ориентиры. Кто-то проходит за 8 месяцев, кто-то за 2 года — оба варианта норма.

---

## 🧭 Как проходить курс

1. **Установите Go 1.23+** с [go.dev/dl](https://go.dev/dl/) и настройте `gopls` в редакторе.
2. **Клонируйте репозиторий** — внутри `/course` лежат markdown-файлы по каждому модулю.
3. **Идите по порядку** — модули зависят друг от друга. Перепрыгивать опасно.
4. **Не смотрите видосы пассивно** — открыли видео → пишете тот же код параллельно.
5. **Делайте проект каждого модуля** — без проекта модуль не считается пройденным.
6. **Ведите блог-конспект** — хоть в `/notes` репозитория. Объяснил себе → понял.
7. **Подпишитесь на [@Golang_google](https://t.me/Golang_google)** — там разбирают свежие фичи Go и вакансии.

### 📆 Рекомендованный ритм недели

| День | Активность | Время |
|------|-----------|-------|
| Пн | Теория модуля (книга/статья) | 1.5–2 ч |
| Вт | Практика: примеры из туториала | 2 ч |
| Ср | Теория + видос | 1.5 ч |
| Чт | Своя имплементация | 2 ч |
| Пт | Тесты + рефакторинг | 1.5 ч |
| Сб | Работа над проектом модуля | 3–4 ч |
| Вс | Чтение исходников, ревью, отдых | 1 ч |

---

## 🧪 Подробный план уроков по неделям

Здесь — расширенный план первого квартала (модули 00–04). Полные планы остальных модулей лежат в `/course/<NN>-*.md`.

### Модуль 00 — Fundamentals (3–4 недели)

#### Неделя 1 — синтаксис и типы
- **Урок 1.1** «Hello, World правильно». Установка Go, GOPATH vs go modules, `go run`, `go build`, кросс-компиляция. Практика: написать 5 версий hello — с аргументами, env-переменными, stdin, JSON-выводом, exit codes.
- **Урок 1.2** Скалярные типы и литералы. Числа (int vs int64), string vs []byte, rune, typed/untyped константы, `iota`. Практика: калькулятор BMI с обработкой некорректного ввода.
- **Урок 1.3** Управление потоком. `if`, `for` (3 формы), `switch` (type switch), `goto` (зачем?). Практика: FizzBuzz, реализованный 4 разными способами; решение задачек с [Exercism Go track](https://exercism.org/tracks/go).
- **Урок 1.4** Функции, multiple return, named returns, variadic, замыкания. Практика: набор функций для статистики ([]float64 → mean, median, mode, stdev).

#### Неделя 2 — коллекции и память
- **Урок 2.1** Массивы vs слайсы: длина, capacity, underlying array, `append` подводные камни, копирование. Практика: реализовать свой `Stack` и `Queue` на слайсах с тестами.
- **Урок 2.2** Maps: zero value, iteration order, `delete`, конкурентный доступ. Практика: word-frequency counter, читающий большой текст и выдающий топ-N слов.
- **Урок 2.3** Strings, runes, UTF-8, `strings.Builder`, `bytes.Buffer`. Практика: транслитерация русский ↔ латиница.
- **Урок 2.4** Pointers, value vs pointer receivers, когда копирование вредит. Практика: бенчмарк big-struct value vs pointer.

#### Неделя 3 — структуры, методы, интерфейсы
- **Урок 3.1** `struct`, теги (json, db, validate), embedding (composition over inheritance). Практика: модель `Order` с JSON-сериализацией и валидацией.
- **Урок 3.2** Методы, value vs pointer receivers, method sets. Практика: тип `Money` с безопасной арифметикой (без float).
- **Урок 3.3** Интерфейсы — implicit, пустой интерфейс, type assertion, type switch, `io.Reader/Writer` идиома. Практика: написать свой `io.Reader`, который сжимает строку в gzip on-the-fly.
- **Урок 3.4** Errors как values: `errors.New`, `fmt.Errorf("%w", ...)`, `errors.Is/As`, sentinel vs typed vs opaque ошибки. Практика: библиотека парсинга конфига с собственными типами ошибок.

#### Неделя 4 — продвинутое и проект
- **Урок 4.1** `defer`, `panic`, `recover` — паттерны и анти-паттерны.
- **Урок 4.2** Generics (1.18+): type parameters, constraints, `comparable`, `any`. Практика: написать generic `Filter`, `Map`, `Reduce`.
- **Урок 4.3** Iterators (1.23+) — `range over func`. Практика: переписать word-counter из 2.2 как iterator.
- **Финальный проект:** CLI-утилита `gocount` — flags, чтение stdin/файлов, glob, бенчмарк против системного `wc`. Покрытие тестами ≥ 80%.

### Модуль 01 — Tooling & Modules (1 неделя)
- **Урок 1** `go mod` под микроскопом: версии, replace, retract, minimum version selection.
- **Урок 2** `go work` и монорепо.
- **Урок 3** Линтеры: `golangci-lint` конфиг для prod-проекта, `gofumpt`, `gci`, `betteralign`.
- **Урок 4** Taskfile.yml vs Makefile; pre-commit hooks (lefthook).
- **Урок 5** GitHub Actions workflow для Go (matrix Go-версий, cache, codecov).
- **Финальный проект:** монорепо-шаблон со всем настроенным CI и pre-commit.

### Модуль 02 — Concurrency (3–4 недели)

#### Неделя 1 — основы
- **Урок 1** Горутины: стек, цена создания, GMP-модель в общих чертах.
- **Урок 2** Каналы: buffered vs unbuffered, направление, close, range, nil-channel паттерн.
- **Урок 3** `select` и таймауты, default-ветка, идиома `done`-channel.
- **Урок 4** Race detector в действии: пишем код с гонкой, ловим её `-race`.

#### Неделя 2 — sync и context
- **Урок 5** `sync.Mutex/RWMutex`: когда RW даёт выигрыш, deadlock-стратегии.
- **Урок 6** `sync.WaitGroup`, `sync.Once`, `sync.Pool` (когда вредит).
- **Урок 7** `atomic` и lock-free счётчики; happens-before.
- **Урок 8** `context.Context` — cancel, timeout, deadline, value (и почему value лучше избегать).

#### Неделя 3 — паттерны
- **Урок 9** Worker pool с back-pressure.
- **Урок 10** Pipeline + fan-in/fan-out.
- **Урок 11** errgroup, semaphore, singleflight.
- **Урок 12** Graceful shutdown сервиса: signal → ctx.Done → wait → exit.

#### Неделя 4 — проект
- **Финальный проект:** многопоточный web-crawler с rate limit на хост, depth limit, retries (exponential backoff), persisting в BoltDB, graceful shutdown по `SIGTERM`.

### Модуль 03 — Standard Library (2–3 недели)
- **Урок 1** `io.Reader/Writer` композиция: `TeeReader`, `MultiReader`, `LimitReader`.
- **Урок 2** `bufio` правильно: Scanner-ловушки на длинных строках.
- **Урок 3** `os`: env, signals, process management, file system.
- **Урок 4** `net/http` server: ServeMux 1.22+, middleware-цепочки, server timeouts.
- **Урок 5** `net/http` client: transport, retries, connection pooling, timeouts ВЕЗДЕ.
- **Урок 6** `encoding/json` глубже: `json.Decoder` стримом, custom Marshal/Unmarshal, `omitempty`-нюансы.
- **Урок 7** `time` без боли: zones, monotonic clock, mock-абстракции для тестов.
- **Урок 8** `log/slog` (1.21+) — handlers, attributes, source, context.
- **Финальный проект:** RSS-агрегатор с structured logging, retries, graceful shutdown.

### Модуль 04 — Testing (2 недели)
- **Урок 1** `testing.T` + subtests + table-driven (с `t.Run`).
- **Урок 2** `t.Parallel()`, `t.Cleanup()`, helper functions.
- **Урок 3** Моки: testify/mock, gomock, mockery — pros/cons.
- **Урок 4** `httptest.Server` + `httptest.ResponseRecorder`.
- **Урок 5** Integration tests через [testcontainers-go](https://golang.testcontainers.org/) (Postgres, Redis в Docker).
- **Урок 6** Fuzzing (`testing.F`) — пишем и находим реальный баг.
- **Урок 7** Benchmarks + `benchstat` для сравнения.
- **Финальный проект:** библиотека парсинга промокодов с 95% coverage, fuzz-найденными багами и benchmark-сравнением 2 реализаций.

> Полные планы по модулям 05–18 — в `/course/05-web.md` ... `/course/18-ai-data.md`. Каждый файл уже содержит конкретные уроки, ссылки и проектные задания.

---

## 🌟 Топ бесплатных ресурсов

### Книги
- **A Tour of Go** — [go.dev/tour](https://go.dev/tour)
- **Effective Go** — [go.dev/doc/effective_go](https://go.dev/doc/effective_go)
- **Learn Go with Tests** — [quii.gitbook.io](https://quii.gitbook.io/learn-go-with-tests/)
- **The Go Programming Language** (главы доступны, образцы — gopl.io)
- **Designing Data-Intensive Applications** — Kleppmann (для модулей 13–16)
- **Concurrency in Go** — Cox-Buday (главы 1–3 в открытом доступе)

### Видеокурсы и YouTube
- [Nikolay Tuzov — Golang с нуля](https://www.youtube.com/@nikolay_tuzov) (RU)
- [Ardan Labs Ultimate Go](https://github.com/ardanlabs/gotraining) (EN, open-source)
- [TechSchool — Go + gRPC](https://www.youtube.com/@TechSchoolGuru)
- [JustForFunc — Francesc Campoy](https://www.youtube.com/c/JustForFunc) (EN)
- [Anthony GG — Go projects](https://www.youtube.com/@anthonygg_) (EN)

### Практика и задачи
- [Exercism Go track](https://exercism.org/tracks/go) — задачки с ментором
- [Gophercises](https://gophercises.com/) — 20 пет-проектов
- [Go by Example](https://gobyexample.com/) — рецепты
- [Project Euler на Go](https://projecteuler.net/) — алгоритмы
- [Advent of Code](https://adventofcode.com/) на Go

### Блоги и newsletters
- [Dave Cheney — practical Go](https://dave.cheney.net/)
- [Eli Bendersky](https://eli.thegreenplace.net/tag/golang)
- [Three Dots Labs](https://threedots.tech/)
- [Go Weekly](https://golangweekly.com/)
- Telegram: [@Golang_google](https://t.me/Golang_google) — главный русскоязычный канал

### Документация и спецификации
- [pkg.go.dev/std](https://pkg.go.dev/std) — стандартная библиотека
- [Go Language Specification](https://go.dev/ref/spec) — обязательно к прочтению на уровне Middle+
- [Go Memory Model](https://go.dev/ref/mem) — для модуля 02

---

## 📱 Главный источник новостей по Go (Telegram)

Если вы пишете на Go в 2026 — подпишитесь, это сэкономит часы поиска:

- 🥇 **[@Golang_google](https://t.me/Golang_google)** — главный русскоязычный канал по Go. Свежие фичи, статьи, разбор PR в Go core, вакансии Middle/Senior, мемы. Это первое, что должно быть в подписках.
- 📂 **[Папка Telegram «Go-ресурсы»](https://t.me/addlist/MUtJEeJSxeY2YTFi)** — собранная коллекция каналов: новости, чаты по Go, вакансии, материалы для собесов. Добавляется одной кнопкой.

Дополнительно стоит мониторить:
- [Gophers Slack](https://invite.slack.golangbridge.org/) — англоязычное community №1, есть канал `#russian`
- [r/golang](https://www.reddit.com/r/golang/) — субреддит
- [Hacker News tag golang](https://hn.algolia.com/?q=golang)

---

## ⚠️ Красные флаги — типичные ошибки, которые тормозят рост

Это вещи, которые на каждом ревью встречаются у Junior/Middle и тормозят повышение грейда. Если узнаёте себя — пересоберите подход.

1. **«Я смотрю курс, но не пишу код».** Пассивный просмотр видосов не даёт навыка. Правило: каждые 10 минут видео → 20 минут самостоятельной практики.
2. **Игнорирование `go vet`, `golangci-lint` и race detector.** Если запускаете тесты без `-race` — вы ловите гонки в проде, а не локально.
3. **Прятать ошибки через `_`.** `f, _ := os.Open(...)` — классика. В Go ошибки — часть контракта функции, их обрабатывают, а не глотают.
4. **Делать всё через интерфейсы «на всякий случай».** Интерфейс пишется на стороне потребителя и только когда есть ≥ 2 реализации. Преждевременная абстракция — главный анти-паттерн в Go.
5. **Goroutine без `context` и без `WaitGroup`/`errgroup`.** Любая горутина, которая не умеет завершаться по сигналу — потенциальная утечка.
6. **`panic` вместо ошибки.** `panic` — только для невосстановимых ситуаций (битый инвариант), не для «не нашёл юзера в БД».
7. **Один большой `pkg/utils`.** Признак отсутствия архитектуры. Разносите по доменным пакетам.
8. **Глобальные переменные и init-магия.** Усложняет тесты, делает порядок инициализации непредсказуемым.
9. **Тесты только на happy path.** Edge cases, ошибочные пути, конкурентность — без них тест бесполезен.
10. **«У меня нет времени на pprof / OpenTelemetry».** На Senior без observability и профилирования не берут. Закладывайте их в проект с первого коммита.
11. **Копипаста из ChatGPT/Copilot без понимания.** AI — помощник, не автор. Если не можете объяснить каждую строку — переписывайте.
12. **Перестали читать стандартную библиотеку.** Исходники `net/http`, `sync`, `context` — лучший учебник по идиомам Go.
13. **Игнор `slog`, тащат `logrus`/`zap` в новые проекты.** С 1.21+ структурное логирование есть в стандартной библиотеке. Используйте.
14. **Не знают, что такое escape analysis.** На Middle+ это базовый инструмент оптимизации.
15. **Отказ от собеседований «пока не готов».** Собеседования — лучший фидбек. Идите даже если не готовы — узнаете, что качать.

---

## 💎 Лучшие практики Go — разбор по темам

Это сборник идиом и инженерных правил, которые отличают код Junior от кода Senior. Каждый пункт — то, что вы будете слышать на ревью в любой нормальной Go-команде.

### 🧱 Структура кода и пакеты
- **Имена пакетов — короткие, нижний регистр, без подчёркиваний**: `user`, `auth`, `httputil`. Никаких `user_service` или `userService`. Пакет `utils` / `common` / `helpers` — запах, режьте по доменам.
- **Пакет — это API**. Экспортируйте минимум: `MarshalJSON` — да, внутренний `parseHeader` — нет. Чем меньше публичная поверхность, тем проще менять реализацию.
- **Не делайте циклические импорты**. Если возникает желание — значит, домен разрезан неправильно. Выносите общие типы в отдельный пакет (`domain`, `model`) или объединяйте.
- **Файлы внутри пакета группируйте по фиче, а не по типу**. `user_repository.go`, `user_service.go` — лучше, чем `models.go`, `services.go`, `repositories.go`.
- **`internal/` — ваш друг**. Всё, что не должно импортироваться извне модуля, кладите в `internal/`. Go-компилятор сам запретит.
- **Не плодите подпакеты раньше времени**. Один файл — нормально. Разделение на пакеты делайте, когда видно границу ответственности.

### ✍️ Стиль и именование
- **Соблюдайте `gofmt`/`gofumpt`**. Споров о стиле в Go нет — есть инструмент. Поставьте в pre-commit hook.
- **Короткие имена в коротком скоупе, длинные — в широком**. `i` в цикле — норма; `userRepositoryFactory` в пакете `user` — избыточно (просто `Factory`).
- **Аббревиатуры пишем единым регистром**: `userID`, `HTTPServer`, `URLParser`. Не `userId` и не `HttpServer`.
- **Getter без `Get`**: `u.Name()`, не `u.GetName()`. Setter — с `Set`: `u.SetName(...)`.
- **Имя интерфейса = действие + `er`**: `Reader`, `Writer`, `Closer`, `Stringer`. Интерфейс с одним методом — особенно ценный.
- **Receiver — короткий и консистентный**: `u *User`, не `this`, не `self`, не `user`. И во всех методах одинаковый.

### 🧯 Обработка ошибок
- **Ошибка — это значение**. Возвращайте, проверяйте, оборачивайте. Никаких исключений.
- **Оборачивайте с контекстом**: `fmt.Errorf("create user: %w", err)`. Цепочка `%w` позволяет потом `errors.Is/As`.
- **Не логируйте и не возвращайте одновременно**. Логирует только тот, кто решил, что ошибка обработана. Иначе одна ошибка превращается в три записи в логе.
- **Sentinel-ошибки — для известных ситуаций**: `var ErrNotFound = errors.New("not found")`. Сравнение через `errors.Is`.
- **Типизированные ошибки — когда нужны детали**: `type ValidationError struct { Field, Msg string }`. Сравнение через `errors.As`.
- **Не сравнивайте через `err.Error() == "..."`** — это хрупкая привязка к тексту.
- **`panic` только для невосстановимого**: битый инвариант, невозможная ветка, init-ошибка. Бизнес-ошибки — `return err`.
- **`defer` с проверкой ошибки**: `defer func() { if cerr := f.Close(); cerr != nil { err = errors.Join(err, cerr) } }()` — особенно для `Close` на записи.

### 🌀 Конкурентность
- **Don't communicate by sharing memory; share memory by communicating** — классическая мантра. Но если канал тащить не надо — `sync.Mutex` чище.
- **Любая горутина должна знать, как умереть**. `context.Context` или `done`-канал — обязательно. Иначе утечка.
- **Не запускайте `go f()` в библиотечных функциях**, если не задокументировали это. Управление горутиной — ответственность вызывающего.
- **`context.Context` — первый параметр** функции, имя `ctx`. Не храните в struct (кроме особых случаев типа request-scoped объектов).
- **Не передавайте `*sync.Mutex` по значению** — копируется состояние блокировки. Используйте указатель или встраивайте по значению в структуру (она тоже не должна копироваться — `go vet` подскажет).
- **`sync.WaitGroup.Add` — до `go`**, не внутри горутины. Иначе race.
- **`errgroup` вместо ручного WaitGroup**, когда нужна агрегация ошибок и cancel при первой.
- **`sync.Pool` — только для дорогих объектов**, которые реально переиспользуются. На мелочи даёт минус.
- **Buffered channel `size = N` — это не оптимизация**, это бэк-прешер на N сообщений. Думайте про это как про очередь.
- **Закрывает канал только отправитель**. Получатель — никогда. Иначе `send on closed channel` panic.
- **Всегда тестируйте с `-race`**. Локально, в CI, в pre-merge — везде.

### 🧩 Интерфейсы и дизайн
- **Accept interfaces, return structs**. Параметры — узкие интерфейсы (`io.Reader`), возврат — конкретный тип. Так клиенту проще, чем гадать, что прячется за интерфейсом.
- **Маленькие интерфейсы лучше больших**. `io.Reader` (1 метод) переиспользуется тысячами библиотек. `Repository` с 15 методами — нет.
- **Интерфейсы определяет потребитель, не реализатор**. Не пишите `UserRepository` в пакете `user` и не реализуйте его там же. Пакет `service` сам объявит, что ему нужно от хранилища.
- **`any` (он же `interface{}`) — крайнее средство**. С generics 1.18+ почти всегда есть лучше.
- **Не делайте `Service` god-object**. Если структура зависит от 10 интерфейсов — она делает слишком много.

### 🧪 Тестирование
- **Table-driven tests — стандарт de facto**. Один цикл, понятный diff, легко добавлять кейсы.
- **`t.Parallel()` в каждом тесте, где можно**. Catch race conditions раньше + быстрее CI.
- **`t.Cleanup()` вместо `defer`** — корректнее работает с параллельными подтестами.
- **Не моки ради моков**. Моким то, что выходит за процесс (DB, HTTP, gRPC). Чистые функции моками не покрывают — это превращает тест в проверку реализации, а не поведения.
- **Integration тесты — через [testcontainers-go](https://golang.testcontainers.org/)**. Реальный Postgres/Redis в Docker лучше любого мока.
- **Fuzzing — для парсеров, валидаторов, кодеков**. Запустите на 10 минут — найдёте баги, которые table-driven никогда не покрывал бы.
- **Покрытие — не цель, а индикатор**. 80% с осмысленными тестами лучше 100% с проверкой геттеров.
- **`testdata/` — для фикстур**. Go-toolchain игнорирует эту папку при сборке.

### 🌐 HTTP и API
- **Timeouts на сервере — обязательно**: `ReadHeaderTimeout`, `ReadTimeout`, `WriteTimeout`, `IdleTimeout`. Дефолтный `http.Server{}` без них — приглашение к slowloris.
- **Timeouts на клиенте — тоже**. `http.DefaultClient` без таймаута — мина замедленного действия. Создавайте свой `http.Client`.
- **`context.Context` в каждый запрос**. `http.NewRequestWithContext` — стандарт.
- **`r.Body.Close()` после `io.ReadAll`** — иначе утечка соединения из пула.
- **Не используйте `http.Get/Post` в продакшене** — у них нет таймаутов и контекста.
- **Graceful shutdown**: `srv.Shutdown(ctx)` по сигналу `SIGTERM`, дайте 10–30 секунд, чтобы инфлайт-запросы доехали.
- **Middleware — цепочкой, в правильном порядке**: recover → request id → logging → tracing → auth → rate limit → handler.
- **Не паникуйте в хендлере**. Recover-middleware ловит panic и возвращает 500, но это последняя линия обороны, не норма.
- **Версионируйте API с первого дня**: `/v1/users`. Менять контракт без версии — ломать клиентов.

### 🗄 Базы данных
- **Connection pool — настраивайте под нагрузку**. `SetMaxOpenConns`, `SetMaxIdleConns`, `SetConnMaxLifetime`. Дефолты — не для прода.
- **Всегда `QueryContext`/`ExecContext`** — версии без контекста зависнут навечно при проблемах с БД.
- **Транзакция — короткая**. Никаких HTTP-вызовов и долгих расчётов внутри `BEGIN ... COMMIT`. Только работа с БД.
- **Откат через `defer`**: `defer tx.Rollback()` сразу после `Begin`. `Commit` отменит rollback. Безопасно и идиоматично.
- **`sqlc` или `pgx` напрямую** > ORM. В Go ORM-ы дают мало пользы и много магии.
- **Миграции — версионируемые и идемпотентные** (`goose`/`atlas`). Никаких `ALTER TABLE` руками в проде.
- **Индексы под реальные запросы**, не «на всякий случай». `EXPLAIN ANALYZE` — ваш главный инструмент.
- **N+1 запросов — главный убийца перформанса**. JOIN или batch-загрузка.

### ⚡ Производительность
- **Сначала измерь, потом оптимизируй**. `pprof` + benchmark + `benchstat`. Интуиция врёт.
- **Preallocate slices/maps**: `make([]T, 0, n)` и `make(map[K]V, n)` — экономит реаллокации.
- **Избегайте `fmt.Sprintf` в hot path** — рефлексия дорогая. Используйте `strconv` и `strings.Builder`.
- **Escape analysis читайте**: `go build -gcflags='-m'`. Что уехало в кучу — кандидат на оптимизацию.
- **GOMEMLIMIT (1.19+)** — soft limit на память, спасает от OOM при кратковременных всплесках.
- **PGO (Profile-Guided Optimization)** — бесплатные 5–15% перформанса с 1.21+. Просто положите `default.pgo` рядом с `main.go`.
- **`sync.Pool` — для аллокаций, не для коннектов**. Коннекты — это другой контракт жизни.
- **Не страдайте микро-оптимизациями** в коде, который вызывается 10 раз в день. Оптимизируйте hot path.

### 📜 Логирование и observability
- **`log/slog` (1.21+) — стандарт**. Никаких `logrus`/`zap` в новых проектах без причины.
- **Structured logging, не `fmt.Printf`-style**. `slog.Info("user created", "id", u.ID, "email", u.Email)` — поля, не интерполяция.
- **Не логируйте PII в plain text**: пароли, токены, email-ы. Маскируйте или хешируйте.
- **Correlation/trace id во всех логах запроса**. Без этого распределённая трассировка бесполезна.
- **Логи — это события, метрики — это числа, трейсы — это причинно-следственная цепочка**. Не путайте, не подменяйте одно другим.
- **OpenTelemetry — единый стандарт** для traces/metrics/logs. Не пишите кастомные клиенты.
- **`pprof` всегда включён в проде** на отдельном порту за auth. Когда сервис тормозит, у вас 30 секунд на снятие профиля.

### 🔒 Безопасность
- **`govulncheck` в CI** — на каждый PR. Бесплатно ловит известные CVE в зависимостях.
- **`gosec` для статанализа**. Поможет с `crypto/md5`, hardcoded credentials и подобным.
- **TLS везде**. mTLS между сервисами. Никаких `InsecureSkipVerify: true` в проде.
- **JWT — RS256, не HS256**. Симметричный ключ утечёт.
- **Secrets — через Vault/SOPS/cloud KMS**, не в `.env` и не в Git.
- **Валидация ввода на границе**. Доверяете только тому, что сами проверили.
- **Rate limiting на уровне gateway и приложения**. Двойной слой.
- **Update Go регулярно**. Минорные релизы — закрытые CVE.

### 📦 Зависимости и модули
- **Минимизируйте зависимости**. Каждая внешняя библиотека — потенциальный CVE, конфликт версий, и просто чужой код в вашем бинаре.
- **Проверяйте `go.sum` в Git**. Без него `go mod download` может скачать что угодно.
- **`replace` — только локально, не в релизах**. Иначе ломаете downstream.
- **`go mod tidy` — на каждый коммит**. CI должен это проверять.
- **Pin major-версии в импортах**: `v2`/`v3` в пути модуля. Breaking changes не должны быть тихими.

### 🚢 Production-готовность
- **Graceful shutdown** — обязательно. SIGTERM → stop accepting → wait inflight → exit.
- **Health checks — раздельно**: `/livez` (жив ли процесс) и `/readyz` (готов ли принимать трафик). Kubernetes их различает.
- **Конфиг через env + flags + файл**, в таком порядке приоритета. `viper`/`koanf` это умеют из коробки.
- **12-factor app** — читайте, это не догма, а проверенный список граблей.
- **Distroless Docker image** для финального бинаря: `gcr.io/distroless/static`. Нет shell — меньше attack surface, ещё и весит мало.
- **Multi-stage Dockerfile**: builder + minimal runtime. Никаких `golang:1.23` в проде.
- **`CGO_ENABLED=0` по умолчанию**. Статический бинарь — деплоится куда угодно.
- **Версия и commit hash в `/version` endpoint**. `-ldflags "-X main.version=..."` при сборке.

### 🧠 Code review и командная работа
- **Маленькие PR**. 200 строк ревьюится за 30 минут, 2000 — не ревьюится вообще.
- **Один PR = одно изменение**. Рефактор и новая фича — отдельно.
- **Тесты в том же PR, что и код**. «Тесты добавлю потом» = «никогда».
- **Ревью — про код, не про человека**. «Этот метод можно упростить» вместо «ты не понимаешь Go».
- **Conventional commits**: `feat:`, `fix:`, `docs:`, `refactor:`. Это даёт автогенерацию changelog и понятную историю.
- **ADR (Architecture Decision Records)** — для важных решений. Через год вы забудете, почему выбрали NATS, а не Kafka.

> 📌 Шпаргалка по идиомам в одном месте: [Go Code Review Comments](https://go.dev/wiki/CodeReviewComments), [Effective Go](https://go.dev/doc/effective_go), [Uber Go Style Guide](https://github.com/uber-go/guide/blob/master/style.md).

---

## 🔥 3 железных правила

1. **Каждый модуль закрывается проектом.** Без проекта — модуль не пройден.
2. **Каждый проект коммитится на GitHub.** Публичный repo с README и тестами — ваш портфель.
3. **Каждую неделю пишете заметку «что узнал»** — в `/notes` или личный блог. Это закрепляет знание.

---

## ❓ FAQ

**❓ Можно без опыта программирования?**  
Можно, но будет тяжело. Сначала пройдите [CS50](https://cs50.harvard.edu/) (бесплатно) — базовый CS и алгоритмы.

**❓ Go или Rust в 2026?**  
Go — для backend-сервисов, инфраструктуры, AI-агентов. Rust — для systems, embedded, perf-critical. Они не конкуренты. Учите Go, если цель — backend и быстро на работу.

**❓ Нужна ли мат-база?**  
Для модулей 00–12 — нет. Для 14 (distributed) и 16 (system design) — желательно знать теорию вероятности и базовую алгоритмику.

**❓ Сколько часов в день?**  
Минимум 1.5 часа в будни + 3–4 часа в выходные. Меньше — потеряете темп.

**❓ Как искать первую работу?**  
После модуля 06 уже можно отправлять CV на Junior. После модуля 09 — на Middle. Главное — публичные проекты на GitHub и пет-проект, который вы можете объяснить в деталях.

**❓ Что делать, если застрял?**  
Час борьбы → пять минут на решение из интернета → реализация заново без подглядывания. Если застрял на неделю — спроси в [Gophers Slack](https://invite.slack.golangbridge.org/) или в [@Golang_google](https://t.me/Golang_google) чате.

---

## 🤝 Контрибьюции

PR'ы приветствуются: опечатки, новые бесплатные ресурсы на русском, уточнения по модулям. Открой issue, если нашёл устаревшую ссылку.

---

## 📄 Лицензия

MIT — используй, форкай, улучшай.

---

⭐ Если roadmap помог — поставь звезду, это мотивирует развивать курс.

---

## 🧠 Продвинутые вопросы по Go — с кодом и разбором

Этот раздел — сборник каверзных вопросов, которые задают на Middle/Senior-собеседованиях. Каждый вопрос содержит код, разбор поведения и объяснение «почем».

---

### 1. Что выведет эта программа? (goroutine + closure)

```go
package main

import (
    "fmt"
    "sync"
)

func main() {
    var wg sync.WaitGroup
    for i := 0; i < 5; i++ {
        wg.Add(1)
        go func() {
            defer wg.Done()
            fmt.Println(i)
        }()
    }
    wg.Wait()
}
```

**Разбор:** Программа скорее всего выведет `5 5 5 5 5` (Go ≤ 1.21). Все горутины захватывают одну и ту же переменную `i` по ссылке (closure). К моменту запуска цикл уже завершился и `i == 5`.

**Правильный вариант:**

```go
for i := 0; i < 5; i++ {
    wg.Add(1)
    i := i // shadowing: новая переменная в каждой итерации
    go func() {
        defer wg.Done()
        fmt.Println(i)
    }()
}
// Или: передавать значение аргументом:
go func(n int) {
    defer wg.Done()
    fmt.Println(n)
}(i)
```

> Начиная с Go 1.22 переменная цикла создаётся заново на каждой итерации автоматически, поэтому исходный код начнёт выводить 0..4 правильно.

---

### 2. Есть ли гонка данных? (map + goroutines)

```go
package main

import "sync"

func main() {
    m := make(map[string]int)
    var wg sync.WaitGroup
    for i := 0; i < 100; i++ {
        wg.Add(1)
        go func(n int) {
            defer wg.Done()
            m["key"] = n // ← здесь
        }(i)
    }
    wg.Wait()
}
```

**Разбор:** Да, **гонка данных**. Map в Go не потокобезопасен. Одновременная запись ведёт к panics в runtime (начиная с Go 1.6). Запуск с `-race` детектирует это немедленно.

**Правильный вариант:**

```go
var mu sync.Mutex
// ...
go func(n int) {
    defer wg.Done()
    mu.Lock()
    m["key"] = n
    mu.Unlock()
}(i)

// Или использовать sync.Map для частого конкурентного доступа:
var sm sync.Map
sm.Store("key", n)
```

---

### 3. Что выведет программа? (defer + named return)

```go
package main

import "fmt"

func f() (result int) {
    defer func() {
        result++
    }()
    return 0
}

func main() {
    fmt.Println(f()) // ?
}
```

**Разбор:** Выведет `1`. Как это работает:
1. `return 0` присваивает `result = 0`
2. Дефер выполняется: `result++` → `result = 1`
3. Функция возвращает `1`

Практическое применение — обёртывание ошибки с контекстом:

```go
func dbQuery(ctx context.Context) (err error) {
    defer func() {
        if err != nil {
            err = fmt.Errorf("dbQuery: %w", err)
        }
    }()
    return someOperation()
}
```

---

### 4. Утечка горутины — найдите проблему

```go
func fetchData(url string) (string, error) {
    ch := make(chan string)
    go func() {
        resp, err := http.Get(url)
        if err != nil {
            return
        }
        defer resp.Body.Close()
        body, _ := io.ReadAll(resp.Body)
        ch <- string(body)
    }()

    select {
    case data := <-ch:
        return data, nil
    case <-time.After(1 * time.Second):
        return "", errors.New("timeout")
    }
}
```

**Разбор:** При таймауте горутина продолжает выполнять `http.Get`, а потом пытается отправить в `ch` — но читателя нет, unbuffered канал, горутина **зависает навсегда**.

**Правильный вариант:**

```go
func fetchData(ctx context.Context, url string) (string, error) {
    ch := make(chan string, 1) // буферизованный канал
    go func() {
        req, err := http.NewRequestWithContext(ctx, http.MethodGet, url, nil)
        if err != nil {
            return
        }
        resp, err := http.DefaultClient.Do(req)
        if err != nil {
            return
        }
        defer resp.Body.Close()
        body, _ := io.ReadAll(resp.Body)
        ch <- string(body)
    }()
    select {
    case data := <-ch:
        return data, nil
    case <-ctx.Done():
        return "", ctx.Err()
    }
}
```

---

### 5. Interface nil trap — почему `err != nil` верно, хотя ошибки нет?

```go
package main

import "fmt"

type MyError struct{ msg string }

func (e *MyError) Error() string { return e.msg }

func getError(fail bool) error {
    var err *MyError
    if fail {
        err = &MyError{"something failed"}
    }
    return err // ← ловушка!
}

func main() {
    err := getError(false)
    if err != nil {
        fmt.Println("got error:", err) // это выполнится!
    }
}
```

**Разбор:** Интерфейс состоит из двух слов: **(ttype, value)**. `return err` возвращает интерфейс с **(type=`*MyError`, value=nil)** — это **НЕ nil-интерфейс**, потому что type задан.

**Правило:** никогда не возвращайте типизированный nil через интерфейс:

```go
func getError(fail bool) error {
    if fail {
        return &MyError{"something failed"}
    }
    return nil // настоящий nil-интерфейс
}
```

---

### 6. Что выведет программа? (slice sharing)

```go
package main

import "fmt"

func main() {
    a := []int{1, 2, 3, 4, 5}
    b := a[1:3]       // b = [2, 3], len=2, cap=4
    b = append(b, 99)
    fmt.Println(a)    // ?
    fmt.Println(b)    // ?
}
```

**Разбор:**
- `a`: `[1 2 3 99 5]` — **сюрприз!**
- `b`: `[2 3 99]`

`b` указывает на тот же underlying array, что и `a`. `append` записал `99` в позицию индекса 3 общего массива, т.к. `cap(b) = 4 > len(b) = 2`.

**Защита через full slice expression:**

```go
b := a[1:3:3] // len=2, cap=2 — ограничиваем capacity!
b = append(b, 99)
fmt.Println(a) // [1 2 3 4 5] — не изменился
fmt.Println(b) // [2 3 99]
```

---

### 7. Deadlock — почему программа зависает?

```go
package main

func main() {
    ch := make(chan int)
    ch <- 42 // блокирует навсегда
}
```

**Разбор:** `fatal error: all goroutines are asleep - deadlock!`. Небуферизованный канал блокирует отправителя, пока не появится получатель. Go runtime обнаруживает deadlock, когда все горутины заблокированы.

```go
// Исправленный вариант 1: буферизованный канал
ch := make(chan int, 1)
ch <- 42

// Исправленный вариант 2: отправка в горутине
ch := make(chan int)
go func() { ch <- 42 }()
fmt.Println(<-ch)
```

---

### 8. Escape analysis — почему переменная уходит в кучу?

```go
//go:noinline
func newInt() *int {
    x := 42
    return &x // x "убегает" из стека на кучу
}
```

**Разбор:** Компилятор проводит **escape analysis**: если переменная используется за пределами функции — она аллокируется на куче.

```bash
go build -gcflags='-m' .
# Вывод: ./main.go:5:2: moved to heap: x
```

Оптимизация — принимать указатель снаружи:

```go
// Вместо return &Result{...}
func process(r *Result) { r.fill() } // нет лишней аллокации в hot path
```

---

### 9. sync.Mutex — value vs pointer receiver

```go
type Counter struct {
    mu  sync.Mutex
    val int
}

func (c Counter) Inc() { // value receiver!
    c.mu.Lock()
    defer c.mu.Unlock()
    c.val++
}

func main() {
    c := Counter{}
    c.Inc()
    c.Inc()
    fmt.Println(c.val) // ?
}
```

**Разбор:** Выведет `0`. Value receiver получает **копию** структуры, включая `sync.Mutex`, что является UB. `go vet` выдаст: `call of c.Inc copies lock value`.

```go
func (c *Counter) Inc() { // pointer receiver
    c.mu.Lock()
    defer c.mu.Unlock()
    c.val++
}
// Теперь c.val == 2
```

> Правило: структуры с `sync.Mutex`, `sync.WaitGroup` и др. **всегда** используют pointer receiver и **никогда** не копируются.

---

### 10. Context cancellation — правильный паттерн проверки

```go
func doWork(ctx context.Context, items []string) error {
    for _, item := range items {
        // Неблокирующая проверка контекста ДО работы:
        select {
        case <-ctx.Done():
            return ctx.Err()
        default:
        }
        if err := process(ctx, item); err != nil {
            return err
        }
    }
    return nil
}
```

**Разбор:** Это **правильный паттерн**. `select { case <-ctx.Done(): default: }` — неблокирующая проверка. Проверка идёт ДО `process`, чтобы не начинать работу, если уже отменили.

Лучше всего — передавать `ctx` в `process`, чтобы он сам корректно обрабатывал отмену (например, через `http.NewRequestWithContext`, `db.QueryContext`).

---

### 11. nil-срез вс пустой срез

```go
var s1 []int = nil
var s2 []int = []int{}

fmt.Println(s1 == nil) // true
fmt.Println(s2 == nil) // false
fmt.Println(len(s1), len(s2)) // 0 0
```

**Разбор:** Оба среза работают одинаково с `len`, `cap`, `range`, `append`. Разница — в JSON:

```go
json.Marshal(s1) // → "null"
json.Marshal(s2) // → "[]"
```

> Правило: возвращайте `nil` для "нет данных" и `[]T{}` для "пустой список". JSON-клиенты обычно ожидают `[]`, а не `null`.

---

### 12. Worker pool — что не так?

```go
func processItems(items []string) {
    jobs := make(chan string)

    for w := 0; w < 5; w++ {
        go func() {
            for job := range jobs {
                process(job)
            }
        }()
    }

    for _, item := range items {
        jobs <- item
    }
    // Без close(jobs) и без WaitGroup!
}
```

**Разбор:** Две проблемы:
1. Без `close(jobs)` воркеры не завершатся (цикл `range jobs` зависает навсегда)
2. Без `WaitGroup` функция вернётся раньше окончания воркеров

**Правильный вариант:**

```go
func processItems(items []string) {
    jobs := make(chan string)
    var wg sync.WaitGroup

    for w := 0; w < 5; w++ {
        wg.Add(1)
        go func() {
            defer wg.Done()
            for job := range jobs {
                process(job)
            }
        }()
    }

    for _, item := range items {
        jobs <- item
    }
    close(jobs) // сигнал — новых заданий не будет
    wg.Wait()   // ждём завершения всех воркеров
}
```

---

### 13. Generics — ограничения типов (Go 1.18+)

```go
// Не скомпилируется: operator + not defined on T
func Sum[T any](nums []T) T {
    var total T
    for _, n := range nums { total += n }
    return total
}

// Правильно: constraint с тильдой (~)
type Number interface {
    ~int | ~int32 | ~int64 | ~float32 | ~float64
}

func Sum[T Number](nums []T) T {
    var total T
    for _, n := range nums { total += n }
    return total
}
```

**Разбор:** Тильда `~int` означает «все типы, у которых underlying type — int». Поэтому подходят кастомные типы:

```go
type Celsius float64
fmt.Println(Sum([]Celsius{36.6, 37.0})) // работает!
```

---

### 14. Go Memory Model — happens-before

```go
var x int
var done bool

func setup() {
    x = 42
    done = true
}

func main() {
    go setup()
    for !done {}
    fmt.Println(x) // Гарантировано ли 42?
}
```

**Разбор:** **НЕТ гарантии**. Без синхронизации компилятор и CPU могут переупорядочить операции. Race detector покажет data race.

**Идиоматичный вариант:**

```go
done := make(chan struct{})
go func() {
    x = 42
    close(done) // happens-before receive
}()
<-done
fmt.Println(x) // гарантированно 42

// Или через atomic:
var x atomic.Int64
var done atomic.Bool
go func() { x.Store(42); done.Store(true) }()
for !done.Load() {}
fmt.Println(x.Load())
```

> Go Memory Model гарантирует happens-before только для явных точек синхронизации: канал, `sync.Mutex`, `sync/atomic`.

---
