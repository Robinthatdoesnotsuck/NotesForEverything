# Rails essentials for dommies

## The rails console brother

+ The rails is a great tool to manage well every rails app that we do or maintain
+ It can manage everything related to it, from creating and accessing the DB, the APIs and a whole lot of mumbmo jumbo
+ To access it we just need to do this in our root directory of our app
    + ```rails console```

+ Once we have it running we just need to use the commands that rails has

### Actions for DBs

+ The basic one will be for creating a new entry on one of our models
    ``` name_of_model.create! param: value, etc```

### Actions for testing    

+ To run tests with the default testing framework, that is  minitest we use
    ```rails test```
    + This will run every test we have under the test directory
        +  That means EVERYTHING
## Models

+ To create a new model for your whatever you are doing just need to use the command:
    ```
    rails generate model User email:string password_digest:string
    ```
+ Migrations
    + Migrations are just the fancy way to say that the DB that we are using and the thing we have in the app is gonna sync up
    + This is contained in the db/migrate directory once we do something with the models using rails.
    + This is manage by itself cause well to see if we don't fup something on the way
    + We can also modify this migrations before the sync up with the database so that we can make a simple model in the rails cli and then add complexity to it with ruby so that it is easier than been constraint by the console.
        + The modifications that we do are bounded by the Active record and well rails syntax so check that out to its equivalent on the db that you want to do something
    + To finish the migration or to build it just run
    ```
    rake db:migrate
    ```
    + If you did everything right you should just get a message in the console that well whatever table, db or anything you modified with the migration was succesful

+ Validation basics for models
    + Rails has a validation library already on its well libraries
    + So depending of what we want to do, we just need to open our models directory and choose a model to start validating it.
        + Check documentation for this pls [Rails active record validation](https://guides.rubyonrails.org/active_record_validations.html)
        + We just need to add the validation that we need depending of well what we want, is as complex and as easy as you want
    + The validation will apply to everything related to that model so even if you want to create lets say so an email and you validated it to only be valid if it has an @, it won't let you even if you use the rails cli

## Unit Testing with MiniTest

### For models
+ Minitest is the default framework for testing included in rails
+ It uses something called Fixtures, which helps us in filling with test data our database 
    + This fixtures are defined in YAML files in the tests/fixtures directory
    + There is always one file per template
    + This file is created as you create models
        + So you have to modify this template YAML for your model
        + Then you have to modify the thest that are on the well test/models directory for each model to validate these tests

+ Adding testeses
 + while we add test to whatever model we are using we just need to follow these conventions
    + If we are testing something to not be valid we have to use ```assert_not name_of_model.valid?```
    + On the contrary if we are validating that something must be true we use ```assert name_of_model.valid?```

## Basic Security

### Hashing your passwords
