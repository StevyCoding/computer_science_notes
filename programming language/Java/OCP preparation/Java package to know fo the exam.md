
Here’s a list of essential **Java packages** to know for the Java exam:

### **Core Packages**:
1. **`java.lang`**  
   - Automatically imported.
   - Includes core classes like `String`, `Math`, `System`, `Object`, `Thread`, `Exception`, etc.

2. **`java.util`**  
   - Includes utility classes such as:
     - `ArrayList`, `HashMap`, `HashSet`, `Collections`, `Random`, `Date`, `Optional`.

3. **`java.io`**  
   - For input and output operations:
     - `File`, `InputStream`, `OutputStream`, `BufferedReader`, `BufferedWriter`, `IOException`.

4. **`java.nio`**  
   - New I/O package for handling I/O efficiently:
     - `Path`, `Files`, `StandardOpenOption`, `FileSystems`.

5. **`java.net`**  
   - For networking:
     - `URL`, `Socket`, `HttpURLConnection`, `InetAddress`.

6. **`java.time`**  
   - For working with dates and times (introduced in Java 8):
     - `LocalDate`, `LocalTime`, `LocalDateTime`, `ZoneId`, `Duration`, `Period`.

7. **`java.math`**  
   - For mathematical operations:
     - `BigDecimal`, `BigInteger`, `MathContext`.

### **Concurrency and Multithreading**:
8. **`java.util.concurrent`**  
   - For concurrency utilities:
     - `ExecutorService`, `Future`, `CompletableFuture`, `CountDownLatch`, `Semaphore`.

9. **`java.util.stream`**  
   - For functional programming:
     - `Stream`, `Collectors`, `IntStream`, `Optional`.

### **Annotations**:
10. **`java.lang.annotation`**  
   - For creating and managing annotations:
     - `Annotation`, `Retention`, `Target`.

### **Exceptions and Error Handling**:
11. **`java.lang.reflect`**  
   - For reflection (inspecting classes, methods at runtime):
     - `Field`, `Method`, `Constructor`.

### **Packages to Focus on for the Exam**:
- **`java.lang`** (core classes, exceptions)
- **`java.util`** (collections, streams)
- **`java.time`** (date/time handling)
- **`java.io`** (I/O operations)
- **`java.util.concurrent`** (multithreading basics)

### **`java.util.Date` (Deprecated but Still Important)**

- **Classes to Know**:
    
    - `java.util.Date`: Represents date and time.
    - `java.util.Calendar`: More flexible date/time handling (though somewhat clunky).
    - `java.text.SimpleDateFormat`: For formatting dates.
- **Why It's Important**:
    
    - **Legacy code**: You may encounter `Date` and `Calendar` in older systems or questions.
    - Basic knowledge is needed for **converting between old (`Date`) and new (`java.time`) APIs**

These packages cover a wide range of topics commonly tested on Java exams, such as **collections**, **concurrency**, **streams**, and **exception handling**.