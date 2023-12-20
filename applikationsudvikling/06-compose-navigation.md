# Compose navigation



## Preparation

- https://developer.android.com/jetpack/compose/navigation
- [Jetpack Compose Navigation: The Complete Beginner's Course](https://youtu.be/jt5sJEnDsSQ?si=HLF3qV0BaRB8MhuZ)



## `Navhost`

An empty container that displays the composables that are navigated to. Kind of like `index.html`shows different routes in react.

A NavHost is a Composable that displays other composable destinations, based on a given route. 

As you navigate between composables, the content of the `NavHost` is automatically [recomposed](https://developer.android.com/jetpack/compose/mental-model#recomposition).



## `NavController`

An object that manages app navigation within a `NavHost`. The `NavController` orchestrates the swapping of destination content in the `NavHost` as users move throughout your app.



### Arguments

Sending arguments to another route is a bit tricky. Here is how it works:



### First setup the route

First we need to tell Compose that the route can take an argument, we do that in the route by adding the `sendArgumentsHere/{name}`. This is very much like in NodeJS/Express. We now need to tell Compose navigation that the route `sendArgumentsHere` can take some arguments. We do that with the `arguments = listOf(navArgument("name") { type = NavType.StringType })`. Here we tell Compose navigation that it can take one parameter that has a String as a type. 

Now to get the actual argument we write this:

```kotlin
val name = backStackEntry.arguments?.getString("name") ?: return@composable
SendArgumentsHere(name)
```

The first line gets the name argument from the backStack if the name argument is passed. Then we call the `SendArgumentsHere` Composable function with that argument



### Add the argument to the Composable

The Composable function need to take the name argument

```kotlin
@Composable
fun SendArgumentsHere(name: String) {
    Text(text = name)
}
```



### Navigate to the route with a specific name

This is the easy part:

```kotlin
navController.navigate("sendArgumentsHere/Benjamin");
```

Here we send the string `"Benjamin"` to the `SendArgumentsHere` composable function



### BackStack

[https://developer.android.com/guide/navigation/backstack](https://developer.android.com/guide/navigation/backstack)

The back stack consists of a stack of navigation screens. Every time you navigate to a new screen, the with fx `navController.navigate("screen1")` the stack new screen is added to the back stack. When the back button is pressed, the latest screen on the backstack is removed (or [poped](https://www.youtube.com/watch?v=o724TbnN4Mk) to be more precise)



### `popBackStack`

We can pop the back stack ourselves by calling `navController.popBackStack()`. This will be like pressing the back button

We can also pop back to a specific route `navController.popBackStack("screen1", false)`. Everything above that route will pop. The second argument specifies if the route itself should also be poped. 



## Code example

```kotlin
package com.example.navigation

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.Column

import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.lazy.LazyColumn
import androidx.compose.foundation.lazy.items
import androidx.compose.material3.Button
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.getValue
import androidx.compose.runtime.mutableIntStateOf
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.runtime.setValue
import androidx.compose.ui.Modifier

import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import androidx.navigation.NavController
import androidx.navigation.NavHostController
import androidx.navigation.NavType
import androidx.navigation.compose.NavHost
import androidx.navigation.compose.composable
import androidx.navigation.compose.rememberNavController
import androidx.navigation.navArgument
import com.example.navigation.ui.theme.NavigationTheme


class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContent {
            val information by remember {
                mutableStateOf( mutableMapOf<String, Int>("price1" to 6));
            }

            val navController = rememberNavController()
            Column {
                Text(text = "asd")
                NavHost(navController = navController, startDestination = "screen1") {
                    composable("screen1") {
                        Screen1("benjamin",
                            onNavigate = {
                            information["price2"] = 2;
                            navController.navigate("screen2")
                            println(navController.currentBackStackEntry)
                        }, onToArguments = {
                            navController.navigate("sendArgumentsHere/Benjamin")
                        })
                    }
                    composable("screen2") {
                        Screen2(id = 2, onNavigate = {
                            information["price3"] = 5;
                            navController.navigate("screen3")
                            println(navController.currentBackStackEntry)
                        })
                    }
                    composable("screen3") {
                        Screen3(information, onBackToStart = {
                            navController.popBackStack("screen1", false);
                            println(navController.currentBackStackEntry)
                        })
                    }
                    composable("sendArgumentsHere/{name}", arguments = listOf(navArgument("name") { type = NavType.StringType })) { backStackEntry ->
                        val name = backStackEntry.arguments?.getString("name") ?: return@composable
                        SendArgumentsHere(name)
                    }
                }
            }
        }
    }
}

@Composable
fun Screen1(name: String, onNavigate: ()-> Unit, onToArguments: () -> Unit) {
    Column {
        Text(
            text = "Screen 1",
            fontSize = 32.sp
        )
        Text(
            text = "Hello $name!"
        )
        Button(onClick = onNavigate) {
            Text("Go to Screen 2")
        }
        Button(onClick = onToArguments) {
            Text("To arguments screen")
        }
    }
}

@Composable
fun Screen2( id: Int, onNavigate: () -> Unit) {
    Column {
        Text(
            text = "Screen 2!",
            fontSize = 32.sp
        )
        Button(onClick = onNavigate) {
            Text(text = "Go to screen 3")
        }
    }
}

@Composable
fun Screen3(status: MutableMap<String, Int>, onBackToStart: () -> Unit) {
    Column {
        Text(
            text = "Screen 3",
            fontSize = 32.sp
        )
        Text(
            text = "We are at ${status["price1"]}, ${status["price2"]}, , ${status["price3"]}!!!"
        )
        Button(onClick = onBackToStart) {
            Text(text = "Back to start");
        }
    }
}

@Composable
fun SendArgumentsHere(name: String) {
    Text(text = name)
}
```



## Exercise

Sådan noget main screen, til login, til dashboard, måske log ud







