# Basic Java and classes and objects



## Methods



### Methods 1

A person is elligible to vote if his/her age is greater than or equal to 18. Define a method to find out if he/she is elligible to vote. Let the user input their age. Get inspiration in the terminal output below

```
Please enter your age
6
You are not eligible to vote
```



### Methods 2

Define two methods to print the maximum and the minimum number respectively among three numbers

```java
int max = getMax(1, 18, 8);
System.out.println(max); // 18

int min = getMin(1, 18, -8);
System.out.println(min); // -8
```



### Methods 3

Define a program to find out whether a given number is even or odd

```java
boolean isThreeOdd = isOdd(3);
System.out.println(isThreeOdd); // true

boolean isEightOdd = isOdd(8);
System.out.println(isEightOdd); // false
```

Now let the user input the number that should be checked if it is odd or even



### Methods 4

Write a program that takes your full name as input and displays the abbreviations of the first and middle names except the last name which is displayed as it is.

For example, if your name is `Robert Brett Roser`, then the output should be `R.B. Roser`. Or `Benjamin Dalsgaard Hughes` will be `B.D. Hughes`



## Classes and objects



### Car & driver

There is a car, which has attributes *model* and *price*, and the car has functionalities *start*, *stop* and *move*. Also, there is a driver, having attributes *name* and *age*, and the behaviour *drive*.

Create the classes *Car* and *Driver*. The functionality of the methods does not matter. Just print something to the console



### Employee

Create a class called Employee that includes three pieces of information as instance variables

- A first name
- A last name
- A monthly salary

Your class should have a constructor that initializes the three instance variables. 

If the monthly salary is not positive, set it to 0.0. 

Create two Employee objects and display each object’s yearly salary. 

Then give each Employee a 10% raise and display each Employee’s yearly salary again.



## The brain puzzle 🧠🤔 - optional

Write a program that will return `true` if a word somewhere has letters that comes after each other in the alphabet.

Fx the word Abracadabra should return `true` because the two characters `A` and `b` comes after each other in the alphabet and comes after each other in the word.

Hello should return `false` because there are no characters that comes after each other in the alphabeat

Nope should return `true` because `o` comes after `n` in the alphabet



## Peer review

I Fronter får i én person i skal reviewe. Lad være med at bruge for lang tid på review, max 20 min

Kig efter de her ting i jeres review

- Er den rigtige type brugt?
- Er det nogle gode variabelnavne?
- Er koden nem at læse og forstå?
- Husk at skrive noget positivt om koden!
