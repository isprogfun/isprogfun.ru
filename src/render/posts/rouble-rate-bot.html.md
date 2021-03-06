---
layout: 'post'
title: 'Разработка бота с курсом рубля для телеграма'
isPublished: true
date: '02-26-2016'
keywords: 'telegram, телеграм, бот, бот для телеграм, курс рубля, бот на node.js, node.js, mongo, mongodb'
---

После появления ботов в мессенджере [телеграм](https://telegram.org/) у меня появилось желание написать своего бота. Хотелось выбрать в качестве пробного сервиса что-то простое, чтобы по большей части ознакомиться именно с платформой, а не закапываться в какую-то задачу.

Так возникла идея сделать бота, который будет по запросу отправлять информацию о текущем курсе рубля к доллару и евро. Соответственно сам бот должен постоянно получать эти данные, используя открытый api. Сначала я использовал данные с yahoo, но в какой-то момент они стали довольно часто отваливаться да и данные разнились с курсом в России, и я переключился на [апи московской биржы](http://moex.com/iss/reference/). Там данные приходят с задержкой в минут 10 и непонятно, как часто можно опрашивать (я поставил обновление раз в пять минут), но работает всё очень стабильно.

Интересный момент — из двух вариантов получения апдейтов и я решил использовать вебхуки и на тот момент нельзя было использовать самоподписанный сертификат ssl, а сервер должен был быть доступен только по https. Поэтому пришлось вникнуть, купить сертификат и настроить https для сайта. Что было в любом случае интересно и полезно.

Также в какой-то момент я решил добавить боту возможность самостоятельных оповещений пользователя по резкому колебанию курса и сделал настройку, где можно отключить/включить оповещения, а также настроить разницу курса, при которой эти оповещения надо отправлять.

Под капотом как и раньше использовал nodejs+mongo, результат можно посмотреть на [гитхабе](https://github.com/isprogfun/RoubleRateBot).

[Ссылка на бота](https://storebot.me/bot/roubleratebot) в Telegram Bot Store.
