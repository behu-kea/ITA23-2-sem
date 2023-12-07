# AsyncTask

Google Training: [Google](https://developer.android.com/codelabs/android-training-create-asynctask?index=..%2F..%2Fandroid-training#0)

### Exercise 1

- Create an application from an Empty Activity with a simple "Hello World" TextView
- Create a class that extends AsyncTask, and changes the "Hello World" to "Text Changed Asynchronous" after 4 seconds
  - Use Thread.sleep(4000) to make the application wait 4 seconds inside the doInBackground() method.

### Exercise 2

- Fork & Download the following boilerplate code: [Github](https://github.com/nicklasdean/dadjokes-async)
- Notice the following: 
  - DadJokeService is a class that calls an API. It receives back JSON data, and returns a String to the onPostExecute( ) method
  - The services uses the HttpURLConnection to make a request: https://www.baeldung.com/java-http-request
- Expand the application such that:
  - A dad joke is displayed instead of the "Hello World" on the application MainActivity when the application is run

### Exercise 3 (Advanced)

- Refactor the code such that:
  - The dad joke JSON response is split into the following parts:
    - Id
    - Joke
  - Write a java class called: *DadJoke* and save data from the HTTP response inside the object. Only save relevant data.
    - Use the split method (and other string manipulation to clean up the response) https://www.baeldung.com/java-split-string 
  - Instead of displaying the full JSON response, display it in a user-friendly way with a textview for the ID and a textview for the Joke itself.
