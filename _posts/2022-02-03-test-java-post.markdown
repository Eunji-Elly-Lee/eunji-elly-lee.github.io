---
layout:     post
title:      "About Java"
date:       2022-02-14
image:      java_code.jpg
categories: [Java]
---

<p class="intro"><span class="dropcap">J</span>ava is a high-level, object-oriented, general-purpose programming language developed in 1995 by James Gosling.</p>

One of Java's big features is that it is a platform-independent language. When compiling Java code, a Java compiler generates a class file (.class) that is byte code, which can run on any Java virtual machine regardless of the underlying computer architecture.

![Java logo](https://w.namu.la/s/95f3898eb4996f6ba5a3930b212b295da56e062e9427da87331a510d3d868bd81f24d10d242ca0d93f4ad94053b9321549cb4590ea815a8d39ba92cde1a7da442da8503354444ceb7fa3f72486d3d3d278c082ed6739920f027739705079953f)

**Java's core concepts**

- Object: An object is an instance of a class and has states and behaviors.
- Class: A class is a template or blueprint that contains the behaviors and states of its instance.
- Method: A method is a behavior of an object.
- Instance variable: An instance variable creates a state of an object with its assigned value.

**Java's basic syntax**

This is the code of a Java file named HelloWorld.java

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
- The single-line comment puts two forward slashes (//) in front of a sentence. The multi-line comment is written between a combination of one forward-slash and asterisk (/* ) and the other of one asterisk and forward-slash ( */).