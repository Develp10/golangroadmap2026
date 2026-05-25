# 🔐 Модуль 16. Security в Go

> **Срок:** 3–4 недели  
> **Уровень:** 🔴 Senior  
> **Цель модуля:** писать код, который не стыдно вынести в публичный интернет: знать OWASP, криптографию, supply chain, secrets management, zero-trust.

---

## Урок 16.1. Secure coding на Go

- 🎯 **Цель:** OWASP Top 10 в контексте Go, безопасные дефолты, валидация ввода.
- 📚 **Теория:** OWASP Top 10 (2021/2025), Go secure coding guidelines, статья Filippo Valsorda про safe defaults.
- 💻 **Практика:** прогнать `gosec`, `govulncheck`, `staticcheck` на проекте. Починить SQL injection, SSRF, path traversal в учебном уязвимом приложении.
- ✅ **Чек:** почему `fmt.Sprintf` в SQL — антипаттерн. Чем `html/template` отличается от `text/template`.
- ⚠️ **Красный флаг:** конкатенация строк для SQL/HTML/shell.

## Урок 16.2. Криптография практически

- 🎯 **Цель:** AEAD (AES-GCM, ChaCha20-Poly1305), KDF (argon2id, scrypt), HMAC, асимметрика, подписи.
- 📚 **Теория:** Filippo Valsorda blog, Cryptography Engineering (Schneier/Ferguson), [age](https://github.com/FiloSottile/age).
- 💻 **Практика:** реализовать «сейф» для секретов через age и `crypto/aes`. Хеширование паролей argon2id с правильными параметрами. Подпись JWT через EdDSA, разобрать риски `alg:none`.
- ✅ **Чек:** почему ECB запрещён. Когда HMAC, когда подпись. Что значит constant-time compare.
- ⚠️ **Красный флаг:** свой шифр / своя крипта. MD5/SHA1 для паролей. JWT-библиотека без проверки `alg`.

## Урок 16.3. TLS, mTLS, PKI

- 🎯 **Цель:** TLS 1.3, mTLS, ALPN, SNI, OCSP stapling, certificate pinning, internal PKI.
- 📚 **Теория:** RFC 8446, smallstep CA blog, Let's Encrypt docs.
- 💻 **Практика:** поднять собственный CA через `step-ca`, выпустить сертификаты, настроить mTLS между двумя Go-сервисами. SPIFFE/SPIRE сверху.
- ✅ **Чек:** что такое cipher suite в TLS 1.3 (их всего 5). Зачем нужен SNI. Что даёт mTLS поверх mesh.
- ⚠️ **Красный флаг:** `InsecureSkipVerify: true` в проде.

## Урок 16.4. AuthN/AuthZ: OAuth2, OIDC, RBAC/ABAC

- 🎯 **Цель:** OAuth2 flows, OIDC, PKCE, токены доступа, RBAC vs ABAC, ReBAC (Zanzibar).
- 📚 **Теория:** RFC 6749/7636/8252, OIDC спека, статьи про Google Zanzibar и OpenFGA.
- 💻 **Практика:** интегрировать сервис с OIDC-провайдером через `coreos/go-oidc`, реализовать PKCE-flow. Authorization через OpenFGA или casbin.
- ✅ **Чек:** разница access/id/refresh token. Когда PKCE обязателен. Почему JWT для сессий — спорно.
- ⚠️ **Красный флаг:** свой OAuth-сервер. JWT с длинным TTL без revocation.

## Урок 16.5. Secrets management и supply chain

- 🎯 **Цель:** Vault/SOPS/sealed-secrets, SBOM, sigstore, SLSA уровни, Go module proxy security.
- 📚 **Теория:** SLSA framework, sigstore/cosign docs, Go module mirror & checksum database.
- 💻 **Практика:** подписать Docker-образ cosign'ом, собрать SBOM через syft, проверить через grype. Хранить секреты в Vault, доставать на старте через agent.
- ✅ **Чек:** что даёт `go.sum` и Go checksum DB. Что такое SLSA Level 3.
- ⚠️ **Красный флаг:** секреты в env-vars в репо. `go get` через прокси без verification.

## Урок 16.6. Container & runtime security

- 🎯 **Цель:** distroless/scratch образы, non-root, read-only FS, seccomp/AppArmor, Falco, Trivy.
- 📚 **Теория:** Aqua Security cloud-native security, NIST 800-190, Falco docs.
- 💻 **Практика:** уменьшить Go-образ до scratch+CA bundle, прогнать Trivy. Включить Pod Security Standards `restricted` и починить нарушения.
- ✅ **Чек:** зачем CAP_NET_BIND_SERVICE может быть нужен. Почему readonly rootfs ломает /tmp.
- ⚠️ **Красный флаг:** Go-сервис на `ubuntu:latest` от root.

## Урок 16.7. Zero-trust и threat modeling

- 🎯 **Цель:** STRIDE, attack trees, BeyondCorp, network policies, mTLS-everywhere, least privilege.
- 📚 **Теория:** "Threat Modeling" (Adam Shostack), Google BeyondCorp papers, NIST 800-207.
- 💻 **Практика:** провести STRIDE для своего сервиса, выписать митигации. Настроить NetworkPolicy в k8s с default-deny.
- ✅ **Чек:** буквы STRIDE и пример каждой. Что значит zero-trust в сети.
- ⚠️ **Красный флаг:** «у нас VPN, поэтому внутренние сервисы без auth».

---

## 🎯 Проект модуля

**Secure-by-default REST-сервис.**

Критерии приёмки:
- OIDC + PKCE для пользователей, mTLS между сервисами.
- Argon2id для паролей, AES-GCM для шифрования полей.
- SBOM + cosign-подпись образа.
- gosec/govulncheck/trivy в CI, без findings уровня high.
- NetworkPolicy default-deny + Pod Security `restricted`.
- STRIDE-документ и threat model в репо.

---

## 🏁 Чек-пойнт модуля

- [ ] Не пишу свою крипту, знаю, какие примитивы брать.
- [ ] Настраивал TLS/mTLS руками с нуля.
- [ ] Понимаю OAuth2/OIDC до уровня flows.
- [ ] Собирал и подписывал SBOM.
- [ ] Делал threat model для реального сервиса.

---

[← Модуль 15. Observability & SRE](./15-observability.md) | [Модуль 17. Cloud Native & K8s Operators →](./17-cloud-native.md)
