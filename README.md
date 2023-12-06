# Описание
Проект API для YATUBE представляет собой API-сервис социальной сети Yatube. 
По адресу  http://127.0.0.1:8000/redoc/ будет доступна **документация** для API Yatube. В документации описано, как должен работать API. Документация представлена в формате Redoc.

## Как запустить проект:

* Клонировать репозиторий и перейти в него в командной строке:
cd api_final_yatube

* Cоздать и активировать виртуальное окружение:
python3 -m venv env
source env/bin/activate

* Установить зависимости из файла requirements.txt:
python3 -m pip install --upgrade pip
pip install -r requirements.txt

* Выполнить миграции:
python3 manage.py migrate

* Запустить проект:
python3 manage.py runserver

## Стек технологий
Django==3.2.16
Python==3.9
DRF
JWT + Djoser


## Проверка работы
В директории postman_collection сохранена коллекция запросов для отладки и проверки работы текущей версии API Yatube. Для использования коллекции ее необходимо импортировать в Postman.

### Примеры запросов
___
Примеры запросов можно увидеть по адресу  http://127.0.0.1:8000/redoc/ или воспользоваться коллекцией. 
  Для наглядности, вот несколько **примеров**:

* Создание публикации осуществляется по адресу:

POST /api/v1/posts/

Тело запроса:
```json
{
    "text": "string",
    "image": "string",
    "group": 0
}
```

* Запрос на создание подписки:

POST */api/v1/follow/*
```json
{
    "following": "{{adminUsername}}"
}
```

* Запрос к странице подписок(доступна только авторизованным пользователям):

GET */api/v1/follow/*

* Запрос к странице групп:

GET */api/v1/groups/*

### *Так как в проекте подключен Joser, доступ к запросам к API осуществляется по токкену.*
Пользователя можно создать с помощью, например Postman. Для этого передайте в запросе к странице http://127.0.0.1:8000/auth/users/ необходимые данные: username и password.
Затем отправьте POST-запрос на эндпоинт /auth/jwt/create/, передав действующий логин и пароль в полях username и password. Вы получите токкен и далее, при каждом запросе к API нужно в заголовке запроса, в поле Authorization, передавать основной токен доступа, полученный в поле access. Перед самим токеном должно стоять ключевое слово Bearer и пробел: Bearer токен.

Автор [Darya](https://github.com/PopkovaDar):relaxed:
