
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

| Eclipse                  | IntelliJ
| -------------------------|---------
|+ Open and Free           |- Gratis
|- buggy and slow          |+ fast and smart (but non so much, not always)
|+ lot of plugin and tools |+ essential and well integrated, plugin
|+ Enterprise Development  |- Enterprise Developement Requires Ultimate Editon
|+ Javascript native?      |- Javascript requires WebStorms?
|+ Better null analisys    |+ External annotations

Per il momento ho scelto di continuare ad usare Eclipse perchè gratuita, più completa, e per l'analisi migliore dei null pointer sui generici: mi permette di scrivere codice 100% esente dai null pointer. Almeno finchè non mi risolvono l'issue 236740

## TODO: Altre cose da vedere

- [C and C++ software development toolkit for SOAP/XML](https://en.wikipedia.org/wiki/GSOAP)
- [free installer for Windows programs](https://jrsoftware.org/isinfo.php)
My Gity-Wiki

war ear aar

https://stackshare.io/
pubblicare quando avrò progetto gradle:
https://community.ptc.com/t5/Windchill/Windchill-tips-building-your-project-with-Maven/td-p/292254
https://community.ptc.com/t5/Windchill/Windchill-Java-development-using-Apache-Maven/td-p/314530
