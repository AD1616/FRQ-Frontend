# FRQ 1





<script>


function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}


function CarYear(year) {
    
    result = document.getElementById("CarResult");

    // it always says false now
    fetch('https://breadbops.gq/api/calendar/fetchCars/honda/' + year)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = year + data.CarYear;

    })
}

</script>

### Check Honda models for a certain year
<input id="inputYear" placeholder="Input Year">
<button onclick="CarYear(getYear())">Submit</button>
<p id="CarYearResult"></p>

<!-- ### Check the Number of Leap Years in an Interval -->
<!-- <input id="inputYear1" placeholder="Input Starting Year">
    <input id="inputYear2" placeholder="Input Ending Year">
    <button onclick="numberOfLeapYears(getYear1(), getYear2())">Submit</button>
<p id="numberOfLeapYearsResult"></p> -->



<form>
      <label for = "year" class = "label"> Enter a year:<label><br>
      <input type = "number" id = "year" name = "year" class = "input"><br>
      <input type = "submit" class = "button">
    </form>
<script>
    // Deployed API URL
        const API_URL = 'https://breadbops.gq/api/calendar/fetchCars/honda/';
        document.getElementById('input-form').addEventListener('submit', (event) => {
            event.preventDefault();
            var year = document.getElementById('year').value;
            // Combine API URL with expression.
fetch('https://breadbops.gq/api/calendar/fetchCars/honda/' + ${year})
            .then(response => response.json())
            .then(data => {
                // Output data to table
                const table = document.getElementById('results');
                const row = table.insertRow(-1);
                const Cell = row.insertCell(0);
                const isLeapYearCell = row.insertCell(1);
                Cell.innerHTML = data.year;
                isLeapYearCell.innerHTML = data.isLeapYear;
            });
        });
  </script>