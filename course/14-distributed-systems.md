# 🌐 Модуль 14. Distributed Systems

> **Срок:** 6–8 недель  
> **Уровень:** 🔴 Senior  
> **Цель модуля:** проектировать распределённые системы на Go: понимать CAP, консистентность, консенсус, отказоустойчивость; уметь спорить про trade-off'ы без чтения статей в реальном времени.

---

## Урок 14.1. Фундамент распределённых систем

- 🎯 **Цель:** свободно говорить про CAP, PACELC, FLP, линеаризуемость и причинность.
- 📚 **Теория:** Martin Kleppmann "DDIA" (главы 5–9), статьи Jepsen, Aphyr.
- 💻 **Практика:** разобрать 5 реальных систем (Postgres, Cassandra, Kafka, etcd, DynamoDB) по CAP/PACELC и уровням изоляции.
- ✅ **Чек:** отличаешь линеаризуемость от serializability. Объясняешь split-brain на примере.
- ⚠️ **Красный флаг:** «у нас CP-система» без понимания, что именно мы теряем при partition.

## Урок 14.2. Time, clocks, ordering

- 🎯 **Цель:** понимать NTP/PTP, monotonic clock, Lamport timestamps, vector clocks, hybrid logical clocks.
- 📚 **Теория:** Lamport "Time, Clocks and Ordering of Events", статьи про HLC и TrueTime.
- 💻 **Практика:** реализовать на Go vector clock и HLC. Сравнить с monotonic time из `time.Now()`.
- ✅ **Чек:** почему wall-clock time в распределёнке опасен. Где HLC лучше Lamport.
- ⚠️ **Красный флаг:** использование `time.Now()` для упорядочивания событий между нодами.

## Урок 14.3. Консенсус: Raft, Paxos, ZAB

- 🎯 **Цель:** понимать Raft на уровне реализации, знать про Multi-Paxos, EPaxos, ZAB.
- 📚 **Теория:** Raft paper (Ongaro & Ousterhout), https://raft.github.io, исходники `hashicorp/raft` и `etcd-io/raft`.
- 💻 **Практика:** реализовать минимальный Raft (leader election + log replication) на Go. Тесты на split-brain и leader failure.
- ✅ **Чек:** объясняешь term, commitIndex, matchIndex. Что такое pre-vote и зачем.
- ⚠️ **Красный флаг:** «возьмём Raft из библиотеки и всё будет ок» без понимания снапшотов и compaction.

## Урок 14.4. Replication, репликационные модели

- 🎯 **Цель:** sync/async/semi-sync replication, leader-based, leaderless (Dynamo-style), multi-leader.
- 📚 **Теория:** DDIA глава 5, статьи про Cassandra (Dynamo paper), CRDT (Marc Shapiro).
- 💻 **Практика:** реализовать G-Counter и LWW-Set как CRDT на Go. Симулировать сеть с задержками и потерями.
- ✅ **Чек:** в чём преимущество quorum reads/writes (R+W>N). Где CRDT уместен, где — нет.
- ⚠️ **Красный флаг:** «multi-master без конфликтов, потому что мы умные».

## Урок 14.5. Distributed transactions: 2PC, Saga, Outbox

- 🎯 **Цель:** уметь выбрать между 2PC, TCC, Saga (orchestration/choreography), Outbox/Inbox.
- 📚 **Теория:** Chris Richardson "Microservices Patterns", статьи про Saga и Outbox.
- 💻 **Практика:** написать Saga-оркестратор на Go с компенсациями (заказ → платёж → склад → доставка). Outbox с публикацией в Kafka/NATS exactly-once.
- ✅ **Чек:** почему 2PC плохо масштабируется. Как Outbox решает dual write problem.
- ⚠️ **Красный флаг:** dual write «БД + брокер» без транзакционного outbox.

## Урок 14.6. Idempotency, exactly-once, retry storms

- 🎯 **Цель:** идемпотентные API, dedup-ключи, jittered backoff, circuit breaker, hedged requests.
- 📚 **Теория:** Marc Brooker "Exponential Backoff and Jitter", статьи AWS про timeouts.
- 💻 **Практика:** обернуть HTTP-клиент в middleware с retry+jitter+circuit breaker (gobreaker). Idempotency-Key в REST API.
- ✅ **Чек:** разница at-least-once и exactly-once-effectively. Когда нужны hedged requests.
- ⚠️ **Красный флаг:** retry без backoff и jitter — гарантированный thundering herd.

## Урок 14.7. Service discovery, load balancing, mesh

- 🎯 **Цель:** client-side vs server-side LB, consistent hashing, Envoy/Istio/Linkerd, gRPC LB policies.
- 📚 **Теория:** Envoy docs, gRPC LB design doc, статьи про consistent hashing (Karger, Jump Hash).
- 💻 **Практика:** реализовать Jump Consistent Hash на Go. Сравнить round-robin, least-request и consistent hashing на симуляции.
- ✅ **Чек:** когда нужен service mesh, а когда хватит библиотеки. Что такое xDS.
- ⚠️ **Красный флаг:** mesh «потому что модно» — на 3 сервиса.

## Урок 14.8. Streaming и event-driven архитектура

- 🎯 **Цель:** Kafka/NATS JetStream/Pulsar — partitioning, consumer groups, exactly-once semantics, compaction.
- 📚 **Теория:** Kafka definitive guide, статьи Confluent про EOS, NATS docs.
- 💻 **Практика:** event sourcing-сервис на Go + Kafka: команды → события → проекции (CQRS). Реплей событий.
- ✅ **Чек:** что гарантирует Kafka EOS и какой ценой. Когда event sourcing вреден.
- ⚠️ **Красный флаг:** event sourcing для CRUD-формочки.

---

## 🎯 Проект модуля

**Распределённое key-value хранилище с Raft-репликацией.**

Критерии приёмки:
- 3–5 нод, leader election, log replication, snapshot.
- gRPC API: Get/Put/Delete/Watch.
- Linearizable reads (через read index или lease).
- Тесты с jepsen-like симуляцией: kill leader, network partition, clock skew.
- Метрики Prometheus: raft term, commit lag, leader changes.
- README с trade-off'ами и схемой.

---

## 🏁 Чек-пойнт модуля

- [ ] Спокойно обсуждаю CAP/PACELC на собесе.
- [ ] Реализовывал Raft (хотя бы учебный) сам.
- [ ] Применял Saga и Outbox в боевом коде.
- [ ] Понимаю exactly-once в Kafka и его ограничения.
- [ ] Различаю service discovery, LB и service mesh.

---

[← Модуль 13. Go Runtime & Internals](./13-runtime-internals.md) | [Модуль 15. Observability & SRE →](./15-observability.md)
