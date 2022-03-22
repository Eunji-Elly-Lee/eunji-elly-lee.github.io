---
layout:     post
title:      "Java Basics"
date:       2022-02-15
image:      java_code.jpg
categories: [Java]
---

<p class="intro"><span class="dropcap">J</span>ava is a high-level, object-oriented, general-purpose programming language developed in 1995 by James Gosling.</p>

One of Java's big features is that it is a platform-independent language. It means, when compiling Java code, a Java compiler generates a class file whose extension is .class that is byte code, which can run on any Java virtual machine regardless of the underlying computer architecture. Java is extensively used worldwide with this advantage and a feature of the English-like programming language.

<div style="text-align:center">
<img src="/assets/img/java_img/java_log.png" width="50%">
</div>

### Java's Basic Terminologies

These are descriptions of the five most basic terminologies used within Java programming.

- **Class**: A class is a template or blueprint that contains the behaviors and states of its instance.
- **Object**: An object is an instance of a class and has states and behaviors.
- **Method**: A method is a behavior of an object.
- **Constructor**: A constructor is a special kind of method which is a maker of an instance of an object.
- **Instance variable**: An instance variable is a state value of an object assigned.

### Java's Basic Syntax

This is a sample code of a Java file named HelloWorld.java We can see basic syntax from this code.

```java
package packagename;

import java.io.*;

public class HelloWorld {
    public static void main(String[] args) {
        // A constant variable
        final String SAY_HELLO = "Hello, world!";

        /*
        System.out.print("Hello, ");
        System.out.println("world!");
        */

        System.out.println(SAY_HELLO);
    }
}
```

- A program file name should exactly match the class name, and its extension is .java.
- If a class does not belong to any package, an entry of a package may not be mandatory.
- A Java statement ends with a semi-colon (;).
- Java is a case-sensitive language. A class name should start with an upper case letter, while a method name should start with a lower case letter.
- In the case of a compound word, the first letter of the following word is capitalized (e.g. camelCase). However, even if it is a compound word, a package name should be all in lower case letters, and a constant name should be all upper case letters and combined using underscore (_).
- The single-line comment puts two slashes (//) in front of a sentence. The multi-line comment is written between a combination of one slash and asterisk (/&#42;) and the other of one asterisk and slash (&#42;/).