# Testing



## Preparation

[Write your first Compose UI test](https://www.youtube.com/watch?v=JyUJZvJ-OV8)



[Testing in android playlist](https://www.youtube.com/watch?v=EkfVL5vCDmo&list=PLQkwcJG4YTCSYJ13G4kVIJ10X5zisB2Lq&index=1)







TDD - Test driven development. Write tests first. Then start developing code. Could maybe be huge in the age of AI



What makes a good test:

- Scope - How much coverage 
- Speed - The faster then more you will use it
- Fidelity- How close to real scenario
- Not a flaky test



Three types of tests:

1. Unit tests - single units. Fx function `getSum` . 70% of our app
2. Integration tests - How two components work together. Interaction betwen components. 20 %
3. UI tests/end-to-end - Whole interaction. Log in, then click a button etc



## Test strategy

- **Success path:** The success path tests - also known as happy path tests, focus on testing the functionality for a positive flow.
- **Error path:** The error path tests focus on testing the  functionality for a negative flow–that is, to check how the app responds to error conditions or invalid user input.
- **Boundary case:** A boundary case focuses on testing boundary conditions in the app. 



`androidtest` vs `test` folder

`androidtest` - Everything that runs on the emulator or need some android context

`test` - Everything else. Fx testing a `getSum` function does not need android



## Dependencies

The dependencies should be made for each `androidtest` vs `test` . Here it is called `testImplementation` and `androidTestimplementation`





## Writing the test



```kotlin
@Test
fun `empty username returns false`() {
	val sum = getSum(listOf(1,2,3));
	assertThat(sum).equals(6)
}
```



### `@before` and `@after`

If we want some code to run before each test is run

```
@Before
fun setup() {
	// do something here
}
```



After is usually meant to destroy objects or close database connections

```
@After
fun teardown() {
	// do something here
}
```





## UI tests



```kotlin
@get: Rule
val rule = createComposeRule()
```



### Create a test

```kotlin
@Test
fun addNote() {
    rule.setContent { AppNavigation(notesViewModel); }

    rule.onNodeWithText("Add new note")
        .performClick()

    rule.onNodeWithText("Title")
        .performTextInput("olol")

    rule.onNodeWithText("Content")
        .performTextInput("olol1")

    rule.onNodeWithText("Save note")
        .performClick()

    rule.onNodeWithText("olol")
        .assertExists("The note with title 'olol' was not found in the list.")
}
```



## Exercises



## Notes app

For the notes app we were working on last time, lets write some tests for that app. The repo can be found [here](https://github.com/behu-kea/ita-23-2-sem-code/tree/for-testing-lecture/noteapp) with all features implemented



### Unit tests





### UI tests

You have to write some ui tests that test the following:

- When creating a new note that note will show up in the overview
- When searching for a note the correct notes will be shown in the overview
- Changing a note will change it in the overview







## Tværfagligt projekt

Lav nogle unit tests og nogle UI tests for jeres app



