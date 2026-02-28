# Zodiaczone
Personalized Daily Horoscope Website with Real Astrology API
<!DOCTYPE html>
<html>
<head>
<title>🔮 Cosmic Horoscope Portal</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
margin:0;
font-family:'Segoe UI',sans-serif;
background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);
display:flex;
justify-content:center;
align-items:center;
height:100vh;
overflow:hidden;
color:white;
}

/* Floating Stars */
body::before{
content:"";
position:absolute;
width:200%;
height:200%;
background:url('https://www.transparenttextures.com/patterns/stardust.png');
animation:moveStars 60s linear infinite;
opacity:0.3;
}

@keyframes moveStars{
from{transform:translate(0,0);}
to{transform:translate(-500px,-500px);}
}

.card{
position:relative;
background:rgba(255,255,255,0.1);
backdrop-filter:blur(15px);
padding:25px;
width:90%;
max-width:400px;
border-radius:20px;
box-shadow:0 8px 30px rgba(0,0,0,0.6);
text-align:center;
z-index:1;
}

h2{
margin-bottom:15px;
}

input,select{
width:100%;
padding:10px;
margin:8px 0;
border-radius:8px;
border:none;
outline:none;
}

button{
width:100%;
padding:10px;
background:#ffcc70;
color:black;
border:none;
border-radius:8px;
font-weight:bold;
cursor:pointer;
}

button:hover{
background:#ffd88a;
}

.result{
margin-top:15px;
padding:12px;
background:rgba(255,255,255,0.15);
border-radius:10px;
font-size:14px;
}
</style>
</head>

<body>

<div class="card">

<h2>🌙 Cosmic Horoscope 🔮</h2>

<input type="text" id="name" placeholder="Enter Your Name ✨">

<select id="rasi">
<option value="">Select Zodiac ♈</option>
<option value="aries">♈ Aries</option>
<option value="taurus">♉ Taurus</option>
<option value="gemini">♊ Gemini</option>
<option value="cancer">♋ Cancer</option>
<option value="leo">♌ Leo</option>
<option value="virgo">♍ Virgo</option>
<option value="libra">♎ Libra</option>
<option value="scorpio">♏ Scorpio</option>
<option value="sagittarius">♐ Sagittarius</option>
<option value="capricorn">♑ Capricorn</option>
<option value="aquarius">♒ Aquarius</option>
<option value="pisces">♓ Pisces</option>
</select>

<select id="nakshatra">
<option value="">Select Nakshatra 🌟</option>
<option>Ashwini</option>
<option>Bharani</option>
<option>Krittika</option>
<option>Rohini</option>
<option>Mrigashira</option>
<option>Ardra</option>
<option>Punarvasu</option>
<option>Pushya</option>
<option>Ashlesha</option>
<option>Magha</option>
<option>Purva Phalguni</option>
<option>Uttara Phalguni</option>
<option>Hasta</option>
<option>Chitra</option>
<option>Swati</option>
<option>Vishakha</option>
<option>Anuradha</option>
<option>Jyeshtha</option>
<option>Mula</option>
<option>Purva Ashadha</option>
<option>Uttara Ashadha</option>
<option>Shravana</option>
<option>Dhanishta</option>
<option>Shatabhisha</option>
<option>Purva Bhadrapada</option>
<option>Uttara Bhadrapada</option>
<option>Revati</option>
</select>

<button onclick="getHoroscope()">✨ Reveal My Destiny ✨</button>

<div class="result" id="result"></div>

</div>

<script>

async function getHoroscope(){

let name=document.getElementById("name").value;
let sign=document.getElementById("rasi").value;
let nak=document.getElementById("nakshatra").value;

if(name==""||sign==""||nak==""){
alert("Please fill all details 🌟");
return;
}

let response=await fetch(
"https://aztro.sameerkumar.website/?sign="+sign+"&day=today",
{method:"POST"}
);

let data=await response.json();

document.getElementById("result").innerHTML=
"<b>🌟 Hello "+name+"!</b><br><br>"+
"🔮 Zodiac: "+sign.toUpperCase()+"<br>"+
"✨ Nakshatra: "+nak+"<br><br>"+
"📅 Date: "+data.current_date+"<br><br>"+
"🌙 Horoscope:<br>"+data.description+"<br><br>"+
"😊 Mood: "+data.mood+"<br>"+
"🍀 Lucky Number: "+data.lucky_number+"<br>"+
"⏰ Lucky Time: "+data.lucky_time;
}

</script>

</body>
</html>
