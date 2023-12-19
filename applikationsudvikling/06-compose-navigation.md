# Compose navigation



## Preparation

- https://developer.android.com/jetpack/compose/navigation





## `Navhost`

An empty container that displays the composables that are navigated to. Kind of like `index.html`shows different routes in react.

A NavHost is a Composable that displays other composable destinations, based on a given route. 

As you navigate between composables, the content of the `NavHost` is automatically [recomposed](https://developer.android.com/jetpack/compose/mental-model#recomposition).



```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContent {
            //val information: MutableMap<String, Int> = mutableMapOf("price1" to 4);

            var information by remember {
                mutableStateOf( mutableMapOf<String, Int>("price1" to 6));
            }

            information.put("price1", 10);

            val test = mutableMapOf<String, Int>();
            test.put("price1", 10);

            val navController = rememberNavController()
            Column {
                Text(text = "asd")
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
                    composable("status") {
                        Status(information)

                    }
                }
            }

        }
    }
}

@Composable
fun Greeting(name: String, onNavigate: ()-> Unit) {
    Text(
        text = "Hello $name!"
    )
    Button(onClick = onNavigate) {
        Text("Go to Friends List")
    }
}

@Composable
fun Greeting2( id: Int, onNavigate: () -> Unit) {
    Text(
        text = "We are at $id!!!"
    )
    Button(onClick = onNavigate) {
        Text(text = "Send to status")
    }
}

@Composable
fun Status(status: MutableMap<String, Int>) {
    Text(
        text = "We are at ${status["price1"]}, ${status["price2"]}, , ${status["price3"]}!!!"
    )
}
```





## `NavController`

An object that manages app navigation within a `NavHost`. The `NavController` orchestrates the swapping of destination content in the `NavHost` as users move throughout your app.





## Dont understand yet

`popBackStack`



And the `backStack`