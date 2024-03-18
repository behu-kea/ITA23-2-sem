# Sensors



Idag skal i selv researche et emne. Det er for at gøre jeg klar til at blive rigtige webudviklere. Det kan godt være lidt angstprovokerende, men husk at jeg er her til at hjælpe jer i processen! 



## Class overview

08:30 - 10:00 - Investigate your topic

10:00 - 10:15 - Break

10:15 - 10:45 - Presentations

10:45 - 11:30 - Exercises

11:30 - 11:45 - Recap



Random groups. Need minimum two groups per topic



### Investigate your topic

The first 1.5 hours you have to investigate one of the technologies below. Here are some of the things you have to consider:

1. How does the technology work in a non technical way? What is it doing? Why is it smart? When should i use it?
2. How do i implement the technology in Android Studio using java? Create a small prototype and push the code to GitHub
3. Make a 10 minute presentation focusing on your topic
4. Create a fun exercise that a group can spend about 45 minutes on
   1. Remember to make the first steps of the exercise super easy!



Here are the topics:

1. Accelerometer
2. Position (latitude and longitude)
3. Camera





<!--

For code examples go to: [https://github.com/behu-kea/sensors-android-java](https://github.com/behu-kea/sensors-android-java)

## How sensors work:

In `onCreate` you create a new SensorManager:

```java
sensorManager = (SensorManager) getSystemService(SENSOR_SERVICE);
```



I `onResume` lave en accelerometer vha. SensorManager: 

```java
Sensor accelerometer = sensorManager.getDefaultSensor(Sensor.TYPE_ACCELEROMETER);
```



Tjek om der er en accellerometer og derefter registrer listeneren:

```java
if (accelerometer != null) {
            sensorManager.registerListener(this, accelerometer,
                    SensorManager.SENSOR_DELAY_NORMAL, SensorManager.SENSOR_DELAY_UI);
        }
```



Implementer `SensorEventListener` interfacet og nu får du data fra sensor ved at implementere onSensorChanged metoden



```java
@Override
public void onSensorChanged(SensorEvent event) {
    if (event.sensor.getType() == Sensor.TYPE_ACCELEROMETER) {
        float[] values = event.values;
      	sout(values);
        //textView1.setText("x: "+values[0]+"\ny: "+values[1]+"\nz: "+values[2]);
    } 
}
```



## How location works

First in the `AndroidManifest.xml` file make sure that permissions are asked for:

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.INTERNET" />
```

Now it works quite like the other sensor:

Create a `LocationManager` like this

```java
locationManager = (LocationManager) getSystemService(Context.LOCATION_SERVICE);
```



Now start location updates using this code 

```java
locationManager.requestLocationUpdates(LocationManager.GPS_PROVIDER, 0L, (float) 0, (LocationListener) this);
```



Implement the `LocationListener` interface. Now in the `onLocationChanged` method get the latitude and longitude

```java
@Override
public void onLocationChanged(Location location) {
    textView1 = (TextView) findViewById(R.id.textView1);
    textView1.setText("Latitude:" + location.getLatitude() + ", Longitude:" + location.getLongitude());
}
```



## How camera works

First create a button and an `ImageView` in the `activity_main.xml`

In `onCreate` get the `ImageView`.



When button to take image with is clicked create a new `cameraIntent` and start the activity

```java
Intent cameraIntent = new Intent(android.provider.MediaStore.ACTION_IMAGE_CAPTURE);
startActivityForResult(cameraIntent, CAMERA_REQUEST);
```

Now when the camera comes back with an image taken the `onActivityResult` gets called. We can now get the data from the image and put into the `ImageView`



```java
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);
    if (requestCode == CAMERA_REQUEST) {
        Bitmap photo = (Bitmap) data.getExtras().get("data");
        imageView.setImageBitmap(photo);
    }
}
```

`CAMERA_REQUEST` is just a number that identifies that intent. It could have been literally any number. 



## Ressources



### Sensors

- https://www.youtube.com/watch?v=reDLrzGyAfk&list=PL_CeQH2n4d4FJnPGpcNL8Byk96TGyoNDj
- https://developer.android.com/guide/topics/sensors/sensors_position
- https://developer.android.com/guide/topics/sensors/sensors_motion
- https://developer.android.com/guide/topics/sensors



### Location

Husk at give lokationsadgang til appen!

- https://javapapers.com/android/get-current-location-in-android/



### Camera

- 



-->









