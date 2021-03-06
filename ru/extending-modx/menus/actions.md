---
title: "Действия и меню"
translation: "extending-modx/menus/actions"
note: "Действия были объявлены устаревшими в 2.3 и будут удалены в 3.0."
---

MODX Revolution представляет совершенно новую структуру программы для своего ядра. Менеджер также построен на так называемых _контроллерах_ и _шаблонах_, которые используют обработку AJAX для отправки данных _коннекторам_, которые обращаются к _процессорам_.

Контроллеры - это просто PHP-файлы, которые загружают правильный шаблон Smarty для отображения и извлекают любые данные предварительного рендеринга для шаблона. Revolution абстрагирует эти контроллеры в БД как `modAction`, позволяя сторонним разработчикам легко создавать пользовательские страницы менеджера, которые «подключаются» к текущей системе MODX без изменения ядра.

Для работы `modAction` требуется наличие контроллера и шаблона, которые можно найти в каталогах `manager/controllers` и `manager/templates`. У них есть несколько определенных параметров, которые стоит отметить:

- **Контроллер** - указывает на файл контроллера. Если файл - index.php, вы можете отключить его, и MODX попытается найти его с помощью интеллектуального поиска.
- **Загрузить заголовки** - если этот флажок установлен, будет загружен верхний и нижний колонтитулы MODX для внутренней страницы. Если вы хотите просто пустую страницу для страницы менеджера, оставьте этот флажок выключенным.
- **Темы языка** - это просто разделение языковых областей, которые обеспечивают более быстрый доступ к i18n. Их можно найти в каталоге `core/lexicon/en` (или fr, de и т.д.), А новые темы можно легко создать, просто используя раздел Lexicon Management.

Например, сторонние разработчики могут захотеть создать тему лексикона под названием «кнопки» для TinyMCE, которая будет ссылаться на тему в `core/components/tinymce/lexicon/en/buttons.inc.php`.
Они могут просто: A) использовать скрипт сборки для установки лексикона через транспортный пакет или B) предложить пользователям импортировать темы лексикона с помощью утилиты **Import Lexicon** в **Управление словарями**.

Затем вы можете загрузить тему через:

``` php
$modx->lexicon->load('tinymce:buttons');
```

`modAction's` также легко подключаются к `modMenu`, которые являются абстрактными представлениями верхней строки меню в менеджере. Опять же, это позволяет сторонним разработчикам легко и быстро разрабатывать пользовательские реализации меню для своих компонентов - или позволяет пользователям переупорядочивать верхнее меню.

Всем этим можно управлять с помощью панели «Действия», которая находится в меню «Инструменты».

Любые изменения в порядке «основных» пунктов меню будут отменены во время обновлений Revolution.

## Связанные страницы

- [Пользовательские страницы менеджера](extending-modx/custom-manager-pages "Пользовательские страницы менеджера")
- [Интернационализация](extending-modx/internationalization "Интернационализация")
