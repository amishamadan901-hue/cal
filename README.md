<!DOCTYPE html>
<html>
<head>
<title>Simple Calculator</title>

<style>
body {
  text-align: center;
  font-family: Arial;
}

button:hover {
  background-color: lightblue;
}
</style>

</head>

<body>

<h2>Calculator</h2>

<input type="number" id="n1" placeholder="Number 1"><br><br>
<input type="number" id="n2" placeholder="Number 2"><br><br>

<button onclick="calculate('+')">Add</button>
<button onclick="calculate('-')">Subtract</button>
<button onclick="calculate('*')">Multiply</button>
<button onclick="calculate('/')">Divide</button>
<br><br>

<button onclick="saveResult()">Save Result</button>

<h3 id="res"></h3>

<script>

let result = "";

// one function for all operations
function calculate(op) {

  let a = Number(document.getElementById("n1").value);
  let b = Number(document.getElementById("n2").value);

  if (op === '+') result = a + b;
  else if (op === '-') result = a - b;
  else if (op === '*') result = a * b;
  else if (op === '/') {
    if (b === 0) result = "Cannot divide by 0";
    else result = a / b;
  }

  document.getElementById("res").innerText = "Result: " + result;
}

// save result to file
function saveResult() {

  let content = "Result: " + result;

  let file = new Blob([content], { type: "text/plain" });

  let link = document.createElement("a");
  link.href = URL.createObjectURL(file);
  link.download = "result.txt";

  link.click();
}

</script>

</body>
</html>
