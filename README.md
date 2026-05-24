# Яндекс Маршруты — Manual QA

Ручное тестирование веб‑сервиса **Яндекс Маршруты**: тест‑анализ, классы эквивалентности и граничные значения, тест‑кейсы и баг‑репорты.

![Manual QA](https://img.shields.io/badge/Type-Manual%20QA-blue)
![Scope](https://img.shields.io/badge/Scope-Test%20analysis%20%2B%20CE%20%2B%20GZ%20%2B%20TCs-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Focus](https://img.shields.io/badge/Focus-Time%20%26%20Address%20Validation-purple)
![Bugs](https://img.shields.io/badge/Bugs-16_total%20%7C%209_critical-red)

---

## 🧭 Содержание

- [Описание](#описание)
- [Ссылки](#ссылки)
- [Артефакты](#артефакты)
- [Критические дефекты](#критические-дефекты)
- [Итоги тестирования](#итоги-тестирования)
- [Окружение](#окружение)
- [Вывод](#вывод)
- [Автор](#автор)

---

## 📌 Описание

Цель работы — оценить качество реализации:

- **валидации полей времени (часы/минуты)**;
- **валидации адресов (Откуда/Куда)**;
- **расчёта стоимости и времени поездки** на собственном автомобиле.

На основе результатов анализа, КЭ/ГЗ, прогонов тест‑кейсов и баг‑репортов сформированы выводы о готовности продукта к релизу.

---

## 🔗 Ссылки

- **Сервис (тестируемый стенд)**:  
  `https://qa-routes.praktikum-services.ru/`
- **Требования к сервису**:  
  `https://docs.google.com/document/d/1tIs3KqK79vGR60EoGiDKLavvgsj0cjjrdSRK3AFdY6g/edit`

---

## 🧪 Артефакты

| Артефакт                | Формат        | Расположение |
|-------------------------|--------------|--------------|
| ✅ Тест‑анализ          | Markdown      | [`analysis/overview.md`](analysis/overview.md) |
| ✅ Тест‑анализ          | Google Sheets | [«Этап 1. Тест‑анализ»](https://docs.google.com/spreadsheets/d/1ku3De2DZUbj_QlJKdQU7wEh0N3EIILJ8D6_vwkshmQU/edit?gid=1610041137) |
| ✅ КЭ и ГЗ (время)      | Markdown      | [`ce-gz/time-fields.md`](ce-gz/time-fields.md) |
| ✅ КЭ и ГЗ (адреса)     | Markdown      | [`ce-gz/address-fields.md`](ce-gz/address-fields.md) |
| ✅ КЭ и ГЗ (маршруты)   | Markdown      | [`ce-gz/routes-and-time-intervals.md`](ce-gz/routes-and-time-intervals.md) |
| ✅ КЭ и ГЗ              | Google Sheets | [«Этап 2. КЭ и ГЗ»](https://docs.google.com/spreadsheets/d/1ku3De2DZUbj_QlJKdQU7wEh0N3EIILJ8D6_vwkshmQU/edit?gid=1304990855) |
| ✅ Тест‑кейсы           | GitHub        | [`testcases/`](testcases) |
| ✅ Тест‑кейсы           | Google Sheets | [«Этап 3. Тест‑кейсы»](https://docs.google.com/spreadsheets/d/1ku3De2DZUbj_QlJKdQU7wEh0N3EIILJ8D6_vwkshmQU/edit?gid=1524919368) |
| 🐞 Баг‑репорты          | GitHub        | [`bugreports/`](bugreports) |
| 🐞 Баг‑репорты          | Google Sheets | [«Этап 4. Баг‑репорты»](https://docs.google.com/spreadsheets/d/1ku3De2DZUbj_QlJKdQU7wEh0N3EIILJ8D6_vwkshmQU/edit?gid=454479584) |

> Артефакты покрывают весь цикл: от тест‑анализа и проектирования КЭ/ГЗ до тест‑кейсов, прогонов и баг‑репортов с привязкой к требованиям и сценариям.

Примеры групп тест‑кейсов:

- `TC-hours.md` — валидация поля **Часы** (`T1–T24`);
- `TC-minutes.md` — валидация поля **Минуты** (`T25–T48`);
- `TC-from-address.md` — поле **Откуда** (`T49–T53`);
- `TC-to-address.md` — поле **Куда** (`T55–T59`);
- `TC-own-car-cost.md` — расчёт стоимости/времени на своём авто (`T60–T65`).

## 🚨 Критические дефекты

Ключевые критические баги по результатам тестирования:

`BUG2`, `BUG3`, `BUG4`, `BUG6`, `BUG7`, `BUG11`, `BUG14`, `BUG15`, `BUG16`

Подробности по каждому дефекту (окружение, шаги, ER/AR, Severity/Priority, связь с тест‑кейсами) оформлены в отдельных файлах в папке [`bugreports/`](bugreports).

---

## 📊 Итоги тестирования

### Тест‑кейсы

| Метрика           | Значение |
|-------------------|----------|
| Всего тест‑кейсов | **64**   |
| Passed            | **39**   |
| Failed            | **25**   |

### Баги

| Метрика          | Значение |
|------------------|----------|
| Всего багов      | **16**   |
| Критических      | **9**    |
| Желательных      | **7**    |

---

## 💻 Окружение

- **OS**: Windows 11 Pro 21H2  
- **Browser**: Google Chrome 144.0.7559.133

---

## ✅ Вывод

> **Вывод:** из‑за ошибок в валидации полей (Часы/Минуты/Откуда/Куда) и некорректных расчётов стоимости/времени поездки релиз **не рекомендуется** до исправления критических дефектов и повторного регресса.

---

## 👤 Автор

**Anatoly Elnikov (когорта 53)**  
Manual QA Engineer
