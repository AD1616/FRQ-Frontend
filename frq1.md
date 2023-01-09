# FRQ 1





<script>

// function numberOfLeapYears(year1, year2) {
    
//     result = document.getElementById("numberOfLeapYearsResult");

//     // backend doesnt have this yet
//     fetch('https://breadbops.gq/api/calendar/numberOfLeapYears/' + year1 + "/" + year2)
//     .then(response => response.json())
//     .then(data => {

//         console.log(data);

//         result.innerHTML = "Leap Years between " + year1 + "and " + year2 + ": " + data.numberOfLeapYears;

//     })
// }

// function getYear1(){
//     let inputYear1 = document.getElementById("inputYear1").value;
//     return inputYear1;
// }

// function getYear2(){
//     let inputYear2 = document.getElementById("inputYear2").value;
//     return inputYear2;
// }

function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}

//duplicate this to month, day, and year as before
//should have the day of year stuff when we put it in the backend.
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

### Check if a Year is a Leap Year
<input id="inputYear" placeholder="Is it a Leap Year?">
<button onclick="CarYear(getYear())">Submit</button>
<p id="CarYearResult"></p>

### Check the Number of Leap Years in an Interval
<!-- <input id="inputYear1" placeholder="Input Starting Year">
    <input id="inputYear2" placeholder="Input Ending Year">
    <button onclick="numberOfLeapYears(getYear1(), getYear2())">Submit</button>
<p id="numberOfLeapYearsResult"></p> -->