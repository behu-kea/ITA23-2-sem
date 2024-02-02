# Exercises

#### **Inheritance**

**A)**

Write an abstract class called `Animal` An `animal` has 3 attributes:

- name
- nrOfLegs
- isMammal

Animal has a method: makeSound() that prints the sound of the an-
imal.

- Create 2 animal classes that extends the Animal class and overrides
  the method to produce their unique sound.
- Create a list, add 5 animals to the list and print every animals sound.
- Override the `toString` method such that if an animal object is printed, it will return a string in the following format: [name=`name`, nrOfLegs=`nrOfLegs`, isMammal=`isMammal`]



**B)** **Advanced (Optional)**

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

#### `Sedan`

Create a subclass of `Car` class and name it as `Sedan`. The `Sedan` class has the following fields and methods.

- `length`

- `getSalePrice()`

If the `length` is more than 20 meters then 5% discount otherwise 10% discount



#### `AutoShop`

Create an `AutoShopApp` script which contains the `main()` method. Perform the following within the `main()` method.

Create an instance of `Sedan` class and initialize all the fields with appropriate values.

Create two instances of the `Ford` class and initialize all the fields with appropriate values.

Create a `Truck` instance

Print  the sale prices of all instances.



#### Access modification

**A)**

- Create a class Product with a constructor
- A product has an String: itemName,  Int: quantity and Int: price
  - The name has a public getter & setter
  - The quanty has a public getter but private setter
  - The price has no getters or setters - it is private
- To get a price from a product object a function called getPriceAsString should be called.
  - The function returns a string containing the price in a format such as: `$100.00`
  - eg. a price of 50 returns the string `"$50.00"`
  - You will to [convert](https://kotlinandroid.org/kotlin/kotlin-convert-integer-to-string/#:~:text=To%20convert%20a%20given%20int,given%20integer%20value%2C%20say%20intValue%20.&text=The%20function%20returns%20a%20string,in%20the%20given%20integer%20value.) an integer to a String



**B)**

- Create a class Person
- A person has a cpr number and name
- A person has a private function that calculates the age of the person by their CPR number
- A person has a field: age.
  - The field is public and uses the private function to return a result.
  - The setter is private, as no one from outside should be able to use the function



**B)**