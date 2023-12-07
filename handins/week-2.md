# Nedarvning, abstract, override, interface, 4 pillars



### Inheritance 1

Create a new class called `Computer`. Before you add any more code, know that you will need to add two additional classes: `Laptop` and `SmartPhone`

1. For a parent class add 3 properties, 2 methods, and a constructor.
2. For a child class add *at least* 1 additional property and 1 additional method.

In the main method create a `Laptop` and a `SmartPhone`



### Modelling

We have to create the classes for a School. 

This school have different employees 👇

- Teacher
- Janitor
- Headmaster
- It admin

There are also classes (as in a school class not a java class). A class can have a list of students and a name. 

A school can have a list of classes and a list of employees.

Try and think about the different classes you would need to solve this problem. First write the plan down. 

When you have a plan start writing the actual classes to solve this problem. 

The functionality insinde the methods is not important, but the classes and the class structure is!

For the employees, make a parent class. Think about what sepcific attributes you would have for the different roles



### Interface 1

Create an interface called `FastFood` (with appropriate methods) and create a `Sandwich` class, a `Pizza` class and a class you decide that implements the `FastFood` interface.

Add some different `Fastfood` objects to an array. Now iterate through that array and use some of the methods you have created above. 



### Interface 2

Create a class that implements the following interface. Now create two objects using the class created

```java
interface Vehicle {
    void changeGear(int a);
    void speedUp(int a);
    void applyBrakes(int a);
}
```



### Override

Create a class called `RapSong` with a method called `play` that prints "Playing a rap song"

Now create a class called `OldSchoolRap` that extends `RapSong` and overrides the `play` method to print "Playing old school rap"

Define a class called `NewSchoolRap` that extends `RapSong` and overrides the `play` method to print "Playing new school rap"

In the `Main` class, create an instance of each class and call the `play` method on each



## Autoshop - optional

#### `Car`

Create a super class called `Car`. The `Car` class has the following fields and methods. 

- `speed`
- `regularPrice`
- `color`
- `getSalePrice()`



#### `Truck`

Create a sub class of `Car` class and name it as `Truck`. The `Truck` class has the following fields and methods. 

- `weight`
- `getSalePrice()`

If the weight of a `Truck` is more than 2000 kg then there is a discount of 10% otherwise 20%



#### `Ford`

Create a subclass of `Car` class and name it as `Ford`. The `Ford` class has the following fields and methods 

- `year`
- `manufacturerDiscount`
- `getSalePrice()`

If a `manufacturerDiscount` is set then the salesPrice will be that much cheaper



#### `AutoShop`

Create `AutoShop` class which contains the `main()` method. Perform the following within the `main()` 
method. 

- Create an instance of `Truck` class and initialize all the fields with appropriate values. Use `super(...)` method in 
  the constructor for initializing the fields of the superclass. 
- Create two instances of the `Ford` class and initialize all the fields with appropriate values. `Use super(...)` 
  method in the constructor for initializing the fields of the super class. 
- Create an instance of `Car` class and initialize all the fields with appropriate values. Display the sale prices of all instances.



## Peer review

I Fronter får i én person i skal reviewe. Lad være med at bruge for lang tid på review, max 20 min

Kig efter de her ting i jeres review

- Er den rigtige type brugt?
- Er det nogle gode variabelnavne?
- Er koden nem at læse og forstå?
- Husk at skrive noget positivt om koden!
