# Модуль 4. Стандартная библиотека 🟢

**Срок:** 3 недели  
**Цель модуля:** выжать максимум из стандартной библиотеки Go — она невероятно мощная и в 80% случаев внешние библиотеки не нужны.

---

## Урок 4.1. net/http — клиент

**📚 Теория:** `http.Client`, `http.DefaultClient` (почему его не надо в production), таймауты (Dial, TLS, Response), `http.Transport`, connection pooling, повторы.

**💻 Практика:** обёртка над `http.Client` с retry и экспоненциальным backoff.

---

## Урок 4.2. net/http — сервер

**📚 Теория:** `http.Handler`/`HandlerFunc`, `http.ServeMux` (в Go 1.22+ с pattern-роутингом по методу и патху), middleware-паттерн через функции-декораторы.

**💻 Практика:** мини-API с эндпоинтами `GET /tasks`, `POST /tasks`, `DELETE /tasks/{id}` на чистом stdlib.

---

## Урок 4.3. encoding/json

**📚 Теория:** `Marshal`/`Unmarshal`, теги `json:"name,omitempty"`, `RawMessage`, кастомные `MarshalJSON`/`UnmarshalJSON`, streaming через `json.Decoder`/`json.Encoder`.

**💻 Практика:** свой `MarshalJSON` для `time.Time` в формате `dd.MM.yyyy`.

---

## Урок 4.4. io, bufio, os

**📚 Теория:** интерфейсы `io.Reader`/`io.Writer`/`io.Closer`, `io.Copy`, `bufio.Scanner` (осторожно с буфером больших строк!), `os.File`, `os.Open`/`os.Create`.

**💻 Практика:** прочитай файл 1 ГБ построчно, подсчитай частоту слов.

---

## Урок 4.5. time

**📚 Теория:** `time.Now`, `time.Parse`/`Format` (референсная дата!), монотонные часы, `Ticker`, `Timer`, `AfterFunc`, таймзоны.

**💻 Практика:** cron-подобный планировщик через `Ticker`.

---

## Урок 4.6. log/slog

**📚 Теория:** стандарт с Go 1.21, JSON/text handlers, уровни лога, атрибуты, контекстные поля, смена дефолтного логгера.

**💻 Практика:** логи в JSON с полями `request_id`, `user_id`, `latency_ms`.

---

## Урок 4.7. flag, os/signal, graceful shutdown

**📚 Теория:** парсинг аргументов через `flag`, перехват сигналов (`SIGINT`, `SIGTERM`), `signal.NotifyContext`, graceful shutdown сервера через `http.Server.Shutdown`.

---

## 🎯 Проект модуля: httpcheck

CLI-утилита `httpcheck`:
- принимает список URL через флаг `-f urls.txt` или stdin
- - делает параллельные запросы
  - - выводит таблицу: URL, статус, время ответа, размер
    - - поддерживает Ctrl+C для корректного завершения
     
      - **Критерии приёмки:** нет внешних зависимостей (`go.mod` пустой), логи в JSON, graceful shutdown.
     
      - ---

      ## 🏁 Чек-пойнт модуля

      - [ ] Свободно пишешь HTTP-сервер и клиент без фреймворков
      - [ ] - [ ] Используешь `log/slog` вместо старого `log`
      - [ ] - [ ] Реализуешь graceful shutdown
      - [ ] - [ ] httpcheck работает на чистой stdlib
     
      - [ ] **Предыдущий:** [Модуль 3 ←](03-concurrency.md) · **Следующий:** [Модуль 5. Базы данных →](05-databases.md)
      - [ ] 
