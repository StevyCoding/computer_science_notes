The Collection Java is a framework that provides an architecture to store and manipulate the group of objects.

Java Collections can achieve all the operations that you perform on a data such as searching, sorting, insertion, manipulation, and deletion.

Java Collection means a single unit of objects. Java Collection framework provides many interfaces (Set, List, Queue, Deque) and classes ([ArrayList](https://www.javatpoint.com/java-arraylist), Vector, [LinkedList](https://www.javatpoint.com/java-linkedlist), [PriorityQueue](https://www.javatpoint.com/java-priorityqueue), HashSet, LinkedHashSet, TreeSet).

[collections java docuementation](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html)


## Hierarchy of Collection Framework

![[Pasted image 20240412014821.png]]

# Java Collection interface
The collections framework defines several interfaces. This section provides an overview of each interface

|Sr.No.|Interface & Description|
|---|---|
|1|[The Collection Interface](https://www.tutorialspoint.com/java/java_collection_interface.htm)<br><br>This enables you to work with groups of objects; it is at the top of the collections hierarchy.|
|2|[The List Interface](https://www.tutorialspoint.com/java/java_list_interface.htm)<br><br>This extends **Collection** and an instance of List stores an ordered collection of elements.|
|3|[The Set](https://www.tutorialspoint.com/java/java_set_interface.htm)<br><br>This extends Collection to handle sets, which must contain unique elements.|
|4|[The SortedSet](https://www.tutorialspoint.com/java/java_sortedset_interface.htm)<br><br>This extends Set to handle sorted sets.|
|5|[The Map](https://www.tutorialspoint.com/java/java_map_interface.htm)<br><br>This maps unique keys to values.|
|6|[The Map.Entry](https://www.tutorialspoint.com/java/java_mapentry_interface.htm)<br><br>This describes an element (a key/value pair) in a map. This is an inner class of Map.|
|7|[The SortedMap](https://www.tutorialspoint.com/java/java_sortedmap_interface.htm)<br><br>This extends Map so that the keys are maintained in an ascending order.|
|8|[The Enumeration](https://www.tutorialspoint.com/java/java_enumeration_interface.htm)<br><br>This is legacy interface defines the methods by which you can enumerate (obtain one at a time) the elements in a collection of objects. This legacy interface has been superceded by Iterator.|
## Java Collection Classes
Java provides a set of standard collection classes that implement Collection interfaces. Some of the classes provide full implementations that can be used as-is and others are abstract class, providing skeletal implementations that are used as starting points for creating concrete collections.

The standard collection classes are summarized in the following table −

## Sr.No. | Class & Description

| Sr.No. | Class & Description                                                       |
| ------ | ------------------------------------------------------------------------- |
| 1      | **AbstractCollection**                                                    |
|        | Implements most of the Collection interface.                              |
| 2      | **AbstractList**                                                          |
|        | Extends AbstractCollection and implements most of the List interface      |
|        | (ordered collection).                                                     |
| 3      | **AbstractSequentialList**                                                |
|        | Extends AbstractList for use by collections with sequential access        |
|        | (elements accessed in order).                                             |
| 4      | **LinkedList**                                                            |
|        | Implements a linked list by extending AbstractSequentialList.             |
| 5      | **ArrayList**                                                             |
|        | Implements a dynamic array by extending AbstractList.                     |
| 6      | **AbstractSet**                                                           |
|        | Extends AbstractCollection and implements most of the Set interface       |
|        | (unique elements).                                                        |
| 7      | **HashSet**                                                               |
|        | Extends AbstractSet for use with a hash table (fast lookups).             |
| 8      | **LinkedHashSet**                                                         |
|        | Extends HashSet to allow insertion-order iterations.                      |
| 9      | TreeSet                                                                   |
|        | Implements a set stored in a tree (sorted elements). Extends AbstractSet. |
| 10     | **AbstractMap**                                                           |
|        | Implements most of the Map interface (key-value pairs).                   |
| 11     | **HashMap**                                                               |
|        | Extends AbstractMap to use a hash table (fast lookups based on key).      |
| 12     | **TreeMap**                                                               |
|        | Extends AbstractMap to use a tree (sorted keys).                          |
| 13     | **WeakHashMap**                                                           |
|        | Extends AbstractMap to use a hash table with weak keys                    |
|        | (garbage collected when no other references exist).                       |
| 14     | **LinkedHashMap**                                                         |
|        | Extends HashMap to allow insertion-order iterations.                      |
| 15     | **IdentityHashMap**                                                       |
|        | Extends AbstractMap and uses reference equality when comparing keys       |
|        | (checks if objects are the same object).                                  |
The _AbstractCollection, AbstractSet, AbstractList, AbstractSequentialList_ and _AbstractMap_ classes provide skeletal implementations of the core collection interfaces, to minimize the effort required to implement them.

The following legacy classes defined by java.util have been discussed in the previous chapter −

| Sr.No. | Class & Description                                                                                      |
|--------|-----------------------------------------------------------------------------------------------------------|
| 1      | **Vector**                                                                                                    |
|        | This implements a dynamic array. It is similar to **ArrayList**, but with some differences.                  |
| 2      | **Stack**                                                                                                     |
|        | **Stack** is a subclass of **Vector** that implements a standard last-in, first-out stack.                        |
| 3      | **Dictionary**                                                                                                |
|        | **Dictionary** is an abstract class that represents a key/value storage repository and operates much like **Map**.|
| 4      | **Hashtable**                                                                                                 |
|        | **Hashtable** was part of the original java.util and is a concrete implementation of a **Dictionary**.           |
| 5      | **Properties**                                                                                                |
|        | **Properties** is a subclass of **Hashtable**. It is used to maintain lists of values in which the key is a String and the value is also a String. |
| 6      | **PriorityQueue**                                                                                            |
|        | **PriorityQueue** class is an unbounded priority queue based on a priority heap.                               |
|        | A priority queue relying on natural ordering also does not permit insertion of non-comparable objects.    |
| 7      | **BitSet**                                                                                                    |
|        | A **BitSet** class creates a special type of array that holds bit values. This array can increase in size as needed. |
| 8      | **ArrayDeque**                                                                                                |
|        | **ArrayDeque** class provides resizable-array and implements the **Deque** interface.                              |
|        | Array deques have no capacity restrictions so they grow as necessary to support usage.                     |
| 9      | **EnumMap**                                                                                                   |
|        | **EnumMap** class is a specialized **Map** implementation for use with enum keys.                                  |
|        | All of the keys in an enum map must come from a single enum type that is specified, explicitly or implicitly, when the map is created. |
| 10     | **Queue**                                                                                                     |
|        | The **Queue** interface is provided in java.util package and it implements the **Collection** interface.          |
|        | The queue implements FIFO i.e. First In First Out. This means that the elements entered first are the ones that are deleted first. |
| 11     | **Deque**                                                                                                     |
|        | **Deque** class is a specialized **Queue** that allows the insertion, removal, and inspection of elements at both the ends.|
|        | It extends the **Queue** interface.                                                                           |

## The Collection Algorithms

The collections framework defines several algorithms that can be applied to collections and maps. These algorithms are defined as static methods within the Collections class.

Several of the methods can throw a **ClassCastException**, which occurs when an attempt is made to compare incompatible types, or an **UnsupportedOperationException**, which occurs when an attempt is made to modify an unmodifiable collection.

Collections define three static variables: EMPTY_SET, EMPTY_LIST, and EMPTY_MAP. All are immutable.