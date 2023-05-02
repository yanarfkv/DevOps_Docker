# Базовый образ, на основе которого будет создаваться образ
FROM ubuntu:latest

# Информация о том, кто создал образ
MAINTAINER Yana Rafikova yana.rafikova2405@mail.ru

# Установка необходимых пакетов (Apache и MySQL)
RUN apt-get update && apt-get install -y apache2 mysql-server

# Установка рабочей директории
WORKDIR /var/www/html

# Определение переменных среды
ENV MYSQL_ROOT_PASSWORD=testPassword \
	MYSQL_DATABASE=testDB \
	MYSQL_USER=yana \
	MYSQL_PASSWORD=testPassword

# Копирование файлов в контейнер
COPY index.html .

# Настройка БД (копирование БД (testDB.sql) в каталог /docker-entrypoint-initdb.d)
ADD testDB.sql /docker-entrypoint-initdb.d

# Создание тома для хранения данных MySQL
VOLUME /var/lib/mysql

# Указание пользователя, от имени которого будет запускаться контейнер
USER yana

# Открытие портов для доступа к серверу и БД
EXPOSE 80 3306

# Запуск сервера и БД при старте контейнера
CMD service apache2 start && service mysql start && /bin/bash