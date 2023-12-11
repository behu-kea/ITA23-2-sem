# Classes and objects



## Preparation



- https://kotlinlang.org/docs/classes.html#class-members
- https://kotlinlang.org/docs/properties.html
- https://kotlinlang.org/docs/visibility-modifiers.html



## Peer instruction



### Question 1

```java
class MyClass {
    public int x = 5;
}

public class Main {
    public static void main(String[] args) {
        MyClass myObj = new MyClass();
        System.out.println(myObj.x);
    }
}
```

What is the output of the above code when executed?

1. 5
2. 0
3. Null
4. Compiler error



### Question 2

```java
class MyClass {
    public int x = 5;

    public MyClass(int x) {
        this.x = 7;
    }
}

public class Main {
    public static void main(String[] args) {
        MyClass myObj = new MyClass(1);
        System.out.println(myObj.x);
    }
}
```

What is the output of the above code when executed?

1. 5
2. 7
3. 1
4. Null
5. Compiler error



## Exercises



### 📝 Exercise 1 - level 1

Create a `Dog` class. The class should have

- 4 attributes that you choose
- 1 method that you choose
- Create 2 instances of dogs using the constructor!

Now call the method on the two dog objects. 



### 📝 Exercise 2 - level 1

Create the classes modelling the following objects. Add both some relevant attributes and some relevant methods

- Recipe
- A Tinder profile
- A musical instrument



### 📝 Exercise 3 - level 2

1. Skriv en klasse der hedder `Lamp`
2. `Lamp` har en boolean instansvariabel der angiver om den er tændt eller slukket. 
3. Når man laver et nyt `lamp`-objekt skal der være en constructor hvor man kan vælge om lampen som udgangspunkt er tændt eller slukket
4. Skriv en metode der hedder `toggleLight`, som tænder lampen hvis den er slukket, og slukker lampen hvis den er tændt. 
5. Lav en klasse `Room` med en main-metode hvor du instantierer forskellige lampeobjekter (skrivebordslampe, sengelampe el. lign.) og tester om de virker som de skal
6. Lav en attribut i `Lamp` der holder øje med hvor mange gange lamp er blevet togglet
7. Lav en metode der returnerer antal gange lampen er togglet.



### 📝 Exercise 4 - level 3

Create a class `Dog` that has the attributes mood, energy, and hunger, with a range of values between 10 (maximum) and 0 (minimum)

Create methods that can change the attributes. If a method attempts to raise an attribute above 10 or lower it below 0, the attribute should remain unchanged, and a message should be printed indicating that the dog is at maximum/minimum [mood/energy/hunger].

Now create a class `DogFarm` that includes a method to generate `Dog` objects. 

In the main method, create an instance of `DogFarm` and generate several `Dog` objects.