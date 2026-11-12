We can create a Document API in HJava by the help of Javadoc. In the Java file, we must use comment `/**...*/` to document class, method, constructor, fields, etc.

```java
package com.abc;

/** This class is a user-defined class that contains one method: cube. */
public class M {

    /** The cube method prints the cube of the given number. */
    public static void cube(int n) {
        System.out.println(n * n * n);
    }
}
```

to generate documentation, use this command:

```cmd
javadoc M.java
```