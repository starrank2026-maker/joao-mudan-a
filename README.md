# joao-mudan-a<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>João Mudanças — Orçamento Online</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Montserrat:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
<style>
:root{
  --red:#D32F2F;--red2:#FF5252;--red-dark:#B71C1C;
  --bg:#0A0A0A;--bg2:#111;--card:#161616;
  --border:rgba(211,47,47,.22);--border2:rgba(255,255,255,.07);
  --text:#F5F0EE;--text2:#9E9E9E;--green:#25D366;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth;-webkit-tap-highlight-color:transparent}
body{background:var(--bg);color:var(--text);font-family:'Montserrat',sans-serif;min-height:100vh;overflow-x:hidden}
body::-webkit-scrollbar{width:4px}
body::-webkit-scrollbar-track{background:var(--bg)}
body::-webkit-scrollbar-thumb{background:var(--red);border-radius:2px}

/* LOADING */
#loading{position:fixed;inset:0;z-index:9999;background:#000;display:flex;flex-direction:column;align-items:center;justify-content:center;transition:opacity .6s,visibility .6s}
#loading.hide{opacity:0;visibility:hidden;pointer-events:none}
.ld-icon{font-size:3rem;margin-bottom:16px;animation:truck 1.1s ease-in-out infinite alternate}
@keyframes truck{from{transform:translateX(-10px)}to{transform:translateX(10px)}}
.ld-name{font-family:'Playfair Display',serif;font-size:1.6rem;font-weight:900;color:var(--red2);letter-spacing:3px;margin-bottom:4px}
.ld-sub{font-size:.48rem;letter-spacing:5px;color:var(--text2);text-transform:uppercase;margin-bottom:22px}
.ld-bar{width:150px;height:2px;background:rgba(255,255,255,.08);border-radius:2px;overflow:hidden}
.ld-fill{height:100%;width:0;background:var(--red2);border-radius:2px;animation:fill 1.8s ease forwards}
@keyframes fill{to{width:100%}}

/* HEADER */
header{position:fixed;top:0;left:0;right:0;z-index:100;height:56px;padding:0 14px;display:flex;align-items:center;justify-content:space-between;background:rgba(6,6,6,.94);backdrop-filter:blur(20px);border-bottom:1px solid var(--border)}
.hlogo{display:flex;align-items:center;gap:8px;text-decoration:none}
.hlogo-name{font-family:'Playfair Display',serif;font-size:.9rem;font-weight:900;color:var(--red2);letter-spacing:1px;display:block}
.hlogo-sub{font-size:.4rem;letter-spacing:3px;color:var(--text2);text-transform:uppercase}
.open-pill{display:flex;align-items:center;gap:5px;font-size:.55rem;font-weight:700;letter-spacing:1px;color:#4CAF50;text-transform:uppercase}
.open-dot{width:6px;height:6px;border-radius:50%;background:#4CAF50;animation:blink 1.4s ease-in-out infinite;flex-shrink:0}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.25}}

/* HERO */
.hero{margin-top:56px;background:linear-gradient(160deg,#0a0000 0%,#1a0000 60%,#0a0000 100%);padding:40px 20px 36px;text-align:center;position:relative;overflow:hidden}
.hero-glow{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:350px;height:350px;background:radial-gradient(circle,rgba(211,47,47,.13) 0%,transparent 70%);pointer-events:none}
.hero-truck{font-size:2.8rem;display:block;margin-bottom:10px;animation:float 3s ease-in-out infinite}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-8px)}}
.hero-badge{display:inline-block;background:rgba(211,47,47,.18);border:1px solid rgba(255,82,82,.35);color:var(--red2);font-size:.48rem;font-weight:800;letter-spacing:3px;text-transform:uppercase;padding:4px 12px;border-radius:3px;margin-bottom:10px;position:relative;z-index:1}
.hero-title{font-family:'Playfair Display',serif;font-size:clamp(1.7rem,6vw,2.5rem);font-weight:900;color:#fff;line-height:1.1;margin-bottom:8px;position:relative;z-index:1}
.hero-title span{color:var(--red2)}
.hero-desc{font-size:.72rem;color:rgba(255,255,255,.65);line-height:1.8;margin-bottom:22px;position:relative;z-index:1;max-width:380px;margin-left:auto;margin-right:auto}
.btn-hero{display:inline-flex;align-items:center;gap:8px;background:linear-gradient(135deg,var(--red2),var(--red-dark));color:#fff;font-weight:800;font-size:.75rem;letter-spacing:2px;text-transform:uppercase;padding:13px 28px;border-radius:50px;border:none;cursor:pointer;box-shadow:0 8px 28px rgba(211,47,47,.5);transition:transform .2s,box-shadow .2s;position:relative;z-index:1}
.btn-hero:hover{transform:translateY(-3px);box-shadow:0 14px 40px rgba(211,47,47,.65)}
.hero-feats{display:flex;justify-content:center;gap:14px;margin-top:20px;flex-wrap:wrap;position:relative;z-index:1}
.hero-feat{display:flex;align-items:center;gap:4px;font-size:.56rem;color:rgba(255,255,255,.55)}

/* STATS */
.stats-bar{background:linear-gradient(135deg,#0f0000,#1a0000);border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:14px 16px}
.stats-inner{display:flex;justify-content:space-around;align-items:center;max-width:460px;margin:0 auto}
.stat{text-align:center}
.stat-n{font-family:'Playfair Display',serif;font-size:1.3rem;font-weight:900;color:var(--red2);display:block;line-height:1}
.stat-l{font-size:.46rem;color:var(--text2);letter-spacing:2px;text-transform:uppercase;margin-top:2px}
.stat-div{width:1px;height:32px;background:var(--border)}

/* QUESTIONÁRIO WRAPPER */
.quiz-wrapper{padding:28px 14px 50px;max-width:560px;margin:0 auto}
.quiz-intro{background:var(--card);border:1px solid var(--border);border-radius:20px;padding:22px;margin-bottom:24px;text-align:center}
.qi-icon{font-size:2.2rem;margin-bottom:10px;display:block}
.qi-title{font-family:'Playfair Display',serif;font-size:1.1rem;font-weight:700;color:var(--text);margin-bottom:6px}
.qi-desc{font-size:.68rem;color:var(--text2);line-height:1.7}

/* PROGRESS */
.prog-wrap{margin-bottom:20px}
.prog-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px}
.prog-txt{font-size:.58rem;color:var(--text2);letter-spacing:1px}
.prog-pct{font-size:.62rem;font-weight:800;color:var(--red2)}
.prog-track{height:3px;background:rgba(255,255,255,.07);border-radius:2px;overflow:hidden}
.prog-fill{height:100%;background:linear-gradient(90deg,var(--red2),var(--red-dark));border-radius:2px;transition:width .5s cubic-bezier(.4,0,.2,1)}

/* PERGUNTA CARD */
.pergunta{display:none;flex-direction:column;gap:14px;animation:fadeUp .4s ease}
.pergunta.show{display:flex}
@keyframes fadeUp{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}
.perg-num{font-size:.52rem;font-weight:800;letter-spacing:3px;color:var(--red2);text-transform:uppercase}
.perg-label{font-size:1rem;font-weight:700;color:var(--text);line-height:1.4}
.perg-hint{font-size:.64rem;color:var(--text2);line-height:1.6;background:rgba(255,255,255,.03);border-left:2px solid var(--red);padding:8px 12px;border-radius:0 8px 8px 0}

/* INPUTS */
.finput,.fselect,.ftextarea{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.1);border-radius:12px;padding:13px 15px;color:var(--text);font-family:'Montserrat',sans-serif;font-size:.8rem;transition:border-color .2s,background .2s;width:100%}
.finput:focus,.fselect:focus,.ftextarea:focus{outline:none;border-color:var(--red2);background:rgba(211,47,47,.05)}
.finput::placeholder,.ftextarea::placeholder{color:rgba(255,255,255,.18)}
.fselect{-webkit-appearance:none;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6'%3E%3Cpath d='M0 0l5 5 5-5' stroke='%23FF5252' stroke-width='1.5' fill='none'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 14px center;padding-right:32px;cursor:pointer;background-color:rgba(255,255,255,.04)}
.fselect option{background:#1a0000;color:var(--text)}
.ftextarea{resize:none;height:100px;line-height:1.6}
.frow{display:grid;grid-template-columns:1fr 1fr;gap:10px}

/* OPCOES CLICAVEIS */
.opcoes{display:flex;flex-direction:column;gap:8px}
.opcoes.grid2{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.opcao{border:1px solid rgba(255,255,255,.09);border-radius:12px;padding:12px 14px;background:rgba(255,255,255,.03);cursor:pointer;transition:all .2s;display:flex;align-items:center;gap:10px}
.opcao:hover{border-color:rgba(211,47,47,.35);background:rgba(211,47,47,.05)}
.opcao.sel{border-color:var(--red2);background:rgba(211,47,47,.1)}
.ocheck{width:20px;height:20px;border-radius:50%;border:2px solid rgba(255,255,255,.18);display:flex;align-items:center;justify-content:center;flex-shrink:0;transition:all .2s;font-size:.65rem}
.opcao.sel .ocheck{background:var(--red2);border-color:var(--red2);color:#fff}
.o-icon{font-size:1.1rem;flex-shrink:0}
.o-name{font-size:.78rem;font-weight:600;color:var(--text)}
.o-desc{font-size:.58rem;color:var(--text2);margin-top:1px}

/* FOTO HINT */
.foto-hint{background:rgba(37,211,102,.07);border:1px solid rgba(37,211,102,.3);border-radius:12px;padding:14px;display:flex;gap:10px;align-items:flex-start}
.fh-icon{font-size:1.4rem;flex-shrink:0}
.fh-title{font-size:.72rem;font-weight:800;color:#4CAF50;margin-bottom:3px}
.fh-text{font-size:.62rem;color:rgba(255,255,255,.6);line-height:1.6}

/* BOTÕES NAV */
.nav-btns{display:flex;gap:10px;margin-top:4px}
.btn-prev{flex:1;background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:50px;padding:13px;font-family:'Montserrat',sans-serif;font-weight:700;font-size:.7rem;letter-spacing:1px;color:var(--text2);cursor:pointer;transition:all .2s}
.btn-prev:hover{background:rgba(255,255,255,.09)}
.btn-next{flex:2;background:linear-gradient(135deg,var(--red2),var(--red-dark));border:none;border-radius:50px;padding:13px;font-family:'Montserrat',sans-serif;font-weight:800;font-size:.75rem;letter-spacing:2px;text-transform:uppercase;color:#fff;cursor:pointer;box-shadow:0 6px 22px rgba(211,47,47,.4);transition:transform .2s,box-shadow .2s}
.btn-next:hover{transform:translateY(-2px);box-shadow:0 10px 30px rgba(211,47,47,.6)}

/* RESUMO */
.resumo-box{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:16px;margin-bottom:14px}
.res-title{font-size:.58rem;font-weight:800;letter-spacing:2px;color:var(--red2);text-transform:uppercase;margin-bottom:12px;display:flex;align-items:center;gap:6px}
.res-title::after{content:'';flex:1;height:1px;background:linear-gradient(90deg,rgba(211,47,47,.3),transparent)}
.res-item{display:flex;gap:8px;padding:7px 0;border-bottom:1px solid rgba(255,255,255,.04);align-items:flex-start}
.res-item:last-child{border-bottom:none}
.res-icon{font-size:.9rem;flex-shrink:0;margin-top:1px}
.res-key{font-size:.62rem;color:var(--text2);min-width:110px;flex-shrink:0}
.res-val{font-size:.68rem;color:var(--text);font-weight:600;line-height:1.5}

/* WA BTN */
.btn-wa{width:100%;background:linear-gradient(135deg,#25D366,#128C7E);border:none;border-radius:50px;padding:15px;font-family:'Montserrat',sans-serif;font-weight:800;font-size:.8rem;letter-spacing:1px;color:#fff;cursor:pointer;box-shadow:0 6px 25px rgba(37,211,102,.35);transition:transform .2s,box-shadow .2s;display:flex;align-items:center;justify-content:center;gap:10px;margin-bottom:8px}
.btn-wa:hover{transform:translateY(-2px);box-shadow:0 10px 35px rgba(37,211,102,.5)}
.wa-note{text-align:center;font-size:.58rem;color:var(--text2);letter-spacing:.5px;line-height:1.7}

/* SUCESSO */
.success-screen{display:none;flex-direction:column;align-items:center;text-align:center;padding:40px 20px;gap:12px}
.success-screen.show{display:flex}
.suc-icon{font-size:3.5rem;animation:pop .5s ease}
@keyframes pop{0%{transform:scale(0)}70%{transform:scale(1.2)}100%{transform:scale(1)}}
.suc-title{font-family:'Playfair Display',serif;font-size:1.4rem;font-weight:900;color:var(--red2)}
.suc-sub{font-size:.7rem;color:var(--text2);line-height:1.8;max-width:300px}
.suc-tag{background:rgba(76,175,80,.1);border:1px solid rgba(76,175,80,.3);color:#4CAF50;font-size:.6rem;font-weight:800;letter-spacing:1px;padding:7px 16px;border-radius:50px;text-transform:uppercase}

/* REVIEWS */
.reviews{background:var(--bg2);padding:28px 14px;border-top:1px solid var(--border2)}
.sec-label{font-size:.52rem;font-weight:800;letter-spacing:3px;color:var(--red2);text-transform:uppercase;text-align:center;margin-bottom:5px}
.sec-title{font-family:'Playfair Display',serif;font-size:1.2rem;font-weight:700;color:var(--text);text-align:center;margin-bottom:18px}
.review-grid{display:flex;flex-direction:column;gap:10px;max-width:480px;margin:0 auto}
.rv{background:var(--card);border:1px solid var(--border2);border-radius:14px;padding:14px}
.rv-top{display:flex;align-items:center;gap:10px;margin-bottom:7px}
.rv-av{width:36px;height:36px;border-radius:50%;background:linear-gradient(135deg,var(--red2),var(--red-dark));color:#fff;font-weight:900;font-size:.85rem;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.rv-name{font-size:.76rem;font-weight:700;color:var(--text)}
.rv-date{font-size:.52rem;color:var(--text2)}
.rv-stars{font-size:.68rem;color:#FFD54F;margin-bottom:5px}
.rv-text{font-size:.66rem;color:var(--text2);line-height:1.6;font-style:italic}

/* FOOTER */
footer{background:#050505;border-top:1px solid var(--border);padding:26px 14px;text-align:center}
.ft-logo{font-family:'Playfair Display',serif;font-size:1.2rem;color:var(--red2);margin-bottom:6px}
.ft-info{font-size:.6rem;color:var(--text2);line-height:1.9;margin-bottom:8px}
.ft-copy{font-size:.48rem;color:rgba(255,255,255,.13);letter-spacing:2px}

/* TOAST */
.toast{position:fixed;top:68px;left:50%;transform:translateX(-50%) translateY(-14px);z-index:9998;background:linear-gradient(135deg,rgba(211,47,47,.94),rgba(127,0,0,.94));backdrop-filter:blur(10px);color:#fff;font-weight:700;font-size:.7rem;padding:9px 20px;border-radius:50px;letter-spacing:.5px;opacity:0;pointer-events:none;transition:opacity .3s,transform .3s;white-space:nowrap;box-shadow:0 6px 24px rgba(211,47,47,.4)}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

@media(max-width:360px){.frow{grid-template-columns:1fr}.opcoes.grid2{grid-template-columns:1fr}}
</style>
</head>
<body>

<div id="loading">
  <span class="ld-icon">🚚</span>
  <span class="ld-name">JOÃO MUDANÇAS</span>
  <span class="ld-sub">Seu lar, nossa missão</span>
  <div class="ld-bar"><div class="ld-fill"></div></div>
</div>

<div class="toast" id="toast"></div>

<header>
  <a class="hlogo" href="#">
    <span style="font-size:1.3rem">🚚</span>
    <div>
      <span class="hlogo-name">JOÃO MUDANÇAS</span>
      <span class="hlogo-sub">Desde 2010 · Confiança e Cuidado</span>
    </div>
  </a>
  <div class="open-pill"><div class="open-dot"></div>Aberto</div>
</header>

<!-- HERO -->
<section class="hero">
  <div class="hero-glow"></div>
  <span class="hero-truck">🚚</span>
  <div class="hero-badge">Orçamento 100% Online · Grátis</div>
  <h1 class="hero-title">Sua mudança com <span>segurança</span> e cuidado</h1>
  <p class="hero-desc">Responda algumas perguntas rápidas e receba seu orçamento personalizado pelo WhatsApp em até 2 horas.</p>
  <button class="btn-hero" onclick="document.getElementById('quizSection').scrollIntoView({behavior:'smooth'})">
    📋 Solicitar Orçamento Grátis
  </button>
  <div class="hero-feats">
    <div class="hero-feat">✅ Seguro incluso</div>
    <div class="hero-feat">✅ Equipe treinada</div>
    <div class="hero-feat">✅ Caminhão próprio</div>
    <div class="hero-feat">✅ Retorno em até 2h</div>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stats-inner">
    <div class="stat"><span class="stat-n">+2.400</span><span class="stat-l">Mudanças feitas</span></div>
    <div class="stat-div"></div>
    <div class="stat"><span class="stat-n">98%</span><span class="stat-l">Satisfeitos</span></div>
    <div class="stat-div"></div>
    <div class="stat"><span class="stat-n">14 anos</span><span class="stat-l">No mercado</span></div>
  </div>
</div>

<!-- QUESTIONÁRIO -->
<section id="quizSection">
<div class="quiz-wrapper">

  <div class="quiz-intro">
    <span class="qi-icon">👋</span>
    <div class="qi-title">Olá! Seja bem-vindo à João Mudanças 🚚</div>
    <div class="qi-desc">Será um prazer te atender! Para enviarmos um orçamento <strong>preciso e personalizado</strong>, vamos fazer algumas perguntas rápidas. Leva menos de 3 minutos!</div>
  </div>

  <!-- PROGRESS -->
  <div class="prog-wrap">
    <div class="prog-top">
      <span class="prog-txt" id="progTxt">Pergunta 1 de 7</span>
      <span class="prog-pct" id="progPct">14%</span>
    </div>
    <div class="prog-track"><div class="prog-fill" id="progFill" style="width:14%"></div></div>
  </div>

  <!-- P1: NOME E CONTATO -->
  <div class="pergunta show" id="p1">
    <div class="perg-num">Pergunta 1 de 7</div>
    <div class="perg-label">Qual é o seu nome e WhatsApp? 👤</div>
    <div class="perg-hint">Usaremos para enviar seu orçamento personalizado.</div>
    <input class="finput" id="fNome" placeholder="Seu nome completo">
    <input class="finput" id="fTel" type="tel" placeholder="(22) 99999-9999">
    <div class="nav-btns"><button class="btn-next" onclick="goTo(2)">Próxima →</button></div>
  </div>

  <!-- P2: ENDEREÇOS -->
  <div class="pergunta" id="p2">
    <div class="perg-num">Pergunta 2 de 7</div>
    <div class="perg-label">Qual é o endereço de origem e destino? 📍</div>
    <div class="perg-hint">Informe cidade, bairro e rua. Isso define a distância e o valor do frete.</div>
    <div style="display:flex;flex-direction:column;gap:6px">
      <label style="font-size:.58rem;color:var(--red2);font-weight:800;letter-spacing:1px;text-transform:uppercase">🔴 Origem (de onde sai)</label>
      <textarea class="ftextarea" style="height:70px" id="fOrigem" placeholder="Ex: Rua das Flores, 123 — Bairro Centro — São Paulo / SP"></textarea>
    </div>
    <div style="display:flex;flex-direction:column;gap:6px">
      <label style="font-size:.58rem;color:#4CAF50;font-weight:800;letter-spacing:1px;text-transform:uppercase">🟢 Destino (para onde vai)</label>
      <textarea class="ftextarea" style="height:70px" id="fDestino" placeholder="Ex: Av. Paulista, 500 — Bairro Bela Vista — São Paulo / SP"></textarea>
    </div>
    <div class="nav-btns">
      <button class="btn-prev" onclick="goTo(1)">← Voltar</button>
      <button class="btn-next" onclick="goTo(3)">Próxima →</button>
    </div>
  </div>

  <!-- P3: LISTA DE ITENS + FOTO -->
  <div class="pergunta" id="p3">
    <div class="perg-num">Pergunta 3 de 7</div>
    <div class="perg-label">Quais são os principais itens da mudança? 📦</div>
    <div class="perg-hint">Liste os móveis e objetos mais importantes. Quanto mais detalhado, mais preciso será o orçamento.</div>
    <textarea class="ftextarea" style="height:110px" id="fItens" placeholder="Ex: 1 sofá de 3 lugares, 1 cama box casal, 1 guarda-roupa 6 portas, 1 geladeira duplex, 1 máquina de lavar, TV 55&quot;, 10 caixas de pertences..."></textarea>
    <div class="foto-hint">
      <span class="fh-icon">📸</span>
      <div>
        <div class="fh-title">Dica: Envie fotos e vídeos pelo WhatsApp!</div>
        <div class="fh-text">Após receber sua solicitação, nossa equipe vai entrar em contato. <strong>Já separe fotos ou vídeos dos seus móveis</strong> para enviar na conversa — isso acelera e melhora muito a precisão do orçamento! 😊</div>
      </div>
    </div>
    <div class="nav-btns">
      <button class="btn-prev" onclick="goTo(2)">← Voltar</button>
      <button class="btn-next" onclick="goTo(4)">Próxima →</button>
    </div>
  </div>

  <!-- P4: MONTAGEM -->
  <div class="pergunta" id="p4">
    <div class="perg-num">Pergunta 4 de 7</div>
    <div class="perg-label">Precisa de desmontagem e montagem de móveis? 🔧</div>
    <div class="perg-hint">Se sim, informe quais móveis precisam ser desmontados.</div>
    <div class="opcoes">
      <div class="opcao sel" onclick="selOp(this,'montagem')"><div class="ocheck">✓</div><span class="o-icon">✅</span><div><div class="o-name">Sim, preciso</div><div class="o-desc">Inclua desmontagem e montagem</div></div></div>
      <div class="opcao" onclick="selOp(this,'montagem')"><div class="ocheck"></div><span class="o-icon">❌</span><div><div class="o-name">Não preciso</div><div class="o-desc">Apenas transporte</div></div></div>
      <div class="opcao" onclick="selOp(this,'montagem')"><div class="ocheck"></div><span class="o-icon">🤔</span><div><div class="o-name">Não sei ainda</div><div class="o-desc">Quero consultar antes</div></div></div>
    </div>
    <textarea class="ftextarea" style="height:75px;margin-top:4px" id="fMontagem" placeholder="Quais móveis precisam ser desmontados? Ex: Guarda-roupa 6 portas, cama box, estante..."></textarea>
    <div class="nav-btns">
      <button class="btn-prev" onclick="goTo(3)">← Voltar</button>
      <button class="btn-next" onclick="goTo(5)">Próxima →</button>
    </div>
  </div>

  <!-- P5: VOLUMES EXTRAS -->
  <div class="pergunta" id="p5">
    <div class="perg-num">Pergunta 5 de 7</div>
    <div class="perg-label">Tem caixas, malas, sacolas, plantas ou outros volumes? 🎒</div>
    <div class="perg-hint">Informe a quantidade aproximada para calcularmos o espaço necessário no caminhão.</div>
    <textarea class="ftextarea" id="fVolumes" placeholder="Ex: 15 caixas de papelão médias, 3 malas grandes, 2 plantas grandes, 4 sacolas de roupas..."></textarea>
    <div class="nav-btns">
      <button class="btn-prev" onclick="goTo(4)">← Voltar</button>
      <button class="btn-next" onclick="goTo(6)">Próxima →</button>
    </div>
  </div>

  <!-- P6: ACESSO -->
  <div class="pergunta" id="p6">
    <div class="perg-num">Pergunta 6 de 7</div>
    <div class="perg-label">Como é o acesso nos imóveis? 🏢</div>
    <div class="perg-hint">Informe tanto a origem quanto o destino. Isso afeta o tempo e a equipe necessária.</div>
    <div style="display:flex;flex-direction:column;gap:6px;margin-bottom:4px">
      <label style="font-size:.58rem;color:var(--red2);font-weight:800;letter-spacing:1px;text-transform:uppercase">🔴 Origem</label>
      <div class="opcoes grid2" id="acessoO">
        <div class="opcao sel" onclick="selOp(this,'acessoO')"><div class="ocheck">✓</div><span class="o-icon">🛗</span><div><div class="o-name">Elevador</div></div></div>
        <div class="opcao" onclick="selOp(this,'acessoO')"><div class="ocheck"></div><span class="o-icon">🪜</span><div><div class="o-name">Escada</div></div></div>
        <div class="opcao" onclick="selOp(this,'acessoO')"><div class="ocheck"></div><span class="o-icon">🏠</span><div><div class="o-name">Térreo</div></div></div>
        <div class="opcao" onclick="selOp(this,'acessoO')"><div class="ocheck"></div><span class="o-icon">🤷</span><div><div class="o-name">Não sei</div></div></div>
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:6px">
      <label style="font-size:.58rem;color:#4CAF50;font-weight:800;letter-spacing:1px;text-transform:uppercase">🟢 Destino</label>
      <div class="opcoes grid2" id="acessoD">
        <div class="opcao sel" onclick="selOp(this,'acessoD')"><div class="ocheck">✓</div><span class="o-icon">🛗</span><div><div class="o-name">Elevador</div></div></div>
        <div class="opcao" onclick="selOp(this,'acessoD')"><div class="ocheck"></div><span class="o-icon">🪜</span><div><div class="o-name">Escada</div></div></div>
        <div class="opcao" onclick="selOp(this,'acessoD')"><div class="ocheck"></div><span class="o-icon">🏠</span><div><div class="o-name">Térreo</div></div></div>
        <div class="opcao" onclick="selOp(this,'acessoD')"><div class="ocheck"></div><span class="o-icon">🤷</span><div><div class="o-name">Não sei</div></div></div>
      </div>
    </div>
    <div class="nav-btns">
      <button class="btn-prev" onclick="goTo(5)">← Voltar</button>
      <button class="btn-next" onclick="goTo(7)">Próxima →</button>
    </div>
  </div>

  <!-- P7: DATA -->
  <div class="pergunta" id="p7">
    <div class="perg-num">Pergunta 7 de 7</div>
    <div class="perg-label">Qual é a data prevista para a mudança? 📅</div>
    <div class="perg-hint">Se ainda não tem data certa, selecione uma aproximada ou marque como flexível.</div>
    <input class="finput" id="fData" type="date">
    <div class="opcoes" style="margin-top:4px" id="dataFlex">
      <div class="opcao" onclick="selOp(this,'dataFlex');document.getElementById('fData').value=''"><div class="ocheck"></div><span class="o-icon">📆</span><div><div class="o-name">Data flexível</div><div class="o-desc">Quanto antes, melhor</div></div></div>
      <div class="opcao" onclick="selOp(this,'dataFlex');document.getElementById('fData').value=''"><div class="ocheck"></div><span class="o-icon">⚡</span><div><div class="o-name">Urgente</div><div class="o-desc">Preciso nos próximos dias</div></div></div>
    </div>
    <textarea class="ftextarea" style="height:70px;margin-top:4px" id="fObsGeral" placeholder="Observações extras: acesso difícil, animais de estimação, horário especial, dúvidas..."></textarea>
    <div class="nav-btns">
      <button class="btn-prev" onclick="goTo(6)">← Voltar</button>
      <button class="btn-next" onclick="goResumo()">Ver Resumo ✓</button>
    </div>
  </div>

  <!-- RESUMO -->
  <div class="pergunta" id="pResumo">
    <div class="perg-num">✅ Tudo pronto!</div>
    <div class="perg-label">Confira seu pedido antes de enviar 🔍</div>
    <div class="resumo-box" id="resumoBox"></div>
    <div class="foto-hint" style="margin-bottom:14px">
      <span class="fh-icon">📸</span>
      <div>
        <div class="fh-title">Lembre-se: envie as fotos pelo WhatsApp!</div>
        <div class="fh-text">Após clicar em enviar, <strong>mande fotos ou vídeos dos móveis e itens</strong> diretamente na conversa do WhatsApp. Isso ajuda nossa equipe a dar um orçamento ainda mais preciso! 😊</div>
      </div>
    </div>
    <button class="btn-wa" onclick="sendWA()">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="white"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
      ENVIAR ORÇAMENTO PELO WHATSAPP
    </button>
    <div class="wa-note">
      Você será direcionado ao WhatsApp da João Mudanças<br>
      📸 <strong>Já separe as fotos dos seus móveis</strong> para enviar na conversa!
    </div>
    <div class="nav-btns" style="margin-top:10px"><button class="btn-prev" onclick="goTo(7)">← Editar</button></div>
  </div>

  <!-- SUCESSO -->
  <div class="success-screen" id="successScreen">
    <span class="suc-icon">🎉</span>
    <div class="suc-title">Solicitação Enviada!</div>
    <div class="suc-tag">✅ Orçamento a caminho</div>
    <div class="suc-sub">Sua solicitação foi enviada! Em até <strong>2 horas úteis</strong> nossa equipe vai entrar em contato pelo WhatsApp com seu orçamento personalizado.<br><br>📸 <strong>Não esqueça de enviar as fotos dos seus móveis na conversa!</strong></div>
    <button class="btn-next" style="padding:12px 28px;border-radius:50px;border:none;margin-top:8px" onclick="resetQuiz()">Nova Solicitação</button>
  </div>

</div>
</section>

<!-- REVIEWS -->
<section class="reviews">
  <div class="sec-label">Avaliações</div>
  <div class="sec-title">O que nossos clientes dizem</div>
  <div class="review-grid">
    <div class="rv"><div class="rv-top"><div class="rv-av">M</div><div><div class="rv-name">Marina Alves</div><div class="rv-date">15 de março, 2025</div></div></div><div class="rv-stars">⭐⭐⭐⭐⭐</div><div class="rv-text">"Preenchi o formulário em 5 minutos e em 1 hora já tinha o orçamento no WhatsApp. Equipe pontual, cuidadosa e sem nenhum imprevisto!"</div></div>
    <div class="rv"><div class="rv-top"><div class="rv-av">R</div><div><div class="rv-name">Roberto Fonseca</div><div class="rv-date">2 de fevereiro, 2025</div></div></div><div class="rv-stars">⭐⭐⭐⭐⭐</div><div class="rv-text">"Mudança de 3 quartos com desmontagem de todos os móveis. Tudo impecável. O preço foi o melhor que encontrei!"</div></div>
    <div class="rv"><div class="rv-top"><div class="rv-av">C</div><div><div class="rv-name">Camila Rocha</div><div class="rv-date">10 de janeiro, 2025</div></div></div><div class="rv-stars">⭐⭐⭐⭐⭐</div><div class="rv-text">"Mudança de SP para RJ. Nenhum item danificado. Enviei fotos dos móveis pelo WhatsApp e o orçamento foi certeiro!"</div></div>
  </div>
</section>

<footer>
  <div class="ft-logo">🚚 JOÃO MUDANÇAS</div>
  <div class="ft-info">
    📍 Atendemos todo o Brasil · Sede em São Paulo, SP<br>
    📲 (11) 94000-1234<br>
    🕐 Segunda a Sábado: 7h às 19h · Domingo: 8h às 14h
  </div>
  <div class="ft-copy">© 2025 JOÃO MUDANÇAS · TODOS OS DIREITOS RESERVADOS</div>
</footer>

<script>
let cur=1;const TOTAL=7;

window.addEventListener('load',()=>setTimeout(()=>document.getElementById('loading').classList.add('hide'),2000));

function goTo(n){
  if(n>cur&&!valid(cur))return;
  hide(cur);
  cur=n;
  show(cur);
  updProg(cur);
  document.getElementById('quizSection').scrollIntoView({behavior:'smooth',block:'start'});
}

function goResumo(){
  if(!valid(7))return;
  hide(7);
  buildResumo();
  document.getElementById('pResumo').classList.add('show');
  updProgCustom('✅ Resumo','100%');
  document.getElementById('quizSection').scrollIntoView({behavior:'smooth',block:'start'});
}

function hide(n){
  const el=document.getElementById('p'+n);
  if(el)el.classList.remove('show');
}
function show(n){
  const el=document.getElementById('p'+n);
  if(el){el.classList.remove('show');void el.offsetWidth;el.classList.add('show');}
}
function updProg(n){
  const pct=Math.round((n/TOTAL)*100);
  document.getElementById('progFill').style.width=pct+'%';
  document.getElementById('progTxt').textContent='Pergunta '+n+' de '+TOTAL;
  document.getElementById('progPct').textContent=pct+'%';
}
function updProgCustom(txt,pct){
  document.getElementById('progFill').style.width=pct;
  document.getElementById('progTxt').textContent=txt;
  document.getElementById('progPct').textContent=pct;
}

function valid(n){
  if(n===1){
    if(!document.getElementById('fNome').value.trim()){showToast('⚠️ Informe seu nome');return false;}
    if(!document.getElementById('fTel').value.trim()){showToast('⚠️ Informe seu WhatsApp');return false;}
  }
  if(n===2){
    if(!document.getElementById('fOrigem').value.trim()){showToast('⚠️ Informe o endereço de origem');return false;}
    if(!document.getElementById('fDestino').value.trim()){showToast('⚠️ Informe o endereço de destino');return false;}
  }
  if(n===3){
    if(!document.getElementById('fItens').value.trim()){showToast('⚠️ Liste os principais itens');return false;}
  }
  return true;
}

function selOp(el,grp){
  el.closest('.opcoes').querySelectorAll('.opcao').forEach(o=>{o.classList.remove('sel');o.querySelector('.ocheck').textContent='';});
  el.classList.add('sel');
  el.querySelector('.ocheck').textContent='✓';
}

function getSelLabel(grpId){
  const sel=document.getElementById(grpId)?.querySelector('.opcao.sel .o-name');
  return sel?sel.textContent:'Não informado';
}

function buildResumo(){
  const dt=document.getElementById('fData').value;
  const dtFmt=dt?dt.split('-').reverse().join('/'):'—';
  const dtFlex=document.querySelector('#dataFlex .opcao.sel .o-name');
  const dataFinal=dtFlex?dtFlex.textContent:(dt?dtFmt:'Não informado');
  const items=[
    ['👤','Nome',document.getElementById('fNome').value||'—'],
    ['📲','WhatsApp',document.getElementById('fTel').value||'—'],
    ['🔴','Origem',document.getElementById('fOrigem').value||'—'],
    ['🟢','Destino',document.getElementById('fDestino').value||'—'],
    ['📦','Itens principais',document.getElementById('fItens').value||'—'],
    ['🔧','Montagem/Desmontagem',getSelLabel('p4 .opcoes')],
    ['🎒','Volumes extras',document.getElementById('fVolumes').value||'Não informado'],
    ['🛗','Acesso — Origem',getSelLabel('acessoO')],
    ['🛗','Acesso — Destino',getSelLabel('acessoD')],
    ['📅','Data da mudança',dataFinal],
    ['📝','Observações',document.getElementById('fObsGeral').value||'—'],
  ];
  let html='';
  items.forEach(([ic,k,v])=>{
    html+=`<div class="res-item"><span class="res-icon">${ic}</span><span class="res-key">${k}</span><span class="res-val">${v}</span></div>`;
  });
  document.getElementById('resumoBox').innerHTML='<div class="res-title">📋 Resumo do Pedido</div>'+html;
}

function sendWA(){
  const nm=document.getElementById('fNome').value.trim(),tel=document.getElementById('fTel').value.trim();
  if(!nm||!tel){showToast('⚠️ Dados incompletos');return;}
  const ori=document.getElementById('fOrigem').value||'—';
  const dest=document.getElementById('fDestino').value||'—';
  const itens=document.getElementById('fItens').value||'—';
  const montagemOp=document.querySelector('#p4 .opcoes .opcao.sel .o-name')?.textContent||'—';
  const montagemDet=document.getElementById('fMontagem').value||'—';
  const volumes=document.getElementById('fVolumes').value||'Não informado';
  const acessoO=getSelLabel('acessoO');
  const acessoD=getSelLabel('acessoD');
  const dt=document.getElementById('fData').value;
  const dtFmt=dt?dt.split('-').reverse().join('/'):'—';
  const dtFlex=document.querySelector('#dataFlex .opcao.sel .o-name');
  const dataFinal=dtFlex?dtFlex.textContent:(dt?dtFmt:'Não informado');
  const obs=document.getElementById('fObsGeral').value||'—';

  const msg=`🚚 *SOLICITAÇÃO DE ORÇAMENTO — JOÃO MUDANÇAS*\n━━━━━━━━━━━━━━━━\n\n👤 *CLIENTE*\nNome: ${nm}\nWhatsApp: ${tel}\n\n━━━━━━━━━━━━━━━━\n📍 *ENDEREÇOS*\n🔴 Origem: ${ori}\n🟢 Destino: ${dest}\n\n━━━━━━━━━━━━━━━━\n📦 *ITENS DA MUDANÇA*\n${itens}\n\n🔧 Montagem/Desmontagem: ${montagemOp}\nDetalhes: ${montagemDet}\n\n🎒 Volumes extras: ${volumes}\n\n━━━━━━━━━━━━━━━━\n🏢 *ACESSO*\nOrigem: ${acessoO}\nDestino: ${acessoD}\n\n━━━━━━━━━━━━━━━━\n📅 *DATA DA MUDANÇA*\n${dataFinal}\n\n📝 *OBSERVAÇÕES*\n${obs}\n\n━━━━━━━━━━━━━━━━\n📸 _O cliente foi orientado a enviar fotos e vídeos dos móveis nesta conversa._\n\n_Solicitação via site João Mudanças 🚚_`;

  window.open('https://wa.me/5522992286480?text='+encodeURIComponent(msg),'_blank');
  document.getElementById('pResumo').classList.remove('show');
  document.getElementById('successScreen').classList.add('show');
}

function resetQuiz(){
  document.getElementById('successScreen').classList.remove('show');
  ['fNome','fTel','fOrigem','fDestino','fItens','fMontagem','fVolumes','fData','fObsGeral'].forEach(id=>{
    const el=document.getElementById(id);if(el)el.value='';
  });
  cur=1;show(1);updProg(1);
  document.getElementById('quizSection').scrollIntoView({behavior:'smooth',block:'start'});
}

let tTimer;
function showToast(m){const t=document.getElementById('toast');t.textContent=m;t.classList.add('show');clearTimeout(tTimer);tTimer=setTimeout(()=>t.classList.remove('show'),2500);}
</script>
</body>
</html>
