# FRQ 2


<form id="form">
  Email: <input type="text" id="email"><br>
  Password: <input type="text" id="password"><br>
  Name: <input type="text" id="name"><br>
  Date of Birth: <input type="text" id="dob"><br>
  <input type="button" value="Submit" onclick="submitPerson()">
</form> 

<table id="table">
  <tr>
   <th>ID</th>
    <th>Email</th>
    <th>Password</th>
    <th>Name</th>
    <th>Date of Birth</th>
  </tr>
</table>


<script>
// Function to submit a person to the backend
function submitPerson() {
  // Get the values from the form
  const email = document.getElementById('email').value;
  const password = document.getElementById('password').value;
  const name = document.getElementById('name').value;
  const dob = document.getElementById('dob').value;

  // Make a POST request to the backend
  fetch('https://breadbops.gq/api/person/post', {
    method: 'POST',
    body: 'email=${email}&password=${password}&name=${name}&dob=${dob}',
  }).then(response => {
    // If the request was successful, get the list of people and update the table
    if (response.ok) {
      getPeople();
    }
  });
}

// Function to get the list of people and update the table
function getPeople() {
  // Make a GET request to the backend
  fetch('https://breadbops.gq/api/person/').then(response => {
    if (response.ok) {
      response.json().then(people => {
        // Clear the current table rows
        const table = document.getElementById('table');
        while (table.rows.length > 1) {
          table.deleteRow(-1);
        }

        // Add a row for each person
        for (const person of people) {
          const row = table.insertRow(-1);
          row.insertCell(-1).innerHTML = person.id;
          row.insertCell(-1).innerHTML = person.email;
          row.insertCell(-1).innerHTML = person.password;
          row.insertCell(-1).innerHTML = person.name;
          row.insertCell(-1).innerHTML = person.dob;
        }
      });
    }
  });
}

// Initially get the list of people and update the table
getPeople();

function getInputId(){
    let input = document.getElementById("inputId").value;
    console.log(input);
    return input;
}


function getId(id) {
    idResult = document.getElementById("idResult");

    if(id < 10452){
        idResult.innerHTML = "Invalid ID. Person 0 has an ID of 19.";
    }
    // Fetch data from API
    fetch('https://breadbops.gq/api/person/' + id)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        idResult.innerHTML = "Person: " + data.name;
    })
}

</script>

<p id="idResult"></p>

<input id="inputId" placeholder="Input Id">
    <button onclick="getId(getInputId())">Get Person by ID</button>

<br>