Тарасов Сергей Владимирович
----------------------------

 - Прототипирование
 - Расчеты и математическое моделирование
 - Прикладное программирование на **[C++](https://en.wikipedia.org/wiki/C%2B%2B)**, **[Tcl/Tk](https://en.wikipedia.org/wiki/Tcl)**, **[Python](https://en.wikipedia.org/wiki/Python_(programming_language))** (Текстовые приложения, Графические оболочки, API-шки)
 - Разработка и администрирование баз данных на **MS SQL Server**-е в части **[SQL](https://en.wikipedia.org/wiki/SQL) + [XML](https://en.wikipedia.org/wiki/XML)** [описание](http://www.chernyshov.com/SPPO_6/theory/wt_xml.htm) ([XPath](https://en.wikipedia.org/wiki/XPath) & [XQuery](https://en.wikipedia.org/wiki/XQuery), [EXPath](http://expath.org/), [XSD](https://en.wikipedia.org/wiki/XML_Schema_(W3C)) [описание](https://bdpx.github.io/xml/lab3/xsd.html), [XSL](https://ru.wikipedia.org/wiki/XSL), [XSLT](https://en.wikipedia.org/wiki/XSLT). [EXSLT](https://ru.wikipedia.org/wiki/EXSLT), [Relax NG](https://en.wikipedia.org/wiki/RELAX_NG), [XSpec](https://github.com/expath/xspec/tree/master), [XLink](https://en.wikipedia.org/wiki/XLink), [XMark](https://projects.cwi.nl/xmark/index.html), [XInclude](https://www.w3.org/TR/xinclude/), [XProc](https://en.wikipedia.org/wiki/XProc), [OPML](https://en.wikipedia.org/wiki/OPML), [XQL](http://www.ibiblio.org/xql/xql-proposal.html))

![007 001 001](https://user-images.githubusercontent.com/104857185/209877366-3c1a9309-736c-49ce-9bb3-709e16110020.jpg)

ИМХО тезисно по текущей ситуации с СУБД в целом:

SQL и XML по отдельности имеют много разной критики, но по полноте функционала замены пока не наблюдается. Есть определенные ограничения в преобразовании типов данных Python -> SQL -> XML и обратно, так как типы данных из пространств имен XSD, XQuery беднее и аскетичнее. Есть сложности в передаче результата работы (кода возврата) функции и процедуры Python -> SQL -> XPath & XQuery и обратно. Это очень важный момент для SQL Server-а, так как при нагрузке он не собирает запросы от прикладной программы в очередь, а откидывает их в том числе по взаимоблокировке и недогружается. Поэтому написать, протестировать и отладить в полном объеме - трудная и сложная работа. Идут работы по разработке собственного [функционала](https://docs.sqlalchemy.org/en/14/dialects/mssql.html#module-sqlalchemy.dialects.mssql.pyodbc) Python-а для работы с СУБД, в том числе с SQL Server-ом, но нет плагина или интеграции [Saxon-а](https://www.saxonica.com/about/about.xml), [Schematron-а](https://en.wikipedia.org/wiki/Schematron) и возможностей [BaseX](https://ru.wikipedia.org/wiki/BaseX) внутри ядра баз данных SQL Server-а. То есть для достижения красоты и гармонии в прикладном программировании усилий разработчиков мало и требуется прогресс в развитии и со стороны библиотек Python-а, и со стороны SQL Server-а.

Много разрозненных наработок, использующих возможности только XML для работы с данными недоведены, устарели и стали историей.

Есть коммерческие платформы для работы с данными, например [MarkLogic](https://www.marklogic.com/), но они сами в себе.

Объектно-ориентированные базы данных в виде составных и пользовательских типов данных с неограниченной гибкостью как продолжение темы объектно-ориентированного программирования (начиная со списков и словарей с их срезами, DataFrame-ы из [pandas](https://en.wikipedia.org/wiki/Pandas_(software)) и заканчивая классами с их композицией и наследованием), к которым подводят мысль во многих книгах, пока не имеют своих полноценных СУБД и используются в университетской среде для записи и чтения небольших и несложных объемов данных настолько, насколько позволяет оперативная память операционной системы, на которой их исполняют и только в однопользовательском режиме.

no-SQL-ные СУБД, числу которых сейчас нет счета, по сравнению с SQL-ными имеют столько преимуществ сколько и неудобств. Какая-то одна no-SQL-ная СУБД в чем-то лучше и в чем-то хуже какой-то другой. Большинство в разных модификациях являются продолжением темы JSON + двоичные поля и BLOB-ы. Не заменят XML, так как есть принципиальное отличие:
 - *.xml - ветвление, топология, структура,
 - *.dat, *.ini, *.json, *.yaml - словарь, конфигурация, настройка
