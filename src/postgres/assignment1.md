
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
    SELECT relname, relkind, reltuples, relpages, relchecks
    FROM pg_class
    WHERE relkind = 'r'   -- 'r' means ordinary table
    AND relname NOT LIKE 'pg_%'
    AND relname NOT LIKE 'sql_%';

    here
    relname -> table name,
    relkind → object type (e.g., r for table, i for index, v for view)
    reltuples → estimated number of rows
    relpages → estimated number of disk pages
    relhaspkey → whether a primary key exists
    relchecks → number of check constraints
    ```

5. (1 pt) Write a query that finds the country name of the Fight Club event.

    ```
    SELECT c.country_name
    FROM events e
    JOIN venues v ON e.venue_id = v.venue_id
    JOIN countries c ON v.country_code = c.country_code
    WHERE e.title = 'Fight Club';
    ```

3. (1 pt) Add a city in the U.S. for Springfield with a zip of 01119. Show the query below:

    ```
    INSERT INTO cities (name, postal_code, country_code)
    VALUES ('Springfield', '01119', (SELECT country_code FROM countries WHERE country_name = 'United States'));

    ```

4. (1 pt) Add a private venue in the U.S. for Rivers Hall with address 1215 Wilbraham Rd, Springfield, MA , zipcode 01119.

    ```
    INSERT INTO venues (venue_id, name, street_address, postal_code, country_code,  type)
    VALUES (
        3,
        'Rivers Hall',
        '1215 Wilbraham Rd, Springfield, MA',
        '01119',
        (SELECT country_code FROM cities WHERE name = 'Springfield' AND postal_code = '01119'),
        'private'
    );
    ```

5. (1 pt) Add an event called ‘New Student Welcome’ that starts at 3:30 PM on August 22nd and ends at 5:00 PM on August 22nd that is held in Rivers Hall.

    ```
    INSERT INTO events (event_id, title, starts, ends, venue_id)
    VALUES (4,
        'New Student Welcome',
        '2025-08-22 15:30:00',
        '2025-08-22 17:00:00',
        (SELECT venue_id FROM venues WHERE name = 'Rivers Hall')
    );

    ```

6. (1 pt) Alter the events table with a boolean value called “adult” that is true if the event is for adults only and false otherwise.

    ```
    ALTER TABLE events
    ADD COLUMN adult BOOLEAN DEFAULT FALSE;

    ```

7. (1 pt) Add an event titled “cooking class” that is adult only to be held in the Crystal Ballroom. List the query here:

    ```
    INSERT INTO events (event_id, title, starts, ends, venue_id, adult)
    VALUES (
    5,
    'cooking class',
    NOW(),         -- placeholder start
    NOW() + INTERVAL '2 hours',  -- placeholder end
    (SELECT venue_id FROM venues WHERE name = 'Crystal Ballroom'),
    TRUE
    );

    ```

8. (1 pt) Write a query that shows the cities, event title and venue name for all events with a venue:

    ```
    SELECT ci.name as city_name, e.title AS event_title, v.name as venue_name
    FROM events e
    JOIN venues v ON e.venue_id = v.venue_id
    JOIN cities ci ON v.postal_code = ci.postal_code;

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
