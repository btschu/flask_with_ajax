# flask_with_ajax

Objectives:

- Discuss responding with JSON
- Understand how to communicate with Flask via AJAX

Now that we understand how to use fetch to get data from another server, the next step is to be able to communicate with our own servers.  In our flask app we will start responding with JSON instead of rendering templates.

Somewhere in a controller file . . .

```
from flask import jsonify
from flask_app import app
@app.route('/get_data')
def get_data():
    # jsonify will serialize data into JSON format.
    return jsonify(message="Hello World")
```

Somewhere in your static javascript file . . .

```
function getData(){
    fetch('http://localhost:5000/get_data')
        .then( response => response.json() )
        .then( data => console.log(data) )
}
// Prints out { message : "Hello World" }
getData();
```

And now we can fetch data from our own server!!!

To understand this process a bit further let's create an example together.

- Go ahead and create a new ERD in MySQL workbench that looks like this with the schema called user_names:

- Once you created the ERD, or dowloaded the file and opened in MySQL Workbench, go ahead and forward engineer it to your local database.

- Create a couple of rows in your users table using a SQL query.

- Download this basic MVC Flask App.  Make sure to change the mysql password for your config file to your own password!!!

- Once opened in VSCode, run pipenv install flask PyMySQL in the terminal.
Then run the server.

- We are now rendering a template for our index route and using our javascript file to get the data and insert it into the table.

