# 🚀 Golang Roadmap 2026

Полный путь от нуля до Senior Go-разработчика на русском языке. С реальными сроками, бесплатными ресурсами, проектами и проверкой себя на каждом этапе.

> **Общая длительность:** ~10–14 месяцев при 2–3 часах в день.
> До уверенного Middle — около 8 месяцев. До Senior — 2+ года реальной практики.

---

## 📌 Как пользоваться роадмапом

Каждый блок построен по одной схеме: **что учим → зачем это нужно → где брать материал → какой проект пишем → как проверить, что понял**.

Не прыгай вперёд. Go обманчиво простой, и без фундамента ты упрёшься в потолок на собеседованиях по конкурентности, профилированию и архитектуре.

Делай каждый проект сам, не подсматривая. Подсмотреть можно только после того, как застрял минимум на час.

---

## 📚 Содержание

0. Подготовка фундамента
1. Синтаксис и основы Go
2. Глубокий Go
3. Конкурентность
4. Стандартная библиотека и инструменты
5. Базы данных
6. Web и API
7. Тестирование
8. Микросервисы и сети
9. DevOps минимум
10. Архитектура и паттерны
11. Performance и production
12. Подготовка к собесам

---

## 🟢 Этап 0. Подготовка фундамента (2–3 недели)

Если ты вообще никогда не программировал — этот этап обязательный. Если уже знаешь любой язык, проскакивай к Этапу 1.

**Что нужно понимать:**
- как работает компьютер на пальцах: память, стек, куча, процессы и потоки;
- что такое компилируемый язык и чем он отличается от интерпретируемого;
- системы счисления, базовая алгебра логики;
- терминал, базовые команды bash/zsh;
- Git и GitHub: clone, commit, push, pull, branch, merge, rebase, PR.

**Материалы:**
- «Грокаем алгоритмы» Адитья Бхаргава — для интуиции;
- курс «Введение в программирование» от Хекслет (бесплатно);
- Pro Git (бесплатная книга на русском, git-scm.com/book/ru);
- MIT «Missing Semester» — терминал, Git, инструменты разработчика.

**Чек-пойнт:** можешь склонировать репозиторий, создать ветку, сделать коммит, открыть Pull Request и решить merge-конфликт без паники.

---

## 🟢 Этап 1. Синтаксис и основы Go (3–4 недели)

Здесь твоя задача — научиться читать и писать идиоматичный Go-код. Не учи язык как Python или Java: он другой по философии — меньше магии, больше явности.

**Темы:**
- установка Go, GOPATH vs Go modules, структура проекта;
- переменные, типы, константы, iota;
- управляющие конструкции: if, for, switch (особенно type switch);
- функции, множественный возврат, named returns, variadic;
- указатели — без них дальше никуда;
- структуры, методы, получатели по значению vs по указателю;
- интерфейсы — главная фишка Go, учить долго и вдумчиво;
- error handling: errors.Is, errors.As, обёртывание;
- срезы, массивы, мапы (как устроены внутри);
- panic, recover, defer и порядок их выполнения.

**Материалы:**
- A Tour of Go (go.dev/tour) — обязательно пройти полностью;
- «Go на практике» Алан Донован, Брайан Керниган — настольная книга;
- курс «Программирование на Go» от Stepik (бесплатный, на русском);
- канал Никиты Соболева и Алекса Карпова на YouTube;
- gobyexample.com — короткие примеры на каждый чих.

**Проект:** CLI-утилита для управления списком задач (todo) с сохранением в JSON-файл. С флагами через flag, цветным выводом и тестами.

**Чек-пойнт:** можешь объяснить разницу между срезом и массивом, что произойдёт при append к срезу с capacity = length, и когда метод нужно делать на указателе.

---

## 🟡 Этап 2. Глубокий Go (4–6 недель)

Этот этап отделяет Junior от Middle. Здесь учим, как Go устроен изнутри.

**Темы:**
- memory model: stack vs heap, escape analysis (`go build -gcflags="-m"`);
- как устроены slice, map, string, interface на уровне runtime;
- сборщик мусора (GC): tricolor marking, write barriers, GOGC;
- горутины и планировщик (GMP-модель) — на уровне понимания;
- generics (type parameters, constraints) — стандарт с 1.18;
- reflection и unsafe — знать, чтобы не использовать без причины;
- embedding структур и интерфейсов вместо наследования;
- идиомы: functional options, builder, errors as values.

**Материалы:**
- «100 Go Mistakes and How to Avoid Them» Тейва Харсаньи — обязательно;
- блог Дэйва Чейни (dave.cheney.net);
- доклады Go Devroom на FOSDEM, GopherCon (YouTube);
- статьи Уильяма Кеннеди (Ardan Labs).

**Проект:** свой in-memory key-value store с TTL, конкурентный, с benchmark-тестами и профилированием через pprof.

**Чек-пойнт:** можешь объяснить, что такое escape analysis, почему интерфейс — это два указателя и когда стоит, а когда не стоит использовать reflection.

---

## 🟡 Этап 3. Конкурентность (3–4 недели)

Главная причина, почему Go выбирают для бэкенда. Учи медленно и с практикой — здесь живут самые жёсткие баги.

**Темы:**
- горутины: запуск, жизненный цикл, утечки;
- каналы: буферизованные и небуферизованные, направленные;
- select, default, timeout-паттерн;
- sync: Mutex, RWMutex, WaitGroup, Once, Cond, Map, Pool;
- context: cancel, deadline, value, как правильно прокидывать;
- паттерны: pipeline, fan-in/fan-out, worker pool, semaphore;
- race detector (`go test -race`), data race vs race condition;
- atomic-операции, sync/atomic, package atomic.Pointer.

**Материалы:**
- «Concurrency in Go» Кэтрин Кокс-Будэй — лучшая книга по теме;
- статья «Go Concurrency Patterns» Роба Пайка (видео + текст);
- курс «Concurrency in Go» на Stepik;
- блог-серия Влада Михальчука по конкурентности (на русском).

**Проект:** многопоточный веб-краулер с ограничением скорости, retry-логикой, отменой через context и graceful shutdown.

**Чек-пойнт:** можешь без подсказок реализовать worker pool, объяснить, чем deadlock отличается от livelock, и когда канал лучше мьютекса.

---

## 🟢 Этап 4. Стандартная библиотека и инструменты (3 недели)

Стандартная библиотека Go — одно из её главных преимуществ. Многое из того, для чего в других языках нужны внешние пакеты, здесь есть из коробки.

**Темы:**
- io, bufio, io.Reader/Writer как фундаментальные абстракции;
- encoding/json, encoding/xml, encoding/gob;
- net/http: client, server, middleware-паттерн;
- log/slog (структурный логгер с 1.21);
- time, time.Ticker, time.AfterFunc;
- os, os/exec, signal handling;
- встроенные инструменты: go fmt, go vet, go doc, go mod;
- линтеры: golangci-lint, staticcheck.

**Материалы:**
- официальная документация pkg.go.dev — читать;
- «The Go Programming Language» — главы про стандартную библиотеку;
- доклад «Practical Go» Дэйва Чейни.

**Проект:** HTTP-клиент с retry, rate limiting и кешированием на диск.

---

## 🟡 Этап 5. Базы данных (3–4 недели)

**Темы:**
- SQL основы: SELECT, JOIN, индексы, EXPLAIN, нормализация;
- database/sql — стандартный интерфейс;
- драйверы: pgx (PostgreSQL), go-sql-driver/mysql;
- транзакции, уровни изоляции, deadlocks;
- query-builders: squirrel, goqu;
- ORM: GORM, ent, sqlc (последний — отдельный мастхэв);
- миграции: golang-migrate, goose;
- NoSQL: Redis (go-redis), MongoDB (mongo-go-driver);
- connection pool: настройка SetMaxOpenConns, SetMaxIdleConns.

**Материалы:**
- «Use the Database, Luke» — серия статей Маркуса Винанда;
- документация pgx и sqlc;
- курс «PostgreSQL для разработчиков» от Postgres Professional (на русском).

**Проект:** REST API для блога с PostgreSQL, миграциями, sqlc и нормальной работой с транзакциями.

**Чек-пойнт:** можешь нарисовать схему БД с тремя связанными таблицами, написать миграцию, объяснить, что такое N+1 проблема и как её избежать.

---

## 🟡 Этап 6. Web и API (4–6 недель)

**Темы:**
- HTTP в глубину: методы, статусы, заголовки, keep-alive, HTTP/2;
- маршрутизаторы: chi, gin, echo, fiber, стандартный mux 1.22+;
- middleware: логирование, recover, CORS, auth, rate limit;
- аутентификация: JWT, OAuth2, sessions;
- валидация: go-playground/validator;
- REST best practices, версионирование API;
- OpenAPI/Swagger: swaggo, oapi-codegen;
- WebSocket (gorilla/websocket, nhooyr/websocket);
- GraphQL (gqlgen) — на обзор;
- gRPC и Protocol Buffers.

**Материалы:**
- «Let's Go» и «Let's Go Further» Алекса Эдвардса — две лучшие книги по веб-разработке на Go;
- документация chi и gin;
- gRPC Tutorial с официального сайта.

**Проект:** социальная сеть-лайт: регистрация, посты, лайки, лента, JWT-аутентификация, swagger-документация.

---

## 🟢 Этап 7. Тестирование (2–3 недели)

**Темы:**
- testing package: TestMain, t.Run, t.Parallel, t.Helper;
- table-driven tests как стандарт индустрии;
- subtests и benchmark-тесты;
- testify (assert, require, suite, mock) — самый популярный;
- gomock и mockery для генерации моков;
- testcontainers-go для интеграционных тестов с реальной БД;
- fuzzing (`go test -fuzz`) — с 1.18;
- coverage и его адекватная интерпретация;
- integration vs unit vs e2e — где какие применять.

**Материалы:**
- «Learn Go with Tests» (бесплатная книга);
- доклад «Advanced Testing with Go» Митчелла Хашимото;
- блог Питера Боргона.

**Проект:** покрыть тестами один из предыдущих проектов на 80%+, с интеграционными тестами через testcontainers.

---

## 🟠 Этап 8. Микросервисы и сети (6–8 недель)

**Темы:**
- архитектура микросервисов: за и против, когда не нужно;
- gRPC и protobuf глубоко: streaming, interceptors, deadlines;
- очереди сообщений: Kafka, NATS, RabbitMQ — выбор и работа;
- service discovery: Consul, etcd;
- API Gateway: Kong, Traefik;
- circuit breaker, retry, timeout — паттерны устойчивости;
- distributed tracing: OpenTelemetry, Jaeger;
- saga-паттерн, outbox-паттерн, idempotency;
- межсервисная аутентификация: mTLS, JWT.

**Материалы:**
- «Building Microservices» Сэма Ньюмана (любое издание);
- «Designing Data-Intensive Applications» Мартина Клеппманна — обязательно;
- доклады с конференций Saint HighLoad, GoCloud.

**Проект:** интернет-магазин из 3–4 микросервисов: каталог, заказы, оплата, нотификации. С Kafka, gRPC и трейсингом.

---

## 🟠 Этап 9. DevOps минимум (3–4 недели)

Без этого Senior-ом не стать. Не обязательно быть DevOps, но язык понимать должен.

**Темы:**
- Docker: Dockerfile, multi-stage builds, docker-compose;
- Kubernetes: Pod, Deployment, Service, Ingress, ConfigMap, Secret;
- Helm — на уровне «прочитать чарт»;
- CI/CD: GitHub Actions, GitLab CI;
- Prometheus + Grafana: метрики, alert rules;
- логи: Loki, ELK-стек;
- линукс-минимум: процессы, сигналы, systemd, базовый sysadmin.

**Материалы:**
- «Kubernetes Up & Running» Бренда Бернса;
- курс «Docker и Kubernetes» от Слёрма (есть бесплатные части);
- блог Learnk8s.

**Проект:** задеплоить микросервисный проект из 8-го этапа в Kubernetes с метриками, логами и трейсингом.

---

## 🔴 Этап 10. Архитектура и паттерны (4–6 недель)

**Темы:**
- Clean Architecture в Go — и её адекватная критика;
- Hexagonal/Ports & Adapters;
- DDD-минимум: bounded context, aggregate, value object;
- CQRS и event sourcing;
- организация проекта: стандартный layout (golang-standards/project-layout) — и почему его не все любят;
- слои: handler → service → repository;
- dependency injection: вручную, wire, fx;
- идемпотентность, eventually consistent системы.

**Материалы:**
- «Чистая архитектура» Роберта Мартина;
- статьи и серия видео от Three Dots Labs (Watermill, DDD в Go);
- блог Бена Джонсона про структуру Go-проектов.

**Чек-пойнт:** можешь спроектировать сервис с правильным разделением слоёв, объяснить, почему интерфейсы определяются на стороне потребителя.

---

## 🔴 Этап 11. Performance и production (3–4 недели)

**Темы:**
- профилирование: pprof (CPU, heap, goroutine, block, mutex);
- flame graphs, continuous profiling (Pyroscope);
- benchmark-тесты, benchstat;
- оптимизация аллокаций: sync.Pool, переиспользование буферов;
- GOMAXPROCS, GOGC, GOMEMLIMIT — тюнинг рантайма;
- работа с большими объёмами данных, streaming;
- graceful shutdown, zero-downtime deploy;
- наблюдаемость: метрики RED, USE, SLO/SLI.

**Материалы:**
- доклады Felix Geisendörfer по pprof;
- блог Cloudflare про Go-производительность;
- «Systems Performance» Брендана Грегга — для общего понимания.

**Проект:** взять любой свой сервис, профилировать, найти 3 узких места и оптимизировать. Зафиксировать цифры до и после.

---

## 🟣 Этап 12. Подготовка к собесам (3 недели)

**Темы:**
- алгоритмы и структуры: массивы, строки, хеш-таблицы, деревья, графы, DP — на уровне easy/medium LeetCode;
- системный дизайн: TinyURL, Twitter feed, чат, нотификации;
- поведенческое интервью: STAR-метод;
- разбор частых Go-вопросов: nil interface, slice gotchas, defer execution, channel deadlocks;
- mock-интервью с друзьями или на pramp.com.

**Материалы:**
- LeetCode — топ-150 задач, тег Go;
- «Cracking the Coding Interview» — для общей подготовки;
- канал «Tech Interviews Pro» и материалы Алексея Голуба (на русском);
- репозиторий go-interview-questions и подобные.

---

## 🧰 Полезные источники на постоянку

- **Подкасты:** Go Time, GolangShow, Веб-стандарты, Радио-Т;
- **YouTube:** justforfunc, ArdanLabs, GopherCon, Никита Соболев;
- **Telegram:** @gogolang, @golang_ru, @gophers_ru;
- **Сообщества:** Gophers Slack, Reddit r/golang, форум gophers.ru;
- **Блоги:** dave.cheney.net, eli.thegreenplace.net, blog.golang.org.

---

## 📈 Как понять, что ты вырос

- **Junior:** пишешь CRUD, разбираешься в чужом коде с подсказками.
- **Middle:** проектируешь сервис с нуля, знаешь, почему делаешь так, а не иначе.
- **Senior:** принимаешь архитектурные решения, понимаешь trade-off, наставляешь других, видишь проблемы до их появления.

Не торопись прыгать в Senior по зарплате — лучше быть крепким Middle с глубоким пониманием, чем Senior, который не может объяснить, как работает планировщик.

---

## ⚠️ Чего избегать

- Туториал-ада: бесконечного просмотра курсов без написания кода.
- Слепого копирования архитектуры Clean Architecture в простой CRUD.
- Преждевременной оптимизации — сначала измеряй, потом оптимизируй.
- Микросервисов там, где хватит монолита.
- ORM-магии без понимания SQL.

---

## 🤝 Контрибьют

Нашёл ошибку или хочешь добавить материал — открывай PR или issue. Roadmap живой, обновляется по мере выхода новых версий Go и инструментов.

