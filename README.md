# Проект «API для Yatube»
### Описание
Yatube - это социальная сеть для публикации своих постов. Пользователи могут просматривать посты, подписываться на авторов и комментировать их записи
через программный интерфейс взаимодействия.

Документация будет доступна по адресу http://127.0.0.1:8000/redoc/ после того, как вы запустите проект. В документации описано, как должен работать ваш API. Документация представлена в формате **Redoc**.
### Технологии
* Python 3.9
* Django 3.2.16
* Django REST Framework
### Как запустить проект
* Создайте и активируйте виртуальное окружение
```
python3 -m venv env
```
```
source env/bin/activate
```
* Установите зависимости из файла requirements.txt
```
python3 -m pip install --upgrade pip
```
```
pip install -r requirements.txt
```
* Выполните миграции:
```
python3 manage.py migrate
```
* Запустите проект:
```
python3 manage.py runserver
```
### Аутентификация
Для аутентификации используются JWT-токены.

#### Пример регистрации нового пользователя
1. Придумайте новую пару «логин-пароль» и отправьте POST-запрос на http://127.0.0.1:8000/api/v1/users/, передав их в полях username и password.
```
{
    "username": "newuser",
    "password": "Changeme!1"
} 
```
Пример ответа:
```
{
    "email": "",
    "username": "newuser",
    "id": 6
}
```

2. Теперь можно получить токен: отправьте POST-запрос на эндпоинт /v1/jwt/create/, передав действующий логин и пароль в полях username и password. 

Пример ответа:
```
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTYyMDk0MTQ3NywianRpIjoiODUzYzE5MTg5NzMwNDQwNTk1ZjI3ZTBmOTAzZDcxZDEiLCJ1c2VyX2lkIjoxfQ.0vJBPIUZG4MjeU_Q-mhr5Gqjx7sFlO6AShlfeINK8nA",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjIwODU1Mzc3LCJqdGkiOiJkY2EwNmRiYTEzNWQ0ZjNiODdiZmQ3YzU2Y2ZjNGE0YiIsInVzZXJfaWQiOjF9.eZfkpeNVfKLzBY7U0h5gMdTwUnGP3LjRn5g8EIvWlVg"
}
```

### Примеры запросов
#### Получение публикаций
Отправьте GET-запрос на эндпоинт v1/posts/?limit=2&offset=4
Пример ответа:
```
{
    "count": 10,
    "next": "http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=6",
    "previous": "http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=2",
    "results": [
        {
            "id": 21,
            "author": "newuser",
            "text": "string_1",
            "pub_date": "2023-02-12 11:19:19",
            "image": null,
            "group": 2
        },
        {
            "id": 22,
            "author": "newuser",
            "text": "string_2",
            "pub_date": "2023-02-12 11:20:39",
            "image": null,
            "group": 3
        }
    ]
}
```
#### Создание публикации
Отправьте POST-запрос на эндпоинт v1/posts/, передав текст поста в поле `text`. При необходимости можно указать id группы в поле `group`.
```
{
    "text": "string",
    "group": 1
} 
```
Пример ответа:
```
{
    "id": 27,
    "author": "newuser",
    "text": "string",
    "pub_date": "2023-02-12 14:15:55",
    "image": null,
    "group": 1
}
```
