# Mono — сайт-визитка

Одна страница, один файл: `index.html` с inline CSS и JS. Без фреймворков,
сборки и npm. Единственная внешняя зависимость — шрифт Onest с Google Fonts,
запасной вариант — system-ui.

## Локальная проверка

```bash
python3 -m http.server 8000
# http://localhost:8000
```

Открыть файл напрямую тоже можно, но копирование адреса в буфер обмена
работает только в защищённом контексте (https или localhost).

## Что заменить перед публикацией

Значения подставлены по данным из окружения. Проверьте три строки:

| Что | Где | Текущее значение |
| --- | --- | --- |
| Telegram | `href="https://t.me/..."` | `@monod0t` |
| Email | `data-copy` и `aria-label` у кнопки | `alimahmetov111@gmail.com` |
| GitHub | `href="https://github.com/..."` | `virtuoso3004` |

Плюс адрес страницы в `<link rel="canonical">`, `og:url` и в `<title>`,
если репозиторий будет называться иначе.

## Публикация на GitHub Pages

```bash
git init -b main
git add index.html README.md
git commit -m "Mono: одностраничный сайт-визитка"
git remote add origin https://github.com/ЛОГИН/mono-site.git
git push -u origin main
```

Создать публичный репозиторий и включить Pages (нужен `gh` и авторизация):

```bash
gh repo create mono-site --public --source=. --remote=origin --push
gh api --method POST repos/ЛОГИН/mono-site/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

Без `gh`: создайте репозиторий `mono-site` на github.com, запушьте `main`,
затем Settings → Pages → Source: Deploy from a branch → `main`, папка `/ (root)`.
Через минуту страница будет доступна по адресу
`https://ЛОГИН.github.io/mono-site/`.
