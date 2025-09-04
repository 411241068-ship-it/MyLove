<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>I Love You — Ratu Dinda Azhar Afifah</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600;800&display=swap" rel="stylesheet">
<style>
  :root{
    --bg1:#ffdee9; /* pink muda */
    --bg2:#b5fffc; /* biru muda */
    --ink:#2b2b2b;
    --white:#fff;
    --accent:#ff3b7a;
    --accent-dark:#e13068;
    --glass: rgba(255,255,255,.6);
  }
  *{box-sizing:border-box}
  html,body{
    height:100%;
    margin:0;
    font-family:'Poppins', system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
    color:var(--ink);
    background: radial-gradient(1200px 900px at 80% -10%, #ffd5e4 0%, transparent 60%),
                linear-gradient(135deg, var(--bg1), var(--bg2));
    overflow:hidden;
  }

  /* Container */
  .app{
    position:relative;
    height:100%;
    width:100%;
  }

  /* Floating soft hearts background */
  .floaters{
    position:absolute; inset:0;
    pointer-events:none;
    overflow:hidden;
    z-index:0;
  }
  .floater{
    position:absolute;
    font-size:clamp(14px, 3vw, 26px);
    opacity:.18;
    animation: rise linear infinite;
    will-change: transform, opacity;
    filter: drop-shadow(0 4px 8px rgba(0,0,0,.08));
  }
  @keyframes rise{
    from{ transform: translateY(110vh) rotate(0deg) scale(.8); }
    to  { transform: translateY(-15vh) rotate(360deg) scale(1.15); }
  }

  /* Slides */
  .slides{
    position:relative;
    height:100%;
    display:grid;
    place-items:center;
    overflow:hidden;
    z-index:1;
  }
  .slide{
    position:absolute; inset:0;
    display:grid; place-items:center;
    padding:32px;
    opacity:0;
    transform: translateY(20px) scale(.98);
    transition: opacity .6s ease, transform .6s cubic-bezier(.2,.8,.2,1);
    pointer-events:none;
  }
  .slide.active{
    opacity:1;
    transform: translateY(0) scale(1);
    pointer-events:auto;
  }

  /* Card */
  .card{
    background: linear-gradient(180deg, rgba(255,255,255,.75), rgba(255,255,255,.5));
    border:1px solid rgba(255,255,255,.55);
    box-shadow: 0 10px 30px rgba(255,59,122,.18), 0 4px 12px rgba(0,0,0,.06);
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    border-radius: 28px;
    padding: clamp(28px, 5vw, 56px);
    text-align:center;
    max-width: 780px;
  }
  .title{
    font-weight:800;
    letter-spacing:.5px;
    font-size: clamp(34px, 7vw, 72px);
    line-height:1.1;
    margin: 0 0 18px;
    background: linear-gradient(90deg, #ff005d, #ff7aa2, #ff005d);
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
  }
  .subtitle{
    font-weight:300;
    font-size: clamp(14px, 2.5vw, 18px);
    margin:0 0 24px;
    opacity:.8;
  }

  /* Heart button */
  .heart-btn{
    position:relative;
    display:inline-grid;
    place-items:center;
    width:90px; height:90px;
    border:none;
    background:transparent;
    cursor:pointer;
    transition: transform .2s ease;
    outline-offset: 6px;
  }
  .heart-btn:active{ transform: scale(.96); }

  /* Heart shape */
  .heart{
    position:relative;
    width:64px; height:64px;
    transform: rotate(-45deg);
    background: var(--accent);
    border-radius: 16px 0 0 16px;
    box-shadow: 0 8px 20px rgba(255,59,122,.35), inset 0 -4px 10px rgba(0,0,0,.08);
  }
  .heart::before, .heart::after{
    content:"";
    position:absolute;
    width:64px; height:64px;
    background: var(--accent);
    border-radius:50%;
    box-shadow: inset 0 -4px 10px rgba(0,0,0,.08);
  }
  .heart::before{ top:-32px; left:0; }
  .heart::after { left:32px; top:0; }

  /* pulsing */
  .heart-pulse{
    animation: pulse 1.2s ease-in-out infinite;
  }
  @keyframes pulse{
    0%,100%{ transform: rotate(-45deg) scale(1); }
    50%    { transform: rotate(-45deg) scale(1.08); }
  }

  /* Sparkles on click */
  .burst{
    position:absolute; inset:0; display:grid; place-items:center; pointer-events:none;
  }
  .dot{
    position:absolute; width:10px; height:10px; border-radius:50%;
    background: var(--accent);
    transform: translate(-50%,-50%);
    animation: pop .8s ease forwards;
  }
  @keyframes pop{
    from{ opacity:1; transform: translate(-50%,-50%) scale(1); }
    to  { opacity:0; transform: translate(var(--x), var(--y)) scale(0); }
  }

  /* Next slide message */
  .love-line{
    font-weight:800;
    font-size: clamp(30px, 6.5vw, 64px);
    line-height:1.15;
    margin:0 0 10px;
    color:#ff236f;
    text-shadow: 0 6px 24px rgba(255,35,111,.18);
  }
  .name{
    font-weight:600;
    font-size: clamp(18px, 3.5vw, 28px);
    margin:0;
    opacity:.9;
  }

  /* Footer note */
  .note{
    margin-top:20px;
    font-size:12px;
    opacity:.6;
  }

  /* Small helper link */
  .back{
    margin-top:24px;
    display:inline-block;
    font-size:14px;
    padding:10px 14px;
    border-radius: 999px;
    background: rgba(255,255,255,.65);
    border:1px solid rgba(0,0,0,.06);
    text-decoration:none;
    color:#e73376;
    transition: transform .2s ease, background .2s ease;
  }
  .back:hover{ transform: translateY(-1px); background: rgba(255,255,255,.85); }

  /* Accessibility focus */
  .heart-btn:focus-visible{
    outline: 3px dashed rgba(255,59,122,.6);
  }

  /* Responsive tweak */
  @media (max-width:420px){
    .heart-btn{ width:78px; height:78px; }
    .heart, .heart::before, .heart::after{ width:54px; height:54px; }
    .heart::before{ top:-27px; }
    .heart::after { left:27px; }
  }
</style>
</head>
<body>
  <div class="app" role="application" aria-label="Love Slides">
    <!-- Decorative floating hearts -->
    <div class="floaters" aria-hidden="true" id="floaters"></div>

    <main class="slides">
      <!-- Slide 1 -->
      <section class="slide active" id="slide-1" aria-labelledby="title-1">
        <div class="card">
          <h1 class="title" id="title-1">Klik Hati ku sayang</h1>
          <p class="subtitle">Klik hati di bawah untuk lanjut ➜</p>

          <button class="heart-btn" id="go-next" aria-label="Lanjut ke slide berikutnya">
            <div class="heart heart-pulse" aria-hidden="true"></div>
            <div class="burst" aria-hidden="true" id="burst"></div>
          </button>

          <div class="note">Dibuat dengan ❤</div>
        </div>
      </section>

      <!-- Slide 2 -->
      <section class="slide" id="slide-2" aria-live="polite" aria-labelledby="title-2">
        <div class="card">
          <h2 class="love-line" id="title-2">I love You</h2>
          <p class="name">Ratu Dinda Azhar Afifah</p>
          <a href="#" class="back" id="go-back" title="Kembali ke awal">Kembali</a>
        </div>
      </section>
    </main>
  </div>

<script>
  // Simple slideshow logic
  const s1 = document.getElementById('slide-1');
  const s2 = document.getElementById('slide-2');
  const goNext = document.getElementById('go-next');
  const goBack = document.getElementById('go-back');
  const burst = document.getElementById('burst');
  const floaters = document.getElementById('floaters');

  function showSlide(slide){
    [s1, s2].forEach(el => el.classList.remove('active'));
    slide.classList.add('active');
  }

  // Heart confetti burst
  function burstHearts(x,y){
    burst.innerHTML = '';
    const pieces = 14;
    for(let i=0;i<pieces;i++){
      const dot = document.createElement('div');
      dot.className = 'dot';
      const angle = (Math.PI * 2 / pieces) * i;
      const dist = 80 + Math.random()*40;
      dot.style.setProperty('--x', `${Math.cos(angle)*dist}px`);
      dot.style.setProperty('--y', `${Math.sin(angle)*dist}px`);
      burst.appendChild(dot);
    }
  }

  // Floating background hearts
  function spawnFloaters(){
    const count = 24;
    const symbols = ['❤','♡','❥','♥'];
    for(let i=0;i<count;i++){
      const h = document.createElement('div');
      h.className = 'floater';
      h.textContent = symbols[Math.floor(Math.random()*symbols.length)];
      h.style.left = `${Math.random()*100}%`;
      h.style.animationDuration = `${14 + Math.random()*12}s`;
      h.style.animationDelay = `${-Math.random()*20}s`;
      h.style.opacity = 0.08 + Math.random()*0.25;
      floaters.appendChild(h);
    }
  }
  spawnFloaters();

  // Events
  goNext.addEventListener('click', (e)=>{
    const rect = e.currentTarget.getBoundingClientRect();
    burstHearts(rect.left + rect.width/2, rect.top + rect.height/2);
    // small delay for burst animation
    setTimeout(()=> showSlide(s2), 240);
  });

  goBack.addEventListener('click', (e)=>{
    e.preventDefault();
    showSlide(s1);
  });

  // Keyboard support: Enter/Space on first slide
  goNext.addEventListener('keyup', (e)=>{
    if(e.key === 'Enter' || e.key === ' '){
      goNext.click();
    }
  });
</script>
</body>
</html>
