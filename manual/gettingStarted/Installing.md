<!--- Copyright (C) 2009-2013 Typesafe Inc. <http://www.typesafe.com> -->
# Инсталация на Play

## Предпоставки

За да стартирате Play framework-а ви трябва [JDK 6 или по-нова версия](http://www.oracle.com/technetwork/java/javase/downloads/index.html). 

> Ако използвате MacOS, Java е вградена. Ако използвате Linux, уверете се, че използвате или Sun JDK, или OpenJDK (а не gcj, което е Java командата по подразбиране при много Linux дистрибуции). Ако използвате Windows просто изтеглете и инсталирайте най-новата JDK версия.

Уверете се, че `java` and `javac` командите са достъпни в цялата система (можете да проверите това като напишете `java -version` и `javac -version` в командния прозорец). 

## Инсталация на Activator-а

Play се разпространява чрез т.нар. [Typesafe Activator](http://typesafe.com/activator). Typesafe Activator provides the build tool (sbt) that Play is built on, and also provides many templates and tutorials to help get you started with writing new applications.

Download the latest [Activator distribution](https://typesafe.com/platform/getstarted) and extract the archive to a location where you have both read **and write** access. (Running `activator` writes some files to directories within the distribution, so don't install to `/opt`, `/usr/local` or anywhere else you’d need special permission to write to.)

## Add the activator script to your PATH

For convenience, you should add the Activator installation directory to your system `PATH`. On UNIX systems, this means doing something like:

```bash
export PATH=/path/to/activator:$PATH
```

On Windows you’ll need to set it in the global environment variables. This means update the `PATH` in the environment variables and don't use a path with spaces.

> If you’re on UNIX, make sure that the `activator` script is executable.
> 
> Otherwise do a:
> ```bash
> chmod a+x /path/to/activator
> ```

> If you're behind a proxy make sure to define it with `set HTTP_PROXY=http://<host>:<port>` on Windows or `export  HTTP_PROXY=http://<host>:<port>` on UNIX.

## Check that the activator command is available

From a shell, launch the `activator -help` command. 

```bash
$ activator -help
```

If everything is properly installed, you should see the basic help:

[[images/activator.png]]

You are now ready to create a new Play application.

> **Напред:** [[Създаване на ново приложение | NewApplication]]
