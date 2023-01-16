Объемы работ и очень краткое изложение принципов по [прикладному программированию](https://en.wikipedia.org/wiki/Application_software) :slightly_smiling_face: на [**C++**](https://en.wikipedia.org/wiki/C%2B%2B), [**Tcl/Tk**](https://en.wikipedia.org/wiki/Tcl), [**Python**](https://en.wikipedia.org/wiki/Python_(programming_language)) для [централизованных](https://en.wikipedia.org/wiki/Centralized_computing) и [распределенных](https://en.wikipedia.org/wiki/Distributed_computing) вычислений на [Windows Server](https://en.wikipedia.org/wiki/Windows_Server "Многих она не устраивает, но на сегодняшний момент из имеющихся в наличии это самая лучшая ОС. Если нужно что-то другое, то тогда пора изобрести что-то действительно принципиально новое. По-моему уже хватит мучить Linux-ы и тем более BSD . Прикладные пакеты на Linux (Debian-ы и RedHat-совместимые) делают индийские и бразильские студенты. Аппаратные сбои в электронике Linux просто не видит или не определяется их источники. Согласно сплетням еще в 2007-м году разработчики из NetBSD и из OpenBSD перебежали в M$ и в Google"), а также для [децентрализованных](https://en.wikipedia.org/wiki/Decentralized_computing) вычислений на [клиентской Windows](https://en.wikipedia.org/wiki/Microsoft_Windows):

1. Прототипирование и архитектурные решения

В принципе практически все наработки являются прототипами и склоняются к циклу **"Анализ - Дизайн - Разработка - Тестирование - Эксплуатация - Анализ"** (см. [русскоязычную адаптацию](http://sewiki.ru/Systems_Engineering_Thinking_Wiki:%D0%9E%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5) с легким уклоном в [гностику](https://en.wikipedia.org/wiki/Gnosticism)), поэтому для поддержания актуальности требуют [постоянного совершенствования](https://en.wikipedia.org/wiki/CI/CD).

Для задачи попроще вполне подходит скрипт, работающий в командной строке с ключами и с путями, посложнее - [Интерактивная текстовая или графическая оболочка](https://en.wikipedia.org/wiki/User_interface_design). Если требуется что-то явить миру, поверх серверной или отдельной клиентской компоненты подымается ВЭБ-сайт (выполняется отдельно, в объем данных репозиториев может входить в виде подмодуля как внешняя разработка). [💬](https://www.codeproject.com/Articles/5283291/Examples-of-Layered-Application-Architecture-Based "Первая статья (устаревшая, но в целом правильная точка зрения)") [💬](https://www.codeproject.com/Articles/5317447/Layered-Application-Architecture-with-a-Homogeneou "Вторая статья того же автора")

2. Расчеты и математическое моделирование

С появлением вычислительной техники в 1990-х многие эмпирические методы в прикладной математике с номограммами потеряли свою практическую пользу. Стало возможно посчитать аналитические формулы напрямую, используя конечно-разностные формы их записи. Посчитали различные задачи оптимизации, которые ждали своего решения еще с 1960-х годов. Для удобства восприятия решение как правило стремились получить в виде экстремума градиента на поверхности или на облаке точек, подбирая диапазоны итерации вручную или более осторожно методом последовательного приближения.

3. Разработка и администрирование баз данных **MS SQL Server**-а в части **[SQL](https://en.wikipedia.org/wiki/SQL) + [XML](https://en.wikipedia.org/wiki/XML)** [💬](http://www.chernyshov.com/SPPO_6/theory/wt_xml.htm "Его описание") ([XPath](https://en.wikipedia.org/wiki/XPath) & [XQuery](https://en.wikipedia.org/wiki/XQuery), [XSD](https://en.wikipedia.org/wiki/XML_Schema_(W3C)) [💬](https://bdpx.github.io/xml/lab3/xsd.html "Его описание")). А также анализ структур и баз данных с помощью [EXPath](http://expath.org/), [XSL](https://en.wikipedia.org/wiki/XSL), [XSLT](https://en.wikipedia.org/wiki/XSLT), [EXSLT](https://en.wikipedia.org/wiki/EXSLT), [Relax NG](https://en.wikipedia.org/wiki/RELAX_NG), [XSpec](https://github.com/expath/xspec/tree/master), [XLink](https://en.wikipedia.org/wiki/XLink), [XMark](https://projects.cwi.nl/xmark/index.html), [XInclude](https://www.w3.org/TR/xinclude/), [XProc](https://en.wikipedia.org/wiki/XProc), [OPML](https://en.wikipedia.org/wiki/OPML), [XQL](http://www.ibiblio.org/xql/xql-proposal.html)

**SQL** и **XML** по отдельности имеют много разной критики, но по полноте функционала замены им пока не наблюдается. Есть определенные ограничения в преобразовании типов данных по цепочке `Python <-> SQL <-> XML`, так как типы данных SQL и типы данных из пространств имен [XDM](https://en.wikipedia.org/wiki/XQuery_and_XPath_Data_Model) аскетичнее и не перекрываются полностью. Есть сложности в возврате результата работы (кода возврата) функции (хранимой процедуры) `XPath & XQuery -> SQL -> Python`. Это важный момент, так как если ничего не предпринять дополнительно, то SQL Server при возрастании нагрузки не собирает запросы от прикладной программы в очередь, а откидывает их в том числе по взаимоблокировке и недогружается. Разрабатывается собственный [функционал](https://docs.sqlalchemy.org/en/14/dialects/mssql.html#module-sqlalchemy.dialects.mssql.pyodbc) Python-а для работы с SQL Server-ом, но нет плагина или интеграции [Saxon](https://www.saxonica.com/about/about.xml)-а, [Schematron](https://en.wikipedia.org/wiki/Schematron)-а и возможностей [BaseX](https://en.wikipedia.org/wiki/BaseX) внутри ядра баз данных. Таким образом для достижения красоты и гармонии в прикладном программировании усилий разработчиков мало. Требуется также прогресс в развитии ядра баз данных SQL Server-а.

Много разрозненных наработок, использующих возможности только **XML** для работы с данными недоведены, устарели и стали историей.

[**Объектно-ориентированные базы данных**](https://en.wikipedia.org/wiki/Object_database) в виде составных и пользовательских типов данных с неограниченной гибкостью как продолжение темы [**объектно-ориентированного программирования (сокращенно ООП)**](https://en.wikipedia.org/wiki/Object-oriented_programming), начиная со списков и словарей с их срезами, [DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html)-ы как главный козырь [Pandas](https://en.wikipedia.org/wiki/Pandas_(software)) и заканчивая классами с их композицией и наследованием, к которым подводят мысль во многих книгах, пока к сожалению не обрели своих СУБД и используются в университетской среде насколько позволяет оперативная память операционной системы и только в однопользовательском режиме.

[**не-SQL-ные СУБД**](https://en.wikipedia.org/wiki/NoSQL "Есть мнение в разных источниках, что они быстрее SQL-ных баз") :thought_balloon: (https://aws.amazon.com/ru/nosql "Статья на Amazon-е"), числу которых сейчас нет счета, по сравнению с **SQL-ными** имеют столько преимуществ сколько и неудобств. Какая-то одна в чем-то лучше и в чем-то хуже какой-то другой. Большинство из них в разных модификациях являются продолжением темы [JSON](https://en.wikipedia.org/wiki/JSON) + двоичные поля и [BLOB](https://en.wikipedia.org/wiki/Binary_large_object)-ы. Кстати, могли бы сразу за основу взять [YAML](https://en.wikipedia.org/wiki/YAML). Но видимо разработчики - сторонники JavaScript-а. Не заменят XML, так как есть принципиальное отличие:
 - `*.xml` - ветвление, топология, структура,
 - `*.dat, *.ini, *.json, *.yaml` - словарь, конфигурация, настройка.

![007 001 001](https://user-images.githubusercontent.com/104857185/209877366-3c1a9309-736c-49ce-9bb3-709e16110020.jpg)

Есть коммерческие платформы для работы с данными непонятно на чем, например [MarkLogic](https://www.marklogic.com/), но они сами в себе

4. Замена бумажного и электронного документооборота, а также замена коммерческих консультантов :dollar: :pound: :euro:

Руководящие документы (Руководства, Нормативы, Стандарты, Приказы, Инструкции) необходимо перестать распечатывать на бумаге, а также гонять их копии разной давности с ЭЦП и без по электронной почте, ватсапам, телегам и соцсетям. Необходимо дать доступ к ним только из единственного авторитетного источника не в виде художественного текста, а в виде чистого императива, который может определенно и однозначно восприниматься прикладными программами для принятия решений и возврата отчетов о выполнении. Для этого их вероятно потребуется **переосмыслить**, перенеся повествовательную часть в комментарии, и **продумать их структуру ветвления** с данными, параметрами и ссылками на другие источники в зависимости от типа документа и его отрасли, затем **сохранить в формате XML**, чтобы упорядоченно **записать в поля** `XML(CONTENT dbo.XSD-схема)` таблиц баз данных и **парсить** как [DOM](https://ru.wikipedia.org/wiki/Document_Object_Model) или [SAX](https://en.wikipedia.org/wiki/Simple_API_for_XML) запросами на XPath & XQuery **вручную** или **программно** в прикладных задачах :hibiscus: :four_leaf_clover:

![1 001 001](https://user-images.githubusercontent.com/104857185/167037090-9cd548c0-9643-4903-adce-13e2a039226d.jpg)

Таким образом документы и вносимые в них изменения смогут быстро и просто исполняться без перечитывания их текста, без сравнения с предыдущими редакциями и без трактования их разными людьми в разных контекстах и ситуациях.

5. API-шки сопряжения с автоматикой смежных систем

[API-шки](https://en.wikipedia.org/wiki/API) в широком понимании модели [Клиент - Сервер](https://en.wikipedia.org/wiki/Client%E2%80%93server_model) локально или по сети применяются для облегчения внесения изменений и для обеспечения единообразия в повторном применении исходных текстов <span style="color:green">`(функции, интерфейсы, статические и динамические библиотеки)`</span> на всех клиентах в обращениях к службам, предоставляемым серверными компонентами в [Сервисном слое](https://en.wikipedia.org/wiki/Service_layer), который сопоставляется с прикладным слоем в [Модели OSI](https://en.wikipedia.org/wiki/OSI_model), а точнее располагается в 3-й уровне абстракции [ее 8-ого надслоя](https://en.wikipedia.org/wiki/Layer_8) в разной степени гибкости [Сервис-ориентированной архитектуры](https://en.wikipedia.org/wiki/Service-oriented_architecture) и который пока относят к стороннему (часто закрытому) программному обеспечению, дописанному дополнительно к общеизвестным прикладным протоколам :slightly_smiling_face: Этот слой в полном варианте состоит из пары - сервер состояний <span style="color:Orange">(в идеале внешний сервер СУБД)</span> и сервер сообщений о событиях <span style="color:Orange">(например OPC-сервер)</span> :slightly_smiling_face:

![009 001](https://user-images.githubusercontent.com/104857185/211207093-d0c7b9b9-5594-4dcd-a3e3-b7f81757ff6f.jpg)

Фирмы-изготовители оборудования и программного обеспечения для работы с ним, к которому они не прилагают исчерпывающее описание состояний и событий, свои DDK и SDK, а также и исходные тексты **для написания прикладных API-шек с нуля или поверх комплектных от фирмы-изготовителя**, в эту идею к сожалению не вписываются, так как этим исключают интеграцию с ними прикладных задач 🤔 Они закрываются, применяя сертификаты, программные и аппаратные ключи, смарт-лицензии и активацию по сети, а к широкому сообществу обращаются лишь раз от разу при потребности в свежих идеях, которых это сообщество без глубокого вовлечения вероятно дает недостаточно. Они чрезмерно увлеклись переносом функционала на [Облака](https://en.wikipedia.org/wiki/Cloud_computing), увеличивая вероятность отказов при разрывах соединения с первичным оборудованием 🤔 Таким образом, без проникновения концепции [Open Source](https://en.wikipedia.org/wiki/Open_source) технический прогресс в этой отрасли смещается в сторону налаживания межоблачного взаимодействия и наблюдается замедление в развитии программной части для первичного оборудования (прошивки, операционные системы, языки программирования, конфигураторы) и соответственно самого первичного оборудования :confused: Ситуация вынуждает опытных разработчиков искать простора для полета их творческой мысли в стартапах на более мелких задачах :unamused: Требуется политическое решение