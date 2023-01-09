# FRQ 2

<html>
<head>
  <title>Person API</title>
</head>
<body>
  <h1>Person API</h1>

  <!-- Form to input new person -->
  <form id="person-form">
    Email: <input type="text" name="email"><br>
    Password: <input type="text" name="password"><br>
    Name: <input type="text" name="name"><br>
    DOB: <input type="text" name="dob"><br>
    <input type="submit" value="Submit">
  </form>

  <!-- Table to display people -->
  <table id="people-table">
    <tr>
      <th>ID</th>
      <th>Email</th>
      <th>Name</th>
      <th>DOB</th>
    </tr>
  </table>

  <script>
    // Get form element
    const form = document.getElementById('person-form');

    // Handle form submission
    form.addEventListener('submit', (event) => {
      event.preventDefault();  // prevent page reload

      // Get form data
      const data = new FormData(form);

      // Send POST request to API
      fetch('https://breadbops.gq/api/person/post', {
        method: 'POST',
        body: data
      })
      .then(response => response.text())  // parse response as text
      .then(message => {
        alert(message);  // show message from API
      });
    });

    // Send GET request to API to get list of people
    fetch('https://breadbops.gq/api/person/')
    .then(response => response.json())  // parse response as JSON
    .then(people => {
      // Get table element
      const table = document.getElementById('people-table');

      // Add each person to the table
      people.forEach(person => {
        const row = document.createElement('tr');
        row.innerHTML = `
          <td>${person.id}</td>
          <td>${person.email}</td>
          <td>${person.name}</td>
          <td>${person.dob}</td>
        `;
        table.appendChild(row);
      });
    });
  </script>
</body>
</html>
