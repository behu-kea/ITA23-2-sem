# Interactive UI & components



## Plan in class

Recreate the layout for one of the [following designs](https://www.google.com/search?q=modern+app+layout&client=firefox-b-d&source=lnms&tbm=isch&sa=X&ved=2ahUKEwi1gdWmurX9AhV8RvEDHbX_DnEQ_AUoAXoECAEQAw&biw=1792&bih=902&dpr=2#imgrc=mFAxR1cYg_t89M)

Flexbox android layout: [https://github.com/google/flexbox-layout](https://github.com/google/flexbox-layout)



## Exercise



### Layout

Recreate the following layouts

![Recreate the following layouts](assets/CleanShot-2023-02-27-at-11.04.42.png)



### Confetti app 🎉

Let's create an app that shows confetti when clicking on a button



#### Install the confetti module

In the `build.gradle` file, add `implementation 'nl.dionsegijn:konfetti-xml:2.0.2'` to the `dependencies {}` part

Now press `Sync Now` in the top to download and install the library

> This is like `npm install` for Java! The `build.gradle` is like the `package.json` file!



#### Add a confetti view to our `activity_main.xml`

Add this code to the `activity_main.xml` view. This will add a `KonfettiView` where konfetti will be drawn

```xml
<nl.dionsegijn.konfetti.xml.KonfettiView
    android:id="@+id/konfettiView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintLeft_toLeftOf="parent"
    app:layout_constraintRight_toRightOf="parent"
    app:layout_constraintTop_toTopOf="parent" />
```



#### Create the boilerplate code

In the `MainActivity.java` add this code:

```java
public class MainActivity extends AppCompatActivity {
    private KonfettiView konfettiView = null;
    private Shape.DrawableShape drawableShape = null;
    private Party party = null;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        konfettiView = findViewById(R.id.konfettiView);

        EmitterConfig emitterConfig = new Emitter(200, TimeUnit.MILLISECONDS).perSecond(50);
        party = new PartyFactory(emitterConfig)
                .spread(360)
                .colors(Arrays.asList(0xfce18a, 0xff726d, 0xf4306d, 0xb48def))
                .setSpeedBetween(0f, 30f)
                .position(new Position.Relative(0.5, 0.3))
                .build();
    }
}
```



#### 🎉🎉🎉🎉🎉🎉

To actually start the confetti use this code

```java
konfettiView.start(party);
```



#### 📝 One button

Create a button that when clicked will start showing confetti



#### 📝 Two buttons

Create two buttons. When one button is clicked is should show short burts of confetti. For the other button is should show a long burst of confetti



#### 📝 Confetti where clicked

Make is possible so that where the user clicks there will be confetti. Maybe this mode could be activated with a slider.



#### 📝 Keep holding the button

Create a button that will spew confettit as long as the button is pressed!



#### Create a fart button 💨

When clicking a button a fart sound should be played
