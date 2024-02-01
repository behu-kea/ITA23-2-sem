# Firebase Cloud Firestore



## Create your Firestore in Firebase

go to [https://console.firebase.google.com/?pli=1](https://console.firebase.google.com/?pli=1) -> add project, give it a name -> Add analytics if necessary -> click create



Go into your Firestore and under `Get started by adding Firebase to your app` click on Android. Follow the guide. 



Now create a Database in your Firestore. Go to your firebase project -> click Cloud Firestore -> click Create database. Select `Start in test mode`

**🚨OBS!!!!!🚨**: The default security rules for test mode allow anyone with your database reference to view, edit and delete all data in your database for the  next 30 days **🚨OBS!!!!!🚨**

Now in your `build.gradle.kts` add the following line

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
