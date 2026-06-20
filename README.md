# Практическое задание №7

Практическое занятие N7: контейнеризация учебного Go-сервиса `tasks`.

## Что внутри

- `services/tasks` - минимальный HTTP-сервис на Go.
- `services/tasks/Dockerfile` - multi-stage Docker-сборка.
- `services/tasks/.dockerignore` - исключает лишние файлы из build context.
- `deploy/docker-compose.yml` - запуск сервиса через Docker Compose.

## Запуск без Docker

```
cd services/tasks
go run ./cmd/tasks
curl http://localhost:8082/health
```
<img width="571" height="54" alt="image" src="https://github.com/user-attachments/assets/460c133b-f2c4-42be-bbf6-2bbdfe6a56ed" />
<img width="980" height="361" alt="image" src="https://github.com/user-attachments/assets/0a232a74-c38a-46f5-8f1f-f17048d257ea" />


## Запуск в Docker

```
cd services/tasks
docker build -t techip-tasks:0.1 .
docker run --rm -p 8082:8082 -e TASKS_PORT=8082 techip-tasks:0.1
```
<img width="1110" height="413" alt="image" src="https://github.com/user-attachments/assets/63225e24-37af-4fd3-8f2c-5bc78aa7f0fa" />

<img width="891" height="34" alt="image" src="https://github.com/user-attachments/assets/0b66ce98-ec9b-40a8-96a8-1c11569dc625" />



## Запуск через Compose

```
cd deploy
docker compose up -d --build
docker compose ps
docker compose logs -f
```
<img width="1263" height="156" alt="image" src="https://github.com/user-attachments/assets/417c7b17-2622-4455-8042-1e7bb6dc2cf7" />




