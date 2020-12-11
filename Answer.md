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
   
