We can create document api in hjava by the help of javadoc. In the java file we must use comment `/**..**/` top post information for the class, method, constructor, fileds etc.

```java
package com.abc;  
/** This class is a user-defined class that contains one methods cube.*/  
public class M{  
  
/** The cube method prints cube of the given number */  
public static void  cube(int n){System.out.println(n*n*n);}  
}  
```

to generate de doc use this command
```cmd
javadoc M.jva
```