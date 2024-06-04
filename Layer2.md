## Второй слой - логика, расчеты, математическое моделирование, анализ

Если нужно что-то для нечастого или начального использования вручную с ключами, с путями и с последовательным вводом-выводом или для вторичных вызовов как функция, [API](https://en.wikipedia.org/wiki/API)-шка , то пишем [скрипт](https://timeweb.com/ru/community/articles/chto-takoe-skript):
 - на `Python`-е с помощью среды разработки [pyCharm](https://en.wikipedia.org/wiki/PyCharm),
 - для работы с **SQL**-ными базами данных на `SQL` с помощью среды разработки [SQL Server Management Studio](https://en.wikipedia.org/wiki/SQL_Server_Management_Studio) или [Azure Data Studio](https://learn.microsoft.com/ru-ru/azure-data-studio/quickstart-sql-server) (попроще, кривая, на разных Unicode-ах строчки не на win-1251 преобразует в ромбики и квадратики, закидывает все без разбора на GitHub),
 - для работы c **XML**-ными структурами данных, а также `XML`-ными полями внутри `SQL`-ных баз данных на `XPath & XQuery`с помощью среды управления [BaseX](https://en.wikipedia.org/wiki/BaseX) [💬](https://docs.basex.org/wiki/XQuery_Update "Статья на сайте разработчиков"), [Oxygen XML](https://en.wikipedia.org/wiki/Oxygen_XML_Editor) [💬](https://www.oxygenxml.com/doc/versions/25.0/ug-editor/topics/preferences-xslt-saxon8.html) или [Raptor XML](https://www.altova.com/raptorxml) (вот неплохое [видео](https://www.youtube.com/watch?v=fu6o5Cw0XzU)),
 - на `SQL` со вставками на `XPath & XQuery`, после проверок на всех режимах упаковываем его в [хранимую процедуру](https://en.wikipedia.org/wiki/Stored_procedure) базы данных и вызываем из `Python`-а с передачей параметров на вход и выход (см. [статью](https://github.com/mkleehammer/pyodbc/wiki/Calling-Stored-Procedures) ).

Примечания по 3-му пункту:
 - Если в хранимую процедуру передаются не одинарные переменные, а массивы данных, то для экономии емкости ОЗУ используем [временные таблицы](https://metanit.com/sql/sqlserver/10.4.php) на [tempdb](https://learn.microsoft.com/ru-ru/sql/relational-databases/databases/tempdb-database?view=sql-server-ver16) с двойным хэштэгом в начале имени для ее переноса в глобальную зону видимости. Перед повторным использованием временной таблицы надо не забыть очистить ее от предыдущих данных.
 - В преобразовании типов данных по цепочке `Python` <-> `SQL` <->  `XPath & XQuery` на `XML` (cм. пространства имен [XDM](https://en.wikipedia.org/wiki/XQuery_and_XPath_Data_Model)) есть [тонкости](https://en.wikipedia.org/wiki/Object%E2%80%93relational_impedance_mismatch "Вступительная часть по освещению данной темы").
 - Не всегда правильно возвращается результат работы и не все результаты работы возвращаются (успех, отказ, причина отказа).
 - Особенность применяемого на сервере диалекта `SQL` такова, что в функционале `XPath & XQuery` не все работает, как описано в [версии 3.0](https://www.w3schools.com/xml/xml_xpath.asp). Иногда требуется добавлять кавычки, круглые и фигурные скобки и спецсимволы. Тут поможет только опыт и наработки.
 - Можно применить пользовательские пространства имен `xmlns:x__="http://www._____ ..."` посложнее, которые неплохо бы держать где-нибудь на внешнем ресурсе.

Для подключения к базам данных:
 - со справочниками достаточно [драйвера СУБД](https://stackoverflow.com/questions/39440008/differences-between-drivers-for-odbc-drivers), драйверы с возможностями побогаче по наблюдениям работают медленнее,
 - с оперативными (рабочими) данными, в которых присутствуют вложенные обработки исключений и помеченные транзакции, нужен [системный DSN](https://www.websense.com/content/support/library/data/v85/help/windows%20dsn.aspx) на базе драйвера СУБД.

Без индексов [SQL Server](https://en.wikipedia.org/wiki/Microsoft_SQL_Server) сильно грузится и откидывает тяжелые запросы по [взаимоблокировке](https://learn.microsoft.com/ru-ru/sql/relational-databases/sql-server-deadlocks-guide?view=sql-server-ver16) [💬](https://learn.microsoft.com/ru-ru/troubleshoot/sql/database-engine/performance/understand-resolve-blocking). Обертываем запрос в обработку исключения и выполняем ее в цикле попыток с нарастающей задержкой, чтобы не спамить сервер. При увеличении количества попыток паузы растягиваются и сервер недогружается. Снять попытки с паузы можно обратными вызовами от [Service Broker](https://learn.microsoft.com/ru-ru/sql/database-engine/configure-windows/sql-server-service-broker?view=sql-server-ver16). Но там много ручной работы, которая усложняет внесение изменений. Внутри цикла попыток дополнительно надо:
 - проиндексировать поля таблиц, участвующих в условиях выборки,
 - уточнить уровни изоляции транзакций,
 - а также принять иные меры,
 
 которые описаны например в [статье](https://habr.com/ru/companies/mindbox/articles/261661/).

Что даст примерно следующий эффект:
 - сузятся диапазоны блокировки данных,
 - блокировка перейдет с данных на индексы,
 - запросы останутся в очереди,
 - нагрузка процессора снизится в 10 ... 12 раз,
 - нагрузка на жесткие диски уменьшится примерно на 2 порядка,
 - счетчики попыток уменьшатся примерно на 2 порядка.

Для `SQL`-ных полей есть библиотека [SQLAlchemy](https://docs.sqlalchemy.org/en/14/dialects/mssql.html#module-sqlalchemy.dialects.mssql.pyodbc) как слой абстракции в режиме [Core](https://docs.sqlalchemy.org/en/20/core) или в режиме [ORM](https://docs.sqlalchemy.org/en/20/orm/). Но в ней возможности пока победнее.

----

Для проверки `XML`-ных структур данных на соответствие задуманному применяется:
 - сначала [XSD](https://en.wikipedia.org/wiki/XML_Schema_(W3C)) [💬](https://bdpx.github.io/xml/lab3/xsd.html "Описание") и [Relax NG](https://en.wikipedia.org/wiki/RELAX_NG) - определение входной информации на соответствие,
 - затем при необходимости [Schematron](https://en.wikipedia.org/wiki/Schematron) [💬](https://schematron.com/hints/xsdtoschematron/01_converting_xml_schemas_to_schematron.html) - поглубже и посложнее, чем `XSLT`,
 - [Saxon](https://www.saxonica.com/about/about.xml).

Для `XML`-ных структур данных применяются:
 - [XLink](https://en.wikipedia.org/wiki/XLink) - привязка ссылок на внешние ресурсы,
 - [XInclude](https://en.wikipedia.org/wiki/XInclude) [💬](https://www.w3.org/TR/xinclude/) - привязка или вставка внешних файлов, в том числе других структур данных,
 - [XPointer](https://en.wikipedia.org/wiki/XPointer) - индексация по подветкам и по узлам,
 - [XPath](https://en.wikipedia.org/wiki/XPath) [💬](https://www.w3.org/TR/xpath-functions/#maps-and-arrays) & [XQuery](https://en.wikipedia.org/wiki/XQuery) [💬](http://xmlhack.ru/texts/03/xquery/what.is.xquery.html) [💬](https://documentation.softwareag.com/webmethods/compendiums/v10-5/C_API_Management/index.html#page/api-mgmt-comp%2Fco-portlet_custom_search_write_xquery.html%23) и [EXPath](http://expath.org/) - написание запросов вручную,
 - [XQL](http://www.ibiblio.org/xql/xql-proposal.html) [💬](https://www.w3.org/TandS/QL/QL98/pp/xql.html) - написание запросов частично программно и частично вручную,
 - [XProc](https://en.wikipedia.org/wiki/XProc) и [OPML](https://en.wikipedia.org/wiki/OPML) - выполнение запроса в прикладном слое,
 - [XSLT](https://en.wikipedia.org/wiki/XSLT), [EXSLT](https://en.wikipedia.org/wiki/EXSLT) и [XMark](https://projects.cwi.nl/xmark/index.html) - оформление результата запроса,
 - [XSpec](https://xspec.io/about/) [💬](https://github.com/expath/xspec/tree/master) [💬](https://groups.google.com/g/xspec-users "Обсуждения по теме в группе") - анализ работы вышеперечисленных.

Эти наработки из самостоятельного (иногда платного) прикладного ПО также перешли в плагины для сред разработки и в библиотеки:
 - [xml](https://docs.python.org/3/library/xml.html),
 - [lxml](https://lxml.de/) [💬](https://pypi.org/project/lxml "Статья на зеркале с библиотекой со ссылками на GitHub") (быстрее, сложнее),
 - [bs4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) [💬](https://en.wikipedia.org/wiki/Beautiful_Soup_(HTML_parser)),

 которые парсят их как:
  - [DOM](https://en.wikipedia.org/wiki/Document_Object_Model), если как `SAX` никак ни сделать,
  - [SAX](https://en.wikipedia.org/wiki/Simple_API_for_XML) для экономина ресурсах и на вводе-выводе при использовании комплектного `XML`-ного парсера `SQL Server`-а внутри `XML`-ных ячеек.
  
Иногда используется комбинированный подход по ситуации - `SAX` внутри `DOM` или `DOM` внутри `SAX`.

Само собой изменяемую запись в базе данных надо заблокировать транзакцией с оптимальным уровнем изоляции, которая должна отработать максимально быстро и не ставить на паузу остальных клиентов. Запросы пишутся с учетом используемого уровня изоляции и блокировки.

----

Множество разрозненных наработок только на **XML** только для работы с данными недоведены, устарели и стали историей.

![007 001 001](https://user-images.githubusercontent.com/104857185/209877366-3c1a9309-736c-49ce-9bb3-709e16110020.jpg)

Для преобразования XML-ных структур данных в SQL-ные таблицы и обратно с начала 2000-х применялся [SQLXML](https://en.wikipedia.org/wiki/SQL/XML). Используется как плагин для импорта считанной топологии в конфигурацию, а из конфигурации в конструктор (дизайнер) проекта SCADA-системы SIEMENS-а.

----
Источников информации, в которых упоминаются эти тонкие и важные моменты, море в основном как точки входа к платным курсам обучения и далее к приглашению о сотрудничестве, но там капают пипеткой и не торопятся дать решение, чтобы обойти конкретные затыки в продвижении, а скорее убедить, что их авторы нужны и важны и что наверное стоит передать наработки в их так сказать более опытные руки, для экономии времени и сил сразу перекинув все что есть со всеми пояснениями на их инфраструктуру (на облако), потому что как выяснится позднее у них больше ресурсов на их доводку.
