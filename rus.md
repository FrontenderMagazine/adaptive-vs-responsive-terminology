# Адаптивно-отзывчивый: разбираемся в терминологии

Анонс [веб-сайта][1], позволяющего сравнить
на примере простой страницы фиксированный, резиновый, адаптивный и отзывчивый
типы макетов, вызвал большой резонанс в веб-сообществе. Несмотря на то,
сколько всего уже было сказано об отзывчивом и адаптивном веб-дизайне,
энтропия непонимания принципиальной разницы подходов в веб-разработке имеющих
подобные названия только возрастает.

Я постараюсь разложить все по полочкам и объяснить принципиальную разницу
между типами макетов и подходами к веб-разработке.

## Типы HTML-макетов

Под макетом в данной статье подразумевается не изображение в формате PSD, а
уже готовая разметка HTML-страницы.

### Фиксированные макеты

> px

Фиксированный макет — макет страницы, ширина контента которой жестко задана в
пикселях и не меняется в зависимости от размеров окна браузера.

Фиксированная верстка является пережитком прошлого, когда ширина контента
страницы была строго продиктована разрешением самых популярных экранов (800 на
600, затем 1024 на 768 и так далее). Даже сейчас еще легко можно встретить
сайты с фиксированной шириной контента в 960 пикселей.

![Иллюстрация][Фиксированный макет]

### Резиновые макеты

> %

Резиновый тип макетов еще называют тянущимся (дословно с английского "жидкие",
*liquid*, жидкость), так как контент принимает размер любого экрана за счет
использования для структурных элементов относительных показателей (зачастую,
процентных) вместо статических, в пикселях.

Данный тип макетов в чистом виде также является устаревшим, так как учитывает
только один тип устройств и не заботится о том, как контент будет выглядеть на
экранах с критически большой или маленькой шириной.

![Иллюстрация][Резиновый макет]

### Адаптивные макеты

> px + media-queries

Адаптивный макет является очень близким к следующему типу — отзывчивому и
базируется на использовании медиа запросов (англ. media queries) для адаптации
контента под различные параметры экранов.

Главное отличие от отзывчивого типа состоит в том, что при данном типе верстки
страница «прыгает» по контрольным точкам, смещаясь и адаптируя контент каждый
раз к наиближайшей следующей из них. То есть медиа-запросы описывают
фиксированные положения контента для каждой из контрольных точек. В итоге мы
имеем набор из нескольких фиксированных макетов для работы с различными
разрешениями экранов.

Минус такого подхода к верстке страниц очевиден — мы не можем предугадать как
будет выглядеть контент на всех устройствах, учитывая что расстояния между
контрольными точками могут быть достаточно большими.

Данный подход наиболее актуален, если критические точки описывают не ширину
наиболее часто встречающихся устройств, а обусловлены дизайном самой страницы.

![Иллюстрация][Адаптивный макет]

### Отзывчивые макеты

> % + media-queries

Отзывчивый тип макетов страниц в отличие от адаптивного основывается на
принципе «резины», но так же как и он используют медиа запросы для
приспособления контента под ширину устройства.

В итоге, отзывчивая страница не «прыгает» по контрольным точкам, а плавно
изменяется между ними.

![Иллюстрация][Отзывчивый макет]

### Смешанный

> px + % + media-queries

Не стоит отрицать, что существуют и иные решения для создания макетов.

Например  адаптация под различные устройства может быть чем-то между
адаптивной и отзывчивой версткой страниц. Данная ситуация довольно часто
встречается как попытка оптимизации уже существующего сайта под различные типы
устройств («mobile last»).

## Подходы к созданию веб-сайтов и веб-приложений

Сейчас мы посмотрим на подходы и стратегии разработки веб-сайтов. Это нечто
большее, чем способ верстки страницы, так как зачастую включает в себя и
решение проблем на уровне пользовательского взаимодействия, реструктуризации
страницы или даже адаптации предоставляемого пользователю контента.

### Отзывчивый веб-дизайн

> % + media-queries + %-media

**Отзывчивый веб-дизайн** был описан впервые [в статье на A List Apart][2].
Название подхода взято по примеру [отзывчивой архитектуры][3], области
архитектурной практики и исследований. Отзывчивая архитектура здания
предполагает адаптацию самого строения (формы, цвета) в зависимости от
состояния окружающей среды.

В 2011 Маркотте опубликовал одноименную книгу, в которой он собрал в единую
технику некоторые давно известные приемы адаптации контента.

Этан не изобрел ничего нового на тот момент, а просто систематизировал знания
и предложил решения проблем для старых устройств и браузеров. Но это и было
действительно то, что нужно, во время множества ОС, устройств и браузеров.

Подход основывается на резиновых макетах, медиа запросах и отзывчивых
(«резиновых») медиа-элементах (изображения, видео).

Следовательно *отзывчивый макет страницы плюс использование отзывчивых
изображений и видео*.

Заметим  что техника отзывчивого веб-дизайна использует только средства HTML и
CSS для решения задачи адаптации контента под различные устройства.

### Адаптивный веб-дизайн

> % + media-queries + %-media + JavaScript + magic

Прежде чем ознакомиться с такой стратегией в разработке, как адаптивный веб-дизайн,
стоит немножечко поговорить о других стратегиях, концепциях и
техниках, на которых базируется данный подход. А именно, "сначала мобильные" и
"прогрессивное улучшение".

Прогрессивное улучшение — это стратегия веб-разработки, которая основывается
на доступности контента и семантике на самом низком уровне, а остальные же
уровни, такие как стилизация (CSS) и дополнительные скрипты (JavaScript), —
лишь дополнения, которые делают жизнь проще. Стратегия была представлена в
2003 году на знаменитой конференции [SXSW][4] Стивеном Чампионом. В отличие
от концепции [постепенной деградации][5], когда разработчики ориентируются только на
современные браузеры и "урезают" возможности для более старых, прогрессивное
улучшение идет с обратной стороны, делая контент доступным для наибольшего
количества устройств и браузеров. Так как эта проблема в наше время стоит
довольно серьезно, данная стратегия даже была названа [Top #1 трендом в веб-дизайне на 2012-й год][6].

В уже далеком 2011-ом [Люк Вроблевски][7] с помощью «[A Book Apart][8]»
выпустил книгу под названием «[Mobile First][9]», которая, как и
многие книги этого издателя, быстро стала бестселлером. Несложно догадаться,
что книга освящает стратегию, которая предполагает, что вся разработка от
планирования бизнес-целей, UX и веб-дизайна до последней строчки кода будет
вестись начиная от самой компактной «мобильной версии» до настольных
компьютеров, приставок или телевизоров.

**Адаптивный веб-дизайн** как подход был описан в [одноименной книге][10] Аарона
Густафсона. Подход берет лучшее из идей «сначала мобильные» и прогрессивного
улучшения и дополняет их. В простом изложении данная стратегия предполагает
использование чистого HTML как базиса и дальнейших улучшений и фич за счет
использования слоев CSS и JavaScript. Если для какого-то определенного
браузера или устройства доступна какая-то новая фича, то ее можно использовать
только после проверки на ее доступность, сохраняя обратную совместимость с не
поддерживающими устройствами (например, тач-события).

> *«Чистый HTML работает везде.»*<br>
> — Кто-то на какой-то конференции

В последнее время довольно занятным является спор об адаптации
предоставляемого контента как такового под различные устройства и их
возможности. Несомненно, имеет место существовать предположение, что если я
захожу на сайт с какого-нибудь древнего телефона, то, скорее всего, все, что я
хочу отыскать — это адрес и телефонный номер организации, если со смарт тв —
то почитать новости или посмотреть видео-ролики, что еще более вероятно.
Данную гибкость в предоставляемом пользователю контенте в некоторой мере также
можно отнести к стратегии адаптивного веб-дизайна. Но не стоит забывать, что
пользователи — это городские сумасшедшие с соседнего подъезда и зачастую
нельзя предугадать ситуацию, в которой находится пользователь в данный момент
времени, основываясь на устройстве, наборе его характеристик и поддерживаемых
фич, или даже скорости соединения.

Стоит также отметить, что адаптивный веб-дизайн — это стратегия разработки
веб-сайтов и веб-приложений, в то время, когда отзывчивый веб-дизайн является
техникой адаптации макета под различные устройства; зачастую, составной частью
адаптивного веб-дизайна.

## И в заключение

> *«Вы мне это прекратите!»*<br>
> — Братья Стругацкие, «Понедельник начинается в субботу» (1965)

Ничего нового придумано не было. Прогрессивное улучшение как подход
существовал с 2002. Резиновые макеты и медиа-запросы еще старше (первый
черновик был опубликован еще в [апреле 2001-го][11]!). Проблема
оптимизации под различные устройства и платформы встала наиболее остро с
развитием смартфонов (и возможности открывать обычные веб-страницы на
различного рода устройствах), а в последствии и планшетных компьютеров и
других устройств, таких как Smart TV или игровых консолей. Но ускорение
развития и разработки веб-стандартов, а так же  систематизация подходов к
веб-разработке позволило ее  в некотором смысле решить.

В наше время довольно остро стоит вопрос с терминологией и ее пониманием в
сообществе веб-разработчиков. Такая тенденция появилась неспроста и
наблюдается не только на пост-советском пространстве, но и во всем мире
(проверить достаточно просто — запросить в Google «adaptive vs. responsive web
design» и посмотреть разнообразие в понимании терминологии в различных
постах).

Еще одним ярким примером такого недопонимания является [недавний пост][12]
русского дизайнера [Ильи Бирмана][13].

## Материалы для дальнейшего чтения

* [3 articles that discuss the differences between "responsive" and "adaptive" web design][14]
* [What’s the difference between adaptive and responsive web design?][15]
* [Responsive Web Design][16]
* [Резиновый дизайн, респонсив и адаптив][17]

[1]: http://liquidapsive.com/
[2]: http://alistapart.com/article/responsive-web-design
[3]: http://en.wikipedia.org/wiki/Responsive_architecture
[4]: http://en.wikipedia.org/wiki/South_by_Southwest
[5]: http://en.wikipedia.org/wiki/Fault-tolerant_system
[6]: http://www.netmagazine.com/features/15-top-web-design-and-development-trends-2012
[7]: http://www.lukew.com/about/
[8]: http://www.abookapart.com/
[9]: http://www.abookapart.com/products/mobile-first
[10]: http://easy-readers.net/books/adaptive-web-design/
[11]: http://www.w3.org/standards/history/css3-mediaqueries
[12]: http://ilyabirman.ru/meanwhile/all/responsive/
[13]: http://ilyabirman.ru/
[14]: https://plus.google.com/103751101313992876152/posts/ezi7gr6T1kR
[15]: http://www.digitalfamily.com/tutorials/css-article/whats-the-difference-between-adaptive-and-responsive-web-design/
[16]: http://alistapart.com/article/responsive-web-design
[17]: http://ilyabirman.ru/meanwhile/all/responsive/

[Фиксированный макет]: img/fixed-static-layout.png "Фиксированный макет"
[Резиновый макет]: img/liquid-layout.png "Резиновый макет"
[Адаптивный макет]: img/adaptive-layout.png "Адаптивный макет"
[Отзывчивый макет]: img/responsive-layout.png "Отзывчивый макет"
