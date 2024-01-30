# Android recap -  Key Concepts



## 1. Layout

Layouts in Android define the structure and appearance of your app's UI. They are typically created using XML files.

### Common Layout Types

- **LinearLayout**: Positions views in a row or column.
- **RelativeLayout**: Positions views relative to each other or their parent container.
- **ConstraintLayout**: Flexible layout that allows for complex view positioning and sizing.



### Example: LinearLayout

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Button 1"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Button 2"/>

</LinearLayout>
```



## 2. Event Listeners - onClick

Event listeners allow your app to respond to user interactions like button clicks.



 **activity_main.xml**

```xml
<Button
    android:id="@+id/button"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:text="Click me"
    android:onClick="onButtonClick"/>
```



**MainActivity.java**

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void onButtonClick(View view) {
        System.out.println("Button clicked");
    }
}
```



## 3. Creating Multiple Activities

In Android Studio, right-click the `app/java` folder, then navigate to `New > Activity` and choose the desired activity template (e.g., `Empty Activity`).

Name the activity (e.g., `SecondActivity`) and click `Finish`.

Android Studio will generate the following files:

- `SecondActivity.java`: The Java class file for the new activity.
- `activity_second.xml`: The layout XML file for the new activity.

Android Studio should automatically add the new activity to the `AndroidManifest.xml` file. If not you need to add that yourself



## 4. Intents

Intents are used to navigate between activities or to interact with components of the system or other apps.



There are two ways of starting an activity:



### 1. Opening another activity

**MainActivity.java**

```java
public void openSecondActivity(View view) {
    Intent intent = new Intent(MainActivity.this, SecondActivity.class);
    startActivity(intent);
}
```



To pass data between activities, use the `putExtra()` method

**MainActivity.java**

```java
public void openSecondActivity(View view) {
    Intent intent = new Intent(MainActivity.this, SecondActivity.class);
    intent.putExtra("key", "value123");
    startActivity(intent);
}
```



In the receiving activity, use the `getIntent()` method to retrieve the data.

**SecondActivity.java**

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_second);

    Intent intent = getIntent();
    String value = intent.getStringExtra("key");
    System.out.println(value); //value123
}
```



### 2. Opening another activity but expecting data to come back

First create a new intent to open the `SecondActivity`

**MainActivity.java**

```java
 public void openSecondActivity(View view) {
    Intent intentToOpenSecondActivity = new Intent(this, SecondActivity.class);
   
    startActivityForResult(intentToOpenSecondActivity, 123);
}
```



Now in the `SecondActivity` when a button is clicked fx put some data in the intent and close the activity using the `finish()` method. This will close and destroy the activity

**SecondActivity.java**

```java
public void closeSecondActivity(View view) {
    Intent intent = new Intent();
    intent.putExtra("sendThisDataToMainActivity", "benjamin");
    setResult(RESULT_OK, intent);
    finish();
}
```



In the `MainActivity` the `onActivityResult` method is called when we get back to the `MainActivity`. Here we can get the data sent in the intent using `data.getStringExtra("dataSecondActivity")`

**MainActivity.java**

```java
@Override
public void onActivityResult(int requestCode,
                             int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);
  	if(requestCode == 123) {
      System.out.println(data.getStringExtra("dataSecondActivity"));
    } 
}
```



## 5. Getting Data from User

Use input elements like `EditText` to get data from the user.



```xml
<EditText
    android:id="@+id/editText"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Enter text"/>
```



### Retrieving User Input

```java
EditText editText = findViewById(R.id.editText);
String input = editText.getText().toString();
```



## Lifecycle

![Android Activity Lifecycle - javatpoint](assets/Android-Activity-Lifecycle.png)



```java
@Override
protected void onResume() {
    super.onResume();
}
```



## Exercises



### ChatGPT level assesor

I want for you to assess my Javascript programming level from 1 to 10  is. Where 1 is beginer and 10 is expert  

You should give me exercises one at a time. The exercise need to be  solved with code. The exercises should match the level you think i am  at. Never help with solving the exercise or writing pseudocode for it.

You will provide the exercise and i will give you code. For each  exercise i complete provide the following:  

1. Feedback for the exercise 
2. The level you think i am at



When you are confident of my level generate a report. The report should  contain the following  

1. The level you think i am at  
2. Feedback on the code i wrote
3. Where i should focus to improve



Lets start with the first question



### 📝 Todo list

Make a simple to-do list app that allows users to add, delete, and mark tasks as completed



Examples

- [https://todomvc.com/examples/vue/](https://todomvc.com/examples/vue/)
- [https://todolist-771945458.development.catalystserverless.com/app/](https://todolist-771945458.development.catalystserverless.com/app/)



<!--

## Fetchin data from api

[https://github.com/joneikholmkea/ListPrep/blob/main/app/src/main/java/com/joneikholm/listprep/CustomAdapterActivity.java](https://github.com/joneikholmkea/ListPrep/blob/main/app/src/main/java/com/joneikholm/listprep/CustomAdapterActivity.java)



```java
private void getArticles(MyAdapter myAdapter) {
        fetchData = new FetchData();
        String result = "";
        try {
            result = fetchData.execute().get(); // will perform the internet query
            JSONObject jsonObject = myJSONParser.parse(result);
            JSONArray articles = (JSONArray) jsonObject.get("results");
            int count = 0;
            for(Object article : articles){
                JSONObject jsonArticle = (JSONObject)article;
                dataArr[count] = (String)jsonArticle.get("title");
               // contentArr[count] = (String)jsonArticle.get("content");
                linkArr[count] = (String)jsonArticle.get("link");
                count++;
            }
            myAdapter.notifyDataSetChanged(); // tells the adapter to refresh
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
```



[https://github.com/joneikholmkea/ListPrep/blob/main/app/src/main/java/com/joneikholm/listprep/service/FetchData.java](https://github.com/joneikholmkea/ListPrep/blob/main/app/src/main/java/com/joneikholm/listprep/service/FetchData.java)



```java
package com.joneikholm.listprep.service;

import android.os.AsyncTask;

import java.io.InputStream;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class FetchData extends AsyncTask<String,Void,String> {

    private String url = "https://newsdata.io/api/1/news?apikey=pub_19053672a88b2a19505c6b4b536a1a0bc3332&country=dk";
//    private String url = "https://newsapi.org/v2/top-headlines?country=us&apiKey=a3e688609c5940a98dc8df7713251264";
    private String result = "";
    HttpURLConnection urlConnection;
    @Override
    protected String doInBackground(String... strings) {
        System.out.println("calling doInBackground");
        try {
            URL url = new URL(this.url);
            urlConnection = (HttpURLConnection) url.openConnection();
            urlConnection.connect();
            System.out.println("L24 " + urlConnection.getResponseMessage());
            System.out.println("L24 " + urlConnection.getResponseCode());
            InputStream in = urlConnection.getInputStream();
            InputStreamReader reader = new InputStreamReader(in);
            int data = reader.read();
            while(data != -1){
                char c = (char)data;
                result += c;
                data = reader.read();
            }
            return result;
        } catch (Exception e) {
            e.printStackTrace();
            return "Failed " + e.getMessage();
        } finally {
            urlConnection.disconnect();
        }

    }
}
```



-->
