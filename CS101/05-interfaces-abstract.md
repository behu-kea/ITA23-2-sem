# Interfaces & abstract



## Preparation

- [Learn Kotlin for Android: Abstract Classes & Functions (Lesson 19)](https://www.youtube.com/watch?v=_KoBfDb4Gtw)
- [Learn Kotlin for Android: Interfaces (Lesson 20)](https://www.youtube.com/watch?v=RctW18zpgec)



Optional

- https://kotlinlang.org/docs/interfaces.html



## Overview

- Go through some examples and discuss if we should use inheritance, abstract, contract, just classes
  - Gå igennem den her [https://github.com/behu-kea/first-semester-java/blob/9d5b9fc185978dad0bfdbc0b83fdc7937326db4d/assets/Bookingsystem%20(DK).pdf](https://github.com/behu-kea/first-semester-java/blob/9d5b9fc185978dad0bfdbc0b83fdc7937326db4d/assets/Bookingsystem%20(DK).pdf)



## Peer instruction



### Question 1

What kind of error does the follwing code produce?

```java
interface UserInterface {
    var name: String
    var email: String

    fun displayUserInfo()
    fun updateEmail(newEmail: String)
}


class User(override var name: String, override var email: String) : UserInterface {
    override fun displayUserInfo() {
        println("User Name: $name")
        println("User Email: $email")
    }

    override fun updateEmail(newEmail: String) {
        email = newEmail
        println("Email updated to: $email")
        return newEmail
    }
}
```

1.  `updateEmail` incorrectly returns a value
2. Wrong assignment in `updateEmail`
3. displayUserInfo` prints incorrect information` 
4. `User` does not override `displayUserInfo` properly



### Question 2

What happens when `camilla.getAge();` is called?

```java
package interfaces

interface PersonInterface {
    fun sayHi();
    val age: Int;
    val name: String;
}

class Person(override var name: String, override val age: Int) : PersonInterface {
    override fun sayHi() {
        println("Hi, I'm $name!")
    }
}

fun main() {
    val camilla = Person("Camilla", 6)
    println("Age: ${camilla.age}")
    camilla.sayHi()
}

```

- `null`
- 6
- Syntax error
- None of the above



## Topics



### Interface

An interface works a lot like a contract or a set of rules. In an interface we define attributes and functions a class should have to implement that specific interface. 

Lets get concrete:

This Interface defines what it is like to be a `Product`. That means that classes implementing this interface **has to have** 

- An attribute called `name` which is a `String`
- An attribute called `price` which is an `Int`
- An attribute called `name` which is an `Int`
- An function called `printProductDetails` 

```kotlin
interface Product {
    val name: String;
    val price: Int;
  	val id: Int;
    fun printProductDetails();
}
```

Here is how an `interface` gets implemented by a class

```kotlin
class Television: Product {
		override val name: String,
    override val price: Int,
    override val id: Int
) : Product {
    override fun printProductDetails() {
				println("${this.name} is an amazing television");
    }
}
```

Let's initialise a television

```kotlin
val samsungTelevision: Television = Television("Samsung TV", 8000, 123456789);
```

We use the `override` keyword because we are overwriting a property from the interface we are implementing

We can even add functionality inside of the interface:

```kotlin
interface Computer{
    val name: String;
    val price: Int;
    val location: Map<String, Double>;

    fun printLocation() {
        println("${this.name} is an amazing television");
    };
}
```

Now we dont need to override the `printLocation` method because it has been defined

A class can inherit from only one class but can implement mutiple interfaces



### Abstract

An abstract class is a class that cannot be instantiated. The classic example of an abstract class is an animal. An `Animal` is an abstract concept (it is not a elephant or mouse or dog which are specific animals) therefore it does not make sense to instantiate an `Animal`

```kotlin
abstract class Animal {
    abstract val name: String;
    abstract val size: Double;
    abstract fun makeSound();
}

class Elephant(
    override val name: String,
    override val size: Double
) : Animal() {
    override fun makeSound() {
        println("asd");
    }
}

fun main() {
  // This will not work!!! We cannot instantiate or create an object of a Abstract class!
  val Dog: Animal = Animal("Perter the elephant", 1000.0); // Error
  // But we can do this:
  val Elephant: Elephant = Elephant("Perter the elephant", 1000.0);
}
```



## Exercises



### Car and driver

There is a car, which has attributes *model* and *price*, and the car has functionalities *start*, *stop* and *move*. Also, there is a driver, having attributes *name* and *age*, and the behaviour *drive*.

Create the classes *Car* and *Driver*. The functionality of the methods does not matter. Just print something to the console



### Employee

Create a class called Employee that includes three pieces of information as instance variables

- A first name
- A last name
- A monthly salary (double)

Your class should have a constructor that initializes the three instance variables. If the monthly salary is not positive, set it to 0.0. Create two Employee objects and display each object’s yearly salary. Then give each Employee a 10% raise and display each Employee’s yearly salary again.



### Computer

Create two classes `Mobile` and `RaspberriPi` that implements this interface:

```java
public interface Computer {
    val name: String;
    val price: Int;
  	val location: Map<String, Double>;
  	fun printLocation();
}
```

Create two `Mobile` and two `RaspberriPi` objects



### FastFood

Create an interface called FastFood (with appropriate methods) and create a `Sandwich` class, a `Pizza` class and a class you decide that implements the FastFood interface.

Add some different `Fastfood` objects to an array. Now iterate through that array and use some of the methods you have created above.



### Chat-GPT opgave

Hop ind på [https://chat.openai.com/chat](https://chat.openai.com/chat) og lav en konto. Det er ikke obligatorisk! Hvis i ikke vil kan i bare bruge opgaven der er lidt længere nede

Brug den her prompt til at lave en interface opgave der er tailored til et emne i synes er sjovt



#### Prompt

Act as an experienced lecturer with many years of experience in creating fun and easy to understand exercises for students

Create a fun, easy to understand and interesting exercise for students. The exercise should learn the students how to use a kotlin interface. 

The exercise should fit the students interests. Here are the student interests: COMMA_SEPERATED_INTERESTS



#### Opgave eksempel

Problem Statement: You are a software engineer for the Springfield Nuclear Power Plant, and you have been tasked with creating a system to keep track of the employees at the plant. The plant's manager has already created a Java interface called "Employee" which represents an employee at the plant.

Your task is to implement the "Employee" interface and create classes for each type of employee at the plant. The manager wants the following information to be stored for each employee:

- Name of the employee
- Job title of the employee
- Salary of the employee (in dollars)

Use the "Employee" interface to create classes for the following employees:

1. Homer Simpson (Safety Inspector)
2. Waylon Smithers (Executive Assistant)
3. Carl Carlson (Nuclear Technician)
4. Lenny Leonard (Nuclear Technician)

Then, write a program that creates an array of "Employee" objects, one for each of the employees listed above. The program should then print out the name, job title, and salary of each employee in the array.

Here is the code for the "Employee" interface:

```java
public interface Employee {
  getName(): String;
  getJobTitle(): String;
  getSalary(): Int;
}
```

Good luck, and let's hope the employees at the Springfield Nuclear Power Plant don't cause any meltdowns!



### Streaming service - Level 3

We need to create the functionality for a Music Library.



#### Song

A song has to obey by the rules that they have to have methods for returning a title, artist and duration. it should also have a method for getting how many plays it has

*Tip: think interfaces*



#### Music Library

A Music Library contains songs. With a Music library we should be able to add a song, we should be able to search for a song using either title, artist or with a specific minimum duration. It should also be able to get the most popular songs



#### Main method

Now create some songs and add them to the Music Library. 

Search for some artists using title, artist and duration

Get the most popular 5 songs in the music library



