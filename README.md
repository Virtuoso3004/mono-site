# Mono. — сайт-визитка

Одностраничный сайт фронтенд-разработчика Mono. Живая версия:
**https://virtuoso3004.github.io/mono-site/**

Один `index.html` с inline CSS и JS, без фреймворков и сборки. Единственная
внешняя зависимость — Google Fonts (Unbounded и Golos Text).

## Что внутри

- Логотип собран из четырёх PNG-спрайтов в `assets/` по процентам из
  `assets/positions.json`: кольцо, синий пазл, надпись MONO и точка.
- Анимация сборки логотипа с магнитной `ease-in`-кривой, серой точкой
  `#2b2f3a` до стыка, вспышкой, волной и синей точкой. Клик по логотипу
  повторяет сборку.
- `prefers-reduced-motion`: анимации отключаются, логотип сразу собран.
- Две карточки проектов с CSS-превью и нативными `<dialog>`-окнами.
  Открытие от точки клика, закрытие по фону и Esc.
- Контакты: Telegram [@monod0t](https://t.me/monod0t) и
  GitHub [Virtuoso3004](https://github.com/Virtuoso3004).
- Mobile-first, проверено на 360–1440 px; safe-area, `touch-action`,
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
