
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>What Echoes Within My Heart</title>

<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Allura&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;margin:0;padding:0}

body{
    min-height:100vh;
    background:#fff;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
    font-family:'Allura',cursive;
}

/* Soft glow */
.flicker{
    position:fixed;
    inset:0;
    pointer-events:none;
    box-shadow:0 0 120px 35px rgba(255,200,220,0.2) inset;
    animation:flickerGlow 2s infinite alternate;
}

@keyframes flickerGlow{
    0%{box-shadow:0 0 120px 35px rgba(255,200,220,0.2) inset;}
    50%{box-shadow:0 0 130px 40px rgba(255,180,200,0.25) inset;}
    100%{box-shadow:0 0 110px 30px rgba(255,200,220,0.15) inset;}
}

/* Floating hearts */
.heart{
    position:absolute;
    width:16px;
    height:16px;
    background:red;
    transform:rotate(45deg);
    border-radius:0 50% 50% 50%;
    animation:floatHeart linear infinite;
}
.heart::before,.heart::after{
    content:"";
    position:absolute;
    width:16px;
    height:16px;
    background:red;
    border-radius:50%;
}
.heart::before{top:-8px;left:0;}
.heart::after{left:-8px;top:0;}

@keyframes floatHeart{
    0%{transform:translateY(0) rotate(45deg);opacity:1;}
    100%{transform:translateY(-700px) rotate(45deg);opacity:0;}
}

/* Envelope */
.envelope{
    width:90%;
    max-width:460px;
    height:300px;
    position:relative;
    cursor:pointer;
    animation:float 4s ease-in-out infinite;
}

@keyframes float{
    0%,100%{transform:translateY(0)}
    50%{transform:translateY(-10px)}
}

.env-body{
    position:absolute;
    inset:0;
    background:linear-gradient(145deg,#f9f1e6,#e7d7c3);
    border-radius:16px;
    box-shadow:0 35px 90px rgba(0,0,0,.3), inset 0 0 60px rgba(255,255,255,.7);
}

.env-body::before{
    content:"";
    position:absolute;
    inset:16px;
    border:6px double rgba(255,255,255,.9);
    border-radius:12px;
}

.flap{
    position:absolute;
    inset:0;
    background:linear-gradient(145deg,#f3e7d5,#d8c2aa);
    clip-path:polygon(0 0,50% 58%,100% 0);
    border-radius:16px 16px 0 0;
    transform-origin:top;
    transition:1.2s cubic-bezier(.19,1,.22,1);
}

.seal{
    width:60px;
    height:60px;
    background:radial-gradient(circle,#a1121f,#5c000b);
    border-radius:50%;
    position:absolute;
    bottom:18px;
    left:50%;
    transform:translateX(-50%);
    box-shadow:0 8px 25px rgba(0,0,0,.5);
}

.seal::after{
    content:"❤";
    position:absolute;
    inset:0;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:26px;
    color:#ffd9df;
}

.env-text{
    position:absolute;
    top:18px;
    width:100%;
    text-align:center;
    font-family:'Great Vibes',cursive;
    font-size:32px;
    color:#6a3a2a;
}

/* Music + Vinyl */
.music-box{
    display:none;
    position:fixed;
    inset:0;
    background:rgba(255,255,255,.97);
    justify-content:center;
    align-items:center;
    flex-direction:column;
    gap:18px;
    padding:20px;
}

.album-bg{
    width:250px;
    height:250px;
    background:#111;
    border-radius:14px;
    display:flex;
    justify-content:center;
    align-items:center;
    box-shadow:0 25px 70px rgba(0,0,0,.45);
}

.vinyl{
    width:180px;
    height:180px;
    border-radius:50%;
    background:radial-gradient(circle,#000 0%,#111 45%,#000 70%,#222 100%);
    animation:spin 3s linear infinite;
    animation-play-state:paused;
    position:relative;
}

/* YOUR ALBUM ART */
.vinyl::before{
    content:"";
    position:absolute;
    inset:40px;
    background:url('https://lastfm.freetls.fastly.net/i/u/ar0/99ca8d89a4b625905e1cfe4fc279162d.jpg') center/cover no-repeat;
    border-radius:50%;
}

.vinyl::after{
    content:"";
    width:12px;
    height:12px;
    background:white;
    border-radius:50%;
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
}

@keyframes spin{
    from{transform:rotate(0deg)}
    to{transform:rotate(360deg)}
}

/* Letter Card */
.letter{
    display:none;
    width:92%;
    max-width:700px;
    background:linear-gradient(135deg,#fff,#fffaf4);
    padding:40px;
    border-radius:18px;
    box-shadow:0 30px 80px rgba(0,0,0,.25);
    font-size:22px;
    line-height:1.9;
    overflow-y:auto;
    max-height:75vh;
    position:relative;
}

.letter.show{
    display:block;
    animation:fadeUp 1s ease forwards;
}

@keyframes fadeUp{
    from{transform:translateY(20px);opacity:0}
    to{transform:none;opacity:1}
}

.title{
    font-family:'Great Vibes',cursive;
    font-size:48px;
    text-align:center;
    color:#d6336c;
    margin-bottom:25px;
}

.click-card{
    background:#ffe3e6;
    border-radius:18px;
    padding:12px 24px;
    font-family:'Great Vibes',cursive;
    font-size:22px;
    color:#d6336c;
    box-shadow:0 10px 25px rgba(0,0,0,.2);
    cursor:pointer;
    transition:.3s;
}

.click-card:hover{transform:scale(1.07)}
</style>
</head>

<body>

<div class="flicker"></div>

<script>
for(let i=0;i<25;i++){
    let h=document.createElement("div");
    h.className="heart";
    h.style.left=Math.random()*100+"%";
    h.style.animationDuration=5+Math.random()*3+"s";
    h.style.animationDelay=Math.random()*5+"s";
    document.body.appendChild(h);
}
</script>

<div class="envelope" onclick="openEnvelope()">
    <div class="env-body"></div>
    <div class="flap" id="flap"></div>
    <div class="env-text">What Echoes Within My Heart</div>
    <div class="seal" id="seal"></div>
</div>

<div class="music-box" id="musicBox">
    <div class="album-bg">
        <div class="vinyl" id="vinyl"></div>
    </div>

    <div class="click-card" onclick="showLetter()">Open Letter</div>

    <iframe 
        src="https://open.spotify.com/embed/track/1lORkxEMmsCZqhoxcmk3A3?utm_source=generator&autoplay=1"
        width="300" height="80"
        frameborder="0"
        allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
        style="border-radius:12px;">
    </iframe>
</div>

<div class="letter" id="letter">
    <div class="title">What Echoes Within My Heart</div>
    <p id="typewriter"></p>
</div>

<script>
const letterText = `Ginamos,  Bagnet,  Pritong Talong,  Fried Banana…

Happy Heart's Day, Josh!!  

Bayad ko na 'to sa binigay mo sksksksk

I hope I made your day, today! love u`;

function typeWriter(text,i=0){
    if(i<text.length){
        document.getElementById("typewriter").innerHTML += text.charAt(i);
        document.getElementById("letter").scrollTop = document.getElementById("letter").scrollHeight;
        setTimeout(()=>typeWriter(text,i+1),80);
    }
}

function openEnvelope(){
    document.getElementById('flap').style.transform="rotateX(180deg)";
    document.getElementById('seal').style.display='none';
    setTimeout(()=>{
        document.querySelector('.envelope').style.display="none";
        document.getElementById('musicBox').style.display="flex";
        document.getElementById('vinyl').style.animationPlayState="running";
    },1200);
}

function showLetter(){
    const letter = document.getElementById('letter');
    letter.classList.add('show');
    document.getElementById("typewriter").innerHTML="";
    typeWriter(letterText);
}
</script>

</body>
