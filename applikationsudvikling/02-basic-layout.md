# Basic layout



## Learning goals

- `@Composable`
  - `@Preview`
- `Modifier`
- `Column`
- Multiple activities



## Preparation

- Go through [this guide](https://developer.android.com/courses/pathways/android-basics-compose-unit-1-pathway-3). The two following elements are important, the rest is optional
  - Intro to Jetpack Compose (video)
  - Build a simple app with text composables (Codelab)



## `@Composable`

`@composable` annotation informs the Compose compiler that this function is intended to convert data into UI



### `@Preview`





## `modifier`





## `Column`





## Multiple activities



### 1. Create `SecondActivity` Kotlin File

First, you need to create a new Kotlin file for your second activity:

1. In Android Studio, right-click on the `app/src/main/java/your/package/name/` directory in the Project panel.
2. Choose `New` > `Kotlin File/Class`.
3. Name the new class, e.g., `SecondActivity`, and select `File` from the kind options.



Inside the new SecondActivity write

```
package YOUR_PACKAGE_HERE

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.material3.Text

class SecondActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            Text(text = "lol")
        }
    }
}
```

`YOUR_PACKAGE_HERE` could fx be `com.example.basiclayoutexercisesolutions`



### 2. Add the activity to the `manifests/AndroidManifest.xml` file

After the main activity add the following:

```xml
<activity android:name=".SecondActivity" />
```



### 3. Navigate to the activity

In your `MainActivity.kt`

Add the following code:

```kotlin
Button(onClick = {
    val intent = Intent(this, SecondActivity::class.java);
    startActivity(intent);
}) {
    Text(text = "navigate to other Activity")
}
```

This code adds a button that when clicked navigates to the new activity





