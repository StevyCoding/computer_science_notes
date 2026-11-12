# Exception Handling in Java 🚀

Exception Handling in Java is one of the powerful mechanisms to handle runtime errors, so that the normal flow of the application can be maintained.

## Types of Exception

1.  Checked Exception
2.  Unchecked Exception
3.  Error 🚨

-   Checked Exceptions are checked at Compile time.
-   Unchecked exceptions occur at runtime.
-   Errors are irrecoverable (e.g., OutOfMemoryError, VirtualMachineError, etc.).

## Java Exception Keywords

| Keyword | Description |
|---|---|
| `try` | The "try" keyword is used to specify a block where we should place exception code. It means we can't use a `try` block alone. The `try` block must be followed by either `catch` or `finally`. |
| `catch` | The "catch" block is used to handle the exception. It must be preceded by a `try` block, which means we can't use a `catch` block alone. It can be followed by a `finally` block later. |
| `finally` | The "finally" block is used to execute necessary code of the program. It is executed whether an exception is handled or not. |
| `throw` | The "throw" keyword is used to throw an exception. |
| `throws` | The "throws" keyword is used to declare exceptions. It specifies that there may occur an exception in the method. It doesn't throw an exception. It is always used with the method signature. 

```javascript
// Example Code (Illustrative)
try {
  // Code that might throw an exception
} catch (e) {
  // Handle the exception
} finally {
  // Code to execute regardless of exception
}
```