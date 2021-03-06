---
layout: 'post'
title: 'Тестирование геймпада Logitech F710 на OS X 10.9'
isPublished: true
date: '12-12-2013'
---

Вкратце — геймпад подключается, но игры с ним отказываются нормально работать, да и сам геймпад будет похуже, чем его конкурент с Xbox 360. Хотя я помню, что Bioshoсk проходился вполне нормально. Но на маке всё посложней. И игр толком нет, хотя я проверял в основном платформеры, которые как раз должны были замечательно работать с геймпадом.

## Установка геймпада
Для начала пробуем просто подключить геймпад по ~~[инструкции](http://www.macgamepads.com/gamepads/f710/index.html)~~.
Также возможно понадобиться установка драйвера с сайта [tattiebogle.net](http://tattiebogle.net/index.php/ProjectRoot/Xbox360Controller/OsxDriver).
По окончании установки в настройках системы появится новый пункт меню с драйверами, которые как бы от Xbox 360.

## Удаление геймпада из системы
[Инструкция](http://forums.macrumors.com/showthread.php?t=447793)

Ищем в консоли установленный пакет по имени:
```bash
pkgutil --pkgs | grep 360
```

Допустим нужный нам пакет называется `com.mice.pkg.Xbox360controller`. Набираем в консоли:
```bash
pkgutil --files com.mice.pkg.Xbox360controller
```
Внимательно просматриваем вывод и удаляем нужные папки и файлы. Затем просим систему 'забыть' пакет:
```bash
pkgutil --forget com.mice.pkg.Xbox360controller
```
## Игры
### Rochard
Клавиши в меню и игре работают, на клавиатуре играть значительно проще. Направление удержания предметов надо фиксировать, при этом необходимо было нажать замедление времени, прыжок и движение в сторону. Пальцы запутались. Сел за клавиатуру — всё сделал в две секунды.

### Shank 2, Bastion, Mark of the Ninja
Неправильно работают клавиши даже в меню.

### Trine
Клавиши не работают в принципе, хотя геймпад можно выбрать в меню.

### Trine 2
Геймпад не обнаружился даже в меню
