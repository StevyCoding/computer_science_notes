> [!question]- Question 18  : Can we write a try block without catch block ? 
Yes we can write a try block with  finally, but we cannot write tr block alone

>[!question]-  Question 19 How to handle multiple exception together ? 
> - ou can write multiple catch block or use pipe symbole to separate multiple exceptions²

>[!question]- Question 21 Difference between throw and throws keyword, And discuss Exception Progpagation 
> - throw is a keywork used to explicitly throw an exception in a program, inside a function or inside a block of code.
> - throws is a keyword which is used with the method signature to declare an exception which my get throw by the method while executing the code

 
>[!question]- Question 22  Exception handling with method oveririding
>parent child must have declared a throw exception to override the method with a throw exception
>if parent class declare an exception the child can declare no exception, declare same exception, declare narrower exception (more broader exception declaration than parent one is not allowed)
>

>[!question]- Question 23 Programs related to Exception handling and return keyword
> If you write anything after return statement / throw exception statement, then that will give Compile time as "Unreachable code"

>[!question]- Question 25 How to make custom check and unchecked exception
> custom unchecked exception : extends RuntimeException
> custom checked exception : extends Exception

>[!question]- Question 26 : What happen when you throw an exception from finally block ?*

>[!question]- Question 28 explain try-with resource
>introduce in Java 7 it allows us to declare resources which will be used inside the try block it assure us that the resource will be close closed after execution of this block.

>[!question]- Question 29 Why String is immutable ?
> 1. String pool
> 2. Security
> 3. Multi-threading
> 4. Caching
> 5. Class Loaders

>[!question]- Question 30 What does the equal() method of String so ?
>As we now Object is the parent method of all classes, and Object class has a equal() method that compare the reference of two objects, but String class has overridden this method and String class's equals() method method compares the contents of two strings.

>[!question]- Question 31 : Explain StringBuffer and StringBuilder
>StringBuffer provides thread-safety as all its method are synchronized, this makes performance of StringBuffer slower as compared to StringBuilder.

>[!question]- Question 32: Explain the output of below program related to equals() method of StringBuilder
>La sortie est "Not Equal" car les classes `StringBuffer` et `StringBuilder` ne **surchargent** pas les méthodes `equals()` et `hashcode()`.

>[!question]- Question 35: What is Maker interface ?

>[!question]- Question 37 : What is Comparable and Comparator ? :
>Bot Comparable and Comparator interfaces are used to sort the collection of objects.

>[!question]- Question 39 :Difference between Compartable and Comparator 

>[!question]- Question 43 Explain Auto-boxing and Un-boxing
>In Java 1.5, the concepts of Auto-boxing and Un-boxing were introduced to automatically convert primitive type to object and vice-versa

>[!question]- Question 45 : Can you pass primitve llong value in switch statement?
>No, it only work with 4 primitives and their wrappers, as well as enum type and String class :
>- byte and Byte
>- short and Short
>- char and Character
>- int and integer
>- enum
>- String

>[!question]- Question 46:  Explain static keyword in Java
> In Java a static member is a member of a class who's not associate with an instance of a class. Instead, the member belongs to the class itself.
> In java Static is apllicable for the following :
> - Variable
> - Method
> - Block
> - Nested class

>[!question] Question 48 :  What is a constructor chaining in Java ?
> When a constructor calls another contructor, it is know as constructore chaining. this can be done in two ways:

>[!question]- Question 49 : What is init block ?
>