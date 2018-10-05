## COMPANION OBJECT

- It should be placed at the beginning of its wrapper class.
- Name of constant is upper case and  specified with keywords **const val**.

**Recommended**

~~~kotlin
class MyFragment: Fragment() {
    companion object {
        const val TYPE_VIEW_HEADER: Int = 0
        const val TYPE_VIEW_FOOTER: Int = 1
    }
}
~~~

**Not recommended**

~~~kotlin
class MyFragment: Fragment() {
    companion object {
        val TypeViewHeader: Int = 0
        val TypeViewFooter: Int = 1
    }
}
~~~

- When you want to use components in companion object, you should call directly.

**Recommended**

~~~kotlin
class MyClass {
   companion object {
       const val NUMBER: Int = 10
   }
}

val x: Int = MyClass.NUMBER
~~~

**Not recommended**

~~~kotlin
class MyClass {
   companion object {
       const val NUMBER: Int = 10
   }
}

val x: Int = MyClass.Companion.NUMBER
~~~

## EXTENSION FUNCTION

- Extension function is used when actually needed.
- Do not define extension function of a class in this class.

**Recommended**

~~~kotlin
class Person(val name: String) {
   // handle somethings
}

fun Person.setName(name: String) {
   // handle somethings
}
~~~

**Not recommended**

~~~kotlin
class Person(val name: String) {
   fun Person.setName(name: String) {
       // handle somethings
   }
}
~~~

- Extension property should not use **this** keyword to access to properties of the object applied.

**Recommended**

~~~kotlin
val <T> List<T>.lastIndex: Int
   get() = size - 1
~~~

**Not recommended**

~~~kotlin
val <T> List<T>.lastIndex: Int
   get() = this.size - 1
~~~

- When adding extensions to external classes, create a extension package and make separate files for each type:
 + StringExtensions.kt
 + BitmapExtensions.kt
 + ...

## DESTRUCTURING DECLARATIONS

-  Paramaters should directly destructer without componentN()

**Recommended**

~~~kotlin
data class Person(var name: String, var age: Int) {
    // handle somethings
}

val person = Person("Nguyen Van A", 22)
val (name, age) = person
println("Name:$name,Age:$age")
~~~

**Not recommended**

~~~kotlin
data class Person(var name: String, var age: Int) {
    // handle somethings
}

val person = Person("Nguyen Van A", 22)
val name = person.component1()
val age = person.component2()
println("Name:$name,Age:$age")
~~~




