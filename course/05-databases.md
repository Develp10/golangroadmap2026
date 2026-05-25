# Модуль 5. Базы данных 🟡

**Срок:** 3–4 недели  
**Цель модуля:** научиться работать с реляционными БД, без которых не бывает production-сервисов. Плюс Redis для кэша.

---

## Урок 5.1. SQL-минимум

**📚 Теория:** `SELECT`, `WHERE`, `JOIN` (INNER/LEFT/RIGHT/FULL), `GROUP BY`, `HAVING`, агрегаты, подзапросы, CTE (`WITH`), оконные функции, `EXPLAIN ANALYZE`, индексы (B-tree, Hash, GIN), нормальные формы.

**💻 Практика:** поднять PostgreSQL в Docker, выполнить 20 запросов на тестовой БД (Sakila, Chinook).

---

## Урок 5.2. database/sql + pgx

**📚 Теория:** открытие пула (`pgxpool.New`), `QueryContext`, `QueryRowContext`, `Scan`, prepared statements, обработка `sql.ErrNoRows`.

**💻 Практика:** репозиторий `UserRepo` с методами `Create`, `GetByID`, `Update`, `Delete`, `List`.

---

## Урок 5.3. Транзакции

**📚 Теория:** ACID, уровни изоляции (Read Uncommitted / Read Committed / Repeatable Read / Serializable), феномены (dirty/phantom/non-repeatable read), deadlock'и, оптимистичные вс пессимистичные блокировки.

**💻 Практика:** перевод денег между счетами в транзакции с rollback при ошибке.

**✅ Чек:** разница Read Committed и Repeatable Read.

---

## Урок 5.4. Миграции

**📚 Теория:** `goose` или `golang-migrate`, up/down миграции, версионирование схемы, совместимые изменения (backward-compatible).

**💻 Практика:** напиши 5 миграций для библиотеки книг.

---

## Урок 5.5. Query Builder и codegen

**📚 Теория:** `squirrel` для динамических запросов, `sqlc` для генерации типобезопасного кода из SQL.

**💻 Практика:** перепиши `UserRepo` через `sqlc`.

---

## Урок 5.6. ORM (gorm)

**📚 Теория:** плюсы/минусы, soft delete, hooks, associations, N+1 проблема и как её ловить.

**⚠️ Красный флаг:** ORM в высоконагруженных запросах без знания, что генерируется.

---

## Урок 5.7. Redis

**📚 Теория:** `go-redis/redis`, типы (strings, lists, hashes, sets, sorted sets), кэш (TTL, cache stampede), очередь (`LPUSH`/`BRPOP`), pub/sub, distributed locks (Redlock).

**💻 Практика:** кэш для `UserRepo.GetByID` с инвалидацией при `Update`/`Delete`.

---

## 🎯 Проект модуля: Библиотека книг

REST-сервис `library`:
- CRUD книг и авторов
- - поиск по тексту (`tsvector` в Postgres)
  - - пагинация (cursor-based)
    - - кэш популярных книг в Redis
      - - миграции
       
        - **Критерии приёмки:** N+1 отсутствует, `EXPLAIN ANALYZE` показывает использование индексов, кэш инвалидируется корректно.
       
        - ---

        ## 🏁 Чек-пойнт модуля

        - [ ] Пишешь SQL на уровне JOIN, GROUP BY, CTE
        - [ ] - [ ] Понимаешь уровни изоляции
        - [ ] - [ ] Находишь N+1 и исправляешь её
        - [ ] - [ ] Пишешь миграции с backward-совместимостью
        - [ ] - [ ] Кэшируешь в Redis без cache stampede
       
        - [ ] **Предыдущий:** [Модуль 4 ←](04-stdlib.md) · **Следующий:** [Модуль 6. Web и API →](06-web-api.md)
        - [ ] 
