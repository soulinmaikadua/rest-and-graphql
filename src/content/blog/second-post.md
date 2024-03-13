---
title: "PHP create"
description: "Lorem ipsum dolor sit amet"
pubDate: "Jul 15 2022"
heroImage: "/rest-and-graphql/blog-placeholder-4.jpg"
---

```php
<?php

// Define database connection parameters
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "my_database";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Check if the request is a POST request
if ($_SERVER["REQUEST_METHOD"] === "POST") {
    // Get the POST data
    $first_name = $_POST["first_name"];
    $last_name = $_POST["last_name"];
    $email = $_POST["email"];
    $password = $_POST["password"];

    // Prepare SQL statement to insert user data into the database
    $sql = "INSERT INTO users (first_name, last_name, email, password) VALUES (?, ?, ?, ?)";

    // Prepare the SQL statement
    $stmt = $conn->prepare($sql);

    // Bind parameters to the prepared statement
    $stmt->bind_param("ssss", $first_name, $last_name, $email, $password_hash);

    // Hash the password
    $password_hash = password_hash($password, PASSWORD_DEFAULT);

    // Execute the prepared statement
    if ($stmt->execute()) {
        // User created successfully
        $response = array("success" => true, "message" => "User created successfully");
    } else {
        // Error creating user
        $response = array("success" => false, "message" => "Error: " . $conn->error);
    }

    // Close the prepared statement
    $stmt->close();

    // Respond with JSON
    header('Content-Type: application/json');
    echo json_encode($response);
}

// Close the database connection
$conn->close();
?>

```
