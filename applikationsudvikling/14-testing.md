# Testing



## Overview





## Preparation

- [https://developer.android.com/jetpack/compose/testing](https://developer.android.com/jetpack/compose/testing) (se video læs om Semantics, Setup og Testing APIs)

- [Testing in android playlist](https://www.youtube.com/watch?v=EkfVL5vCDmo&list=PLQkwcJG4YTCSYJ13G4kVIJ10X5zisB2Lq&index=1)





Three types of tests:

1. Unit tests - single units. Fx function `getSum` . 70% of our app
2. Integration tests - How two components work together. Interaction betwen components. 20 %
3. UI tests/end-to-end - Whole interaction. Log in, then click a button etc





TDD - Test driven development. Write tests first. Then start developing code. Could maybe be huge in the age of AI



What makes a good test:

- Scope - How much coverage 
- Speed - The faster then more you will use it
- Fidelity- How close to real scenario
- Not a flaky test



3. 



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

These are teste that test the ui more than the functionality. That means we write code that clicks buttons, writes text in input fields and check if the right elements are on the page



To create a UI test we must first create a rule that we can use to interact with our app

```kotlin
@get: Rule
val rule = createComposeRule()
```

you could say that `rule` is kind of like `document` in javascript. With the `document` we can get elements, click and set text in input fields. 



### Create a test

To create a test write the `@Test` annotation before a function. This function will now be part of your tests. 

First we have to specify what content we are testing. We can test the full application, but we can alos just test a `@Composable`. 

```kotlin
rule.setContent { AppNavigation(notesViewModel); }
```

`AppNavigation(notesViewModel)` is a `Composable`



#### Getting a node

When we have defined the content we need to start selecting some elements. In javascript we did this with `document.querySelector` . Using a `rule` we do that with `rule.onNodeWithText("Add new note")`. Here we get a node that has the text `Add new note`. 



We can also select a node anothe way like this:

```kotlin
rule.onNode(
	hasText("Add new note")
	and
	hasClickAction()
)
```

We can also use tags. 



#### Create some action

When we have a node, we can create an action on that note, fx click it, write text in the node etc.

Here we click a node

```kotlin
rule.onNodeWithText("Add new note")
	.performClick()
```



Here we write some text in a node

```kotlin
rule.onNodeWithText("Title")
	.performTextInput("olol")
```



#### Check stuff

Now we can check if some node was created with our action:

```kotlin
rule.onNodeWithText("olol")
	.assertExists()
```



#### Full example

Here is an example of a test that tests that creating a new node works as expected

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
        .assertExists()
}
```



Read more about UI testing in compose here: [https://developer.android.com/jetpack/compose/testing](https://developer.android.com/jetpack/compose/testing)



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



