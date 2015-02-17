---
title: "Generating and Serving HTML on Express Server"
---

Recently I encountered a situation where I wanted to generate and serve up a
HTML page based on the information I receive from the database that is connected
to the Express server. To do this, I built a server-side HTML Generator. Here is
the basic version of the code.

```
var htmlGenerator = function(req, res, data) {
  // host variable is useful for loading static files
  var host = req.headers.host;

  // content-type of the response is html
  res.writeHead(200, {
    'Content-Type': 'text/html'
  });

  // add necessary html header elements
  var html = createHeader(host);

  // create body of the html
  html = createContents(host, html, data);

  // write generated html onto the response
  res.write(html);

  // end the response and serve up the html
  res.end();
};
```

Let's look at each function that adds components to the html string.

```
var createHeader = function(host) {
  var html = '';

  html += '<!DOCTYPE html><html><head>';

  // add bootstrap css
  html += '<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">';

  // use host variable to load your script
  html += '<script type="text/javascript" src="http://' + host + '/app.js"></script>';

  html += '</head>';
};

var createContents = function(host, html, data) {
  html += '<body>';

  // populate the body
  html += '<p>' + data + '</p>';

  // wrap the html with closing tags
  html += '</body></html>';
};
```

As seen above, **createHeader** function adds necessary header elements such as css and
scripts to the html string, and **createContents** function adds elements that reside
within the body tag.

Once the html string is populated, **res.write(html)** will write that html string
to the response, and **res.end()** will serve up the html page.

While this HTML generator is fully functional, you may also want to take a look at
template engines such as [jade](http://jade-lang.com/) if you are interested in this topic.
