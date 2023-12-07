# Getting up and running

### Firebase

https://firebase.google.com/docs/android/setup
https://firebase.google.com/docs/auth/android/start
https://firebase.google.com/docs/auth/android/manage-users

### Authentication

1. Create a project on firebase
2. Add firebase to local Android Project: https://firebase.google.com/docs/android/setup#console
3. Add Firebase Authentication to your app: https://firebase.google.com/docs/auth/android/start

4. Add Email/Password as sign-in providers end result:

![image-20230324115443305](assets/image-20230324115443305.png)

Approximately 10.000.000.000 can go wrong in this process. Help your neighbour. 

# Checklist

##### Build.gradle (Project: *your-project-name*) should look like this:

```json
buildscript {
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath 'com.google.gms:google-services:4.3.15'
    }
}

plugins {
    id 'com.android.application' version '7.3.0' apply false
    id 'com.android.library' version '7.3.0' apply false
}

allprojects {
    repositories {
        google()
        mavenCentral()
    }
}

```

##### Build.gradle (Module: *[your-project-name*]) should look *SOMEWHAT* like this:

```json
plugins {
    id 'com.android.application'
    id 'com.google.gms.google-services'
}

android {
    namespace 'com.example.firebase'
    compileSdk 33

    defaultConfig {
        applicationId "com.example.firebase"
        minSdk 33
        targetSdk 33
        versionCode 1
        versionName "1.0"

        testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}

dependencies {

    implementation 'androidx.appcompat:appcompat:1.6.1'
    implementation 'com.google.android.material:material:1.8.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.4'
    testImplementation 'junit:junit:4.13.2'
    androidTestImplementation 'androidx.test.ext:junit:1.1.5'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.5.1'

    implementation platform('com.google.firebase:firebase-bom:31.2.3')
    implementation 'com.google.firebase:firebase-analytics'
    implementation platform('com.google.firebase:firebase-bom:31.2.3')
    implementation 'com.google.firebase:firebase-auth'

}
```

##### settings.gradle

```javascript
pluginManagement {
    repositories {
        gradlePluginPortal()
        google()
        mavenCentral()
    }
}

rootProject.name = "firebase"
include ':app'
```

## Exercise 1: Make it work

- Create a  basic application-flow that has 4 activities:
  - Create or Login Activity - The user will choose if they want to login or create a new user by two buttons.
  - Create Activity: The user can input an e-mail and a password to create a user. If a user cannot be created, a Toast will appear and inform the user.
  - Login Activity: The user can input an e-mail and password to login. If they successfully login, they are directed to a "*Members Only*" Activity with the following message:
    - This is a members only club: Welcome [user e-mail address]



## Exercise 2: Make it better

- A valid e-mail has the following constraints:
  - Contains one and only one @
  - Contains at least one .
  - Are more than 3 characters long
- If the user e-mail does not live up to these constraints - it will not be allowed. Before sending the e-mail to firebase with *createUserWithEmailAndPassword( )* or *signInWithEmailAndPassword()* You should verify that the e-mail lives up to the abovementioned constraints.
  - Hint: Create an object with a method that will verify the e-mail. Then it can be reused. 

## (Advanced) Only authorized users gets dad jokes

- Expand your DadJoke application such that a user needs to be logged in to receive a Dad Joke
- When a user is signed in a Dad Joke is displayed