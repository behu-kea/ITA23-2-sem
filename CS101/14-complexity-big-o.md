# Complexity and Big O



Thanks. I dont understand O(log n) can you try and explain it to me with a piece of java code?



## Plan





## Code in class

Solve this problem:

- [https://edabit.com/challenge/PZ7rZh9C47CvYHfN2](https://edabit.com/challenge/PZ7rZh9C47CvYHfN2)

- [https://edabit.com/challenge/Mc6Xi4PRw7fDzeMDB](https://edabit.com/challenge/Mc6Xi4PRw7fDzeMDB)



<!--

Modelling if time:

Problem Description:

DSB has contacted us regarding creating a ticket scanner for a train conductor in a train

A ticket has an owner, a from and to station, a start date and a finish date

A owner has a fullname, age and a picture

The ticket scanner should scan peoples tickets and have a list of all the scanned tickets. It should be able to remove tickets. The scanner should at all time be able to report how many people are on a train. 

The scanner should be able to check if a ticket is valid or not. If a ticket is not valid it should not be added to the tickets list

Let's first 

1. Model first (attributes, constructor and empty methods)
2. Then implement functionality

-->



## Exercises



### Big O

You need to figure out the Big O for these code snippets. They are written in js. You dont have to understand what the code exactly does. 



**1**

```java
public Boolean isEven(Integer value) {
    if (value % 2 == 0) {
      return true;
    } else {
      return false;
    } 
}
```



**2**

```java
public Boolean areYouHere(ArrayList<Integer> array1, ArrayList<Integer> array2) {
  for (Integer itemArray1 : array1) {
    for (Integer itemArray2 : array2) {
      if (itemArray1 == itemArray2) return true;
    }
  }

  return false;
}
```



**3**

```java
public ArrayList<Integer> doubleArrayValues(ArrayList<Integer> array) {
  for (int i = 0; i < array.size(); i++) {
    Integer number = array.get(i);
    array.set(i, number * 2);
  }

  return array;
}
```



**4**

```java
public Integer naiveSearch(ArrayList<Integer> array, Integer itemToFind) {
  Integer itemToReturn = new Integer();
  for (Integer item : array) {
    if(item == itemToFind) {
      itemToReturn = item;
    }
  }
  
  return itemToReturn;
}
```



**5**

```java
public String createPairs(ArrayList<Integer> array1, ArrayList<Integer> array2) {
  String pair = "";
  for (Integer itemArray1 : array1) {
    for (Integer itemArray2 : array2) {
      pair = itemArray1 + ", " + itemArray2;
    }
  }

  return pair;
}
```



**6**

```java
public ArrayList<Integer> generateFib(Integer n) {
  ArrayList<Integer> result = new ArrayList<>();

  for (int i = 0; i < n; i++) {
    if (i == 1) {
      result.add(0);
    } else if (i == 2) {
      result.add(1);
    } else {
      result.add(result.get(i - 2) + result.get(i - 3));
    }
  }

  return result;
}
```



**7**

```java
public Object findRandomElement(ArrayList<Integer> array) {
  Integer randomIndex = rand.nextInt(array.size());
  return array.get(randomIndex);
}
```



**8**

```java
public Boolean isPrime(Integer n) {
  // n = 2
  if (n < 2 || n % 1 != 0) {
    return false;
  }
  for (int i = 2; i < n; ++i) {
    if (n % i == 0) {
      return false;
    }
  }
  return true;
}
```



**9**

```java
public Integer factorialOf(Integer n) {
  // n = 3
  switch(n) {
    case 0:
      return 1;
    case 1:
      return 1;
    default:
      return n * factorialOf(n - 1);
  }
}
```





### Problem solving

1. [https://edabit.com/challenge/3CaszbdZYGN4otQD8](https://edabit.com/challenge/3CaszbdZYGN4otQD8)
2. [https://edabit.com/challenge/Y46Xp2pcvTB77bmdD](https://edabit.com/challenge/Y46Xp2pcvTB77bmdD)
3. [https://edabit.com/challenge/4gzDuDkompAqujpRi](https://edabit.com/challenge/4gzDuDkompAqujpRi)
4. [https://edabit.com/challenge/rvsvGvqZ3BzNieKqA](https://edabit.com/challenge/rvsvGvqZ3BzNieKqA)







