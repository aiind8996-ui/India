<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Jai Shree Ram App</title>

<style>
:root{ --accent:#ff9933; }

*{
  box-sizing:border-box;
  -webkit-user-select:none;
  user-select:none;
  -webkit-touch-callout:none;
}

body{
  margin:0;
  background:black;
  color:white;
  font-family:system-ui, Arial;
  height:100vh;
  overflow:hidden;
}

/* ================= PAGE ================= */
.page{
  display:none;
  height:100vh;
  width:100%;
  text-align:center;
  padding-top:90px;
  position:relative;
}
.page.active{display:block;}

/* ================= TOP BAR ================= */
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
  z-index:10;
}

/* ================= ICONS ================= */
.back{
  position:fixed;
  top:15px; left:15px;
  font-size:26px;
  z-index:11;
}
.settings{
  position:fixed;
  top:15px; right:15px;
  font-size:24px;
  z-index:11;
}

/* ================= SETTINGS MENU ================= */
.menu{
  position:fixed;
  top:65px; right:15px;
  background:#111;
  border:1px solid var(--accent);
  border-radius:10px;
  padding:8px;
  width:210px;
  display:none;
  z-index:50;
}
.menu div{
  padding:10px;
  font-size:14px;
  border-bottom:1px solid #222;
}
.menu div:last-child{border:none;}
.menu div:hover{background:#1c1c1c;}

/* ================= BUTTONS ================= */
.main-btn{
  margin-top:100px;
  padding:16px 45px;
  font-size:20px;
  border-radius:10px;
  border:2px solid var(--accent);
  background:#111;
  color:white;
}

/* ================= CARDS ================= */
.card{
  margin:16px auto;
  width:85%;
  max-width:320px;
  padding:15px;
  border-radius:12px;
  background:#111;
  border:1px solid var(--accent);
  color:#00ffcc;
  font-size:18px;
  text-decoration:none;
  display:block;
}

/* ================= CHAT ================= */
.chat-box{
  width:85%;
  max-width:320px;
  margin:10px auto;
  display:flex;
  gap:12px;
}
.chat-btn{
  flex:1;
  padding:14px;
  background:#0f0f0f;
  border:1px solid var(--accent);
  border-radius:12px;
  font-size:16px;
  color:#25D366;
  text-decoration:none;
}

/* =================================================
   🔱 HOME PAGE BEAUTIFUL ANIMATION 🔱
================================================= */

/* Animated Light Background */
#page1::before{
  content:"";
  position:absolute;
  inset:0;
  background:
    radial-gradient(circle at 20% 30%, rgba(255,153,51,0.18), transparent 40%),
    radial-gradient(circle at 80% 70%, rgba(255,204,102,0.15), transparent 40%);
  animation:bgMove 8s linear infinite;
  z-index:-1;
}

@keyframes bgMove{
  0%{background-position:0% 0%,100% 100%;}
  100%{background-position:100% 100%,0% 0%;}
}

/* Jai Shree Ram Glow */
#page1 .top{
  animation:ramGlow 2.5s ease-in-out infinite;
}

@keyframes ramGlow{
  0%,100%{
    text-shadow:0 0 6px var(--accent),
                0 0 12px var(--accent);
  }
  50%{
    text-shadow:0 0 14px var(--accent),
                0 0 28px var(--accent);
  }
}

/* OPEN Button Entry + Pulse */
#page1 .main-btn{
  opacity:0;
  animation:btnEntry 1s ease forwards, pulse 2s ease-in-out infinite;
}

@keyframes btnEntry{
  from{transform:scale(0.6);opacity:0;}
  to{transform:scale(1);opacity:1;}
}

@keyframes pulse{
  0%{box-shadow:0 0 0 0 rgba(255,153,51,0.6);}
  70%{box-shadow:0 0 0 18px rgba(255,153,51,0);}
  100%{box-shadow:0 0 0 0 rgba(255,153,51,0);}
}
</style>
</head>

<body>

<!-- SETTINGS MENU -->
<div class="menu" id="menu">
  <div onclick="fullscreen()">🔲 Full Screen</div>
  <div onclick="theme('#ff9933')">🎨 Saffron</div>
  <div onclick="theme('#00ffcc')">🎨 Cyan</div>
  <div onclick="theme('#00ff00')">🎨 Green</div>
  <div onclick="theme('#ff00ff')">🎨 Pink</div>
  <div onclick="theme('#ffffff')">🎨 White</div>
  <div onclick="lang()">🌐 Language</div>
  <div onclick="share()">📤 Send App</div>
</div>

<!-- PAGE 1 -->
<div class="page active" id="page1">
  <div class="top">🚩 Jai Shree Ram 🚩</div>
  <div class="settings" onclick="toggleMenu()">⚙️</div>
  <button class="main-btn" onclick="openPage()">OPEN</button>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2">
  <div class="back" onclick="goBack()">←</div>
  <div class="settings" onclick="toggleMenu()">⚙️</div>
  <div class="top">🚩 Jai Shree Ram 🚩</div>

  <a class="card" href="https://aiind8996-ui.github.io/documents.-upload-/" target="_blank">📄 PDF Upload</a>
  <a class="card" href="https://aiind8996-ui.github.io/-/" target="_blank">🔗 CC</a>

  <div class="card">💬 Chat</div>
  <div class="chat-box">
    <a class="chat-btn" href="https://wa.me/916392908732" target="_blank">💚 Chat</a>
    <a class="chat-btn" href="https://wa.me/917800049619" target="_blank">💚 Chat</a>
  </div>
</div>

<script>
const page1=document.getElementById("page1");
const page2=document.getElementById("page2");
const menu=document.getElementById("menu");

function openPage(){
  page1.classList.remove("active");
  page2.classList.add("active");
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
function lang(){ alert("Language option demo"); }
function share(){
  if(navigator.share){
    navigator.share({title:"Jai Shree Ram App",url:location.href});
  }
}

/* 🔒 GOOGLE / TOUCH LOCK */
document.addEventListener("contextmenu",e=>e.preventDefault());
document.addEventListener("selectstart",e=>e.preventDefault());
document.addEventListener("copy",e=>e.preventDefault());
document.addEventListener("cut",e=>e.preventDefault());
document.addEventListener("paste",e=>e.preventDefault());
document.addEventListener("dragstart",e=>e.preventDefault());
</script>

</body>
</html>
