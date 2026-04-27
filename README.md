
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Kanii 💖</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:Arial, sans-serif;
}

body{
  overflow:hidden;
  background:black;
}

/* ===== STARS ===== */
.stars{
  position:fixed;
  width:100%;
  height:100vh;
  background:black;
  z-index:-2;
}

.star{
  position:absolute;
  width:2px;
  height:2px;
  background:white;
  border-radius:50%;
  animation:moveStars 10s linear infinite;
}

@keyframes moveStars{
  from{transform:translateY(0); opacity:1;}
  to{transform:translateY(-1000px); opacity:0;}
}

/* ===== SCREENS ===== */
.screen{
  position:absolute;
  width:100%;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  text-align:center;
  transition:1s ease;
  color:white;
  pointer-events:none;
}

.screen.center{pointer-events:auto;}

.center{transform:translateY(0);}
.up{transform:translateY(-100vh);}
.down{transform:translateY(100vh);}

/* INTRO */
#intro{
  background:black;
  font-size:22px;
  animation:fadeIn 3s ease;
}

@keyframes fadeIn{
  from{opacity:0;}
  to{opacity:1;}
}

/* INPUT */
input{
  padding:12px;
  border-radius:10px;
  border:none;
  outline:none;
  margin-top:15px;
  text-align:center;
}

button{
  margin-top:15px;
  padding:10px 25px;
  border:none;
  border-radius:20px;
  background:pink;
  cursor:pointer;
}

/* FINAL TEXT */
#loveText{
  font-size:34px;
  transition:1.5s ease;
  opacity:0;
  animation:glow 1s infinite alternate;
}

@keyframes glow{
  from{text-shadow:0 0 10px pink;}
  to{text-shadow:0 0 30px red;}
}

/* HEARTS & FLOWERS */
.heart,.flower{
  position:absolute;
  font-size:24px;
  animation:float 5s linear forwards;
}

@keyframes float{
  from{transform:translateY(0);opacity:1;}
  to{transform:translateY(-900px);opacity:0;}
}

/* HEARTBEAT */
.heartbeat{
  animation:pulse 1s infinite;
}

@keyframes pulse{
  0%{transform:scale(1);}
  50%{transform:scale(1.02);}
  100%{transform:scale(1);}
}

/* PHOTO (JPG SUPPORT) */
#photo{
  width:180px;
  height:180px;
  border-radius:50%;
  border:4px solid pink;
  margin-top:20px;

  background:url("kanii.jpg"); /* 👈 YOUR JPG FILE */
  background-size:cover;
  background-position:center;

  box-shadow:0 0 30px pink;
  opacity:0;
  transition:2s ease;
}

/* MUSIC */
audio{display:none;}

</style>
</head>

<body>

<!-- STARS -->
<div class="stars" id="stars"></div>

<!-- MUSIC -->
<audio id="music" loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8c8a5d7b7.mp3?filename=romantic-music-ambient-110225.mp3">
</audio>

<!-- INTRO -->
<div id="intro" class="screen center">
  <h1>💖 This is for someone very special 💖</h1>
</div>

<!-- SCREEN 1 -->
<div id="s1" class="screen down">
  <h1>💖 Kanii 💖</h1>
  <p>Write the nickname you call me everyday</p>
  <input id="name" placeholder="type here..." autocomplete="off">
  <button onclick="check()">Unlock</button>
  <p id="err" style="color:red;"></p>
</div>

<!-- SCREEN 2 -->
<div id="s2" class="screen down">
  <h1>Hi Kanii 💕</h1>
  <p>Touch the screen to see your surprise...</p>
</div>

<!-- SCREEN 3 -->
<div id="s3" class="screen down heartbeat">

  <h1 id="loveText">I LOVE YOU MY KANII NUMM NUMM 💖</h1>


  <!-- PHOTO UNDER TEXT -->
  <div id="photo"></div>

</div>

<script>

/* STARS */
const stars=document.getElementById("stars");
for(let i=0;i<80;i++){
  let s=document.createElement("div");
  s.className="star";
  s.style.left=Math.random()*window.innerWidth+"px";
  s.style.top=Math.random()*window.innerHeight+"px";
  stars.appendChild(s);
}

/* SCREENS */
let intro=document.getElementById("intro");
let s1=document.getElementById("s1");
let s2=document.getElementById("s2");
let s3=document.getElementById("s3");

/* MUSIC */
let music=document.getElementById("music");

/* INTRO FLOW */
setTimeout(()=>{
  intro.classList.add("up");
  s1.classList.remove("down");
  s1.classList.add("center");

  music.play().catch(()=>{});
},3000);

/* CHECK NAME */
function check(){
  let val=document.getElementById("name").value;

  if(val==="hamudi"){
    s1.classList.add("up");
    s2.classList.remove("down");
    s2.classList.add("center");
  }else{
    document.getElementById("err").innerText="Wrong nickname 💔";
  }
}

/* TOUCH SCREEN */
s2.addEventListener("click",()=>{
  s2.classList.add("up");
  s3.classList.remove("down");
  s3.classList.add("center");
  startMagic();
});

/* HEARTS */
function heart(){
  let h=document.createElement("div");
  h.className="heart";
  h.innerHTML="💖";
  h.style.left=Math.random()*window.innerWidth+"px";
  h.style.top=window.innerHeight+"px";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),5000);
}

/* FLOWERS */
function flower(){
  let f=document.createElement("div");
  f.className="flower";
  f.innerHTML="🌸";
  f.style.left=Math.random()*window.innerWidth+"px";
  f.style.top=window.innerHeight+"px";
  document.body.appendChild(f);
  setTimeout(()=>f.remove(),5000);
}

/* MAGIC */
function startMagic(){
  setInterval(heart,120);
  setInterval(flower,200);

  setTimeout(()=>{
    document.getElementById("loveText").style.opacity="1";
  },800);

  setTimeout(()=>{
    document.getElementById("photo").style.opacity="1";
  },2000);
}

/* CLICK HEART BURST */
document.body.addEventListener("click",(e)=>{
  for(let i=0;i<5;i++){
    let h=document.createElement("div");
    h.innerHTML="💖";
    h.style.position="absolute";
    h.style.left=e.clientX+"px";
    h.style.top=e.clientY+"px";
    h.style.animation="float 2s linear forwards";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),2000);
  }
});

</script>

</body>
</html>
