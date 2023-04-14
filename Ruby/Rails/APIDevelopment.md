# Using Rails to create a RESTFul api

+ We'll just create a folder called api under the controllerss directory 
+ Then we modify the routes.rb on config in our rails application as we add resources or routes to our api

+ We have to create a namespace under the routes.rb file, this tells rails to map the namespace to the directory that matches the name of the previously created one under controllers

## USEFUL SIDE NOTES

+ To check what media types can be handled natively by RAILS you can use the rails console and use this command
    ```
    Mime::SET.collect(&:to_s)
    ```
+ To add a default format you can add after the namespace the defaults option
    + ```defaults: { format: :json }```
    + you add it in form of a label
+ Also to add versioning to our api we just need to create another directory inside the api one called v1
+ And add a namespace inside the main namespace pointing to this new directory
