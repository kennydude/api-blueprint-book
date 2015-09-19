# Getting Started

An API Blueprint is just Markdown. It just looks for sections of your Markdown file it recognises and turns this into a block of JSON which is easy to make into an API console, tests and more.

## Software

In this book we'll stick to the open source stuff, however feel free to use Apiary if you want to.

The main components which are really useful are:

* [Dredd](https://github.com/apiaryio/dredd) will test your API against your blueprint making sure it lines up.
* [Aglio](https://github.com/danielgtaylor/aglio) will produce a HTML file (all self-contained) of your API documentation which provides most of what you expect of API documentation.
* [drakov](https://github.com/Aconex/drakov) will provide a mock server which will respond to requests with the responses you provide.
 
There are many more which are documented on the [API Blueprint website](https://apiblueprint.org) and if you want to build something else, bindings are available to the parser (written in C).

## Your first API blueprint

We'll opt for a nice simple hello world which looks like the following:

    FORMAT: 1A
    HOST: https://api.example.com
    
    # GET /message
    + Response 200 (text/plain)
          
          Hello World!

* The first line is the version of API Blueprint. At the time of writing, `1A` was the latest so we are using that.
* The second line is optional and tells us where the API lives on the internet. Most of the time you'll want to include this as it allows you to have nice things like an API console against the live API.
* The fourth line is a Markdown heading, however it is recognised as a route. The contents of this block (until the next heading) are to do with when you send a `GET` request to `https://api.example.com/message` (which obviously isn't live).
* The fifth line indicates that it's talking about the response and the server will respond to the request with a status code of `200 OK` and the Content-Type is `text/plain`
* The seventh line is a Markdown code block, but it's recognised as the response you'll get from the server.
 
There's a lot more to API blueprint than this, however this is perfectly valid.