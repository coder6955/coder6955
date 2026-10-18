# Uday Vishnu Patil

**Senior Backend Engineer | Java, Spring Boot, event-driven systems**

I'm a backend engineer based in Mumbai, India, with 10+ years of experience across Java and Python services, microservices, data processing, and cloud deployments. I'm open to remote senior backend engineering roles.

My work includes Kafka and Debezium CDC pipelines, transactional outbox workflows, Redis caching and atomic Lua operations, and containerized services on AWS. I focus on data consistency, failure handling, and making production systems easier to operate.

[LinkedIn](https://www.linkedin.com/in/uday-patil-dev/) · [Accepted contributions](https://github.com/pulls?q=is%3Apr+author%3Acoder6955+is%3Amerged) · [Open pull requests](https://github.com/pulls?q=is%3Apr+author%3Acoder6955+is%3Aopen)

## Selected open-source work

Status checked on **18 October 2026**. Pull request links show the latest review and merge status.

| Project | Contribution | Status |
| --- | --- | --- |
| [Apprise](https://github.com/caronc/apprise/pull/1756) | Fixed Matrix rich-text title/body separation and matching message-size accounting; added regression coverage for direct and encrypted notifications. | **Merged** |
| [Kroxylicious](https://github.com/kroxylicious/kroxylicious/pull/5112) | Replaced deprecated Java Operator SDK APIs, migrated operator metrics, and documented metric-name and PromQL changes. Verified 118 focused operator tests; [upstream unit tests passed on Java 21 and 25](https://github.com/kroxylicious/kroxylicious/actions/runs/38729111778). | Open; Kubernetes and documentation CI also passed; awaiting review |
| [Kroxylicious](https://github.com/kroxylicious/kroxylicious/pull/5113) | Fixed Kafka share-group cleanup so a missing group cannot mask a consumption failure. Verified 486 module tests on Linux and five additional share-consumer runs. | Open; ready for review |
| [Failsafe](https://github.com/failsafe-lib/failsafe/pull/402) | Proposed a fix for circuit breaker statistics after inactivity, with deterministic clock-based tests and a regression for the failure threshold. | Open; awaiting review |
| [ThingsBoard](https://github.com/thingsboard/thingsboard/pull/16248) | Quoted and escaped PostgreSQL timeseries partition identifiers; verified generated DDL and TTL paths against PostgreSQL. | Draft; full build validation pending |
| [JHipster](https://github.com/jhipster/jhipster.github.io/pull/1745) | Corrected a Bootstrap Sass example that failed to compile; verified import order against generator templates and compiled the example. | Open; ready for review |
| [Apprise](https://github.com/caronc/apprise/pull/1760) | Proposed optional YAML support for embedded applications, with isolated interpreter tests and branch coverage for disabled/missing YAML. | Closed; not merged |

[Read the Failsafe case study: diagnosing a sliding-window circuit breaker bug](https://github.com/coder6955/coder6955/blob/main/case-studies/failsafe-circuit-breaker.md).

### Investigation and regression coverage

For [REA's SQLite snapshot size-limit issue](https://github.com/morluto/rea/issues/4127#issuecomment-6194342656), I implemented a typed, non-retryable resource-limit error with exact byte counts and CLI/MCP regression coverage. Linux validation passed 122 tests with three conditional skips, plus static and documentation checks. I also verified the compiled CLI against a real 270 MB database. The tested patch and evidence were shared for reuse in an overlapping contribution; I did not submit a separate PR.

## Engineering experience

- **EZCONTACTS, Apr 2024-present:** backend modernization with Spring Boot, Kafka/Debezium CDC, transactional outbox, Redis, AWS ECS, and centralized logging.
- **JUSTDIAL, Aug 2020-Apr 2024:** Java/Python APIs, large-file ingestion, asynchronous processing, database optimization, and cloud delivery.
- **Earlier roles:** backend APIs, automation, payments, reporting, and production delivery across Java, Python, and PHP systems.

## Core stack

| Area | Technologies |
| --- | --- |
| Backend | Java, Spring Boot, Python, Flask, REST APIs |
| Messaging and consistency | Kafka, Debezium CDC, transactional outbox, RabbitMQ |
| Data | PostgreSQL, MySQL, Redis, Lua |
| Deployment and operations | AWS, Docker, Kubernetes, CI/CD, ELK, Prometheus, Grafana |

I'm interested in backend reliability, event-driven architecture, and practical distributed systems engineering.
