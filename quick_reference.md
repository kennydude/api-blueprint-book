# Quick Reference

This is a quick reference for API blueprint. It's not as technical as [the spec](https://github.com/apiaryio/api-blueprint/blob/master/API%20Blueprint%20Specification.md) but it should allow you to be able to produce an in-depth API Blueprint.

Comments have been added using `<!-- html comment tags like this -->`.

You can also view this on Apiary [here](http://docs.dogdatabase.apiary.io/#).

```markdown
FORMAT: 1A
HOST: https://api.example.com

# Dog Database

Dog Database is designed to be an example of how API blueprint works
You should be able to use this to get an idea on how most of the concepts work
inside of API Blueprint.

## Authentication

It's just Markdown, so feel free to add free-flowing text to describe
your API where Blueprint can't. So feel free to add your own
headings such as Authentication etc.

## Group Status

<!-- Groups allow us to group together endpoints. You do this
     with a heading which starts with Group
-->

## GET /api/status/

This endpoint returns any issues with the service
at the moment

<!-- dredd can actually understand this block when you're
     testing APIs. It checks for the types are rougly
     the same. It's best to use the other ways of
     describing JSON responses
-->

+ Response 200 (application/json)

        {
            "status": "ok",
            "results": [
                {
                    "message": "Minor issues to notifications",
                    "severity": "minor",
                    "id": 2
                }
            ]
        }

## Individual Status [GET /api/status/{id}/]

<!-- URL Parameters are defined here
     For POST parameters, please see further down
-->

+ Parameters

    - id: `2` (integer, required) - ID number of the status message

+ Response 200 (application/json)

        {
            "message": "Minor issues to notifications",
            "severity": "minor",
            "id": 2
        }

# Group Dogs

Endpoints for dealing with our catalogue of dogs.

## Breeds [/breeds/]

### GET

Get all breeds in our database

<!-- For the documentation on Dog Breed type, jump down
     to the bottom of the document for "Data Structures".
     
     This format is called MSON (Markdown Syntax for Object Notation) 
     https://github.com/apiaryio/mson
-->

+ Response 200 (application/json)

    + Attributes
    
        + previous: `http://.../` (string, required, nullable) - The previous set of results
        + next: `http://.../` (string, required, nullable) - The next set of results
        + count: `992` (number, required) - Total number of records
        + results (array[Dog Breed]) - Results

### POST

Add a new breed to the database

+ Request Valid new breed (application/json)

    + Attributes (Dog Breed)

+ Response 201 (application/json)

    + Attributes (Dog Breed)

+ Request Not valid request (application/json)

    + Attributes
        + name: `Springer` (string)
        + country: `England` (string)
        + long_haired: `sometimes` (string)

+ Response 401 (application/json)

    + Attributes
    
        + message: `long_haired not valid` (string, required) - Message in English of error
        + code: `20292` (number, required) - Error code

# Data Structures

## Dog Breed (object)

+ name: `English Springer Spaniel` (string, required) - The name of the breed
+ long_haired: `true` (boolean, required) - Is the dog long haired?
+ country: `England` (string, required) - Country of Origin of the breed
+ id: `1` (number) - ID in the database for this breed
```