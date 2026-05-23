# Домашнє завдання №4. Пакети, сервіси та журнали

## Завдання 1. Менеджери пакетів

```bash
sudo apt update
sudo apt install tree -y
which tree
tree --version
dpkg -l | grep tree
sudo apt remove tree -y
tree --version
```

## Завдання 2. Керування сервісами через systemctl

```bash
sudo systemctl status cron
sudo systemctl stop cron
systemctl is-active cron
sudo systemctl start cron
systemctl is-active cron
sudo systemctl enable cron
systemctl is-enabled cron
```

## Завдання 3. Робота з логами

```bash
cd /var/log
sudo tail -n 10 syslog
sudo journalctl -p err -n 20
sudo journalctl -u cron -n 20
```

## Завдання 4. Створення власного сервісу

```bash
cd ~
nano myscript.sh
```

Вміст файлу `myscript.sh`:

```bash
#!/bin/bash

while true
do
    date >> /home/geliusinda/myscript_output.txt
    sleep 1
done
```

```bash
chmod +x ~/myscript.sh
sudo nano /etc/systemd/system/myscript.service
```

Вміст файлу `/etc/systemd/system/myscript.service`:

```ini
[Unit]
Description=My custom date writing script
After=network.target

[Service]
ExecStart=/home/geliusinda/myscript.sh
Restart=always
User=geliusinda

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl daemon-reload
sudo systemctl start myscript.service
sudo systemctl status myscript.service
tail ~/myscript_output.txt
sudo systemctl enable myscript.service
systemctl is-enabled myscript.service
```
