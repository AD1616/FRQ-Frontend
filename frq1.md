# FRQ 1


<table id="idk"></table>


<script>

let table = document.getElemenetById("idk");

function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}
function getBrand(){
    let inputBrand = document.getElementById("inputBrand").value;
    return inputBrand;
}


function isLeapYear(brandparam, yearparam) {
    
    result = document.getElementById("isLeapYearResult");
    console.log(yearparam);
    console.log(brandparam);
    // Fetch data from API
    fetch('https://breadbops.gq/api/calendar/fetchCars/' + brandparam + "/" + yearparam)
    .then(response => response.json())
    .then(data => {

const table = document.getElementById('idk');
        while (table.rows.length > 1) {
          table.deleteRow(-1);
        }
        console.log(data);
        for (const car of data.Results) {
          const row = table.insertRow(-1);
          row.insertCell(-1).innerHTML = car.Make_ID;
          row.insertCell(-1).innerHTML = car.Model_ID;
          row.insertCell(-1).innerHTML = car.Make_Name;
          row.insertCell(-1).innerHTML = car.Model_Name;
        }

        result.innerHTML =  yearparam + brandparam + data.Results;

    })
}

</script>

### Car Models for Honda Year
<input id="inputYear" placeholder="Input a Year">
<input id="inputBrand" placeholder="Input a Brand">
<button onclick="isLeapYear(getBrand(), getYear())">Submit</button>
<p id="isLeapYearResult"></p>
