# Introduction

*This is work in progress. Don't use.*

This is very fresh (Oct 27, 2015).

More info coming soon as I'm developing this for our internal use.

# Development

Install all dependencies:

```
$ npm i
```

You can also use a globally installed
[nodemon](https://github.com/remy/nodemon) to automatically
restart the server whenever the server source code changes.

```
nodemon
```
# Run

To run the server simply:

```
node index.js --slides ../path/to/slides/folder
```

This will serve the files at the shown port.
You can use `--port 4321` to change the port it is listening to.

# MVP

D The MVP will only support a list of images.
D Delay will be the same number for all of them.
D There is no admin page. It is just a JSN file.
D The image transition is smooth.
D It should react when the data on the server changes (invalidate cache somehow).

# Next versions:

* Run on cloud
* Security (login/helmet, etc)
* Persistence with PouchDB
* Admin portal
* Live updating according to the latest changes in database
* reordering of slides
* set a time range for when a slide can be visible
* variable durations
* PowerPoint style templates with text
* URLs
* down/counters
* Make a nice logo
* Put the big logo behind the body
* Make a loading animation if necessary
* Coffeescript/Stylus/YAML?

## New Algorithm:

* Get the list of slides from the server.
* If there is no slide, show the default diagnostics page.
* Change them one by one.
* Let the browser cache handle the load, just keep two at a time.
* If an error happens show the error & diagnostics page.
* Sync the time with the server if the down counter is implemented.

## diagnostics page

* What went wrong (and how to solve it)
* Serve URL
* Resolution
* Some basic info about the important features of the browser that we're using
* Some performance benchmark of the browser can be nice
* An indicator for the next retry to see if the error is solved
* Branding and logo

## Show proper messages on screen subtly and professionally:

* When the server is unreachable (maybe temporarily)
* When the image cannot be loaded for some reason (bad format, too big, etc)
* When an internal error happens for some reason (have a built-in console.log using DOM) and listen to window.onerror()
* When there is no image on the server

## Diagnostics mode:

* Server asks all clients to show ID/IP, resolution, server url, etc.

## Interactivity:

* Go to next slide on a click of a mouse

# Directory structure

### Shared:

* The browser application
* Shared templates

### User based

* Templates
* Presentation

# Data architecture

## Presentation

Is a collection of slides in the order.

### Slide

Type:

* URL
* image
* template + text
* counter(date+time) + text + image

Meta:

* Active
* Schedule (for when to show/hide, date+time,calendar, etc.)
* How long to show (auto = word count + defaultMin)

# Business model

Free: 10 slides, HD quality, no custom templates, up to 10 screens
Paid: 100 slides, 4k quality, custom templates, up to 100 screens, mail support, custom per-screen ids.
