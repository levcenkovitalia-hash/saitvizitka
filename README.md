# Сайт-портфолио — Виталия Юрченко

Статический one-page сайт (HTML/CSS/vanilla JS), готов к публикации на GitHub Pages.

## Структура

```
site/
├── index.html
├── css/style.css
├── js/main.js
├── images/
│   ├── portrait.jpg
│   ├── gallery/          # слайды по 4 кейсам (по 3 шт.)
│   └── reviews/          # 3 скриншота отзывов
└── README.md
```

## Перед публикацией: настройка формы заявки

Форма отправляет заявку в email (через Web3Forms) и в Telegram. Пока не настроены ключи — форма покажет пользователю сообщение об ошибке настройки.

Откройте [js/main.js](js/main.js) и заполните три константы в начале блока `Lead form`:

```js
const WEB3FORMS_ACCESS_KEY = 'YOUR_WEB3FORMS_ACCESS_KEY';
const TELEGRAM_BOT_TOKEN = 'YOUR_TELEGRAM_BOT_TOKEN';
const TELEGRAM_CHAT_ID = 'YOUR_TELEGRAM_CHAT_ID';
```

### 1. Email — Web3Forms (бесплатно, без регистрации с паролем)

1. Зайдите на [web3forms.com](https://web3forms.com).
2. Введите email `Vita_Levchenko@mail.ru` — на него придёт Access Key.
3. Вставьте полученный ключ в `WEB3FORMS_ACCESS_KEY`.

Заявки с сайта будут приходить на `Vita_Levchenko@mail.ru`.

### 2. Telegram — уведомления о заявках

1. В Telegram напишите [@BotFather](https://t.me/BotFather), создайте бота командой `/newbot`, получите **токен**.
2. Напишите новому боту любое сообщение (например «привет»).
3. Откройте в браузере:
   `https://api.telegram.org/bot<ВАШ_ТОКЕН>/getUpdates`
   и найдите в ответе `"chat":{"id": ... }` — это ваш **chat_id**.
4. Вставьте токен и chat_id в `TELEGRAM_BOT_TOKEN` и `TELEGRAM_CHAT_ID`.

⚠️ **Важно:** токен бота будет виден в открытом исходном коде страницы (сайт статический, без сервера). Для формы заявок это не критично — максимум, что может случиться, это спам в чат бота. Если хотите избежать этого риска, используйте вместо прямого вызова Telegram API встроенную интеграцию с Telegram в самом сервисе форм (например, в Getform или в платных тарифах Web3Forms) — тогда токен не нужно хранить на фронтенде.

## Публикация на GitHub Pages

1. Создайте репозиторий на GitHub (например `vitalia-portfolio`).
2. Содержимое папки `site/` должно оказаться в корне репозитория (или в ветке `gh-pages` / папке `/docs` — на ваш выбор в настройках Pages).
3. Настройки репозитория → **Pages** → Source → выберите ветку и папку.
4. Сайт будет доступен по адресу `https://<username>.github.io/<repo>/`.

Пример через терминал (если репозиторий уже создан на GitHub):

```bash
cd site
git init
git remote add origin https://github.com/<username>/<repo>.git
git add .
git commit -m "Первая публикация сайта"
git branch -M main
git push -u origin main
```

Затем в настройках репозитория включите GitHub Pages для ветки `main` (папка `/root`).

### Свой домен (опционально)

Добавьте файл `CNAME` в корень `site/` с содержимым вашего домена (например `vitaliayurchenko.ru`) и настройте DNS-записи домена согласно [документации GitHub Pages](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Локальный просмотр перед публикацией

```bash
cd site
python3 -m http.server 8765
```

Открыть [http://localhost:8765](http://localhost:8765).
