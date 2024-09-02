  

- Система контроля версий Git и сервис GitHub
    
    Git — это инструмент, позволяющий реализовать распределённую систему контроля версий, а GitHub — это сервис для проектов, использующих Git.
    
    Git создает репозитории, а GitHub сохраняет эти репозитории удаленно (хранилище репозиториев).
    
      
    
    **Репозито́рий**[[1]](https://ru.wikipedia.org/wiki/%D0%A0%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B9\#cite_note-1) ([англ.](https://ru.wikipedia.org/wiki/%D0%90%D0%BD%D0%B3%D0%BB%D0%B8%D0%B9%D1%81%D0%BA%D0%B8%D0%B9_%D1%8F%D0%B7%D1%8B%D0%BA) [_repository_](https://ru.wiktionary.org/wiki/repository#%D0%90%D0%BD%D0%B3%D0%BB%D0%B8%D0%B9%D1%81%D0%BA%D0%B8%D0%B9)), **хранилище** — место, где хранятся и поддерживаются какие-либо данные. Чаще всего данные в репозитории хранятся в виде файлов, доступных для дальнейшего распространения по [сети](https://ru.wikipedia.org/wiki/%D0%9A%D0%BE%D0%BC%D0%BF%D1%8C%D1%8E%D1%82%D0%B5%D1%80%D0%BD%D0%B0%D1%8F_%D1%81%D0%B5%D1%82%D1%8C).
    
      
    
    [https://githowto.com/ru](https://githowto.com/ru) - обучение по Git
    
      
    
    git init ( говорим, чтобы git следил за этой папкой, начинаем с него)
    
      
    
    git config --global user.name "Nik"   (указываем, кто работает над проектом)
    
    git config --global user.email  example@gmail.com  (почту того, кто работает над проектом)
    
    или git config -- local  ,если нам нужно конфигурировать файлы локально, а --global означает, что все проекты, которые мы будем создавать, они будут от нашего имени, а локально делается для того, чтобы в каких-то отдельных проектах мы могли указать другое имя.
    
      
    
    У Git репозитория есть 3 состояния файлов:
    
    1.Файлы просто созданы
    
    2.Git следит за определенными файлами
    
    3.Git создал контрольную точку или commit
    
      
    
    git status (проверяет статус git, его контрольные точки)
    
    git add -A (добавить все файлы репозитория)
    
    git add main.css (добавить конкретный файл репозитория)
    
    git commit -a -m "first commit" (создана контрольная точка, -a это значит все файлы добавлены)
    
    git log (если накопилось много commit, позволяет увидеть сколько их было, кем созданы и когда)
    
      
    
    git remote add origin [https://github.com/nik1999777/project.git](https://github.com/nik1999777/project.git)
    
    git push -u origin master (пушим на удаленный репозиторий)
    
    git push (отправляет контрольную точку в удаленный репозиторий)
    
    либо вместо master заменяют на main, как это делается есть на github
    
- Как работать с GitHub с разных компьютеров, gitignore, Git Kraken
    
    Если я работаю из дома и из офиса(работы) или если несколько человек работает над проектом и у меня 2 папки work and home, то
    
    я выхожу в терминале прописываю
    
    cd..
    
    cd work
    
    git clone [https://github.com/nik1999777/project.git](https://github.com/nik1999777/project.git) (путь из github) it project_2
    
    git pull (заходим в другую папку, прописываем и появляются все данные из другой папки)
    
      
    
    Если на удаленном репозитории были какие-то изменения, то всегда нужно прописывать git pull и может получится так, что в удаленном репозитории мы создали Readme.md, а в локальном только создали заголовок h3 и вот теперь 2
    
    проекта локальный и удаленный как бы сливаются (эта операция называется merge), и необходимо задать сообщение нашего commit и нажимаем Ctrl+C 2 раза, пишем :wq! и нажать Enter.
    
- Планировщик GULP. Что такое Node или Node.js.
    
    Gulp помогает автоматизировать большое количество рутинных задач, например компиляция sass кода
    
    Вот для этого и помогает планировщик задач Gulp, с его помощью можно все эти задачи описать, и потом одной терминальной командой запустить эти задачи, чтобы они запускались в автоматическом режиме и нас не беспокоили.
    
    Для того чтобы умело работать с Gulp нужно знать язык программирования JavaScript, так как Gulp настроен на его синтаксисе.
    
    **Node** или **Node.js** — программная платформа, основанная на движке [V8](https://ru.wikipedia.org/wiki/V8_%28%D0%B4%D0%B2%D0%B8%D0%B6%D0%BE%D0%BA_JavaScript%29) (транслирующем [JavaScript](https://ru.wikipedia.org/wiki/JavaScript) в [машинный код](https://ru.wikipedia.org/wiki/%D0%9C%D0%B0%D1%88%D0%B8%D0%BD%D0%BD%D1%8B%D0%B9_%D0%BA%D0%BE%D0%B4)), превращающая JavaScript из узкоспециализированного языка в язык общего назначения. Node.js добавляет возможность [JavaScript](https://ru.wikipedia.org/wiki/JavaScript) взаимодействовать с устройствами [ввода-вывода](https://ru.wikipedia.org/wiki/%D0%92%D0%B2%D0%BE%D0%B4-%D0%B2%D1%8B%D0%B2%D0%BE%D0%B4) через свой [API](https://ru.wikipedia.org/wiki/API) (написанный на [C++](https://ru.wikipedia.org/wiki/C%2B%2B)), подключать другие внешние библиотеки, написанные на разных языках, обеспечивая вызовы к ним из JavaScript-кода. Node.js применяется преимущественно на сервере, выполняя роль [веб-сервера](https://ru.wikipedia.org/wiki/%D0%92%D0%B5%D0%B1-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80), но есть возможность разрабатывать на Node.js и десктопные оконные приложения (при помощи [NW.js](https://ru.wikipedia.org/wiki/NW.js), AppJS или [Electron](https://ru.wikipedia.org/wiki/Electron) для [Linux](https://ru.wikipedia.org/wiki/Linux), [Windows](https://ru.wikipedia.org/wiki/Windows) и [macOS](https://ru.wikipedia.org/wiki/MacOS)) и даже программировать микроконтроллеры (например, tessel, low.js и espruino). В основе Node.js лежит [событийно-ориентированное](https://ru.wikipedia.org/wiki/%D0%A1%D0%BE%D0%B1%D1%8B%D1%82%D0%B8%D0%B9%D0%BD%D0%BE-%D0%BE%D1%80%D0%B8%D0%B5%D0%BD%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5) и [асинхронное (или реактивное)](https://ru.wikipedia.org/wiki/%D0%A0%D0%B5%D0%B0%D0%BA%D1%82%D0%B8%D0%B2%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5) программирование с [неблокирующим вводом/выводом](https://ru.wikipedia.org/wiki/%D0%9D%D0%B5%D0%B1%D0%BB%D0%BE%D0%BA%D0%B8%D1%80%D1%83%D1%8E%D1%89%D0%B0%D1%8F_%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F).
    
    Также у меня есть gulpfile и package.json и я каждый раз вставляю эти 2 файла в мой проект, и в терминале прописываю **npm i**
    
    Чтобы запустить сервер нужно прописать **gulp**, а чтобы остановить сервер нужно нажать комбинацию клавиш **Ctrl+C**
    
    Чтобы очистить историю в терминале нужно прописать **clear**
    
- Методология БЭМ
    
    БЭМ (Блок, Элемент, Модификатор) — компонентный подход к веб-разработке. В его основе лежит принцип разделения интерфейса на независимые блоки. Он позволяет легко и быстро разрабатывать интерфейсы любой сложности и повторно использовать существующий код, избегая «Copy-Paste».
    
- Формы на сайтах
    
    [http://htmlbook.ru/html/input/type](http://htmlbook.ru/html/input/type)   -  типы input
    
    [https://nisnom.com/category/veb-razrabotki/pereklyuchateli/](https://nisnom.com/category/veb-razrabotki/pereklyuchateli/)   -  кнопки на основе input
    
- Знакомство с JavaScript
    
    [**https://learn.javascript.ru/**](https://learn.javascript.ru/)    **-  ресурс для изучения JavaScript**
    
    ```JavaScript
    var name = "Nik";
    
    let number = 7;
    const pi = 3.14;
    
    number = 4;
    
    let leftBorderWidth;
    
    number 
    string - "",'',``
    true/false
    null
    undefined
    let obj = {
        name: 'apple',
        color: 'green';
        weight: 200
    }
    
    Symbol
    
    alert(1234)
    console.log(number)
    let answer = confirm("Вам есть 18?");
    console.log(answer);
    
    let answer = prompt("Вам есть 18?", "");
     console.log(answer);
    
    console.log(4+'fdd');
    
    let isChecked = false,
        isClose = false;
    
    console.log(isChecked && isClose);
    
    console.log(isChecked || isClose);
    
    if (2*6 == 8*1) {
        console.log('Верно')
    } else {
        console.log('Ошибка')
    }
    
    let answer = confirm("Вам есть 18?");
    if (answer) {
        console.log('Проходите')
    } else {
        console.log('Уходи')
    }
    
    const num = 50;
    
    if (num < 49) {
        console.log('Неправильно')
    } else if (num > 100) {
        console.log('Много')
    } else {
        console.log('Верно')
    }
    
    for(let i = 1; i < 8; i++) {
        console.log(i);
    }
    
    function logging(a, b) {
        console.log( a + b )
    }
    
    logging(3, 5);
    
    logging(6, 8);
    ```
    
- Практика. Создаем слайдер на сайте. Slick - слайдер
    
    [https://kenwheeler.github.io/slick/](https://kenwheeler.github.io/slick/) - Slick - слайдер со скриптами
    
    ```HTML
    <link rel="stylesheet" href="css/slick.css">
    
    <script type="text/javascript" src="//code.jquery.com/jquery-1.11.0.min.js"></script>
    <script type="text/javascript" src="//code.jquery.com/jquery-migrate-1.2.1.min.js"></script>
    <script src="js/slick.min.js"></script>
    <script src="js/script.js"></script>
    ```
    
    ```Scss
    .carousel {
        padding: 81px 0;
        &__inner {
            position: relative;
            width: 750px;
            margin: 0 auto; 
        }
        .slick-prev, .slick-next {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            left: -66px;
            border: none;
            background-color: \#fff;
            img {
                width: 30px;
                height: 50px;
            }
        }
    
        .slick-next {
            right: -66px;
            left: auto;
        }
    }
    ```
    
    ```JavaScript
    $(document).ready(function () {
        $('.carousel__inner').slick({
            speed: 300,
            // adaptiveHeight: true,
            prevArrow: '<button type="button" class="slick-prev"><img src="../icons/arrow_left.png"></button>',
            nextArrow: '<button type="button" class="slick-next"><img src="../icons/arrow_right.png"></button>',
            responsive: [
                {
                    breakpoint: 992,
                    settings: {                   
                        dots: true,
                        arrows: false
                    }
                }
            ]
        });
    });
    ```
    
- Альтернативные варианты слайдеров
    
    [https://owlcarousel2.github.io/OwlCarousel2/](https://owlcarousel2.github.io/OwlCarousel2/) -  другой сайт для создания слайдеров со скриптами
    
    [https://github.com/ganlanyuan/tiny-slider](https://github.com/ganlanyuan/tiny-slider)   -  tiny слайдер без скриптов
    
- Создание табов
    
    [https://getbootstrap.com/docs/4.3/components/navs/#javascript-behavior](https://getbootstrap.com/docs/4.3/components/navs/#javascript-behavior) - bootstrap табы
    
    [https://denis-creative.com/jquery-tabs/](https://denis-creative.com/jquery-tabs/) -  Простой jQuery-скрипт для табов (вкладок)
    
- Интерактивные карты на сайте
    
    [https://yandex.ru/map-constructor/](https://yandex.ru/map-constructor/) - конструктор яндекс карт
    
    [https://chrome.google.com/webstore/detail/touch-vpn-secure-and-unli/bihmplhobchoageeokmgbdihknkjbknd](https://chrome.google.com/webstore/detail/touch-vpn-secure-and-unli/bihmplhobchoageeokmgbdihknkjbknd)  - VPN плагин
    
    еще есть google карты
    
- Модальные окна на сайте
    
    [https://getbootstrap.com/docs/4.3/components/modal/](https://getbootstrap.com/docs/4.3/components/modal/) - модальное окно от bootstrap
    
    [https://dimsemenov.com/plugins/magnific-popup/documentation.html](https://dimsemenov.com/plugins/magnific-popup/documentation.html) - скрипт для модальных окон
    
    [http://jquery.page2page.ru/index.php5/%D0%97%D0%B0%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F_%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0](http://jquery.page2page.ru/index.php5/%D0%97%D0%B0%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F_%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0) - документация jquery
    
    [https://html5book.ru/specsimvoly-html/](https://html5book.ru/specsimvoly-html/) - спецсимволы HTML
    
- Валидация форм
    
    [https://jqueryvalidation.org/?__cf_chl_jschl_tk__=67ebce39d9ca9fb5ee25557fd6f9346f181b4f8a-1608855983-0-AbqJSww5VcMEhGnUKOmQvCcO1YLC2RgrK73v-EXbfNQbRuIOF5vMh4m6nX9jo7okfXJ1uTuYidY5XatkMjhgfQ5_rgvoYXfjwxwyq54bQLMykAQuI6-e_5Z_wiRu3ggaq4SXdQ9rTfCGLmzRxLaYRxYLkjmsHERr6Vx36d6ux07AJrdQ4Yqdy7MJb4IXl6QFM3LtOO4YWTR3qEE1VFMJjpWc1K7X1gbhHiGiZYCCrDD9aDz9eYuLKG7FPrAtjJFpZCN6ntWcbtzk8g5XALPBYiMGR-k9sX9IeLdZBuD-I8CR6_dx06LoNe-72-tWSweHUA](https://jqueryvalidation.org/?__cf_chl_jschl_tk__=67ebce39d9ca9fb5ee25557fd6f9346f181b4f8a-1608855983-0-AbqJSww5VcMEhGnUKOmQvCcO1YLC2RgrK73v-EXbfNQbRuIOF5vMh4m6nX9jo7okfXJ1uTuYidY5XatkMjhgfQ5_rgvoYXfjwxwyq54bQLMykAQuI6-e_5Z_wiRu3ggaq4SXdQ9rTfCGLmzRxLaYRxYLkjmsHERr6Vx36d6ux07AJrdQ4Yqdy7MJb4IXl6QFM3LtOO4YWTR3qEE1VFMJjpWc1K7X1gbhHiGiZYCCrDD9aDz9eYuLKG7FPrAtjJFpZCN6ntWcbtzk8g5XALPBYiMGR-k9sX9IeLdZBuD-I8CR6_dx06LoNe-72-tWSweHUA) - плагин для валидации форм
    
    **Валидация** — **это** проверка значений, указанных пользователем, и отображение найденных ошибок
    
- Маска ввода номера сайта
    
    [https://plugins.jquery.com/maskedinput/](https://plugins.jquery.com/maskedinput/)  -  плагин маска ввода номера
    
    +7 (910) 983 21 70 - эта маска
    
- Локальные сервера
    
    [https://ospanel.io/](https://ospanel.io/) - для windows
    
    [https://www.mamp.info/en/windows/](https://www.mamp.info/en/windows/) - для mac
    
    Чтобы мамр заработал нужно ввести в адресную строку [http://localhost:8888/Pulse/](http://localhost:8888/Pulse/)
    
- Отправка писем с сайта
    
    [https://github.com/PHPMailer/PHPMailer](https://github.com/PHPMailer/PHPMailer) -  PHP Mailer документация
    
    [mailer.zip](https://drive.google.com/file/d/11TSNGalwbGO6HnaWqmFOemLg7HKdE34y/view) - папка для скачачивания с PHP скриптом
    
- Плавный скролл по ссылкам и элементам вверх
    
    [http://history-of-blog.ru/verstka-sajtov/plavnaya-prokrutka-do-yakorya-na-jquery-luchshij-skript/](http://history-of-blog.ru/verstka-sajtov/plavnaya-prokrutka-do-yakorya-na-jquery-luchshij-skript/) - скрипт плавного скролла
    
- Анимация сайта при помощи CSS3
    
    [https://html5book.ru/css3-animation](https://html5book.ru/css3-animation) - Документация про анимацию на CSS3
    
- Библиотека для работы с анимациями
    
    [https://animate.style/#documentation](https://animate.style/#documentation) - библиотека анимаций css3
    
    [https://wowjs.uk/](https://wowjs.uk/)  -  документация для настройки анимации css3
    
- Валидация сайта
    
    **Валидация сайта** – проверка HTML-кода веб-ресурса на наличие ошибок и соответствие установленным стандартам. Проверка **валидации сайта** нужна, чтобы в будущем избежать критических ошибок и сбоев в его работе. Также она дает определенную уверенность в том, что адаптивность **сайта** находится на должном уровне.
    
    [https://validator.w3.org/](https://validator.w3.org/)   -    валидатор сайта
    
- Загрузка сайта на реальный хостинг. SSL и FTP
    
    **SSL** ([англ.](https://ru.wikipedia.org/wiki/%D0%90%D0%BD%D0%B3%D0%BB%D0%B8%D0%B9%D1%81%D0%BA%D0%B8%D0%B9_%D1%8F%D0%B7%D1%8B%D0%BA) _Secure Sockets Layer_ — уровень защищённых [сокетов](https://ru.wikipedia.org/wiki/%D0%A1%D0%BE%D0%BA%D0%B5%D1%82_%28%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%BD%D1%8B%D0%B9_%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D1%84%D0%B5%D0%B9%D1%81%29)) — [криптографический протокол](https://ru.wikipedia.org/wiki/%D0%9A%D1%80%D0%B8%D0%BF%D1%82%D0%BE%D0%B3%D1%80%D0%B0%D1%84%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B9_%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB), который подразумевает более безопасную связь. Он использует асимметричную криптографию для аутентификации ключей обмена, симметричное шифрование для сохранения конфиденциальности, коды аутентификации сообщений для целостности сообщений. Протокол широко использовался для обмена мгновенными сообщениями и передачи голоса через [IP](https://ru.wikipedia.org/wiki/IP) ([англ.](https://ru.wikipedia.org/wiki/%D0%90%D0%BD%D0%B3%D0%BB%D0%B8%D0%B9%D1%81%D0%BA%D0%B8%D0%B9_%D1%8F%D0%B7%D1%8B%D0%BA) _Voice over IP_ — [VoIP](https://ru.wikipedia.org/wiki/VoIP)) в таких приложениях, как [электронная почта](https://ru.wikipedia.org/wiki/%D0%AD%D0%BB%D0%B5%D0%BA%D1%82%D1%80%D0%BE%D0%BD%D0%BD%D0%B0%D1%8F_%D0%BF%D0%BE%D1%87%D1%82%D0%B0), интернет-факс и др. В 2014 году правительство США сообщило об уязвимости в текущей версии протокола[[1]](https://ru.wikipedia.org/wiki/SSL\#cite_note-1). SSL должен быть исключён из работы в пользу [TLS](https://ru.wikipedia.org/wiki/TLS) (см. CVE-2014-3566).
    
    **Хо́стинг** (англ. hosting) — услуга по предоставлению ресурсов для размещения информации на сервере, постоянно имеющем доступ к сети (обычно Интернет).
    
    **Доме́нное имя** — символьное имя, служащее для идентификации областей, которые являются единицами административной автономии в сети Интернет, в составе вышестоящей по иерархии такой области. Каждая из таких областей называется доме́ном
    
    **Домен** - это имя вашего сайта
    
      
    
    [**https://link-host.net/**](https://link-host.net/) **-** хостинг, который рекомендует Иван Петреченко
    
    [**https://hosting-ninja.ru/rating/linkhost/videouroki.html?video=7**](https://hosting-ninja.ru/rating/linkhost/videouroki.html?video=7) - про субдомены, как создать субдомены на link хосте
    
    [**https://hostenko.com/wpcafe/tutorials/wordpress-ssl-https/**](https://hostenko.com/wpcafe/tutorials/wordpress-ssl-https/)  -  статься про SSL сетрификат
    
      
    
    **FTP** является сокращением от англ. File Transfer Protocol — протокол передачи файлов, который применяется для обмена файлами по TCP/IP сетям между двумя компьютерами (клиент и сервер). Протоколу передачи файлов больше 40 лет, он был разработан прежде чем появился TCP/IP и тем более HTTP, однако он до сих пор актуален и используется для подключения к удаленным серверам и обмена файлами.
    
    Данный протокол применяет различные сетевые соединения для передачи команд и файлов между клиентом и сервером. FTP сервер, представляет собой компьютер с установленным на него специальным программным обеспечением и ожидающим внешнего подключения от других компьютеров.
    
    **FTP клиент** является программой, которая делает попытку соединится с серверным компьютером, как правило к порту номер 21. После успешного подключения к FTP серверу, можно совершать всевозможные операции над данными располагающимися на нем, в частности, просмотреть содержимое каталогов, загружать и скачивать файлы с FTP сервера, переименовывать, назначать права доступа, удалять файлы с сервера и прочее.
    
    Соединяясь с FTP сервером допустимо пройти авторизацию предоставляя данные для входа без использования шифрования, а также можно подключиться анонимно, если это позволяет FTP сервер. Для защищенной передачи, которая скрывает (шифрует) логин, пароль и данные, FTP соединение может быть зашифровано при помощи SSL/TLS (FTPS). SSH протокол передачи файлов (SFTP) иногда также используется, но между ним и FTPS есть существенная разница.
    
    Основное назначение FTP протокола - это загрузка файлов и их скачивание с удаленного сервера. Для передачи файлов в пассивном режиме инициируется соединение FTP клиентом из обусловленного диапазона портов к порту сервера. В активном режиме FTP сервер подключается к клиенту из порта 20 к определенному порту, который сообщил ему клиент. Основное различие между данными режимами, состоит в том, с какой стороны открывается соединение для передачи файлов.
    
    Для эффективной работы с FTP мы рекомендуем воспользоваться FTP менеджером **FileZilla**. Программа отлично подойдет как для новичков, так и для опытных пользователей. Легкость освоения, кроссплатформенность, множество поддерживаемых языков, большое количество настроек и возможностей делают ее одной из лучших FTP клиентов.
    
- Оптимизация скорости загрузки сайта. Доработки gulpfile
    
    [https://developers.google.com/speed/pagespeed/insights/](https://developers.google.com/speed/pagespeed/insights/)  -  Google PageSpeed - узнайте, как ускорить загрузку своего сайта на любых устройствах.
    
    [https://imagecompressor.com/ru/](https://imagecompressor.com/ru/) -  optimizilla - Этот **оптимизатор изображений** использует эффективную комбинацию лучших алгоритмов сжатия с потерями/без потерь для уменьшения размера изображений в форматах JPEG и PNG до минимально возможного уровня.
    
    [https://tinypng.com/](https://tinypng.com/) - еще один вариант для сжатия изображений
    
    **Кросс-браузерность** — свойство веб-сайта отображаться и функционировать во всех часто используемых браузерах идентично. Под идентичностью функционирования подразумевается: отсутствие некорректной работы, ошибок в вёрстке и способность отображать материал с одинаковой степенью читабельности.
    
    Абсолютно одинаковый сайт может абсолютно по разному отображаться в разных браузерах.
    
    **Кроссплатформенность** — **это** способность **сайта** полноценно работать на всех устройствах и операционных системах, которые использует посетитель.
    
    [https://www.browserstack.com/](https://www.browserstack.com/) - Переведено с английского языка.-BrowserStack - это облачная платформа для веб-тестирования и тестирования мобильных устройств, которая предоставляет разработчикам возможность тестировать свои веб-сайты и мобильные приложения в браузерах, операционных системах и реальных мобильных устройствах
    
    [https://www.npmjs.com/package/gulp-imagemin](https://www.npmjs.com/package/gulp-imagemin) - gulp-imagemin - для того, чтобы отпимизировать все изображения
    
    [https://www.npmjs.com/package/gulp-htmlmin](https://www.npmjs.com/package/gulp-htmlmin) - gulp-htmlmin - для того, чтобы сжать html файл
    
    [https://www.virtualbox.org/](https://www.virtualbox.org/) - для установки виртуальной машины
    
    [https://github.com/andreyalexeich/gulp-scss-starter](https://github.com/andreyalexeich/gulp-scss-starter)  - для быстрого старта проектов