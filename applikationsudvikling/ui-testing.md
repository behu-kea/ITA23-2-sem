# UI testing with espresso

Boilerplate project: https://github.com/nicklasdean/court-counter.git

#### Espresso setup:

**Dependencies**

Ensure that your build.gradle (Module:App) file has the following dependencies (or newer):

```groovy
testImplementation 'junit:junit:4.12'
androidTestImplementation 'com.android.support.test:runner:1.0.1'
androidTestImplementation 'com.android.support.test.espresso:espresso-core:3.0.1'
```

**Turn on Developer Mode:**

https://developer.android.com/studio/debug/dev-options

**Turn off animations**

In Settings > Systems > Developer Options

 Now look for the **Drawing** section. In this section, turn off the following options:

- Window animation scale
- Transition animation scale
- Animator duration scale

#### Exercises:

1. Use espresso to verify if the UI works in portrait mode as intended



2. Use espresso to verify if the UI has inconsistencies when changing orientation

```java
//This is how to change your orientation to landscape if your test has been generated with an ActivityScenarioRule
mActivityScenarioRule.getScenario().onActivity(activity -> {
    activity.setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_LANDSCAPE);
});
```

OR

```java
//This is how to change your orientation to landscape if your test has been generated with an ActivityTestRule
mActivityTestRule.getActivity().setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_LANDSCAPE);
```



3. (Advanced) Address & solve the issue - what is the problem?

- To extend the issue read the following article and understand the relevance to the observed bug:

https://medium.com/androiddevelopers/viewmodels-a-simple-example-ed5ac416317e

Note: ViewModelProviders.of is deprecated in some versions of Android SDK

To invoke a ViewModel in your activity use the following approach:

```java
//In this example, ScoreModel is the class that extends ViewModel
ScoreViewModel viewModel = new ViewModelProvider(this).get(ScoreModel.class);
```

4. (Advanced) Confirm that the issue has been solved for landscape orientation