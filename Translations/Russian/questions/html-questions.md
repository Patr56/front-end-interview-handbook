# HTML Вопросы и ответы

Ответы на [вопросы кандидату на должность front-end разработчика - HTML вопросы](https://github.com/h5bp/Front-end-Developer-Interview-Questions/tree/master/Translations/Russian#html). Pull requests предложения и исправления приветствуются!

* [Для чего нужен `doctype`?](#Для-чего-нужен-doctype)
* [Как следует оформлять страницу, содержимое которой может быть на разных языках?](#Как-следует-оформлять-страницу-содержимое-которой-может-быть-на-разных-языках)
* [На что необходимо обратить внимание при разработке мультиязычных сайтов?](#На-что-необходимо-обратить-внимание-при-разработке-мультиязычных-сайтов)
* [Для чего отлично подойдут `data-` атрибуты?](#Для-чего-отлично-подойдут-data--атрибуты)
* [Представьте HTML5 как открытую веб-платформу. Из каких блоков состоит HTML5?](#Представьте-html5-как-открытую-веб-платформу-Из-каких-блоков-состоит-html5)
* [Объясните разницу между `cookie`, `sessionStorage` и `localStorage`.](#Объясните-разницу-между-cookie-sessionstorage-и-localstorage)
* [Объясните разницу между `<script>`, `<script async>` и `<script defer>`.](#Объясните-разницу-между-script-script-async-и-script-defer)
* [Почему хорошей практикой считается располагать `<link>` для подключения CSS между `<head></head>`, а `<script>` для подключения JS ставить перед `</body>`? Знаете ли вы исключения?](#Почему-хорошей-практикой-считается-располагать-link-для-подключения-css-между-headhead-а-script-для-подключения-js-ставить-перед-body-Знаете-ли-вы-исключения)
* [Что такое прогрессивный рендеринг?](#Что-такое-прогрессивный-рендеринг)
* [Для чего используется атрибут `srcset` в теге изображения? Опишите процесс, который использует браузер при оценке содержимого этого атрибута.](#Для-чего-используется-атрибут-srcset-в-теге-изображения-Опишите-процесс-который-использует-браузер-при-оценке-содержимого-этого-атрибута)
* [Приходилось ли вам работать с языками HTML-шаблонизации?](#Приходилось-ли-вам-работать-с-языками-html-шаблонизации)

### Для чего нужен `doctype`?

Элемент `<!DOCTYPE>` предназначен для указания типа текущего документа — DTD (document type definition, описание типа документа). Это необходимо, чтобы браузер понимал, как следует интерпретировать текущую веб-страницу, поскольку HTML существует в нескольких версиях, кроме того, имеется XHTML (EXtensible HyperText Markup Language, расширенный язык разметки гипертекста), похожий на HTML, но различающийся с ним по синтаксису. Чтобы браузер «не путался» и понимал, согласно какому стандарту отображать веб-страницу и необходимо в первой строке кода задавать `<!DOCTYPE html>`.

###### Источники

* http://htmlbook.ru/html/%21doctype
* https://stackoverflow.com/questions/7695044/what-does-doctype-html-do
* https://www.w3.org/QA/Tips/Doctype
* https://quirks.spec.whatwg.org/#history

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Как следует оформлять страницу, содержимое которой может быть на разных языках?

Вопрос немного расплывчатый, предположу, что спрашивается о наиболее распространенном случае, а именно о том, как оформлять страницу, доступную на нескольких языках, но на странице оформление должно быть только на одном языке.

Когда HTTP запрос отправляется на сервер, браузерный клиент, обычно, передаёт информацию о языке системы, например в заголовке запроса `Accept-Language`. Сервер может использовать эту информацию из заголовка и вернуть нужную языковую версию страницы, если таковая имеется, иначе вернётся страница по умолчанию. Возвращаемый HTML документ, должен содержать атрибут `lang` в `<html>` тэге, например `<html lang="en">...</html>`

На сервере, разметка HTML содержат `i18n` метки для вставки переводов, в зависимости от языка. Контекст для отображения содержится в специальных языковых хранилищах, например в файлах YML или JSON. Затем сервер динамически генерирует HTML-страницу с содержимым на выбранном языке, обычно с помощью серверного фреймворка/платформы.

###### Источники

* https://www.w3.org/International/getting-started/language

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### На что необходимо обратить внимание при разработке мультиязычных сайтов?

* Использование `lang` атрибута в HTML.
* Направление пользователей на их родной язык. Это позволяет пользователю легко изменить свою страну / язык без проблем.
* Текст в изображениях, это не является масштабируемым подходом. Размещение текста в изображении является популярным способом получить красивые, несистемные шрифты для отображения на любом компьютере. Каждый поддерживаемый язык на сервере для пользователей, должен содержать такой же язык в изображении. Это очень накладно и может со временем выйти из-под контроля.
* Ограничительные слова / длина предложения. Некоторый текст может быть длиннее или короче при написании на другом языке. Будьте осторожны, текст на другом языке может вылезти за пределы отведённого места, при отображении на странице. Лучше избегать ситуаций, когда количество текста может привести к нарушению оформления страницы. Количество символов вступает в неприятную игру с такими элементами, как заголовки, ярлыки и кнопки. Текст статьи или комментарии менее подвержены проблемам переводов на разные языки.
* Восприятие цвета. Цвета воспринимаются по-разному в разных языках и культурах. Дизайн должен использовать цвет соответствующим образом.
* Форматирование дат и валют. Календарные даты иногда представлены по-разному. Например "Май 31, 2012" в США и "31 мая 2012" в России.
* Не объединяйте переведенные строки. Не делайте ничего подобного `"Сегодняшняя дата" + date`. Это не подходит для языков с различным порядком слов. Вместо этого используйте шаблонную строку с подстановкой параметров для каждого языка. Например, посмотрите на следующие два предложения на английском и китайском языках: `"I will travel on {% date %}"` и `"{% date %} 我会出发"`.  Обратите внимание, что позиция переменной `date` отличается из-за грамматических правил языка.
* Направление чтения языка. На русском языке, мы читаем слева-направо, сверху-вниз, на традиционном японском языке, текст читается вверх-вниз, справа-налево.

###### Источники

* https://www.quora.com/What-kind-of-things-one-should-be-wary-of-when-designing-or-developing-for-multilingual-sites

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Для чего отлично подойдут `data-` атрибуты?

До того, как JavaScript фреймворки стали популярными, программисты использовали `data-` атрибуты для хранения информации внутри DOM дерева, без использования нестандартных атрибутов HTML-тэгов или дополнительных свойств DOM дерева. Этот способ подходит для хранения данных, скрытых от страницы или приложения, для которых больше нет соответствующих атрибутов или элементов.

В наши дни плохая практика использовать атрибуты `data -`. Пользователи могут сами легко изменить атрибут данных с помощью "Инструмента разработчика" в браузере. Модель данных лучше хранить в самом JavaScript и изменять DOM через привязку данных, например, через JavaScript библиотеку или фреймворк (React, Angular, Vue и т.д.).

###### Источники

* http://html5doctor.com/html5-custom-data-attributes/
* https://www.w3.org/TR/html5/dom.html#embedding-custom-non-visible-data-with-the-data-*-attributes

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Представьте HTML5 как открытую веб-платформу. Из каких блоков состоит HTML5?

* Семантика - позволяет точнее описывать, что из себя представляет ваш контент (Новые HTML тэги).
* Связь - новые способы общения с сервером (WebSockets, Server-sent события, WebRTC).
* Оффлайн и Хранилище - методы, позволяющие сохранять информацию локально на стороне клиента (Кеш приложения, DOM Storage, IndexedDB).
* Мультимедиа - создание и взаимодействие с видео и звуком (HTML5 audio и video, WebRTC, Camera API).
* 2D/3D Графика и эффекты - способы значительно разнообразить  представление (Canvas, SVG, WebGL).
* Производительность и интеграция - обеспечивает оптимизацию скорости и лучшеее использование компьютерного оборудования (Web Workers, JIT-компилирование).
* Доступ к устройству - использование разных устройств для ввода и вывода информации (Camera API, Touch события, Геолокация).
* Стилизация - создание изощренных и совершенных тем (CSS).

###### Источники

* https://developer.mozilla.org/ru/docs/HTML/HTML5

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Объясните разницу между `cookie`, `sessionStorage` и `localStorage`.

Все вышеперечисленные технологии являются хранилищами данных типа ключ-значение на стороне клиента. Они могут хранить значения только в виде строк.

|                                               | `cookie`                                                    | `localStorage` | `sessionStorage`    |
| --------------------------------------------- | ----------------------------------------------------------- | -------------- | ------------------- |
| Инициатор                                     | Клиент или сервер. Сервер использует заголовок `Set-Cookie` | Клиент         | Клиент              |
| Срок действия                                 | Задаётся вручную                                            | Навсегда       | По закрытию вкладки |
| Персистентность между сеансами браузера       | Зависит от того, установлен ли срок действия                | Да             | Нет                 |
| Отправляется на сервер с каждым HTTP запросом | Автоматически проставляются в заголовке `Cookie` запроса    | Нет            | Нет                 |
| Ограничения размера (на домен)                | 4kb                                                         | 10MB           | 10MB                |
| Доступность                                   | Все окна                                                    | Все окна       | Некоторые вкладки   |

###### Источники

* https://www.html5rocks.com/en/tutorials/offline/quota-research/
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies
* http://tutorial.techaltum.com/local-and-session-storage.html

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Объясните разницу между `<script>`, `<script async>` и `<script defer>`.

* `<script>` - Парсинг HTML приостанавливается, скрипт загружается и выполняется немедленно, парсинг HTML продолжается после выполнения скрипта.
* `<script async>` - Скрипт будет загружаться параллельно с парсингом HTML и выполнен так скоро, как это возможно (потенциально до окончания парсинга HTML). Используйте `async`, когда выполнение скрипта не зависит от остальных скриптов на странице, например для аналитики.
* `<script defer>` - Скрипт будет загружаться параллельно с парсингом HTML и будет выполнен после парсинга страницы. Если на странице несколько таких скриптов, они будут выполняться по порядку расположения в документе. Если для скрипта требуется полное DOM дерево на момент выполнения, то `defer` атрибут отлично подойдёт. У этого подхода нет больших отличий от обычного `<script>` расположенного рядом с закрывающимся тегом `</body>`.  Скрипт с атрибутом `defer` не должен содержать `document.write`.

Примечание: `async` и `defer` атрибуты игнорируются, если отсутствует атрибут `src`.

###### Источники

* http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html
* https://stackoverflow.com/questions/10808109/script-tag-async-defer
* https://bitsofco.de/async-vs-defer/

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Почему хорошей практикой считается располагать `<link>` для подключения CSS между `<head></head>`, а `<script>` для подключения JS ставить перед `</body>`? Знаете ли вы исключения?

**Размещение тэгов `<link>` в `<head>`**

Размещение `<link>` в заголовке документа HTML - это часть спецификации HTML. Размещение в самом начале HTML документа тэгов `<link>`, позволяет документу отображаться постепенно, что улучшает восприятие пользователем информации. Если стили подключаются в конце HTML документа, это может заблокировать постепенное отображение документа во многих браузерах, например Internet Explorer. Некоторые браузеры блокируют отрисовку, чтобы избежать необходимость перекрашивать элементы страницы при изменении стилей. В этот момент пользователь, обычно, видит пустую белую страницу. Это предотвращает резкие изменения оформления контекста на странице.

**Размещение тэгов `<script>` только перед `</body>`**

`<script>` блокирует парсинг HTML, скачивает скрипт и выполняет его. Скачивание скриптов в конце документа, позволяет браузеру сперва распарсить HTML и отобразить содержимое пользователю, а затем приступить к выполнению скриптов.

В некоторых ситуациях невозможно расположить `<script>` внизу документа, например при использовании в скрипте `document.write()`, хотя это плохая практика. Также, расположение `<script>` в конце документа, подразумевает, что браузер не может начать скачивание скриптов, пока не распарсит весь документ. Одним из возможных решений является размещение `<script>` внутри `<head>` с использованием атрибута `deffer`

###### Источники

* https://developer.yahoo.com/performance/rules.html#css_top

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Что такое прогрессивный рендеринг?

Progressive rendering is the name given to techniques used to improve the performance of a webpage (in particular, improve perceived load time) to render content for display as quickly as possible.

It used to be much more prevalent in the days before broadband internet but it is still used in modern development as mobile data connections are becoming increasingly popular (and unreliable)!

Examples of such techniques:

* Lazy loading of images - Images on the page are not loaded all at once. JavaScript will be used to load an image when the user scrolls into the part of the page that displays the image.
* Prioritizing visible content (or above-the-fold rendering) - Include only the minimum CSS/content/scripts necessary for the amount of page that would be rendered in the users browser first to display as quickly as possible, you can then use deferred scripts or listen for the `DOMContentLoaded`/`load` event to load in other resources and content.
* Async HTML fragments - Flushing parts of the HTML to the browser as the page is constructed on the back end. More details on the technique can be found [here](http://www.ebaytechblog.com/2014/12/08/async-fragments-rediscovering-progressive-html-rendering-with-marko/).

###### Источники

* https://stackoverflow.com/questions/33651166/what-is-progressive-rendering
* http://www.ebaytechblog.com/2014/12/08/async-fragments-rediscovering-progressive-html-rendering-with-marko/

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Для чего используется атрибут `srcset` в теге изображения? Опишите процесс, который использует браузер при оценке содержимого этого атрибута.

You would use the `srcset` attribute when you want to serve different images to users depending on their device display width - serve higher quality images to devices with retina display enhances the user experience while serving lower resolution images to low-end devices increase performance and decrease data wastage (because serving a larger image will not have any visible difference). For example: `<img srcset="small.jpg 500w, medium.jpg 1000w, large.jpg 2000w" src="..." alt="">` tells the browser to display the small, medium or large `.jpg` graphic depending on the client's resolution. The first value is the image name and the second is the width of the image in pixels. For a device width of 320px, the following calculations are made:

* 500 / 320 = 1.5625
* 1000 / 320 = 3.125
* 2000 / 320 = 6.25

If the client's resolution is 1x, 1.5625 is the closest, and `500w` corresponding to `small.jpg` will be selected by the browser.

If the resolution is retina (2x), the browser will use the closest resolution above the minimum. Meaning it will not choose the 500w (1.5625) because it is greater than 1 and the image might look bad. The browser would then choose the image with a resulting ratio closer to 2 which is 1000w (3.125).

`srcset`s solve the problem whereby you want to serve smaller image files to narrow screen devices, as they don't need huge images like desktop displays do — and also optionally that you want to serve different resolution images to high density/low-density screens.

###### Источники

* https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images
* https://css-tricks.com/responsive-images-youre-just-changing-resolutions-use-srcset/

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Приходилось ли вам работать с языками HTML-шаблонизации?

Yes, Pug (formerly Jade), ERB, Slim, Handlebars, Jinja, Liquid, just to name a few. In my opinion, they are more or less the same and provide similar functionality of escaping content and helpful filters for manipulating the data to be displayed. Most templating engines will also allow you to inject your own filters in the event you need custom processing before display.

[[↑] К оглавлению](#html-Вопросы-и-ответы)

### Другие ответы

* https://neal.codes/blog/front-end-interview-questions-html/
* http://peterdoes.it/2015/12/03/a-personal-exercise-front-end-job-interview-questions-and-my-answers-all/

---
