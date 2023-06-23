---
layout: default
nav_order: 10
title: "Подтверждение оплаты счёта"
parent: "Инвойсбокс.Бизнес"
---

# Подтверждение оплаты заказа

Для подтверждения оплаты счёта с использованием гарантийного фонда, необходимо вызвать следующий метод API:

- метод: `POST`
- ресурс: `/v3/business/api/invoice/{invoiceId}/confirm`
- тело запроса - объект [CreateInvoicePaymentRequest](#createinvoicepaymentrequest)
- тело ответа - объект [InvoicePaymentResponse](#invoicepaymentresponse)
- Возможные [ошибки](/docs/dictionary/error/)

<details>
  <summary>Пример запроса</summary>
<section markdown="1">
``` json
POST /v3/business/api/invoice/{invoiceId}/confirm
Authorization: Bearer b37c4c689295904ed21eee5d9a48d42e
Content-Type: application/json
Accept: application/json
{
}
```
</section>
</details>

## Параметры запроса

| Свойство        | Обязательное | Тип        | Описание       | Пример значения                        |
|-----------------|--------------|------------|----------------|----------------------------------------|
| invoiceId       | да           | string(36) | Id счёта       | `01771534-1a57-f184-dee3-ebeb91dded75` |

## CreateInvoicePaymentRequest

Нет

## InvoicePaymentResponse

Повторяет свойства объекта [CreateInvoicePaymentRequest](#createinvoicepaymentrequest) с дополнительными свойствами:

| Свойство   | Обязательное | Тип        | Описание                                      | Пример значения                         |
|------------|--------------|------------|-----------------------------------------------|-----------------------------------------|
| id         | да           | string(36) | Идентификатор транзакции в системе Инвойсбокс | `8c0e116d-31a5-4210-b62e-6b6917851f69`  |


---
[Читать далее &raquo;](/business/schema/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .fs-6 .fw-300 }