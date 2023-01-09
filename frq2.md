# FRQ 2


<!-- person-form.html -->
<form class="person-form">
  <label for="email">Email:</label>
  <input type="email" name="email" required>
  <br>
  <label for="password">Password:</label>
  <input type="password" name="password" required>
  <br>
  <label for="name">Name:</label>
  <input type="text" name="name" required>
  <br>
  <label for="dob">Date of Birth:</label>
  <input type="date" name="dob" required>
  <br>
  <input type="submit" value="Submit">
</form>

<!-- display the input fields -->
<div class="person-display"></div>

<!-- app.js -->

<style>
const personFormElement = document.querySelector(".person-form");
const personDisplayElement = document.querySelector(".person-display");

personFormElement.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = new FormData(personFormElement);
  const personData = {
    email: formData.get("email"),
    password: formData.get("password"),
    name: formData.get("name"),
    dob: formData.get("dob")
  };

  const person = new Person(personData.email, personData.password, personData.name, personData.dob);
  // Do something with the person object, such as send it to an API

  // Display the input fields
  personDisplayElement.innerHTML = `
    <p>Email: ${person.email}</p>
    <p>Password: ${person.password}</p>
    <p>Name: ${person.name}</p>
    <p>Date of Birth: ${person.dob}</p>
  `;
});
</style>