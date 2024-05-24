Simple HTTP Server with MySQL Integration
This project is a simple HTTP server built in Python that interacts with a MySQL database to manage user data.

Features
Submit User Data: Accept user data via a POST request and store it in a MySQL database.
Fetch User Data: Retrieve all stored user data via a GET request.
Frontend Integration: Simple HTML/JavaScript frontend to interact with the server.
Prerequisites
Python 3.x installed
MySQL installed and running
mysql-connector-python package installed
Setup Instructions

Step 1: Database Setup
Install MySQL:
Download and install MySQL from the official website.
Create Database and Table:
Open your MySQL command line or MySQL Workbench.
Create a new database and table using the following commands:

CREATE DATABASE user_data;
USE user_data;
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255),
    phone VARCHAR(255),
    dob DATE,
    description TEXT
);

Step 2: Python Environment Setup
Install Required Python Package:
Open your terminal or command prompt.
Install mysql-connector-python package using pip:

pip install mysql-connector-python

Step 3: Configure Database Connection
Update Database Configuration:
Open the Python script.
Locate the db_config dictionary and update it with your MySQL credentials:


db_config = {
    'user': 'your_username',
    'password': 'your_password',
    'host': 'localhost',
    'database': 'user_data'
}

Step 4: Running the Server
Start the HTTP Server:
In your terminal or command prompt, navigate to the directory containing the Python script.
Run the server using Python:

python server.py
The server will start on http://localhost:8080.

Step 5: Using the Application
Submit User Data:

Use a tool like Postman or your frontend form to send a POST request to http://localhost:8080/submit.
The request body should be in JSON format and include the following fields: name, email, phone, dob, description.
Fetch User Data:

Send a GET request to http://localhost:8080/show.
The response will contain all stored user data in JSON format.
Frontend Interaction
Clear Form:

Click the "Clear" button to reset all form fields.
Submit Form:

Fill out the form and click the "Submit" button to send the data to the server.
Show Data:

Click the "Show" button to fetch and display all stored user data.
Contributing
We welcome contributions! Please open an issue or submit a pull request for any improvements or bug fixes.

License
This project is licensed under the MIT License.
