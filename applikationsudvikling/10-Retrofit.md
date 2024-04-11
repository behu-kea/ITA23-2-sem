# Retrofit

Reference project: https://github.com/nicklasdean/retrofit-basic



- Read the documentation to the following API: 
  - https://www.boredapi.com/documentation



## Make it work: GET request

#### Exercise A

Without using the android framework (empty project - as seen in the reference project)

- Create an API interface, Model / DTO and retrofit instance such that: 
  - You can fetch a single random event and print its properties to the console

#### Exercise B

Parameters: (@Query not @Path)

![image-20240411093741953](assets/image-20240411093741953.png)

Without using the android framework (empty project - as seen in the reference project)

- Expand the project with another API call with parameters
- The program takes a number of participants as parameter and returns a random activity with a given numbner of participants
  - The user inputs the parameters by standard input: readLine()

#### Exercise C

Without using the android framework (empty project - as seen in the reference project)

- Expand the project with another API call with parameters
- The program takes a specified accessibility in an inclusively constrained range of price (min / max price)
  - The user inputs the parameters by standard input: readLine()

- Implement with a call instead of returning the Activity object
  - If the response is successful print the activity
  - If the response if not successful print "failure"



## Make it work: POST request

- Read the documentation to the following API POST CREATE request: 

  - Register - Successful
  - Register - Unsuccessful
  - Login - Successful
  - Login - Unsuccessful
  
  ![image-20240407110259710](assets/image-20240407110259710.png)

![image-20240407110433754](assets/image-20240407110433754.png)

![image-20240407110345839](assets/image-20240407110345839.png)

![image-20240407110445782](assets/image-20240407110445782.png)

#### Exercise A

Without using the android framework (empty project - as seen in the reference project)

- Create an API interface, Model / DTO and retrofit instance such that:
  - You can POST an email and password and receive a response for <u>registration</u>
    - If successful: Print the response to the console
    - If unsuccessful: Print the response to the console

  

- Create an API interface, Model / DTO and retrofit instance such that:

  - You can POST an email and password and receive a response for <u>login</u>
    - If successful: Print the response to the console
    - If unsuccessful: Print the response to the console

Reference: https://github.com/nicklasdean/retrofit-basic/tree/main/app/src/main/java/com/example/reqresPOSTexample



## Make it right: Repository pattern

**Refactor** the code such that:

- Registration & Login are both contained in a repository class that exposes 2 functions:
  - Create User
  - Login User

Client code (or other developers) should be able to use the repository class without understanding details of the implementation.

- If you have several retrofit instances, both of these are instantiated in the repository



## Advanced (Optional) 

Use the following API: https://anapioficeandfire.com/

- Create a model and retrofit instance such that a user can request a character by name and receive all data about the character