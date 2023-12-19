# Compose navigation



## Preparation

- https://developer.android.com/jetpack/compose/navigation





## `Navhost`

An empty container that displays the composables that are navigated to. Kind of like `index.html`shows different routes in react.

A NavHost is a Composable that displays other composable destinations, based on a given route. 

As you navigate between composables, the content of the `NavHost` is automatically [recomposed](https://developer.android.com/jetpack/compose/mental-model#recomposition).



```kotlin

var information by remember {
    mutableStateOf( mutableMapOf<String, Int>("price1" to 6));
}

val navController = rememberNavController()

NavHost(navController = navController, startDestination = "profile") {
    composable("profile") {
        Greeting("benjamin", onNavigate = {
            information["price2"] = 2;
            navController.navigate("friendslist")
        })
    }
    composable("friendslist") {
        Greeting2(id = 2, onNavigate = {
            information["price3"] = 5;
            navController.navigate("status")
        })
    }
    composable("status") { Status(information) }
}
```





## `NavController`

An object that manages app navigation within a `NavHost`. The `NavController` orchestrates the swapping of destination content in the `NavHost` as users move throughout your app.





## Dont understand yet

`popBackStack`



And the `backStack`