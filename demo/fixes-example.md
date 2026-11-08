# Правки для example.com

Аудит: **58/100** · 38/66 веса · провалено проверок: 12 · 2026-11-08

Порядок: сначала критичные/важные, затем средние. Готовые теги — в `snippets.html`, файлы — в `snippets/`.

| # | Проверка | Сейчас | Предлагается | Куда |
|---|---|---|---|---|
| 1 | Title 30–60 символов | «Example Domain» (14 симв.) | база «Example Domain» — дополнить брендом/городом до 30–60 символов (шаблон ниже, подставьте свои значения) | <head> → <title> |
| 2 | Meta description 70–160 символов | отсутствует | «This domain is for use in documentation examples without needing permission. This is not a service; avoid relying on it for testing and monitoring purposes.» (156 симв.) | <head> → <meta name="description"> |
| 3 | Ровно один H1 | 0 заголовков H1 | добавить <h1>Example Domain</h1> в начало контента | первый блок <body> после шапки |
| 4 | Canonical | отсутствует | <link rel="canonical" href="https://example.com/"> | <head> |
| 5 | robots.txt | отсутствует или пуст | создать https://example.com/robots.txt (готовый файл в snippets/robots.txt) | корень сайта |
| 6 | sitemap.xml | отсутствует | создать https://example.com/sitemap.xml из 0 внутренних ссылок (файл в snippets/sitemap.xml, дополнить последние страницы) | корень сайта |
| 7 | Open Graph | нет или неполные | добавить og:title/description/type/url | <head> |
| 8 | Twitter Card | отсутствует | добавить twitter:card и twitter:title | <head> |
| 9 | JSON-LD разметка | отсутствует | добавить Organization (поля name/url) | <head> или перед </body> |
| 10 | Security-заголовки | меньше 2 из 5 | добавить X-Content-Type-Options, X-Frame-Options, Referrer-Policy, CSP (конфиги nginx/apache в snippets/) | конфиг сервера |
| 11 | H2-подзаголовки есть | не пройдена: h2=0 | Разбить текст H2-подзаголовками с второстепенными ключами (структура + удержание). | настройка сайта |
| 12 | Порядок заголовков без пропусков (H1→H2→H3) | не пройдена: заголовков нет | Не прыгать через уровень (после H1 — H2, не H3); починить иерархию заголовков. | настройка сайта |

## Детали

### 1. Title 30–60 символов (важно)
- Сейчас: «Example Domain» (14 симв.)
- Предлагается: база «Example Domain» — дополнить брендом/городом до 30–60 символов (шаблон ниже, подставьте свои значения)
- Где: <head> → <title>

```html
<title>{Example Domain} — {name/city}</title>
```

### 2. Meta description 70–160 символов (важно)
- Сейчас: отсутствует
- Предлагается: «This domain is for use in documentation examples without needing permission. This is not a service; avoid relying on it for testing and monitoring purposes.» (156 симв.)
- Где: <head> → <meta name="description">

```html
<meta name="description" content="This domain is for use in documentation examples without needing permission. This is not a service; avoid relying on it for testing and monitoring purposes.">
```

### 3. Ровно один H1 (важно)
- Сейчас: 0 заголовков H1
- Предлагается: добавить <h1>Example Domain</h1> в начало контента
- Где: первый блок <body> после шапки

```html
<h1>Example Domain</h1>
```

### 4. Canonical (важно)
- Сейчас: отсутствует
- Предлагается: <link rel="canonical" href="https://example.com/">
- Где: <head>

```html
<link rel="canonical" href="https://example.com/">
```

### 5. robots.txt (средне)
- Сейчас: отсутствует или пуст
- Предлагается: создать https://example.com/robots.txt (готовый файл в snippets/robots.txt)
- Где: корень сайта

```html
User-agent: *
Allow: /

Sitemap: https://example.com/sitemap.xml

```

### 6. sitemap.xml (средне)
- Сейчас: отсутствует
- Предлагается: создать https://example.com/sitemap.xml из 0 внутренних ссылок (файл в snippets/sitemap.xml, дополнить последние страницы)
- Где: корень сайта

```html
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
</urlset>

```

### 7. Open Graph (средне)
- Сейчас: нет или неполные
- Предлагается: добавить og:title/description/type/url
- Где: <head>

```html
<meta property="og:title" content="Example Domain">
<meta property="og:description" content="This domain is for use in documentation examples without needing permission. This is not a service; avoid relying on it for testing and monitoring purposes.">
<meta property="og:type" content="website">
<meta property="og:url" content="https://example.com/">
```

### 8. Twitter Card (низко)
- Сейчас: отсутствует
- Предлагается: добавить twitter:card и twitter:title
- Где: <head>

```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Example Domain">
```

### 9. JSON-LD разметка (низко)
- Сейчас: отсутствует
- Предлагается: добавить Organization (поля name/url)
- Где: <head> или перед </body>

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example",
  "url": "https://example.com/"
}
</script>
```

### 10. Security-заголовки (средне)
- Сейчас: меньше 2 из 5
- Предлагается: добавить X-Content-Type-Options, X-Frame-Options, Referrer-Policy, CSP (конфиги nginx/apache в snippets/)
- Где: конфиг сервера

```html
# nginx
add_header X-Content-Type-Options nosniff;
add_header X-Frame-Options SAMEORIGIN;
add_header Referrer-Policy strict-origin-when-cross-origin;
add_header Permissions-Policy "geolocation=(), microphone=()";

```

### 11. H2-подзаголовки есть (средне)
- Сейчас: не пройдена: h2=0
- Предлагается: Разбить текст H2-подзаголовками с второстепенными ключами (структура + удержание).
- Где: настройка сайта

### 12. Порядок заголовков без пропусков (H1→H2→H3) (низко)
- Сейчас: не пройдена: заголовков нет
- Предлагается: Не прыгать через уровень (после H1 — H2, не H3); починить иерархию заголовков.
- Где: настройка сайта
