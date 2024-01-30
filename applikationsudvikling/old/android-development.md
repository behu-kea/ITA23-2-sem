# Android development



- First install Android Studio



## Activity

Single focused thing that the user can do. Typically has a layout



## Gradle

Like npm for java libraries

Er ikke sådan helt med på det her endnu. Under Gradle Scripts ligger en fil der styrer det der gradle noget. 

Måske se en youtube video her



## Structure

- `java` - all the java files will go here
  - `com.example.helloworld` - where the java files lives
  - `com.example.helloworld (AndroidTest)` - Used for testing
  - `com.example.helloworld (test)` - Used for testing

- `res` - this is related to the interface. Holds ressources such as images, strings and layouts
  - `layout` - will contain the different layouts (screens)
  - `drawable` - will contain all ressources like images
- `AndroidManifest.xml` - Provide essential information about the app to the abdroid system. Like icon, label, category, theme. 



The MainActivity.java is like the index.html. The first activity the user sees.





## Using a virtual device

Using the device manager we define the characteristics of a device and then emulate it.



Tools -> device manager



## Running on your phone

https://developer.android.com/codelabs/android-training-hello-world?index=..%2F..%2Fandroid-training#5



## Logging

Logging is done using logical. In the bottom click the logcat tab. 

It is possible to set the log type. Per default it is verbose. 

To log something write: `Log.d("MainActivity", "Hello World");`

`mainactivity` is a tag that can be filtered upon when looking at the logs. 



## UI

UI on Android consists of a hierarchy of obejcts called views. Every element on the screen is a view. `View` is the base class. There are some different ones:

- `TextView`
- `Editview`
- `Button`
- `ScrollView`



The java code that displays the UI is in a class that extends `Activity`.  An activity is associated with a layout of views defined by an xml file. 

Fx `MainActivity` displays a layout defined in `activity_main.xml` what has a `TextView`.



### Constraints

Represents alignment or constraint to another view

**hvordan præcis fungerer de her??**



### Palette

UI elements



### Component Tree

Shows the hierarchy of the views.  A child inherits the attributes of its parent.



### Attributes

Offers access to the xml file. 



### Height and width

View inspector. Avoid setting fixed values becuase screen sizes change

For the width and the height you can set different values:

- `match_constraint` will expand until it meets its parent
- `wrap-content` will expand based in the content inside of the element



### Colors.xml

Defines the standard colors in the application



### Fontsize

Use dp units when you specify font sizes so that the sizes are adjusted for both the screen density and the user's preference



### Gravity

dont understand this



### Adding text as ressources

Text should not be hardcoded they should be represented as ressources.Easier to manage in seperate file.

They are saved in the `strings.xml` file under values



### Click listener

There are different ways of adding clicklisteners to a button:

1. In the design tab attributes there is an `onclick` method. Write the java method in the class that belongs to the activity
2. In the xml add `android:onClick="showToast"`. Where `showToast` is the name of the method. New hover over the `showToast` method and click `Create ‘showToast(view)' in MainActivity`



### Text

Refer to text messages in Java by using `R.string.RESSOURCE_NAME`



### `onCreate` method

Inflate the layout. Means set the content of the view to the XML layout



### Landscape vs horizontal

To create a new view for landscape click the dropdown that says `activity_main.xml` and click on `Create landscape qualifier`

This will create a new folder with the main_activity.xml inside of it. I think the folder naming is what controls what should be shown.

**How do i show maximum width?**



### UI Layouting

**Don't quite get it yet**

pack align guidelines 

gravity



#### Weight

The `android:layout_weight` attribute indicates how much of the extra space in the `LinearLayout` will be allocated to the `View`.

Like flex grow and flex shrink



https://developer.android.com/codelabs/constraint-layout#0



### `LinearLayout`

Is a `ViewGroup` that arranges the views inside it vertically or horizontally

Has width, height and orientation. Kind of like flex



### `RelativeLayout`

Views are positioned relative to each other





### `TextView`

Add `android:autoLink="web"` to automatically create links



### `ScrollView`

can only contain one child. But that view can be a LinearLayout



## Activity and intents

`MainActivity.java` is main activity just like `index.html`



When a new activity starts, that new activity is pushed onto the back stack and takes user focus



An activity is started with an intent which is a message that requests an action from another activity. 

Intents can be explicit og implicit

- Explicit you know exactly what class is the target of the intent
- Implicit you dont know the target but have a general action to perform



### Activity hierarchy

Actiities can have hierarchies. When going back fx it goes to the parents of the activity. You do that in the manifests -> AndroidManifest.xml file. To the activity you add the `meta-data android:name="android.support.PARENT_ACTIVITY"` xml tag



```xml
<activity android:name=".SecondActivity"
    android:label = "Second Activity"
    android:parentActivityName=".MainActivity">
    <meta-data android:name="android.support.PARENT_ACTIVITY"
        android:value="com.example.android.twoactivities.MainActivity" />
</activity>

```



### Intent

To create a new explicit intent write the following code:

```java
Intent intent = new Intent(this, SecondActivity.class);
startActivity(intent);
```



#### Passing data

Your intent object can pass data to the target activity in two ways: in the data field, or in the intent *extras*. 

The intent *extras* are key/value pairs in a  [`Bundle`](https://developer.android.com/reference/android/os/Bundle.html). The key is in this following example 1 and the message some string

That is done through `intent.putExtra(EXTRA_MESSAGE, mMessageEditText.getText().toString());`



**Sending**

```java
public static final String EXTRA_MESSAGE = "com.example.android.twoactivities.extra.MESSAGE";
public static final int TEXT_REQUEST = 1;
Intent intent = new Intent(this, SecondActivity.class);
// use key value pairs to store data
intent.putExtra(EXTRA_MESSAGE, mMessageEditText.getText().toString());
startActivity(intent, TEXT_REQUEST);
```



**Receiving**

Use the key to get the data stored

```java
Intent intent = getIntent();
String message = intent.getStringExtra(MainActivity.EXTRA_MESSAGE);
```



### Getting data back from a view



```java
public void onActivityResult(int requestCode,
                                 int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        Log.d(LOG_TAG, "asd");
        Log.d(LOG_TAG, data.getStringExtra("com.example.android.twoactivities.extra.REPLY"));
}
```





## Lifecycle

You can override differnet methods to access specific events in an activities lifecycle

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    mMessageEditText = findViewById(R.id.editTextTextPersonName);
    replyFromSecondActivityView = findViewById(R.id.replyFromSecond);
}

@Override
protected void onStart() {
    super.onStart();
}
```



![Diagram of the App Lifecycle](assets/59d40f71d715436.png)





### Storing user data

All configuration changes result in the current `Activity` being destroyed and recreated as if it were new. Therefore users can loose data that they fx were writing. 

To keep from losing data in an `Activity` when it is unexpectedly destroyed and recreated, you need to implement the `onSaveInstanceState()` method



#### Storing data in bundle

```java
@Override
public void onSaveInstanceState(Bundle outState) {
    super.onSaveInstanceState(outState);
    outState.putBoolean("reply_visible", true);
}
```



#### Getting that data back

In the `onCreate` method you have the `Bundle savedInstanceState`

```java
savedInstanceState.getString("reply_visible")
```



## Implicit intents

With an implicit intent, you initiate an activity without knowing which  app or activity will handle the task. For example, if you want your app  to take a photo, send email, or display a location on a map, you  typically don't care which app or activity performs the task.



# Troubleshoot: 

##### adb issues + not able to boot device, daemon starts, but a process on a port fails (windows):

- (maybe) **Preferences/settings** > **Tools** > **Emulator** > **When encountering  snapshots incompatible...** > 
- Set to Delete automatically

![image-20230307130737240](assets/image-20230307130737240.png)

- (Certainly) **Build,Execution ,Deployment** > **Debugger**> **Uncheck enable adb mDSN for wireless debugging**

![image-20230307131100931](assets/image-20230307131100931.png)
