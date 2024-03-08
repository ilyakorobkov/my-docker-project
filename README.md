# my-docker-project
Проект сделан в рамках прохождения онлайн курсов на Скилбокс.

Процесс установки Docker и Docker Compose по инструкии преподавателя в видео уроках:
1. suddo apt update - обновление списка пакетов системы
2. sudo apt install apt-transport-https ca-certificates curl software-properties-common - установка необходимых пакетов для добавления репозитория Докер
3. curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -  - добавление официального ключа
4. sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" - Добавляем репозиторий Docker к списку APT
5. sudo apt update - обновление пакетов, чтобы докер добавился в репозиторий
6.  sudo apt install docker-ce - установка Докер

7.  docker --version - проверка версии докер (в моем случае Docker version 25.0.3, build 4debf41)
8.   sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose  - установка докер композ
9.   sudo chmod +x /usr/local/bin/docker-compose

10. nano hello.py - Разработка простой программы
11. print("Привет, мир!") - Ctrl + X, затем Y

12. чтобы добавить файл в репозиторий:
13. git init
14. git add hello.py
15. git commit -m "Добавлен простой скрипт на Python"
16. git branch -M main
17. git remote add origin https://github.com/ilyakorobkov/my-docker-project/
18. git push -u origin main

19. Создание Dockerfile
20. nano Dockerfile
21.  Используем базовый образ Python
FROM python:3.9

 Устанавливаем рабочую директорию в контейнере
WORKDIR /app

 Копируем файлы зависимостей в рабочую директорию
COPY requirements.txt ./

 Устанавливаем зависимости
RUN pip install --no-cache-dir -r requirements.txt

 Копируем остальные файлы приложения в контейнер
COPY . .

 Команда для запуска приложения при старте контейнера
CMD ["python", "hello.py"]

22. docker build -t my-python-app - собираем образ
23. docker run my-python-app - запускаем в контейнере

24. новый файл с именем docker-compose.yml в корневом каталоге
25. version: '3'
    services:
      myapp:
        build: .
        ports:
          - "8080:8080"

26. docker-compose up - запускаем контейнер

после выдало ошибку, нужно было пересобрать образ и добавить зависимости в requirements.txt (nano requirements.txt) - добавил flask и повторил процедуру

Все скрины и файлы добавлены к репозиторию.
