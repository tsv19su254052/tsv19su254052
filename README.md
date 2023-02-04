[Объемы выполняемых работ и способы их выполнения](https://github.com/tsv19su254052/tsv19su254052/blob/main/Works.md)

[Применяемые языки программирования и их библиотеки](https://github.com/tsv19su254052/tsv19su254052/blob/main/Languages.md)

Примечания:

Репозитории индувидуальной разработки здесь и в организациях являются так сказать неполными **бэкапами с оригиналов проектов** (только отслеживаемые на `Git`-е файлы проекта).

Функция `GitHub`-а ограничена возможностью:
 - выбрать текущую ветку,
 - почитать текстовые и графические пояснения к проекту,
 - ознакомиться с математическим обеспечением,
 - посмотреть исходники,
 - почитать объемы доработок,
 - предложить правку с помощью `Pull Request`-а, предварительно уточнив ветку для внесения правок,
 - склонировать исходники себе или ответвить их у себя (мало пользы, так как клон или ветка со временем устареет или разойдется с оригиналом и будет конфликт слияния).

Синхронизировать подмодули на репозитории и его клонах средствами `GitHub`-а не получится (там только неактивные ссылки), потому что они асинхронно импортированы внутри среды разработки в проект как дубликаты (импортируются и синхронизируются с их оригиналами в окошке терминала командами `git submodules ...`) и соответственно не отслеживаются на `Git`-е (не дублируются дважды) для экономии места на репозитории. 

Некоторые особенности `GitHub`-а:
 - на репозиториях оригиналов подмодулей значек <span style="color:Green">"Used by ..."</span> пока не появляется (граф зависимостей - см. https://stackoverflow.com/questions/56888176/how-to-configure-github-used-by-feature-for-java-projects),
 - при добавлении участника в `Contributor`-ы его активность на `GitHub`-е (если она ему так важна и нужна) не видна ни у него, ни у остальных.

Оригиналы проектов хранятся в сетевой папке на файловом сервере, полностью функциональны только внутри инфраструктуры и могут запускаться на исполнение:
 - из внешней сети или в локальной подсетке по RDP на терминальном сервере (один набор интерпретаторов и их библиотек для всех пользователей),
 - в локальной подсетке на клиенте c подключенной сетевой папки (интерпретатор и библиотеки, устанавливаются на каждом клиенте дополнительно).

При смене учетки на Windows или на Google проект не синхронизируется с GitHub-ом (как второй и третий фактор проверки владения репозиторием):
![pyCharm - Ошибка синхронизации с GitHub-ом (другая учетка)](https://user-images.githubusercontent.com/104857185/216789558-ea500396-740e-4977-a426-22d01753f799.png)

Базы данных и их бэкапы хранятся на сервере СУБД и привязаны к его системным настройкам.

Конфигурация и топология аппаратуры, прошивки аппаратуры, настройки локальной сети (адреса, шлюзы, сервера, vlan-ы и остальное) хранятся в своих папках на файловом сервере (пути до них указаны в репозиториях), откуда их можно открыть и прочитать на аппаратуре или в конфигураторе аппаратуры.

----
Связаться со мной можно в обсуждениях на репозиториях. К критике отношусь конструктивно. Буду благодарен за замечания.

Проспонсировать :sparkling_heart: можно на карточку :credit_card: <span style="color:Green">VISA</span> СберБанка 4276 3000 3587 2715
