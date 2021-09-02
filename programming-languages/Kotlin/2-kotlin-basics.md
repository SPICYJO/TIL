# Kotlin Basics

## Function and Variable
<details>
    <summary>Hello, World!</summary>
    
```kotlin
fun main(args: Array<String>) {
    println("Hello, world!")
}
```

- Parameter's type comes after parameter name
- No need to put function inside a class
- Semicolon(;) is optional
</details>

<details>
    <summary>Function</summary>
    
```kotlin
fun max(a: Int, b: Int): Int {
    return if (a > b) a else b
}
```

- Kotlin's `if` is an **expression** not a statement. (`if`, `when`, `try` are also expressions in Kotlin)

```kotlin
fun max(a: Int, b: Int): Int = if (a > b) a else b
```

- Function body can be expressed by either block body or expression body
</details>

<details>
    <summary>Variable</summary>
    
```kotlin
val answer = 42
val answer2: Int = 45
var answer3 = 49
```

- `val`: immutable reference. equivalent to Java's `final` variable
- `var`: mutable reference. equivalent to Java's regular variable
</details>

<details>
    <summary>String template</summary>
    
```kotlin
val value = 12
"Hi, $value"
"Hi, " + value // equivalent
"Hi, ${value}" // better practice to wrap with bracket
"Hi, ${value + 4}" // expressions are welcomed
```

</details>

## Class and Property
<details>
    <summary>Property</summary>
    
- In Java, field and accessor methods(getter, setter) are referred as property

```kotlin
class Person (
    val name: String,
    var isMarried: Boolean
)
```

- Kotlin internally generates getter, setter methods like Java
- `val` corresponds to read only field (private field, only getter)
- `var` corresponds to writable field (private field, getter and setter)

```kotlin
class Rectangle(val height: Int, val width: Int) {
    val isSquare: Boolean
        get() {
            return height == width
        }
}
```

- You can also define custom accessor methods

</details>
<details>
    <summary>Source code structure: Directory and Package</summary>
    
```kotlin
package geometry.shapes

import java.util.Random

class Rectangle(val height: Int, val width: Int) {
    val isSquare: Boolean
        get() {
            return height == width
        }
}
```

- In Kotlin, it is not forced to manage directory accroding to package names unlike Java
- You can also put as many classes you want into one file
- It would be still a good practice to follow Java's convention
</details>

## `enum` and `when`
<details>
    <summary>enum</summary>
    
```kotlin
enum class Color {
    RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET
}
```

```kotlin
enum class Color(val r: Int, val g: Int, val b: Int) {
    RED(255, 0, 0), GREEN(0, 255, 0), BLUE(0, 0, 255);  // notice there is a semicolon

    fun rgb() = (r * 256 + g) * 256 + b
}
```

</details>

<details>
    <summary>when</summary>
    
```kotlin
fun getGrade(color: Color) = 
    when (color) {
        Color.RED, Color.ORANGE, Color.YELLOW -> "A"
        Color.GREEN -> "B"
        Color.INDIGO -> "C"
        else -> "F"
    }
```

- Kotlin's `when` is similar to Java's `switch`
- `when` is an expression

```kotlin
fun getSomething(color: Color) = 
    when {
        color == Color.RED -> "hot"
        color == Color.BLUE -> "cold"
        else -> {
            1+2
            "not sure"
        }
    }
```

- it is also possible to use when with no parameter
- it is also possible to use a block. In this case, `when` is evaluated to last expression's value
- notice that `==` compares equality of two operands in Kotlin, not identity like in Java

</details>

<details>
    <summary>smart cast</summary>
    
```kotlin
interface Expr
class Num(val value: Int) : Expr
class Sum(val left: Expr, val right: Expr) : Expr

fun eval(e: Expr): Int {
    if (e is Num) {
        val n = e as Num // No need to explicitly cast to Num
        return n.value
    }
    if (e is Sum) {
        return eval(e.right) + eval(e.left)
    }
    throw IllegalArgumentException("Unknown expression)
}
```

- Kotlin's `as` is similar to Java's `instanceof`, but it smartly cast into the specified type


</details>


## `while` and `for` loop
<details>
    <summary>while loop</summary>
    
```kotlin
while (condition) {
    /*...*/
}
```
```kotlin
do {
    /*...*/
} while (condition)
```

</details>

<details>
    <summary>for loop</summary>
    
```kotlin
for (i in 1..100) { // 1 to 100(inclusive)
    /*...*/
}
```
```kotlin
for (i in 1 until 100) { // 1 to 100(exclusive)
    /*...*/
}
```
```kotlin
for (i in 100 downTo 1 step 2) {
    /*...*/
}
```
```kotlin
val map = TreeMap<Int, String>()
for ((key, value) in map) { // destructuring
    /*...*/
}
```

- cf) `in` can also be used to determine if value is in the certain range. (e.g. `3 in 4..6`, `3 !in 4..6`)

</details>


## Exception handling


<details>
    <summary>try, catch, finally</summary>
    
```kotlin
fun readNumber(reader: BufferedReader): Int? {
    try {
        val line = reader.readLine()
        return Integer.parseInt(line)
    }
    catch (e: NumberFormatException) {
        return null
    }
    finally {
        reader.close()
    }
}
```

- Unlike Java, there is no need to explicitly handle cheched exception (i.e. In Java, it is forced to either catch it or declare with `throws` keyword in function signature)
- `try` is also an expression

</details>