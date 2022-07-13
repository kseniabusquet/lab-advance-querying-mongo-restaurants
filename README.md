![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# MongoDB | Compass CRUD Restaurants

## Introduction

We are back with our queries! :wink:

We have learned some super useful query operators that will helps us to make much better queries to retrieve the data we need. For this lab, we will be using the **MongoDB Restaurants Sample** database. Please keep reading and work on the following iterations.

## Requirements

- Fork this repo
- Clone this repo

## Submission

- Upon completion, run the following commands

```
$ git add .
$ git commit -m "done"
$ git push origin master
```

- Create Pull Request so your TAs can check up your work.

## Deliverables

Since we will be querying our database from Mongo Compass, you will need to copy/paste the `filter`, `projection`, `sort`, `skip` and `limit` you entered on Mongo Compass. In the `queries.md` file, you will find the instructions about the queries you need to do, and a field to fill the answers.

### Example

1. This is an example

- **`filter`**: /_You should copy/paste the filter in here_/
- **`projection`**: /_You should copy/paste the projection in here_/
- **`sort`**: /_You should copy/paste the sort in here_/
- **`skip`**: /_You should copy/paste the skip in here_/
- **`limit`**: /_You should copy/paste the limit in here_/

## Instructions

### Iteration 1

First, we need to import the database we will be using for the `lab`. We will use a MongoDB sample database that contains 
data about restaurants in New York. The dataset contains restaurants' name, address, cuisine type, and grades among other properties.

The database contains more than 25k documents. Each document holds the data about each of the restaurants. A document looks like the following:

```json
{
  "address": {
    "building": "1007",
    "coord": [
      -73.856077,
      40.848447
    ],
    "street": "Morris Park Ave",
    "zipcode": "10462"
  },
  "borough": "Bronx",
  "cuisine": "Bakery",
  "grades": [
    {
      "date": {
        "$date": 1393804800000
      },
      "grade": "A",
      "score": 2
    },
    {
      "date": {
        "$date": 1378857600000
      },
      "grade": "A",
      "score": 6
    },
    {
      "date": {
        "$date": 1358985600000
      },
      "grade": "A",
      "score": 10
    },
    {
      "date": {
        "$date": 1322006400000
      },
      "grade": "A",
      "score": 9
    },
    {
      "date": {
        "$date": 1299715200000
      },
      "grade": "B",
      "score": 14
    }
  ],
  "name": "Morris Park Bake Shop",
  "restaurant_id": "30075445"
}
```

1. You will find the `.zip` file of the database on the **lab** folder.
2. Unzip the file
3. Navigate to this lab's folder in your terminal, and when inside, import the database to Mongo using the following command:

**When running the `mongoimport` you should be located in the same folder as the `data.json` file.**

```bash
$ mongoimport --db restaurantsDB --collection restaurants --drop --file data.json
```

What this mongoimport will do for us is to create a database named _restaurantsDB_, and inside the database will create a collection named _restaurants_ which will be fed with _data.json_.

_Side note_: In case errors or hanging with no response when running this command, add [--jsonArray](https://docs.mongodb.com/manual/reference/program/mongoimport/#cmdoption-mongoimport-jsonarray) at the end of the previous command.

4. Check on Mongo Compass if everything goes ok

### Iteration 2

You already know how this goes, so let's start working:

1. All the documents in the collection restaurants.
2. Display the fields restaurant_id, name, borough and cuisine, but exclude the field _id for all the documents in the collection restaurant.
3. Display the fields restaurant_id, name, borough and zip code, but exclude the field _id for all the documents in the collection restaurant.
4. All the restaurant which is in the borough Bronx.
5. The first 5 restaurant which is in the borough Bronx.
6. The next 5 restaurants after skipping first 5 which are in the borough Bronx.
7. The restaurants who achieved a score more than 90.
8. The restaurants that achieved a score, more than 80 but less than 100.
9. The restaurants which locate in latitude value less than -95.754168
10. The restaurants that do not prepare any cuisine of 'American' and their grade score more than 70 and latitude less than -65.754168.
11. The restaurants which do not prepare any cuisine of 'American' and achieved a score more than 70 and located in the longitude less than -65.754168.
12. The restaurants which do not prepare any cuisine of 'American ' and achieved a grade point 'A' not belongs to the borough Brooklyn. The document must be displayed according to the cuisine in descending order.
13. The restaurants which belong to the borough Bronx and prepared either American or Chinese dish.
14. Display the restaurant_id, name, borough and cuisine for those restaurants which belong to the borough Staten Island or Queens or Bronxor Brooklyn.
15. Display the restaurant_id, name, borough and cuisine for those restaurants which are not belonging to the borough Staten Island or Queens or Bronxor Brooklyn.
16. Display the restaurant_id, name, borough and cuisine for those restaurants which achieved a score which is not more than 10.
17. Display the restaurant_id, name, address and geographical location for those restaurants where 2nd element of coord array contains a value which is more than 42 and upto 52.
18. Display the documents sorting by the name of the restaurants in ascending order along with all the columns.
19. Display the documents sorting by the name of the restaurants in descending along with all the columns.
20. Display the documents sorting by the name of the cuisine in ascending order and for that same cuisine borough should be in descending order.
21. All documents in the restaurants collection where the coord field value is Double.

### Bonus queries

22. Display the restaurant name, borough, longitude and attitude and cuisine for those restaurants which contains 'mon' as three letters somewhere in its name.
23. Display the restaurant name, borough, longitude and latitude and cuisine for those restaurants which contain 'Mad' as first three letters of its name.
