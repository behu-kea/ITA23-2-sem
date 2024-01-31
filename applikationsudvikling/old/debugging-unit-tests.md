Optional boilerplate: [Github](https://github.com/nicklasdean/debug-unit-test)

Google Training 1: [Unit tests](https://developer.android.com/codelabs/android-training-unit-tests?index=..%2F..%2Fandroid-training#0)

Google Traning 2: [Debugging](https://developer.android.com/codelabs/android-training-using-debugger?index=..%2F..%2Fandroid-training#0)

# Create a new unit test from a class:

Right-click class and *Generate*

![image-20230310101626049](assets/image-20230310101626049.png)



*Test*

![image-20230310101700924](assets/image-20230310101700924.png)

*Junit4* - check boxes to autogenerate test methods aimed at class methods

![image-20230310101717757](assets/image-20230310101717757.png)

# Arrange, act, assert

https://freecontent.manning.com/making-better-unit-tests-part-1-the-aaa-pattern/

```java
public class UserVerificatorTest {
    @Test
    public void isUserRequiredAge() {
        //Arrange
        //Create instance of object we would like to test
        UserVerificator userVerificator = new UserVerificator();
        
        //Act
        //Generate a result from a certain input
        //Testing whether a user aged 7 will generate a true/falase
        boolean actual = userVerificator.isUserRequiredAge(7);
        
        //Assert
        //Checking result
        assertFalse(actual);
    }
}
```



# Assert methods are overloaded

```java
//Passed
assertTrue(true);
assertFalse(false);

//Not passed
assertEquals("Hello", "Hi");
assertEquals(1,5);

//Passed
assertArrayEquals(new int[]{1,2,3},new int[]{1,2,3});
```



# Exercises

#### 📝 A)

For a user to be verified they have to live up to a certain standard:

- They must be above 18 in age
- A negative number is considered faulty input
- A valid username is longer than 3 characters
- A valid username consists only of lower capital letters
- A valid username is no longer than 20 characters in length

- A valid username does not contain the backslash symbol: */*



Write a class with a method for each validity check.

Write unit tests for each of the methods, with a test-design that takes boundaries into account.

- Data input from the user is **not** important at this stage



#### 📝 B)

- Make it work as an application such that:
  - A user can enter their username and age
  - They will be directed to a "succes"-Activity if age and username is approved
  - They will be directed to a "failure"-Activtiy if age and username is not approved



#### 📝 C) (Advanced) optional

We would like to add another feature:

- A user can pick: 
  - Their birthday 
  - A date in the future. 
- The application will calculate and display how many birthdays the user will celebrate between the dates.

https://developer.android.com/reference/android/widget/DatePicker

Implement unit tests that will tests if the application calculates correctly

- Remember boundary analysis
