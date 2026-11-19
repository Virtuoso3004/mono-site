# Mono. — сайт программиста

Одностраничный сайт программиста Mono. Живая версия:
**https://virtuoso3004.github.io/mono-site/**

Один `index.html` с inline CSS и JS, без фреймворков и сборки. Единственная
внешняя зависимость — Google Fonts (Unbounded и Golos Text).

## Что внутри

- Логотип собран из четырёх PNG-спрайтов в `assets/` по процентам из
  `assets/positions.json`: кольцо, синий пазл, надпись MONO и точка.
- Анимация сборки: кольцо и надпись, синий пазл входит сбоку по магнитной
  `ease-in`-кривой, серая точка `#2b2f3a` до стыка, затем вспышка, волна,
  искры и синяя точка. Клик по логотипу повторяет сборку.
- `prefers-reduced-motion`: анимации отключаются, логотип сразу собран.
- Две карточки проектов с CSS-превью: два пазла для сайта-визитки и
  интерфейс чата для Telegram-бота. Каждая открывает нативное
  `<dialog>`-окно.
- Блок «Что собираю» — семь плиток на серой сетке внутри отдельного окна:
  сайты, боты, автоматизация, интеграции, парсинг, поддержка и задача
  вне списка.
- Контакты: Telegram [@monod0t](https://t.me/monod0t) и
  GitHub [Virtuoso3004](https://github.com/Virtuoso3004).
- Mobile-first, проверено на 360–1920 px; safe-area, `touch-action`,
  видимый `:focus-visible`, без горизонтального скролла.

## Структура

```
index.html              страница целиком
assets/
  ring-white.png        белое кольцо
  piece-blue.png        синий пазл
  wordmark-mono-white.png
  dot-blue.png
  logo-full.png         фавикон и OG-изображение
  positions.json        координаты спрайтов
```

## Локальный запуск

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## Публикация

GitHub Pages: ветка `main`, корень репозитория. Страница пересобирается
автоматически после пуша в `main`.

## Контакты

- Telegram: https://t.me/monod0t
- GitHub: https://github.com/Virtuoso3004
- Бот: https://t.me/Mono_BeautyBot
