# Step 1: Setup Environment

First, make sure you have Python installed on your system. Then, install Flask and MySQL connector using pip:
pip install Flask
pip install mysql-connector-python

# Step 2: Setup MySQL Database

Create a MySQL database and a table to store the user information. You can do this using a MySQL client like phpMyAdmin or via command line:
CREATE DATABASE flask_demo;
USE flask_demo;
CREATE TABLE users (
id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(100) NOT NULL,
email VARCHAR(100) NOT NULL
);

# Step 3: Create Flask Application

Create a new directory for your Flask application and create a file named app.py:
from flask import Flask, render_template, request
import mysql.connector

app = Flask(**name**)

# MySQL Configuration

db = mysql.connector.connect(
host="localhost",
user="your_username",
password="your_password",
database="flask_demo"
)
cursor = db.cursor()

@app.route('/')
def index():
return render_template('index.html')

@app.route('/submit', methods=['POST'])
def submit():
if request.method == 'POST':
name = request.form['name']
email = request.form['email']

        # Insert data into the database
        sql = "INSERT INTO users (name, email) VALUES (%s, %s)"
        val = (name, email)
        cursor.execute(sql, val)
        db.commit()

        return 'Data Submitted Successfully!'

if **name** == '**main**':
app.run(debug=True)

# Step 4: Create HTML Template

Create a folder named templates inside your project directory, and inside it, create a file named index.html(Given below is the output of the html file):

<!-- <!DOCTYPE html> -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flask MySQL Form</title>
</head>
<body>
    <h3>Submit your information</h3>
    <form action="/submit" method="post">
        <label for="name">Name:</label><br>
        <input type="text" id="name" name="name" required><br><br>
        <label for="email">Email:</label><br>
        <input type="email" id="email" name="email" required><br><br>
        <input type="submit" value="Submit">
    </form>
</body>
</html>

# Step 5: Run the Application

Navigate to your project directory in the terminal and run the Flask application:
python app.py

# Step 6:

Visit http://localhost:5000 in your web browser, fill out the form, and submit. The data should be stored in the MySQL database.
