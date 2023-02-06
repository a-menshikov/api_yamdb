# Проект YaMDb

Проект YaMDb собирает отзывы пользователей на произведения. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка». Список категорий может быть расширен. 
Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). 
Добавлять произведения, категории и жанры может только администратор.

## Пользовательские роли и права доступа

- Аноним — может просматривать описания произведений, читать отзывы и комментарии.
- Аутентифицированный пользователь (user) — может читать всё, как и Аноним, может публиковать отзывы и ставить оценки произведениям (фильмам/книгам/песенкам), может комментировать отзывы; может редактировать и удалять свои отзывы и комментарии, редактировать свои оценки произведений. Эта роль присваивается по умолчанию каждому новому пользователю.
- Модератор (moderator) — те же права, что и у Аутентифицированного пользователя, плюс право удалять и редактировать любые отзывы и комментарии.
- Администратор (admin) — полные права на управление всем контентом проекта. Может создавать и удалять произведения, категории и жанры. Может назначать роли пользователям.
- Суперюзер Django должен всегда обладать правами администратора, пользователя с правами admin. Даже если изменить пользовательскую роль суперюзера — это не лишит его прав администратора. Суперюзер — всегда администратор, но администратор — не обязательно суперюзер.

## Технологии

- Python 3.10
- Django 3.2
- Djangorestframework 3.12.4


## Запуск проекта в dev-режиме

1. Клонировать репозиторий и перейти в него в командной строке:

```bash
    git clone <ссылка с git-hub>
```

2. Cоздать виртуальное окружение:

windows
```bash
    python -m venv venv
```

linux
```bash
    python3 -m venv venv
```

3. Активируйте виртуальное окружение

windows
```bash
    source venv/Scripts/activate
```

linux
```bash
    source venv/bin/activate
```

4. Установите зависимости из файла requirements.txt

```bash
    pip install -r requirements.txt
```

5. В папке с файлом manage.py выполните команду:

windows
```bash
    python manage.py runserver
```

linux
```bash
    python3 manage.py runserver
```

## Документация к проекту

Документация для API после установки доступна по адресу
```
    http://127.0.0.1/redoc/
```

## Примеры запросов

- GET-Response: <http://127.0.0.1:8000/api/v1/titles/1/>

Request:

```J-SON
{
    "id": 1,
    "name": "Побег из Шоушенка",
    "year": 1994,
    "description": null,
    "genre": [
        {
            "name": "Драма",
            "slug": "drama"
        }
    ],
    "category": {
        "name": "Фильм",
        "slug": "movie"
    },
    "rating": 10
}
```

- GET-Response: <http://127.0.0.1:8000/api/v1/titles/1/reviews/1/>

Request:

```J-SON
{
    "id": 1,
    "author": "bingobongo",
    "title": 1,
    "text": 
        "Ставлю десять звёзд!\n...Эти голоса были чище и светлее тех,
        о которых мечтали в этом сером, убогом месте. Как будто две птички 
        влетели и своими голосами развеяли стены наших клеток, и на короткий
        миг каждый человек в Шоушенке почувствовал себя свободным.",
    "score": 10,
    "pub_date": "2023-02-05T18:06:02.054698Z"
}
```

## Авторы

Студенты курса "Python-разработчик" от Яндекс-Практикума:

[Артём Меньшиков](https://github.com/a-menshikov)
```
модели, view и эндпойнты для:
произведений,
категорий,
жанров;
импорт данных из csv файлов
```

[Андрей Полушин](https://github.com/pandser)
```
система регистрации и аутентификации,
права доступа,
работа с токеном,
система подтверждения через e-mail
```

[Лазаренков Евгений](https://github.com/lazarenkov-e)
```
модели, view и эндпойнты для:
отзывов,
комментариев,
рейтинга произведений
```
