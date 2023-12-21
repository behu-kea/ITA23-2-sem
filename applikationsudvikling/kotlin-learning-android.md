# Kotlin learning Android



## Layout & Ui & Components

The `onCreate()` function is the entry point to this Android app and calls other functions to build the user interface.



The  [`setContent()`](https://developer.android.com/reference/kotlin/androidx/compose/ui/platform/ComposeView#setContent(kotlin.Function0)) function within the `onCreate()` function is used to define your layout through composable functions. 



### Jetpack Compose

[https://www.youtube.com/watch?v=6_wK_Ud8--0](https://www.youtube.com/watch?v=6_wK_Ud8--0)

Jetpack Compose er komponentbaseret. Declarative approach. 



All functions marked with the `@Composable` annotation can be called from the `setContent()`

```kotlin
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text(text = "Hello $name!")
}
```

`@composable` is just a Kotlin function.



What was view before is now a composable



The `@Preview` is just what we see in the preview



#### `Text`

This will just draw test. You can add parameteres to it

```kotlin
Text(
  text = "Hello $name!"
	color: Color.Blue
  fontSize = 30.sp
)
```



#### Modifier

Modify and change appearance of the composable



```kotlin
Text(
    text = "Hello $name!",
    color = Color.Blue,
    fontSize = 30.sp,
    modifier = Modifier
        .background(
            color = Color.Red,
        )
        .padding(16.dp)
        .border(
            width = 2.dp,
            color = Color.Red,
            shape = RoundedCornerShape(30.dp)
        ),

)
```



**DP (Density-Independent Pixels)**: Is a virtual pixel based on the pixel density of the screen. 

**SP (Scale-Independent Pixels)**: The same as above but takes the users chosen text size into account

In summary, use DP for all layout sizing, and use SP for text sizes. 



### Layout



#### Column and Row

```kotlin
Column (
    modifier = Modifier
        .background(Color.Red)
        .fillMaxSize(),
    horizontalAlignment = Alignment.End,
    verticalArrangement = Arrangement.Center,
) {
    Text(
        text = "Hello $name!",
        color = Color.Blue,
        fontSize = 30.sp,
        modifier = Modifier
            .background(
                color = Color.Red,
            )
            .padding(16.dp)
    )
    Text(
        text = "Benjamin",
        color = Color.Blue,
        fontSize = 30.sp,
        modifier = Modifier
            .background(
                color = Color.Red,
            )
            .padding(16.dp)
    )
}
```



We can use

```
modifier = Modifier
	.fillMaxSize()
	
// or

modifier = Modifier
	.fillMaxWidth()
	
// or

modifier = Modifier
	.fillMaxHeight()
	
// or

modifier = Modifier
	.size(400dp)
```



The arrangement vs alignment is like justify center, align items

```
horizontalAlignment = Alignment.End,
verticalArrangement = Arrangement.Center
```



#### Box

`Box` composable in Jetpack Compose can be somewhat analogous to a `div` in HTML, particularly in the way it's often used as a container for  other UI elements. It's a layout composable that allows you to stack its children on top of each other



```
Box(
	modifier = Modifier
		.size(400.dp),
  contentAlignment = Alignment.Center
)
```



#### Image

```kotlin
Image(
    painter = painterResource(id = R.drawable.ic_launcher_foreground),
    contentDescription = "android icon"
)
```



### LazyColumn or LazyRow

We can just use a column, but no recycler behavior (only rendering items on screen)



```kotlin
LazyColumn (
    modifier = Modifier
        .height(height = 70.dp)
){
    items(10) { i ->
        androidx.compose.material3.Icon(
            imageVector = Icons.Default.Settings,
            contentDescription = null
        )
    }
}
```



### State

State is value that can change over time

Recomposition: When state changes in a composable, then that composable will redraw. Which means the functions will get called again. 

When state changes, the framework intelligently only recomposes those  parts of the UI that are affected by the changed state, making it  efficient.

So fx in this example:

```kotlin
var count = mutableStateOf(0);
Column {
    Text(
        text = "0",
        fontSize = 30.sp
    )
    Button(onClick = { /*TODO*/ }) {
        Text(text = "Click me")
    }
}
```

The count will get recalled loosing its new value (if fx we say that the count is changed on click) Therefore we need to remember the count (so it is not reassigned to 0)

In Compose, the `remember` function is used to preserve state across recompositions



```
var count = remember{
    mutableStateOf(0);
}
```



#### Full code

```kotlin
setContent {
    var count by remember {
        mutableStateOf(0);
    }
    Column {
        Text(
            text = count.toString(),
            fontSize = 30.sp
        )
        Button(onClick = { count++ }) {
            Text(text = "Click me")
        }
    }
}
```



## Activities & intents



## Lifecycle

Virker som i java. Man overrider nogle metoder



## State management

```kotlin
override fun onResume() {
    super.onResume()
    Log.d(TAG, "onResume Called")
}

override fun onRestart() {
    super.onRestart()
    Log.d(TAG, "onRestart Called")
}

override fun onPause() {
    super.onPause()
    Log.d(TAG, "onPause Called")
}

override fun onStop() {
    super.onStop()
    Log.d(TAG, "onStop Called")
}

override fun onDestroy() {
    super.onDestroy()
    Log.d(TAG, "onDestroy Called")
}

```







## Layout code



```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            Greeting(name = "test");
        }
    }
}

@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Column (
        modifier = Modifier
            .background(Color.Red)
            .fillMaxSize(),
        horizontalAlignment = Alignment.End,
        verticalArrangement = Arrangement.Center,
    ) {
        Text(
            text = "Hello $name!",
            color = Color.Blue,
            fontSize = 30.sp,
            modifier = Modifier
                .background(
                    color = Color.Red,
                )
                .padding(32.dp)
        )
        Text(
            text = "Benjamin",
            color = Color.Blue,
            fontSize = 30.sp,
            modifier = Modifier
                .background(
                    color = Color.Red,
                )
                .padding(16.dp)
        )
        Image(
            painter = painterResource(id = R.drawable.ic_launcher_foreground),
            contentDescription = "android icon"
        )

        LazyColumn (
            modifier = Modifier
                .height(height = 70.dp)
        ){
            items(10) { i ->
                androidx.compose.material3.Icon(
                    imageVector = Icons.Default.Settings,
                    contentDescription = null
                )
            }
        }
    }

}

@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    KotlinAndroidLearningTheme {
        Greeting("test")
    }
}
```



## Architecture

UDF Unidirectional data flow



![CleanShot-2023-12-06-at-15.02.32](assets/CleanShot-2023-12-06-at-15.02.32.png)

With data the ui can be updated

