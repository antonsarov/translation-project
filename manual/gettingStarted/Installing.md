<!--- Copyright (C) 2009-2013 Typesafe Inc. <http://www.typesafe.com> -->
# Инсталация на Play

## Предпоставки

За да стартирате Play framework-а ви трябва [JDK 6 или по-нова версия](http://www.oracle.com/technetwork/java/javase/downloads/index.html). 

> Ако използвате MacOS, Java е вградена. Ако използвате Linux, уверете се, че използвате или Sun JDK, или OpenJDK (а не gcj, което е Java командата по подразбиране при много Linux дистрибуции). Ако използвате Windows просто изтеглете и инсталирайте най-новата JDK версия.

Уверете се, че `java` and `javac` командите са достъпни в цялата система (можете да проверите това като напишете `java -version` и `javac -version` в командния прозорец). 

## Инсталация на Activator-а

Play се разпространява чрез т.нар. [Typesafe Activator](http://typesafe.com/activator). Typesafe Activator provides the build tool (sbt) that Play is built on, and also provides many templates and tutorials to help get you started with writing new applications.

Изтеглете най-новата [версия на Activator-а](https://typesafe.com/platform/getstarted) и екстрахирайте архива в директория, за която има права за четене **и писане**. (При стартирането на `activator` се създават някои файлове в директорията, така че не инсталирайте в `/opt`, `/usr/local` или на подобни места, които изискват специални права за достъп.)

## Добавяне на activator script-а към PATH променливата

За улеснение е добре да добавите инсталационната директория на Activator-а към системната променлива `PATH`. При UNIX системите това обикновено става така:

```bash
export PATH=/path/to/activator:$PATH
```

Под Windows трябва да промените глобалните системни променливи: добавете директорията към `PATH` променливата и не използвайте директория с интервали в името.

> Под UNIX се уверете, че скриптът `activator` е изпълняем.
> 
> Ако се налага, използвайте:
> ```bash
> chmod a+x /path/to/activator
> ```

> Ако сте зад прокси-сървър се уверете, че това е дефинирано: `set HTTP_PROXY=http://<host>:<port>` под Windows или `export  HTTP_PROXY=http://<host>:<port>` под UNIX.

## Уверете се, че командата activator съществува

От терминала стартирайте командата `activator -help`. 

```bash
$ activator -help
```

Ако всичко е инсталирано по ред ще видите помощния екран:

[[images/activator.png]]

Вече сте готови да създадете ново Play приложение.

> **Напред:** [[Създаване на ново приложение | NewApplication]]
