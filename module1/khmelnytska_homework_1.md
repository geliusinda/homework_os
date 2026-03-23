# Домашнє завдання №1. Основи Linux і робота в терміналі

## Завдання 1. Базові команди
cd ~
ls
cd Downloads
ls
echo "" > file1.txt
cat file1.txt
cd /home/geliusinda
cd ~


## Завдання 2. Робота з документацією

Команди:

man ls
help cd
man cat
man man
cp --help
mv --help

Відповіді:

1. Який ключ ls показує приховані файли?
-a

2. Який ключ у cat нумерує рядки?
-n

3. Чим відрізняються man і --help?
man — повна документація команди з детальним описом.
--help — коротка довідка прямо в терміналі.



## Завдання 3. Міні-сценарій

cd ~
mkdir test_folder
cd test_folder
echo "Hello" > test.txt
ls
cd ..
cd test_folder
man ls
