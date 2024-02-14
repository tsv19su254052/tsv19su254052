## Второй слой - логика, расчеты, математическое моделирование, анализ, нейросетки (машинное обучение), искусственный интеллект

Если нужно что-то для нечастого или начального использования вручную с ключами, с путями и с последовательным вводом-выводом или для вторичных вызовов как функция, [API](https://en.wikipedia.org/wiki/API)-шка или [хранимая процедура](https://en.wikipedia.org/wiki/Stored_procedure) для работы с **SQL**-ными базами данных, **XML**-ными структурами данных, а также `XML`-ными полями внутри `SQL`-ных баз данных, то пишем [скрипт](https://timeweb.com/ru/community/articles/chto-takoe-skript):
 - на `SQL` с помощью среды разработки [SQL Server Management Studio](https://en.wikipedia.org/wiki/SQL_Server_Management_Studio) или [Azure Data Studio](https://learn.microsoft.com/ru-ru/azure-data-studio/quickstart-sql-server) (попроще, кривая, на неанглийских кодировках лепит краказябру, может закидывать всю папку проекта на GitHub),
 - на `XPath & XQuery`с помощью среды управления [BaseX](https://en.wikipedia.org/wiki/BaseX) [💬](https://docs.basex.org/wiki/XQuery_Update "Статья на сайте разработчиков"), [Oxygen XML](https://en.wikipedia.org/wiki/Oxygen_XML_Editor) [💬](https://www.oxygenxml.com/doc/versions/25.0/ug-editor/topics/preferences-xslt-saxon8.html) или [Raptor XML](https://www.altova.com/raptorxml),
 - на `SQL` со вставками на `XPath & XQuery`,
 - на `Python`-е с помощью среды разработки [pyCharm](https://en.wikipedia.org/wiki/PyCharm),
 - то же с уже проверенными вставками на `SQL` + `XPath & XQuery` - в преобразовании типов данных по цепочке `Python` <-> `SQL` <-> `XML + XPath & XQuery` (cм. пространства имен [XDM](https://en.wikipedia.org/wiki/XQuery_and_XPath_Data_Model)) есть [тонкости](https://en.wikipedia.org/wiki/Object%E2%80%93relational_impedance_mismatch "Вступительная часть по освещению данной темы"), не всегда правильно возвращается результат работы (успех, отказ, причина отказа).

Для подключения к базам данных:
 - со справочниками достаточно [драйвера СУБД](https://stackoverflow.com/questions/39440008/differences-between-drivers-for-odbc-drivers), драйверы с возможностями побогаче по наблюдениям работают медленнее,
 - с оперативными (рабочими) данными, в которых присутствуют вложенные обработки исключений и транзакции, нужен [системный DSN](https://www.websense.com/content/support/library/data/v85/help/windows%20dsn.aspx) на базе драйвера СУБД.

Без индексов [SQL Server](https://en.wikipedia.org/wiki/Microsoft_SQL_Server) сильно грузится и откидывает тяжелые запросы по [взаимоблокировке](https://learn.microsoft.com/ru-ru/sql/relational-databases/sql-server-deadlocks-guide?view=sql-server-ver16) [💬](https://learn.microsoft.com/ru-ru/troubleshoot/sql/database-engine/performance/understand-resolve-blocking). Обертываем запрос в обработку исключения и выполняем ее в цикле попыток с нарастающей задержкой, чтобы не спамить сервер. При увеличении количества попыток паузы растягиваются и сервер недогружается. Снять попытки с паузы можно обратными вызовами от [Service Broker](https://learn.microsoft.com/ru-ru/sql/database-engine/configure-windows/sql-server-service-broker?view=sql-server-ver16). Но там много ручной работы, которая усложняет внесение изменений. Внутри цикла попыток дополнительно надо:
 - проиндексировать поля таблиц, участвующих в условиях выборки,
 - уточнить уровни изоляции транзакций,
 - а также принять иные меры,
 
 как описано например в [статье](https://habr.com/ru/companies/mindbox/articles/261661/).

Что даст примерно следующий эффект:
 - сузятся диапазоны блокировки данных,
 - блокировка перейдет с данных на индексы,
 - запросы останутся в очереди,
 - нагрузка процессора снизится в 10 ... 12 раз,
 - нагрузка на жесткие диски уменьшится примерно на 2 порядка,
 - счетчики попыток уменьшатся примерно на 2 порядка.

Для `SQL`-ных полей есть библиотека [SQLAlchemy](https://docs.sqlalchemy.org/en/14/dialects/mssql.html#module-sqlalchemy.dialects.mssql.pyodbc) как слой абстракции в режиме [Core](https://docs.sqlalchemy.org/en/20/core) или в режиме [ORM](https://docs.sqlalchemy.org/en/20/orm/). Но там возможности пока победнее, чем в вышеперечисленных пунктах.

----

Для `XML`-ных структур данных применяются:
 - [XSD](https://en.wikipedia.org/wiki/XML_Schema_(W3C)) [💬](https://bdpx.github.io/xml/lab3/xsd.html "Описание") и [Relax NG](https://en.wikipedia.org/wiki/RELAX_NG) - определение входной информации на соответствие,
 - [XLink](https://en.wikipedia.org/wiki/XLink) - привязка ссылок на внешние ресурсы,
 - [XInclude](https://en.wikipedia.org/wiki/XInclude) [💬](https://www.w3.org/TR/xinclude/) - привязка или вставка внешних файлов, в том числе других структур данных,
 - [XPointer](https://en.wikipedia.org/wiki/XPointer) - индексация по подветкам и по узлам,
 - [XPath](https://en.wikipedia.org/wiki/XPath) [💬](https://www.w3.org/TR/xpath-functions/#maps-and-arrays) & [XQuery](https://en.wikipedia.org/wiki/XQuery) [💬](http://xmlhack.ru/texts/03/xquery/what.is.xquery.html) [💬](https://documentation.softwareag.com/webmethods/compendiums/v10-5/C_API_Management/index.html#page/api-mgmt-comp%2Fco-portlet_custom_search_write_xquery.html%23) и [EXPath](http://expath.org/) - написание запросов вручную,
 - [XQL](http://www.ibiblio.org/xql/xql-proposal.html) [💬](https://www.w3.org/TandS/QL/QL98/pp/xql.html) - написание запросов частично программно и частично вручную,
 - [XProc](https://en.wikipedia.org/wiki/XProc) и [OPML](https://en.wikipedia.org/wiki/OPML) - выполнение запроса в прикладном слое,
 - [XSLT](https://en.wikipedia.org/wiki/XSLT), [EXSLT](https://en.wikipedia.org/wiki/EXSLT) и [XMark](https://projects.cwi.nl/xmark/index.html) - оформление результата запроса,
 - [Saxon](https://www.saxonica.com/about/about.xml),
 - [Schematron](https://en.wikipedia.org/wiki/Schematron) [💬](https://schematron.com/hints/xsdtoschematron/01_converting_xml_schemas_to_schematron.html) - поглубже и посложнее, чем `XSLT`,
 - [XSpec](https://xspec.io/about/) [💬](https://github.com/expath/xspec/tree/master) [💬](https://groups.google.com/g/xspec-users "Обсуждения по теме в группе") - анализ работы вышеперечисленных.

Эти наработки из самостоятельного (иногда платного) прикладного ПО также перешли в плагины для сред разработки и в библиотеки:
 - [xml](https://docs.python.org/3/library/xml.html),
 - [lxml](https://lxml.de/) [💬](https://pypi.org/project/lxml "Статья на зеркале с библиотекой со ссылками на GitHub") (быстрее, сложнее),
 - [bs4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) [💬](https://en.wikipedia.org/wiki/Beautiful_Soup_(HTML_parser)) (чистый парсер),

 которые их парсят как [SAX](https://en.wikipedia.org/wiki/Simple_API_for_XML), анализируют как [DOM](https://en.wikipedia.org/wiki/Document_Object_Model), изменяют и записывают.

Можно применить пользовательские пространства имен посложнее, которые неплохо бы держать где-нибудь на внешнем ресурсе `xmlns:x__="http://www._____ ..."` .

Множество разрозненных наработок только на **XML** только для работы с данными недоведены, устарели и стали историей.

![007 001 001](https://user-images.githubusercontent.com/104857185/209877366-3c1a9309-736c-49ce-9bb3-709e16110020.jpg)

Для преобразования XML-ных структур данных в SQL-ные таблицы и обратно есть [SQLXML](https://en.wikipedia.org/wiki/SQL/XML). Например, используется в SCADA-системе SIEMENS-а для импорта считанной топологии в проект.
