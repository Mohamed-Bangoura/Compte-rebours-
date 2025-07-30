<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Compte à rebours 🎂</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@400;600&display=swap');
    body {
      margin:0; padding:0;
      height:100vh;
      display:flex; flex-direction:column;
      align-items:center; justify-content:center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family:'Poppins',sans-serif;
      text-align:center; color:#fff;
      overflow:hidden;
    }
    h1{font-family:'Pacifico'; font-size:3rem; margin-bottom:1rem; text-shadow:2px 2px 10px rgba(0,0,0,0.3);}
    .countdown {display:flex; gap:15px; font-size:2rem; font-weight:600;}
    .box {background:rgba(255,255,255,0.2); padding:15px; border-radius:12px; min-width:70px;}
    .label {display:block; font-size:1rem; margin-top:5px;}
    .confetti, .balloon {pointer-events:none; position:absolute;}
    .confetti {animation:fall 5s linear infinite;}
    @keyframes fall {0%{transform: translateY(-50px);}100%{transform: translateY(110vh);}}
  </style>
</head>
<body>
  <h1>🎉 Ton anniversaire approche !</h1>
  <div class="countdown">
    <div class="box"><span id="days">00</span><span class="label">Jours</span></div>
    <div class="box"><span id="hours">00</span><span class="label">Heures</span></div>
    <div class="box"><span id="minutes">00</span><span class="label">Minutes</span></div>
    <div class="box"><span id="seconds">00</span><span class="label">Secondes</span></div>
  </div>
  <script>
    const target = new Date(new Date().getFullYear(),6,31,0,0,0).getTime();
    function upd(){
      const now=Date.now(), d=target-now;
      if(d<=0){
        document.body.innerHTML='<h1>🎂 Joyeux anniversaire ! 🎈</h1>';
        return;
      }
      const days=Math.floor(d/86400000),
            hrs=Math.floor((d%86400000)/3600000),
            mins=Math.floor((d%3600000)/60000),
            secs=Math.floor((d%60000)/1000);
      document.getElementById('days').textContent=days;
      document.getElementById('hours').textContent=hrs.toString().padStart(2,'0');
      document.getElementById('minutes').textContent=mins.toString().padStart(2,'0');
      document.getElementById('seconds').textContent=secs.toString().padStart(2,'0');
    }
    setInterval(upd,1000); upd();
    // Confettis & ballons
    for(let i=0;i<80;i++){
      const c=document.createElement('div');
      c.className='confetti';
      c.style.left=Math.random()*100+'vw';
      c.style.width=c.style.height='8px';
      c.style.background=['#ffc','lightblue','pink','#9f9'][i%4];
      c.style.opacity=Math.random();
      c.style.animationDuration=2+Math.random()*3+'s';
      document.body.append(c);
    }
  </script>
</body>
</html>
