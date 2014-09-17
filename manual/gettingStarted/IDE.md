<!--- Copyright (C) 2009-2013 Typesafe Inc. <http://www.typesafe.com> -->
# Настройка на предпочитаната среда за разработка (IDE)

Да се работи с Play е лесно. Дори не е нужна специална среда за разработка, защото Play автоматично компилира и обновява промените, които правите по файловете с изходен код, така че можете да използвате и обикновен текстов редактор.

Все пак използването на модерни среди за разработка за Java или Scala ви носи предимства като автоматично допълване на думите, компилация на място, рефакторизиране и дебъгване.

## Eclipse

### Генериране на конфигурацията

Play има команда за улесняване на конфигурацията на Eclipse. За да преобразувате едно Play приложение в работещ проект под Eclipse, използвайте командата `eclipse`:

```
[my-first-app] $ eclipse
```

Ако искате да вземете и наличните библиотеки с изходен код (това ще отнеме повече време, а и някои от тях може да липсват):

```
[my-first-app] $ eclipse with-source=true
```

> Забележете, че ако използвате под-проекти, трябва да декларирате `skipParents` съответно в `build.sbt`:

```
import com.typesafe.sbteclipse.core.EclipsePlugin.EclipseKeys

EclipseKeys.skipParents in ThisBuild := false
```

или в play конзолата напишете:

``` 
[my-first-app] $ eclipse skip-parents=false
```

> Освен това, ако не искате компилацията да се включи преди извикването на `eclipse`, тогава просто добавете това към настройките:

```
EclipsePlugin.EclipseKeys.preTasks := Seq()
```

След това трябва да импортиране приложението в Workspace-а чрез менюто **File/Import/General/Existing project…** (първо компилирайте проекта).

[[images/eclipse.png]] 

За да дебъгвате стартирайте приложението чрез `activator -jvm-debug 9999 run` и в Eclipse изберете **Debug As**, **Debug Configurations** от контекстното меню на проекта. В диалоговия прозорец **Debug Configurations** натиснете с десен бутон върху **Remote Java Application** и изберете **New**. Променете **Port** на 9999 и натиснете **Apply**. Сега можете да натиснете **Debug**, за да се свържете със стартираното приложение. Ако спрете дебъг-сесията това няма да спре сървъра.

> **Съвет**: Можете да стартирате приложението си чрез `~run`, за да включите директната компилация при промяна на файла. По този начин scala темплейт файловете биват автоматично разпознати, когато създадете нов темплейт във `view` и автоматично компилирани, когато файлът бъде променен. Ако използвате само `run`, тогава трябва да обновите страницата в браузера (`Refresh`).

Ако правите някакви важни промени по приложенито ви, като например промяна на classpath, използвайте `eclipse` командата, за да генерирате конфигурационните файлове отново.

> **Съвет**: Не публикувайте конфигурационните файлове на Eclipse, когато работите в екип!

Генерираните конфигурационни файлове съдържат абсолютни референции към специфичната за вас инсталация. Когато работите в екип всеки разработчик трябва да държи конфигурационните файлове на Eclipse при себе си.

## IntelliJ

Intellij IDEA ви дава възможност да създавате Play приложения без да използвате терминала. Няма нужда да конфигурирате каквото и да било извън средата за разработка, SBT build tool се грижи за изтеглянето на подходящите библиотеки, разкриването на зависимости и създаването на проекта.

Преди да започнете да създавате Play приложения с IntelliJ IDEA се уверете, че актуалните плъгини за Scala (ако разработвате със Scala) и Play 2 са активирани в IntelliJ IDEA.

За да създадете Play приложение:

- Отворете ***New Project*** съветника, изберете ***Play 2.x*** в ***Scala*** секцията и натиснете ***Next***.
- Enter your project's information and click ***Finish***.

IntelliJ IDEA ще създаде празно приложение с SBT.

Можете и да импортирате вече съществуващ Play проект.

За да импортирате Play проект:

- Отворете Project съветника, изберете ***Import Project***.
- В прозореца изберете проекта, който искате да импортирате и натиснете ***OK***.
- На следващата страница от съветника изберете опцията ***Import project from external model***, изберете ***SBT project*** и натиснете ***Next***. 
- На следващата страница от съветника изберете допълнителни опции при импортирането и натиснете ***Finish***. 

Проверете структурата на проекта, уверете се, че необходимите зависимости са изтеглени.
Можете да използвате асистентите при писане на код, навигация и функциите за анализиране на код.

Можете да стартирате създаденото приложение и да видите резултата в браузера `http://localhost:9000`. 

За да стартирате Play приложение:
-	В project областта, натиснете с десен бутон върху приложението.
-	От контекстното меню изберете ***Run Pla2 App***.

Можете да стартирате дебъг сесия за всяко Play приложение чрез стандартните Run/Debug Configuration настройки.

За по-детайлна информация, вижте Play Framework 2.x урока тук:

<http://confluence.jetbrains.com/display/IntelliJIDEA/Play+Framework+2.0> 


## Netbeans

### Генериране на конфигурацията

За момента Play не поддържа генериране на Netbeans проекти.


## ENSIME

### Инсталиране на ENSIME

Следвайте инструкциите за инсталация на <https://github.com/ensime/ensime-emacs>

### Генериране на конфигурацията

Редактирайте файла project/plugins.sbt и добавете следния ред (първо проверете на <https://github.com/ensime/ensime-sbt> за най-новата версия на плъгина):

```
addSbtPlugin("org.ensime" % "ensime-sbt" % "0.1.5-SNAPSHOT")
```

Стартирайте Play:

```
$ activator
```

Напишете 'ensime generate' в play конзолата. Плъгинът ще генерира един .ensime файл в основата на Play проекта.

```
$ [MYPROJECT] ensime generate
[info] Gathering project information...
[info] Processing project: ProjectRef(file:/Users/aemon/projects/www/MYPROJECT/,MYPROJECT)...
[info]  Reading setting: name...
[info]  Reading setting: organization...
[info]  Reading setting: version...
[info]  Reading setting: scala-version...
[info]  Reading setting: module-name...
[info]  Evaluating task: project-dependencies...
[info]  Evaluating task: unmanaged-classpath...
[info]  Evaluating task: managed-classpath...
[info] Updating {file:/Users/aemon/projects/www/MYPROJECT/}MYPROJECT...
[info] Done updating.
[info]  Evaluating task: internal-dependency-classpath...
[info]  Evaluating task: unmanaged-classpath...
[info]  Evaluating task: managed-classpath...
[info]  Evaluating task: internal-dependency-classpath...
[info] Compiling 5 Scala sources and 1 Java source to /Users/aemon/projects/www/MYPROJECT/target/scala-2.9.1/classes...
[info]  Evaluating task: exported-products...
[info]  Evaluating task: unmanaged-classpath...
[info]  Evaluating task: managed-classpath...
[info]  Evaluating task: internal-dependency-classpath...
[info]  Evaluating task: exported-products...
[info]  Reading setting: source-directories...
[info]  Reading setting: source-directories...
[info]  Reading setting: class-directory...
[info]  Reading setting: class-directory...
[info]  Reading setting: ensime-config...
[info] Wrote configuration to .ensime
```

### Стартиране на ENSIME

От Emacs, стартирайте M-x ensime и следвайте инструкциите на екрана.

Това е всичко. Сега трябва да имате работеща проверка на типовете, допълване и т.н. Забележете, че ако добавяте нови библиотеки към play проекта, ще се наложи да извикате "ensime generate" отново и да рестартирате ENSIME.

### Повече информация

Вижте ENSIME README на <https://github.com/ensime/ensime-emacs>.
Ако имате въпроси, пишете на групата ensime на <https://groups.google.com/forum/?fromgroups=#!forum/ensime>.


## Всики Scala плъгини, ако са нужни

Scala е по-нов език за програмиране, така че функционалността се предлага под формата на плъгини, а не в основата на средите за разработка.

- Eclipse Scala IDE: <http://scala-ide.org/>
- NetBeans Scala Plugin: <https://java.net/projects/nbscala>
- IntelliJ IDEA Scala Plugin: <http://confluence.jetbrains.net/display/SCA/Scala+Plugin+for+IntelliJ+IDEA>
- Плъгинът в IntelliJ IDEA е в активна разработка и затова използването на nightly build може да ви даде допълнителна функционалност за сметка на някои малки недостатъци.
- Nika (11.x) Plugin Repository: <http://www.jetbrains.com/idea/plugins/scala-nightly-nika.xml>
- Leda (12.x) Plugin Repository: <http://www.jetbrains.com/idea/plugins/scala-nightly-leda.xml>
- IntelliJ IDEA Play plugin (наличен само за Leda 12.x): <http://plugins.intellij.net/plugin/?idea&pluginId=7080>
- ENSIME - Scala IDE Mode за Emacs: <https://github.com/aemoncannon/ensime>
(виж по-горе за инструкции относно ENSIME/Play)

&nbsp;

> **Напред:** 
>
> – [[Play уроци|Tutorials]]
