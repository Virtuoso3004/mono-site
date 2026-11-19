# Mono — сайт-визитка

Одна страница, один файл: `index.html` с inline CSS и JS. Без фреймворков,
сборки и npm. Единственная внешняя зависимость — шрифт Onest с Google Fonts,
запасной вариант — system-ui.

## Что на странице

| Секция | Якорь | Что внутри |
| --- | --- | --- |
| Шапка | `#top` | Имя, навигация, статус «Принимаю заказы» |
| Первый экран | — | Вордмарк `Mono.`, фраза и кнопка в Telegram |
| Проекты | `#projects` | Портфолио, проекты раскрываются по кнопке «Детали» |
| Что делаю | `#services` | Четыре направления |
| Чем работаю | `#stack` | Список технологий |
| Связаться | `#contacts` | Telegram, email, GitHub |
| Подвал | — | Год и ссылка наверх |

## Локальная проверка

```bash
python3 -m http.server 8000
# http://localhost:8000
```

Открыть файл напрямую тоже можно, но копирование адреса в буфер обмена
работает только в защищённом контексте: https или localhost.

## Как добавить проект

Найдите секцию `#projects` в `index.html`. Каждый проект — это блок:

```html
<article class="project">
  <div class="project__head">
    <h3 class="project__name">Название</h3>
  </div>
  <p class="project__desc">Одно предложение о том, что это и для кого.</p>
  <div class="project__foot">
    <p class="project__stack">Технологии через запятую</p>
    <button class="project__toggle" type="button" aria-expanded="false" aria-controls="project-3">
      <span class="project__toggle-label">Детали</span>
      <span class="toggle-icon" aria-hidden="true"></span>
    </button>
  </div>
  <div class="project__panel" id="project-3">
    <div class="project__panel-inner">
      <div class="project__panel-body">
        <p>Что сделано, как работает, чем полезно.</p>
        <ul class="project__links">
          <li><a href="https://ссылка">Открыть сайт</a></li>
        </ul>
      </div>
    </div>
  </div>
</article>
```

Вставьте блок перед строкой `<a class="project project--next" ...>`, чтобы
призыв «Обсудить ваш проект» остался последним. В новом блоке:

1. `aria-controls="project-3"` и `id="project-3"` должны совпадать.
2. Номер должен быть уникальным — у двух существующих проектов `project-1`
   и `project-2`.
3. Список ссылок можно убрать, если ссылок нет. Второй абзац тоже
   необязателен.

Кнопка «Детали» меняет подпись на «Скрыть» и работает с клавиатуры.
Без JavaScript панели открыты, а кнопки скрыты — текст проекта виден всегда.

## Контакты

| Что | Где | Текущее значение |
| --- | --- | --- |
| Telegram | `href="https://t.me/..."` в шапке, hero и контактах | `monod0t` |
| Email | `data-copy`, `aria-label` и видимая строка | `alimahmetov111@gmail.com` |
| GitHub | `href="https://github.com/..."` | `Virtuoso3004` |

Плюс адрес страницы в `<link rel="canonical">`, `og:url` и `<title>`,
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
