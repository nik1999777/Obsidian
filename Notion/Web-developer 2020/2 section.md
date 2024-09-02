  

- Bootstrap
    
    Документация bootstrap:
    
    [https://getbootstrap.com/](https://getbootstrap.com/)
    
    Колоночная верстка:
    
    ```HTML
    <div class="container">
            <div class="row">
                <div class="col-3">1</div>
                <div class="col-5">2</div>
                <div class="col-4">3</div>
            </div>
            <div class="row"></div>
    </div>
    ```
    
- Препроцессоры. SASS/SCSS/LESS
    
    Конвертация CSS в SASS:
    
    [https://css2sass.herokuapp.com/](https://css2sass.herokuapp.com/)
    
    ```Scss
    $text_color: blue
    @mixin box 
        display: block
        width: 250px
        height: 200px   
        background-color: red
        
    h1  
        color: $text_color
        font-size: 50px
        @include box
    h2
        color: $text_color
    .block
        background-color: black
        h3
            color: $text_color 
        &_color
            background-color: \#fff
            button
                @include box
        .block_color
            color: $text_color
    ```
    
- Псевдоклассы и псевдоэлементы в CSS
    
    Псевдоклассы:
    
    **Псевдокласс :hover**
    
    Определяет стиль элемента при наведении на него курсора мыши, но при этом элемент еще не активирован, иными словами кнопка мыши не нажата.
    
    **Псевдокласс :active**
    
    Псевдокласс :active определяет стиль активного элемента. Это такое состояние элемента, которое происходит между щелчком и отпусканием клавиши мыши. В основном применяется к ссылкам и кнопкам, но ими не ограничен.
    
    **Псевдокласс :focus**
    
    Псевдокласс :focus определяет стиль для элемента, получающего фокус. Например, им может быть текстовое поле формы, в которое устанавливается курсор.
    
    **Псевдокласс :nth-child**
    
    Псевдокласс :nth-child используется для добавления стиля к элементам на основе нумерации в дереве элементов.
    
      
    
    Псевдоэлементы:
    
    **Псевдоэлемент ::after**
    
    Псевдоэлемент, который используется для вывода контента после содержимого элемента, к которому он добавляется. Псевдоэлемент ::after работает совместно со свойством [content](https://webref.ru/css/content).
    
    **Псевдоэлемент ::before**
    
    Псевдоэлемент ::before применяется для отображения контента до содержимого элемента, к которому он добавляется. Работает совместно со свойством [content](https://webref.ru/css/content).
    
    По умолчанию ::before создаёт строчный элемент
    
- Настройки VSCode
    
    ```JavaScript
    {
        "window.zoomLevel": 1,
        "workbench.activityBar.visible": true,
        "workbench.statusBar.visible": true,
        "workbench.colorTheme": "Oceanic Next",
        "liveServer.settings.donotShowInfoMsg": true,
        "editor.minimap.enabled": false,
        "editor.multiCursorModifier": "ctrlCmd",
        "explorer.confirmDelete": false,
        "editor.formatOnPaste": false,
        "editor.detectIndentation": false,
        "javascript.updateImportsOnFileMove.enabled": "always",
        "explorer.confirmDragAndDrop": false,
        "workbench.iconTheme": "vscode-icons",
        "liveSassCompile.settings.formats": [
        
            {
                "format": "compressed",
                "extensionName": ".min.css",
                "savePath": "~/../css/"
            }
        ],
        "liveSassCompile.settings.autoprefix": [
            "> 1%",
            "last 2 versions"
        ]
    }
    ```
    
- Как работать с иконками. Иконочные шрифты
    
    Ресурс для поиска иконок:
    
    [https://seeklogo.com/](https://seeklogo.com/)
    
    Создать свой иконочный шрифт:
    
    [https://icomoon.io/app/#/select](https://icomoon.io/app/#/select)
    
    Еще один ресурс с иконками:
    
    [https://www.flaticon.com/](https://www.flaticon.com/)
    
    FontAwesome: (как подключать иконочные шрифты)
    
    [https://fontawesome.com/](https://fontawesome.com/)
    
- Адаптация проектов под различные устройства
    
    Статья про медиа-запросы:
    
    [https://html5book.ru/css3-mediazaprosy/](https://html5book.ru/css3-mediazaprosy/)
    
    fixed - фиксированная верстка
    
    rubber - резиновая верстка
    
    adaptive - адаптивная весртка
    
    responsive - отзывчивая верстка
    
- Локальные ссылки и favicon
    
    Сервис для создания favicon
    
    [https://www.favicon.by/](https://www.favicon.by/)
    
    Как подключить favicon:
    
    [http://htmlbook.ru/faq/kak-dobavit-ikonku-sayta-v-adresnuyu-stroku-brauzera](http://htmlbook.ru/faq/kak-dobavit-ikonku-sayta-v-adresnuyu-stroku-brauzera)
    
    **Локальные ссылки:**
    
    ```HTML
    <section class="require" id="require">
    
    <li class="menu_item"><a href="\#require" class="menu_link">Со своим автомобилем</a></li>
    <li class="menu_item"><a href="\#require" class="menu_link">На автомобиле компании</a></li>
    ```
    
- Публикация сайта в интернете. Домен и хостинг.
    
    [https://pages.github.com/](https://pages.github.com/) -  документация как выложить сайт на github
    
    [https://www.divier.ru/stati/domeny_i_domennye_imena_v_chem_raznitsa/](https://www.divier.ru/stati/domeny_i_domennye_imena_v_chem_raznitsa/) - про разницу в доменах и доменных именах