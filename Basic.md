# BASIC KOTLIN CONVENTION

### Variable:

* Non-constant names are written in **lowerCamelCase**. These apply to instance properties, local properties, and parameter names.

~~~kotlin
val variable = "var"
val nonConstScalar = "non-const"
val elementStudents = listOf(mutableInstance)
val mutableValues = mapOf("Alice" to mutableInstance, "Bob" to mutableInstance2)
~~~

* All  letters of constant name is **UpperCase**

~~~kotlin
companion object {
    const val GOOGLE_HOME_URL = "http://www.google.com"
}
~~~

## Type Inference

* Type inference should be preferred where possible to explicitly decleard types

**GOOD**

~~~kotlin
val student = Student()
val age = 21
~~~

**BAD**

~~~kotlin
val student: Student = Student()
val age: Int = 21
~~~

## Strings

* Always prefer string interpolation if possible.

**GOOD**

~~~kotlin
val name = "${user.firstName} ${user.lastName}"
~~~

**BAD**

~~~kotlin
val name = user.firstName + " " + user.lastName
~~~

## If Expression

**GOOD**

~~~kotlin
if (someTest) {
...
} else {
...
}
~~~

**BAD**

~~~kotlin
if (someTest) {
...
}
else {
...
}
~~~

  * An **if/else** conditional that is used as an expression may omit braces only if the entire expression fits on one line.

**GOOD**

~~~kotlin
val value = if (string.isEmpty()) 0 else 1  // Okay
~~~

**BAD**

~~~kotlin
val value = if (string.isEmpty())  // WRONG!
                0
            else
                1
~~~

## When Expression

* Unlike `switch` statements in Java, `when` statements do not fall through. Separate cases using commas if they should be handled the same way. Always include the else case.

**GOOD**

~~~kotlin
when (Input) {
    1, 2 -> doSomethingForCaseOneOrTwo()
    3 -> doSomethingForCaseThree()
    else -> print("No case satisfied")
}
~~~

**BAD**

~~~kotlin
when (Input) {
    1 -> doSomeThingForCaseOne()
    2 -> doSomeThingForCaseOneOrTwo()
    3 -> doSomeThingForCaseThree()
}
~~~

## Smart Cast

**GOOD**

~~~kotlin
dog as? Animal ?: throw IllegalArgumentException("not Animal!")
dog.foo()
~~~

**BAD**

~~~kotlin
if (dog !is Animal) {
    throw IllegalArgumentException("not Animal!")
}
dog.foo()
~~~

## Collections

* Should be used `MutableList` if that `List` change data in future
* If you create the list to read only, you can use `List` instead of using `MutableList`

**GOOD**

~~~kotlin
val students: MutableList<Int> = ArrayList()
~~~

**BAD**

~~~kotlin
val students :List<Int> = ArrayList()
~~~

## Equality

* Should be used equal instead of "==" operator

**GOOD**

~~~kotlin
a.equal(b)
!a.equal(b)
~~~

**BAD**

~~~kotlin
a == b
a != b
~~~

## This Expression

* Don't use `this@label` if compiler uderstood that `this`

**GOOD**

~~~kotlin
data class Test(var name: String) {

    fun showName(name: String) {
        this.name = name
    }
}
~~~

**BAD**

~~~kotlin
data class Test(var name: String) {

    fun showName(name: String) {
        this@Test.name = name
    }
}
~~~

## Where to break

Code has a column limit of **100** characters. Any line that would exceed this limit must be line-wrapped
   
   * When a line is broken at an `assignment operator( =, +=, -=, *=, /=, %=)` the break comes after the symbol.

~~~kotlin
fun compare(a: String, b: String): Boolean =
             ...
~~~

* The break comes before the symbol `.` and `::` and `non-assignment operator`
   
~~~kotlin
addMarker(MarkerOptions()
                    .position(currentLocation)
                    .draggable(true)
                    .title(resources.getString(R.string.current_location))
~~~

~~~kotlin
fun getSomething(
        a:String,
        b:String,
        c:String,
        d:String,
        ::isSomething
){
   ...
}
~~~

   * A `method` or `constructor` name stays attached to the open parenthesis ( `(` ) that follows it and a `comma (,) `stays attached to the token that precedes it.
   
~~~kotlin
fun <T> Iterable<T>.joinToString(
        separator: CharSequence = ", ",
        prefix: CharSequence = "",
        postfix: CharSequence = ""
): String {
     ...
}     
~~~

   * A lambda arrow (`->`) stays attached to the argument list what precedes it.
   
~~~kotlin
val printSummary = { username: String, age: String, score: Int ->
                       println("User '$username' with '$age' get $score points.")
                   }
~~~

## Annotation

   * Member or type annotations are placed on separate lines immediately prior to the annotated construct.
   
~~~kotlin
@Retention(SOURCE)
@Target(FUNCTION, PROPERTY_SETTER, FIELD)
annotation class Global
~~~

   * Annotations without arguments can be placed on a single line.
   
~~~kotlin
@JvmField @Volatile
var disposable: Disposable? = null
~~~

   * When only a single annotation without arguments is present it may be placed on the same line as the declaration
   
~~~kotlin
@Volatile var disposable: Disposable? = null

@Test fun selectAll() {
     ...
}
~~~
