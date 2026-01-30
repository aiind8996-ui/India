<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>............ App</title>

<style>
:root{ --accent:#ff9933; }

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  user-select:none;
}

body{
  font-family:system-ui,Arial;
  height:100vh;
  overflow:hidden;
  background:black;
  color:white;
}

/* ===== COMMON ===== */
.page{
  position:absolute;
  inset:0;
  display:none;
  text-align:center;
}
.page.active{display:block;}

.top{
  position:fixed;
  top:0; left:0;
  width:100%;
  height:60px;
  line-height:60px;
  font-size:22px;
  font-weight:600;
  color:var(--accent);
  background:black;
  z-index:20;
  animation:floatText 3s ease-in-out infinite alternate;
}

@keyframes floatText{
  from{transform:translateY(0)}
  to{transform:translateY(-8px)}
}

.settings{
  position:fixed;
  top:15px;
  right:10px;
  font-size:24px;
  z-index:30;
  cursor:pointer;
}

.back{
  position:fixed;
  top:15px;
  left:15px;
  font-size:26px;
  z-index:30;
  cursor:pointer;
}

/* ===== MENU (SIDE FIXED) ===== */
.menu{
  position:fixed;
  top:65px;
  right:0;
  width:200px;
  background:#0e0e0e;
  border-left:2px solid var(--accent);
  display:none;
  z-index:50;
  animation:slideIn .3s ease;
}
@keyframes slideIn{
  from{transform:translateX(100%)}
  to{transform:translateX(0)}
}

.menu div{
  padding:14px;
  border-bottom:1px solid #222;
  font-size:14px;
  cursor:pointer;
}
.menu div:hover{
  background:var(--accent);
  color:black;
}

/* ===== PAGE 1 ===== */
#page1{
  background:linear-gradient(45deg,#ff9933,#ffcc33,#ff6600,#ffaa00);
  background-size:400% 400%;
  animation:homeBG 18s ease infinite;
}
@keyframes homeBG{
  0%{background-position:0% 50%}
  50%{background-position:100% 50%}
  100%{background-position:0% 50%}
}

.main-btn{
  margin-top:140px;
  padding:18px 55px;
  font-size:22px;
  border-radius:12px;
  border:2px solid var(--accent);
  background:#111;
  color:white;
  cursor:pointer;
  animation:pulse 2s infinite;
}
@keyframes pulse{
  0%{box-shadow:0 0 10px var(--accent)}
  50%{box-shadow:0 0 28px var(--accent)}
  100%{box-shadow:0 0 10px var(--accent)}
}

/* OPEN TRANSITION */
.fadeOut{
  animation:fadeOut .6s forwards;
}
@keyframes fadeOut{
  to{opacity:0;transform:scale(1.2)}
}

/* ===== PAGE 2 ===== */
#page2{
  background:radial-gradient(circle at top,#00ffcc,#001010,#000);
  animation:dangerBG 10s linear infinite;
  padding-top:90px;
}
@keyframes dangerBG{
  0%{filter:hue-rotate(0deg)}
  100%{filter:hue-rotate(360deg)}
}

.card{
  margin:16px auto;
  width:85%;
  max-width:320px;
  padding:16px;
  border-radius:14px;
  background:#111;
  border:1px solid var(--accent);
  font-size:18px;
  color:#00ffcc;
  cursor:pointer;
  transition:.3s;
}
.card:hover{
  background:var(--accent);
  color:black;
  transform:scale(1.08);
}

.chat-box{
  display:flex;
  gap:12px;
  width:85%;
  max-width:320px;
  margin:10px auto;
}
.chat-btn{
  flex:1;
  padding:14px;
  border-radius:14px;
  background:#0f0f0f;
  border:1px solid var(--accent);
  color:#25D366;
  text-decoration:none;
  transition:.3s;
}
.chat-btn:hover{
  background:var(--accent);
  color:black;
}
</style>
</head>

<body>

<!-- MENU -->
<div class="menu" id="menu">
  <div onclick="fullscreen()">🔲 Full Screen</div>
  <div onclick="theme('#ff9933')">🎨 Saffron</div>
  <div onclick="theme('#00ffcc')">🎨 Cyan</div>
  <div onclick="theme('#00ff00')">🎨 Green</div>
  <div onclick="theme('#ff00ff')">🎨 Pink</div>
</div>

<!-- PAGE 1 -->
<div class="page active" id="page1">
  <div class="top">..........</div>
  <div class="settings" onclick="toggleMenu()">⚙️</div>
  <button class="main-btn" onclick="openPage()">OPEN</button>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
  <div class="back" onclick="goBack()">←</div>
  <div class="settings" onclick="toggleMenu()">⚙️</div>
  <div class="top">......</div>

  <div class="card" onclick="openYouTube()">▶️ YouTube</div>
  <div class="card" onclick="openLink('https://aiind8996-ui.github.io/documents.-upload-/')">📄 PDF Upload</div>
  <div class="card" onclick="openLink('https://aiind8996-ui.github.io/Photo-uplod-/')">🖼️ Photo Upload</div>
  <div class="card" onclick="openLink('https://aiind8996-ui.github.io/-/')">🔗 CC</div>

  <div class="card">💬 Chat</div>
  <div class="chat-box">
    <a class="chat-btn" href="https://wa.me/917007576493" target="_blank">💚 Chat</a>
    <a class="chat-btn" href="https://wa.me/917007576493" target="_blank">💚 Chat</a>
  </div>
</div>

<script>
const page1=document.getElementById("page1");
const page2=document.getElementById("page2");
const menu=document.getElementById("menu");

function openPage(){
  page1.classList.add("fadeOut");
  setTimeout(()=>{
    page1.classList.remove("active","fadeOut");
    page2.classList.add("active");
  },600);
  menu.style.display="none";
}

function goBack(){
  page2.classList.remove("active");
  page1.classList.add("active");
  menu.style.display="none";
}

function toggleMenu(){
  menu.style.display = menu.style.display==="block"?"none":"block";
}

function fullscreen(){
  if(!document.fullscreenElement){
    document.documentElement.requestFullscreen();
  }else{
    document.exitFullscreen();
  }
}

function theme(color){
  document.documentElement.style.setProperty('--accent',color);
}

function openYouTube(){
  window.open("https://aiind8996-ui.github.io/YouTube-/","_blank","noopener");
}

function openLink(url){
  window.open(url,"_blank","noopener");
}

document.addEventListener("contextmenu",e=>e.preventDefault());
</script>

</body>
</html>
