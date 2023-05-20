[Student registration form codes.docx](https://github.com/Ikramlechqer/Student-registration-form/files/11523168/Student.registration.form.codes.docx)
# Student-registration-form
Student registration form that allows users to input their information and stores in a MySQL database 



<!DOCTYPE html>

<html>

<body>

<h2>Student Registration Form</h2>

<form action="insert.php" method="post">

  Full Name:<br>

  <input type="text" name="full_name" required>

  <br>

  Email:<br>

  <input type="email" name="email" required>

  <br>

  Gender:<br>

  <input type="radio" name="gender" value="Male" required> Male

  <input type="radio" name="gender" value="Female"> Female

  <br><br>

  <input type="submit" value="Submit">

</form> 

</body>

</html>


<?php

$servername = "localhost";

$username = "root";

$password = ""; // use your database password

$dbname = "myDB"; // your database name

// Create connection

$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection

if ($conn->connect_error) {

  die("Connection failed: " . $conn->connect_error);

}

// sql to create table

$sql = "CREATE TABLE IF NOT EXISTS students (

id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,

full_name VARCHAR(30) NOT NULL,

email VARCHAR(50),

gender ENUM('Male','Female')

)";

if ($conn->query($sql) === TRUE) {

  echo "Table students created successfully";

} else {

  echo "Error creating table: " . $conn->error;

}

$conn->close();

?>

<?php

require 'db.php';

$full_name = $_POST['full_name'];

$email = $_POST['email'];

$gender = $_POST['gender'];

$sql = "INSERT INTO students (full_name, email, gender) VALUES ('$full_name', '$email', '$gender')";

if ($conn->query($sql) === TRUE) {

  echo "New record created successfully";

} else {

  echo "Error: " . $sql . "<br>" . $conn->error;

}

$conn->close();

?>

}
