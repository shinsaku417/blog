---
title: "Deploying Angular/Node/Express App with Heroku"
---

My team and I have been working on a Legacy Project at Hack Reactor, which takes on
other group's codebase and adding new features on top of it. One of the things
we focused first is to deploy our project and make it go live. We had a rough time
deploying our previous project with [Microsoft Azure](http://azure.microsoft.com/en-us/), so this time we decided to
deploy our app using [Heroku](https://www.heroku.com/).

Heroku provided us with an extremely useful [tutorial](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction). Each step
is very short and well explained, and we had a much smoother time with Heroku than
we had with Azure. There were couple important things to keep in mind.

## Make a Procfile (with no extension)

Our Procfile looked something like this:

```js
web: node server.js
```

This tells Heroku to spin up a node server by running node server.js.

## Define environmental variables

Use config variables that you can define in the Heroku website such that your
app will not be using any local host and ports. You can also define your API keys
in the config variables as well.

```js
var port = PROCESS.ENV.PORT;
var API_KEY = PROCESS.ENV.API_KEY;
```

## Using Bower install

Our app didn't have any bower dependencies installed when we added bower install
in the Procfile. To solve this problem, we added the following in our package.json:

```js
"dependencies": {
  // your other dependencies
  "bower": "~1.3.3"
},
"scripts": {
  "postinstall": "./node_modules/bower/bin/bower install"
}
```

By including bower in the node modules, Heroku will first run npm install and
install bower within the node_modules, then after npm install is done, it will
run bower install using bower in the node modules. With this, our app now has
all of bower dependencies installed.
