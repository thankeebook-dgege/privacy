---
layout: default
title: ThankeeBook — Политика приватности
---

# Политика приватности ThankeeBook

Действует с 24 сентября 2026 года.
Приложение: ThankeeBook (`com.thankeebook.app`).
Кто отвечает за данные: [ФИО или наименование ИП], Армения.
Связаться: thankeebook@gmail.com

Этот документ описывает то, что приложение делает на самом деле. Всё,
что здесь написано, можно проверить по коду: он лежит в закрытом
репозитории и по запросу показывается проверяющим магазина.

---

## Коротко

- Всё сохранённое лежит **на вашем телефоне**. Ссылки, заметки, папки,
  сохранённые копии статей, обложки — ничего из этого не уходит на
  сервер само по себе.
- На сервер что-то отправляется **только когда вы сами нажали
  ИИ-функцию**, и только то, что нужно для ответа.
- **Вход нужен только для ИИ.** Всё остальное работает без него:
  сохранения, папки, поиск, напоминания, копии статей.
- **Вход только через Google.** Мы получаем почту, имя и ссылку на
  фото профиля. Больше ничего, и пароль мы не видим никогда.
- **Безличных записей у нас нет.** Раньше приложение входило анонимно,
  и подписка оказывалась привязана к телефону: переустановил — потерял
  оплаченное. Теперь она привязана к вашему Google-аккаунту и
  переживает и переустановку, и смену телефона.
- **Рекламы нет. Счётчиков посещаемости нет. Данные никому не
  продаются.**

---

## Что остаётся только на телефоне

Приложение хранит в своей внутренней памяти:

- сохранённые ссылки, видео, музыку, статьи и заметки;
- папки, метки, избранное, «посмотреть позже», архив;
- сохранённые копии страниц и обложки;
- напоминания;
- настройки: язык, оформление, шрифт, выбранная модель;
- отпечаток PIN-кода, если вы его поставили.

Эти данные не копируются на сервер и недоступны разработчику. Они
исчезают, когда вы удаляете приложение или очищаете его данные.

**Про PIN честно.** PIN закрывает папки и записи внутри приложения и
хранится не как есть, а как отпечаток (PBKDF2, 120 000 повторений,
со случайной солью). Но он **не шифрует файлы на телефоне**. Человек с
разблокированным телефоном и техническими навыками до файлов
доберётся. PIN защищает от чужого взгляда, а не от криминалиста.

## Что отправляется на сервер и когда

Только по вашему нажатию на одну из ИИ-функций. Отправляется:

| Функция | Что уходит |
|---|---|
| Краткое описание | ссылка, заголовок, ваша заметка |
| Разбор в рецепт, места, события | ссылка, заголовок, заметка, описание |
| Проверка фактов | ссылка, заголовок, ваша заметка |
| Определение музыки | ссылка на ролик |

Вместе с этим уходят: номер вашей записи на сервере, название
выбранной модели и язык приложения.

Не уходит никогда: содержимое других записей, список папок, сохранённые
копии страниц, напоминания, PIN, содержимое телефона.

## Что хранится на сервере

Сервер (Supabase) хранит по каждому номеру:

- состояние подписки и дату её окончания;
- счётчики обращений за минуту, сутки и месяц;
- потраченную сумму за сутки, в центах;
- отметки о нарушениях и блокировках, если они были.

Если вы вошли через Google, к этому добавляется то, что Google
сообщает о вашем аккаунте: **почта, имя и ссылка на фото профиля**.
Пароль мы не видим никогда: вход происходит на стороне Google, а к нам
приходит только подтверждение, что это вы.

Один и тот же Google-аккаунт всегда даёт одну и ту же запись, в том
числе на новом телефоне. Поэтому подписка не теряется ни при
переустановке, ни при смене устройства.

**Содержимое ваших запросов на сервере не сохраняется.** Оно проходит
через него к модели и возвращается вам ответом. В журналы сервера
пишутся только сообщения об ошибках, без текста запроса.

## Кому данные передаются дальше

Чтобы ИИ-функции работали, текст запроса уходит поставщику модели.
Сейчас это:

- **Google** (модель Gemini, в том числе поиск по открытым источникам
  для проверки фактов);
- **Mistral AI**.

Если позже появится определение музыки, ссылка на ролик будет уходить
в **AudD**.

К этим компаниям применяются их собственные правила обработки данных.
Мы передаём им только то, что перечислено в таблице выше.

Сервер и база данных размещены в **Supabase**.

Никому другому данные не передаются. Не продаются, не обмениваются, не
используются для рекламы.

## Разрешения, которые просит приложение

| Разрешение | Зачем |
|---|---|
| Интернет | ИИ-функции и загрузка обложек |
| Микрофон | голосовой ввод заметки и голосовой поиск |
| Уведомления | напоминания, которые вы сами поставили |
| Запуск после перезагрузки | чтобы поставленные напоминания пережили перезагрузку телефона |

**Про голосовой ввод честно.** Звук мы не получаем и не храним: приложение
отдаёт его системному распознавателю вашего телефона. На большинстве
Android-устройств это служба Google, и она может обрабатывать запись на
своих серверах по своим правилам. К нам приходит только готовый текст, и
только в то поле, куда вы диктовали.

Доступа к контактам, местоположению, звонкам, СМС и всей галерее
приложение не просит. Картинку для папки вы выбираете через системное
окно выбора, и приложение видит только выбранный файл.

## Сколько это хранится

- На телефоне — пока вы не удалите запись или приложение.
- Счётчики за минуту и сутки — сменяются следующим периодом.
- Месячные счётчики и суммы расхода — до 13 месяцев, для учёта.
- Блокировки — до окончания срока, после чего снимаются сами.

## Как удалить свои данные

- **На телефоне:** удалить приложение или очистить его данные в
  настройках Android. Этого достаточно, чтобы не осталось ничего.
- **На сервере:** напишите на thankeebook@gmail.com с той же почты,
  которой входили. Этого достаточно, чтобы вас опознать. Если вы ИИ не
  пользовались, то и записи на сервере у вас нет: заводить её без
  входа приложение не умеет.

Строки удаляются в течение 30 дней. Номер вашей записи всегда можно
посмотреть в приложении, в разделе «О приложении».

## Дети

Приложение не предназначено для детей младше 13 лет и не собирает их
данные намеренно. Если выяснится, что данные ребёнка попали на сервер,
напишите нам, и мы их удалим.

## Изменения

Если политика поменяется, новая дата появится вверху этого документа, а
существенные изменения будут показаны в приложении при обновлении.

## Вопросы

thankeebook@gmail.com

---
---

# ThankeeBook Privacy Policy

Effective 24 September 2026.
App: ThankeeBook (`com.thankeebook.app`).
Data controller: [full legal name], Armenia.
Contact: thankeebook@gmail.com

This document describes what the app actually does. Everything here can
be verified against the source code, which is kept in a private
repository and shown to store reviewers on request.

---

## In short

- Everything you save stays **on your phone**. Links, notes, folders,
  saved copies of articles, thumbnails — none of it leaves the device by
  itself.
- Something is sent to the server **only when you press an AI feature**,
  and only what is needed to answer.
- **Signing in is only needed for the AI features.** Everything else
  works without it: saving, folders, search, reminders, page copies.
- **Signing in is through Google only.** We receive your email address,
  your name and a link to your profile picture. Nothing else, and we
  never see your password.
- **We keep no anonymous records.** The app used to sign in
  anonymously, which tied the subscription to the phone: reinstall and
  you lost what you paid for. It is now tied to your Google account and
  survives both a reinstall and a new phone.
- **No ads. No analytics. Your data is not sold to anyone.**

---

## What stays on the phone only

The app keeps in its own private storage:

- saved links, videos, music, articles and notes;
- folders, tags, favourites, watch later, archive;
- saved page copies and thumbnails;
- reminders;
- settings: language, theme, font, chosen model;
- the fingerprint of your PIN, if you set one.

None of this is copied to the server, and the developer cannot see it.
It disappears when you uninstall the app or clear its data.

**An honest note about the PIN.** The PIN locks folders and entries
inside the app and is stored as a fingerprint, not as text (PBKDF2,
120,000 rounds, random salt). But it **does not encrypt the files on
your phone**. Someone holding an unlocked phone with the right technical
skills can reach them. The PIN protects against a passing glance, not
against forensics.

## What is sent to the server, and when

Only when you press one of the AI features. What is sent:

| Feature | What goes out |
|---|---|
| Short summary | link, title, your note |
| Extract a recipe, places, events | link, title, note, summary |
| Fact check | link, title, your note |
| Identify music | link to the video |

Along with it: the number of your record on the server, the name of the
chosen model and the app language.

Never sent: the contents of your other entries, your folder list, saved
page copies, reminders, your PIN, or anything else on the phone.

## What the server stores

The server (Supabase) stores, per number:

- subscription status and expiry date;
- request counters per minute, day and month;
- the amount spent today, in cents;
- abuse strikes and blocks, if any occurred.

If you signed in with Google, this also holds what Google tells us
about your account: **your email address, your name and a link to your
profile picture**. We never see your password: the sign-in happens on
Google's side, and only a confirmation that it is you reaches us.

The same Google account always gives the same record, including on a
new phone. That is why the subscription is not lost on a reinstall or
when you change devices.

**The contents of your requests are not stored on the server.** They
pass through it to the model and come back as an answer. Server logs
contain error messages only, never the text of a request.

## Who else receives data

For the AI features to work, the text of a request goes to the model
provider. Currently:

- **Google** (the Gemini model, including search over open sources for
  fact checking);
- **Mistral AI**.

If music identification ships later, the video link will go to **AudD**.

Those companies' own data practices apply to what they receive. We send
them only what is listed in the table above.

The server and database are hosted by **Supabase**.

No one else receives your data. It is not sold, traded, or used for
advertising.

## Permissions the app asks for

| Permission | Why |
|---|---|
| Internet | AI features and loading thumbnails |
| Microphone | dictating a note and voice search |
| Notifications | reminders you set yourself |
| Start after reboot | so reminders survive a phone restart |

**An honest note about voice input.** We never receive or store the audio:
the app hands it to your phone's own speech recogniser. On most Android
devices that is a Google service, and it may process the recording on
Google's servers under Google's own terms. Only the finished text reaches
us, and only in the field you dictated into.

The app does not ask for contacts, location, calls, SMS, or your whole
photo library. You pick a folder picture through the system picker, and
the app only ever sees the file you chose.

## How long this is kept

- On the phone: until you delete the entry or the app.
- Minute and day counters: replaced by the next period.
- Monthly counters and spend totals: up to 13 months, for accounting.
- Blocks: until they expire, after which they lift themselves.

## How to delete your data

- **On the phone:** uninstall the app, or clear its data in Android
  settings. That is enough to leave nothing behind.
- **On the server:** write to thankeebook@gmail.com from the same
  address you signed in with. That is enough to identify you. If you
  never used the AI features, there is no record of you on the server
  at all: the app cannot create one without a sign-in.

Rows are deleted within 30 days. The number of your record is always
visible in the app under "About".

## Children

The app is not intended for children under 13 and does not knowingly
collect their data. If you believe a child's data reached the server,
write to us and we will delete it.

## Changes

If this policy changes, a new date appears at the top of this document,
and material changes are shown in the app on update.

## Questions

thankeebook@gmail.com
