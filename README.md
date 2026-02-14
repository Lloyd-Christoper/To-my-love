<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Love 💜</title>

<style>
body {
    margin: 0;
    height: 100vh;
    background: radial-gradient(circle at top, #2a004d, #0f001f);
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    overflow:hidden;
    font-family: Arial, sans-serif;
    color:white;
}

/* Flower */
.flower {
    position: relative;
    width:150px;
    height:150px;
    animation:bloom 2s ease-out forwards;
}

.petal{
    position:absolute;
    width:70px;
    height:70px;
    background:linear-gradient(145deg,#b266ff,#7a00cc);
    border-radius:70px 0;
    transform-origin:bottom right;
    opacity:0;
    animation:fadeIn 1.5s forwards;
}

.p1{transform:rotate(0deg) translate(40px);animation-delay:.2s;}
.p2{transform:rotate(60deg) translate(40px);animation-delay:.4s;}
.p3{transform:rotate(120deg) translate(40px);animation-delay:.6s;}
.p4{transform:rotate(180deg) translate(40px);animation-delay:.8s;}
.p5{transform:rotate(240deg) translate(40px);animation-delay:1s;}
.p6{transform:rotate(300deg) translate(40px);animation-delay:1.2s;}

.center{
    position:absolute;
    width:45px;height:45px;
    background:#ffd966;
    border-radius:50%;
    top:52px;left:52px;
    box-shadow:0 0 15px gold;
}

@keyframes bloom{from{transform:scale(0);}to{transform:scale(1);}}
@keyframes fadeIn{to{opacity:1;}}

/* Sparkles */
.sparkle{
    position:absolute;
    width:6px;height:6px;
    background:white;
    border-radius:50%;
    animation:float 6s linear infinite;
}

@keyframes float{
    from{transform:translateY(100vh);}
    to{transform:translateY(-10vh);opacity:0;}
}

/* Letter */
.letter {
    margin-top:25px;
    width:120px;
    height:80px;
    background:white;
    border-radius:8px;
    position:relative;
    cursor:pointer;
    perspective:600px;
}

/* Fold flap */
.flap{
    position:absolute;
    width:100%;
    height:50%;
    background:#e6ccff;
    top:0;
    transform-origin:top;
    transition:transform .8s;
}

/* Paper content */
.paperInside{
    position:absolute;
    inset:0;
    display:flex;
    justify-content:center;
    align-items:center;
    color:#5a0099;
    font-weight:bold;
    padding:10px;
    text-align:center;
    opacity:0;
    transition:opacity .8s .4s;
}

/* Open state */
.letter.open .flap{
    transform:rotateX(-180deg);
}

.letter.open .paperInside{
    opacity:1;
}

/* Hearts */
.heart{
    position:absolute;
    font-size:18px;
    animation:explode 1s forwards;
}

@keyframes explode{
    from{
        transform:translate(0,0) scale(0.5);
        opacity:1;
    }
    to{
        transform:translate(var(--x), var(--y)) scale(1.5);
        opacity:0;
    }
}
</style>
</head>

<body>

<div class="flower">
<div class="petal p1"></div>
<div class="petal p2"></div>
<div class="petal p3"></div>
<div class="petal p4"></div>
<div class="petal p5"></div>
<div class="petal p6"></div>
<div class="center"></div>
</div>

<div class="letter" onclick="openLetter(this)">
    <div class="flap"></div>
    <div class="paperInside">
        Happy Valentines Day,<br>
        Myloveee,<br>
        Iloveyouu 💜
    </div>
</div>

<script>
/* Sparkles */
for(let i=0;i<25;i++){
 let s=document.createElement("div");
 s.className="sparkle";
 s.style.left=Math.random()*100+"vw";
 s.style.animationDuration=(3+Math.random()*4)+"s";
 document.body.appendChild(s);
}

/* Open letter + hearts explode */
function openLetter(el){
    el.classList.add("open");

    for(let i=0;i<20;i++){
        let h=document.createElement("div");
        h.className="heart";
        h.innerHTML="💜";
        h.style.left=el.offsetLeft+60+"px";
        h.style.top=el.offsetTop+40+"px";

        let x=(Math.random()-0.5)*300+"px";
        let y=(Math.random()-0.5)*300+"px";
        h.style.setProperty("--x",x);
        h.style.setProperty("--y",y);

        document.body.appendChild(h);
        setTimeout(()=>h.remove(),1000);
    }
}
</script>

</body>
</html>
