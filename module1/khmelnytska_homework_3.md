# Завдання 1. Огляд активних процесів

```bash
ps aux
```

```bash
top
```

У `top` натиснути:

```text
Shift + M
```

Вийти з `top`:

```text
q
```

```bash
echo $$
```

```bash
ps
```

# Завдання 2. Робота у фоні та керування процесами

```bash
sleep 1000 &
```

```bash
jobs
```

```bash
fg
```

Після `fg` натиснути:

```text
Ctrl + Z
```

```bash
jobs
```

```bash
ps | grep sleep
```

```bash
kill -9 14
```

```bash
jobs
```

```bash
nohup sleep 1000 &
```

# Завдання 3. Пріоритети та обмеження

```bash
nice -n 10 sleep 1000 &
```

```bash
ps | grep sleep
```

```bash
sleep 1000 &
```

```bash
ps | grep sleep
```

```bash
renice 15 22
```

```bash
ulimit -a
```

# Завдання 4. Моніторинг ресурсів

```bash
df -h
```

```bash
free -h
```
