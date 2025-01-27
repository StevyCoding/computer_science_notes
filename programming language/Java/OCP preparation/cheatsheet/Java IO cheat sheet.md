

### Java I/O Cheat Sheet
![[Java I_O Cheatsheet for OCP 17 Exam.png]]


---

#### 1. I/O Overview

- Java I/O is used to handle input and output operations like reading from and writing to files, network connections, or in-memory data.
- Java I/O is categorized into Streams and Readers/Writers.

---

#### 2. I/O Streams

##### 2.1. Stream Types

- **Byte Streams** (handles raw binary data)
    - `InputStream`: Read bytes.
    - `OutputStream`: Write bytes.
- **Character Streams** (handles character data, encoded in UTF-8 or UTF-16)
    - `Reader`: Read characters.
    - `Writer`: Write characters.

##### 2.2. Common Stream Classes

- **Byte Streams:**
    - `FileInputStream` / `FileOutputStream`
    - `BufferedInputStream` / `BufferedOutputStream`
    - `ObjectInputStream` / `ObjectOutputStream`
- **Character Streams:**
    - `FileReader` / `FileWriter`
    - `BufferedReader` / `BufferedWriter`
    - `PrintWriter`

---

#### 3. File I/O (java.nio.file)

The `java.nio.file` package provides better file handling with Path, Files, and other utility classes.

##### 3.1. Basic File Operations

- `Files.copy(Path source, Path target)`: Copy a file.
- `Files.delete(Path path)`: Delete a file.
- `Files.exists(Path path)`: Check if a file exists.
- `Files.createFile(Path path)`: Create a new file.

##### 3.2. Path Class

- **Path** represents the location of a file or directory.
    - `Path path = Paths.get("file.txt")`
    - `path.getFileName()`: Get the name of the file.
    - `path.toAbsolutePath()`: Get absolute path.

##### 3.3. Files Class

- `Files.readAllLines(Path path)`: Read all lines from a file.
- `Files.write(Path path, Iterable<? extends CharSequence> lines)`: Write lines to a file.

---

#### 4. Reading and Writing Files

##### 4.1. Reading Files

- **Byte Stream (InputStream):**
    
    ```java
    InputStream in = new FileInputStream("file.txt");
    int data = in.read();
    in.close();
    ```
    
- **Character Stream (Reader):**
    
    ```java
    Reader reader = new FileReader("file.txt");
    int data = reader.read();
    reader.close();
    ```
    

##### 4.2. Writing Files

- **Byte Stream (OutputStream):**
    
    ```java
    OutputStream out = new FileOutputStream("file.txt");
    out.write(data);
    out.close();
    ```
    
- **Character Stream (Writer):**
    
    ```java
    Writer writer = new FileWriter("file.txt");
    writer.write(data);
    writer.close();
    ```
    

##### 4.3. Buffered I/O

- Improves efficiency by reducing the number of I/O operations.
    
    ```java
    BufferedReader reader = new BufferedReader(new FileReader("file.txt"));
    BufferedWriter writer = new BufferedWriter(new FileWriter("file.txt"));
    ```
    

---

#### 5. Object Serialization

- **Serializable** interface marks a class as serializable.
    
    ```java
    public class MyClass implements Serializable {
        private int id;
        private String name;
    }
    ```
    
- **Object Streams** allow serialization/deserialization of objects:
    
    ```java
    ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("object.dat"));
    out.writeObject(myObject);
    out.close();
    
    ObjectInputStream in = new ObjectInputStream(new FileInputStream("object.dat"));
    MyClass myObject = (MyClass) in.readObject();
    in.close();
    ```
    

---

#### 6. PrintWriter

- Used for printing formatted text to files or consoles.
    
    ```java
    PrintWriter writer = new PrintWriter(new FileWriter("file.txt"));
    writer.println("Hello, World!");
    writer.close();
    ```
    

---

#### 7. NIO (New I/O)

##### 7.1. NIO Classes

- **Paths**: Represents file paths.
- **Files**: Utility class for file operations (copy, move, delete, etc.).
- **FileChannel**: Provides low-level file operations.

##### 7.2. FileChannel

- Used for reading and writing files with performance optimizations.
    
    ```java
    FileChannel channel = new RandomAccessFile("file.txt", "rw").getChannel();
    ByteBuffer buffer = ByteBuffer.allocate(1024);
    channel.read(buffer);
    channel.close();
    ```
    

##### 7.3. ByteBuffer

- A container for data used in NIO.
    
    ```java
    ByteBuffer buffer = ByteBuffer.allocate(256);
    buffer.put("Hello".getBytes());
    buffer.flip();
    ```
    

---

#### 8. File Visitors

##### 8.1. Walk File Tree

- Walk through directory trees using `Files.walkFileTree`.
    
    ```java
    Files.walkFileTree(Paths.get("/path"), new SimpleFileVisitor<Path>() {
        @Override
        public FileVisitResult visitFile(Path file, BasicFileAttributes attrs) {
            System.out.println(file);
            return FileVisitResult.CONTINUE;
        }
    });
    ```
    

---

#### 9. I/O Exceptions

##### 9.1. Handling I/O Exceptions

- **IOException** is the parent exception for file I/O errors.
    
    ```java
    try {
        Files.copy(Paths.get("source.txt"), Paths.get("target.txt"));
    } catch (IOException e) {
        e.printStackTrace();
    }
    ```
    

##### 9.2. Checked vs. Unchecked Exceptions

- **Checked**: Must be caught or declared (e.g., `IOException`).
- **Unchecked**: Runtime exceptions do not need to be declared or caught.

---

#### 10. Stream Operations (Java 8 and above)

##### 10.1. Streams

- Streams in Java 8+ can be used with file I/O to process large volumes of data efficiently.
    
    ```java
    List<String> lines = Files.lines(Paths.get("file.txt"))
                               .filter(line -> line.contains("example"))
                               .collect(Collectors.toList());
    ```
    

##### 10.2. Using `Files.lines()`

- Efficiently read large files line by line.
    
    ```java
    try (Stream<String> lines = Files.lines(Paths.get("file.txt"))) {
        lines.forEach(System.out::println);
    }
    ```
    

---

#### 11. Important I/O Methods

|Method|Description|
|---|---|
|`Files.copy(Path, Path)`|Copies a file from source to target|
|`Files.move(Path, Path)`|Moves or renames a file|
|`Files.delete(Path)`|Deletes a file|
|`Files.exists(Path)`|Checks if a file exists|
|`Files.readAllLines(Path)`|Reads all lines from a file|
|`Files.write(Path, List<String>)`|Writes a list of strings to a file|
|`Files.walk(Path)`|Traverses a directory tree|

---

#### 12. Key Java I/O Interfaces

- **InputStream / OutputStream**: Byte-based input/output.
- **Reader / Writer**: Character-based input/output.
- **Serializable**: For object serialization.
- **Closeable**: Interface for resources that need closing.

---

This cheat sheet should cover the essential topics for Java I/O in **Java 17 OCP exam**. For any specific topic, try practicing related questions or scenarios for better comprehension.