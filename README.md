# api_final
## Yatube API

Описание:
Yatube API — это RESTful API для социальной сети, где пользователи могут публиковать посты, комментировать их, создавать группы и подписываться на других пользователей. Проект реализован с использованием Django REST Framework (DRF) и предоставляет следующие возможности:
Создание, редактирование и удаление постов.
Добавление комментариев к постам.
Управление группами (создание и просмотр).
Подписка на других пользователей.
Аутентификация и авторизация с использованием JWT-токенов.
API предназначен для разработчиков, которые хотят интегрировать функциональность социальной сети в свои приложения.
____
## Установка:
1) Клонируйте репозиторий:
    ```
    git clone https://github.com/ваш-username/ваш-репозиторий.git
    cd {ваш-репозиторий}
    ```

2) Создайте и активируйте виртуальное окружение:
   ```
    python -m venv venv
    source venv/bin/activate  # Для Linux/MacOS
    venv\Scripts\activate     # Для Windows
   ```

4) Установите зависимости:
   ```
    pip install -r requirements.txt
   ```

6) Примените миграции:
   ```
    python manage.py migrate
   ```

8) Запустите сервер:
   ```
    python manage.py runserver
   ```

10) API будет доступен по адресу:
    http://127.0.0.1:8000/api/v1/
____

## Примеры запросов к API:

### Аутентификация:
Получение JWT-токена:
```
curl -X POST http://127.0.0.1:8000/api/v1/jwt/create/ \
     -H "Content-Type: application/json" \
     -d '{"username": "ваш-username", "password": "ваш-пароль"}'
```
Обновление JWT-токена:
```
curl -X POST http://127.0.0.1:8000/api/v1/jwt/refresh/ \
     -H "Content-Type: application/json" \
     -d '{"refresh": "ваш-refresh-токен"}'
```
    
### Посты:
Получение списка постов:
```
curl -X GET http://127.0.0.1:8000/api/v1/posts/ \
     -H "Authorization: Bearer ваш-токен"
```

Создание нового поста:
```
curl -X POST http://127.0.0.1:8000/api/v1/posts/ \
     -H "Authorization: Bearer ваш-токен" \
     -H "Content-Type: application/json" \
     -d '{"text": "Текст нового поста", "group": 1}'
```

### Комментарии:

Добавление комментария к посту:
```
curl -X POST http://127.0.0.1:8000/api/v1/posts/1/comments/ \
     -H "Authorization: Bearer ваш-токен" \
     -H "Content-Type: application/json" \
     -d '{"text": "Текст комментария"}'
```

Получение списка комментариев к посту:
```
curl -X GET http://127.0.0.1:8000/api/v1/posts/1/comments/ \
     -H "Authorization: Bearer ваш-токен"
```

### Группы:

Получение списка групп:
```
curl -X GET http://127.0.0.1:8000/api/v1/groups/ \
     -H "Authorization: Bearer ваш-токен"
```
### Подписки
Подписка на пользователя:
```
curl -X POST http://127.0.0.1:8000/api/v1/follow/ \
     -H "Authorization: Bearer ваш-токен" \
     -H "Content-Type: application/json" \
     -d '{"following": "username-пользователя"}'
```
Получение списка подписок пользователя:

```
curl -X GET http://127.0.0.1:8000/api/v1/follow/ \
     -H "Authorization: Bearer ваш-токен"
```

___

## Технологии
### Django — веб-фреймворк для создания API.

### Django REST Framework (DRF) — библиотека для создания RESTful API.

### Simple JWT — библиотека для аутентификации с использованием JWT-токенов.

### SQLite — база данных по умолчанию для разработки.

___
## Автор
### *Manakov Vadim (lolopogff)*
___
*P.S.*
В некоторых моментах код выглядит достаточно неоптимизированным (особенно вьюсеты). При оптимизации код не проходит тесты pytest, поэтому оставил в таком виде, как есть.
