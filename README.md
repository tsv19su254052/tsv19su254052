Тарасов Сергей Владимирович
----------------------------
Объемы работ и очень краткое изложение принципов по [прикладному программированию](https://en.wikipedia.org/wiki/Application_software) :slightly_smiling_face: на [**C++**](https://en.wikipedia.org/wiki/C%2B%2B), [**Tcl/Tk**](https://en.wikipedia.org/wiki/Tcl), [**Python**](https://en.wikipedia.org/wiki/Python_(programming_language)) для [централизованных](https://en.wikipedia.org/wiki/Centralized_computing) и [распределенных](https://en.wikipedia.org/wiki/Distributed_computing) вычислений на [Windows Server](https://en.wikipedia.org/wiki/Windows_Server "Многих она не устраивает, но на сегодняшний момент из имеющихся в наличии это самая лучшая ОС. Если нужно что-то другое, то тогда пора изобрести что-то действительно принципиально новое. По-моему уже хватит мучить Linux-ы и тем более BSD . Прикладные пакеты на Linux (Debian-ы и RedHat-совместимые) делают индийские и бразильские студенты. Аппаратные сбои в электронике Linux просто не видит или не определяется их источники. Согласно сплетням еще в 2007-м году разработчики из NetBSD и из OpenBSD перебежали в M$"), а также для [децентрализованных](https://en.wikipedia.org/wiki/Decentralized_computing) вычислений на [клиентской Windows](https://en.wikipedia.org/wiki/Microsoft_Windows):

Язык [C++](https://isocpp.org/ "Перешел на него после Fortran-а в 1993-м году") еще в ходу и в настоящее время в основном используется для написания операционных систем, драйверов и коммерческого программного обеспечения и в источниках уже не упоминается как язык высокого уровня.

Язык [Tcl](https://www.tcl.tk/about/language.html "Делал некоторые графические оболочки с помощью среды разработки tkBuilder") (имеет возможности примерно как у [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language)) и [Basic](https://en.wikipedia.org/wiki/BASIC)) изначально был задуман для системных задач и хорошо применялся на [ORACLE Solaris](https://en.wikipedia.org/wiki/Oracle_Solaris), в конце 1990-х также применятся для написания скриптов-обработчиков виджетов на графических оболочках внутри например среды разработки [tkBuilder](https://sourceforge.net/projects/tkbuilder84/) и [Komodo](https://www.activestate.com/products/komodo-ide/).

Язык [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Начал изучать его вместе с Python-ом и вскоре понял, что Python значительно лучше и полностью перешел на него") по-тихому уходит в прошлое. Проект на нем - как правило вязанка папок с файлами, в том числе jar-иками. Сразу не сообразишь, где точка входа на исполнение и все остальное. В основном допиливают и перепиливают наработки начала 2000-х, когда он перехватил инициативу и хорошо вписался в ВЭБ-разработку. Его поддержка на разных уровнях устаревает и засыхает.

Язык [R](https://en.wikipedia.org/wiki/R_(programming_language) "Пробовал его для расчетов данных с SQL Server-а") - простенький предметно-ориентированный язык с бедным набором типов данных, рассчитанный на математиков и экономистов. В [Data Science](https://en.wikipedia.org/wiki/Data_science) с разным успехом применяют богатые возможности [DataFrame](https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/data.frame)-ов для импорта моментальных снимков баз данных и анализа их срезов, но перегонять снимок в память - это очень круто даже для их серверов. Есть особенность - все числовые переменные векторные, поэтому операции над ними работают не по правилам арифметики, а по правилам действий с векторами и матрицами. Графических приложений на нем не предвидится. Есть скрипты, которые можно исполнять на голом интерпретаторе или внутри среды разработки [R Studio](https://en.wikipedia.org/wiki/RStudio "Еще сырая. Если зависает скрипт или одна вкладка, то виснет все. Если кодировка не ASCII и не win-1251, то лепит краказябру. В кадре терминала черным и красным шрифтом вываливает все, что надо и не надо. При занятости сервера СУБД его драйвер ждет несколько секунд и сбрасывает соединение. Для сравнения драйвер Python-а ждет часами и сутками"). Документации много, есть много видео на YouTube, но примеров мало.

Язык [Python](https://www.python.org/ "Есть сомнительное с моей точки зрения мнение, что в математических расчетах он медленнее C++, но не прилагаются результаты замеров. Кстати, когда делал прикладные программы на C++, то в журналах были горы ошибок и предупреждений, на Python-е - там пусто. Установленные интерпретаторы и библиотеки по отдельности лучше не обновлять - возможны глюки. Виртуальное окружение (интерпретатор и библиотеки указанных в файле `requirements.txt` версий) во многопользовательской системе - временная вынужденная мера, от которой надо уйти, потому что пользователям на клиентах дается ярлык (символическая или мягкая ссылка) на скрипт с файлового сервера, ставится интерпретатор, ставятся используемые с ним библиотеки, но раздавать или делать дубликаты виртуального окружения разработчика со всеми переделками всем клиентам как-то не по фэншую") имеет необъятные возможности благодаря богатству типов данных и разработанным под него библиотекам и теперь надежно доминирует. Имеет приятную особенность - меньше использует операционную систему как **C++** и больше работает в профиле пользователя. Фрэймворки [Tk, Ttk и Ttk+](https://en.wikipedia.org/wiki/Tk_(software)) в виде комплектной библиотеки [tkinter](https://en.wikipedia.org/wiki/Tkinter), которые использовались еще на [twm](https://en.wikipedia.org/wiki/Twm) и имеют по нынешним временам [ограниченные возможности](https://gitlab.freedesktop.org/xorg/app/twm "Очень интересная страница разработчика") для творчества. Фрэймворк [pySimpleGUI](https://www.pysimplegui.org/en/latest/) прост, интересен, имеет наборы стилей, внешне напоминает ВЭБ-разработку, но на нем мало примеров. Фрэймворки [Gtk и Gtk+](https://en.wikipedia.org/wiki/GTK) используются в Linux-е и в настоящее время имеют ошибки (библиотека pyGTK на Windows пока не ставится). Фрэймворк [wxPython](https://en.wikipedia.org/wiki/WxPython) неправильно отображает кодировки и не пропорцинально отображает виждеты в разных сочетаниях. Самый лучший и ходовой фрэймворк - это [pyQt](https://en.wikipedia.org/wiki/Qt_(software)), в котором имеется комплектный [QtDesigner](https://doc.qt.io/qt-6/qtdesigner-manual.html) для рисования макетов и записи их отдельными ресурсными файлами. Среда разработки [pyCharm](https://en.wikipedia.org/wiki/PyCharm) просто идеальна.

Для простой прикладной задачи вполне подходит скрипт, работающий в командной строке с ключами и с путями. Для одновременного обозревания нескольких параметров в прикладной задаче разрабатывается и применяется графическая оболочка (окно с диалогами или диалог с диалогами). Интерактивная текстовая оболочка - уже раритет. Если требуется что-то явить миру, поверх серверной или отдельной клиентской компоненты подымается ВЭБ-сайт (выполняется отдельно, в объем данных репозиториев может входить в виде подмодуля как внешняя разработка).

 - Прототипирование

В принципе практически все наработки являются прототипами и склоняются к циклу **"Анализ - Дизайн - Разработка - Тестирование - Эксплуатация - Анализ"**, поэтому для поддержания актуальности требуют постоянного совершенствования (`UX/UI` и `CI/CD`).

 - Расчеты и математическое моделирование

С появлением вычислительной техники в 1990-х многие эмпирические методы в прикладной математике с номограммами потеряли свою практическую пользу. Стало возможно посчитать аналитические формулы напрямую, используя конечно-разностные формы их записи. Посчитали различные задачи оптимизации, которые ждали своего решения еще с 1960-х годов. Для удобства восприятия решение как правило стремились получить в виде экстремума градиента на поверхности или на облаке точек, подбирая диапазоны итерации вручную или более осторожно методом последовательного приближения.

- Разработка и администрирование баз данных **MS SQL Server**-а в части **[SQL](https://en.wikipedia.org/wiki/SQL) + [XML](https://en.wikipedia.org/wiki/XML)** [описание](http://www.chernyshov.com/SPPO_6/theory/wt_xml.htm) ([XPath](https://en.wikipedia.org/wiki/XPath) & [XQuery](https://en.wikipedia.org/wiki/XQuery), [XSD](https://en.wikipedia.org/wiki/XML_Schema_(W3C)) [описание](https://bdpx.github.io/xml/lab3/xsd.html)). А также анализ структур и баз данных на [EXPath](http://expath.org/), [XSL](https://en.wikipedia.org/wiki/XSL), [XSLT](https://en.wikipedia.org/wiki/XSLT), [EXSLT](https://en.wikipedia.org/wiki/EXSLT), [Relax NG](https://en.wikipedia.org/wiki/RELAX_NG), [XSpec](https://github.com/expath/xspec/tree/master), [XLink](https://en.wikipedia.org/wiki/XLink), [XMark](https://projects.cwi.nl/xmark/index.html), [XInclude](https://www.w3.org/TR/xinclude/), [XProc](https://en.wikipedia.org/wiki/XProc), [OPML](https://en.wikipedia.org/wiki/OPML), [XQL](http://www.ibiblio.org/xql/xql-proposal.html)

**SQL** и **XML** по отдельности имеют много разной критики, но по полноте функционала замены им пока не наблюдается. Есть определенные ограничения в преобразовании типов данных по цепочке `Python <-> SQL <-> XML`, так как типы данных SQL и типы данных из пространств имен [XDM](https://en.wikipedia.org/wiki/XQuery_and_XPath_Data_Model) аскетичнее и не перекрываются полностью. Есть сложности в возврате результата работы (кода возврата) функции (хранимой процедуры) `XPath & XQuery -> SQL -> Python`. Это важный момент, так как если ничего не предпринять дополнительно, то SQL Server при возрастании нагрузки не собирает запросы от прикладной программы в очередь, а откидывает их в том числе по взаимоблокировке и недогружается. Разрабатывается собственный [функционал](https://docs.sqlalchemy.org/en/14/dialects/mssql.html#module-sqlalchemy.dialects.mssql.pyodbc) Python-а для работы с SQL Server-ом, но нет плагина или интеграции [Saxon](https://www.saxonica.com/about/about.xml)-а, [Schematron](https://en.wikipedia.org/wiki/Schematron)-а и возможностей [BaseX](https://en.wikipedia.org/wiki/BaseX) внутри ядра баз данных. Таким образом для достижения красоты и гармонии в прикладном программировании усилий разработчиков мало. Требуется также прогресс в развитии ядра баз данных SQL Server-а.

Много разрозненных наработок, использующих возможности только **XML** для работы с данными недоведены, устарели и стали историей.

[**Объектно-ориентированные базы данных**](https://en.wikipedia.org/wiki/Object_database) в виде составных и пользовательских типов данных с неограниченной гибкостью как продолжение темы [**объектно-ориентированного программирования (сокращенно ООП)**](https://en.wikipedia.org/wiki/Object-oriented_programming), начиная со списков и словарей с их срезами, [DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html)-ы как главный козырь [Pandas](https://en.wikipedia.org/wiki/Pandas_(software)) и заканчивая классами с их композицией и наследованием, к которым подводят мысль во многих книгах, пока к сожалению не обрели своих СУБД и используются в университетской среде насколько позволяет оперативная память операционной системы и только в однопользовательском режиме.

[**не-SQL-ные СУБД**](https://aws.amazon.com/ru/nosql/ "Есть мнение в разных источниках, что они быстрее SQL-ных баз"), числу которых сейчас нет счета, по сравнению с **SQL-ными** имеют столько преимуществ сколько и неудобств. Какая-то одна в чем-то лучше и в чем-то хуже какой-то другой. Большинство из них в разных модификациях являются продолжением темы [JSON](https://en.wikipedia.org/wiki/JSON) + двоичные поля и [BLOB](https://en.wikipedia.org/wiki/Binary_large_object)-ы. Кстати, могли бы сразу за основу взять [YAML](https://en.wikipedia.org/wiki/YAML). Но видимо разработчики - сторонники JavaScript-а. Не заменят XML, так как есть принципиальное отличие:
 - `*.xml` - ветвление, топология, структура,
 - `*.dat, *.ini, *.json, *.yaml` - словарь, конфигурация, настройка.

Есть коммерческие платформы для работы с данными непонятно на чем, например [MarkLogic](https://www.marklogic.com/), но они сами в себе

![007 001 001](https://user-images.githubusercontent.com/104857185/209877366-3c1a9309-736c-49ce-9bb3-709e16110020.jpg)

- Замена бумажного и электронного документооборота, а также замена коммерческих консультантов

Руководящие документы (Руководства, Нормативы, Стандарты, Приказы, Инструкции) необходимо перестать распечатывать на бумаге, а также гонять их копии разной давности с ЭЦП и без по электронной почте, ватсапам, телегам и соцсетям. Необходимо дать доступ к ним только из единственного авторитетного источника не в виде художественного текста, а в виде чистого императива, который может определенно и однозначно восприниматься прикладными программами для принятия решений и возврата отчетов о выполнении. Для этого их вероятно потребуется **переосмыслить**, перенеся повествовательную часть в комментарии, и **продумать их структуру ветвления** с данными, параметрами и ссылками на другие источники в зависимости от типа документа и его отрасли, затем **сохранить в формате XML**, чтобы упорядоченно **записать в поля** `XML(CONTENT dbo.XSD-схема)` таблиц баз данных и **парсить** как [DOM](https://ru.wikipedia.org/wiki/Document_Object_Model) или [SAX](https://en.wikipedia.org/wiki/Simple_API_for_XML) запросами на XPath & XQuery **вручную** или **программно** в прикладных задачах. Таким образом документы и вносимые в них изменения смогут быстро и просто исполняться без перечитывания их текста, без сравнения с предыдущими редакциями и без трактования их разными людьми в разных контекстах и ситуациях.

###### Хранение информации в файлах различных типов и их использование

![1 001 001](https://user-images.githubusercontent.com/104857185/167037090-9cd548c0-9643-4903-adce-13e2a039226d.jpg)

 - API-шки сопряжения с автоматикой смежных систем

[API-шки](https://en.wikipedia.org/wiki/API) в широком понимании модели [Клиент - Сервер](https://en.wikipedia.org/wiki/Client%E2%80%93server_model) локально или по сети применяются для облегчения внесения изменений и для обеспечения единообразия в повторном применении исходных текстов <span style="color:green">`(функции, интерфейсы, статические и динамические библиотеки)`</span> на всех клиентах в обращениях к службам, предоставляемым серверными компонентами в [Сервисном слое](https://en.wikipedia.org/wiki/Service_layer), который сопоставляется с прикладным слоем в [Модели OSI](https://en.wikipedia.org/wiki/OSI_model), а точнее располагается в 3-й уровне абстракции [ее 8-ого слоя](https://en.wikipedia.org/wiki/Layer_8) в разной степени гибкости [Сервис-ориентированной архитектуры](https://en.wikipedia.org/wiki/Service-oriented_architecture) и который пока относят к стороннему (часто закрытому) программному обеспечению, дописанному дополнительно к общеизвестным прикладным протоколам :slightly_smiling_face: Этот слой в полном варианте состоит из пары - сервер состояний <span style="color:Orange">(в идеале внешний сервер СУБД)</span> и сервер сообщений о событиях <span style="color:Orange">(например OPC-сервер)</span> :slightly_smiling_face:

![009 001](https://user-images.githubusercontent.com/104857185/211207093-d0c7b9b9-5594-4dcd-a3e3-b7f81757ff6f.jpg)

Фирмы-изготовители оборудования и программного обеспечения для работы с ним, к которому они не прилагают исчерпывающее описание состояний и событий, свои DDK и SDK, а также и исходные тексты **для написания прикладных API-шек с нуля или поверх комплектных от фирмы-изготовителя**, в эту идею к сожалению не вписываются, так как этим исключают интеграцию с ними прикладных задач. Они закрываются, применяя сертификаты, программные и аппаратные ключи, смарт-лицензии и активацию по сети, а к широкому сообществу обращаются лишь раз от разу при потребности в свежих идеях, которых это сообщество без глубокого вовлечения вероятно дает недостаточно. Они чрезмерно увлеклись переносом функционала на [Облака](https://en.wikipedia.org/wiki/Cloud_computing), увеличивая вероятность отказов при разрывах соединения с первичным оборудованием. Таким образом, без проникновения концепции [Open Source](https://en.wikipedia.org/wiki/Open_source) технический прогресс в этой отрасли смещается в сторону налаживания межоблачного взаимодействия и наблюдается замедление в развитии программной части для первичного оборудования (прошивки, операционные системы, языки программирования, конфигураторы) и соответственно самого первичного оборудования. Ситуация вынуждает опытных разработчиков искать простора для полета их творческой мысли в стартапах на более мелких задачах. Требуется политическое решение
