<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>World Cup 2026 Draw</title>

<style>
body {
  font-family: Arial;
  text-align: center;
  color: white;
  background-size: cover;
  background-position: center;
  transition: background 0.5s;
}
.container {
  background: rgba(0,0,0,0.7);
  padding: 20px;
  border-radius: 12px;
  margin: 20px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
  margin: 5px;
}
img {
  width: 120px;
  border-radius: 10px;
}
</style>
</head>

<body>

<div class="container">
<h1>⚽ World Cup 2026 Draw</h1>

<button onclick="draw()">Draw Country + Name</button>

<h2 id="country"></h2>
<p id="history"></p>
<p id="location"></p>
<p id="player"></p>
<img id="playerImg">

<hr>

<h3>Add Names (one per line)</h3>
<textarea id="nameInput" rows="4" cols="30"></textarea><br>
<button onclick="loadNames()">Load Names</button>
</div>

<script>
/* -------- COUNTRIES (EDITABLE) -------- */
let countries = [
{
 name:"USA",
 flag:"https://flagcdn.com/w320/us.png",
 history:"First played WC in 1930, best finish 3rd place.",
 location:"North America",
 player:"Landon Donovan",
 playerImg:"https://upload.wikimedia.org/wikipedia/commons/4/4f/Landon_Donovan_2019.jpg"
},
{
 name:"Mexico",
 flag:"https://flagcdn.com/w320/mx.png",
 history:"Played in 17 World Cups, famous for Round of 16 runs.",
 location:"North America",
 player:"Hugo Sánchez",
 playerImg:"https://upload.wikimedia.org/wikipedia/commons/9/9c/Hugo_Sanchez.jpg"
},
{
 name:"Brazil",
 flag:"https://flagcdn.com/w320/br.png",
 history:"5-time World Cup champions (record).",
 location:"South America",
 player:"Pelé",
 playerImg:"https://upload.wikimedia.org/wikipedia/commons/5/5c/Pele_con_brasil_%28cropped%29.jpg"
},
{
 name:"France",
 flag:"https://flagcdn.com/w320/fr.png",
 history:"Champions in 1998 and 2018.",
 location:"Europe",
 player:"Zinedine Zidane",
 playerImg:"https://upload.wikimedia.org/wikipedia/commons/5/5f/Zinedine_Zidane_2019.jpg"
}
];

/* -------- NAME SYSTEM -------- */
let namePool = [];
let nameCount = {};

/* Load names */
function loadNames() {
  let input = document.getElementById("nameInput").value.trim().split("\n");
  namePool = [];
  nameCount = {};
  input.forEach(n => {
    namePool.push(n);
    namePool.push(n); // twice
    nameCount[n] = 0;
  });
  alert("Names loaded!");
}

/* -------- DRAW FUNCTION -------- */
function draw() {
  if (countries.length === 0 || namePool.length === 0) {
    alert("No countries or names left!");
    return;
  }

  let cIndex = Math.floor(Math.random() * countries.length);
  let country = countries.splice(cIndex,1)[0];

  let nIndex = Math.floor(Math.random() * namePool.length);
  let name = namePool.splice(nIndex,1)[0];
  nameCount[name]++;

  document.body.style.backgroundImage = `url(${country.flag})`;

  document.getElementById("country").innerText =
    country.name + " → Assigned to: " + name;

  document.getElementById("history").innerText =
    "History: " + country.history;

  document.getElementById("location").innerText =
    "Location: " + country.location;

  document.getElementById("player").innerText =
    "Best Player: " + country.player;

  document.getElementById("playerImg").src =
    country.playerImg;
}
</script>

</body>
</html>
