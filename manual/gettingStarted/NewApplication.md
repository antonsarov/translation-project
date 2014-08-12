<!--- Copyright (C) 2009-2013 Typesafe Inc. <http://www.typesafe.com> -->
# Създаване на ново приложение

## Създаване на ново приложение чрез activator командата

Командата `activator` може да бъде използвана за създаване на ново Play приложение. Activator-ът дава възможност да изберете темплейт, на който да се базира новото ви приложение. За обикновените Play проекти използвайте `play-scala` (за Scala базирани Play приложения) и `play-java` (за Java базирани Play приложения).

> Забележете, че ако на този етап изберете темплейт за Scala или Java, това не означава, че не можете да промените езика по-късно. Например можете да създадете ново приложение със стандартния Java темплейт и да добавите Scala код когато решите.

За да създадете стандартно Play Scala приложение, изпълнете:

```bash
$ activator new my-first-app play-scala
```

За да създадете стандартно Play Java приложение, изпълнете:

```bash
$ activator new my-first-app play-java
```

И в двата случая можете да замените `my-first-app` с име по желание. Activator-ът ще използва това име и за името на директорията, в която да създаде приложението. Името може да бъде променяно на по-късен етап.

[[images/activatorNew.png]]

След като приложението е създадено, използвайте командата `activator` отново, за да влезете в [[Play конзолата|PlayConsole]].

```bash
$ cd my-first-app
$ activator
```

> Ако искате да използвате други Activator темплейти можете да изпълните `activator new`.  Ще бъдете попитани за име на приложението и ще имате възможност да разгледате темплейтите и да изберете подходящ.

## Създаване на ново приложение чрез графичния интерфейс на Activator-а (Activator UI)

Можете да създавате Play приложения и чрез Activator UI.  За тази цел изпълнете:

```bash
$ activator ui
```

Документация как да използвате Activator UI можете да намерите [тук](https://typesafe.com/activator/docs).

## Създаване на ново приложение без Activator-а

Възможно е да създадете ново Play приложение и без да инсталирате Activator-а, използвайки sbt директно.

> Първо инсталирайте [sbt](http://www.scala-sbt.org/), ако е нужно.

Създайте нова директория за приложението и конфигурирайте sbt build скрипта по следния начин.

В `project/plugins.sbt` добавете:

```scala
// The Typesafe repository 
resolvers += "Typesafe repository" at "http://repo.typesafe.com/typesafe/releases/"

// Use the Play sbt plugin for Play projects
addSbtPlugin("com.typesafe.play" % "sbt-plugin" % "%PLAY_VERSION%")
```

Уверете се, че сте заменили `%PLAY_VERSION%` с версията, която искате да използвате. Ако искате да използвате snapshot версия, трябва да добавите този resolver: 

```
// Typesafe snapshots
resolvers += "Typesafe Snapshots" at "http://repo.typesafe.com/typesafe/snapshots/"
```

В `build.sbt` за Java проекти:

```scala
name := "my-first-app"

version := "1.0"

lazy val root = (project in file(".")).enablePlugins(PlayJava)
```

...или Scala проекти:

```scala
name := "my-first-app"

version := "1.0.0-SNAPSHOT"

lazy val root = (project in file(".")).enablePlugins(PlayScala)
```

След това можете да стартирате sbt конзолата в директорията:

```bash
$ cd my-first-app
$ sbt
```

sbt ще зареди проекта и ще изтегли зависимостите.

> **Напред:** [[Анатомия на Play приложението|Anatomy]]
