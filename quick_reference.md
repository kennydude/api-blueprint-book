# Quick Reference

This is a quick reference for API blueprint. It's not as technical as [the spec](https://github.com/apiaryio/api-blueprint/blob/master/API%20Blueprint%20Specification.md) but it should allow you to be able to produce an in-depth API Blueprint.

Comments have been added using `<!-- html comment tags like this -->`

```markdown
FORMAT: 1A
HOST: https://api.example.com

# My API

My API is designed to be an example of how API blueprint works
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

+ Response 200 (application/json)

<!-- dredd can actually understand this block when you're
     testing APIs. It checks for the types are rougly
     the same. It's best to use the other ways of
     describing JSON responses
-->

        {
            "status": "ok",
            "results": [
                {
                    "message": "Minor issues to notifications",
                    "severity": "minor"
                }
            ]
        }


```