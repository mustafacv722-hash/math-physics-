<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Al-Harithiya Calculator</title>
<style>
body { 
  background: #111; 
  color: white; 
  font-family: Arial; 
  text-align: center; 
  padding: 30px; 
  margin:0;
}
h1 { margin-bottom: 20px; }

input { 
  padding: 12px; 
  width: 320px; 
  font-size: 18px; 
  border-radius: 10px; 
  border: 1px solid #555; 
  text-align: center; 
  background: rgba(0,0,0,0.3);
  color:#fff;
  backdrop-filter: blur(5px);
  margin-bottom: 20px;
}

.button-container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
  margin-bottom: 20px;
}

.operation-box, .physics-box {
  background: rgba(135,206,250,0.3); /* سماوي مع بلور */
  backdrop-filter: blur(8px);
  padding: 15px;
  border-radius: 15px;
  max-width: 350px;
}

.operation-box h3, .physics-box h3 {
  margin-bottom: 10px;
  font-size: 18px;
}

button { 
  padding: 15px 20px; 
  margin: 5px; 
  font-size: 16px; 
  border:none; 
  cursor:pointer; 
  border-radius: 50%; 
  color:white;
  background: rgba(135,206,250,0.6); /* سماوي نصف شفاف */
  box-shadow: 2px 2px 5px rgba(0,0,0,0.5);
  transition: 0.2s;
  backdrop-filter: blur(5px);
}
button:hover { 
  transform: scale(1.1);
  box-shadow: 4px 4px 8px rgba(0,0,0,0.7);
}

p { font-size:18px; margin:5px 0; }
small { font-size:10px; color:#aaa; margin-top:20px; display:block; }

/* شاشة الترحيب */
#welcome-screen {
  position: absolute;
  top:0; left:0; right:0; bottom:0;
  background: rgba(0,0,0,0.9);
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

#welcome-screen h2 { font-size:24px; margin-bottom:10px; }
#welcome-screen p { font-size:16-18px; margin-bottom:10px; max-width:500px; }
#welcome-screen button {
  padding: 12px 25px;
  font-size:16px;
  border-radius: 12px;
}
</style>
</head>
<body>

<!-- شاشة الترحيب -->
<div id="welcome-screen">
  <h2>Hi! Welcome to Al-Harithiya Calculator</h2>
  <p>This is a smart calculator powered by AI, containing the most famous physics and math formulas.</p>
  <p>Designed by: Mustafa Ahmed Shaheed, Ali Saif, and Amir Ghaith Shawqi<br>
     with assistance from Mustafa Ahmed Khurshid</p>
  <button onclick="startCalculator()">Start</button>
</div>

<h1>Al-Harithiya Calculator</h1>
<input id="input" placeholder="Type operation or click button">

<div class="button-container">
  <!-- Math Operations -->
  <div class="operation-box">
    <h3>Math Operations</h3>
    <button onclick="addWord('plus')">plus</button>
    <button onclick="addWord('minus')">minus</button>
    <button onclick="addWord('multiply')">multiply</button>
    <button onclick="addWord('divide')">divide</button>
    <button onclick="addWord('power')">power</button>
    <button onclick="addWord('percent')">percent</button>
    <button onclick="clearInput()">C</button>
  </div>

  <!-- Physics Formulas -->
  <div class="physics-box">
    <h3>Physics Formulas</h3>
    <button onclick="setForce()">Force</button>
    <button onclick="setPressure()">Pressure</button>
    <button onclick="setEnergy()">Energy</button>
    <button onclick="setKinetic()">KineticEnergy</button>
    <button onclick="setGravity()">GravitationalForce</button>
    <button onclick="setOhm()">OhmsLaw</button>
    <button onclick="setWork()">Work</button>
    <button onclick="setPower()">Power</button>
    <button onclick="setDensity()">Density</button>
    <button onclick="setMomentum()">Momentum</button>
    <button onclick="setAcceleration()">Acceleration</button>
    <button onclick="clearInput()">C</button>
  </div>
</div>

<br>
<button onclick="calculate()">Confirm</button>

<h3>Result:</h3>
<p id="result"></p>

<h3>Explain:</h3>
<p id="explain"></p>

<small>
Made by Ali Saif Ali Mustafa Ahmed Shaheed Amir Ghaith Shawqi<br>
with the assistance of Mustafa Ahmed Khurshid<br>
First Grade A
</small>

<script>
function startCalculator() {
  document.getElementById("welcome-screen").style.display = "none";
}

function addWord(word) {
    document.getElementById("input").value += " " + word + " ";
}

function clearInput() {
    document.getElementById("input").value = "";
    document.getElementById("result").innerText = "";
    document.getElementById("explain").innerText = "";
}

// Physics formulas
function setForce(){
    let parts = prompt("Enter mass m and acceleration a separated by space").split(" ");
    document.getElementById("input").value = "F=" + parts.join(" multiply ");
}
function setPressure(){
    let parts = prompt("Enter force F and area A separated by space").split(" ");
    document.getElementById("input").value = "P=" + parts.join(" divide ");
}
function setEnergy(){
    let parts = prompt("Enter mass m and speed of light c separated by space").split(" ");
    document.getElementById("input").value = "E=" + parts.join(" multiply ") + " power 2";
}
function setKinetic(){
    let parts = prompt("Enter mass m and velocity v separated by space").split(" ");
    document.getElementById("input").value = "KE=0.5 multiply " + parts[0] + " multiply " + parts[1] + " power 2";
}
function setGravity(){
    let parts = prompt("Enter m1 m2 and distance r separated by space").split(" ");
    document.getElementById("input").value = "G=" + parts[0] + " multiply " + parts[1] + " divide " + parts[2] + " power 2";
}
function setOhm(){
    let parts = prompt("Enter current I and resistance R separated by space").split(" ");
    document.getElementById("input").value = "V=" + parts[0] + " multiply " + parts[1];
}
function setWork(){
    let parts = prompt("Enter force F and distance d separated by space").split(" ");
    document.getElementById("input").value = "W=" + parts[0] + " multiply " + parts[1];
}
function setPower(){
    let parts = prompt("Enter work W and time t separated by space").split(" ");
    document.getElementById("input").value = "P=" + parts[0] + " divide " + parts[1];
}
function setDensity(){
    let parts = prompt("Enter mass m and volume V separated by space").split(" ");
    document.getElementById("input").value = "rho=" + parts[0] + " divide " + parts[1];
}
function setMomentum(){
    let parts = prompt("Enter mass m and velocity v separated by space").split(" ");
    document.getElementById("input").value = "p=" + parts[0] + " multiply " + parts[1];
}
function setAcceleration(){
    let parts = prompt("Enter Δv and time t separated by space").split(" ");
    document.getElementById("input").value = "a=" + parts[0] + " divide " + parts[1];
}

// تفسير الكلمات إلى رموز داخلياً للحساب
function interpretInput(input) {
    input = input.toLowerCase();
    input = input
      .replace(/plus/g, '+')
      .replace(/minus/g, '-')
      .replace(/multiply/g, '*')
      .replace(/divide/g, '/')
      .replace(/power/g, '^')
      .replace(/percent/g, '%')
      .replace(/newton/g, '*1')
      .replace(/n/g, '*1')
      .replace(/pascal/g, '*1')
      .replace(/pa/g, '*1');
    return input;
}

function calculate() {
  let input = document.getElementById("input").value.trim();
  let resultText = "";
  let explainText = "";

  try {
    let processedInput = interpretInput(input);

    if(processedInput.includes("^")){
        let parts = processedInput.split("^");
        let base = parseFloat(parts[0]);
        let exp = parseFloat(parts[1]);
        let res = Math.pow(base, exp);
        resultText = res;
        explainText = `Base ${base} raised to power ${exp} = ${res}`;
    } 
    else if(/[\+\-\*\/%]/.test(processedInput)){
        let res = eval(processedInput);
        resultText = res;
        explainText = `Calculation ${input} = ${res}`;
    }
    else{
        resultText = "Unknown";
        explainText = "Type a valid operation or use buttons";
    }

  } catch(e){
    resultText = "Error";
    explainText = "Check your input format";
  }

  document.getElementById("result").innerText = resultText;
  document.getElementById("explain").innerText = explainText;
}
</script>

</body>
</html>
