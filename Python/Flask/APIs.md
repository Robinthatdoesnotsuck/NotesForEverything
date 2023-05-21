# APIS For flask
+ Is an architectural style of building APIS
    + Code that allows us to take a request
      + It process the request and returns a response
        + Like a web service
    + It exists multiple ways to build apis
      + Everything is process in the server side of things and the apis are just petitions from the client to the server
      + It's a microservice architecture


+ Resource method chart
  + GET
    + GET a resource that the server offers
  + POST
    + Send something to the server POSTING something from the client and expect a response from the server
  + PUT
    + Is used to updated something we POSTED we use POST to create something new in the server
      + Like updating information from a user
  + DELETE
    + Self explained
  + Resources that you're offering


|   METHOD     |      PATH |   USED FOR |   PARAM    |  ON ERROR  |
|--------------|-----------|------------|------------|------------|
| GET          |      /sum | DESCRIPTION| OPTIONAL parameters | what to send on 404 |
| POST |  |  |  |  |
| PUT |  |  |  |  |
| DELETE |  |  |  |  |


+ We use a tool that is installed with pip that is 
  + flask_restful