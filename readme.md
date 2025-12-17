# Пример создания сайта с книгами.

[![Actions Status](https://github.com/comtextspace/test-site/workflows/deploy_site/badge.svg)](https://github.com/comtextspace/test-site/actions)

Инструкция как сделать сайт с книгами или архив статей на основе технологий `comtext`.

Преимущества:

* Автоматическая генерация сайта из материалов в текстовом формате.
* Автоматический экспорт книги и статей в форматы FB2 и EPUB.
* Не нужен отдельный сервер: исходный текст хранится на GitHub, а сайт хостится на GitHub Pages.

## Скопируйте файлы

Скопируйте файлы этого репозиторий в новый репозиторий.

Структура репозитория:

```
├── comtext.yml
├── index.md
├── readme.md
├── content
│   ├── book01.md
│   └── book02.md
└── .github
    └── workflows
        └── deploy-site.yml
```

## Измените название сайта

В файле `comtext.yml` измените название сайта.

```yaml
vuepress:
  title: "Пример сайта"
```

## Если нужно укажите домен

Если к сайту нужно подключить домен то укажите его в файле

```yaml
      url: # укажите домен или оставьте пустым
```

Например

```yaml
      url: mysite.net
```

В настройке DNS домена укажите `CNAME`.

```
CNAME my-github.github.io.
```

Вместо `my-github` используйте имя своего аккаунта на GitHub.

## Включите GitHub Pages

В настройках репозитория `Settings` — `Pages` установите ветку `gh-pages` и нажмите `save`.

## Добавьте книги

В каталог `content` добавьте книги в [формате Comtext](https://research.comtext.space/format-comtext.html).

В файл `comtext.yml` добавьте названия файлов книг.

```yaml
books:
  - content/book01.md
  - content/book02.md
```

Добавьте ссылки на книги на главную страницу в `index.md`.

```
## Книги

- [Первая книга](book01.md) [[files book01]] [PDF](https://my-link){.file-link}
- [Вторая книга](book02.md) [[files book01]] [PDF](https://my-link){.file-link}
```

После фиксации на GitHub сайт будет автоматически пересобран.
