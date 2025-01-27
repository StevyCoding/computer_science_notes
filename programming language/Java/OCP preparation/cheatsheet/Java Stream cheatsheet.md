
Here’s the corrected version without bold on titles:

### Java Streams Cheat Sheet (Java 17 OCP)

---
![[Java Stream Cheatsheet for Java 17 OCP.png]]
#### 1. What is a Stream?

- A **Stream** is a sequence of elements that can be processed in parallel or sequentially.
- Streams allow you to **process collections** in a functional way, making it easier to perform complex operations like filtering, mapping, and reducing.

---

#### 2. Stream Interfaces

- **Stream**: The core stream interface for non-primitive types.
- **IntStream**, **LongStream**, **DoubleStream**: Specialized versions of the stream interface for handling primitive data types efficiently.

---

#### 3. Stream Pipeline

A stream pipeline consists of:

1. **Source**: Data source (e.g., collection, array, I/O channel).
2. **Intermediate Operations**: Transform the data (e.g., `filter()`, `map()`).
3. **Terminal Operations**: Trigger the processing of the stream and produce a result (e.g., `collect()`, `forEach()`).

---

#### 4. Stream Creation

- **From Collections**:
    
    ```java
    List<String> list = Arrays.asList("apple", "banana", "cherry");
    Stream<String> stream = list.stream(); // Sequential Stream
    ```
    
- **From Arrays**:
    
    ```java
    String[] array = {"apple", "banana", "cherry"};
    Stream<String> stream = Arrays.stream(array);
    ```
    
- **From Specific Values**:
    
    ```java
    Stream<String> stream = Stream.of("apple", "banana", "cherry");
    ```
    
- **From a Range** (for primitive types):
    
    ```java
    IntStream stream = IntStream.range(1, 10); // Exclusive of 10
    ```
    

---

#### 5. Intermediate Operations

Intermediate operations return a new stream and are **lazy** (only executed when a terminal operation is invoked).

|**Operation**|**Description**|**Example**|
|---|---|---|
|`filter(Predicate)`|Filters elements based on a condition.|`stream.filter(s -> s.startsWith("a"))`|
|`map(Function)`|Transforms each element into another form (e.g., applying a function).|`stream.map(String::toUpperCase)`|
|`flatMap(Function)`|Flattens nested streams into a single stream.|`stream.flatMap(s -> Arrays.stream(s.split(" ")))`|
|`distinct()`|Removes duplicate elements.|`stream.distinct()`|
|`sorted()`|Sorts the elements in natural order or by a custom comparator.|`stream.sorted()`|
|`peek(Consumer)`|Allows you to perform an action on each element (mainly for debugging).|`stream.peek(System.out::println)`|
|`limit(long)`|Limits the stream to a specified number of elements.|`stream.limit(3)`|
|`skip(long)`|Skips the first `n` elements of the stream.|`stream.skip(2)`|

---

#### 6. Terminal Operations

Terminal operations are **eager** and produce a result or a side-effect (e.g., collect the elements into a list, print them).

|**Operation**|**Description**|**Example**|
|---|---|---|
|`collect(Collector)`|Collects the elements into a collection (e.g., List, Set).|`stream.collect(Collectors.toList())`|
|`forEach(Consumer)`|Performs an action for each element of the stream.|`stream.forEach(System.out::println)`|
|`reduce(BinaryOperator)`|Performs a reduction on the elements using an associative accumulation function.|`stream.reduce((a, b) -> a + b).orElse("default")`|
|`count()`|Returns the number of elements in the stream.|`stream.count()`|
|`anyMatch(Predicate)`|Checks if any elements match the given predicate.|`stream.anyMatch(s -> s.startsWith("a"))`|
|`allMatch(Predicate)`|Checks if all elements match the given predicate.|`stream.allMatch(s -> s.length() > 3)`|
|`noneMatch(Predicate)`|Checks if no elements match the given predicate.|`stream.noneMatch(s -> s.isEmpty())`|
|`findFirst()`|Returns the first element of the stream (if present).|`stream.findFirst()`|
|`findAny()`|Returns any element of the stream (if present).|`stream.findAny()`|
|`toArray()`|Converts the stream into an array.|`stream.toArray()`|

---

#### 7. Collectors

Collectors are used to accumulate the elements of a stream into collections, summarizers, or other formats.

|**Collector**|**Description**|**Example**|
|---|---|---|
|`Collectors.toList()`|Collects elements into a `List`.|`stream.collect(Collectors.toList())`|
|`Collectors.toSet()`|Collects elements into a `Set`.|`stream.collect(Collectors.toSet())`|
|`Collectors.joining()`|Joins the elements into a single `String`.|`stream.collect(Collectors.joining(", "))`|
|`Collectors.groupingBy()`|Groups elements based on a classifier function.|`stream.collect(Collectors.groupingBy(String::length))`|
|`Collectors.partitioningBy()`|Partitions elements based on a predicate.|`stream.collect(Collectors.partitioningBy(s -> s.length() > 3))`|
|`Collectors.counting()`|Counts the number of elements in a stream.|`stream.collect(Collectors.counting())`|
|`Collectors.summarizingInt()`|Collects statistical data (e.g., count, sum, average) of `int` elements.|`stream.collect(Collectors.summarizingInt(String::length))`|
|`Collectors.reducing()`|Performs a reduction of the stream elements into a single value.|`stream.collect(Collectors.reducing((a, b) -> a + b))`|

---

#### 8. Lazy vs Eager Evaluation

- **Lazy**: Intermediate operations are lazy and are only executed when a terminal operation is invoked.
- **Eager**: Terminal operations are eager and trigger the processing of the stream pipeline.

---

#### 9. Parallel Streams

- **Parallel streams** allow you to process data in parallel to take advantage of multi-core processors.
    - To convert a stream to parallel:
        
        ```java
        Stream<String> parallelStream = list.stream().parallel();
        ```
        
    - Terminal operations on parallel streams are often more efficient, but they require caution regarding thread safety and ordering.

---

#### 10. Examples of Common Stream Operations

**Example 1: Filtering and Collecting**

```java
List<String> list = Arrays.asList("apple", "banana", "cherry", "date");
List<String> filteredList = list.stream()
                                .filter(s -> s.startsWith("a"))
                                .collect(Collectors.toList());
System.out.println(filteredList); // [apple]
```

**Example 2: Mapping and Reducing**

```java
List<String> list = Arrays.asList("apple", "banana", "cherry");
int totalLength = list.stream()
                      .map(String::length)
                      .reduce(0, Integer::sum);
System.out.println(totalLength); // 15
```

**Example 3: Grouping**

```java
List<String> list = Arrays.asList("apple", "banana", "cherry", "date", "fig");
Map<Integer, List<String>> groupedByLength = list.stream()
                                                .collect(Collectors.groupingBy(String::length));
System.out.println(groupedByLength); // {5=[apple], 6=[banana], 7=[cherry], 4=[date], 3=[fig]}
```

---

#### 11. Summary of Key Methods

|**Method**|**Description**|
|---|---|
|`filter(Predicate)`|Filters elements based on a condition.|
|`map(Function)`|Transforms each element into another form.|
|`flatMap(Function)`|Flattens nested streams.|
|`distinct()`|Removes duplicate elements.|
|`sorted()`|Sorts the elements.|
|`collect(Collector)`|Collects elements into a collection.|
|`forEach(Consumer)`|Performs an action for each element.|
|`reduce(BinaryOperator)`|Performs a reduction on the elements.|
|`toArray()`|Converts the stream into an array.|

---

This cheat sheet should cover all the key **Stream API** concepts and methods that you will need to master for the **Java 17 OCP Exam**. Understanding streams and functional-style programming will significantly improve your ability to write efficient and clean Java code.