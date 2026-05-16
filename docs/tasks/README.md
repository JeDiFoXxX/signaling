# Задачи разработки signaling

Пошаговый план v1 (REST + in-memory) и roadmap (WebSocket, auth, CI).  
Спецификация: [docs/spec.md](../spec.md).

## Зависимости Maven (по этапам)

| Зависимость | Задача | Назначение |
|-------------|--------|------------|
| *(уже в pom)* `spring-boot-starter-webmvc` | — | REST API |
| *(уже в pom)* `spring-boot-starter-websocket` | 13 | WebSocket (позже) |
| `spring-boot-starter-test` | [00](./00-bootstrap.md) | Единый test-starter (при необходимости заменяет раздельные test-стартеры) |
| `spring-boot-starter-validation` | [05](./05-service-storage-validation.md) | `jakarta.validation` на DTO |
| `spring-boot-starter-actuator` | [14](./14-makefile-ci.md) | `/actuator/health` для Docker/CI |
| `spring-boot-starter-oauth2-resource-server` | [13](./13-websocket-auth.md) | JWT на конечном этапе (если валидация локально) |

`@EnableScheduling` — только в [10-scheduler-cleanup.md](./10-scheduler-cleanup.md) (вместе с `RoomCleanupScheduler`).

## Порядок v1

| # | Файл | Содержание |
|---|------|------------|
| 00 | [00-bootstrap.md](./00-bootstrap.md) | Конфиг, test-starter, smoke |
| 01 | [01-room-status.md](./01-room-status.md) | `RoomStatus` |
| 02 | [02-dto-signaling.md](./02-dto-signaling.md) | `SignalingDto` |
| 03 | [03-dto-response.md](./03-dto-response.md) | `SignalingResponseDto` |
| 04 | [04-model-call-room.md](./04-model-call-room.md) | `CallRoom` |
| 05 | [05-service-storage-validation.md](./05-service-storage-validation.md) | Map, validation starter |
| 06 | [06-service-make-call.md](./06-service-make-call.md) | `make_call` |
| 07 | [07-service-conflicts.md](./07-service-conflicts.md) | 404/409 |
| 08 | [08-service-call-actions.md](./08-service-call-actions.md) | accept/reject/leave |
| 09 | [09-controller-rest.md](./09-controller-rest.md) | `POST /api/v1/signaling` |
| 10 | [10-scheduler-cleanup.md](./10-scheduler-cleanup.md) | `@EnableScheduling`, TTL |
| 11 | [11-exception-handler.md](./11-exception-handler.md) | JSON-ошибки |
| 12 | [12-integration-tests.md](./12-integration-tests.md) | E2E |
| 13 | [13-websocket-auth.md](./13-websocket-auth.md) | WS + oauth2-resource-server |
| 14 | [14-makefile-ci.md](./14-makefile-ci.md) | actuator, Makefile, Docker, CI |

## Статус

| Задача | Статус |
|--------|--------|
| 00–14 | не начато |
