# SEO Setup — Цена Дня WB

Сайт: https://kristall2002-art.github.io/tsena-dnya-site/
Sitemap: https://kristall2002-art.github.io/tsena-dnya-site/sitemap.xml (1820 URL)

---

## 1. Google Search Console

### Регистрация
1. Перейти: https://search.google.com/search-console/
2. Нажать "Добавить ресурс"
3. Выбрать "Ресурс с префиксом URL" и ввести: `https://kristall2002-art.github.io/tsena-dnya-site/`
4. Выбрать метод верификации "Тег HTML"
5. Скопировать мета-тег вида: `<meta name="google-site-verification" content="ВАША_СТРОКА">`
6. Добавить этот тег в `<head>` файла `index.html` (и желательно в шаблон generate.py для всех страниц)
7. Сделать git push
8. Подождать ~2 минуты пока GitHub Pages обновится
9. Нажать "Подтвердить" в Google Search Console

### Альтернативный метод — HTML-файл
1. Google даст файл вида `google1234567890abcdef.html`
2. Положить его в корень сайта `/home/sergei/tsena-dnya-site/`
3. git push
4. Подтвердить

### Подача sitemap
1. В Google Search Console: боковое меню -> "Файлы Sitemap"
2. Ввести: `sitemap.xml`
3. Нажать "Отправить"
4. Статус должен стать "Успешно" через несколько минут

### Запрос индексации
1. В Google Search Console: строка поиска сверху -> вставить URL главной страницы
2. Нажать "Запросить индексирование"
3. Повторить для ключевых страниц (категории)
4. Для 1800+ товарных страниц — достаточно подать sitemap, Google обойдёт их сам

---

## 2. Яндекс.Вебмастер

### Регистрация
1. Перейти: https://webmaster.yandex.ru/
2. Войти с Яндекс ID
3. Нажать "+" (добавить сайт)
4. Ввести: `https://kristall2002-art.github.io/tsena-dnya-site/`
5. Выбрать метод верификации:
   - **Мета-тег** (рекомендуется): скопировать `<meta name="yandex-verification" content="ВАША_СТРОКА">` и добавить в `<head>` файла `index.html`
   - **HTML-файл**: скачать файл `yandex_XXXXX.html` и положить в корень сайта
6. git push, подождать обновления GitHub Pages
7. Нажать "Проверить"

### Подача sitemap
1. В Яндекс.Вебмастере: "Индексирование" -> "Файлы Sitemap"
2. Добавить URL: `https://kristall2002-art.github.io/tsena-dnya-site/sitemap.xml`
3. Нажать "Добавить"

### Запрос индексации
1. "Индексирование" -> "Переобход страниц"
2. Добавить URL главной и категорий
3. Яндекс обойдёт остальные через sitemap

---

## 3. Текущее состояние SEO (аудит)

### OG-теги — OK
- Все страницы товаров: og:title, og:description, og:image (WB), og:url, og:type=product
- Все страницы категорий: og:title, og:description, og:image (icon-512), og:url, og:type=website
- twitter:card = summary_large_image на товарах, summary на категориях

### Schema.org (JSON-LD) — OK
- Товары: @type=Product, price (число), priceCurrency=RUB, availability=InStock
- BreadcrumbList на товарах: Главная -> Категория -> Товар
- JSON валидный

### Мета-теги — OK
- Уникальный title на каждой странице товара
- Description содержит название и цену
- canonical URL корректный

### Хлебные крошки (HTML) — OK
- Категории: Главная > Категория
- Товары: Главная > Категория > Товар
- Все ссылки относительные и корректные

### Ссылки — OK
- "Купить на WB" -> wildberries.ru/catalog/{article}/detail.aspx
- "Следить за ценой" -> t.me/tsena_dnya_bot?start=track_{article}
- "Главная" -> ../../ (корректно)
- Карточки в категориях -> ../../products/{article}/

### Мелкие замечания
- На страницах категорий нет JSON-LD BreadcrumbList (есть только HTML-хлебные крошки). Не критично, но можно добавить для полноты.
- robots.txt и sitemap.xml — на месте.

---

## 4. Чек-лист после верификации

- [ ] Добавить мета-тег Google в index.html (и в generate.py шаблон)
- [ ] Добавить мета-тег Яндекса в index.html (и в generate.py шаблон)
- [ ] git push
- [ ] Подтвердить оба вебмастера
- [ ] Подать sitemap в Google Search Console
- [ ] Подать sitemap в Яндекс.Вебмастер
- [ ] Запросить индексацию главной страницы в обоих
- [ ] Через 3-7 дней проверить покрытие индекса
