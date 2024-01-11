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
    - String literal
  - Boolean
  - Integer, float, double
  - Array fixed number of values
  - List
  - Map
    - mapOf
- Nullability
- Input
- Functions



## Måske noget peer instruction?



## Preparation

- [Installer Android Studio](https://developer.android.com/studio)
- [Kotlin in 100 Seconds](https://www.youtube.com/watch?v=xT8oP0wy-A0)
- [Learn Kotlin in 12 Minutes](https://www.youtube.com/watch?v=iYrgWO2oibY)
- [https://kotlinlang.org/docs/basic-syntax.html](https://kotlinlang.org/docs/basic-syntax.html) Optional



## Topics



### List

To create a list, remember to think about if it should be mutable or non mutable (can be changed or cant be changed)

```kotlin
val prices: MutableList<Int> = mutableListOf(2,3,4,5);
```

The list works a lot like in js

```kotlin
val prices: MutableList<Int> = mutableListOf(2,3,4,5);
println(prices[1])

prices.add(67);
println(prices)
```





## Opgaver



### Opgave 1 - Level 1

Do these steps one step at a time! Think about what type of data should be stored in the different variables

1. Create a variable called `age` (no reassignment!)
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



### Opgave 3 - Level 1 - Lidt stenet opgave

- Convert a string to uppercase
- Get the character on index 3
- Print the index of a character in the string
- Concatenate two different string
- Check these strings are equal to each other. Uppercases should be ignored!
  - `hello`, `ollhe` should print `false`
  - `bike`, `banana` should print `false`
  - `name`, `NaMe` should print `true`
  - `yes`, `yes` should print `true`



### Opgave 5 - level 1

Create a `Map` that contains the numberplate of a car and that cars color



### Opgave 4 - level 2

Create a `List`. Add some prices to the `List`



Now create a function that takes a `List` of integers and returns the second largest integer in that array



Use the function to find the second largest integer of the `List` created above



### Opgave 7 - level 2

Create a function that prompts the user to provide a number, computes the half of the number and prints the result with a friendly message

*Research how inputs work in Kotlin*



### Opgave 8 - level 2

Write a Kotlin function (and a lambda version) that accepts two integers from the user and then prints 

- the sum
- the difference
- the product
- the average
- the distance  (the difference between integer, can only be positive)
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



## 🔐 The code breaker - Level 3

[https://behu.gitbook.io/java-first-semester/projects/the-code-breaker#the-code-breaker](https://behu.gitbook.io/java-first-semester/projects/the-code-breaker#the-code-breaker)
