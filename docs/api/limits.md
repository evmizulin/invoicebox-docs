---
layout: default
title: "Ограничения"
nav_order: 100
parent: "Подключение к API"
date: 2023-11-21 00:00:00 +0300
---

# Ограничения

Число и частота запросов к API Инвойсбокс ограничены. Параметры ограничения запросов могут быть изменены для каждой учётной
записи или диапазонов IP индивидуально. Ограничения по умолчанию:
- 100 запросов за 30 секунд для одной учётной записи
- 500 запросов за 30 секунд для одного IP-адреса

Если число запросов превышено, API вернёт ошибку с HTTP-кодом 429 (Too Many Requests).

---
[Читать далее &raquo;](/docs/api/postman){: .btn .btn-primary .mb-4 .mb-md-0 .mr-2 }
