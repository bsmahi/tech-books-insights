# The Road to Java 25 Features - Verbose to Minimalistic

_On **September 16, 2025**, Java released the 25th version of the Java Development Kit (JDK), designated as
a **Long-Term Support (LTS)** release with support guaranteed for a minimum of eight years.
This release represents a significant advancement over previous versions, introducing a range of enhancements across
the **language, runtime, and tooling**.
JDK 25 notably extends support for artificial intelligence and machine learning workloads through improved APIs and
performance optimizations. These developments are aimed at increasing developer efficiency and facilitating the
development of robust, enterprise-grade applications._

_While this release boosts developer productivity, it also enhances the platform's performance, stability, and security.
Furthermore, it brings renewed confidence in Java’s ability to deliver a robust set of modern features designed to
support next-generation, AI-powered application development._

## Table of Contents

### 1. Language Enhancement Features

- [**Module Import Declarations**](#1-module-import-declarations)
- **Compact Source Files and Instance Main Methods**
- **Flexible Constructor Bodies**
- **(_Third Preview_) Primitive Types of Patterns, instanceof, and Switch**

### 2. Library Enhancement Features

- **Compact Source Files and Instance Main Methods**
- **Module Import Declarations**
- **Flexible Constructor Bodies**

### 3. Security Enhancement Features

- **Key Derivation Function API**
- **(_Preview_) PEM Encodings of Cryptographic Objects**

### 3. Performance Enhancement Features

- **Compact Object Headers**
- **Ahead-of-Time Command-Line Ergonomics**
- **Ahead-of-Time Method Profiling**

### 4. Monitoring Enhancement Features

- **Compact Object Headers**
- **Ahead-of-Time Command-Line Ergonomics**
- **Ahead-of-Time Method Profiling**

## Pre-Requisites

#### 1. Download **JDK 25** and Installation

- [Download Java 25](https://www.oracle.com/in/java/technologies/downloads/)
- [Java Installation Steps](https://docs.oracle.com/en/java/javase/25/install/overview-jdk-installation.html)

#### 2. Download IntelliJ IDEA

- [Windows](https://www.jetbrains.com/idea/download?section=windows)
- [MacOS](https://www.jetbrains.com/idea/download/?section=mac)
- [Linux](https://www.jetbrains.com/idea/download/?section=linux)

Firstly, we will explore about the **Language Enhancement Features**

### 1. Module Import Declarations

#### Feature Evolution Summary

- **[JEP 476 – Incubation](https://openjdk.org/jeps/476)**:  
  Introduced the feature as an incubator module, allowing early access for developers to try it and provide feedback.

- **[JEP 494 – Second Preview](https://openjdk.org/jeps/494)**:  
  The feature was refined based on feedback and made available as a preview (not enabled by default).

- **[JEP 511 – Finalized](https://openjdk.org/jeps/511)**:  
  The feature is standardized and fully integrated into **JDK 25**, no longer requiring preview flags or special
  modules.

#### Before JDK 25

Traditionally, classes and packages from `java.lang.*` are automatically imported by the compiler. However, nowadays,
most developers work with classes and interfaces such as **List, Set, Map, Stream, and Path**, which need to be
explicitly imported based on the packages being used in the class. For example:

```java
package com.bsmlabs.features.importdeclaration;

import java.util.List; // or import java.util.*;
import java.util.Map;
import java.util.function.Function; // or import java.util.function.*;
import java.util.stream.Collectors; // or import java.util.stream.*;

public class ImportBeforeJDK25 {

    public static void main(String[] args) {
        List<String> courses = List.of("Course On Java 25", "Spring Boot", "MicroServices", "DevOps");
        Map<String, String> coursesDetails = courses.stream()
                .collect(Collectors.toMap(s -> s.toUpperCase().substring(0, 1), Function.identity()));
        System.out.println(coursesDetails);

        Date date = new Date();
        System.out.println(date);
        java.sql.Date sqlDate = new java.sql.Date(date.getTime()); // with full qualified class name
        System.out.println(sqlDate);
    }
}
```

- These imports are **class-level or package-level**.
- Developers often used wildcard imports like import `java.util.*;` for convenience.
- Every class used from another package had to be imported (unless fully qualified).

#### In JDK 25

Importing all these classes and interfaces individually can sometimes be a daunting and repetitive task for developers.
It also increases the number of import statements in the file, leading to more verbose and cluttered code.

However, with **_Module Import Declarations_** feature, we can get rid of importing all the classes and packages just
importing single import statement. We have to follow the below convention for **Module Import Declaration**

For example

```java
import module java.base;
```

- `java.base` is the default module that contains most core Java classes like `java.util`, `java.lang`, `java.io`, etc.
- With the above single statement, you can import all the packages exported by the module `java.base`
- All the packages have been exported and included in the `module-info.java` file located at
  `<JDK_HOME>/java.base/module-info.java`.

#### Key Components of `module-info.java`

```java
module my.module {
    requires java.sql;
    exports java.lang;
    exports com.sun.crypto.provider to jdk.crypto.cryptoki;
    uses java.lang.System.LoggerFinder;
    provides java.nio.file.spi.FileSystemProvider with jdk.internal.jrtfs.JrtFileSystemProvider;
}
```

- `requires java.sql`: Dependency on another module with [transitive](https://en.wikipedia.org/wiki/Transitive_relation) in nature
- `exports java.lang;`: Publicly exposed package
- `exports com.sun.crypto.provider to jdk.crypto.cryptoki;`: Restricted export
- `uses java.lang.System.LoggerFinder;`: Service loader support
- `provides java.nio.file.spi.FileSystemProvider with jdk.internal.jrtfs.JrtFileSystemProvider;`: Provides an
  implementation of the `java.nio.file.spi.FileSystemProvider` interface using the class
  `jdk.internal.jrtfs.JrtFileSystemProvider`

For example module `java.base`

```java
module java.base {
    exports java.io;  // Publicly exposed package
    exports java.lang;
    exports java.lang.annotation;
    exports java.lang.classfile;
    exports java.lang.classfile.attribute;

    ...

    exports java.util;
    exports java.util.concurrent;
    exports java.util.concurrent.atomic;
    exports java.util.concurrent.locks;
    exports java.util.function;
    
    ...

    exports com.sun.crypto.provider to jdk.crypto.cryptoki; // Restricted export
    exports com.sun.security.ntlm to java.security.sasl;
    exports jdk.internal to jdk.incubator.vector;
    
    ...
    uses java.lang.System.LoggerFinder; // Service loader support
    uses java.net.ContentHandlerFactory;
    provides java.nio.file.spi.FileSystemProvider with jdk.internal.jrtfs.JrtFileSystemProvider;

```

- With `import module`, you no longer need to import individual classes like `List`, `Map`, `Collectors`, or `Function`
  if they are part of the imported module.
- You can still use fully qualified class names when necessary.
- NOTE: _it doesn’t work with unnamed modules_

```java
package com.bsmlabs.features.importdeclaration;

import module java.base;

public class ImportsInJDK25 {

    public static void main(String[] args) {
        List<String> courses = List.of("Course On Java 25", "Spring Boot with DevOps", "MicroServices", "DevOps");
        Map<String, String> coursesDetails = courses.stream()
                .collect(Collectors.toMap(s -> s.toUpperCase().substring(0, 1), Function.identity()));
        System.out.println(coursesDetails);

        Date date = new Date();
        System.out.println(date);
        java.sql.Date sqlDate = new java.sql.Date(date.getTime()); // with full qualified class name
        System.out.println(sqlDate);
    }
}
```

- `List`, `Map`, `Collectors`, `Function`, `Date` — all come from `java.base`, so importing the module covers them.
- `java.sql.Date` is NOT part of `java.base`, so it's used with its _**fully qualified name**_. If used frequently,
  you'd either:
    - Use `import java.sql.Date;`, or
    - Import the `import module java.sql` module
