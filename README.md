[Объемы выполняемых работ](https://github.com/tsv19su254052/tsv19su254052/blob/main/Works.md)

[Применяемые средства разработки](https://github.com/tsv19su254052/tsv19su254052/blob/main/Languages.md)

Проекты индувидуальной разработки на репозиториях здесь и в организациях, разработанные в том числе по подсказкам со [StackOverFlow](https://stackoverflow.com/users/15883118/tarasov-sergey "Помогает ориентироваться в огромном разнообразии библиотек и их методов на основе опыта их применения другими опытными разработчиками") и с [ChatGPT](https://openai.com/product/gpt-4 "Ищет ответы на короткие вопросы")  частично отслеживаются на `GitHub`-е по мере надобности в объеме, необходимом для удобства сведения и внесения изменений. Полностью функциональны внутри инфраструктуры, так как подключаются к серверу СУБД и что-то тянут с ссылочных файлов. Могут запускаться на исполнение на [клиентах](https://en.wikipedia.org/wiki/Client%E2%80%93server_model) следующими способами:
 - Внутри локальной сети по [ярлыку](https://sysadminwiki.ru/wiki/%D0%9C%D1%8F%D0%B3%D0%BA%D0%B8%D0%B5_%D0%B8_%D0%B6%D1%91%D1%81%D1%82%D0%BA%D0%B8%D0%B5_%D1%81%D1%81%D1%8B%D0%BB%D0%BA%D0%B8) , который указывает на исходник в подключенной [сетевой папке](https://ru.wikipedia.org/wiki/File_%28%D1%81%D1%85%D0%B5%D0%BC%D0%B0_URI%29) с файлового сервера. Интерпретатор и библиотеки устанавливаются на каждом клиенте дополнительно, из-за чего возможны глюки и косяки из-за разных версий и подверсий интерпретатора и библиотек.
 - Внутри локальной сети или из внешней сети по [RDP](https://ru.wikipedia.org/wiki/Remote_Desktop_Protocol) в [терминальном сервере](https://ru.wikipedia.org/wiki/%D0%A2%D0%B5%D1%80%D0%BC%D0%B8%D0%BD%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80). Один набор интерпретаторов и их библиотек для всех пользователей.
 - Внутри локальной сети или из внешней сети по [ВЭБ-мордочке](https://en.wikipedia.org/wiki/Website "Версия для компьютера и мобильная версия"). Предпологается совместая работа например на [coda.io](https://coda.io/workspaces/ws-ga7Eabm46u/folders/fl-7OkuhzSo66?source=doc-title-bar) с пре-`Commit`-ами [Terraform](https://en.wikipedia.org/wiki/Terraform_(software)) на инфраструктуре облака. Вот неплохое [видео](https://www.youtube.com/watch?v=JC_OyWpqNSA) с примером на [Selectel](https://en.wikipedia.org/wiki/Selectel). После ~~вождения за нос в трех соснах~~ знакомства с [Kubernetes](https://en.wikipedia.org/wiki/Kubernetes), `Node`-ами на [Docker](https://en.wikipedia.org/wiki/Docker_(software))-е с каким-нибудь минималистичным `Linux`-ом, `POD`-ами (надо рисовать проект, надо писать конфиги и манифесты на `yaml`-иках и все полностью закидывать туда), а затем с [VPS и VDS](https://www.reg.ru/vps/). И в итоге провайдер таки предложит как вершину их сервиса просто отдельные серверы с нормальной операционной системой типа `Windows Server` и прикладным ПО под нее. А еще просто перевезти свои сервера к ним и подключить их в их подсетку и за-`deploy`-ить проект в их облаке. Так же один набор интерпретаторов и их библиотек для всех пользователей.
 - Внутри локальной сети или из внешней сети в [мобильном приложении](https://en.wikipedia.org/wiki/Mobile_app) под [Android](https://en.wikipedia.org/wiki/Android_(operating_system)) :iphone:. 

Оригиналы стволовой и оперативных веток проектов хранятся на файловом сервере.

Функция `GitHub`-а на репозитории ограничена возможностью:
 - [x] выбрать текущую ветку,
 - [x] почитать текстовые и графические пояснения к проекту,
 - [x] ознакомиться с математическим обеспечением,
 - [x] посмотреть исходники,
 - [x] почитать объемы доработок,
 - [x] предложить правку с помощью `Pull Request`-а, предварительно уточнив ветку для внесения правок,
 - [ ] склонировать исходники себе или ответвить их у себя (непрактично, так как клон или ветка со временем устареет или разойдется с оригиналом и будет конфликт слияния).

Суммируя обращения к документации по `GitHub`-у и учитывая некоторый практический опыт работы с ним в том числе, дополнительно отмечу некоторые моменты:
 - На репозиториях оригиналов подмодулей значек <span style="color:Green">"Used by ..."</span> пока не появляется с включенным графом зависимостей или без него (см. [статью](https://stackoverflow.com/questions/56888176/how-to-configure-github-used-by-feature-for-java-projects)).
 - Синхронизировать подмодули на репозитории и его клонах средствами `GitHub`-а не получится (там только неактивные ссылки), потому что они асинхронно импортированы внутри среды разработки в проект как дубликаты (импортируются и синхронизируются с их оригиналами в окошке терминала командами `git submodules ...`) и соответственно не отслеживаются на `Git`-е (не дублируются дважды) для экономии места на репозитории. Свои подмодули не импортирую (они у меня есть).
 - Перетасовывать папки и файлы внутри папки проекта ([Git](https://en.wikipedia.org/wiki/Git) и [SVN](https://en.wikipedia.org/wiki/Apache_Subversion) это допускают в отличие от [CVS](https://en.wikipedia.org/wiki/Concurrent_Versions_System)) нежелательно. При обновлении кое-что может улететь с репозитория и из проекта, поэтому надо проверить их наличие и привязку на `Git`-е перед обновлением.
 - При добавлении участника в `Contributor`-ы его активность на `GitHub`-е (если она ему так важна и нужна) <span style="color:red;"> не видна ни у него, ни у остальных </span>.
 - Желательно делать `Commit`-ы на определенных стадиях готовности, чтобы не было сложностей со сведением `Pull Request`-ов на оперативной ветке.
 - При смене или переименовании недоменной учетки или при смене локального пароля на `Windows`, а также смене учетки на `Google` плагин `Git`-а в `pyCharm`-е не синхронизирует проект с `GitHub`-ом и не видит историю изменений. Пишет, что срабатывает второй и третий фактор проверки владения репозиторием (см. прилагаемый снимок экрана ниже) и придется переезжать на новую учетку на `GitHub`-е. Выход из ситуации - команда `git config --global --add safe.directory ...` , но она срабатывает на один сеанс работы с проектом. При этом эта активность на GitHub-е не отображается.

![pyCharm - Ошибка синхронизации с GitHub-ом (другая учетка)](https://user-images.githubusercontent.com/104857185/216789558-ea500396-740e-4977-a426-22d01753f799.png)

![pyCharm - git submodule add](https://github.com/tsv19su254052/tsv19su254052/assets/104857185/239cc5e3-8c76-4c03-8629-acb14e9fef99)

<!--
```diff
+ this text is highlighted in green
- this text is highlighted in red
```

```json
   // Code for coloring
```
```html
   // Code for coloring
```
```js
   // Code for coloring
```
```css
   // Code for coloring
```
-->

Текущая версия `pyCharm` пока не гармонирует со своим плагином для интеграции с [TortoiseGIT](https://en.wikipedia.org/wiki/TortoiseGit)

![TortoiseGit Plugin for pyCharm Установка с диска](https://github.com/tsv19su254052/tsv19su254052/assets/104857185/bf1d5fb9-0a03-4da8-a15b-b7477875ea55)

Базы данных в проектах - наиболее трудоемкая часть разработки. Делаются, администрируются, правятся, хранятся на сервере СУБД и привязаны к его системным настройкам. В объем проектов не входят. На `GitHub`-е соответственно не отслеживаются.

Прошивки и конфигурация аппаратуры, топология локальных сетей, настройки коммутаторов и маршрутизаторов (адреса, шлюзы, серверы DHCP и DNS, vlan-ы и остальное) хранятся в своих папках на файловом сервере, откуда их можно открыть и прочитать на аппаратуре или в конфигураторах аппаратуры. Пути до них указаны в текстовой части на репозиториях. На `GitHub`-е также не отслеживаются - он их не понимает.

----
Связаться со мной можно в обсуждениях на репозиториях. К критике отношусь конструктивно. Буду благодарен за замечания.

Облагодетельствовать :sparkling_heart: можно на карточку :credit_card: <span style="color:Green">VISA</span> СберБанка 4276 3000 3587 2715
