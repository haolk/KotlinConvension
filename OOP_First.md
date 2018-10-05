# Visibility Modifiers

- **Kotlin** have 4 **visibility modifiers: public, internal, protected, private.** But when we using we must define **visibility modifier** that have the smallest range of use.
- If **visibility modifiers** is **public**, omitted it:

**Recommended**

~~~kotlin
val name: String = "This is name"
~~~

**Not recommended**

~~~kotlin
public val name: String = "This is name"
~~~

# Class

- **Constructor**: Initialize class properties as primary constructor parameters instead of in an init block.

**Recommended**

~~~kotlin
class Person (val firstName: String, val lastName) {
    // handle something
}
~~~

**Not recommended**

~~~kotlin
class Person (firstName: String, lastName: String) {
  	val firstName: String
  	val lastName: String

  	init {
		this.firstName = firstName
		this.lastName = lastName
  	}

  	// handle something
}
~~~

# Function
 
- If a function returns Unit, the return type should be omitted.

**Recommended**

~~~kotlin
fun showText (text: String) {
   	println(text)
}
~~~

**Not recommended**

~~~kotlin
fun showText (text: String): Unit {
    println(text)
}
~~~

- If the function only executes an expression, the expression should be placed on the declaration line.

**Recommended**

~~~kotlin
fun sum (a: Int, b: Int): Int = a + b
~~~

**Not recommended**

~~~kotlin
fun sum (a: Int, b: Int): Int {
 	return a + b
}
~~~

- If the function has an empty body, use the Unit type instead of empty bracket body.

**Recommended**

~~~kotlin
fun doNothing() = Unit
~~~

**Not recommended**

~~~kotlin
fun doNothing() {
	// No opp
}
~~~ 

# Data class

Only using data keyword when class need equals(), hashCode(), toString(), copy(), componentN() function. Example: Models class.

# Enum classes

An enum with no functions and no documentation on its constants may optionally be formatted as a single line.

~~~kotlin
enum class Answer { YES, NO, MAYBE }
~~~

When the constants in an enum are placed on separate lines, a blank line is not required between them except in the case where they define a body.

~~~kotlin
enum class Answer {
    YES,
    NO,

    MAYBE {
        override fun toString() = """¯\_(ツ)_/¯"""
    }
}
~~~

# Generics

When define an object of a generic class we don't need define type of that object.

~~~kotlin
class Food<T>(kind: T) {
	var value = kind
}
~~~

**Recommended**

~~~kotlin
val fish = Food("Fish")
~~~

**Not recommended**

~~~kotlin
val fish: Food<String> = Food<String>("Fish")
~~~ 
