
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>hvd 2ll</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital@1&family=Quicksand:wght@400;600&display=swap');

*{box-sizing:border-box;margin:0;padding:0;}

body{
  background:#ffffff;
  font-family:'Quicksand',sans-serif;
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  overflow:hidden;
  color:#222;
  /* Soft paper texture background */
  background-image: url('https://www.transparenttextures.com/patterns/paper-fibers.png');
  background-repeat: repeat;
  background-size: auto;
}

.container{
  width:100%;
  max-width:420px;
  padding:15px;
  text-align:center;
}

h1{
  margin-bottom:12px;
  font-weight:600;
  letter-spacing:2px;
}

/* VINYL */
.vinyl-wrap{
  width:200px;
  height:200px;
  margin:15px auto;
  border-radius:50%;
  background:radial-gradient(circle,#000 30%,#111 45%,#222 70%,#000 100%);
  display:flex;
  justify-content:center;
  align-items:center;
  animation:spin 6s linear infinite;
  box-shadow:0 0 25px rgba(0,0,0,.25);
}

.vinyl-wrap img{
  width:70px;
  height:70px;
  border-radius:50%;
  object-fit:cover;
  border:2px solid white;
}

@keyframes spin{
  from{transform:rotate(0deg);}
  to{transform:rotate(360deg);}
}

/* LETTER BUTTON */
.open-btn{
  padding:10px 22px;
  background:#ff6f91;
  border:none;
  border-radius:20px;
  color:white;
  font-size:15px;
  cursor:pointer;
  transition:.3s;
}

.open-btn:hover{
  background:#ff4d6d;
}

/* LETTER CARD */
.letter{
  position:fixed;
  inset:0;
  background:rgba(255,255,255,.85);
  display:flex;
  justify-content:center;
  align-items:center;
  opacity:0;
  pointer-events:none;
  transition:.4s;
}

.letter.active{
  opacity:1;
  pointer-events:auto;
}

.letter-card{
  background:#fff;
  color:#333;
  width:92%;
  max-width:420px;
  max-height:75vh;
  border-radius:15px;
  padding:20px 18px 30px;
  box-shadow:0 0 30px rgba(0,0,0,.12);
  overflow-y:auto;
  font-family:'Playfair Display',serif;
  position:relative;
  animation:fadeUp .6s ease;
}

@keyframes fadeUp{
  from{opacity:0; transform:translateY(20px);}
  to{opacity:1; transform:translateY(0);}
}

.close-x{
  position:absolute;
  top:10px;
  right:14px;
  font-size:22px;
  cursor:pointer;
  color:#aaa;
}

.close-x:hover{color:#000}

#typedText{
  font-size:17px;
  line-height:1.7;
  white-space:pre-wrap;
}

/* FLOATING HEARTS */
.heart{
  position:fixed;
  color:#ff6f91;
  font-size:18px;
  animation:floatUp 6s linear infinite;
  opacity:.6;
}

@keyframes floatUp{
  from{transform:translateY(100vh) scale(1);}
  to{transform:translateY(-10vh) scale(1.5); opacity:0;}
}

/* MOBILE */
@media(max-width:480px){
  .vinyl-wrap{width:160px;height:160px}
  h1{font-size:20px}
  #typedText{font-size:16px}
}

</style>
</head>

<body>

<div class="container">
  <h1>hvd 2ll</h1>

  <div class="vinyl-wrap">
    <img src="https://lastfm.freetls.fastly.net/i/u/ar0/99ca8d89a4b625905e1cfe4fc279162d.jpg">
  </div>

  <iframe style="border-radius:12px" src="https://open.spotify.com/embed/track/1lORkxEMmsCZqhoxcmk3A3?utm_source=generator" width="100%" height="80" frameBorder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>

  <br><br>
  <button class="open-btn" onclick="openLetter()">Open Letter</button>
</div>

<div class="letter" id="letter">
  <div class="letter-card">
    <div class="close-x" onclick="closeLetter()">×</div>
    <div id="typedText"></div>
  </div>
</div>

<script>
const text = `Ginamos, Bagnet, Pritong Talong, Fried Banana...

Happy Heart's Day, Josh!!
Bayad ko na 'to sa binigay mo sa akin hahahahaha i hope you'll like it!`;

let index = 0;
let typing;

function openLetter(){
  document.getElementById("letter").classList.add("active");
  document.getElementById("typedText").innerHTML = "";
  index = 0;
  typing = setInterval(typeEffect, 40);
}

function closeLetter(){
  document.getElementById("letter").classList.remove("active");
  clearInterval(typing);
}

function typeEffect(){
  if(index < text.length){
    document.getElementById("typedText").innerHTML += text.charAt(index);
    index++;
    document.querySelector(".letter-card").scrollTop = document.querySelector(".letter-card").scrollHeight;
  } else {
    clearInterval(typing);
  }
}

/* FLOATING HEARTS */
function createHeart(){
  const heart = document.createElement("div");
  heart.className="heart";
  heart.innerHTML="♥";
  heart.style.left=Math.random()*100+"vw";
  heart.style.animationDuration=(Math.random()*3+4)+"s";
  document.body.appendChild(heart);

  setTimeout(()=>heart.remove(),6000);
}

setInterval(createHeart,400);
</script>

</body>
