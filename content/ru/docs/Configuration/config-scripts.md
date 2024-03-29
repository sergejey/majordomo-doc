---
title: Сценарии
weight: 40
---

Расположение раздела: **Панель управления &rarr; Объекты &rarr; Сценарии**

Сценарий -- это программа, которая исполняет заданную последовательность действий. В разделе **Сценарии** можно
создать любое количество подобных программ и, для удобства организации, привязать их к определённым *категориям*.

Обязательными свойствами любого сценария являются **Название** и **Код**. 

**Описание** не является обязательным,
но его можно использовать, чтобы в нескольких предложения описать суть сценария.

![](../config-scripts-edit.png)

## Варианты программирования сценария

Для программирования сценариев существует несколько способов, которые устанавливаются путём выбора опции "Использовать для программирования".
Обратите внимание, что описанные ниже варианты программирования, могут применяться не только в сценариях, но и в других
частях системы, позволяющих задавать код (например, методы объектов).

### Код

"Классический" способ программирования -- написание программы с использованием языка программирования. Основным языком
программирования, используемом в проекте, является язык **[PHP](https://www.php.net/manual/ru/intro-whatis.php)** (на нём же написана большая часть кода проекта).
Т.е. можно использовать встроенный редактор кода для написания полноценной программы, задействовав все имеющиеся в PHP
функции и операторы, а так же используя дополнительный набор функций, который предоставляется проектом MajorDoMo (см. раздел
[Встроенные PHP функции]({{<ref "/docs/Integration/integration-functions">}})).

Пример PHP-кода сценария:
```php
$weather = "Сегодня ожидается ".str_replace('&deg;',' ',getGlobal('weatherToday'));
$weather .= ". Завтра ".str_replace('&deg;',' ',getGlobal('weatherTomorrow'));
$weather .= ". Сейчас на улице ".getGlobal('TempOutside').'.';
$weather = str_replace('&deg;','',$weather);
say($weather,2);
```

Кроме языка программирования PHP, код также может быть написан с использованием языка программирования **Python**,
поддержка которого также реализована в системе (см. раздел [Поддержка Python]({{<ref "/docs/Integration/integration-python">}}))

### Blockly

При выборе опции **Blockly** появляется доступ к визуальной среде программирования, где программа создаётся путём
перетаскивания блоков, как в детском конструкторе Лего. В левой части интерфейса находятся категории, нажав на которую
появляется список блоков, любой из которых можно добавить в программу, перетащив в основную рабочую область.

Пример программы на Blockly:
![](../config-scripts-blockly.png)

Важно отметить, что программа на Blockly в итоге представляет собой всё тот же PHP-код и переключение в опцию программирования *Код*
сохранит программу на Blockly, но покажет её именно в виде кода.

Пример представление программы выше в виде кода:
```php
function length($value) {
  if (is_string($value)) {
    return strlen($value);
  } else {
    return count($value);
  }
}

if (length('123') > 2) {
  say('Привет', 2);
  callMethod("Dimmer11.turnOn");
}
```

### Устройства

Не очень гибкий, но самый простой вариант задать последовательность действий над Простыми устройствами в ходе
выполнения сценария -- есть возможность только добавить устройство и указать какое действие должно быть с ним
произведено.

Пример:
![](../config-scripts-devices.png)

## Способы вызова сценария

Сценарии пишутся для того, чтобы исполнять заданную в них программу автоматически, а для этого необходимо, чтобы
сценарий был вызван. Существует несколько способа вызова сценария, которые приведены ниже (представим, что наш
сценарий называется *MyScript*).

### Запуск кодом

Сценарий может быть вызван через специальную функцию *runScript* как часть другого сценария. При этом имеется
возможность не просто вызвать сценарий, но и передать какие-то параметры для его исполнения.

```php
runScript('MyScript'); // простой запуск
runScript('MyScript',array('param1'=>123, 'param2'=>'Test')); // запуск с передачей параметров
```
Переданные параметры доступны внутри кода MyScript как массив $params, т.е. их можно использовать в таком виде:
```php
if ($params['param1']===123) { // проверка условия 
 say("Значение параметра ".$params['param2']); // часть кода
}
```

### Запуск по времени

Ещё один способ -- установить расписание запуска в настройках самого сценария. В таком случае, сценарий будет запущен
сам по себе согласно расписанию.

Пример расписания:

![](../config-scripts-timer.png)

### Запуск при изменении свойства

Сценарий может быть запущен автоматически при изменении связанного с ним свойства. Если исходный код сценария начинается
с проверки определённого свойства, то система предлагает автоматически связать сценарий с этим свойством.

В данном примере сценарий начинается с проверки текущего времени:

![](../config-scripts-autolink1.png)

Система автоматически связала сценарий со свойством ClockChime.time и, в случае если выбран автоматически запуск,
сценарий будет исполнен каждый раз, когда изменяется указанное свойство:

![](../config-scripts-autolink2.png)

### Запуск как "метода"

Во многих раздела системы существует возможность "привязать" определённое событие к сценарию или методу объекта.
В тех случаях, где есть привязка только к методу объекта, можно использовать "виртуальный" объект AllScripts, у которого
в качестве методов имеются все созданные сценарии.

### Запуск по ссылке

Любой сценарий можно так же исполнить прямым открытием ссылки вида:
```
http://IP_адрес_сервера/objects/?script=devicesTest
```
Также имеется возможность передавать параметры аналогично параметрам через вызов кода:
```
http://IP_адрес_сервера/objects/?script=devicesTest&param1=123&param2=Test
```
Данный способ может использоваться для инициирования определённых действий открытием ссылки с другого устройства.