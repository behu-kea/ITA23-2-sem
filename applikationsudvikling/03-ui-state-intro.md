# UI & State

Compose is a declarative UI framework, meaning that you *declare* how the UI should look in your code.



## Overview

- Peer instruction
- Me coding a small app



## Preparation

- Gå igennem de her punkter i [den her guide](https://developer.android.com/courses/pathways/android-basics-compose-unit-2-pathway-3)
  - Understanding state in Compose - Video
  - Intro to state in Compose - Codelab



## @Composable





## Composition

The *Composition* is a description of the UI built by Compose when it executes composables. Compose apps call composable functions to transform data into UI.



### Initial composition

Initial composition is a creation of the UI by Compose when it executes composable functions the first time.



### Recomposition

Recomposition is the process of running the same composables again to update the tree when their data changes.



Recomposition to update the Composition of the app. When fx some ui needs to be updated when some input is changed



The *Composition* is a description of the UI built by Compose  when it executes composables. Compose apps call composable functions to transform data into UI. If a state change happens, Compose re-executes  the affected composable functions with the new state, which creates an  updated UI—this is called *recomposition*. Compose schedules a *recomposition* for you.

When Compose runs your composables for the first time during *initial composition*

*Recomposition* is when Compose re-executes the composables that  may have changed in response to data changes and then updates the  Composition to reflect any changes.

The Composition can only be produced by an *initial composition* and updated by *recomposition*. The only way to modify the Composition is through *recomposition*. To do this, *Compose needs to know what state to track* so that it can schedule the recomposition when it receives an update.

The value returned by the `mutableStateOf()` function:

- Holds state, which is the bill amount.
- Is mutable, so the value can be changed.
- Is observable, so Compose observes any changes to the value and triggers a recomposition to update the UI.



## State

State in an app is any value that can change over time.



### `remember`

`remember` keeps a value (any value) consistent across recompositions.



If the data is primitive (`Int`, `Double`, `Boolean`) the use `mutableStateOf` like this:

```kotlin
var information2 by remember {
   mutableStateOf(2)
}
```

If it is complex (`List`, `Map`, `String`) then use the relevant `mutable` function. Fx if a `Map` use `mutableMapOf`. When the function is called it returns an instance of that type

```kotlin
var information by remember {
    mutableStateOf( mutableMapOf<String, Int>("price1" to 6));
}
```



### Field value update

Update the text inside the field using a lambda



## State hoisting

A *stateless* composable is a composable that doesn't have a  state, meaning it doesn't hold, define, or modify a new state. On the  other hand, a *stateful* composable is a composable that owns a piece of state that can change over time.

State hoisting is a pattern of moving state to its caller to make a component stateless.



## Exercises - Indkøbsseddel



Den her opgave er en Rite-of-passage for udviklere. Lidt ligesom hello world. Alle skal have prøvet at lave deres egen indkøbsseddel eller notepad. Funktionaliteterne er de samme:

I skal lave en indkøbsseddel app med disse features:

- Man skal kunne oprette nye elementer til indkøbssedlen
- Hvis der ikke er nogle elementer skal der stå "No elements, please create a new element"
- Elementerne skal stå i en liste
- Når man er færdig med et element skal man kunne strege den ud



Nice to have

- Man skal kunne flytte rundt på elementerne, så fx et element der er i bunden kan skubbes op i toppen
- Man skal kunne søge i sine elementer
- Man skal kunne sortere sine elementer på en måde (måske alfabetisk eller oprettelses tidspunkt)



Prøv først at få jeres interface på plads. Sketch gerne først og så få det ned på papir. Processen er rigtig fint beskrevet [her](https://developer.android.com/codelabs/basic-android-kotlin-compose-art-space?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-2-pathway-3%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-art-space#1). Altså hvordan man kommer fra wireframe/prototype til compose elementer

![AI generated Image for inspiration](https://files.oaiusercontent.com/file-vJ8HUzLOxmSC576yCumXodi0?se=2023-12-14T15%3A33%3A50Z&sp=r&sv=2021-08-06&sr=b&rscc=max-age%3D31536000%2C%20immutable&rscd=attachment%3B%20filename%3Dbc21233f-8c9b-409e-93ab-c7e94200663d.webp&sig=BgSHIH1g9HgtZ4h/7vNLu10bq2CLULXgrvEBH8XqkuM%3D)

