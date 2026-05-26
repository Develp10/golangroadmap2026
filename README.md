<div align="center">

# 🚀 Golang Roadmap 2026

**Полный путь от нуля до Senior / Staff Go-разработчика на русском языке**

Реальные сроки · Бесплатные ресурсы · Проекты · Самопроверка

![Go](https://img.shields.io/badge/Go-1.23+-00ADD8?logo=go&logoColor=white)
![Level](https://img.shields.io/badge/Level-Junior%20→%20Staff-blueviolet)
![Time](https://img.shields.io/badge/Time-12–18%20months-orange)
![License](https://img.shields.io/badge/License-MIT-green)
![Language](https://img.shields.io/badge/Language-Russian-red)

</div>

---

## 📚 О курсе

Этот репозиторий — не просто roadmap, а **полноценный курс по Go из 19 модулей**, разбитый по урокам в папке [`/course`](./course).

Курс состоит из двух частей:

* **Основная часть (модули 0–12)** — путь от установки Go до уверенных Senior-собеседований. 10–14 месяцев при 2–3 часах в день.
* **Продвинутая часть (модули 13–18)** — то, что отличает сильного Senior'а от Staff/Principal: runtime, distributed systems, observability, security, K8s operators, AI/ML.

Каждый модуль содержит:

* 🎯 **Цель** — что ты будешь уметь после модуля
* 📚 **Теорию** — что и где читать/смотреть (книги, статьи, видео)
* 💻 **Практику** — конкретные задания и проекты
* ✅ **Чек-пойнт** — самопроверка перед переходом дальше
* ⚠️ **Красные флаги** — типичные ошибки, которые тормозят рост

👉 **Старт:** [Модуль 0 — Фундамент](./course/00-fundamentals.md)

---

## 📑 Содержание

* [Программа курса](#-программа-курса)
* [Подробный разбор модулей](#-подробный-разбор-модулей)
* [Длительность по грейдам](#️-длительность-по-грейдам)
* [Как проходить курс](#-как-проходить-курс)
* [Топ бесплатных ресурсов](#-топ-бесплатных-ресурсов)
* [3 железных правила](#-3-железных-правила)
* [FAQ](#-faq)

---

## 🎓 Программа курса

### Основная часть — путь до Senior

| № | Модуль | Срок | Уровень |
|---|--------|------|---------|
| 0 | [Фундамент](./course/00-fundamentals.md) | 2–3 недели | 🟢 |
| 1 | [Синтаксис и основы Go](./course/01-syntax.md) | 3–4 недели | 🟢 |
| 2 | [Глубокий Go](./course/02-deep-go.md) | 4–6 недель | 🟡 |
| 3 | [Конкурентность](./course/03-concurrency.md) | 3–4 недели | 🟡 |
| 4 | [Стандартная библиотека](./course/04-stdlib.md) | 3 недели | 🟢 |
| 5 | [Базы данных](./course/05-databases.md) | 3–4 недели | 🟡 |
| 6 | [Web и API](./course/06-web-api.md) | 4–6 недель | 🟡 |
| 7 | [Тестирование](./course/07-testing.md) | 2–3 недели | 🟢 |
| 8 | [Микросервисы и сети](./course/08-microservices.md) | 6–8 недель | 🟠 |
| 9 | [DevOps минимум](./course/09-devops.md) | 3–4 недели | 🟠 |
| 10 | [Архитектура и паттерны](./course/10-architecture.md) | 4–6 недель | 🔴 |
| 11 | [Performance и production](./course/11-performance.md) | 3–4 недели | 🔴 |
| 12 | [Подготовка к собеседованиям](./course/12-interview.md) | 3 недели | 🟣 |

### Продвинутая часть — от Senior к Staff/Principal

| № | Модуль | Срок | Уровень |
|---|--------|------|---------|
| 13 | [Go Runtime & Internals](./course/13-runtime-internals.md) | 4–6 недель | 🔴 |
| 14 | [Distributed Systems](./course/14-distributed-systems.md) | 6–8 недель | 🔴 |
| 15 | [Observability & SRE](./course/15-observability.md) | 3–4 недели | 🔴 |
| 16 | [Security в Go](./course/16-security.md) | 3–4 недели | 🔴 |
| 17 | [Cloud Native & K8s Operators](./course/17-cloud-native.md) | 4–6 недель | 🔴 |
| 18 | [AI/ML & Data Engineering на Go](./course/18-ai-data.md) | 3–4 недели | 🔴 |

> Продвинутая часть не обязана идти строго по порядку. Выбирай модули под свой контекст: Senior backend — 13/14/15, platform engineer — 15/16/17, ML-инфра — 14/15/18.

---

## 🔎 Подробный разбор модулей

Ниже — детальный план каждого модуля: что изучать, что строить, где брать материалы. Полные уроки и чек-листы — внутри файлов в [`/course`](./course).

### Модуль 0. Фундамент 🟢 (2–3 недели)

**Что изучаем.** Установка Go и tooling (`go env`, GOPATH/GOROOT/GOBIN, goimports, golangci-lint, delve), терминал и Unix-философия (grep/sed/awk/find/xargs/tmux), Git глубоко (объектная модель, rebase, конфликты, GPG/sigstore), как устроен компьютер (CPU/кэши/RAM/процессы/потоки), как работает сеть (TCP/IP, DNS, TLS, HTTP/1.1/2/3), первая программа на Go и `go mod`, IDE + Delve + format-on-save.

**Бесплатные ресурсы.** [A Tour of Go](https://go.dev/tour/), [Go by Example](https://gobyexample.com/), [How to Write Go Code](https://go.dev/doc/code), [The Missing Semester (MIT)](https://missing.csail.mit.edu/), [Pro Git на русском](https://git-scm.com/book/ru/v2), [Learn Git Branching](https://learngitbranching.js.org/?locale=ru_RU), [Latency Numbers Every Programmer Should Know](https://gist.github.com/jboner/2841832), YouTube-канал [JustForFunc](https://www.youtube.com/c/JustForFunc).

**Проект модуля.** CLI-утилита `gotodo` — менеджер задач в терминале с JSON-хранилищем, цветным выводом, флагами priority/due/filter, установкой через `go install`, чистым `golangci-lint`.

---

### Модуль 1. Синтаксис и основы Go 🟢 (3–4 недели)

**Что изучаем.** Типы данных и zero values, iota и Stringer, управляющие конструкции и `defer`, функции / замыкания / variadic, functional options, методы (value vs pointer receiver), маленькие интерфейсы, mental model слайса (ptr/len/cap), map, указатели и семантика, идиоматичные ошибки (`errors.Is/As`, wrap через `%w`), организация пакетов и `internal/`.

**Бесплатные ресурсы.** [Effective Go](https://go.dev/doc/effective_go), [Go Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments), [Google Go Style Guide](https://google.github.io/styleguide/go/), [100 Go Mistakes](https://100go.co/), статьи [Dave Cheney "Practical Go"](https://dave.cheney.net/practical-go) и "Don't just check errors, handle them gracefully", блог [Go Slices: usage and internals](https://go.dev/blog/slices-intro).

**Проект модуля.** `gowiki` — статический генератор сайтов на Go: Markdown + front matter + `html/template` + CLI с подкомандами + 80% покрытие тестами + структура `cmd/`, `internal/`, `pkg/`.

---

### Модуль 2. Глубокий Go 🟡 (4–6 недель)

**Что изучаем.** Интерфейсы и nil-interface gotcha, дизайн «accept interfaces, return structs», композиция через embedding, generics (constraints, когда уместны и когда вредны), reflection и её цена, escape analysis (`go build -gcflags="-m"`), стек vs куча, GC на высоком уровне (tri-color marking, write barrier, GOGC, GOMEMLIMIT).

**Бесплатные ресурсы.** [Ardan Labs Ultimate Go (Bill Kennedy)](https://www.ardanlabs.com/training/ultimate-go/) — лекции на YouTube бесплатно, Go blog [про GC](https://go.dev/blog/ismmkeynote), статьи Damian Gryski про escape analysis.

**Проект модуля.** Расширяемый калькулятор через интерфейсы + набор дженерик-контейнеров `Stack[T]`/`Queue[T]`/`Set[T]` с тестами 80%+ и проверенным escape analysis.

---

### Модуль 3. Конкурентность 🟡 (3–4 недели)

**Что изучаем.** Горутины и их цена, планировщик GMP с work-stealing и preemption, каналы (буферизованные / небуферизованные / направленные), `select` и таймауты, пакет `sync` (Mutex/RWMutex/WaitGroup/Once/Cond/Pool), `sync/atomic`, `context.Context` (Cancel/Timeout/Deadline/Value), паттерны (worker pool, fan-in/fan-out, pipeline, semaphore, errgroup, rate limiter), race detector.

**Бесплатные ресурсы.** [Go Concurrency Patterns (Rob Pike)](https://www.youtube.com/watch?v=f6kdp27TYZs), [Advanced Go Concurrency Patterns (Sameer Ajmani)](https://www.youtube.com/watch?v=QDDwwePbDtw), [Go blog про context](https://go.dev/blog/context).

**Проект модуля.** Многопоточный web crawler с лимитом параллелизма, отменой через `context`, graceful shutdown и чистым `go test -race`.

---

### Модуль 4. Стандартная библиотека 🟢 (3 недели)

**Что изучаем.** `net/http` клиент (Transport, connection pooling, retry с backoff) и сервер (новый `ServeMux` в Go 1.22 с роутингом по методу и path-params), `encoding/json` (теги, RawMessage, кастомные Marshal/Unmarshal, streaming), `io`/`bufio`/`os`, `time` (монотонные часы, Ticker/Timer, таймзоны), `log/slog` (Go 1.21+, JSON-логи, атрибуты), `flag`, `os/signal`, graceful shutdown.

**Бесплатные ресурсы.** [Go blog про slog](https://go.dev/blog/slog), [Go 1.22 release notes](https://go.dev/doc/go1.22), [Standard library docs](https://pkg.go.dev/std).

**Проект модуля.** `httpcheck` — параллельный HTTP-чекер URL'ов на чистой stdlib (нулевые зависимости), JSON-логи, Ctrl+C → graceful shutdown.

---

### Модуль 5. Базы данных 🟡 (3–4 недели)

**Что изучаем.** SQL уровня JOIN/GROUP BY/CTE/window functions, EXPLAIN ANALYZE, индексы (B-tree, Hash, GIN), нормальные формы, `database/sql` + `pgx`, транзакции и уровни изоляции, миграции (`goose`/`golang-migrate`), query builder (`squirrel`) и codegen через `sqlc`, ORM (`gorm`) с пониманием минусов, Redis (типы данных, кэш, TTL, distributed locks).

**Бесплатные ресурсы.** [PostgreSQL Tutorial](https://www.postgresqltutorial.com/), [Use The Index, Luke!](https://use-the-index-luke.com/), [pgx docs](https://github.com/jackc/pgx), [sqlc docs](https://docs.sqlc.dev/), [Redis University](https://university.redis.com/).

**Проект модуля.** REST-сервис «Библиотека книг» с full-text поиском в Postgres, cursor-пагинацией, кэшем в Redis, миграциями и решением N+1.

---

### Модуль 6. Web и API 🟡 (4–6 недель)

**Что изучаем.** Современный `ServeMux`, роутеры (chi как идиоматичный, echo, gin), middleware (RequestID, Logging, Recover, CORS, rate limit), JWT (access + refresh, ротация, PKCE), хеширование паролей (argon2id / bcrypt), валидация (`go-playground/validator`), gRPC + Protocol Buffers (unary / streaming / interceptors / deadlines), WebSocket (hub-паттерн, ping/pong), OpenAPI/Swagger (`swaggo/swag`, `oapi-codegen`).

**Бесплатные ресурсы.** [chi docs](https://github.com/go-chi/chi), [gRPC Go Quick Start](https://grpc.io/docs/languages/go/quickstart/), [JWT Handbook](https://auth0.com/resources/ebooks/jwt-handbook), [OWASP Authentication Cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html).

**Проект модуля.** Мини-соцсеть: REST + gRPC + WebSocket-чат, JWT с ротацией, Swagger, валидация на всех эндпоинтах.

---

### Модуль 7. Тестирование 🟢 (2–3 недели)

**Что изучаем.** `testing` + table-driven + subtests + `t.Parallel` + `t.Helper` + `t.Cleanup` + golden files, `testify` (assert / require / suite), моки (`gomock`, `mockery`), интеграционные тесты через `testcontainers-go`, `httptest`, бенчмарки + pprof + `benchstat`, fuzzing (Go 1.18+), покрытие.

**Бесплатные ресурсы.** [Go testing docs](https://pkg.go.dev/testing), [Advanced Testing in Go (Mitchell Hashimoto)](https://www.youtube.com/watch?v=8hQG7QlcLBk), [testcontainers-go docs](https://golang.testcontainers.org/).

**Проект модуля.** Полностью покрыть библиотеку книг из модуля 5: unit ≥70%, 5 интеграционных тестов с testcontainers, 2–3 бенчмарка, 1 fuzz-тест.

---

### Модуль 8. Микросервисы и сети 🟠 (6–8 недель)

**Что изучаем.** Когда микросервисы нужны (а когда монолит), брокеры (Kafka — партиции/consumer groups/гарантии EOS, RabbitMQ — exchange/routing key, NATS JetStream), Saga (choreography vs orchestration), Outbox-pattern, CQRS и Event Sourcing с трезвой оценкой, устойчивость (Circuit Breaker через `sony/gobreaker`, retry с jitter, bulkhead, idempotency keys), service discovery + API Gateway, gRPC interceptors, distributed tracing через OpenTelemetry + Jaeger.

**Бесплатные ресурсы.** [microservices.io (Chris Richardson)](https://microservices.io/), [Kafka: The Definitive Guide (Confluent, бесплатно)](https://www.confluent.io/resources/kafka-the-definitive-guide/), [OpenTelemetry Go docs](https://opentelemetry.io/docs/languages/go/).

**Проект модуля.** Мини-маркетплейс: 4 сервиса (users / catalog / orders / notifier), gRPC между сервисами + Kafka для событий, реализованные Saga + Outbox, сквозной distributed tracing.

---

### Модуль 9. DevOps минимум 🟠 (3–4 недели)

**Что изучаем.** Docker (multi-stage, distroless, scratch, `CGO_ENABLED=0`), docker-compose с healthchecks, Kubernetes базово (Pod/Deployment/Service/Ingress/ConfigMap/Secret), Helm, CI/CD на GitHub Actions, Prometheus + `client_golang` + 4 золотых сигнала, Grafana, structured JSON-логи с корреляцией trace_id.

**Бесплатные ресурсы.** [Docker docs](https://docs.docker.com/), [Kubernetes Basics tutorial](https://kubernetes.io/docs/tutorials/kubernetes-basics/), [Killercoda K8s playground](https://killercoda.com/), [Helm docs](https://helm.sh/docs/), [Prometheus docs](https://prometheus.io/docs/introduction/overview/), [Grafana tutorials](https://grafana.com/tutorials/).

**Проект модуля.** Маркетплейс из модуля 8 → multi-stage Docker, docker-compose локально, развёртывание в kind/minikube через Helm, CI lint→test→build→push в ghcr.io, метрики Prometheus + дашборд Grafana.

---

### Модуль 10. Архитектура и паттерны 🔴 (4–6 недель)

**Что изучаем.** SOLID без слепого переноса из Java, Clean Architecture (слои и правило зависимостей), Hexagonal/Ports & Adapters, DDD-минимум (bounded context, ubiquitous language, aggregate roots, value objects, domain events), event-driven и eventual consistency, идиоматичные паттерны Go (functional options, builder, decorator через middleware, strategy через интерфейс), антипаттерны (god package, anemic domain, преждевременная абстракция, оверинжиниринг).

**Бесплатные ресурсы.** [The Clean Architecture (Uncle Bob)](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html), [DDD Reference (Eric Evans, бесплатный PDF)](https://www.domainlanguage.com/ddd/reference/), статьи [threedots.tech про Go и DDD](https://threedots.tech/), [Go Patterns](https://github.com/tmrts/go-patterns).

**Проект модуля.** Переписать маркетплейс в чистой архитектуре: domain не знает про Postgres/HTTP/gRPC, репозитории — интерфейсы в domain с реализациями в infrastructure, use cases тестируются без БД.

---

### Модуль 11. Performance и production 🔴 (3–4 недели)

**Что изучаем.** pprof в деталях (CPU/heap/goroutine/block/mutex + flame graph), правильные бенчмарки + `benchstat`, GC tuning (GOGC, GOMEMLIMIT, trade-off latency/throughput), снижение аллокаций (`sync.Pool`, `strings.Builder`, преаллокация слайсов), connection pooling (`pgxpool`, `http.Transport.MaxIdleConnsPerHost`), graceful shutdown, liveness/readiness/startup probes, три кита observability.

**Бесплатные ресурсы.** [Profiling Go Programs (Go blog)](https://go.dev/blog/pprof), [Go GC Guide](https://go.dev/doc/gc-guide), [High Performance Go Workshop (Dave Cheney)](https://dave.cheney.net/high-performance-go-workshop/dotgo-paris.html), [Damian Gryski "go-perfbook"](https://github.com/dgryski/go-perfbook).

**Проект модуля.** Найти узкое место в своём сервисе через pprof и ускорить его минимум в 2 раза, документируя процесс «было / стало / что изменил».

---

### Модуль 12. Подготовка к собеседованиям 🟣 (3 недели)

**Что изучаем.** Внутренности Go (GMP-планировщик, GC, memory model, слайс/map/channel в runtime, defer, escape analysis), типовые задачи на собесе (Rate Limiter token/leaky bucket, Worker Pool, LRU, `sync.Map` своими руками, Pub/Sub на каналах, fan-in/fan-out, sharded concurrent map, Promise/Future), System Design по шаблону (functional → non-functional → capacity → API → data model → diagram → bottlenecks), 100–150 LeetCode Easy+Medium на Go, behavioral по STAR.

**Бесплатные ресурсы.** [System Design Primer](https://github.com/donnemartin/system-design-primer), [LeetCode](https://leetcode.com/), [pramp.com](https://www.pramp.com/) (бесплатные peer-to-peer mock-интервью), [interviewing.io](https://interviewing.io/).

**Цель модуля.** 100+ LeetCode решено, 5+ System Design разобрано, 5–10 mock-интервью пройдено, 5–10 behavioral-историй готовы.

---

## 🧬 Продвинутая часть (Senior → Staff/Principal)

### Модуль 13. Go Runtime & Internals 🔴 (4–6 недель)

**Что изучаем.** Go Memory Model и happens-before, scheduler глубоко (sysmon, netpoller, LockOSThread, `go tool trace`), GC внутрь (tricolor + write barrier + pacer, разбор `GODEBUG=gctrace=1`), escape analysis на hot path, `unsafe`/cgo/Plan 9 assembler, reflection и generics под капотом (GC shape stenciling).

**Бесплатные ресурсы.** [Go Memory Model](https://go.dev/ref/mem), [Go GC Guide](https://go.dev/doc/gc-guide), доклады Kavya Joshi, Rick Hudson и Austin Clements на YouTube, статьи Russ Cox и Dmitry Vyukov.

**Проект модуля.** In-memory cache со 100k RPS и p99 < 1ms, GC pause < 1ms, с отчётом до/после по pprof heap/cpu/block/mutex.

---

### Модуль 14. Distributed Systems 🔴 (6–8 недель)

**Что изучаем.** CAP/PACELC/FLP, линеаризуемость vs serializability, time/clocks (Lamport, vector clocks, HLC, TrueTime), консенсус (Raft на уровне реализации, Multi-Paxos, EPaxos, ZAB), репликация (sync/async/leaderless, CRDT), распределённые транзакции (2PC/TCC/Saga/Outbox), idempotency и hedged requests, service discovery + LB + consistent hashing + service mesh (Envoy/Istio), streaming (Kafka EOS, NATS JetStream).

**Бесплатные ресурсы.** [Martin Kleppmann "DDIA" (1 глава бесплатно)](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/), [Jepsen blog (Aphyr)](https://jepsen.io/analyses), [Raft paper](https://raft.github.io/raft.pdf), исходники [hashicorp/raft](https://github.com/hashicorp/raft) и [etcd-io/raft](https://github.com/etcd-io/raft).

**Проект модуля.** Распределённое KV-хранилище с Raft-репликацией, linearizable reads, jepsen-like тестами.

---

### Модуль 15. Observability & SRE 🔴 (3–4 недели)

**Что изучаем.** Three pillars + continuous profiling, OpenTelemetry в Go end-to-end (SDK/exporters/propagators/baggage, head vs tail sampling), Prometheus уровня прода (RED/USE, native histograms, cardinality control), structured slog с trace correlation, continuous profiling (Pyroscope/Parca, eBPF), SLO/SLI/error budget + multi-window burn-rate alerts, incident response + blameless postmortem + chaos engineering.

**Бесплатные ресурсы.** [Google SRE Book](https://sre.google/sre-book/table-of-contents/) и [SRE Workbook](https://sre.google/workbook/table-of-contents/), [Cindy Sridharan blog](https://copyconstruct.medium.com/), [OpenTelemetry docs](https://opentelemetry.io/docs/), [Brendan Gregg blog (eBPF, USE)](https://www.brendangregg.com/).

**Проект модуля.** Полный observability-стек для микросервиса (3 SLO, runbook, chaos-эксперимент, USE+RED дашборды).

---

### Модуль 16. Security в Go 🔴 (3–4 недели)

**Что изучаем.** OWASP Top 10 в Go, gosec/govulncheck/staticcheck в CI, криптография практически (AEAD: AES-GCM/ChaCha20-Poly1305, argon2id для паролей, HMAC, EdDSA, никогда не свой алгоритм), TLS 1.3 + mTLS + PKI (step-ca, SPIFFE/SPIRE), OAuth2/OIDC/PKCE/RBAC/ABAC/ReBAC (OpenFGA/casbin), supply chain (SBOM через syft, подпись через cosign, SLSA уровни, Go checksum DB), container security (distroless/scratch, Pod Security `restricted`, Trivy, Falco), threat modeling по STRIDE + zero-trust + NetworkPolicy default-deny.

**Бесплатные ресурсы.** [Filippo Valsorda blog](https://filippo.io/), [OWASP Top 10](https://owasp.org/Top10/), [SLSA framework](https://slsa.dev/), [sigstore docs](https://docs.sigstore.dev/), [NIST 800-207 Zero Trust](https://csrc.nist.gov/publications/detail/sp/800-207/final).

**Проект модуля.** Secure-by-default REST с OIDC+PKCE, mTLS, argon2id, SBOM+cosign, threat model в репо.

---

### Модуль 17. Cloud Native & K8s Operators 🔴 (4–6 недель)

**Что изучаем.** Kubernetes изнутри (api-server, etcd, reconcile loop), client-go и informers (SharedIndexInformer, work queue, DeltaFIFO), проектирование CRD как API (spec/status subresource, printer columns, CEL-валидация, conversion webhooks), kubebuilder/operator-sdk + controller-runtime (predicates, owner references, финализаторы), admission webhooks (validating/mutating) + OPA/Gatekeeper/Kyverno, Helm + Kustomize + GitOps через ArgoCD/Flux, multi-cluster (Cluster API, Karmada), Knative со scale-to-zero.

**Бесплатные ресурсы.** [Kubebuilder Book](https://book.kubebuilder.io/), [sample-controller](https://github.com/kubernetes/sample-controller), [Kubernetes the Hard Way (Kelsey Hightower)](https://github.com/kelseyhightower/kubernetes-the-hard-way), [controller-runtime docs](https://pkg.go.dev/sigs.k8s.io/controller-runtime).

**Проект модуля.** Production-grade оператор `AppService`: CRD, идемпотентный reconciler, validating webhook, Prometheus-метрики, envtest + e2e в CI, Helm + ArgoCD.

---

### Модуль 18. AI/ML & Data Engineering на Go 🔴 (3–4 недели)

**Что изучаем.** LLM-интеграции (OpenAI/Anthropic/Ollama через SSE streaming + tool calling + retry/timeout), embeddings + vector DB (pgvector/Qdrant/Weaviate/Milvus, HNSW vs IVF, cosine vs L2), RAG-паттерны (chunking, reranking, hybrid search BM25+vector, eval: faithfulness/context recall), agents + MCP с sandbox, stream processing (Kafka/NATS/Redpanda, watermarks, windowing, EOS), OLAP на Go (ClickHouse native protocol, DuckDB, Apache Arrow, Parquet), ML inference (ONNX runtime из Go, dynamic batching, gRPC, Triton).

**Бесплатные ресурсы.** [Anthropic "Building Effective Agents"](https://www.anthropic.com/research/building-effective-agents), [Eugene Yan blog про LLM в продакшене](https://eugeneyan.com/), [Tyler Akidau "Streaming 101/102"](https://www.oreilly.com/radar/the-world-beyond-batch-streaming-101/), [Pinecone learning center](https://www.pinecone.io/learn/), [ClickHouse docs](https://clickhouse.com/docs), [ONNX runtime docs](https://onnxruntime.ai/docs/).

**Проект модуля.** Production RAG-сервис на Go: streaming SSE, tool calling, eval-метрики, guardrails (PII-фильтр, prompt injection detection), A/B тест embedding-моделей.

---

## ⏱️ Длительность по грейдам

| Грейд | Срок (2–3 ч/день) | Что умеешь |
|------|--------------------|-----------|
| 🟢 Junior | 4–6 месяцев | CRUD API, базовая работа с БД, простые горутины, тесты, Docker |
| 🟡 Middle | 8–12 месяцев | Архитектура сервиса, контекст, моки, профилирование, gRPC, миграции |
| 🔴 Senior | 12–14 месяцев основной части | Дизайн систем, наставничество, production-готовность, observability, security |
| 🟣 Staff/Principal | + продвинутая часть и реальная практика | Платформа, distributed systems, runtime internals, operators, AI/ML |

> Время — ориентир. Один проходит за 12 месяцев, другой за 18. Норм оба варианта.

---

## 🧭 Как проходить курс

1. Открой [Модуль 0](./course/00-fundamentals.md) и пройди его до конца, отмечая чекбоксы внутри.
2. Для каждого модуля доводи проект до конца — незаконченный проект учит хуже законченного «плохого».
3. После каждого проекта сверяйся с чек-пойнтом в конце модуля.
4. Пройдя модули 0–7, иди на первые Junior-собеседования — реальный фидбэк ускоряет рост.
5. Пройдя 0–12, ты готов к Middle/Senior. Дальше — модули 13–18 в любом порядке под свою специализацию.
6. Не стесняйся возвращаться к ранним модулям: глубина приходит со вторым проходом.

### Рекомендуемый ритм недели

* **5 дней** — теория + практика по уроку (1–2 часа).
* **1 день** — проект модуля (3–4 часа подряд).
* **1 день** — повторение и решение алгоритмов на LeetCode (1 час).

---

## 📎 Топ бесплатных ресурсов

**Основа языка.** [Tour of Go](https://go.dev/tour/) · [Go by Example](https://gobyexample.com/) · [Effective Go](https://go.dev/doc/effective_go) · [Go Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments) · [Google Go Style Guide](https://google.github.io/styleguide/go/) · [Practical Go (Dave Cheney)](https://dave.cheney.net/practical-go) · [100 Go Mistakes](https://100go.co/) · [Ardan Labs Ultimate Go (YouTube)](https://www.youtube.com/@ArdanLabs) · [JustForFunc (YouTube)](https://www.youtube.com/c/JustForFunc).

**Терминал и Git.** [Missing Semester (MIT)](https://missing.csail.mit.edu/) · [Pro Git на русском](https://git-scm.com/book/ru/v2) · [Learn Git Branching](https://learngitbranching.js.org/?locale=ru_RU).

**Базы данных.** [PostgreSQL Tutorial](https://www.postgresqltutorial.com/) · [Use The Index, Luke!](https://use-the-index-luke.com/) · [Redis University](https://university.redis.com/) · [sqlc docs](https://docs.sqlc.dev/).

**Distributed & SRE.** [Jepsen analyses](https://jepsen.io/analyses) · [Raft paper и визуализация](https://raft.github.io/) · [Google SRE Book + Workbook](https://sre.google/books/) · [microservices.io](https://microservices.io/).

**Observability.** [OpenTelemetry docs](https://opentelemetry.io/docs/) · [Prometheus docs](https://prometheus.io/docs/introduction/overview/) · [Grafana tutorials](https://grafana.com/tutorials/) · [Brendan Gregg blog](https://www.brendangregg.com/).

**Security.** [Filippo Valsorda blog](https://filippo.io/) · [OWASP Top 10](https://owasp.org/Top10/) · [SLSA framework](https://slsa.dev/) · [sigstore docs](https://docs.sigstore.dev/).

**Kubernetes.** [Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/) · [Kubebuilder Book](https://book.kubebuilder.io/) · [Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) · [Killercoda playground](https://killercoda.com/).

**Собеседования.** [LeetCode](https://leetcode.com/) · [System Design Primer](https://github.com/donnemartin/system-design-primer) · [pramp.com](https://www.pramp.com/) · [interviewing.io](https://interviewing.io/).

---

## 📌 3 железных правила

1. **Не прыгай вперёд.** Go обманчиво простой — без фундамента упрёшься в потолок на собесах.
2. **Пиши код сам.** Подсмотреть можно только после часа борьбы с задачей.
3. **Делай проекты до конца.** Незаконченный проект учит хуже законченного «плохого».

---

## ❓ FAQ

**Сколько времени реально нужно до Junior?**
При 2–3 ч/день — 4–6 месяцев, если не пропускать проекты. Без проектов — никогда.

**Можно ли пропустить терминал и Git?**
Нет. Сэкономишь неделю в начале, потеряешь месяцы дальше.

**Что если я уже знаю другой язык?**
Модули 0–1 пройдёшь быстрее, но `пиши Python на Go` — главная ошибка переходящих. Не пропускай идиоматику и mental model.

**Нужен ли английский?**
Базовый — да, большинство первоисточников на нём. Книги и видео можно смотреть с субтитрами.

**Обязательно делать все 19 модулей?**
Основная часть 0–12 — да, если идёшь до Senior. Продвинутая часть 13–18 — выборочно, под свою специализацию.

**Что делать, если застрял?**
Час борьбы → пять минут на решение из интернета → реализация заново без подглядывания. Если застрял на неделю — спроси в [Gophers Slack](https://invite.slack.golangbridge.org/) или на Stack Overflow.

---

## 🤝 Контрибьюции

PR'ы приветствуются: опечатки, новые бесплатные ресурсы на русском, уточнения по модулям. Открой issue, если нашёл устаревшую ссылку.

---

## 📄 Лицензия

MIT — используй, форкай, улучшай.

---

⭐ Если roadmap помог — поставь звезду, это мотивирует развивать курс.
