# FRQ 2

<!DOCTYPE html>
<html>
<head>
	<title>Input Form</title>
</head>
<body>
	<form>
		Email:<br>
		<input type="email" id="email" required><br>
		Password:<br>
		<input type="password" id="password" required><br>
		Name:<br>
		<input type="text" id="name" required><br>
		Date of Birth:<br>
		<input type="date" id="dob" required><br>
		Cars:<br>
		<input type="text" id="cars"><br>
		<br>
		<button type="button" onclick="displayInputs()">Submit</button>
	</form> 
	<br>
	<div id="display"></div>
	
	<script>
		function displayInputs() {
			var email = document.getElementById("email").value;
			var password = document.getElementById("password").value;
			var name = document.getElementById("name").value;
			var dob = document.getElementById("dob").value;
			var cars = document.getElementById("cars").value;
			
			document.getElementById("display").innerHTML = "Email: " + email + "<br>Password: " + password + "<br>Name: " + name + "<br>Date of Birth: " + dob + "<br>Cars: " + cars;
		}
	</script>
</body>
</html>
