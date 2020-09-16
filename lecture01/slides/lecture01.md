## Java As A Second Language
### Lecture 01

---
## What is Advanced Java?

---
## Kotlin

---
## Now serious

---
## About me
- Sergei    
- Software Engineer
- [https://github.com/rybalkinsd](https://github.com/rybalkinsd)

**Люблю зеленые билды**  

^^^
## About me
- Sasha
- Software Engineer
- [https://github.com/Al-p-i](https://github.com/Al-p-i)  

**Люблю смотреть, как другие работают**  

---
## Why Java?
...

---
## Java domain
- Web applications
- Middleware (Kafka/Spark/Flink)
- Android

---
## Plan
1. Basics, git, gradle
2. Classes, OOP
3. Collections, Exceptions, Generics, Streams
4. Web client, HTTP, REST  
5. Web server, Annotations  
6. Java+SQL, JDBC
7. Basic concurrency, Critical section  
8. Basic concurrency, Concurrent data structures  
9. GC, Heap
10. Experiments

---
## Оценка
- 10 занятий: теория + практика
- домашние задания после каждого занятия
- экзамена не будет
- оценка ставится в зависимости от процента сдачи домашних заданий  
  50% ─ 3  
  65% ─ 4  
  80% ─ 5  
  
---
# Setup

---
## Install JDK 14
Follow the instructions
https://sdkman.io/install

### Mac/Linux example:
```shell script
curl -s "https://get.sdkman.io" | bash
```
open new terminal and check if installation is successful
```shell script
sdk version
```
install JDK 14.0.2-adpt
```shell script
sdk install 14.0.2-adpt 
```
---
## Install IntelliJ IDEA Community
https://www.jetbrains.com/ru-ru/idea/download

---
## JShell

```shell script
jshell
```
![JShell](https://i.pinimg.com/originals/49/36/9d/49369d389233522a425f1327d8efecf2.jpg =250x250)
https://medium.com/swlh/how-to-use-jshell-to-improve-your-java-skills-170557d1d680

---
## Hello World!
```java
public class Hello{
  public static void main(String[] args){
    System.out.println("Hello, " + args[0] + "!");
  }
}
```
```shell script
javac Hello.java
```
```shell script
java Hello world 
```
---
## Byte code
```shell script
javap -c Hello.class

Compiled from "Hello.java"
public class Hello {
  public Hello();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: getstatic     #7                  // Field java/lang/System.out:Ljava/io/PrintStream;
       3: aload_0
       4: iconst_0
       5: aaload
       6: invokedynamic #13,  0             // InvokeDynamic #0:makeConcatWithConstants:(Ljava/lang/String;)Ljava/lang/String;
      11: invokevirtual #17                 // Method java/io/PrintStream.println:(Ljava/lang/String;)V
      14: return
}
```

---
## jar/.class
project containing several java files will compile to a bunch of .class files.
```shell script
java -cp Class1.class Class2.class
```
allows to add several .class files into *classpath*

*jar* utility can package them into single .jar file (java archive)

---
# Practice 1
Make pull request with HelloWorld to https://github.com/JavaAsASecondLanguage/JavaAsASecondLanguage

---
## 1. Install git
https://git-scm.com/

Make sure you understand git branches
https://www.atlassian.com/git/tutorials/using-branches

---
## 2. Fork the repository
https://github.com/JavaAsASecondLanguage/JavaAsASecondLanguage

---
## 3. Connect your fork with course repository
1. После форка в вашем github появится несинхронизованная копия (**fork**), **склонируем** ее и получим **рабочую копию** форка
```bash
> git clone https://github.com/YOUR_USERNAME/JavaAsASecondLanguage.git
```
2. Свяжем **рабочую копию вашего форка** с **репозиторием курса**, чтобы вы могли их синхронизировать и работать со свежей версией кода и проверим, что это сработало
```bash
> cd atom
> git remote add upstream https://github.com/JavaAsASecondLanguage/JavaAsASecondLanguage.git
> git remote -v
origin  https://github.com/YOUR_USERNAME/JavaAsASecondLanguage.git (fetch)
origin  https://github.com/YOUR_USERNAME/JavaAsASecondLanguage.git (push)
upstream https://github.com/JavaAsASecondLanguage/JavaAsASecondLanguage.git (fetch)
upstream https://github.com/JavaAsASecondLanguage/JavaAsASecondLanguage.git (push)
```
Теперь ваш fork будет известен git-у как **origin** (по умолчанию)  
а репозиторий курса - как **upstream** (только что настроили)  

---
# Make pull request with practice or homework

^^^

1. Update local cache of course repository
```shell script
git fetch upstream
```
2. Create new branch from upstream version
```shell script
git checkout -b lecture01 upstream/lecture01
```
^^^
## Make changes and push to your fork
git pull --rebase upstream lecture01
//...make your changes
git add MyFixedFile1.java MyFixedFile2.java
git commit -m 'Fixed all bugs and added new'
git push -u origin lecture01
^^^
#Make pull request

^^^

## git branch commands
Посмотреть текущую ветку
```bash
> git branch
master
```
взять последние сведения о ветках из **вашего форка**
```bash
> git fetch origin
```
взять последние сведения о ветках из **репозитория курса**
```bash
> git fetch upstream
```
переключиться на ветку **lecture1**
```bash
> git checkout lecture1
```
Создать ветку **new-branch**
```bash
> git checkout -b new-branch
```

^^^
## git commit commands
посмотреть состояние **рабочей копии**
```shell script
git status
...
```
добавить файл к будущему коммиту (stage)
```shell script
git add changed_file
```
зафиксировать изменения в **локальном репозитории**
```shell script
git commit -m 'Сообщение с пояснением коммита'
```
послать изменения в **ваш форк** на github
```shell script
git push origin branch-to-push
```

^^^
## git update commands
взять новые изменения из **вашего форка**
```shell script
git pull --rebase origin master
```
взять новые изменения из **репозитория курса**
```shell script
> git pull --rebase upstream master
```
**--rebase** заставляет **git** переносить ваши изменения поверх изменений других людей в этой ветке, которые они сделали, пока вы работали над этой веткой локально  
(возможны конфликты)

^^^
## Git editor setup
Для некоторых интерактивных действий (например изменение описания коммита) git использует редактор    
Редактор по умолчанию - **vim**  
Для тех, кто не знает, [как выйти из вима](https://stackoverflow.com/questions/11828270/how-to-exit-the-vim-editor), и пользуется **windows**, простой путь - сделать редактором notepad
```bash
> git config --global core.editor notepad
```

---
## Java Facts
- Java is cross-platform - 'Write Once, Run Anywhere' (WORA)
- Java is compiled to Byte Code, which is executed by Java Virtual Machine (JVM)
- automatic memory management (GC)
- Java is object-oriented, class-based
- static strong safe typization
- concurrent

---
## JDK/JRE/JVM
JDK - Java Development Kit
JRE - Java Runtime Environment
JVM - Java Virtual Machine
![JDK/JRE/JDM](https://gitpitch.com/pitchme/cdn/github/rybalkinsd/atom/lecture01/247D7B1E71608DAC7DA101FEA4A15E47DB76572E7B6CCF18EE72259B9FD843A725CBA98C0863316AEEE68A6E3D1AAD5F24CD996A9AE24F6965B66E828F65D3A10B6C056F53B14756197F66A494E7B96831ADBF0F585661AB/lecture01/presentation/assets/img/jdk-jre2.png)

---
## Licenses
[OpenJDK](https://openjdk.java.net/) - is a free implementation of JDK  
[Oracle JDK](https://www.oracle.com/ru/java/technologies/javase-downloads.html) - proprietary build based on OpenJDK with additional commercial tools and features. Free for development, paid for production  
[AdoptOpenJDK](https://adoptopenjdk.net/) - free OpenJDK build supported by Eclipse Foundation  
There are JDK more builds from different vendors, in most cases it is OpenJDK builds (with support and additional features)  

[HotSpot](https://openjdk.java.net/groups/hotspot/) - implementation of JVM inside OpenJDK project

---
## Versioning
New version is released each 6 months  
LTS (Long Term Support) version is released each 3 Years. Current LTS release is Java 11  

Funny Java Usage Statistics (2020)
https://www.jrebel.com/blog/2020-java-technology-report#JDK-distribution


---
## Gradle
//TODO

---
## Practice 1
Implement

---
## Practice 2
```java
boolean isPalindrome(String str){}
```

---

## Hrefs
Official documentation
https://docs.oracle.com/en/java/javase/14/