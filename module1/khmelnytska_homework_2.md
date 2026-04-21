# Домашнє завдання №2. Файлова система і права доступу

## Завдання 1
cd /
ls

cd /etc
ls

cd /home
ls

## Завдання 2
cd ~
mkdir lab2
cd lab2
touch file.txt
cp file.txt file_copy.txt
mv file_copy.txt renamed.txt
ln file.txt hardlink.txt
ln -s file.txt symlink.txt
find ~ -name "file.txt"

Приклад:
/root/lab2/file.txt

## Завдання 3
ls -l file.txt
chmod 444 file.txt
chmod u+w file.txt
umask
umask 022

## Завдання 4
adduser trainee
addgroup trainee wheel
id trainee
cat /etc/passwd | grep trainee
