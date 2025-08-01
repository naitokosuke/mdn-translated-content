---
title: Expect
slug: Web/HTTP/Reference/Headers/Expect
---

Запрос "HTTP Expect" указывает ожидания, которые должен выполнить сервер, чтобы правильно обработать запрос.

Единственным ожиданием, определённым в спецификации, является "Expect: 100-continue", на который сервер должен ответить:

- {{HTTPStatus("100")}} если информации, содержащейся в заголовке, достаточно, чтобы вызвать немедленный успех,
- {{HTTPStatus("417")}} (Expectation Failed) если он не может удовлетворить ожидания; или любой другой статус 4xx..

Например, сервер может отклонить запрос, если его {{HTTPHeader("Content-Length")}} слишком большой.

Обычные браузеры не отправляют заголовок Expect, но некоторые другие , такие как cURL, делают это по умолчанию.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Header type</th>
      <td>{{Glossary("Request header")}}</td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Forbidden header name")}}</th>
      <td>no</td>
    </tr>
  </tbody>
</table>

## Синтаксис

Никаких других ожиданий, кроме «100-continue», не указано

```
Expect: 100-continue
```

## Директивы

- 100-continue
  - : Сообщает получателям, что клиент собирается отправить (по-видимому большой) тело сообщения в этот запрос и хочет получить промежуточный ответ {{HTTPStatus("100")}} (Continue).

## Примеры

### Большой текст сообщения

Клиент отправляет запрос с заголовком Expect и ожидает ответа сервера перед отправкой тела сообщения.

```
PUT /somewhere/fun HTTP/1.1
Host: origin.example.com
Content-Type: video/h264
Content-Length: 1234567890987
Expect: 100-continue
```

Сервер теперь проверяет запрос и может ответить с ответом {{HTTPStatus("100")}} (Continue), чтобы дать клиенту указание продолжить и отправить тело сообщения, или он отправит {{HTTPStatus("417")}} (Expectation Failed), если какие-либо из ожиданий не могут быть выполнены.

## Характеристики

| Спецификация                       | Название                                                      |
| ---------------------------------- | ------------------------------------------------------------- |
| {{RFC("7231", "Expect", "5.1.1")}} | Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content |

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- {{HTTPStatus("417")}} `Expectation Failed`
- {{HTTPStatus("100")}} `Continue`
