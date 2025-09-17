
# Assignment 1 - Postres

The deadline for this assignment is in Kodiak.

## Part 1

Work through the reading in Chapter 2 Day 1. Save your resulting database
in a file named `db.sql` in the same directory as this file.

## Part 2

Complete the following (part of which is from the Day 1 Homework from the text)

**Find From Day 1 Homework**

1. (1 pt)

    ```
    https://www.postgresql.org/docs/current/
    ```

2. (No answer required)

1. (1 pt)

    ```
    There are three types of MATCH that are simple, FULL, PARTIAL as defined by there names simple is when match is simply used without any extra parameters(as in the default form).

    Under FULL, a referencing row escapes the constraint only if all foreign key columns are NULL. Otherwise, mixing NULL and non-NULL causes a failure.

    Under PARTIAL, which is referenced but not implemented mixing NULL and non-NULL will not cause a failure.
    ```

**Do**

4. (2 pts) Select all the tables that you created from pg_class and examine the tables to identify the types of metadata Postgres stores about the tables. Explain below:

    ```
    Replace this with your answer
    ```

5. (1 pt) Write a query that finds the country name of the Fight Club event.

    ```
    Replace this with your answer
    ```

3. (1 pt) Add a city in the U.S. for Springfield with a zip of 01119. Show the query below:

    ```
    Replace this with your answer
    ```

4. (1 pt) Add a private venue in the U.S. for Rivers Hall with address 1215 Wilbraham Rd, Springfield, MA , zipcode 01119.

    ```
    Replace this with your answer
    ```

5. (1 pt) Add an event called ‘New Student Welcome’ that starts at 3:30 PM on August 22nd and ends at 5:00 PM on August 22nd that is held in Rivers Hall.

    ```
    Replace this with your answer
    ```

6. (1 pt) Alter the events table with a boolean value called “adult” that is true if the event is for adults only and false otherwise.

    ```
    Replace this with your answer
    ```

7. (1 pt) Add an event titled “cooking class” that is adult only to be held in the Crystal Ballroom. List the query here:

    ```
    Replace this with your answer
    ```

8. (1 pt) Write a query that shows the cities, event title and venue name for all events with a venue:

    ```
    Replace this with your answer
    ```

## Part 3

Read Chapter 2 Wrap-up and then

12. (2 pts) List the strengths of Postgres and relational databases.

    * (first strength)
    * (second strength)
    *

13. (2 pts) List of Postgres' weaknesses.

    *
    *
    *

## Submission

Use `save` and or `save-and-stop` to commit and push your work to your
personal repository for this class on GitLab.

Check that your work is properly submitted by browsing your repository
on ***GitHub***.
