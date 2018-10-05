## HIGH-ORDER FUNCTION

- Parameters in high-order function are placed in order: normal paramaters, functions.

**Recommended**

~~~kotlin
fun <T> lock( lock: Lock, body: () -> T) {
   // handle somethings
}
~~~

**Not recommended**

~~~kotlin
fun <T> lock(body: () -> T, lock: Lock) {
   // handle somethings
}

~~~

## LAMBDA

-  Should ignore **()**, **->**, **name parameter** and use **it** keyword to declare the parameter explicitly if the function has only  one parameter as lambda block.

**Recommended**

~~~kotlin
fun onClick(position: (Int) -> Unit) {
   // handle somethings
}

onClick { println(it) }
~~~

**Not recommended**

~~~kotlin
fun onClick(position: (Int) -> Unit) {
   // handle somethings
}

onClick({ position -> println(position) })
~~~

- Should place lambda block out of the round bracket of the function if a function has more than one parameter.

**Recommended**

~~~kotlin
fun onClick(x: String, data: (Int, String) -> Unit) {
   // handle somethings
}
onClick("abc") { position, content ->
   println("Position: $position, Content: $content")
}
~~~

**Not recommended**

~~~kotlin
fun onClick(x: String, data: (Int, String) -> Unit) {
   // handle somethings
}

onClick("abc", { position, content ->
   println("Position: $position, Content: $content")
})
~~~
- Should use **return@label** in a lambda instead of return in an annonymous function.

**Recommended**

~~~kotlin
 fun onClick(position: (Int) -> Int) {
   // handle somethings
    }
    
 onClick { return@onClick it }
~~~

**Not recommended**

~~~kotlin
 fun onClick(position: (Int) -> Int) {
   // handle somethings
    }

 onClick(fun(x: Int): Int {
   // handle somethings
      return x
    })
~~~

## INLINE KEYWORD

- An inline function is used for smalls function(1 -> 5 lines of code), not used for big function.
- The inline modifier can be used on accessors of properties when we do not want to create a backing field.

**Recommended**

~~~kotlin
inline var bar: Bar
    get() = // handle somethings
    set(v) { // handle somethings }
~~~

**Not recommended**

~~~kotlin
var bar: Bar
    get() = // handle somethings
    set(v) { // handle somethings }
~~~



