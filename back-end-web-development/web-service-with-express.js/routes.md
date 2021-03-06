# Routes

## What are Routes?

Routing is the mechanism by which an application responds to request to a particular API endpoint.

For example, a client can make a GET, POST, PUT or DELETE http request for various URLs \(e.g. GET [http://localhost:3000/books](http://localhost:3000/books) or DELETE [http://localhost:3000/students/42](http://localhost:3000/students/42)\).

Based on the URL which is accessed, a different function on the web server will be called. For example, GET [http://localhost:3000/books](http://localhost:3000/books) will get a list of books, and DELETE [http://localhost:3000/students/42](http://localhost:3000/students/42) will remove the student with id of 42. This is the concept of **routing**.

Each route can have one or more handler functions, which are executed when the route is matched.

A simple route example can be found in `express_basic_example_1.js`

```text
node express_basic_example_1.js
```

After the application is started, access the two URLs and you should see different response on the browser page.

[http://localhost:3000/books](http://localhost:3000/books)

[http://localhost:3000/students](http://localhost:3000/students)

### You can have multiple route handlers for one path

Actually, you may define more than one route handlers

You can call `app.METHOD` multiple times, like

```javascript
app.get(path, route_handler1);
app.get(path, route_handler2);
```

or you can declare the handler in one line, like

```javascript
app.get(path, route_handler1, route_handler2);
```

Note that the handlers are executed in the same order as declaration. In the example above, route\_handler1 is called before route\_handler2.

This is illustrated in `express_basic_example_2.js`

```text
node express_basic_example_2.js
```

If you send a request to \`[http://localhost:3000/students](http://localhost:3000/students)", you should see the output of both route handlers, printed in the right sequence.

There are something to take note when there are multiple handlers are used for the same route:

* How an route handler passes the request to the next route handler via next\(\) call
* When we are not ready to send back the response yet, we use `response.write()` method to update the response, instead of using `response.send()` method
* If a route handler needs to send the response back to client, it should call `response.end()` method.

