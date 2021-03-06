# split-file-js

![split-file-js](https://github.com/chekit/split-file-js/blob/master/scissors.png?raw=true)

Скрипт использовался на проекте для создания небольших landing-pages.

В результате сборки проекта получались наборы страниц и файлов, которые именовались по шаблону: 
- *landing-<номер лэндинга>.html*
- *landing-<номер лэндинга>.min.css*

Далее из получившегося html файла необхоми было выделить "уникальные" контентные части, записать их в php файлы, а представленные в .html файле строки вида `%<имя переменной>%` заменить  соответсвующие php переменные вида `<?= $<имя переменной>; ?>`.

> "уникальные" контентные части вычислялись по окружающим их html-комментанриям (комментарии были строго предопределены в шаблоне)

В итоге у нас получались следующие файлы:
- *landing-<номер лэндинга>.content.php*
- *landing-<номер лэндинга>.footer.php*
- *landing-<номер лэндинга>.min.css*

> `<номер лэндинга>` передавался при вызове таска срипта из консоли, например `npm run split -- 10`

Каждый такой набор файлов копировался на сервер разработки в соответствующую папку и подключался к общему index.php файлу. Таким образом в index.php и общем styles.min.css хранилась неизменяемая структура и стили, а подключаемые части были независимы и взаимозаменяемы.


> Скрипт использует обычный JavaScript и *nodejs* модуль *fs* (file system)

> Скрипт был сделан на основе аналогичного для проекта, где результирующий `index.html` нужно было разделять на части вида `header.mobile.html`, `footer.mobile.html` и т.д.
