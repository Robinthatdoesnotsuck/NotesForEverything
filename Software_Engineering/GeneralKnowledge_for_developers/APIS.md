# APIs mumbo jumbo

+ The common protocol to use is REST
  + Which means Representational State Transfer
  + And a RESTful API must follow three conventions
    + Base URI
    + It has an internet media type for data representation, the most common one is JSON
    + And it has the standard HTTP methods that everyone knows
      + GET
      + POST
      + PUT
      + DELETE

+ Defining a root URI
  + There are different patterns to the naming conventions you can use to the URI that your API will have
    + api.example.com/
      + this pattern helps the interface to isolate since it just the api domain with its resources it is simplier when scaling
    + example.com/api/
      + this decouples it from a subdomain since this will be like how you actually program it under the namespace
    + example.com/api/v1
      + This just adds the versioning and it is good UX wise but it might be a hassle to update since you need to add the version to the route everytime you update

+ Versioning the api
  + depending on the technology you are using, it might differ
  + butt )) it is commonly by making just a directory under your api with its version
