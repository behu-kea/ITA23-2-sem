# UI & State

Compose is a declarative UI framework, meaning that you *declare* how the UI should look in your code.



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



## State hoisting

A *stateless* composable is a composable that doesn't have a  state, meaning it doesn't hold, define, or modify a new state. On the  other hand, a *stateful* composable is a composable that owns a piece of state that can change over time.

State hoisting is a pattern of moving state to its caller to make a component stateless.
