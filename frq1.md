# FRQ 1





<script>
function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}


function isLeapYear(yearparam) {
    
    result = document.getElementById("isLeapYearResult");
    console.log(yearparam);
    // Fetch data from API
    fetch('https://breadbops.gq/api/calendar/fetchCars/honda/' + yearparam)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "Is " + yearparam + " a leap year: " + data.isLeapYear;

    })
}

</script>

### Check if a Year is a Leap Year
<input id="inputYear" placeholder="Input a Year">
<button onclick="isLeapYear(getYear())">Submit</button>
<p id="isLeapYearResult"></p>
