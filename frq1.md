# FRQ 1


<script>

function numberOfLeapYears(year1, year2) {
    
    result = document.getElementById("numberOfLeapYearsResult");

    // Fetch data from API
    fetch('https://breadbops.gq/api/calendar/numberOfLeapYears/' + year1 + "/" + year2)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "Leap Years between " + year1 + "and " + year2 + ": " + data.numberOfLeapYears;

    })
}

function getYear1(){
    let inputYear1 = document.getElementById("inputYear1").value;
    return inputYear1;
}

function getYear2(){
    let inputYear2 = document.getElementById("inputYear2").value;
    return inputYear2;
}

function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}

function getMonth1(){
    let inputMonth1 = document.getElementById("inputMonth1").value;
    return inputMonth1;
}

function getDay1(){
    let inputDay1 = document.getElementById("inputDay1").value;
    return inputDay1;
}


function isLeapYear(yearparam) {
    
    result = document.getElementById("isLeapYearResult");

    // Fetch data from API
    fetch('https://breadbops.gq/api/calendar/isLeapYear/' + yearparam)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "Is " + yearparam + " a leap year: " + data.isLeapYear;

    })
}

function dayOfYear(month1, day1) {
    
    result = document.getElementById("dayOfYearResult");

    // Fetch data from API
    fetch('https://breadbops.gq/api/calendar/dayOfYear/' + yearparam)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = month1 + "" + day1  + " is the " + data.dayOfYear "of the year";

    })
}

</script>

### Check if a Year is a Leap Year
<input id="inputYear" placeholder="Input a Year">
<button onclick="isLeapYear(getYear())">Submit</button>
<p id="isLeapYearResult"></p>

### Check the Number of Leap Years in an Interval
<input id="inputYear1" placeholder="Input Starting Year">
    <input id="inputYear2" placeholder="Input Ending Year">
    <button onclick="numberOfLeapYears(getYear1(), getYear2())">Submit</button>
<p id="numberOfLeapYearsResult"></p>

### Check Day Of Year
<input id="inputMonth1" placeholder="Input Month">
    <input id="inputDay1" placeholder="Input Day">
    <button onclick="dayOfYear(getMonth1(), getDay1())">Submit</button>
<p id="dayOfYearResult"></p>
