# Types, debugging, for loop and input



## Learning goals

- Get to run a Java program
- Learn how to create variable of different types in Java
- Primitive types vs object types
- Learn to work with the Scanner



## Preparation

- Read Chapter 1 & 2 in Think Java



## Plan

- 40 minutes of lecturing
- 60 minutes of exercises in random pairs
- 15 minutes of recap of exercises



## Code in class

<!--

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        System.out.println("ss");

        // const age = 2;
        int age = 2;
        // const height = 1.78;
        double height = 1.78;

        // primitive types vs object types

        // const name = "Benjamin";
        String name = "Benjamin";
        // const letter = "a";
        char letter = 'a';

        // const isLucky = false;
        boolean isLucky = false;

        // const prices = [];
        // Dette virker ikke, da vi kun kan indsætte object types i et arraylist
        // ArrayList<int> prices = new ArrayList<int>();
        // Derfor gør vi som vist nedenfor. Med en wrapper klasse Integer der bare giver os adgang til int'en
        ArrayList<Integer> prices = new ArrayList<Integer>();
        
        prices.add(3);
        // prices.push(3);

        // const nameAndAge = {};
        HashMap<String, Integer> nameAndAge = new HashMap<>();
        // nameAndAge["benjamin"] = 35;
        nameAndAge.put("benjamin", 35);
        // console.log(nameAndAge["benjamin"]);
        System.out.println(nameAndAge.get("benjamin"));

        for (int i = 0; i < 3; i++) {
            System.out.println(i);
        }

        // Getting input form the user
        Scanner scanner = new Scanner(System.in);  // Create a Scanner object
        System.out.println("Enter username");

        String userName = scanner.nextLine();  // Read user input
        System.out.println("Username is: " + userName);
    }
}
```

-->



## Exercises 

Feel free to use either the Think Java book, this gitbook: [https://behu.gitbook.io/java-first-semester/](https://behu.gitbook.io/java-first-semester/) or any other online ressource you like

Work in pairs

1. https://behu.gitbook.io/java-first-semester/topics/basics/variables-operators-expressions#exercise-1 20 min
2. https://behu.gitbook.io/java-first-semester/topics/basics/variables-operators-expressions#exercise-5 10 min
3. https://behu.gitbook.io/java-first-semester/topics/basics/strings#execise-2 15 min
5. Create an `ArrayList`. Add some prices to the `ArrayList`. Now  find the average price of the `ArrayList`. 20 min
6. Create a `HashMap` that contains the numberplate of a car and that cars color 10 min
7. https://behu.gitbook.io/java-first-semester/topics/basics/working-with-inputs#question-1-1 15 min
8. https://behu.gitbook.io/java-first-semester/topics/basics/working-with-inputs#exercise-2 - 20 min







