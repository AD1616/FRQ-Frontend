# FRQ 3

<p id="eqResult"></p>

<input id="inputEq" placeholder="Input equation here">
    <button onclick="getEq(getInputEq())">Calculate Equation</button>

<script>

function getInputEq(){
    let equation = document.getElementById("inputEq").value;
    console.log(equation);
    return equation;
}

function getEq(eq) {
    eqResult = document.getElementById("eqResult");
    fetch('https://breadbops.gq/api/calculator/' + eq)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        eqResult.innerHTML = data.Result;
    })
}

</script>