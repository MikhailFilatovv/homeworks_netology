# Домашнее задание к занятию "HTTP/HTTPS" Михаил Филатов

### Задание 1.

#### Описание задания
Перед вами стоит задача создать и настроить Nginx веб-сервер.

#### Требование к результату
- Вы должны отправить скриншот с выполненным заданием.
- К выполненной задаче добавьте скриншот выполненной переадресации.
- В ответе пришлите скриншоты работающей страницы https://localhost и страницы с 301 ответом.

#### Процесс выполнения

1. Запустите программу VirtualBox
2. В программе VirtualBox загрузите операционную систему Ubuntu, если она у вас не установлена в качестве основной системы.
3. Установите Nginx:

```
sudo apt-get install nginx
```
4. Сгенерируйте сертификат для него указав localhost в качестве CN  

```
sudo openssl req -x509 -nodes -newkey rsa:4096 -keyout /etc/nginx/cert.key -out /etc/nginx/cert.pem -days 365
```


5. Замените блок http {  } в файле /etc/nginx/nginx.conf на:

```
http {
    gzip on;
    server {
        listen 80 default_server;
        root   /var/www/public;
        listen  443 ssl http2 default_server;
        server_name  localhost;
        ssl_certificate  /etc/nginx/cert.pem;
        ssl_certificate_key /etc/nginx/cert.key;
        ssl_protocols   TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers   HIGH:!aNULL:!MD5;
        location / {
            index index.html;
        }
    }
}
```

6. Создайте файл /var/www/public/index.html c содержимым.
```
<h1>It works</h1>
```
7. Зайдите на страницу в браузере, пропустив сообщение о неработающем сертификате.
8. Пришлите скриншот работающей страницы https://localhost.
9. Измените конфигурацию сервера добавив переадресацию c Вашего сервера на сайт netology.ru.
```
location / {
  return 301 https://netology.ru;
}
```
10. Используя curl, сделайте запрос к своему серверу.

---

## Ответ:
Через браузер захожу по IP гостевой ОС

![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn1.jpg)
![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn3.jpg)
![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn2.jpg)
![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn4.jpg)

---

### Задание 2.

#### Описание задания
Перед вами стоит задача создать и настроить Apache2 веб-сервер.

#### Требование к результату
- Вы должны отправить скриншоты с выполненным заданием
- К выполненной задаче добавьте результат получившейся конфигурации.

#### Процесс выполнения
1. Запустите программу VirtualBox
2. В программе VirtualBox загрузите вторую виртуальную машину с  операционной системой Ubuntu. 
3. Используя документацию [https://httpd.apache.org/docs/current/](https://httpd.apache.org/docs/current/), установите apache2 веб-сервер. 
4. Выполните аналогичные действия как и задании 1, добившись аналогичной работы сервера.

---
## Ответ:

Через браузер захожу по IP гостевой ОС

![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn5.jpg)
![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn8.jpg)
![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn6.jpg)
![skrin](https://github.com/MikhailFilatovv/git_hw/blob/main/img/http_skrn7.jpg)