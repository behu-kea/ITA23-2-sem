# Fetch data from api



[https://medium.com/@daydreamer_/how-to-fix-android-emulator-wi-fi-connected-with-no-internet-c62fd4ed652d](https://medium.com/@daydreamer_/how-to-fix-android-emulator-wi-fi-connected-with-no-internet-c62fd4ed652d)



In this tutorial, we'll learn how to fetch data from an API using an Android phone with Java. We'll use a simple example that retrieves a JSON string containing movie information.



## Prerequisites

Before we start, make sure you have:

1. Your emulator is connected to the internet. Make sure that the wifi signal is okay. See image below

![CleanShot-2023-03-16-at-14.27.11](assets/CleanShot-2023-03-16-at-14.27.11.png)

If it is not, then fix it using [this guide](https://medium.com/@daydreamer_/how-to-fix-android-emulator-wi-fi-connected-with-no-internet-c62fd4ed652d)



2. In your `AndroidManifest.xml` file, add the following line inside the `<manifest>` element to grant internet access to your app:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```



## Fetching data

You should be now know how to create an async task. We will create an async task that fetches the data from an api



```java
package com.example.fetch_data_from_api;

import android.net.Uri;
import android.os.AsyncTask;
import android.util.Log;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class ApiFetcher extends AsyncTask<Void, Void, String> {

    @Override
    protected String doInBackground(Void... voids) {
        System.out.println("Here!!!");
        return getAstronautsInSpaceJsonString("https://gist.githubusercontent.com/pankaj28843/08f397fcea7c760a99206bcb0ae8d0a4/raw/02d8bc9ec9a73e463b13c44df77a87255def5ab9/movies.json");
    }

    protected void onPostExecute(String astronautsInSpaceJSONString) {
        System.out.println(astronautsInSpaceJSONString);
    }

    static String getAstronautsInSpaceJsonString(String apiUrl) {

        // Set up variables for the try block that need to be closed in the
        // finally block.
        HttpURLConnection urlConnection = null;
        BufferedReader reader = null;
        String bookJSONString = null;

        try {
            // Build the full query URI, limiting results to 10 items and
            // printed books.
            Uri builtURI = Uri.parse(apiUrl).buildUpon()
                    .build();

            // Convert the URI to a URL.
            URL requestURL = new URL(builtURI.toString());

            // Open the network connection.
            urlConnection = (HttpURLConnection) requestURL.openConnection();
            urlConnection.setRequestMethod("GET");
            urlConnection.connect();

            // Get the InputStream.
            InputStream inputStream = urlConnection.getInputStream();

            // Create a buffered reader from that input stream.
            reader = new BufferedReader(new InputStreamReader(inputStream));

            // Use a StringBuilder to hold the incoming response.
            StringBuilder builder = new StringBuilder();

            String line;
            while ((line = reader.readLine()) != null) {
                // Add the current line to the string.
                builder.append(line);

                // Since this is JSON, adding a newline isn't necessary (it won't
                // affect parsing) but it does make debugging a *lot* easier
                // if you print out the completed buffer for debugging.
                builder.append("\n");
            }

            if (builder.length() == 0) {
                // Stream was empty.  Exit without parsing.
                return null;
            }

            bookJSONString = builder.toString();

        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            // Close the connection and the buffered reader.
            if (urlConnection != null) {
                urlConnection.disconnect();
            }
            if (reader != null) {
                try {
                    reader.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

        return bookJSONString;
    }
}
```

We are using the `HttpURLConnection` class to send the request. The connection to the server is literally opened, then the data put into a string and then the connection is closed afterwards. Its a bit more code than js!! And we still just have the json string!