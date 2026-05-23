# Домашнє завдання module 6

## Варіант A — Скрипт бекапу логів

## Завдання 1. Створення тестових каталогів

```bash
mkdir -p logs
```

```bash
mkdir -p backups
```

## Завдання 2. Створення тестових log-файлів

```bash
echo "test log 1" > logs/app.log
```

```bash
echo "test log 2" > logs/error.log
```

## Завдання 3. Створення Bash-скрипта

```bash
nano backup.sh
```

## Код, який був вставлений у nano

```bash
#!/bin/bash

LOCK_FILE="/tmp/backup.lock"

if [ "$#" -ne 2 ]; then
    echo "Usage: ./backup.sh <log_dir><backup_dir>"
    exit 1
fi

LOG_DIR="$1"
BACKUP_DIR="$2"

if [ ! -d "$LOG_DIR" ] || [ ! -d "$BACKUP_DIR" ]; then
    echo "Usage: ./backup.sh <log_dir><backup_dir>"
    exit 1
fi

if [ -f "$LOCK_FILE" ]; then
    echo "Backup already running"
    exit 1
fi

touch "$LOCK_FILE"

DATE=$(date +"%Y-%m-%d_%H-%M")
ARCHIVE_NAME="logs_backup_${DATE}.tar.gz"
ARCHIVE_PATH="${BACKUP_DIR}/${ARCHIVE_NAME}"

tar -czf "$ARCHIVE_PATH" -C "$LOG_DIR" .

if [ "$?" -ne 0 ]; then
    echo "Backup failed"
    rm -f "$LOCK_FILE"
    exit 2
fi

rm -f "$LOCK_FILE"

FULL_PATH=$(realpath "$ARCHIVE_PATH")
echo "Backup created: $FULL_PATH"
```

## Завдання 4. Надання прав на запуск скрипта

```bash
chmod +x backup.sh
```

## Завдання 5. Перевірка успішного запуску скрипта

```bash
./backup.sh logs backups
```

## Завдання 6. Перевірка створеного архіву

```bash
ls -l backups
```

## Завдання 7. Перевірка вмісту архіву

```bash
tar -tzf backups/*.tar.gz
```

## Завдання 8. Перевірка запуску без аргументів

```bash
./backup.sh
```

## Завдання 9. Перевірка запуску з одним аргументом

```bash
./backup.sh logs
```

## Завдання 10. Перевірка запуску з неіснуючим каталогом

```bash
./backup.sh wrong_folder backups
```

## Завдання 11. Перевірка захисту від паралельного запуску

```bash
touch /tmp/backup.lock
```

```bash
./backup.sh logs backups
```

## Завдання 12. Видалення lock-файлу

```bash
rm -f /tmp/backup.lock
```

```bash
rm -f /tmp/backup.lock
```

## Короткий опис

Цей Bash-скрипт створює резервну копію файлів логів.

Скрипт запускається з двома аргументами: перший аргумент — це каталог з логами, другий аргумент — каталог для збереження резервної копії.

Спочатку скрипт перевіряє, чи передано рівно два аргументи. Також він перевіряє, чи обидва аргументи є існуючими каталогами. Якщо умови не виконуються, скрипт виводить повідомлення:

```bash
Usage: ./backup.sh <log_dir><backup_dir>
```

Після цього скрипт перевіряє lock-файл `/tmp/backup.lock`, щоб не допустити паралельний запуск. Якщо lock-файл уже існує, скрипт виводить:

```bash
Backup already running
```

Якщо перевірки пройдені успішно, скрипт створює архів у форматі `.tar.gz`. Назва архіву містить дату і час створення у форматі:

```bash
logs_backup_YYYY-MM-DD_HH-MM.tar.gz
```

Якщо архівація не вдалася, скрипт виводить:

```bash
Backup failed
```

Якщо архів створено успішно, скрипт виводить повний шлях до архіву.
