# Flask Repl Auth Web Application

## Introduction
This is a basic Flask web application that allows Replit users to authenticate using Repl Auth. Once authenticated, the user's account information is displayed on the web page.

## Prerequisites
Replit Account - Ensure you have a Replit account to run and test the application.

## Getting Started
Create a new Python repl on Replit and give it a name.

Open the main.py file and add the provided Flask code.

python

from flask import Flask, render_template, request

app = Flask('app')

@app.route('/')

def home():

  return render_template('index.html')

app.run(host='0.0.0.0', port=8080)

Create a templates folder in the root directory and add a new file named index.html with the provided HTML code.

html

Copy code

<!DOCTYPE html>

<html>
  
  <head>
    
    <title>Repl Auth</title>
    
  </head>
  
  <body>
    
    Hello !
    
  </body>
</html>
Run the code, and you should see 'Hello, Replit!' in the browser.

## Authentication
To enable authentication, add the following script within the body of the index.html page:

html

<div>
  
  <script
    
    authed="location.reload()"
    
    src="https://auth.util.repl.co/script.js"
    
  ></script>
  
</div>

This script provides a "Login with Replit" button.

## Retrieving User Information
To retrieve user information, update the home() function in main.py:

python

@app.route('/')

def home():

    return render_template(
    
        'index.html',
        
        user_id=request.headers['X-Replit-User-Id'],
        
        user_name=request.headers['X-Replit-User-Name'],
        
        user_roles=request.headers['X-Replit-User-Roles']
        
    )
    
Update the index.html file to display user information:

html

<body>
  
  {% if user_id %}
  
  <h1>Hello, {{ user_name }}!</h1>
  
  <p>Your user id is {{ user_id }}.</p>
  
  {% else %} Hello! Please log in.
  
  <div>
    
    <script
    
      authed="location.reload()"
      
      src="https://auth.util.repl.co/script.js"
      
    ></script>
    
  </div>
  
  {% endif %}
  
</body>

![Repl flask Auth ](https://github.com/Mithun1508/Python-Flask-Authentication-/assets/93249038/13c190b5-d6af-4562-9e3b-ad1f2bbb0dbe)

## License
This project is licensed under the MIT License.

