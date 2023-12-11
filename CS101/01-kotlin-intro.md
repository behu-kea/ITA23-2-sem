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
  - ArrayList
  - Map
- For loop
- Input



## Preparation

- [Installer Android Studio](https://developer.android.com/studio)



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

Create an `ArrayList`. Add some prices to the `ArrayList`. Now find the average price of the `ArrayList`



### Opgave 5 - level 1

Create a `HashMap` that contains the numberplate of a car and that cars color



### Opgave 7 - level 2

Create a function that prompts the user to provide a number, computes the half of the number and prints the result with a friendly message



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



### Opgave 9 - level 3

### Emoji Sequence Decoder and encoder - Level 3

Emoji Sequence Decoder - Intermediate

Objective: Develop a Kotlin function to decode a sequence of emojis into text using a specific mapping.

Description: In this exercise, you will create a Kotlin function decodeEmojiSequence that takes a string of emojis and decodes it into a text message. The decoding process is based on a predefined mapping of emoji pairs to characters. Your task is to implement this function to accurately translate the emoji sequence into the corresponding text.

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

Constraints:

- The input string will only contain valid emojis from the defined mapping and will have an even length
- The function should handle cases where invalid emoji pairs are present and return an appropriate error message or placeholder.



Usage:

```kotlin
val sequence = "😀😁😃😄😀😂"
println(decodeEmojiSequence(sequence))
// Output: "ACB"
```



#### Encode

Now create a function that goes the other way. From string to encoded emoji string



```kotlin
println(encodeEmojiSequence("hello"))
// Output: "😅😊😄😆😇😌😇😌😋😁"
```

