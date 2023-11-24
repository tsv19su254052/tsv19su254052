## Второй слой - логика, расчеты, математическое моделирование, анализ, нейросетки (машинное обучение), искусственный интеллект

Если нужно что-то для нечастого использования вручную с ключами, с путями и с последовательным вводом-выводом или для вторичных вызовов как функция, [API](https://en.wikipedia.org/wiki/API)-шка или [хранимая процедура](https://en.wikipedia.org/wiki/Stored_procedure) для работы с базами и структурами данных, то пишем [скрипт](https://timeweb.com/ru/community/articles/chto-takoe-skript):
 - на `SQL` с помощью среды разработки [SQL Server Management Studio](https://en.wikipedia.org/wiki/SQL_Server_Management_Studio),
 - на `XPath & XQuery`с помощью среды управления [BaseX](https://en.wikipedia.org/wiki/BaseX) [💬](https://docs.basex.org/wiki/XQuery_Update "Статья на сайте разработчиков"), [Oxygen XML](https://en.wikipedia.org/wiki/Oxygen_XML_Editor) [💬](https://www.oxygenxml.com/doc/versions/25.0/ug-editor/topics/preferences-xslt-saxon8.html) или [Raptor XML](https://www.altova.com/raptorxml),
 - на `SQL` со вставками на `XPath & XQuery`,
 - на `Python`-е с помощью среды разработки [pyCharm](https://en.wikipedia.org/wiki/PyCharm),
 - то же с уже проверенными вставками на `SQL` + `XPath & XQuery`.

Если ничего не предпринимать дополнительно, то [SQL Server](https://en.wikipedia.org/wiki/Microsoft_SQL_Server) при возрастании нагрузки с клиентов не собирает запросы от прикладного уровня в очередь, а откидывает их в том числе по взаимоблокировке и недогружается.

Для `SQL`-ных полей есть библиотека [SQLAlchemy](https://docs.sqlalchemy.org/en/14/dialects/mssql.html#module-sqlalchemy.dialects.mssql.pyodbc) в режиме [Core](https://docs.sqlalchemy.org/en/20/core) как слой абстракции.

Для `XML`-ных полей есть интересные возможности у библиотек:
 - [lxml](https://lxml.de/apidoc/lxml.isoschematron.html "Статья от разработчиков") [💬](https://pypi.org/project/lxml "Статья на зеркале с библиотекой со ссылками на GitHub"),
 - [xml.dom](https://docs.python.org/3.9/library/xml.dom.minidom.html "DOM") и [xml.etree](https://docs.python.org/3.7/library/xml.etree.elementtree.html "SAX"),
 - [bs4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), 

которые предполагается использовать для парса сайтов в основном как [DOM](https://en.wikipedia.org/wiki/Document_Object_Model), но все они используют те же типы данных (пространства имен).

Для `XML`-ных структур данных применяются:
 - [XSD](https://en.wikipedia.org/wiki/XML_Schema_(W3C)) [💬](https://bdpx.github.io/xml/lab3/xsd.html "Описание") и [Relax NG](https://en.wikipedia.org/wiki/RELAX_NG) (определение входной информации на соответствие),
 - [XLink](https://en.wikipedia.org/wiki/XLink) (привязка ссылок на внешние ресурсы),
 - [XInclude](https://en.wikipedia.org/wiki/XInclude) [💬](https://www.w3.org/TR/xinclude/) (привязка внешних файлов, в том числе других структур данных),
 - [XPointer](https://en.wikipedia.org/wiki/XPointer) (индексация по подветкам и по узлам),
 - [XPath](https://en.wikipedia.org/wiki/XPath) [💬](https://www.w3.org/TR/xpath-functions/#maps-and-arrays) & [XQuery](https://en.wikipedia.org/wiki/XQuery) [💬](http://xmlhack.ru/texts/03/xquery/what.is.xquery.html) [💬](https://documentation.softwareag.com/webmethods/compendiums/v10-5/C_API_Management/index.html#page/api-mgmt-comp%2Fco-portlet_custom_search_write_xquery.html%23) и [EXPath](http://expath.org/) (написание запросов вручную),
 - [XQL](http://www.ibiblio.org/xql/xql-proposal.html) [💬](https://www.w3.org/TandS/QL/QL98/pp/xql.html) (написание запросов частично программно и частично вручную),
 - [XProc](https://en.wikipedia.org/wiki/XProc), [XSpec](https://github.com/expath/xspec/tree/master) и [OPML](https://en.wikipedia.org/wiki/OPML) (выполнение запроса в прикладном слое),
 - [XSLT](https://en.wikipedia.org/wiki/XSLT), [EXSLT](https://en.wikipedia.org/wiki/EXSLT) и [XMark](https://projects.cwi.nl/xmark/index.html) (оформление результата запроса).

 Есть [тонкости 💬](https://en.wikipedia.org/wiki/Object%E2%80%93relational_impedance_mismatch "Вступительная часть по освещению данной темы") в передаче входных данных на вход функции (хранимой процедуры) и в возврате результата из нее обратно. Надо внимательно смотреть на преобразование типов данных в пространствах имен по цепочке `Python <-> SQL <-> XML <-> XPath & XQuery` [XDM](https://en.wikipedia.org/wiki/XQuery_and_XPath_Data_Model), так как те аскетичнее этих и не перекрываются полностью. Можно применить пользовательские пространства имен посложнее, которые неплохо бы держать где-нибудь на внешнем ресурсе `xmlns:x__="http://www._____ ..."` .

 [Saxon](https://www.saxonica.com/about/about.xml) и [Schematron](https://en.wikipedia.org/wiki/Schematron) сейчас из самостоятельного прикладного ПО перешли в плагины для сред разработки.

Множество разрозненных наработок только на **XML** только для работы с данными недоведены, устарели и стали историей.

![007 001 001](https://user-images.githubusercontent.com/104857185/209877366-3c1a9309-736c-49ce-9bb3-709e16110020.jpg)

С развитием и распространением персональной вычислительной техники в начале 1990-х годов многие [эмпирические методы](https://en.wikipedia.org/wiki/Empirical_research) в прикладной математике с [номограммами](https://en.wikipedia.org/wiki/Nomogram) получили свое практическое подтверждение путем расчета аналитических формул напрямую, используя [конечно-разностные формы](https://ru.wikipedia.org/wiki/%D0%A0%D0%B0%D0%B7%D0%BD%D0%BE%D1%81%D1%82%D0%BD%D0%B0%D1%8F_%D1%81%D1%85%D0%B5%D0%BC%D0%B0) их записи в определенных пределах интегрирования или дифференцирования. Для удобства восприятия решение как правило стремились получить в виде экстремума градиента на поверхности или на облаке точек, подбирая диапазоны итерации и шаги приращения вручную или более осторожно методом последовательного приближения. Посчитали различные задачи оптимизации, которые ждали своего решения еще с 1960-х годов.

![лекции по МОСУ у Кудряшева](https://github.com/tsv19su254052/tsv19su254052/assets/104857185/a5459d73-51ee-471a-8e2f-7a01471c1d2a)