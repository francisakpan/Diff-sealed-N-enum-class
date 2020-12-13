## Difference between a Sealed class and Enum class

### Sealed Class
Seealed classes are used when a value have only one of the types from a limited set.
They are abstract classes with a specific number of subclasses all defined in the same file.

For example: 

  ```kotlin
    sealed class Response<out R>
    class Success<R>(val value: R): Response<R>()
    class Failure(val error: Throwable): Response<Nothing>()

    fun handle(response: Response<String>)
    {
      val text = when(response) 
      {
        is Success -> "Success, date are: " + response.value
        is Failure -> "Error"
      }

      print(text)
    }
  ```

### Enum Class
Enum class represent a specific set of values whereas sealed class reperesent a specific set of classes.
The advantage in using enum class is they can be serialized and deserialized out of the box using methods
like  `values` and `valueOf`.

Example:

  ```kotlin
    //Basic usage of enum class
    enum class Direction {
      NORTH, EAST, SOUTH, WEST
    }
  ```
  
  ```kotlin
    /*
    * Using Anonymous classes
    * Enum constants can declare their own anonymous classes with their corresponding methods
    * as well as overiding base methods.
    */
    enum class ProtocolState {
      WAITING {
        override fun signal() = TALKING
      },

      TALKING {
        override fun signal() = WAITING
      };

      abstract fun signal(): ProtocolState
     }
  ```
   
## Why is Kotln interoperable with java
Kotlin is interoperable with java to make it easy for java developers to to migrate their Java projects to
kotln. Kotlin being a JVM (Java Virtual Machine) based language just like java, compiles to byte code exactly eauivalent 
to java byte code which can run on JVM. Due to their equivalent nature they can communicate with each other and that’s
how interoperability is established in kotlin for Java. And makes Kotlin 100% interoperable with Java.

## Difference between procdural and object oriented programming

| Procedural | OOP |
| ---------- | ----------|
| There is no access specifier in procedural programming. | Object oriented programming have access specifiers like private, public, protected etc. |
| Procedural programming does not have any proper way for hiding data so it is less secure. | Object oriented programming provides data hiding so it is more secure.|
| In procedural programming, overloading is not possible. | Overloading is possible in object oriented programming. |
| In the case of procedural the main program is divided into small parts based on the functions and is treated as separate program for individual smaller program. | In OOPs concept of objects and classes is introduced and hence the program is divided into small chunks called objects which are instances of classes. |
| There is no simple process to add data in POP at least not without revising the whole program. | Due to modularity in its programs is less complex and hence new data objects can be created easily from existing objects making object-oriented programs easy to modify. |
