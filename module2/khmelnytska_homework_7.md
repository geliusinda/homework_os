# Домашнє завдання module 7

## Варіант A — Аналіз життєвого циклу контейнера

## Завдання 1. Запуск контейнера з простим застосунком

```bash
docker --version
```

```bash
docker pull python:3.12-slim
```

```bash
docker run -d --name simple-http -p 8080:8000 python:3.12-slim python -m http.server 8000
```

```bash
docker ps
```

```bash
curl http://localhost:8080
```

---

## Завдання 2. Перевірка процесу PID 1 усередині контейнера

```bash
docker exec -it simple-http ps aux
```

```bash
docker exec -it simple-http sh -c "cat /proc/1/cmdline && echo"
```

---

## Завдання 3. Перегляд логів контейнера

```bash
docker logs simple-http
```

---

## Завдання 4. Завершення контейнера

```bash
docker stop simple-http
```

```bash
docker ps -a
```

---

## Завдання 5. Повторна перевірка логів після зупинки

```bash
docker logs simple-http
```

---

## Завдання 6. Видалення контейнера

```bash
docker rm simple-http
```

---

## Завдання 7. Повторний запуск контейнера для додаткової перевірки PID 1

```bash
docker run -d --name simple-http -p 8080:8000 python:3.12-slim python -m http.server 8000
```

```bash
docker exec -it simple-http sh -c "cat /proc/1/cmdline && echo"
```

---

## Завдання 8. Остаточне очищення після виконання

```bash
docker stop simple-http
```

```bash
docker rm simple-http
```
