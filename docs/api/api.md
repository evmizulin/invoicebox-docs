---
layout: default
nav_order: 50
title: "Подключение к API"
has_children: true
permalink: /docs/api
---

# Подключение к API

Инвойсбокс API представляет собой набор HTTP ресурсов, к которым можно обращаться следующими HTTP методами: `GET`, `POST`, `PUT`, `DELETE`.

### Базовые URL

Если вы зарегистрировали магазин через приложение Инвойсбокс или по адресу app.invoicebox.ru, то
следует использовать следующие адреса:

- https://api.invoicebox.ru - для продуктового окружения.
- https://api.stage.invbox.ru - для тестового окружения. Используется только в том случае, если для магазина было оформлено отдельное тестовое окружение.

{: .important }
> Если вы зарегистрировали магазин в личном кабинете Инвойсбокс.Бизнес по адресу business.invoicebox.ru, то
следует использовать версию API `/l3/` в запросах. Для остальных случаев - текущая версия `/v3/`.

### Форматы данных

Тело запроса, если оно требуется, должно быть в формате `json`, кодировка `UTF-8`.

{: .important }
> Наименования параметров, заголовков и свойств объектов во всех запросах чувствительны к регистру.

### Заголовки

В запросах необходимо передавать HTTP-заголовки:

| Наименование | Значение                 | Комментарий                                                                                                                                                                                                                                               |
|--------------|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Content-Type | application/json         | Обязательно                                                                                                                                                                                                                                               |
| Accept       | application/json         | Обязательно                                                                                                                                                                                                                                               |
| User-Agent   | идентификатор приложения | Обязательно. Идентификатор приложения формируется в следующем формате: наименование приложения/версия (версия модулия, если применимо) {иные идентификаторы}. Пример заголовка и идентификатора для CMS Битрикс: User-Agent: Bitrix/21.0 (Invoicebox 3.0) |
| X-Signature  | подпись запроса          | Обязательно в случае использование механизма подписи запроса                                                                                                                                                                                              |

### Структура ответа

Все ответы возвращаются в формате `json`. 
В случае положительного ответа, данные приходят в свойстве `data` основного объекта.

Пример запроса получения единичной сущности:
```json
{
  "data": {
    "id": 1,
    "title":
    "New title"
  }
}
```

Пример запроса получения коллекции сущностей:
```json
{
  "data": [
      {
        "id": 1,
        "title": "Apple"
      },
      {
        "id": 2,
        "title":
        "Orange"
      },
      {
        "id": 3,
        "title":
        "Passion fruit"
      }
    ]
}
```

В случае ошибки, код ответа HTTP будет >= 400, а ответ будет содержать свойство `error`:
```json
{
  "error":{
    "message": "Error",
    "code": "unauthorized"
  }
}
```


{: .important }
> Если запрос не соответствует описанному формату данных (контракту) метода - вернётся ошибка.


---

[Читать далее &raquo;](/docs/api/auth){: .btn .btn-primary .mb-4 .mb-md-0 .mr-2 }