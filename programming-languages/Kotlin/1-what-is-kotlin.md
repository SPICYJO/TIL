# What is Kotlin? Why is it needed?

## How to run Kotlin?
- Install Kotlin and use `kotlinc` and `kotlin`(or `java`) command-line interfaces
  - `kotlin` command without any argument operates as REPL(read-eval-print loop)
  - Most of IDE now supports Kotlin - IntelliJ IDEA, Eclipse, ...
- Quick try is available at https://try.kotl.in without installation

## Features of Kotlin
<details>
    <summary>Interoperability</summary>
    
    Kotlin can be executed wherever environment that Java is executed, e.g. Server, Android and GUI applications. Kotlin can be compiled into not only Java but also Javascript so that it can be executed also on web browsers.
</details>
<details>
    <summary>Statically typed</summary>
    
    Kotlin is statically typed like Java. So it can detect type errors in compile-time not run-time. And it needs less effort for programmers to specify what type variables are, because most of time Kotlin's compiler can infer types of the variables, i.e. type inference. Statically typed langauges have the following advantages.

    - Performance
    - Reliability
    - Maintainability
    - Better support from tools (e.g. IDEs) 
</details>
<details>
    <summary>Functional programming & Object oriented programming</summary>
    
    Kotlin has lots of features that supports functional programming such as followings.

    - Functions are first-class, i.e. functions can be passed as a parameter of function calls or a result of function return.
    - Lambda functions
    - Data class that can easily make value object
    - Kotlin standard library provides APIs that supports functional styles for objects and collections
</details>
<details>
    <summary>Open source</summary>
    
    Kotlin language, compiler, library and tools are open source and can be used free. Kotlin is provided under Apache 2 license. Kotlin is being developed in GitHub.
</details>

## Philosophy of Kotlin
<details>
    <summary>Practicality</summary>
</details>
<details>
    <summary>Brevity</summary>
</details>
<details>
    <summary>Stability</summary>

    Langauge-level support to prevent NullPointerException, ClassCastException.
</details>
<details>
    <summary>Interoperability</summary>

    Java and Kotlin can be used together. Each of them can easily use the other's library and classes. One project can include both Java and Kotlin and it works completely fine.
</details>

## Kotlin tools
<details>
    <summary>Compiler</summary>

```bash
kotlinc <source file or directory> -include-runtime -d <jar name>
java -jar <jar name>
```

    - Kotlin source code(*.kt) -> Kotlin compiler -> *.class -> *.jar
    - Java source code(*.java) -> Java compiler -> *.class -> *.jar
    
    Build system such as Maven, Gradle and Ant can be also used with Kotlin.
</details>
<details>
    <summary>Kotlin plugins for IntelliJ IDEA and Android Studio</summary>

    Kotlin plugins are provided for latest versions of IntelliJ IDEA and Android Studio. 
</details>
<details>
    <summary>Kotlin REPL</summary>

    To use Kotlin REPL, type `kotlinc` command in terminal without any parameter. Kotlin REPL is also available in IntelliJ IDEA.
</details>
<details>
    <summary>Online playground</summary>
    
    - Try Kotlin online: https://try.kotl.in
    - Kotlin Koans: https://play.kotlinlang.org/koans
</details>
<details>
    <summary>Java-Kotlin converter</summary>

    Java and Kotlin can be easily converted using converter. There is a built-in converter in IntelliJ IDEA(Menu -> Code -> Convert Java File to Kotlin File). Converter is also available in Eclipse and web.
</details>