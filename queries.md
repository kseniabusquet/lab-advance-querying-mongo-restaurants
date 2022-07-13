![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the documents in the collection restaurants.

const filter = {};

### 2. Display the fields restaurant_id, name, borough and cuisine, but exclude the field _id for all the documents in the collection restaurant.

const projection = {
  'restaurant_id': 1, 
  'name': 1, 
  'borough': 1, 
  'address.zipcode': 1, 
  '_id': 0
};

### 3. Display the fields restaurant_id, name, borough and zip code, but exclude the field _id for all the documents in the collection restaurant.

const projection = {
  'restaurant_id': 1, 
  'name': 1, 
  'borough': 1, 
  'zip': 1, 
  '_id': 0
};

### 4. All the restaurant which is in the borough Bronx.

const filter = {
  'borough': 'Bronx'
};

### 5. The first 5 restaurant which is in the borough Bronx.

const filter = {
  'borough': 'Bronx'
};

const limit = 5;

### 6. The next 5 restaurants after skipping first 5 which are in the borough Bronx.

const filter = {
  'borough': 'Bronx'
};

const skip = 5;

const limit = 5;

### 7. The restaurants who achieved a score more than 90.

const filter = {
  'grades.score': {
    '$gt': 90
  }
};

### 8. The restaurants that achieved a score, more than 80 but less than 100.

const filter = {
  'grades.score': [
    {
      $elemMatch: {
        '$gt': 80, 
        '$lt': 100
      }
    }
  ]
};

### 9. The restaurants which locate in latitude value less than -95.754168

const filter = {
  'address.coord.0': {
    '$lt': -95.754168
  }
};

### 10. The restaurants that do not prepare any cuisine of 'American' and their grade score more than 70 and latitude less than -65.754168.

const filter = {
  '$and': [
    {
      'cuisine': {
        '$ne': 'American'
      }
    }, {
      'grades.score': {
        '$gt': 70
      }
    }, {
      'address.coord.0': {
        '$lt': -65.754168
      }
    }
  ]
};

### 11. The restaurants which do not prepare any cuisine of 'American' and achieved a score more than 70 and located in the longitude less than -65.754168.

const filter = {
  '$and': [
    {
      'cuisine': {
        '$ne': 'American'
      }
    }, {
      'grades.score': {
        '$gt': 70
      }
    }, {
      'address.coord.0': {
        '$lt': -65.754168
      }
    }
  ]
};

### 12. The restaurants which do not prepare any cuisine of 'American ' and achieved a grade point 'A' not belongs to the borough Brooklyn. The document must be displayed according to the cuisine in descending order.

const filter = {
  '$and': [
    {
      'cuisine': {
        '$ne': 'American'
      }
    }, {
      'borough': {
        '$ne': 'Brooklyn'
      }
    }, {
      'grades.grade': 'A'
    }
  ]
};
const sort = {
  'cuisine': -1
};

### 13. The restaurants which belong to the borough Bronx and prepared either American or Chinese dish.

const filter = {
  '$and': [
    {
      'borough': 'Bronx'
    }, {
      '$or': [
        {
          'cuisine': 'American'
        }, {
          'cuisine': 'Chinese'
        }
      ]
    }
  ]
};

### 14. Display the restaurant_id, name, borough and cuisine for those restaurants which belong to the borough Staten Island or Queens or Bronx or Brooklyn.

const filter = {
  '$or': [
    {
      'borough': 'Staten Island'
    }, {
      'borough': 'Queens'
    }, {
      'borough': 'Bronx'
    }, {
      'borough': 'Brooklyn'
    }
  ]
};
const projection = {
  'restaurant_id': 1, 
  'name': 1, 
  'borough': 1, 
  'cuisine': 1
};

### 15. Display the restaurant_id, name, borough and cuisine for those restaurants which are not belonging to the borough Staten Island or Queens or Bronx or Brooklyn.

const filter = {
  '$nor': [
    {
      'borough': 'Staten Island'
    }, {
      'borough': 'Queens'
    }, {
      'borough': 'Bronx'
    }, {
      'borough': 'Brooklyn'
    }
  ]
};
const projection = {
  'restaurant_id': 1, 
  'name': 1, 
  'borough': 1, 
  'cuisine': 1
};

### 16. Display the restaurant_id, name, borough and cuisine for those restaurants which achieved a score which is not more than 10. (ask Felipe and Nilton)

const filter = {
  'grades.score': {
    '$lt': 10
  }
};
const projection = {
  'restaurant_id': 1, 
  'name': 1, 
  'borough': 1, 
  'cuisine': 1
};

### 17. Display the restaurant_id, name, address and geographical location for those restaurants where 2nd element of coord array contains a value which is more than 42 and up to 52. (Geographical location?)

const filter = {
  '$and': [
    {
      'address.coord.1': {
        '$lte': 52
      }
    }, {
      'address.coord.1': {
        '$gt': 42
      }
    }
  ]
};
const projection = {
  'restaurant_id': 1, 
  'name': 1, 
  'address': 1
};

### 18. Display the documents sorting by the name of the restaurants in ascending order along with all the columns.

const filter = {};
const sort = {
  'name': 1
};

### 19. Display the documents sorting by the name of the restaurants in descending along with all the columns.

const filter = {};
const sort = {
  'name': -1
};

### 20. Display the documents sorting by the name of the cuisine in ascending order and for that same cuisine borough should be in descending order.

const filter = {};
const sort = {
  'cuisine': 1, 
  'borough': -1
};

### 21. All documents in the restaurants collection where the coord field value is Double.

const filter = {
  '$and': [
    {
      'address.coord.0': {
        '$exists': true
      }
    }, {
      'address.coord.1': {
        '$exists': true
      }
    }
  ]
};

## Bonus queries

### 22. Display the restaurant name, borough, longitude and attitude and cuisine for those restaurants which contains 'mon' as three letters somewhere in its name.

const filter = {
  'name': {
    '$regex': 'mon'
  }
};
const projection = {
  'name': 1, 
  'borough': 1, 
  'address.coord': 1,  
  'cuisine': 1
};

### 23. Display the restaurant name, borough, longitude and latitude and cuisine for those restaurants which contain 'Mad' as first three letters of its name.

const filter = {
  'name': {
    '$regex': new RegExp('^Mad')
  }
};
const projection = {
  'name': 1, 
  'borough': 1, 
  'address.coord': 1, 
  'cuisine': 1
};
