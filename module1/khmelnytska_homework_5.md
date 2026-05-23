# Домашнє завдання Module 5

## Завдання 1. Мережева діагностика

```bash
ip a
```

```bash
ping 8.8.8.8
```

```bash
ss -tulpn
```

---

## Завдання 2. SSH-доступ з ключами та config

```bash
ls ~/.ssh
```

```bash
ssh-keygen
```

```bash
ls ~/.ssh
```

```bash
sudo apt update
```

```bash
sudo apt install openssh-server rsync -y
```

```bash
sudo service ssh start
```

```bash
ss -tulpn | grep ssh
```

```bash
sudo service ssh status
```

```bash
ssh-copy-id geliusinda@localhost
```

```bash
ssh geliusinda@localhost
```

```bash
nano ~/.ssh/config
```

```bash
ssh myserver
```

```bash
exit
```

---

## Завдання 3. Копіювання файлів між машинами

```bash
echo "test" > test.txt
```

```bash
scp test.txt myserver:~/
```

```bash
ssh myserver "mkdir -p ~/sync_folder"
```

```bash
mkdir -p local_sync
```

```bash
echo "sync test" > local_sync/sync_test.txt
```

```bash
rsync -av local_sync/ myserver:~/sync_folder/
```

```bash
sftp myserver
```

```bash
ls
```

```bash
cd sync_folder
```

```bash
ls
```

```bash
exit
```
