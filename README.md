### Проект «API для Yatube»

Yatube - социальная сеть для публикации дневников. Позволяет публиковать посты, комментировать посты, осуществлять подписку на авторов.

Для разработки API использован Django REST framework. 
Использованы вьюсеты с ограничением прав доступа пользователей. Реализована аутентификация по JWT-токену.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/yandex-praktikum/api_final_yatube.git
```

```
cd yatube_api
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```
### Примеры.
###### Некоторые примеры запросов к API:

### Публикация и получение постов

Request: ```[GET] http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=1```

Response:

```json
{
    "count": 5,
    "next": "http://127.0.0.1:8000/api/v1/posts/?limit=2&offset=3",
    "previous": "http://127.0.0.1:8000/api/v1/posts/?limit=2",
    "results": [
        {
            "id": 2,
            "author": "string",
            "text": "string",
            "pub_date": "2022-08-06T10:01:17.273956Z",
            "image": "string",
            "group": 0
        },
        {
            "id": 3,
            "author": "string",
            "text": "string",
            "pub_date": "2022-08-06T10:42:39.095878Z",
            "image": "string",
            "group": 0
        }
    ]
}
```

Request: ```[POST] http://127.0.0.1:8000/api/v1/posts/```

Request body:

```json
{
    "text": "string",
    "image": "string",
    "group": 0
}
```

Response:

```json
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2022-08-06T10:59:31.721673Z",
    "image": "string",
    "group": 0
}
```

### Публикация и получение комментариев к постам

Request:```[GET] http://127.0.0.1:8000/api/v1/posts/1/comments/```

Response:

```json
[
    {
        "id": 1,
        "author": "string",
        "post": 1,
        "text": "string",
        "created": "2022-08-06T10:59:31.721673Z"
    }
]
```

Request:```[POST] http://127.0.0.1:8000/api/v1/posts/1/comments/```

Request body:

```json
{
    "text": "1st comment"
}
```

Response:

```json
{
    "id": 1,
    "author": "string",
    "post": 1,
    "text": "string",
    "created": "2022-08-06T10:59:31.721673Z"
}
```

### Подписка на авторов

Request: ```[GET] http://127.0.0.1:8000/api/v1/follow/```

Response:

```json
[
    {
        "user": "string",
        "following": "string"
    }
]
```

Request: ```[POST] http://127.0.0.1:8000/api/v1/follow/```

Request body:

```json
{
    "following": "string"
}
```

Response:

```json
{
    "user": "string",
    "following": "string"
}
```

###Документация к API проекта Yatube (v1):

http://127.0.0.1:8000/redoc/

