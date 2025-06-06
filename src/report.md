# Simple Docker

## Part 1. Готовый докер

##### Возьми официальный докер-образ с **nginx** и выкачай его при помощи `docker pull`.
![image](screens/p1.1.png)

##### Проверь наличие докер-образа через `docker images`.
![image](screens/p1.2.png)

##### Запусти докер-образ через `docker run -d [image_id|repository]`.
![image](screens/p1.3.png)

##### Проверь, что образ запустился через `docker ps`.
![image](screens/p1.4.png)

##### Посмотри информацию о контейнере через `docker inspect [container_id|container_name]`.
По выводу команды определи и помести в отчёт размер контейнера, список замапленных портов и ip контейнера.\
![image](screens/p1.5.1.png)\
![image](screens/p1.5.2.png)\
![image](screens/p1.5.3.png)
###### размер контейнера - 188 Mбайт
###### список замапленных портов - 80
###### ip контейнера - 172.17.0.2

##### Останови докер образ через `docker stop [container_id|container_name]`. Проверь, что образ остановился через `docker ps`.
![image](screens/p1.6.png)
![image](screens/p1.7.png)

##### Запусти докер с портами 80 и 443 в контейнере, замапленными на такие же порты на локальной машине, через команду *run*.
![image](screens/p1.8.png)

##### Проверь, что в браузере по адресу *localhost:80* доступна стартовая страница **nginx**.
![image](screens/p1.9.png)

##### Перезапусти докер контейнер через `docker restart [container_id|container_name]`. Проверь любым способом, что контейнер запустился.
![image](screens/p1.10.png)

## Part 2. Операции с контейнером

##### Прочитай конфигурационный файл *nginx.conf* внутри докер контейнера через команду *exec*.
![image](screens/p2.1.png)
##### Создай на локальной машине файл *nginx.conf*. Настрой в нем по пути */status* отдачу страницы статуса сервера **nginx**.
![image](screens/p2.2.png)
##### Скопируй созданный файл *nginx.conf* внутрь докер-образа через команду `docker cp`.
![image](screens/p2.3.png)
##### Перезапусти **nginx** внутри докер-образа через команду *exec*.Проверь, что по адресу *localhost:80/status* отдается страничка со статусом сервера **nginx**.
![image](screens/p2.34.png)

##### Экспортируй контейнер в файл *container.tar* через команду *export*.Останови контейнер.
![image](screens/p2.5.png)
##### Удали образ через `docker rmi [image_id|repository]`, не удаляя перед этим контейнеры.
##### Удали остановленный контейнер.
![image](screens/p2.6.png)

##### Импортируй контейнер обратно через команду *import*.
![image](screens/p2.7.png)
##### Запусти импортированный контейнер.
![image](screens/p2.8.png)
##### Проверь, что по адресу *localhost:80/status* отдается страничка со статусом сервера **nginx**.
![image](screens/p2.9.png)

## Part 3. Мини веб-сервер

##### Напиши мини-сервер на **C** и **FastCgi**, который будет возвращать простейшую страничку с надписью `Hello World!`.
![image](screens/p3.3.png)
##### Запусти написанный мини-сервер через *spawn-fcgi* на порту 8080. Напиши свой *nginx.conf*, который будет проксировать все запросы с 81 порта на *127.0.0.1:8080*.
![image](screens/p3.2.png)
##### Проверь, что в браузере по *localhost:81* отдается написанная тобой страничка.
![image](screens/p3.1.png)

## Part 4. Свой докер

#### Напиши свой докер-образ, который:
##### 1) собирает исходники мини сервера на FastCgi из [Части 3](#part-3-мини-веб-сервер);
##### 2) запускает его на 8080 порту;
##### 3) копирует внутрь образа написанный *./nginx/nginx.conf*;
##### 4) запускает **nginx**.
![image](screens/p4.7.png)
##### Собери написанный докер-образ через `docker build` при этом указав имя и тег.
![image](screens/p4.1.png)
##### Проверь через `docker images`, что все собралось корректно.
![image](screens/p4.3.png)
##### Запусти собранный докер-образ с маппингом 81 порта на 80 на локальной машине и маппингом папки *./nginx* внутрь контейнера по адресу, где лежат конфигурационные файлы **nginx**'а
![image](screens/p4.4.png)
##### Проверь, что по localhost:80 доступна страничка написанного мини сервера.
![image](screens/p4.8.png)
##### Допиши в *./nginx/nginx.conf* проксирование странички */status*, по которой надо отдавать статус сервера **nginx**.
![image](screens/p4.9.png)
##### Перезапусти докер-образ.Проверь, что теперь по *localhost:80/status* отдается страничка со статусом **nginx**
![image](screens/p4.10.png)



## Part 5. **Dockle**
##### Просканируй образ из предыдущего задания через `dockle [image_id|repository]`.
![image](screens/p5.1.png)
##### Исправь образ так, чтобы при проверке через **dockle** не было ошибок и предупреждений.
![image](screens/p4.11.png)

