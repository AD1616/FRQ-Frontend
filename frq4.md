# FRQ 4

<table>
    <thead>
    <tr>
        <th>Off/On</th>
        <th>Quality</th>
        <th>Light</th>
        <th>Image</th>
    </tr>
    </thead>
    <tbody id="result">
    <!-- generated rows -->
    </tbody>
</table>

<style>
.circle {
  height: 50px;
  width: 50px;
  border-radius: 50%;
}
</style>

<script>

function componentToHex(c) {
    c = Math.round(c);
    let hex = c.toString(16);
    return hex.length == 1 ? "0" + hex : hex;
}
function rgbToHex(r, g, b) {
    return "#" + componentToHex(r) + componentToHex(g) + componentToHex(b);
}

const resultContainer = document.getElementById("result");

fetch('https://breadbops.gq/api/lights/')
  .then((response) => response.json())
  .then(data => {
    console.log(data);
    
    for (const cell of data) {  

        const tr = document.createElement("tr");
        const row = document.createElement("td");
        const column = document.createElement("td");
        const light = document.createElement("td");
        const image = document.createElement("div");

        image.className = "circle";
        gray = cell["light"]["luminosity"] * 255/1000;
        image.style.backgroundColor = rgbToHex(gray, gray, gray);

        if (cell["light"]["on"]) {
            row.innerHTML = "On";
        }
        else {
            row.innerHTML = "Off";
        }
        column.innerHTML = cell["light"]["quality"]; 
        light.innerHTML = cell["light"]["luminosity"]; 

        tr.appendChild(row);
        tr.appendChild(column);
        tr.appendChild(light);
        tr.appendChild(image);

        resultContainer.appendChild(tr);

    }
  })

</script>