---
layout: default
title: ThankeeBook — Политика приватности
---

# Политика приватности ThankeeBook

Действует с 25 сентября 2026 года.
Приложение: ThankeeBook (`com.thankeebook.app`).
Кто отвечает за данные: Даниелов Альберт Варданович, Армения.
Связаться: thankeebook@gmail.com

Этот документ описывает то, что приложение делает на самом деле. Всё,
что здесь написано, можно проверить по коду: он лежит в закрытом
репозитории и по запросу показывается проверяющим магазина.

---

## Коротко

- **Осмотреться можно без входа.** Открыть приложение, полистать,
  понять, нужно ли оно вам, — аккаунт для этого не нужен.
- **Вход нужен, чтобы что-то создавать:** сохранить ссылку, завести
  папку, написать заметку, перенести коллекцию, воспользоваться ИИ.
- **Вход только через Google.** Мы получаем почту, имя и ссылку на фото
  профиля. Пароль мы не видим никогда.
- **Сохранённое хранится и на телефоне, и на нашем сервере.** Иначе оно
  не пережило бы переустановку приложения и не перешло бы на новый
  телефон. Обмен идёт сам, без вашего нажатия.
- **Рекламы нет. Счётчиков посещаемости нет. Данные никому не
  продаются.**

---

## Что уходит на наш сервер

Сохранённое привязано к вашему аккаунту, а не к телефону, и для этого
приложение отправляет его нам. Обмен происходит **сам** — при открытии
приложения и при возвращении в него, — а не по нажатию кнопки.

Отправляется:

| Что | Подробнее |
|---|---|
| Папки | название, заметка к папке, метки, цвет, значок, порядок, вложенность |
| Записи | заголовок, ссылка, ваша заметка, метки, тип, порядок, избранное, «посмотреть позже», архив |
| Ответы ИИ | краткое описание, результат распознавания музыки |
| Текст сохранённых копий статей | сам текст, без картинок |
| Напоминания | дата и время, которые вы поставили |
| Часть настроек | оформление, шрифт, выбранная модель, режимы вида и сортировки, имя и @юзернейм |

**Про закрытые PIN-ом папки скажем прямо.** Их содержимое **тоже
уходит на сервер и лежит там в открытом виде.** PIN закрывает их в
приложении на вашем телефоне; он не шифрует ни файлы, ни серверную
копию. Разработчик технически может прочитать содержимое любой папки,
включая закрытую. Если вы храните что-то, чего не должен видеть никто,
кроме вас, — этому приложению такое доверять не стоит.

**Не уходит никогда:**

- отпечаток PIN-кода и счётчик неудачных попыток;
- история поиска;
- сами картинки: обложки и картинки в копиях статей остаются на
  телефоне;
- содержимое других приложений и телефона.

## Что остаётся только на телефоне

- отпечаток PIN-кода (PBKDF2, 120 000 повторений, случайная соль);
- история поиска;
- обложки и картинки сохранённых статей;
- ежедневные резервные копии — они лежат во внутренней памяти
  приложения, недоступной другим программам, и никуда не отправляются
  сами;
- язык интерфейса и служебные отметки вроде «видел приветствие».

**Про PIN честно.** PIN закрывает папки и записи внутри приложения и
хранится не как есть, а как отпечаток. Но он **не шифрует файлы на
телефоне и не скрывает содержимое от нас**. PIN защищает от чужого
взгляда в ваш телефон, а не от криминалиста и не от разработчика.

## Что уходит поставщикам ИИ

Только когда вы сами нажали ИИ-функцию. Отправляется:

| Функция | Что уходит |
|---|---|
| Краткое описание | ссылка, заголовок, ваша заметка |
| Разбор в рецепт, места, события | ссылка, заголовок, заметка, описание |
| Проверка фактов | ссылка, заголовок, ваша заметка |
| Определение музыки | ссылка на ролик |

Сейчас подключены **Google (модель Gemini, в том числе поиск по
открытым источникам)** и **Mistral AI**. В приложении показывается
выбор из шести моделей, но те, что не подключены, не используются: если
выбранной модели нет, отвечает подключённая. Если позже появятся
остальные — Anthropic, OpenAI, DeepSeek, xAI — или распознавание музыки
через AudD, этот список будет обновлён до того, как они заработают.

К этим компаниям применяются их собственные правила обработки данных.

**Содержимое ваших ИИ-запросов на нашем сервере не сохраняется.** Оно
проходит через него к модели и возвращается ответом. В журналы сервера
пишутся только сообщения об ошибках, без текста запроса.

## Что уходит чужим сайтам

Чтобы показать обложку и название ролика, приложение обращается к
самому сайту, откуда ссылка: **YouTube, TikTok, Vimeo** и другим. Туда
уходит ваша ссылка целиком и ваш адрес в интернете. То же происходит
при проверке, жива ли ссылка, и при сохранении копии статьи — тогда
запрос идёт на сайт статьи.

Эти обращения делаются приложением сами, при открытии, а не по вашему
нажатию. Сайт видит обычный запрос с вашего телефона.

## Что ещё хранится на сервере

По каждому аккаунту:

- почта, имя и ссылка на фото профиля из Google;
- состояние подписки и дата её окончания;
- счётчики обращений к ИИ за минуту, сутки и месяц;
- потраченная на модели сумма за сутки, в центах;
- отметки о нарушениях и блокировках, если они были. Если владелец
  закрыл доступ, почта попадает в отдельный список и остаётся там до
  снятия блокировки.

## Разрешения, которые просит приложение

| Разрешение | Зачем |
|---|---|
| Интернет | обмен с сервером, ИИ-функции, обложки |
| Микрофон | голосовой ввод заметки и голосовой поиск |
| Уведомления | напоминания, которые вы сами поставили |
| Запуск после перезагрузки | чтобы напоминания пережили перезагрузку |

**Про голосовой ввод честно.** Звук мы не получаем и не храним:
приложение отдаёт его системному распознавателю вашего телефона. На
большинстве Android-устройств это служба Google, и она может
обрабатывать запись на своих серверах по своим правилам. К нам приходит
только готовый текст.

Доступа к контактам, местоположению, звонкам, СМС и всей галерее
приложение не просит. Картинку для папки вы выбираете через системное
окно, и приложение видит только выбранный файл.

## Сколько это хранится

- На телефоне — пока вы не удалите запись или приложение.
- На сервере — пока вы не удалите запись или аккаунт.
- Удалённая запись: её содержимое **стирается сразу**, а сама строка
  остаётся пустой отметкой «удалено» — она нужна, чтобы удаление
  доехало до других ваших устройств.
- Счётчики за минуту и сутки — сменяются следующим периодом.
- Месячные счётчики и суммы расхода — до 13 месяцев, для учёта.
- Блокировки — до окончания срока или до снятия.

## Как удалить свои данные

**В приложении:** Профиль → Личные данные → внизу «Удалить аккаунт».
Нужно провести ползунок и вписать фразу — это защита от случайного
нажатия. Удаляется всё: запись на сервере со всеми папками, ссылками и
заметками, и всё сохранённое на этом телефоне.

**Письмом:** напишите на thankeebook@gmail.com с той же почты, которой
входили. Строки удаляются в течение 30 дней.

Две оговорки, чтобы не было неожиданностей:

1. Удаление стирает данные **с сервера и с того телефона, на котором вы
   его нажали**. Если приложение установлено на втором телефоне, там
   останется местная копия, пока вы не удалите приложение или не
   очистите его данные в настройках Android.
2. Если вы входом не пользовались вовсе, записи на сервере у вас нет:
   без входа приложение её не заводит.

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

Effective 25 September 2026.
App: ThankeeBook (`com.thankeebook.app`).
Data controller: Albert Danielov, Armenia.
Contact: thankeebook@gmail.com

This document describes what the app actually does. Everything here can
be verified against the source code, which is kept in a private
repository and shown to store reviewers on request.

---

## In short

- **You can look around without signing in.** Opening the app, browsing
  it and deciding whether you want it needs no account.
- **Signing in is needed to create anything:** saving a link, making a
  folder, writing a note, importing a collection, using the AI.
- **Signing in is through Google only.** We receive your email address,
  your name and a link to your profile picture. We never see your
  password.
- **What you save is kept both on your phone and on our server.**
  Otherwise it would not survive a reinstall and would not follow you to
  a new phone. The exchange happens by itself, without you pressing
  anything.
- **No ads. No analytics. Your data is not sold to anyone.**

---

## What goes to our server

What you save belongs to your account rather than to your phone, and for
that the app sends it to us. The exchange happens **on its own** — when
the app opens and when you return to it — not on a button press.

What is sent:

| What | In detail |
|---|---|
| Folders | name, folder note, tags, colour, icon, order, nesting |
| Entries | title, link, your note, tags, type, order, favourite, watch later, archive |
| AI answers | the short summary, the music recognition result |
| The text of saved article copies | the text itself, without images |
| Reminders | the date and time you set |
| Some settings | theme, font, chosen model, view and sort modes, name and @username |

**About PIN-locked folders, plainly.** Their contents **also go to the
server and are stored there in the clear.** The PIN locks them inside
the app on your phone; it encrypts neither the files nor the server
copy. The developer can technically read the contents of any folder,
locked ones included. If you keep something nobody but you should see,
this app is not the place for it.

**Never sent:**

- the fingerprint of your PIN and the failed-attempt counter;
- your search history;
- the images themselves: thumbnails and pictures inside saved articles
  stay on the phone;
- anything else on your phone.

## What stays on the phone only

- the fingerprint of your PIN (PBKDF2, 120,000 rounds, random salt);
- your search history;
- thumbnails and the pictures of saved articles;
- the daily backups — they live in the app's own private storage, which
  other apps cannot read, and are never sent anywhere by themselves;
- the interface language and housekeeping flags such as "has seen the
  welcome screen".

**An honest note about the PIN.** The PIN locks folders and entries
inside the app and is stored as a fingerprint, not as text. But it
**does not encrypt the files on your phone and does not hide anything
from us**. It protects against someone glancing at your phone, not
against forensics and not against the developer.

## What goes to the AI providers

Only when you press an AI feature yourself:

| Feature | What goes out |
|---|---|
| Short summary | link, title, your note |
| Extract a recipe, places, events | link, title, note, summary |
| Fact check | link, title, your note |
| Identify music | link to the video |

Connected today: **Google (the Gemini model, including search over open
sources)** and **Mistral AI**. The app shows a choice of six models, but
the ones that are not connected are not used: if the chosen model is
absent, a connected one answers instead. Should the others — Anthropic,
OpenAI, DeepSeek, xAI — or music recognition through AudD be switched
on later, this list will be updated before they start working.

Those companies' own data practices apply to what they receive.

**The contents of your AI requests are not stored on our server.** They
pass through it to the model and come back as an answer. Server logs
contain error messages only, never the text of a request.

## What goes to other people's sites

To show a thumbnail and the title of a video, the app asks the site the
link came from: **YouTube, TikTok, Vimeo** and others. Your full link
and your internet address go there. The same happens when the app checks
whether a link is still alive, and when it saves a copy of an article —
then the request goes to the article's own site.

These requests are made by the app itself, on opening, not on your
button press. The site sees an ordinary request from your phone.

## What else the server holds

Per account:

- your email address, name and profile picture link from Google;
- subscription status and expiry date;
- counters of AI requests per minute, day and month;
- the amount spent on models today, in cents;
- abuse strikes and blocks, if any occurred. If the owner closes your
  access, your email goes on a separate list and stays there until the
  block is lifted.

## Permissions the app asks for

| Permission | Why |
|---|---|
| Internet | syncing with the server, AI features, thumbnails |
| Microphone | dictating a note and voice search |
| Notifications | reminders you set yourself |
| Start after reboot | so reminders survive a phone restart |

**An honest note about voice input.** We never receive or store the
audio: the app hands it to your phone's own speech recogniser. On most
Android devices that is a Google service, and it may process the
recording on Google's servers under Google's own terms. Only the
finished text reaches us.

The app does not ask for contacts, location, calls, SMS, or your whole
photo library. You pick a folder picture through the system picker, and
the app only ever sees the file you chose.

## How long this is kept

- On the phone: until you delete the entry or the app.
- On the server: until you delete the entry or your account.
- A deleted entry: its contents are **erased at once**, and the row
  stays behind as an empty "deleted" marker — needed so the deletion
  reaches your other devices.
- Minute and day counters: replaced by the next period.
- Monthly counters and spend totals: up to 13 months, for accounting.
- Blocks: until they expire or are lifted.

## How to delete your data

**In the app:** Profile → Personal details → "Delete account" at the
bottom. You have to drag a slider and type a phrase — that is the guard
against pressing it by accident. Everything goes: the server record with
all folders, links and notes, and everything saved on that phone.

**By email:** write to thankeebook@gmail.com from the same address you
signed in with. Rows are deleted within 30 days.

Two caveats so nothing comes as a surprise:

1. Deleting erases your data **from the server and from the phone you
   pressed it on**. If the app is installed on a second phone, a local
   copy remains there until you uninstall it or clear its data in
   Android settings.
2. If you never signed in, there is no record of you on the server at
   all: the app does not create one without a sign-in.

## Children

The app is not intended for children under 13 and does not knowingly
collect their data. If you believe a child's data reached the server,
write to us and we will delete it.

## Changes

If this policy changes, a new date appears at the top of this document,
and material changes are shown in the app on update.

## Questions

thankeebook@gmail.com
