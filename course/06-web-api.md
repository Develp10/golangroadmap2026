# Модуль 6. Web и API 🟡

**Срок:** 4–6 недель  
**Цель модуля:** писать production-grade web-сервисы: REST, gRPC, WebSocket, JWT, Swagger.

---

## Урок 6.1. Современный http.ServeMux (Go 1.22+)

**📚 Теория:** pattern-роутинг с методами и path params (`GET /users/{id}`), приоритеты паттернов.

**💻 Практика:** REST API на чистом stdlib без фреймворков.

---

## Урок 6.2. Роутеры экосистемы

**📚 Теория:** `chi` (идиоматичный, близок к stdlib), `echo` (больше фичей), `gin` (популярный, но спорные решения). Сравнение API и производительности.

**💻 Практика:** перепиши тот же API на `chi`.

---

## Урок 6.3. Middleware

**📚 Теория:** logging, recover (ловит panic), CORS, RequestID, RealIP, tracing, rate limit, compression.

**💻 Практика:** напиши свои middleware: RequestID, Logging, Recover.

---

## Урок 6.4. Аутентификация

**📚 Теория:** сессии vs JWT (access + refresh), OAuth2 флоу, OpenID Connect, bcrypt/argon2 для паролей, ротация refresh-токенов.

**💻 Практика:** регистрация/логин с JWT, middleware для проверки токена.

**⚠️ Красный флаг:** хранишь пароль в открытом виде или через MD5/SHA1.

---

## Урок 6.5. Валидация

**📚 Теория:** `go-playground/validator`, теги, кастомные правила, локализация ошибок.

**💻 Практика:** валидация входящих DTO на регистрацию.

---

## Урок 6.6. gRPC + Protocol Buffers

**📚 Теория:** `.proto`-файлы, `protoc-gen-go`/`protoc-gen-go-grpc`, unary/server-streaming/client-streaming/bidirectional RPC, interceptors, deadlines, error handling.

**💻 Практика:** gRPC-сервис с одним unary RPC и одним streaming.

---

## Урок 6.7. WebSocket

**📚 Теория:** `gorilla/websocket` или `nhooyr.io/websocket`, ping/pong, broadcasting, hub-паттерн.

**💻 Практика:** чат на WebSocket с комнатами.

---

## Урок 6.8. OpenAPI/Swagger

**📚 Теория:** OpenAPI 3, `swaggo/swag` для генерации из комментариев, `oapi-codegen` для spec-first.

**💻 Практика:** сгенерируй Swagger UI для своего API.

---

## 🎯 Проект модуля: Мини-соцсеть

- REST API: регистрация, логин, лента постов, лайки
- - gRPC API для внутреннего взаимодействия
  - - WebSocket-чат между пользователями
    - - JWT-аутентификация
      - - Swagger-документация
       
        - **Критерии приёмки:** все эндпоинты валидируют вход, JWT ротируются, WebSocket корректно закрывает коннекты.
       
        - ---

        ## 🏁 Чек-пойнт модуля

        - [ ] Пишешь REST API и на stdlib, и на `chi`
        - [ ] - [ ] Понимаешь JWT и реализуешь ротацию refresh-токенов
        - [ ] - [ ] Работаешь с gRPC + Protocol Buffers
        - [ ] - [ ] Используешь WebSocket в production-стиле (hub, ping/pong)
        - [ ] - [ ] Генерируешь Swagger
       
        - [ ] **Предыдущий:** [Модуль 5 ←](05-databases.md) · **Следующий:** [Модуль 7. Тестирование →](07-testing.md)
        - [ ] 
