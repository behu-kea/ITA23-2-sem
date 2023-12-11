# Kotlin intro



## Content



### Course outline

- CS 101
  - Weekly handins
- Android with Kotlin
- 2 projects
  1. UI/UX, some programming tasks
  2. large 11 week project with 3 handins (iterations)
     - You have to find your own problem/project
- Trivselssamtaler efter 5 uger



### Learning goals

- Kotlin
  
  - Compile vs runtime
  - Syntax
- Debugging
- Typer
  - Strenge
  - Boolean
  - Integer, float, double
  - Array fixed number of values
    - Collection like mutableListOf can change
  - Map
    - mapOf
- For loop
- Nullability
- Input



## Preparation

- [Installer Android Studio](https://developer.android.com/studio)
- [Kotlin in 100 Seconds](https://www.youtube.com/watch?v=xT8oP0wy-A0)
- [Learn Kotlin in 12 Minutes](https://www.youtube.com/watch?v=iYrgWO2oibY)
- Optional: [https://kotlinlang.org/docs/basic-syntax.html](https://kotlinlang.org/docs/basic-syntax.html)



## Opgaver



### Opgave 1 - Level 1

Do these steps one step at a time! Think about what type of data should be stored in the different variables

1. Create a variable called `age` (no assignment!)
2. Create another variable called `height`
3. Assign `age` to be your age
4. Assign `height` to be your height in meter
5. Create the variable `shoeSize` and assign it to be your shoesize
6. Create a variable called `name` and assign this to your name



### Opgave 2 - Level 1

Write variables to represent a rectangle:

- Height of 8.5
- Width of 5.5

Create a function that computes the area and the perimeter of the rectangle and print the results



### Opgave 3 - Level 2

- Convert a string to uppercase
- Return the index of a character in a string
- Concatenate two different string
- Check these strings are equal to each other. Uppercases should be ignored!
  - `hello`, `ollhe` should print `false`
  - `bike`, `banana` should print `false`
  - `name`, `NaMe` should print `true`
  - `yes`, `yes` should print `true`



### Opgave 4 - level 1

Create an `Array`. Add some prices to the `Array`. Now find the average price of the `Array`



### Opgave 5 - level 1

Create a `Map` that contains the numberplate of a car and that cars color



### Opgave 7 - level 2

Create a function that prompts the user to provide a number, computes the half of the number and prints the result with a friendly message

*Research how inputs work in Kotlin*



### Opgave 7.1 - level 2

**Objective**: Develop a Kotlin function to safely find emojis in a possibly null string, demonstrating handling of nullability in Kotlin.

**Description**: In this exercise, you will create a Kotlin function `findEmoji` that takes a string, which may be null, as input and returns the first emoji found in the string. If the string is null, contains no emojis, or if any other issue is encountered, the function should handle it gracefully without throwing an exception.

Your function should demonstrate the use of Kotlin's null-safety features, such as safe calls (`?.`), the Elvis operator (`?:`), and safe casting.

**Constraints**:

- The function should be able to handle null input strings.
- Emojis are considered as characters that are outside the standard ASCII range.

**Usage**:

```
kotlin
val text1: String? = "Hello 😄 World!"
val text2: String? = "Just text, no emojis"
val text3: String? = null

println(findEmoji(text1)) // Output: "😄"
println(findEmoji(text2)) // Output: "No emoji found"
println(findEmoji(text3)) // Output: "Input is null"
```

This exercise provides an opportunity to practice handling nullability in Kotlin, which is a crucial aspect of the language's safety features.



### Opgave 8 - level 2

Write a Java program that accepts two integers from the user and then prints 

- the sum
- the difference
- the product
- the average
- the distance  (the difference between integer)
- the maximum (the larger of the two  integers)
- the minimum (smaller of the two integers)

Here is an example:

```
Input 1st integer: 25
Input 2nd integer: 5
Expected Output:
Sum of two integers: 30
Difference of two integers: 20
Product of two integers: 125
Average of two integers: 15.00
Distance of two integers: 20
Max integer: 25
Min integer: 5
```



### Emoji Sequence Cryptographer - level 3

**Objective**: Develop a Kotlin function to encode and decode messages using a complex emoji-based cipher.



**Description**: This exercise involves creating two Kotlin functions: `encodeMessage` and `decodeMessage`. Both functions will utilize a sophisticated mapping system involving emoji pairs and single emojis. The `encodeMessage` function will translate a text message into a string of emojis, while `decodeMessage` will do the reverse, using the same mapping.

Mapping:

​    "😀😁" → `A`

​    "😀😂" → `B`

​    "😃😄" → `C`

​    "😃😅" → `D`

​    "😄😆" → `E`

​    "😄😇" → `F`

​    "😅😂" → `G`

​    "😅😊" → `H`

​    "😆😁" → `I`

​    "😆😋" → `J`

​    "😇😉" → `K`

​    "😇😌" → `L`

​    "😊😂" → `M`

​    "😊😎" → `N`

​    "😋😁" → `O`

​    "😋😌" → `P`

​    "😉😀" → `Q`

​    "😉😍" → `R`

​    "😌😃" → `S`

​    "😌😎" → `T`

​    "😎😀" → `U`

​    "😎😇" → `V`

​    "😍😄" → `W`

​    "😍😅" → `X`

​    "😂😀" → `Y`

​    "😂😃" → `Z`



**Mapping**:

- Single letters (A-Z) are mapped to pairs of emojis.
- Spaces and punctuation marks are mapped to single emojis.
- Special combinations of emojis indicate capitalization or common words.



**Example Mapping**:

- Letters: Same as previously defined in the "Emoji Sequence Decoder" exercise.
- Space: "🌟"
- Period: "🔴"
- Comma: "🔵"
- Exclamation mark: "❗"
- Question mark: "❓"
- Capitalization Indicator: A pair of "👑" before a letter pair indicates that the letter is capitalized.
- Common Words:
  - "The": "🌍🌎"
  - "And": "🌞🌜"



**Constraints**:

- The input text for encoding should be a standard string containing letters, spaces, and basic punctuation.
- The decoding function should handle invalid or incomplete emoji sequences gracefully, returning an error message or placeholder.



**Usage**:

```
kotlin
val text = "Hello, World!"
val encoded = encodeMessage(text)
println(encoded)
// Output: "👑😀😉🌍🌎🔵 👑😍😂🌍🌎🔴"

val decoded = decodeMessage(encoded)
println(decoded)
// Output: "Hello, World!"
```
