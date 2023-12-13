# Interfaces & abstract



## Preparation

- [Learn Kotlin for Android: Abstract Classes & Functions (Lesson 19)](https://www.youtube.com/watch?v=_KoBfDb4Gtw)
- [Learn Kotlin for Android: Interfaces (Lesson 20)](https://www.youtube.com/watch?v=RctW18zpgec)



Optional

- https://kotlinlang.org/docs/interfaces.html



## Overview

Abstract class needs to be called



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



## Exercises



### Computer

Create two java classes `Mobile` and `RaspberriPi` that implements this interface:

```java
public interface Computer {
    val name: String;
    val price: Int;
  	val location: Map<String, Double>;
  	fun printLocation();
}
```

Create two `Mobile` and two `RaspberriPi` objects



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



