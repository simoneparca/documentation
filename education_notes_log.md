
# SQL ID 

- [Oracle: select ID_SEQ.nextval from DUAL](https://stackoverflow.com/questions/30818614/how-to-get-sequence-nextval-from-sql-in-jdbc)
- [insert into mytable(x,y) values (1,2) returning id into v_id;](https://stackoverflow.com/questions/3657565/select-ident-current-tablename-in-oracle)
- [SQLServer 2005+: INSERT INTO aspnet_GameProfiles(UserId,GameId) OUTPUT INSERTED.ID VALUES(@UserId, @GameId), myCommand.ExecuteScalar()](https://stackoverflow.com/questions/5228780/how-to-get-last-inserted-id)
- [SQLServer: If table has a column of type INT IDENTITY (or BIGINT IDENTITY), INSERT INTO dbo.YourTable(columns....) VALUES(...) SELECT SCOPE_IDENTITY()](https://stackoverflow.com/questions/9477502/get-the-last-inserted-row-id-with-sql-statement)
- [Approfondimento del precedente](https://stackoverflow.com/questions/42648/best-way-to-get-identity-of-inserted-row)
- https://stackoverflow.com/questions/40168310/create-a-sql-sequence-programmatically-in-java
- https://stackoverflow.com/questions/39838157/sequence-next-value-in-select-statement

# 2020-03-28 Approfondimenti su Gradle (e Maven)

- https://www.baeldung.com/ant-maven-gradle
- https://www.vogella.com/tutorials/EclipseGradle/article.html
- https://gradle.org/guides/#getting-started
- https://docs.gradle.org/current/userguide/userguide.html
- [Use ant in Gradle](https://docs.gradle.org/current/userguide/ant.html)
- https://docs.gradle.org/current/userguide/application_plugin.html
- https://docs.gradle.org/current/userguide/composite_builds.html da approfondire
- https://docs.gradle.org/current/userguide/declaring_repositories.html
- https://docs.gradle.org/current/userguide/eclipse_plugin.html
- https://docs.gradle.org/current/userguide/maven_plugin.html
- https://docs.gradle.org/current/userguide/multi_project_builds.html complesso
- https://docs.gradle.org/current/userguide/publishing_setup.html ok
- https://docs.gradle.org/current/userguide/publishing_maven.html
- https://docs.gradle.org/current/userguide/writing_build_scripts.html

## 2020-04-01

- https://try.kotlinlang.org/
- https://blog.heckel.io/2014/05/29/gradle-create-windows-installers-debian-packages-manage-a-ppa-and-optional-sub-projects/

Una volta creato un progetto tramite IDE, viene scaricato automaticamente anche Gradle. Per usarlo a linea di comando (esempio):  
<code>
set path=%path%;%USERPROFILE%\.gradle\wrapper\dists\gradle-5.4-bin\59btlbly62hzjka9h1c4c86kd\gradle-5.4\bin
</code>

## 2020-04-04 IntelliJ

Ho iniziato a studiare questa IDE perchè sembra ben pensata, di concezione innovativa, essenziale ma abbastanza completa, può aiutare a svolgere il lavoro di sviluppo più velocemente. Prodotta da [JetBrains](https://www.jetbrains.com/), azienda che ha dimostrato una notevole competenza, e che ha creato anche il linguaggio Kotlin e varie altre soluzioni innovative.  
Il mio interesse è stato rivolto soprattutto alla possibilità di usare le external annotations, per risolvere il fatto che nel mio attuale impiego non apprezzano e non comprendono l'utilità delle verifiche formali sul codice.

- https://www.jetbrains.com/help/idea/external-annotations.html
- https://youtrack.jetbrains.com/issue/IDEA-65566  Allow 'NotNull' as the default element behavior for a given class or package
- https://youtrack.jetbrains.com/issue/IDEA-125281 Support @TypeQualifierDefault for nullable/notnull warnings
- 2013-06-05 https://stackoverflow.com/questions/16938241/is-there-a-nonnullbydefault-annotation-in-idea Non c'è, devi usare @TypeQualifierDefault, vedi 125281
- 2014-04 [JSR 308 Explained: Java Type Annotations](https://www.oracle.com/technical-resources/articles/java/ma14-architect-annotations.html)
- 2015-08-14 https://youtrack.jetbrains.com/issue/IDEA-143937#comment=27-1091565  
2015-09-08 https://youtrack.jetbrains.com/issue/IDEA-144920 Please allow custom @NonnullByDefault annotations
- 2019-07-14 https://youtrack.jetbrains.com/issue/IDEA-218246 False-positive @NotNullByDefault must be initialized, non rilevante
- 2020-04-04 https://youtrack.jetbrains.com/issue/IDEA-236740 NonNullByDefault not working with Generic Types, aperto da me.
https://stackoverflow.com/questions/48349393/can-i-make-intellij-nonnull-nullable-annotations-act-like-eclipse

## 4/4/2020
### main IDE feature compared:

 | Eclipse                   | IntelliJ                                           |
 | ------------------------- | -------------------------------------------------- |
 | + Open and Free           | - Gratis                                           |
 | - buggy and slow          | + fast and smart (but non so much, not always)     |
 | + lot of plugin and tools | + essential and well integrated, plugin            |
 | + Enterprise Development  | - Enterprise Developement Requires Ultimate Editon |
 | + Javascript native?      | - Javascript requires WebStorms?                   |
 | + Better null analisys    | + External annotations                             |

Per il momento ho scelto di continuare ad usare Eclipse perchè gratuita, più completa, e per l'analisi migliore dei null pointer sui generici: mi permette di scrivere codice 100% esente dai null pointer. Almeno finchè non mi risolvono l'issue 236740

## 2020-04-16

- [Corso Ongaro lezione 1][ongaro]
- [Corso full-stack Udemy][studyeasy]

[ongaro]: https://www.ongaro-corsi.com/3pes9j1b
[studyeasy]: [https://www.udemy.com/course/full-stack-java-developer-java/learn/lecture/12951764#overview]

## 2020-04-17

- [Corso full-stack Udemy][studyeasy]

## 2020-04-18

- [Corso Ongaro lezione 2][ongaro]
- [Corso full-stack Udemy][studyeasy]

## 2020-11-13

- Working with Configuration Files.docx
- [Inizio training / test su codility](https://app.codility.com/programmers/)
- [Azure DevOps - Create an Organization](https://github.com/MicrosoftDocs/azure-devops-docs/blob/master/docs/organizations/accounts/create-organization.md)
- [Azure DevOps - Create a project](https://docs.microsoft.com/en-us/azure/devops/organizations/projects/create-project?view=azure-devops&tabs=preview-page

## 2020-11-19

- https://angular.io/start#getting-started-with-a-basic-angular-app
- https://stackblitz.com/edit/angular-parsi-test
- [Publish Markdown files from Git repository to wiki](azure-devops-docs/publish-repo-to-wiki.md)

# 2020-11-29

- [Create a project in Azure DevOps](azure-devops-docs/create-project.md)
- [Markdown syntax for files, widgets, and wikis](azure-devops-docs/markdown-guidance.md)
- [Create a readme for your Git repo](azure-devops-docs/create-a-readme.md)
- [Share your project vision & view project activity](azure-devops-docs/project-vision-status.md)
- [Clone and update wiki content offline](azure-devops-docs/iki-update-offline.md)
- [Differences between provisioned and published wiki](azure-devops-docs/provisioned-vs-published-wiki.md)

## WIP

- https://docs.microsoft.com/en-us/azure/devops/artifacts/overview

## TODO: Altre cose da vedere

My Gity-Wiki

war ear aar

https://stackshare.io/
pubblicare quando avrò progetto gradle:
- https://community.ptc.com/t5/Windchill/Windchill-tips-building-your-project-with-Maven/td-p/292254
- https://community.ptc.com/t5/Windchill/Windchill-Java-development-using-Apache-Maven/td-p/314530
- http://www.gwtproject.org/
- https://www.sonarqube.org/downloads/

- [Atom è un editor di testo e IDE open source e sviluppato da GitHub, basato su Chromium ed è scritto in CoffeeScript, il che gli permette di essere eseguito su qualsiasi piattaforma supportata da Chromium. Una delle sue caratteristiche principali è la possibilità di sviluppare pacchetti utilizzando Node.js. Atom possiede inoltre supporto al sistema di controllo di versione Git.](https://atom.io/docs)
- Electron (precedentemente noto come Atom Shell) è un framework open source gestito e ospitato da GitHub. Electron consente lo sviluppo della GUI di applicazioni desktop utilizzando tecnologie Web: combina il motore di rendering Chromium e il runtime Node.js. Electron è il principale framework per la GUI dietro alcuni importanti progetti open source tra cui Atom, GitHub Desktop, Light Table, Visual Studio Code, WordPress Desktop

- https://developer.mozilla.org/it/docs/Learn/Front-end_web_developer
  - 1 HTML, HTML5
  - 1 CSS (SASS/LESS come plus)
    - https://developer.mozilla.org/en-US/docs/Learn/HTML
  - 1 JavaScript (TypeScript come plus)
    - https://developer.mozilla.org/en-US/docs/Web/JavaScript
    - https://www.typescriptlang.org/docs/
    - 2 NodeJS (Javascript e/o Typescript) runtime di JavaScript Open source multipiattaforma
- 2 [Angular](https://angular.io/docs) versione>5
    - https://angular.io/tutorial#tour-of-heroes-app-and-tutorial
    - https://angular.io/guide/architecture-components#template-syntax
    - https://angular.io/guide/architecture-components#introduction-to-components-and-templates
    - https://angular.io/guide/component-interaction#component-interaction
    - https://angular.io/start/start-routing#adding-navigation
    - https://angular.io/start/start-deployment#deploying-an-application
    - https://angular.io/guide/setup-local#setting-up-the-local-environment-and-workspace
- 1 VueJS
- 1 ReactJS
- 1 Rest
- 2 [open source end-to-end software development platform](GitLab.org)
- 1 Python
- 1 Database relazionali
- 1 Database No Sql
- 1 Architetture SOA & MicroServices
- 1 Paradigmi OOP
- 2 TDD-BDD-test automatici
- 1 jQuery
- Preprocessori, task runner o module bundler (Grunt, Gulp, Webpack)
- Responsive development
- https://www.codecademy.com/
- [C and C++ software development toolkit for SOAP/XML](https://en.wikipedia.org/wiki/GSOAP)
- [Free installer for Windows programs](https://jrsoftware.org/isinfo.php)

