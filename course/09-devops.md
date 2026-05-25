# Модуль 9. DevOps минимум 🟠

**Срок:** 3–4 недели  
**Цель модуля:** научиться выкатывать Go-приложения в production — Docker, Kubernetes, CI/CD, мониторинг.

---

## Урок 9.1. Docker

**📚 Теория:** Dockerfile, слои, кэш сборки, multi-stage builds, минимальные образы (distroless, scratch, alpine), `CGO_ENABLED=0` для статической линковки.

**💻 Практика:** Dockerfile для Go-сервиса в ~10 МБ (multi-stage + distroless).

---

## Урок 9.2. docker-compose

**📚 Теория:** services, networks, volumes, healthchecks, depends_on, environment variables, profiles.

**💻 Практика:** локальное окружение для маркетплейса: 4 сервиса + Postgres + Redis + Kafka.

---

## Урок 9.3. Kubernetes базово

**📚 Теория:** Pod, Deployment, Service (ClusterIP/NodePort/LoadBalancer), ConfigMap, Secret, Ingress, namespace, labels и selectors, kubectl-команды.

**💻 Практика:** разверни Go-сервис в `minikube` или `kind`.

---

## Урок 9.4. Helm

**📚 Теория:** чарты, templates, values.yaml, dependencies, releases, upgrade/rollback.

**💻 Практика:** Helm-чарт для одного сервиса.

---

## Урок 9.5. CI/CD на GitHub Actions

**📚 Теория:** workflows, jobs, steps, actions (`actions/checkout`, `actions/setup-go`), кэш зависимостей, matrix builds, secrets, environment, reusable workflows.

**💻 Практика:** pipeline: linter → tests → build → push в ghcr.io.

---

## Урок 9.6. Мониторинг

**📚 Теория:** Prometheus (scrape model, PromQL), `prometheus/client_golang`, 4 золотых сигнала (latency, traffic, errors, saturation), Grafana для дашбордов, alerting rules.

**💻 Практика:** экспорт метрик `http_requests_total`, `http_request_duration_seconds`, дашборд в Grafana.

---

## Урок 9.7. Production-логи

**📚 Теория:** структурированные JSON-логи, уровни, корреляция с трейсами (`trace_id`, `span_id`), Loki/ELK для агрегации, log levels в production.

**⚠️ Красный флаг:** логи в production на `Debug`-уровне или `fmt.Println`.

---

## 🎯 Практика модуля

Возьми маркетплейс из Модуля 8:
- упакуй каждый сервис в multi-stage Docker-образ
- - напиши docker-compose для локального развёртывания
  - - разверни в `kind`/`minikube` с Helm
    - - настрой GitHub Actions: lint + test + build + push
      - - экспортируй метрики в Prometheus, визуализируй в Grafana
       
        - ---

        ## 🏁 Чек-пойнт модуля

        - [ ] Пишешь multi-stage Dockerfile для Go
        - [ ] - [ ] Разворачиваешь приложение в Kubernetes
        - [ ] - [ ] Настраиваешь CI/CD на GitHub Actions
        - [ ] - [ ] Экспортируешь метрики Prometheus
        - [ ] - [ ] Логи в JSON с корреляцией
       
        - [ ] **Предыдущий:** [Модуль 8 ←](08-microservices.md) · **Следующий:** [Модуль 10. Архитектура и паттерны →](10-architecture.md)
        - [ ] 
