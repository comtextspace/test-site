# Пример сайта с книгами

Инструкция по созданию сайта с книгами на основе технологий ComText. Подходит для библиотеки или архива статей.

Примеры архивов:

* [Архив конференции «Ильенковские чтения»](https://dk.comtext.space/)
* [Архив работ Вальтраут Фрицевны Шелике](https://schaelike.comtext.space/)

Возможности:

* Разметка книг в [формате Comtext](https://research.comtext.space/format-comtext.html).
* Автоматическая генерация сайта из файлов в текстовом формате.  
* Автоматический экспорт книг и статей в форматы FB2 и EPUB.  
* Сервер не требуется: тексты хранятся в репозитории на GitHub, а сайт публикуется автоматически через GitHub Pages. 
* Можно использовать свой домен или стандартный адрес GitHub Pages.

## 1. Скопируйте файлы

Создайте новый репозиторий и скопируйте в него содержимое [этого репозитория](https://github.com/comtextspace/test-site).

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

## 2. Измените название сайта

В файле `comtext.yml` укажите желаемое название:

```yaml
vuepress:
  title: "Пример сайта"
```

## 3. Укажите домен (опционально)

Если вы хотите привязать собственный домен, отредактируйте файл `.github/workflows/deploy-site.yml`.

Замените:

```yaml
url: null
```

на

```yaml
url: mysite.net
```

В настройках DNS вашего домена добавьте запись `CNAME`:

```
CNAME my-github.github.io.
```

Замените `my-github` на имя вашего аккаунта на GitHub.

## 4. Настройте базовый путь сайта 

Если используется собственный домен (например, `mysite.net`), укажите в `comtext.yml`:

```yaml
vuepress:
  title: "Пример сайта"
  base: "/"
```

Если используется стандартный адрес GitHub Pages вида `https://comtextspace.github.io/test-site/`, где `test-site` — имя репозитория, укажите:

```yaml
vuepress:
  title: "Пример сайта"
  base: "/test-site/"
```

## 5. Включите GitHub Pages

В настройках репозитория перейдите в раздел `Settings → Pages`, выберите ветку `gh-pages` и сохраните изменения.

## 6. Добавьте книги

Поместите файлы книг в каталог `content/` в [формате Comtext](https://research.comtext.space/format-comtext.html).

Добавьте пути к книгам в `comtext.yml`:

```yaml
books:
  - content/book01.md
  - content/book02.md
```

Добавьте ссылки на книги в файл главной страницы `index.md`:

```
## Книги

- [Первая книга](book01.md) [[files book01]] [PDF](https://my-link){.file-link}
- [Вторая книга](book02.md) [[files book01]] [PDF](https://my-link){.file-link}
```

После отправки изменений в репозиторий сайт будет автоматически пересобран и опубликован.

[Пример этого сайта](https://comtextspace.github.io/test-site/).
