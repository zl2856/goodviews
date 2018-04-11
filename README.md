# GoodViews

A cinema database and discussion platform.

## Project 1 Part 3

**Description:** Goodviews is a platform for cinema/theater information and ticket reservation. While sites such as IMDB and RottenTomatoes exist to provide audiences with the latest film, TV and celebrity content and allow users to post reviews of media content, they lack a sense of social community. Furthermore, existing platforms often lack coherence due to the variety of media content. In Goodviews, we aim to marry the best aspects of Goodreads and IMDB and create a digital community of film fans. We offer a more ​streamlined ​database by focusing on movies rather than TV shows or other media. Users can curate ​collections ​of movies (such as "Movies I Want To Watch"), browse actors and post ​reviews ​of movies. They will be able to search a ​robust database ​ for films based on year/genre/rating, browse
plot synopsis, and post reviews on movies or theaters.

TODO:
A description of the parts of your original proposal in Part 1 that you implemented, the parts you did not (which hopefully is nothing or something very small), and possibly new features that were not included in the proposal and that you implemented anyway. If you did not implement some part of the proposal in Part 1, explain why.
Briefly describe two of the web pages that require (what you consider) the most interesting database operations in terms of what the pages are used for, how the page is related to the database operations (e.g., inputs on the page are used in such and such way to produce database operations that do such and such), and why you think they are interesting.

1. The PostgreSQL account where DB resides: ic2389
2. URL of web application: [http://35.185.29.235:8111](http://35.185.29.235:8111)
3. Features implemented:
    - User:
        - User may login/register for an account
        - Users REVIEW Reviewable (Movies, Theaters)
    - Movies:
        - Browse movie database on main page and easily view details on plot synopsis
        - View Talent that STARS_IN Movies
        - Movies ISA Reviewable, you can view reviews of movies
    - Talent:
        - View Talent that STARS_IN Movies
    - Theaters:
        - Theaters ISA Reviewable, you can view reviews of theaters
    - Collections:

TODO:
- Application must provide a way to view or interact with all the entities and relationships in your final ER diagram
- INSERT/UPDATE REVIEW
- ADD TO NEW/EXISTING COLLECTION
- CREATE THEATERS PAGE
- CREATE COLLECTIONS PAGE
- UPDATE navigation
- Browse theaters
    - Browse showings at theaters
- COLLECTIONS:
    - Allow users to create Collections
    - User can view their Collection
- Search for films based on year, genre or rating

INTERACT WITH:
- Reviewable Movies
- Reviewable Theaters
- TimeSlots
- Talent

Relationships:
- Theaters SHOW Movies at TimeSlots
- Users BOOK (SHOWINGS of Movies in Theaters during TimeSlots)
- Users CREATE Collections
- Collections CONTAIN Movies

Additional Assumptions:
- Users can BOOK multiple tickets, which may have different price points,
depending on the Showing (based on Movie, Theater, and TimeSlot).
- Users create Collections with unique names that can contain zero or more
movies.
- Showings can be booked up to the Theater capacity (`seat_info` attribute).
- TimeSlots can be before Movie release date (due to previews, etc.)


03-01-2018:

- Updated SQL after Kim's feedback
- Added `NOT NULL` and `CHECK` constraints
- Replaced all instances of `CHAR` iwth `VARCHAR`
- Converted unique identifiers (<id>) to `SERIAL` type, foreign keys still `INTEGER`



## Developer Walkthrough

### Set up Python 3 environment

```py
# Install python 3 dependencies and virtualenv

sudo apt-get install postgresql-9.3 postgresql-server-dev-9.3 git python3-dev python3-pip
sudo pip3 install virtualenv
sudo pip3 install virtualenvwrapper
virtualenv -p python3 env
source env/bin/activate

# Navigate to goodviews directory and install modules

cd goodviews
pip install -r requirements.txt
```

---

COMS4111 Database Systems

Team: Ivy Chen & Gregory Yap
