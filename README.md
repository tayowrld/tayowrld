<!-- README.md  –– drop in / render anywhere where HTML+JS is allowed -->
<!-- ─────────────  HERO / INTRO  -->
<h1 align="center" id="intro">
  <span>👋 Привет, я Иван Курбаков</span>
</h1>

<p align="center" id="tagline">
  Full-stack&nbsp;dev (11 лет), 5 лет коммерции, open-source lover &amp; pixel-aesthetic designer
</p>

<!-- ─────────────  ANIMATED CARD STACK  -->
<div id="scene">
  <div class="card notice">this readme is still in dev mode, ‘cause I’m bored</div>
  <div class="card hello">Hello, my name is…</div>
  <div class="card name">Ivan Kurbakov</div>
  <div class="card if">If misunderstood</div>

  <!-- splashes / particles (styled as Omori-ish confetti) -->
  <div class="splash"></div><div class="splash"></div><div class="splash"></div>
  <div class="splash"></div><div class="splash"></div><div class="splash"></div>
</div>

<!-- ─────────────  STACK & INTERESTS  -->
<h2 id="stack-title">My stack 💻</h2>
<div id="stack">
  <img alt="HTML"    src="https://skillicons.dev/icons?i=html" />
  <img alt="CSS"     src="https://skillicons.dev/icons?i=css"  />
  <img alt="JavaScript" src="https://skillicons.dev/icons?i=js"   />
  <img alt="React"   src="https://skillicons.dev/icons?i=react" />
  <img alt="Next.js" src="https://skillicons.dev/icons?i=nextjs"/>
  <img alt="Tailwind"src="https://skillicons.dev/icons?i=tailwind"/>
  <img alt="Node.js" src="https://skillicons.dev/icons?i=nodejs"/>
</div>

<h2 id="interested-title">Interested in 🔍</h2>
<p id="interested">
  <img alt="Python" src="https://skillicons.dev/icons?i=python" />
  <img alt="Rust"   src="https://skillicons.dev/icons?i=rust"   />
  <img alt="C/C++"  src="https://skillicons.dev/icons?i=cpp"    />
  <img alt="Bash"   src="https://skillicons.dev/icons?i=bash"   />
</p>

<!-- ─────────────  AVATAR  -->
<h2 id="avatar-title">Avatar 🎮</h2>
<p id="avatar">
  <img src="https://raw.githubusercontent.com/tayworldd/tayworldd/main/avatar.gif" width="160" />
</p>

<!-- ─────────────  STYLE  -->
<style>
:root {
  --bg:#0d0d0d;
  --pink:#ffb6ff;
  --lav:#caa0ff;
  --sky:#98d8ff;
  --cyan:#4dfaff;
  --white:#f5f5f5;
  font-family:"Inter",sans-serif;
}
html,body{background:var(--bg);color:var(--white);margin:0;padding:0;scroll-behavior:smooth;}
#intro{font-size:clamp(1.8rem,2.5vw,3rem);letter-spacing:-.5px;}
#tagline{opacity:.8;margin-top:-.5rem;}
#scene{position:relative;margin:4rem auto;max-width:720px;height:320px;padding:1rem;}
.card{
  position:absolute;left:50%;transform:translateX(-50%);
  width:100%;max-width:640px;padding:1.25rem 1rem;border-radius:12px;
  text-align:center;font-weight:600;font-size:clamp(1rem,1.6vw,1.3rem);
  background:var(--pink);color:var(--lav);mix-blend-mode:screen;
  filter:drop-shadow(0 0 12px #0005);
}
.notice{top:0;background:var(--lav);color:#e0d6ff;}
.hello{top:80px;}
.name{top:160px;font-size:clamp(1.2rem,2vw,1.6rem);color:var(--sky);}
.if{top:240px;color:var(--cyan);}
#stack,#interested{display:flex;gap:.5rem;flex-wrap:wrap;justify-content:center;}
#stack img,#interested img{height:48px;transition:transform .4s;}
#stack img:hover,#interested img:hover{transform:translateY(-6px) scale(1.08);}
.splash{
  --size:6px;--clr:var(--cyan);
  position:absolute;width:var(--size);height:var(--size);background:var(--clr);
  border-radius:2px;opacity:.85;
}
</style>

<!-- ─────────────  ANIME.JS MAGIC  -->
<script src="https://cdn.jsdelivr.net/npm/animejs@4/dist/anime.min.js"></script>
<script>
document.addEventListener('DOMContentLoaded',()=>{

  /* floating card breathing */
  anime({
    targets:'.card',
    translateY:[-6,6],
    direction:'alternate',
    easing:'easeInOutSine',
    duration:3500,
    delay:(el,i)=>i*120,
    loop:true
  });

  /* randomized pastel splashes à la Omori background noise */
  const palette=['var(--lav)','var(--pink)','var(--sky)','var(--cyan)'];
  const scene=document.getElementById('scene');
  document.querySelectorAll('.splash').forEach((el,i)=>{
      const size=anime.random(4,10);
      el.style.setProperty('--size',size+'px');
      el.style.setProperty('--clr',palette[i%palette.length]);
      el.style.top=anime.random(0,280)+'px';
      el.style.left=anime.random(0,scene.clientWidth-size)+'px';
      anime({
        targets:el,
        scale:[0,anime.random(1,3)/2],
        rotate:()=>anime.random(-90,90),
        opacity:[.9,0],
        easing:'easeOutExpo',
        duration:2800,
        delay:anime.random(0,1200),
        loop:true
      });
  });

});
</script>
