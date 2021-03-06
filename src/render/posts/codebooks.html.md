---
layout: 'post'
title: 'Проект codebooks.ru'
isPublished: true
date: '02-06-2018'
---

![](/images/codebooks.jpg)

Самыми значимыми в 2017 году моими «проектами» стали обучение на курсе по машинному обучению и [сайт-каталог компьютерных книг](https://codebooks.ru). Про курс я напишу подробней как-нибудь в другой раз, а пока — про сайт.

Почему я решил им заняться? В большей степени это было обусловлено желанием создать относительно большой проект на реакте, с роутером и редаксом, потому что до этого я делал лишь [небольшую форму с индексами](/posts/react-redux.html). Плюс я хотел поднять полноценный бэкенд и получить опыт создания и поддержки rest api с базой данных, потому что до этого я делал лишь [бота для телеграм](/posts/rouble-rate-bot.html) и совсем уж простой бэкенд для [таймера на Elm](/posts/elm-app.html).

Когда я думал о том, какой проект создавать — я не придумал ничего лучше, чем создать очередной сайт-каталог, с книгами про программирование. Да-да, я знаю и пользуюсь [goodreads.com](https://www.goodreads.com/) и мне очень нравятся [автоматические подборки](https://hackernewsbooks.com/).

Оглядываясь назад, думаю, что самыми интересными в итоге оказались вопросы работы именно с бэкендом, потому что именно там был самый большой вызов для меня. При этом я сознательно делал себе некоторые поблажки. Например, выбрал связку Node.js и Mongo, так как имел опыт работы с ними, отказался от своей регистрации, но сделал аутентификацию через GitHub, в процессе не боялся ломать базу, но писал при этом миграции.

В самом начале довольно много времени потратил на продумывание схемы БД и в целом придумал схему, которой придерживался до конца, итоге по ходу написания иногда, конечно, корректировал. Продумывал бэкапы, так как уже терял данные. В итоге, правда, получился всего-навсего простой скрипт, который дампит базу, архивирует и отправляет на другой сервер, но и это неплохо. Продумывал систему деплоя и воспользовался в итоге отличным модулем [pm2](http://pm2.keymetrics.io/).

Был интересный момент с полнотекстовым поиском. Я применил поиск, встроенный в Mongo и, как оказалось, работает он очень плохо — нет возможности настраивать, прикручивать морфологию. В итоге русские тексты он ищет очень плохо, но другой вариант, про который я знал, это эластик возле монги и этот вариант всё-таки оверхед для такого проекта.

Плюс сложной задачей было обработка (создание миниатюр), сохранение и раздача картинок.

Что можно сказать про фронтенд? Я совсем не запаривался над дизайном и у меня сейчас ужасные ссылки из 90-х и вообще минимал, но в целом я старался, чтобы информации была удобочитаемой и доступной. Сумел подружить реакт, редакс и роутер. В редаксе при этом не было очень большой необходимости, я для глобального стейта сохраняю только юзера. Не могу сказать, что я достиг какого-то просветления в реакте, думаю тут отчасти дело в том, что сам проект не подразумевал очень сложных компонентов и их взаимодействия. Но при этом всю мощь реакта и связи модели и DOM я ещё раз оценил, когда делал каталог с пагинацией и фильтрацией. Также на проекте я опробовал связку eslint+prettier и могу сказать, что это хорошо и правильно.

В этом проекте я всё же решил поставить точку и двигаться дальше. Теоретически его можно развивать и с точки зрения продукта (рецензии, оценки, страницы писателей и издательств, несколько изданий у книги и много чего ещё), так и технически (серверный рендеринг, типизация, тесты, деплой в aws и/или использование докера), но при этом я считаю правильным двигаться дальше, раз уж я не планирую заниматься полноценным его развитием. В своё время я получил от этого проекта достаточно интересного челленджа и могу сказать, что довёл его до состояния, когда я сам могу пользоваться им на том уровне, который минимально достаточен (добавление/редактирование книг, поиск, фильтрация, списки читаю/прочёл/хочу прочитать).
