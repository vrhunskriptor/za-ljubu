[index.html](https://github.com/user-attachments/files/34365488/index.html)
<title>Pitanje za milion</title>
<meta name="claude:viewport-fit-sides" content="cover">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Saira+Condensed:wght@500;600;700&family=Playfair+Display:ital,wght@0,600;1,500&display=swap">
<style>
/* Layout: one phone-height studio stage; spotlights behind, question lozenge, four answer lozenges, overlays for verdicts and the win sequence */
:root{
  --ink:#060920;        /* studio dark */
  --stage:#17114a;      /* violet stage glow */
  --rim:#9fb4ff;        /* silver-blue lozenge rim */
  --gold:#f4c652;       /* prize gold */
  --lock:#f0932b;       /* final answer orange */
  --win:#2fc46a;        /* correct green */
  --wrong:#d7333f;      /* wrong red */
  --text:#f5f2ff;
  --muted:#b9b5d8;
  --cond:"Saira Condensed","Arial Narrow","Roboto Condensed",sans-serif;
  --serif:"Playfair Display",Georgia,"Times New Roman",serif;
  color-scheme:dark;
}
[hidden]{display:none!important}
html,body{height:100%;background:var(--ink);color:var(--text)}
body{font-family:var(--cond);overflow:hidden;-webkit-tap-highlight-color:transparent}
.stage{position:relative;height:100%;display:flex;flex-direction:column;justify-content:center;gap:clamp(14px,3vh,28px);padding-block:20px;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px));max-width:820px;margin:0 auto;box-sizing:border-box}
.bg{position:fixed;inset:0;z-index:0;overflow:hidden;background:radial-gradient(ellipse at 50% 65%,var(--stage) 0%,var(--ink) 70%)}
.beam{position:absolute;left:50%;top:-20%;width:40vmax;height:140vmax;transform-origin:50% 0;background:linear-gradient(180deg,rgba(159,180,255,.16),rgba(159,180,255,0) 70%);clip-path:polygon(45% 0,55% 0,100% 100%,0 100%);animation:sweep 9s ease-in-out infinite alternate;mix-blend-mode:screen}
.beam.b2{animation-duration:11s;animation-delay:-4s;background:linear-gradient(180deg,rgba(244,198,82,.10),rgba(244,198,82,0) 70%)}
.beam.b3{animation-duration:13s;animation-delay:-7s}
@keyframes sweep{from{transform:translateX(-50%) rotate(-28deg)}to{transform:translateX(-50%) rotate(28deg)}}
.floor{position:absolute;left:50%;bottom:-30vmax;width:120vmax;height:60vmax;transform:translateX(-50%);border-radius:50%;background:radial-gradient(ellipse,rgba(159,180,255,.18),rgba(0,0,0,0) 60%)}
.stage>*{position:relative;z-index:1}

.top{display:flex;justify-content:space-between;align-items:center;gap:12px}
.prize{white-space:nowrap;font-weight:700;letter-spacing:.12em;text-transform:uppercase;color:var(--gold);font-size:clamp(15px,3.6vw,20px)}
.prize b{font-size:1.35em;letter-spacing:.04em}
.icon-btn{white-space:nowrap;background:rgba(255,255,255,.06);border:1px solid rgba(159,180,255,.4);color:var(--text);font-family:var(--cond);font-size:15px;letter-spacing:.06em;padding:6px 12px;border-radius:20px;cursor:pointer}
.ladder{display:flex;gap:4px;justify-content:center;flex-wrap:wrap}
.ladder span{font-variant-numeric:tabular-nums;font-size:13px;color:var(--muted);padding:2px 7px;border-radius:3px;letter-spacing:.04em}
.ladder span.on{background:var(--lock);color:#1a0d00;font-weight:700}

/* lozenge: rim layer + inner layer, both hexagon-clipped */
.loz{position:relative;--c:linear-gradient(180deg,#141a52,#0a0e33);--r:var(--rim);padding:2px;background:var(--r);clip-path:polygon(22px 0,calc(100% - 22px) 0,100% 50%,calc(100% - 22px) 100%,22px 100%,0 50%)}
.loz>.in{background:var(--c);clip-path:inherit;padding:12px 34px;min-height:100%;box-sizing:border-box;display:flex;align-items:center;gap:10px}
.row{position:relative}
.row::before{content:"";position:absolute;left:-100vw;right:-100vw;top:50%;height:2px;background:var(--rim);opacity:.55;z-index:-1}
.q .in{justify-content:center;text-align:center;min-height:clamp(110px,18vh,150px);font-size:clamp(19px,4.6vw,26px);font-weight:600;line-height:1.25;text-wrap:balance;padding:16px 40px}
.answers{display:grid;grid-template-columns:1fr 1fr;gap:12px 18px}
@media (max-width:560px){.answers{grid-template-columns:1fr;gap:10px}}
.ans{display:block;width:100%;border:0;font:inherit;color:inherit;cursor:pointer;text-align:left}
.ans .in{font-size:clamp(19px,4.8vw,24px);font-weight:600;min-height:54px}
.ans .k{color:var(--lock);font-weight:700;min-width:1.2em}
.ans:hover:not(:disabled){--r:#ffffff}
.ans:focus-visible{outline:none;--r:var(--gold)}
.ans:disabled{cursor:default}
.ans.gone{opacity:.28}
.ans.gone .t{text-decoration:line-through}
.ans.lock{--c:linear-gradient(180deg,#ffb04a,#d8721a);--r:#ffe2b0;color:#1a0d00}
.ans.lock .k{color:#fff}
.ans.lock{animation:pulse .5s ease-in-out infinite alternate}
.ans.right{--c:linear-gradient(180deg,#4fe08a,#1d9b52);--r:#d6ffe6;color:#04210f;animation:blink .25s steps(2) 6}
.ans.right .k{color:#fff}
.ans.bad{--c:linear-gradient(180deg,#f0545e,#a51d28);--r:#ffd0d3;color:#fff}
.ans.bad .k{color:#fff}
@keyframes pulse{to{filter:brightness(1.18)}}
@keyframes blink{50%{filter:brightness(1.6)}}
.hint{text-align:center;color:var(--muted);font-size:15px;letter-spacing:.05em;min-height:1.3em;margin:0}

/* overlays */
.ov{position:fixed;inset:0;z-index:5;display:grid;place-items:center;padding-block:24px;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px));background:rgba(4,6,22,.72);backdrop-filter:blur(3px);-webkit-backdrop-filter:blur(3px);animation:fadein .35s ease}
@keyframes fadein{from{opacity:0}}
.card{max-width:440px;width:100%;text-align:center;display:flex;flex-direction:column;gap:18px;align-items:center}
.verdict{font-family:var(--serif);font-size:clamp(24px,6.4vw,32px);line-height:1.25;font-weight:600;text-wrap:balance;margin:0}
.verdict.red{color:#ff8a92}
.face{font-size:15px;letter-spacing:.2em;text-transform:uppercase;color:var(--muted);margin:0}
.btn{font-family:var(--cond);font-size:20px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;color:#1a0d00;background:linear-gradient(180deg,#ffd77a,#e6a325);border:0;padding:12px 28px;border-radius:30px;cursor:pointer;box-shadow:0 6px 24px rgba(244,198,82,.35)}
.btn:focus-visible,.icon-btn:focus-visible{outline:2px solid #fff;outline-offset:3px}
.intro h1{font-family:var(--cond);font-weight:700;font-size:clamp(34px,10vw,58px);letter-spacing:.06em;line-height:1;margin:0;color:var(--gold);text-transform:uppercase;text-shadow:0 0 30px rgba(244,198,82,.35)}
.intro p{margin:0;color:var(--muted);font-size:18px;letter-spacing:.04em}

.win{align-items:start;place-items:safe center;background:radial-gradient(ellipse at 50% 40%,rgba(40,28,110,.85),rgba(4,6,22,.95));overflow:auto}
.win .card{max-width:520px;gap:10px;margin-block:auto}
.money{font-family:var(--cond);font-weight:700;font-size:clamp(42px,12vw,80px);line-height:1;color:var(--gold);font-variant-numeric:tabular-nums;text-shadow:0 0 40px rgba(244,198,82,.5);margin:0}
.congr{font-family:var(--serif);font-size:clamp(20px,5.4vw,27px);line-height:1.3;margin:0;text-wrap:balance}
.flower-line{font-family:var(--serif);font-style:italic;font-size:clamp(19px,5vw,24px);color:#ffd6e6;margin:0;text-wrap:balance}
#bouquet{width:min(100%,420px,44vh);aspect-ratio:1/1.05;max-width:100%;display:block}
.final{font-family:var(--serif);font-style:italic;font-weight:500;font-size:clamp(30px,8.5vw,46px);color:#fff;margin:0;text-shadow:0 0 24px rgba(255,190,220,.55)}
.step{opacity:0;transform:translateY(12px);transition:opacity 1s ease,transform 1s ease}
.step.show{opacity:1;transform:none}
#fx{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:9}
@media (prefers-reduced-motion:reduce){.beam,.ans.lock,.ans.right{animation:none}.step{transition:none}}
</style>

<div class="bg" aria-hidden="true"><div class="beam"></div><div class="beam b2"></div><div class="beam b3"></div><div class="floor"></div></div>

<main class="stage" id="stage">
  <div class="top">
    <div class="prize">Pitanje za <b>1.000.000 €</b></div>
    <button class="icon-btn" id="mute" aria-pressed="false">♪ Zvuk</button>
  </div>
  <div class="ladder" aria-hidden="true">
    <span>1.000</span><span>32.000</span><span>125.000</span><span>500.000</span><span class="on">1.000.000 €</span>
  </div>
  <div class="row"><div class="loz q"><div class="in" id="question">Danas je poseban dan, nosi određeni broj koji samo Vi znate koji je. Odaberite tačan odgovor:</div></div></div>
  <div class="answers" id="answers">
    <div class="row"><button class="loz ans" data-k="a"><span class="in"><span class="k">A:</span><span class="t">6 dana</span></span></button></div>
    <div class="row"><button class="loz ans" data-k="b"><span class="in"><span class="k">B:</span><span class="t">5 meseci</span></span></button></div>
    <div class="row"><button class="loz ans" data-k="c"><span class="in"><span class="k">C:</span><span class="t">6 meseci</span></span></button></div>
    <div class="row"><button class="loz ans" data-k="d"><span class="in"><span class="k">D:</span><span class="t">6 godina</span></span></button></div>
  </div>
  <p class="hint" id="hint">Dobro razmislite. Imate samo jedan život.</p>
</main>

<div class="ov intro" id="intro">
  <div class="card">
    <p class="face">Večeras u studiju</p>
    <h1>Pitanje<br>za milion</h1>
    <p>Jedno pitanje. Jedan dobitnik. Vi.</p>
    <button class="btn" id="start">Uđi u studio</button>
  </div>
</div>

<div class="ov" id="verdict" hidden>
  <div class="card">
    <p class="face" id="vface">Netačan odgovor</p>
    <p class="verdict red" id="vtext"></p>
    <button class="btn" id="retry">Pokušajte ponovo</button>
  </div>
</div>

<div class="ov win" id="win" hidden>
  <div class="card">
    <p class="money step" id="money">0 €</p>
    <p class="congr step" id="congr">Čestitamo, Vaš subjektivni osećaj Vam je osvojio 1.000.000 evra!</p>
    <p class="flower-line step" id="fl">A evo Vam i cveće, pošto ste prelepi.</p>
    <canvas id="bouquet" class="step" aria-label="Buket ljiljana"></canvas>
    <p class="final step" id="final">Želim ti najlepši dan ♥</p>
  </div>
</div>

<canvas id="fx" aria-hidden="true"></canvas>

<script>
(()=>{
const $=id=>document.getElementById(id);
const TAU=Math.PI*2;
const reduce=matchMedia("(prefers-reduced-motion: reduce)").matches;

/* ================= AUDIO (original score, Web Audio) ================= */
const A={ac:null,master:null,rev:null,muted:false,mode:"none",pad:null,next:0,beat:0,timer:null};
const N=m=>440*Math.pow(2,(m-69)/12);
function audioInit(){
  if(A.ac)return;const AC=window.AudioContext||window.webkitAudioContext;if(!AC)return;
  const ac=A.ac=new AC();A.master=ac.createGain();A.master.gain.value=0.55;
  const comp=ac.createDynamicsCompressor();A.master.connect(comp);comp.connect(ac.destination);
  // generated reverb
  const len=ac.sampleRate*2.6,ir=ac.createBuffer(2,len,ac.sampleRate);
  for(let c=0;c<2;c++){const d=ir.getChannelData(c);for(let i=0;i<len;i++)d[i]=(Math.random()*2-1)*Math.pow(1-i/len,3)}
  A.rev=ac.createConvolver();A.rev.buffer=ir;const rg=ac.createGain();rg.gain.value=0.35;A.rev.connect(rg);rg.connect(A.master);
  A.timer=setInterval(sched,40);
}
function out(node,wet=0.3){node.connect(A.master);if(wet){const g=A.ac.createGain();g.gain.value=wet;node.connect(g);g.connect(A.rev)}}
function env(g,at,a,peak,d,end=0.0001){g.gain.setValueAtTime(0.0001,at);g.gain.exponentialRampToValueAtTime(peak,at+a);g.gain.exponentialRampToValueAtTime(end,at+a+d)}
function tone(type,f,at,a,peak,d,wet=0.3,filt){const ac=A.ac,o=ac.createOscillator(),g=ac.createGain();o.type=type;o.frequency.setValueAtTime(f,at);let n=o;if(filt){const lp=ac.createBiquadFilter();lp.type="lowpass";lp.frequency.value=filt;o.connect(lp);n=lp}n.connect(g);env(g,at,a,peak,d);out(g,wet);o.start(at);o.stop(at+a+d+0.05);return o}
function thump(at,v){const ac=A.ac,o=ac.createOscillator(),g=ac.createGain();o.type="sine";o.frequency.setValueAtTime(70,at);o.frequency.exponentialRampToValueAtTime(38,at+0.25);env(g,at,0.005,v,0.35);o.connect(g);out(g,0.05);o.start(at);o.stop(at+0.45)}
function tick(at,v){const ac=A.ac,b=ac.createBuffer(1,ac.sampleRate*0.03,ac.sampleRate),d=b.getChannelData(0);for(let i=0;i<d.length;i++)d[i]=(Math.random()*2-1)*(1-i/d.length);const s=ac.createBufferSource();s.buffer=b;const hp=ac.createBiquadFilter();hp.type="highpass";hp.frequency.value=6000;const g=ac.createGain();g.gain.value=v;s.connect(hp);hp.connect(g);out(g,0.1);s.start(at)}
function swoosh(at,dur){const ac=A.ac,b=ac.createBuffer(1,ac.sampleRate*dur,ac.sampleRate),d=b.getChannelData(0);for(let i=0;i<d.length;i++)d[i]=Math.random()*2-1;const s=ac.createBufferSource();s.buffer=b;const bp=ac.createBiquadFilter();bp.type="bandpass";bp.Q.value=2;bp.frequency.setValueAtTime(300,at);bp.frequency.exponentialRampToValueAtTime(5000,at+dur);const g=ac.createGain();g.gain.setValueAtTime(0.0001,at);g.gain.exponentialRampToValueAtTime(0.25,at+dur*0.95);g.gain.exponentialRampToValueAtTime(0.0001,at+dur);s.connect(bp);bp.connect(g);out(g,0.4);s.start(at)}

// sustained tension pad (drone + tremolo strings)
function padStart(){
  padStop(0.01);const ac=A.ac,t=ac.currentTime;const bus=ac.createGain();bus.gain.setValueAtTime(0.0001,t);bus.gain.exponentialRampToValueAtTime(0.5,t+2);out(bus,0.45);
  const lp=ac.createBiquadFilter();lp.type="lowpass";lp.frequency.value=900;lp.connect(bus);
  const trem=ac.createGain();trem.gain.value=0.5;trem.connect(lp);const lfo=ac.createOscillator(),lg=ac.createGain();lfo.frequency.value=7;lg.gain.value=0.35;lfo.connect(lg);lg.connect(trem.gain);lfo.start();
  const drone=[N(33),N(40)].map((f,i)=>{const o=ac.createOscillator();o.type=i?"triangle":"sine";o.frequency.value=f;const g=ac.createGain();g.gain.value=i?0.12:0.35;o.connect(g);g.connect(bus);o.start();return o});
  const str=[0,7,-5].map(dt=>{const o=ac.createOscillator();o.type="sawtooth";o.detune.value=dt;o.frequency.value=N(57);const g=ac.createGain();g.gain.value=0.05;o.connect(g);g.connect(trem);o.start();return o});
  A.pad={bus,lp,oscs:[lfo,...drone,...str],str};
}
function padStop(fade=1.2){if(!A.pad)return;const p=A.pad,t=A.ac.currentTime;p.bus.gain.cancelScheduledValues(t);p.bus.gain.setValueAtTime(p.bus.gain.value,t);p.bus.gain.exponentialRampToValueAtTime(0.0001,t+fade);p.oscs.forEach(o=>o.stop(t+fade+0.05));A.pad=null}

const TENSION=[57,60,59,64,57,60,62,64,65,64,62,60];
const CALM=[[53,57,60,65],[50,57,62,65],[46,53,58,62],[48,55,60,64]];
function sched(){
  if(!A.ac||A.ac.state!=="running")return;const now=A.ac.currentTime;
  if(A.next<now)A.next=now+0.05;
  while(A.next<now+0.2){
    const at=A.next,b=A.beat;
    if(A.mode==="tension"||A.mode==="lock"){
      const fast=A.mode==="lock";const spb=fast?0.42:0.94;
      if(b%2===0){thump(at,fast?0.9:0.7);thump(at+0.17,fast?0.5:0.35)}
      tick(at,0.05);
      if(A.pad&&b%4===0){const m=TENSION[(b/4)%TENSION.length];A.pad.str.forEach(o=>o.frequency.setTargetAtTime(N(m),at,0.25))}
      if(b%8===4)tone("sine",N(81+(b%16?0:3)),at,0.01,0.05,1.6,0.6);
      A.next+=spb/2;
    }else if(A.mode==="calm"){
      const ch=CALM[Math.floor(b/8)%4],pat=[0,1,2,3,2,1,3,2];const m=ch[pat[b%8]]+12;
      tone("triangle",N(m),at,0.008,b%8===0?0.12:0.07,1.4,0.5);
      if(b%8===0){tone("sine",N(ch[0]-12),at,0.4,0.12,3.2,0.4);tone("sine",N(ch[2]+24),at,0.005,0.03,2.5,0.7)}
      A.next+=0.36;
    }else{A.next+=0.25}
    A.beat++;
  }
}
function setMode(m){A.mode=m;A.beat=0;if(A.ac)A.next=A.ac.currentTime+0.05}
function sfxLock(){if(!A.ac)return;const t=A.ac.currentTime;swoosh(t,1.9);if(A.pad)A.pad.lp.frequency.exponentialRampToValueAtTime(3000,t+1.9)}
function sfxWrong(){if(!A.ac)return;const t=A.ac.currentTime;padStop(0.3);[[58,57],[57,56],[56,43]].forEach(([a,b],i)=>{const at=t+0.1+i*0.45,d=i===2?1.4:0.4;const o=tone("sawtooth",N(a),at,0.02,0.18,d,0.25,1200);o.frequency.setValueAtTime(N(a),at);o.frequency.exponentialRampToValueAtTime(N(b),at+d)});thump(t+0.1,1)}
function sfxWin(){if(!A.ac)return;const t=A.ac.currentTime;padStop(0.2);thump(t,1.2);
  const brass=(m,at,d,v=0.13)=>{[0,6].forEach(dt=>{const o=tone("sawtooth",N(m),at,0.04,v,d,0.35,2400);o.detune.value=dt})};
  [[67,0],[72,0.16],[76,0.32],[79,0.48]].forEach(([m,o])=>brass(m,t+0.1+o,0.25));
  [60,64,67,72,76].forEach(m=>brass(m,t+0.75,2.6,0.08));thump(t+0.75,1.3);
  for(let i=0;i<16;i++)tone("sine",N(84+[0,4,7,12][i%4]),t+0.8+i*0.09,0.005,0.05,1.2,0.8);
}

/* ================= CONFETTI ================= */
const fx=$("fx"),fc=fx.getContext("2d");let P=[],fxRun=false;
function fxSize(){const d=Math.min(devicePixelRatio||1,2);fx.width=innerWidth*d;fx.height=innerHeight*d}
fxSize();addEventListener("resize",fxSize);
const CC=["#f4c652","#ff5e8a","#ffffff","#9fb4ff","#2fc46a","#ff9f43","#d78bff"];
function burst(n,x,y,spread=1){if(reduce)n=Math.floor(n/4);for(let i=0;i<n;i++){const a=-Math.PI/2+(Math.random()-0.5)*Math.PI*spread,v=(6+Math.random()*12)*(fx.width/900+0.5);P.push({x:x*fx.width,y:y*fx.height,vx:Math.cos(a)*v,vy:Math.sin(a)*v,r:Math.random()*TAU,vr:(Math.random()-0.5)*0.3,w:(6+Math.random()*8)*(fx.width/1200+0.6),c:CC[i%CC.length],t:0,shape:Math.random()<0.25?1:0})}if(!fxRun){fxRun=true;requestAnimationFrame(fxLoop)}}
function rain(n){for(let i=0;i<n;i++)P.push({x:Math.random()*fx.width,y:-Math.random()*fx.height*0.5,vx:(Math.random()-0.5)*2,vy:2+Math.random()*3,r:Math.random()*TAU,vr:(Math.random()-0.5)*0.2,w:(6+Math.random()*7)*(fx.width/1200+0.6),c:CC[i%CC.length],t:0,shape:Math.random()<0.2?1:0});if(!fxRun){fxRun=true;requestAnimationFrame(fxLoop)}}
function fxLoop(){fc.clearRect(0,0,fx.width,fx.height);const g=0.25*(fx.width/900+0.5);
  P=P.filter(p=>p.y<fx.height+40&&p.t<900);
  for(const p of P){p.t++;p.vy+=g*0.6;p.vx*=0.985;p.vy=Math.min(p.vy*0.99,4+p.w*0.3);p.x+=p.vx+Math.sin(p.t*0.05+p.w)*0.8;p.y+=p.vy;p.r+=p.vr;
    fc.save();fc.translate(p.x,p.y);fc.rotate(p.r);fc.scale(1,Math.cos(p.t*0.12+p.w));fc.fillStyle=p.c;
    if(p.shape){fc.beginPath();fc.moveTo(0,p.w*0.35);fc.bezierCurveTo(-p.w*0.7,-p.w*0.2,-p.w*0.25,-p.w*0.7,0,-p.w*0.25);fc.bezierCurveTo(p.w*0.25,-p.w*0.7,p.w*0.7,-p.w*0.2,0,p.w*0.35);fc.fill()}
    else fc.fillRect(-p.w/2,-p.w/4,p.w,p.w/2);fc.restore()}
  if(P.length)requestAnimationFrame(fxLoop);else{fxRun=false;fc.clearRect(0,0,fx.width,fx.height)}}

/* ================= LILY BOUQUET ================= */
const bq=$("bouquet"),bc=bq.getContext("2d");let bqStart=0,bqOn=false;
function rnd(seed){return()=>{seed|=0;seed=seed+0x6D2B79F5|0;let t=Math.imul(seed^seed>>>15,1|seed);t=t+Math.imul(t^t>>>7,61|t)^t;return((t^t>>>14)>>>0)/4294967296}}
function petal(c,L,w,curl,pal,spots,seed){
  c.beginPath();c.moveTo(0,0);
  c.bezierCurveTo(w*0.95,-L*0.22,w*0.85,-L*0.72,curl,-L);
  c.bezierCurveTo(-w*0.75,-L*0.72,-w*0.95,-L*0.22,0,0);c.closePath();
  const g=c.createLinearGradient(0,0,curl*0.6,-L);g.addColorStop(0,pal[0]);g.addColorStop(0.42,pal[1]);g.addColorStop(1,pal[2]);
  c.fillStyle=g;c.fill();c.strokeStyle=pal[3];c.lineWidth=Math.max(0.6,L*0.012);c.stroke();
  c.strokeStyle=pal[4];c.lineWidth=Math.max(0.6,L*0.018);c.beginPath();c.moveTo(0,-L*0.05);c.quadraticCurveTo(curl*0.2,-L*0.55,curl*0.85,-L*0.95);c.stroke();
  if(spots){const r=rnd(seed);c.fillStyle=pal[5];for(let i=0;i<14;i++){const f=0.12+r()*0.4;c.beginPath();c.ellipse((r()-0.5)*w*0.9*f*2.2,-L*f,L*0.012+r()*L*0.01,L*0.018,0,0,TAU);c.fill()}}
}
const PAL={
  pink:["#c2185b","#f06a9a","#fff4f7","rgba(255,255,255,.8)","rgba(255,255,255,.55)","#8e0f44"],
  white:["#c9d97a","#fbfbf2","#ffffff","rgba(230,230,210,.9)","rgba(214,224,170,.7)","#000"],
  blush:["#e2577f","#f8b3c9","#fffafb","rgba(255,255,255,.85)","rgba(255,255,255,.6)","#b02a5a"]
};
function lily(c,x,y,s,rot,bloom,variant,seed,t){
  c.save();c.translate(x,y);c.rotate(rot+Math.sin(t*0.9+seed)*0.03);
  const pal=PAL[variant],spots=variant!=="white",b=Math.max(0.02,bloom);
  const L=s*(0.55+0.45*b),w=s*0.24*(0.5+0.5*b),curl=s*0.16*b;
  c.save();c.scale(1,0.82);
  for(const pass of[0,1])for(let k=0;k<3;k++){
    const base=(k/3)*TAU+(pass?Math.PI/3:0);const ang=base*b+(1-b)*((k-1)*0.12);
    c.save();c.rotate(ang);if(!pass)c.globalAlpha=0.92;petal(c,L*(pass?1:0.96),w*(pass?1:0.92),curl*(k%2?1:-1),pal,spots,seed*7+k+pass*3);c.restore()}
  c.restore();
  if(b>0.35){const sb=(b-0.35)/0.65;
    for(let k=0;k<6;k++){const a=k/6*TAU+0.3,r=s*0.42*sb;const ex=Math.cos(a)*r,ey=Math.sin(a)*r*0.82;
      c.strokeStyle="#cfe3a0";c.lineWidth=Math.max(0.8,s*0.018);c.beginPath();c.moveTo(0,0);c.quadraticCurveTo(ex*0.5,ey*0.5-s*0.06,ex,ey);c.stroke();
      c.fillStyle="#b4521f";c.beginPath();c.ellipse(ex,ey,s*0.045,s*0.018,a,0,TAU);c.fill()}
    c.strokeStyle="#a9cf6a";c.lineWidth=Math.max(1,s*0.025);c.beginPath();c.moveTo(0,0);c.lineTo(Math.cos(1.9)*s*0.5*sb,Math.sin(1.9)*s*0.4*sb);c.stroke();
    c.fillStyle="#7fae3d";c.beginPath();c.arc(Math.cos(1.9)*s*0.5*sb,Math.sin(1.9)*s*0.4*sb,s*0.035,0,TAU);c.fill()}
  c.fillStyle=variant==="white"?"#d4e07e":"#7a0f3a";c.beginPath();c.arc(0,0,s*0.05,0,TAU);c.fill();
  c.restore();
}
function bud(c,x,y,s,rot,t,col){c.save();c.translate(x,y);c.rotate(rot+Math.sin(t*1.1+x)*0.04);const g=c.createLinearGradient(0,0,0,-s);g.addColorStop(0,"#7fae3d");g.addColorStop(0.5,col);g.addColorStop(1,"#fff");c.fillStyle=g;c.beginPath();c.moveTo(0,0);c.bezierCurveTo(s*0.22,-s*0.3,s*0.18,-s*0.8,0,-s);c.bezierCurveTo(-s*0.18,-s*0.8,-s*0.22,-s*0.3,0,0);c.fill();c.strokeStyle="rgba(255,255,255,.5)";c.lineWidth=1;c.beginPath();c.moveTo(0,-s*0.1);c.lineTo(0,-s*0.95);c.stroke();c.restore()}
function leaf(c,x,y,len,ang,t,ph){c.save();c.translate(x,y);c.rotate(ang+Math.sin(t*0.8+ph)*0.05);const g=c.createLinearGradient(0,0,len,0);g.addColorStop(0,"#2e6b2a");g.addColorStop(1,"#6fae4a");c.fillStyle=g;c.beginPath();c.moveTo(0,0);c.quadraticCurveTo(len*0.5,-len*0.16,len,0);c.quadraticCurveTo(len*0.5,len*0.1,0,0);c.fill();c.strokeStyle="rgba(200,240,170,.35)";c.lineWidth=1;c.beginPath();c.moveTo(0,0);c.quadraticCurveTo(len*0.5,-len*0.03,len*0.95,0);c.stroke();c.restore()}
const FLOWERS=[
  // x, y (relative to size), petal size, rotation, variant, delay
  [0.00,-0.70,0.20,0.00,"pink",0.0],
  [-0.24,-0.58,0.18,-0.35,"white",0.35],
  [0.25,-0.57,0.18,0.35,"blush",0.6],
  [-0.12,-0.42,0.17,-0.15,"blush",0.9],
  [0.14,-0.40,0.17,0.2,"white",1.15],
  [-0.33,-0.34,0.15,-0.6,"pink",1.4],
  [0.34,-0.33,0.15,0.6,"pink",1.65]
];
const BUDS=[[-0.06,-0.86,0.12,-0.2,"#f6c4d6"],[0.13,-0.80,0.11,0.3,"#ffffff"],[-0.40,-0.52,0.10,-0.7,"#ffffff"],[0.42,-0.50,0.10,0.75,"#f6c4d6"]];
function bqSize(){const d=Math.min(devicePixelRatio||1,2),r=bq.getBoundingClientRect();bq.width=Math.max(300,r.width*d);bq.height=bq.width*1.05}
function drawBouquet(now){
  const t=(now-bqStart)/1000,c=bc,W=bq.width,H=bq.height,S=W*0.95,bx=W/2,by=H*0.9;
  c.clearRect(0,0,W,H);
  const glowG=c.createRadialGradient(bx,H*0.42,0,bx,H*0.42,W*0.55);glowG.addColorStop(0,"rgba(255,200,225,.22)");glowG.addColorStop(1,"rgba(255,200,225,0)");c.fillStyle=glowG;c.fillRect(0,0,W,H);
  const grow=reduce?1:Math.min(1,t/1.2);
  // stems
  const ends=[...FLOWERS.map(f=>[f[0],f[1]]),...BUDS.map(b=>[b[0],b[1]])];
  ends.forEach(([fx_,fy],i)=>{const ex=bx+fx_*S,ey=by+fy*S*grow;c.strokeStyle=i%2?"#3f7f2f":"#4c8f37";c.lineWidth=Math.max(2,W*0.007);c.beginPath();c.moveTo(bx+(i-5)*W*0.004,by+H*0.05);c.quadraticCurveTo(bx+fx_*S*0.25,by-S*0.2,ex,ey);c.stroke()});
  // leaves
  [[-0.05,-0.2,0.28,-2.3],[0.05,-0.22,0.27,-0.85],[-0.1,-0.3,0.24,-2.7],[0.1,-0.31,0.24,-0.45],[0,-0.25,0.22,-1.75],[-0.15,-0.18,0.2,-3.0],[0.16,-0.18,0.2,-0.15]].forEach(([lx,ly,ln,a],i)=>leaf(c,bx+lx*S,by+ly*S*grow,ln*S*grow,a,t,i));
  // wrap
  const wt=by-S*0.24,wl=bx-S*0.3,wr=bx+S*0.3;
  const wg=c.createLinearGradient(wl,0,wr,0);wg.addColorStop(0,"#e9d6c2");wg.addColorStop(0.5,"#fff4e8");wg.addColorStop(1,"#d9c2aa");
  c.fillStyle=wg;c.beginPath();c.moveTo(wl,wt);c.lineTo(bx-S*0.1,wt+S*0.03);c.lineTo(bx,wt-S*0.02);c.lineTo(bx+S*0.12,wt+S*0.03);c.lineTo(wr,wt);c.lineTo(bx+S*0.05,by+S*0.08);c.lineTo(bx-S*0.05,by+S*0.08);c.closePath();c.fill();
  c.strokeStyle="rgba(150,120,90,.35)";c.lineWidth=1;c.beginPath();c.moveTo(bx,wt-S*0.02);c.lineTo(bx,by+S*0.08);c.moveTo(bx-S*0.1,wt+S*0.03);c.lineTo(bx-S*0.02,by+S*0.08);c.moveTo(bx+S*0.12,wt+S*0.03);c.lineTo(bx+S*0.02,by+S*0.08);c.stroke();
  // ribbon
  const ry=by-S*0.02;c.fillStyle="#d81b60";c.fillRect(bx-S*0.085,ry-S*0.022,S*0.17,S*0.044);
  c.beginPath();c.ellipse(bx-S*0.06,ry,S*0.07,S*0.035,-0.4,0,TAU);c.ellipse(bx+S*0.06,ry,S*0.07,S*0.035,0.4,0,TAU);c.fill();
  c.beginPath();c.moveTo(bx-S*0.01,ry);c.quadraticCurveTo(bx-S*0.06+Math.sin(t*1.5)*S*0.01,ry+S*0.1,bx-S*0.09,ry+S*0.15);c.lineTo(bx-S*0.06,ry+S*0.15);c.quadraticCurveTo(bx-S*0.03,ry+S*0.08,bx+S*0.01,ry);c.fill();
  c.beginPath();c.moveTo(bx+S*0.01,ry);c.quadraticCurveTo(bx+S*0.06+Math.sin(t*1.5+1)*S*0.01,ry+S*0.1,bx+S*0.1,ry+S*0.14);c.lineTo(bx+S*0.07,ry+S*0.15);c.quadraticCurveTo(bx+S*0.03,ry+S*0.08,bx-S*0.01,ry);c.fill();
  c.fillStyle="#ad1457";c.beginPath();c.arc(bx,ry,S*0.022,0,TAU);c.fill();
  // buds and flowers
  BUDS.forEach(([x,y,s,r,col])=>bud(c,bx+x*S,by+y*S*grow,s*S*grow,r,t,col));
  FLOWERS.slice().reverse().forEach(([x,y,s,r,v,dl],i)=>{const bl=reduce?1:Math.min(1,Math.max(0,(t-0.9-dl)/1.6));const e=bl*bl*(3-2*bl);lily(c,bx+x*S,by+y*S*grow,s*S,r,e,v,i+3,t)});
  // sparkles
  const sr=rnd(5);for(let i=0;i<22;i++){const x=sr()*W,y=sr()*H*0.75,ph=sr()*TAU;const a=Math.max(0,Math.sin(t*1.7+ph));c.globalAlpha=a*0.9;c.fillStyle="#fff";const z=W*0.006*a;c.beginPath();c.moveTo(x,y-z*2);c.lineTo(x+z*0.4,y);c.lineTo(x,y+z*2);c.lineTo(x-z*0.4,y);c.fill();c.globalAlpha=1}
  if(bqOn)requestAnimationFrame(drawBouquet);
}

/* ================= GAME FLOW ================= */
const answers=[...document.querySelectorAll(".ans")];
const MSG={
  a:"Sram te bilo, s kim se još viđaš!",
  b:"Sram te bilo, s kim se još viđaš!",
  c:"Mislio sam da imaš iole osećaja za vreme, ali ovo je sramotno."
};
const HINTS=["Dobro razmislite. Imate samo jedan život.","Hmm. Publika je zabrinuta.","Voditelj se znoji. Probajte ponovo.","Ostao je samo jedan odgovor..."];
let busy=false,wrongCount=0,pending=null;
function setAll(dis){answers.forEach(b=>{if(!b.classList.contains("gone"))b.disabled=dis})}
$("start").onclick=()=>{audioInit();if(A.ac&&A.ac.state==="suspended")A.ac.resume();if(A.ac){padStart();setMode("tension")}$("intro").hidden=true;answers[0].focus({preventScroll:true})};
answers.forEach(btn=>btn.onclick=()=>{
  if(busy)return;busy=true;const k=btn.dataset.k;setAll(true);btn.classList.add("lock");$("hint").textContent="Konačan odgovor?";
  setMode("lock");sfxLock();
  setTimeout(()=>{
    btn.classList.remove("lock");
    if(k==="d"){btn.classList.add("right");setMode("none");sfxWin();burst(160,0.5,0.75,1.1);burst(90,0.15,0.9,0.6);burst(90,0.85,0.9,0.6);setTimeout(win,1500)}
    else{btn.classList.add("bad");setMode("none");sfxWrong();pending=btn;$("vface").textContent=k==="c"?"Netačan odgovor (tehnički tačan)":"Netačan odgovor";$("vtext").textContent=MSG[k];setTimeout(()=>{$("verdict").hidden=false;$("retry").focus({preventScroll:true})},900)}
  },reduce?600:2300);
});
$("retry").onclick=()=>{$("verdict").hidden=true;if(pending){pending.classList.remove("bad");pending.classList.add("gone");pending.disabled=true;pending=null}wrongCount++;$("hint").textContent=HINTS[Math.min(wrongCount,3)];busy=false;setAll(false);if(A.ac){padStart();setMode("tension")}};

function win(){
  const w=$("win");w.hidden=false;const show=(id,ms)=>setTimeout(()=>$(id).classList.add("show"),ms);
  show("money",100);
  const m=$("money"),t0=performance.now();(function cnt(n){const p=Math.min(1,(n-t0)/1800),v=Math.round(1000000*(1-Math.pow(1-p,3)));m.textContent=v.toLocaleString("sr-RS")+" €";if(p<1)requestAnimationFrame(cnt)})(t0);
  show("congr",1300);rain(120);
  setTimeout(()=>{if(A.ac)setMode("calm")},2600);
  setTimeout(()=>{$("fl").classList.add("show");bqSize();$("bouquet").classList.add("show");bqStart=performance.now();bqOn=true;requestAnimationFrame(drawBouquet);burst(80,0.5,0.55,2)},3600);
  setTimeout(()=>{$("final").classList.add("show");rain(80);$("final").scrollIntoView({behavior:reduce?"auto":"smooth",block:"end"})},8200);
}
addEventListener("resize",()=>{if(bqOn)bqSize()});

$("mute").onclick=e=>{A.muted=!A.muted;if(A.master)A.master.gain.setTargetAtTime(A.muted?0:0.55,A.ac.currentTime,0.05);e.currentTarget.textContent=A.muted?"♪ Bez zvuka":"♪ Zvuk";e.currentTarget.setAttribute("aria-pressed",A.muted)};
document.addEventListener("visibilitychange",()=>{if(!A.ac)return;document.hidden?A.ac.suspend():A.ac.resume()});
})();
</script>
