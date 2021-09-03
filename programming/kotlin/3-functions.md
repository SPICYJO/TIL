# Functions

## Function and Variable
<details>
    <summary>Collecions in Kotlin</summary>
    
```kotlin
val set = hashSetOf(1, 7, 53)
val list = arrayListOf(1, 7, 53)
val map = hashMapOf(1 to "one", 7 to "seven", 53 to "fifty-three")
```

- Kotlin use Java's collections (You can check it by `javaClass`)
</details>

<details>
    <summary>Function Call</summary>
    
```kotlin
fun <T> joinToString(
    collection: Collection<T>,
    separator: String,
    prefix: String,
    postfix: String
): String {
    val result = StringBuilder(prefix)
    for ((index, element) in collection.withIndex()) {
        if (index > 0) result.append(separator)
        result.append(element)
    }

    result.append(postfix)
    return result.toString()
}

val list = listOf(1, 2, 3)
println(joinToString(list, "; ", "(", ")")) // (1; 2; 3)
```

```kotlin
joinToString(collection, " ", " ", ".") // Hard to understand
joinToString(collection, separator = " ", perfix = " ", postfix = ".") // Much better
```
- You can speicify parameter's name in Kotlin


```kotlin
fun <T> joinToString(
    collection: Collection<T>,
    separator: String = ",",
    prefix: String = "",
    postfix: String = ""
): String
/*...*/

println(joinToString(list, ", ", "", "")) // 1, 2, 3
println(joinToString(list, ", ")) // 1, 2, 3

```
- You can speicify default parameter in Kotlin
- If you call function with default parameter in Java, you may have to use `@JvmOverloads` which generates a bunch of overloaded functions

</details>

<details>
    <summary>Top-level function and property</summary>

```kotlin
// filename: join.kt
package strings

const val string = "HEY"

fun <T> joinToString(...): String {...}
```

```java
// Generated Java Claass
package strings;

public class JoinKt {
    public static final String string = "HEY";

    public static String joinToString(...) {...}
}
```
- In Kotlin, you can create top-level functions and properties, which don't belong to some class
- You can change generated Java class's name by using `@JvmName`

</details>

## Extension function and extension property
<details>
    <summary>Extension function</summary>

```kotlin
// filename: StringUtil.kt
package strings

fun String.lastChar(): Char = this.get(this.length - 1)
```

```kotlin
import strings.lastChar

val c = "Kotlin".lastChar()
```

```kotlin
import strings.lastChar as last

val c = "Kotlin".last()
```

- In Kotlin, you can add additional functions to existing class by defining a extension function
- Extened class and object are called receiver type and receiver object

</details>

<details>
    <summary>Calling extension function in Java</summary>

```java
char c = StringUtilKt.lastChar("Java");
```

- Internally, Kotlin's extension function is converted into a Java static method which get its receiver object as its first parameter.
- Kotlin's extension function is syntatic sugar for static method call
- So, it is not possible to call private method of receiver type in extension function
- Also, it is not possible to override an extension function

</details>

<details>
    <summary>Extension property</summary>
    
```kotlin
val String.lastChar: Char
    get() = get(length - 1)

var StringBuilder.lastChar: Char
    get() = get(length - 1)
    set(value: Char) {
        this.setCharAt(length - 1, value)
    }
```

- You can add additional property by defining extension property
- But there is no way to add additional state(i.e. field) to class
</details>

## vararg, infix function call, destructuring declaration
<details>
    <summary>vararg</summary>
    
```kotlin
val list = listOf(2, 3, 5, 7, 11)

fun listOf<T>(vararg values: T): List<T> { ... }

fun main(args: Array<String>) {
    val list = listOf("args: ", *args)
    println(list)
}
```

- `*`(spread operator) is needed when passing an array as a `vararg` argument

</details>

<details>
    <summary>infix function call and destructuring declaration</summary>
    
```kotlin
val map = mapOf(1 to "one", 7 to "seven")

1.to("one")
1 to "one" // equivalent to 1.to("one")

infix fun Any.to(other: Any) = Pair(this, other) // infix keyword is needed in function declaration
```

```kotlin
val (number, name) = 1 to "one" // destructuring declaration
```

</details>

## local function
<details>
    <summary>local function</summary>
    
```kotlin
// Not good
class User(val id: Int, val name: String, val address: String)

fun saveUser(user: User) {

    if (user.name.isEmpty()) {
        throw IllegalArgumentException("Can't save user ${user.id}: empty Name")
    }

    if (user.address.isEmpty()) {
        throw IllegalArgumentException("Can't save user ${user.id}: empty Address")
    }

    // Save user to database
}

saveUser(User(1, "", "")) // java.lang.IllegalArgumentException: Can't save user 1: empty Name

```
```kotlin
// Much better
class User(val id: Int, val name: String, val address: String)

fun User.validateBeforeSave() {
    fun validate(value: String, fieldName: String) {
        if (value.isEmpty()) {
            throw IllegalArgumentException("Can't save user $id: empty $fieldName")
        }
    }

    validate(name, "Name")
    validate(address, "Address")
}

fun saveUser(user: User) {
    user.validateBeforeSave()

    // Save user to database
}
```

- In Kotlin, it is possible to define a function, i.e. local function inside another function
- By using local function and extension function, it is able to write much cleaner code

</details>
