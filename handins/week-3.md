# ADT's & Repetition

**A)**

Write a method that returns a random number between 1-10.

Call the method 10 times by using a loop



**B)**

Write a method that returns if a user has input a valid CPR number.

A valid CPR number has:

- 10 Digits.
- The first 2 digits are not above 31.
- The middle 2 digits are not above 12.

The method returns true if the CPR number is valid, false if it is not.



**C)**

Write a class: *Article*

- An article has an author and a title

Create 5 articles, add them into an ArrayList and print them by overriding the *.toString()* method



**D)**

Write a class: *Square*

- A square has a width and a height.
- Implement the comparable interface such that two squares can be compared by their perimeter.
- Sort a list of squares using collections.sort();



**E)**

Write a class: *RedditPost*

- A Redditpost has :
  - A date of which is has been posted
  - An author
  - A balance of upvotes / downvotes
  - A Title

When a new instance of RedditPost is instantiated:

- The current date will be generated.
- The balance of upvotes and downvotes starts at 1.
- The title and author has to be provided by the constructor.



Ensure all attributes are private, but accesible by getters & setters.



**F)**

Write a class: *RedditFrontPage*

The RedditFrontPage has:

- An ArrayList of all RedditPosts
- A method in RedditFrontPage deletes a RedditPost from the list, by its index number
