# Проект «API для Yatube»
### Описание
Yatube - это социальная сеть для публикации своих постов. Пользователи могут просматривать посты, подписываться на авторов и комментировать их записи
через программный интерфейс взаимодействия.
### Технологии
* Python 3.9
* Django 3.2.16
* Django REST Framework
### Установка 
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
### Примеры
