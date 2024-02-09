# Firebase Cloud Firestore



## Create your Firestore in Firebase

go to [https://console.firebase.google.com/?pli=1](https://console.firebase.google.com/?pli=1) -> add project, give it a name -> Add analytics if necessary -> click create



Go into your Firestore and under `Get started by adding Firebase to your app` click on Android. Follow the guide. 



Now create a Database in your Firestore. Go to your firebase project -> click Cloud Firestore -> click Create database. Select `Start in test mode`

**🚨OBS!!!!!🚨**: The default security rules for test mode allow anyone with your database reference to view, edit and delete all data in your database for the  next 30 days **🚨OBS!!!!!🚨**

Now in your `build.gradle.kts` (Module App) add the following line

```
implementation("com.google.firebase:firebase-firestore")
```



## Secure your data

```json
// Allow read/write access on all documents to any user signed in to the application
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```



## Create a Collection in Cloud Firestore

Go to your Cloud Firestore database

![Cloud Firestore](assets/CleanShot-2024-02-02-at-12.11.58.png)

Click `Start collection` -> Give it a name -> Now create a document:

Give it an Auto-id and create the relevant fields and values for your first document





## Setting up Firestore

First we need to import the right libraries in the file you will be using

```kotlin
import com.google.firebase.Firebase
import com.google.firebase.firestore.firestore
```



Then you need to create a new instance of a Firestore database

```kotlin
val db = Firebase.firestore
```



## Saving data

We are now ready to use kotlin to save data in our database



### Creating a data class

To hold data we will be using a specific kind of class called a data class. A `data class` is a special class type primarily intended to hold data. The most important feature for us is the serialisation method. Serialization refers to the process of converting an object into a  format that can be stored or transmitted (like JSON, binary, etc.)

Let's create a `Car` data class that matches the fields in the Firestore database:

```kotlin
data class Car(
    val color: String = "", // Make properties public
    val numberOfWheels: Int = 0 // Provide default values
) {}
```



### Saving an object into Firestore

We now have all we need. Create a new object and add it to the database using the following code and the `.add` function

```kotlin
// Create a new user with a first and last name
val greenCar = Car("green", 5);

// Add a new document with a generated ID
db.collection("cars")
    .add(greenCar)
    .addOnSuccessListener { documentReference ->
        Log.d(TAG, "DocumentSnapshot added with ID: ${documentReference}")
    }
    .addOnFailureListener { e ->
        Log.w(TAG, "Error adding document", e)
    }
```



## Getting data from Firestore

To get data from Firestore we use the `.get` function

```kotlin
db.collection("cars")
  .get()
  .addOnSuccessListener { result ->
      for (document in result) {
          val car = document.toObject(Car::class.java)
          Log.d(TAG, "${document.id} => ${car}")
          Log.d(TAG, "${document.id} => ${car.color}")
      }
  }
  .addOnFailureListener { exception ->
      Log.w(TAG, "Error getting documents.", exception)
  }
```

Here we get the `result` from the database and then convert the result into an object we can work with in Kotlin using the `toObject` method: 

```kotlin
val car = document.toObject(Car::class.java);
Log.d(TAG, car.color)
```



 ### Query specific data

You can query specific data like this:

```kotlin
db.collection("cities")
  .whereEqualTo("capital", true)
  .get()
  .addOnSuccessListener { documents ->
      for (document in documents) {
          Log.d(TAG, "${document.id} => ${document.data}")
      }
  }
  .addOnFailureListener { exception ->
      Log.w(TAG, "Error getting documents: ", exception)
  }
```



It is also possible to delete and edit



## Exercise











