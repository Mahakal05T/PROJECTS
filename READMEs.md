Simple HTTP Server with MySQL Integration
This project implements a simple HTTP server in Python that interacts with a MySQL database to handle user data. The server provides endpoints for submitting user data and fetching all stored user data. Additionally, it includes a frontend with basic JavaScript to interact with the server.

Features
Submit User Data: Accepts user data via a POST request and stores it in a MySQL database.
Fetch User Data: Returns all stored user data via a GET request.
Frontend Integration: Includes JavaScript to handle form submission, data fetching, and form clearing.
Requirements
Python 3.x
MySQL
Required Python Packages: mysql-connector-python
Setup
Database Setup
Install MySQL: Ensure MySQL is installed on your system.
Create Database and Table:
sql

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
Python Environment Setup
Install Python Packages:

pip install mysql-connector-python
Download the Code: Clone this repository or download the code files.

Database Configuration: Update the db_config dictionary in the Python script with your MySQL credentials.

db_config = {
    'user': 'your_username',
    'password': 'your_password',
    'host': 'localhost',
    'database': 'user_data'
}
Running the Server
Run the Python Server:

python server.py
This will start the server on http://localhost:8080.
Usage
Endpoints
POST /submit: Submits user data to the server.

Request Body (JSON):


{
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "1234567890",
    "dob": "1990-01-01",
    "description": "Sample user description"
}
GET /show: Fetches all stored user data.

Response Body (JSON):


[
    {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "phone": "1234567890",
        "dob": "1990-01-01",
        "description": "Sample user description"
    }
    // more users
]

Frontend Integration
Clear Form: The clear button resets all form fields.
Submit Form: The submit button sends form data to the server.
Show Data: The show button fetches and displays all stored user data.

document.getElementById('clearBtn').addEventListener('click', () => {
    document.getElementById('userForm').reset();
});

document.getElementById('submitBtn').addEventListen('click', () => {
    const name = document.getElementById('name').value;
    const email = document.getElementById('email').value;
    const phone = document.getElementById('phone').value;
    const dob = document.getElementById('dob').value;
    const description = document.getElementById('description').value;

    const data = { name, email, phone, dob, description };

    fetch('/submit', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(data),
    }).then(response => response.json())
      .then(data => {
          if (data.status === 'success') {
              alert('Data submitted successfully!');
          } else {
              alert('Data submission failed!');
          }
      })
      .catch(error => {
          console.error('Error:', error);
          alert('An error occurred while submitting data.');
      });
});

document.getElementById('showBtn').addEventListener('click', () => {
    fetch('/show')
        .then(response => response.json())
        .then(data => {
            const dataContainer = document.getElementById('dataContainer');
            dataContainer.textContent = JSON.stringify(data, null, 2);
            document.getElementById('dataDisplay').classList.remove('hidden');
        })
        .catch(error => {
            console.error('Error:', error);
            alert('An error occurred while fetching data.');
        });
});
Contributing
Feel free to open issues or submit pull requests for any improvements or bug fixes.