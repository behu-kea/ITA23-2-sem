# Interfaces & 4 pillars



## Læringsmål

- Interfaces
- 4 pillars of OOP



## Preparation for class

- Se interface delen af den her video: [Java guide - Sådan arbejder du med interfaces og abstrakte klasser i Java](https://www.youtube.com/watch?v=yk0e6R3RcDo)
- Se OOP delen af den her video: [Java guide - 4 pillars of OOP, encapsulation og polymorphism](https://youtu.be/GpjpqhthnnU)



Ekstra links:

- [https://behu.gitbook.io/java-first-semester/topics/04-object-oriented-programming/4-pillars-oop](https://behu.gitbook.io/java-first-semester/topics/04-object-oriented-programming/4-pillars-oop)
- [https://behu.gitbook.io/java-first-semester/topics/04-object-oriented-programming/interfaces](https://behu.gitbook.io/java-first-semester/topics/04-object-oriented-programming/interfaces)
- 17.7 i Think Java



## Plan

- Feedback on handin
  - Jeg er **meget** imponeret!
  - if (number % 2 == 0) imod return number % 2 == 0
  - Husk constructor
  - Husk private attributter!
  - I tager virkelig seperation til jer. Det er fedt. Med seperate klasser til fx max og min
  - Gode vareiabel navne
  
- 5 min peer instruction
- 40 min - example code
- 30 min exercise alone or in groups
  - Peer review first
- Break
- 30 min - In random groups of 2-3 create a 5 min presentation that highlights either
  - Interfaces vs Abstract classes
- 20 minute - review of randomnly assigned person
- 15 min - Recap of exercises and topics



## Peer instruction



### Question 1

What kind of error does the follwing code produce?

```java
package interfaces;

import java.util.ArrayList;

public interface PersonInterface {
    void sayHi();
    void setName(String name);
    int getAge();
}

class Person implements PersonInterface {
    String name;
    int age;

    public void sayHi() {
        return "Hi!";
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return this.age;
    }
}

```

- `Person` does not properly implement the `PersonInterface`
- One of the methods returns the wrong type
- There is a syntax error



### Question 2

What happens when `camilla.getAge();` is called?

```java
package interfaces;

import java.util.ArrayList;

public interface PersonInterface {
    void sayHi();
    void setName(String name);
    int getAge();
}

class Person implements PersonInterface {
    String name;
    int age;

    public void sayHi() {
        System.out.println("Hi!");
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return this.age;
    }
}

class Main2 {
    public static void main(String[] args) {
        Person camilla = new Person("Camilla", 6);
        camilla.getAge();
    }
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
    String getName();
    double getPrice();
    ArrayList<String> getFeatures();
}
```

Create two `Mobile` and two `RaspberriPi` objects



### Chat-GPT opgave

Hop ind på [https://chat.openai.com/chat](https://chat.openai.com/chat) og lav en konto. Det er ikke obligatorisk! Hvis i ikke vil kan i bare bruge opgaven der er lidt længere nede

Brug den her prompt til at lave en interface opgave der er tailored til et emne i synes er sjovt



#### Prompt

Act as an experienced lecturer with many years of experience in creating fun and easy to understand exercises for students

Create a fun, easy to understand and interesting exercise for students. The exercise should learn the students how to use a java interface. The setting for the exercise should be the SKRIV_UNIVERS_HER



**Prompt eksempel:**

Act as an experienced lecturer with many years of experience in creating fun and easy to understand exercises for students

Create a fun, easy to understand and interesting exercise for students. The exercise should learn the students how to use a java interface. The setting for the exercise should be the Simpsons universe



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
  public String getName();
  public String getJobTitle();
  public int getSalary();
}
```

Good luck, and let's hope the employees at the Springfield Nuclear Power Plant don't cause any meltdowns!



### Streaming service

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



### 4 pillars of OOP

Take some code you have written before preferably with some classes and objects. Comment the code with the parts that are relevant to 4 pillars of OOP!