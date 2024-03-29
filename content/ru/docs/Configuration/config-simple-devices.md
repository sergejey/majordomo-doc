---
title: Простые устройства (ПУ)
weight: 20
---

## О концепции

Концепция "Простые устройства" (**ПУ**) возникла в процессе работы над упрощением настройки системы для конечного пользователя. Помимо этого, [Объектная модель]({{<ref "/docs/Configuration/config-objects">}}),
хоть и является максимально гибкой в настройке, не включает в себя единый стандарт для настройки типового оборудования Умного Дома,
что, в свою очередь, необходимо для дальнейшей интеграции устройств со сторонними интерфейсами взаимодействия, например такими
как ассистент Алиса от Яндекса или Siri от Apple.

Таким образом, можно представить назначение модуля Простые устройства следующим списком:

- Упрощённый механизм добавление в систему типового оборудования
- Настройка основных параметров типового оборудования
- Установка связей между различным оборудованием через правила взаимодействия
- Интерфейс пользователя для управления оборудованием
- Интеграция добавленных устройств в сторонние сервисы управления (голосовые помощники)

С технической стороны, **Простые устройства** во многих аспектах являются лишь надстройкой **Объектной модели** -- за каждым
типом устройств стоит *класс объектов*, а за каждым устройством -- экземпляр класса (*объект*).

## Поддерживаемые типы устройств

{{% alert%}}
Представленный ниже список поддерживаемых устройств включает те устройства, которые включены в базовое "ядро"
платформы, однако набор устройств может быть расширен за счёт установки дополнительных модулей из [Маркета дополнений]({{<ref "/docs/Integration/integration-market">}}).
{{% /alert %}}

| Тип устройств |
| --- |
| Реле / управляемый выключатель |
| Робот-пылесос |
| Медиа-проигрыватель |
| Телевизор |
| Термостат |
| Кондиционер |
| Диммер (источник света с регулируемой яркостью) |
| RGB (источник света с регулируемым цветом) |
| IP-камера |
| Датчик движения |
| Датчик открытия |
| Датчик протечки |
| Датчик дыма |
| "Открываемое" (привод ворот/окон/дверей) |
| Счётчик (воды, электричества и т.п.) |
| Клавиша (активатор) |
| Общий сенсор |
| Сенсор температуры воздуха |
| Сенсор влажности воздуха |
| Сенсор влажности почвы |
| Сенсор уровня CO2 |
| Сенсор уровня радиации |
| Общий сенсор процентного состояния |
| Сенсор давления |
| Сенсор уровня мощности |
| Сенсор напряжения |
| Сенсор уровня тока |
| Сенсор уровня освещённости |

## Связи между устройствами

| Тип связи | Источник | Возможности |
| --- | --- | --- |
| Действие по событию: переключение | Датчик движения, Кнопка, Датчик открытия, IP-камера | Включение/выключение связанного устройства по событию |
| Действие по событию: включить на время | Датчик движения, Кнопка, Датчик открытия, IP-камера | Включение связанного устройства на заданное время по событию |
| Действие по событию: установить цвет | Датчик движения, Кнопка, Датчик открытия, IP-камера | Установка цвета связанного устройства по событию |
| Управление по термостату | Термостат | Включение/выключение связанного устройства в зависимости от состояния термостата |
| Действие по значению сенсора | Различные сенсоры | Включение/выключение связанного устройства в зависимости от значения сенсора (выше/ниже порога значений) |
| Передача данных сенсора | Различные сенсоры | Установка значения температуры связанного устройства (термостат/кондиционер) по внешнему сенсору |

## Пример настройки

### Список устройств

![](../config-devices-list.png)

### Общая информация

![](../config-devices-general-info.png)

### Настройки устройства

![](../config-devices-settings.png)

### Связанные устройства

Добавление связи:

![](../config-devices-linked.png)

Детали связи:

![](../config-devices-linked-details.png)

### Расписание

![](../config-devices-schedule.png)

### Действия

![](../config-devices-action.png)

### Интерфейс

![](../config-devices-ui.png)

Предустановленный интерфейс управления устройствами доступен по адресу:
```
http://IP_адрес_сервера/apps/devices.html
```

![](../config-devices-ui-page.png)

Вариант размещения устройств на [сцене]({{<ref "/docs/Configuration/UI/config-scenes">}}):

![](../config-devices-ui-scene.png)