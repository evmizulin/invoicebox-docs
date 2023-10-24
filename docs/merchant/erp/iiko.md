---
layout: default
nav_order: 10
title: "iiko"
parent: "Модули для ERP"
grand_parent: "Приём платежей"
---

# Описание модуля iiko

![iiko](/assets/images/erp/iiko.png){: .img-right}

iiko - специализированная система ERP-класса, предназначенная для автоматизации ресторанного бизнеса.
Модуль (плагин) Инвойсбокс для iiko предоставляет простую возможность организации приёма оплаты от организаций и
индивидуальных предпринимателей в залах ресторана.

{: .important }
> В случае, если у вас возникнут сложности при самостоятельной установке модуля и его корректной настройке, пожалуйста,
обратитесь к специалистам [службы поддержки](https://www.invoicebox.ru/ru/contacts/feedback.html).

## Требования

- Минимальная версия `iiko 7.9.7` так как плагин использует `Front API v7`
- Наличие лицензии `api payment (21016318)`
- Запуск iikoFront от имени администратора
- НДС должен быть включен в стоимость блюд

## Установка модуля (плагина)

Распакуйте архив с модулем в папку `C:\Program Files\iiko\iikoRMS\Front.Net\Plugins`

## Настройка модуля (плагина)

Перейдите в папку `C:\Program Files\iiko\iikoRMS\Front.Net\Plugins\BeOpen.Plugins.Invoicebox`
и с помощью блокнота откройте конфигурационный файл `BeOpen.Plugins.Invoicebox.dll.config`.

В конфигурационном файле модуля укажите следующие значения параметров:

- **WS** – адрес вебсокета, к которому требуется подключиться: `ws-gate.invoicebox.ru` (см. [использование веб-сокетов](/docs/api/websockets/))
- **TimeWebSocketSecond** – частота проверки подключения к веб-сокету в секундах: `10`
- **Url** – базовый URL Инвойсбокс API: `https://api.invoicebox.ru` (см. [подключение к API](/docs/api))
- **RoundPolicy** - политика округления, рекомендуется `none`
- **PartnerId** – идентификатор (GUID) Магазина в системе Инвойсбокс. Если ваша организация ещё не зарегистрирована в системе Инвойсбокс, см. ниже функцию регистрации в настройках iikoFront
- **PaymentType** – идентификатор (GUID) типа оплаты. При запуске iikoFront с плагином (модулем), в лог будут выведены все типы оплат, выберите нужный.
Лог плагина находится в папке: `%appdata%\iiko\CashServer\Logs`, название файла: `plugin-BeOpen.Plugins.Invoicebox.log`.

<details>
  <summary>Пример заполненного конфигурационного файла</summary>
<section markdown="1">
``` xml
<BeOpen.Plugins.Invoicebox.Properties.AppSettings>
  <setting name="WS" serializeAs="String">
    <value>ws-gate.invoicebox.ru</value>
  </setting>
  <setting name="TimeWebSocketSecond" serializeAs="String">
    <value>10</value>
  </setting>
  <setting name="Url" serializeAs="String">
    <value>https://api.invoicebox.ru</value>
  </setting>
  <setting name="PartnerId" serializeAs="String">
    <value>ffffffff-ffff-ffff-ffff-ffffffffffff</value>
  </setting>
  <setting name="PaymentType" serializeAs="String">
    <value>27993602-39c4-4d08-8a60-fe8ea63ba181</value>
  </setting>
</BeOpen.Plugins.Invoicebox.Properties.AppSettings>
```
</section>
</details>

## Настройка в iikoOffice / iikoChain

В iikoOffice перейдите в раздел "Розничные продажи" - "Типы оплат" и нажмите "добавить".
Укажите тип оплаты - банковские карты, название выберите по желанию.

{: .warning }
> Чтобы кассиры не могли добавлять тип оплаты вручную без подтверждения оплаты заказа от системы Инвойсбокс,
при настройке типа оплаты для модуля (плагина) установите галку "Запрещать вводить вручную".

![Запрещать вводить вручную](/assets/images/erp/iiko/iiko_office_settings.png)

## Настройка в iikoFront

Перезапустите iikoFront, откройте вкладку дополнений в главном меню.

![Дополнения](/assets/images/erp/iiko/iiko_front_menu.png)

Если ваша организация ещё не зарегистрирована в Инвойсбокс, нажмите "Инвойсбокс: Регистрация в системе" и в открывшемся
окне укажите электронный адрес администратора. Дождитесь получения письма от системы Инвойсбокс.

![Регистрация](/assets/images/erp/iiko/registration.png)

Если ваша организация уже зарегистрирована, нажмите "Инвойсбокс: активация кассы", укажите код активации кассы.

![Активация](/assets/images/erp/iiko/activation.png)
