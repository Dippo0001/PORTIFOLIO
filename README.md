<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Diarley Felipe — Portfólio</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet"/>
<style>
  :root {
    --black:  #080810;
    --deep:   #0e0e1a;
    --purple: #7c3aed;
    --violet: #a855f7;
    --lilac:  #c4b5fd;
    --white:  #f4f0ff;
    --gray:   #9ca3af;
    --border: rgba(124,58,237,0.25);
    --glow:   rgba(124,58,237,0.4);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Mono', monospace;
    font-size: 15px;
    line-height: 1.7;
    cursor: none;
    overflow-x: hidden;
  }

  /* ── CURSOR ────────────────────────────────────────────── */
  #cursor {
    width: 12px; height: 12px;
    background: var(--violet);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.15s ease, opacity 0.2s;
    mix-blend-mode: screen;
  }
  #cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid var(--violet);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9998;
    transition: transform 0.35s ease, opacity 0.2s;
    opacity: 0.5;
  }

  /* ── NOISE OVERLAY ─────────────────────────────────────── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
    opacity: 0.035;
    pointer-events: none;
    z-index: 1000;
  }

  /* ── NAV ───────────────────────────────────────────────── */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 500;
    display: flex; align-items: center; justify-content: space-between;
    padding: 20px 60px;
    background: rgba(8,8,16,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 20px;
    letter-spacing: -0.5px;
    color: var(--white);
  }
  .nav-logo span { color: var(--violet); }
  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a {
    color: var(--gray);
    text-decoration: none;
    font-size: 12px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--violet); }

  /* ── HERO ──────────────────────────────────────────────── */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 140px 60px 80px;
    position: relative;
    overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 60% 50% at 80% 50%, rgba(124,58,237,0.18) 0%, transparent 70%),
      radial-gradient(ellipse 40% 40% at 20% 80%, rgba(168,85,247,0.10) 0%, transparent 60%);
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(124,58,237,0.06) 1px, transparent 1px),
      linear-gradient(90deg, rgba(124,58,237,0.06) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 30%, transparent 100%);
  }
  .hero-content { position: relative; max-width: 820px; }
  .hero-tag {
    display: inline-flex; align-items: center; gap: 8px;
    border: 1px solid var(--border);
    border-radius: 999px;
    padding: 6px 16px;
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--lilac);
    margin-bottom: 32px;
    background: rgba(124,58,237,0.08);
  }
  .hero-tag::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--violet);
    box-shadow: 0 0 8px var(--violet);
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; } 50% { opacity: 0.3; }
  }
  .hero-name {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(48px, 7vw, 88px);
    line-height: 0.95;
    letter-spacing: -2px;
    margin-bottom: 24px;
  }
  .hero-name .line2 {
    color: transparent;
    -webkit-text-stroke: 1px rgba(196,181,253,0.5);
  }
  .hero-name .accent { color: var(--violet); }
  .hero-sub {
    font-family: 'Instrument Serif', serif;
    font-style: italic;
    font-size: clamp(18px, 2.5vw, 26px);
    color: var(--gray);
    margin-bottom: 48px;
    max-width: 540px;
  }
  .hero-ctas { display: flex; gap: 16px; flex-wrap: wrap; }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 10px;
    background: var(--purple);
    color: #fff;
    padding: 14px 32px;
    border-radius: 6px;
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 14px;
    text-decoration: none;
    transition: background 0.2s, box-shadow 0.2s, transform 0.2s;
    border: none; cursor: none;
  }
  .btn-primary:hover {
    background: var(--violet);
    box-shadow: 0 0 32px var(--glow);
    transform: translateY(-2px);
  }
  .btn-ghost {
    display: inline-flex; align-items: center; gap: 10px;
    border: 1px solid var(--border);
    color: var(--lilac);
    padding: 14px 32px;
    border-radius: 6px;
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 14px;
    text-decoration: none;
    transition: border-color 0.2s, color 0.2s, transform 0.2s;
    cursor: none;
  }
  .btn-ghost:hover {
    border-color: var(--violet);
    color: var(--violet);
    transform: translateY(-2px);
  }
  .hero-scroll {
    position: absolute; bottom: 40px; left: 60px;
    display: flex; align-items: center; gap: 12px;
    color: var(--gray); font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase;
  }
  .scroll-line {
    width: 40px; height: 1px;
    background: linear-gradient(90deg, transparent, var(--violet));
    animation: scrollline 2s ease-in-out infinite;
  }
  @keyframes scrollline { 0%,100%{width:40px} 50%{width:70px} }

  /* ── SECTIONS ──────────────────────────────────────────── */
  section { padding: 100px 60px; }
  .section-label {
    font-size: 11px; letter-spacing: 0.15em;
    text-transform: uppercase; color: var(--violet);
    margin-bottom: 12px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::after {
    content: ''; flex: 1; max-width: 60px; height: 1px;
    background: var(--border);
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(32px, 4vw, 52px);
    line-height: 1.05;
    letter-spacing: -1px;
    margin-bottom: 60px;
  }

  /* ── SOBRE ─────────────────────────────────────────────── */
  #sobre { background: var(--deep); border-top: 1px solid var(--border); }
  .sobre-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
  }
  .sobre-text p {
    color: var(--gray);
    font-size: 15px;
    line-height: 1.9;
    margin-bottom: 20px;
  }
  .sobre-text p strong { color: var(--lilac); font-weight: 500; }
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
  }
  .stat-card {
    background: rgba(124,58,237,0.06);
    border: 1px solid var(--border);
    padding: 32px 28px;
    transition: background 0.3s, border-color 0.3s;
  }
  .stat-card:hover {
    background: rgba(124,58,237,0.12);
    border-color: var(--violet);
  }
  .stat-card:first-child { border-radius: 12px 0 0 0; }
  .stat-card:nth-child(2) { border-radius: 0 12px 0 0; }
  .stat-card:nth-child(3) { border-radius: 0 0 0 12px; }
  .stat-card:last-child { border-radius: 0 0 12px 0; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 42px;
    font-weight: 800;
    color: var(--violet);
    line-height: 1;
    margin-bottom: 6px;
  }
  .stat-label { font-size: 12px; color: var(--gray); letter-spacing: 0.05em; }

  /* ── EXPERIÊNCIA ───────────────────────────────────────── */
  #experiencia { background: var(--black); }
  .exp-list { display: flex; flex-direction: column; gap: 2px; }
  .exp-item {
    display: grid;
    grid-template-columns: 200px 1fr;
    gap: 48px;
    padding: 40px 0;
    border-bottom: 1px solid var(--border);
    position: relative;
    transition: background 0.2s;
  }
  .exp-item::before {
    content: '';
    position: absolute; left: -60px; top: 0; bottom: 0; width: 3px;
    background: transparent;
    transition: background 0.3s;
  }
  .exp-item:hover::before { background: var(--violet); }
  .exp-period { color: var(--gray); font-size: 12px; padding-top: 6px; }
  .exp-period strong { display: block; color: var(--lilac); font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; margin-bottom: 4px; }
  .exp-company {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 22px;
    color: var(--white);
    margin-bottom: 4px;
  }
  .exp-role {
    color: var(--violet);
    font-size: 13px;
    margin-bottom: 16px;
    letter-spacing: 0.04em;
  }
  .exp-desc { color: var(--gray); font-size: 14px; line-height: 1.8; }
  .exp-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 16px; }
  .tag {
    background: rgba(124,58,237,0.1);
    border: 1px solid rgba(124,58,237,0.3);
    color: var(--lilac);
    font-size: 11px;
    padding: 4px 12px;
    border-radius: 4px;
    letter-spacing: 0.05em;
  }

  /* ── VIBE CODE ─────────────────────────────────────────── */
  #vibes {
    background: var(--deep);
    border-top: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }
  #vibes::before {
    content: 'VIBE';
    position: absolute;
    right: -20px; top: 50%;
    transform: translateY(-50%);
    font-family: 'Syne', sans-serif;
    font-size: 300px;
    font-weight: 800;
    color: transparent;
    -webkit-text-stroke: 1px rgba(124,58,237,0.06);
    pointer-events: none;
    line-height: 1;
    white-space: nowrap;
  }
  .vibes-intro {
    color: var(--gray);
    font-size: 15px;
    max-width: 600px;
    margin-bottom: 64px;
    line-height: 1.9;
  }
  .vibes-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 24px;
    position: relative;
  }
  .vibe-card {
    background: rgba(8,8,16,0.8);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 32px;
    transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
    position: relative;
    overflow: hidden;
  }
  .vibe-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--violet), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .vibe-card:hover {
    border-color: var(--violet);
    transform: translateY(-6px);
    box-shadow: 0 20px 60px rgba(124,58,237,0.2);
  }
  .vibe-card:hover::before { opacity: 1; }
  .vibe-icon {
    width: 48px; height: 48px;
    background: rgba(124,58,237,0.15);
    border: 1px solid var(--border);
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    margin-bottom: 20px;
  }
  .vibe-card h3 {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 18px;
    color: var(--white);
    margin-bottom: 10px;
  }
  .vibe-card p { color: var(--gray); font-size: 13px; line-height: 1.8; }
  .vibe-placeholder {
    border: 2px dashed rgba(124,58,237,0.25);
    border-radius: 12px;
    padding: 32px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    min-height: 200px;
    gap: 12px;
    transition: border-color 0.3s;
  }
  .vibe-placeholder:hover { border-color: var(--violet); }
  .vibe-placeholder .plus {
    width: 40px; height: 40px;
    border: 1px solid var(--border);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 20px; color: var(--violet);
  }
  .vibe-placeholder span { color: var(--gray); font-size: 12px; letter-spacing: 0.08em; text-transform: uppercase; }

  /* ── GITHUB ────────────────────────────────────────────── */
  #github {
    background: var(--black);
    border-top: 1px solid var(--border);
  }
  .github-box {
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 60px;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 48px;
    align-items: center;
    background: rgba(124,58,237,0.04);
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s;
  }
  .github-box:hover { border-color: rgba(124,58,237,0.5); }
  .github-box::after {
    content: '';
    position: absolute;
    bottom: -60px; right: -60px;
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(124,58,237,0.15), transparent 70%);
  }
  .github-left h2 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 32px;
    margin-bottom: 12px;
  }
  .github-left p { color: var(--gray); font-size: 14px; line-height: 1.8; max-width: 480px; }
  .github-url {
    display: flex; align-items: center; gap: 10px;
    margin-top: 20px;
    background: rgba(124,58,237,0.08);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 20px;
    font-size: 13px;
    color: var(--lilac);
    font-family: 'DM Mono', monospace;
  }
  .github-url .dot { width: 8px; height: 8px; border-radius: 50%; background: var(--violet); box-shadow: 0 0 8px var(--violet); }
  .github-url input {
    background: transparent;
    border: none;
    outline: none;
    color: var(--lilac);
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    width: 260px;
  }
  .github-right { text-align: center; }
  .gh-logo {
    width: 100px; height: 100px;
    background: rgba(124,58,237,0.1);
    border: 1px solid var(--border);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 16px;
    font-size: 48px;
    transition: background 0.3s, box-shadow 0.3s;
  }
  .github-box:hover .gh-logo {
    background: rgba(124,58,237,0.2);
    box-shadow: 0 0 40px var(--glow);
  }
  .gh-open {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--purple);
    color: #fff;
    padding: 12px 28px;
    border-radius: 6px;
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 14px;
    text-decoration: none;
    transition: background 0.2s, box-shadow 0.2s;
    cursor: none;
    border: none;
  }
  .gh-open:hover { background: var(--violet); box-shadow: 0 0 24px var(--glow); }

  /* ── COMPETÊNCIAS ──────────────────────────────────────── */
  #skills-sec { background: var(--deep); border-top: 1px solid var(--border); }
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 16px;
  }
  .skill-pill {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 20px 24px;
    display: flex; align-items: center; gap: 14px;
    transition: border-color 0.3s, background 0.3s;
    background: rgba(124,58,237,0.03);
  }
  .skill-pill:hover {
    border-color: var(--violet);
    background: rgba(124,58,237,0.1);
  }
  .skill-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--violet); flex-shrink: 0; }
  .skill-name { font-size: 13px; color: var(--white); }

  /* ── CONTATO ───────────────────────────────────────────── */
  #contato {
    background: var(--black);
    border-top: 1px solid var(--border);
    text-align: center;
  }
  #contato .section-title { margin-bottom: 20px; }
  #contato p { color: var(--gray); margin-bottom: 40px; font-size: 15px; }
  .contact-links { display: flex; justify-content: center; gap: 16px; flex-wrap: wrap; }
  .contact-link {
    display: inline-flex; align-items: center; gap: 10px;
    border: 1px solid var(--border);
    color: var(--lilac);
    padding: 14px 28px;
    border-radius: 8px;
    text-decoration: none;
    font-size: 13px;
    transition: border-color 0.2s, color 0.2s, background 0.2s;
    cursor: none;
  }
  .contact-link:hover {
    border-color: var(--violet);
    color: var(--violet);
    background: rgba(124,58,237,0.08);
  }

  /* ── FOOTER ────────────────────────────────────────────── */
  footer {
    border-top: 1px solid var(--border);
    padding: 32px 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: var(--gray);
    font-size: 12px;
    background: var(--deep);
  }
  footer span { color: var(--violet); }

  /* ── SCROLL REVEAL ─────────────────────────────────────── */
  .reveal {
    opacity: 0;
    transform: translateY(32px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── RESPONSIVE ────────────────────────────────────────── */
  @media (max-width: 768px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    section { padding: 70px 24px; }
    #hero { padding: 120px 24px 60px; }
    .sobre-grid { grid-template-columns: 1fr; }
    .exp-item { grid-template-columns: 1fr; gap: 8px; }
    .github-box { grid-template-columns: 1fr; padding: 36px 24px; }
    .github-right { display: none; }
    footer { flex-direction: column; gap: 8px; text-align: center; }
    .hero-scroll { display: none; }
  }
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- ── NAV ── -->
<nav>
  <div class="nav-logo">D<span>.</span>Felipe</div>
  <ul class="nav-links">
    <li><a href="#sobre">Sobre</a></li>
    <li><a href="#experiencia">Experiência</a></li>
    <li><a href="#vibes">Vibe Code</a></li>
    <li><a href="#github">GitHub</a></li>
    <li><a href="#contato">Contato</a></li>
  </ul>
</nav>

<!-- ── HERO ── -->
<section id="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>
  <div class="hero-content">
    <div class="hero-tag">Disponível para novas oportunidades</div>
    <h1 class="hero-name">
      DIARLEY<br>
      <span class="line2">FELIPE</span><br>
      <span class="accent">DUARTE</span>
    </h1>
    <p class="hero-sub">Supervisor de Cadastro & TI · Analista de TI · Vibe Coder</p>
    <div class="hero-ctas">
      <a href="#vibes" class="btn-primary">Ver Projetos ↓</a>
      <a href="#contato" class="btn-ghost">Entrar em contato</a>
    </div>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    scroll
  </div>
</section>

<!-- ── SOBRE ── -->
<section id="sobre">
  <div class="section-label">01 — Sobre</div>
  <div class="sobre-grid">
    <div class="sobre-text reveal">
      <h2 class="section-title">Quem sou<br><em style="font-family:'Instrument Serif',serif;font-weight:400;color:var(--lilac)">eu.</em></h2>
      <p>Tenho 22 anos e iniciei minha trajetória profissional aos 18. Comecei como <strong>Auxiliar de E-commerce</strong> na Shopee e evoluí para <strong>Supervisor de Cadastro e TI</strong> no Grupo New — holding formada pelas marcas Newshop, Soye e Facilatacado.</p>
      <p>Ao longo dessa jornada, acumulei experiência em <strong>ERPs, apuração fiscal, gestão de equipes</strong> e automação de processos. Hoje, também exploro o mundo do <strong>Vibe Code</strong> — criando soluções e ferramentas com IA.</p>
      <p>Cursando <strong>Ciências Contábeis</strong> pela UNIASSELVI, com visão híbrida entre tecnologia, dados e gestão.</p>
    </div>
    <div class="stats-grid reveal">
      <div class="stat-card">
        <div class="stat-num">4+</div>
        <div class="stat-label">Anos de experiência</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">7</div>
        <div class="stat-label">Pessoas lideradas</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">5+</div>
        <div class="stat-label">ERPs utilizados</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">3</div>
        <div class="stat-label">Marcas do Grupo New</div>
      </div>
    </div>
  </div>
</section>

<!-- ── EXPERIÊNCIA ── -->
<section id="experiencia">
  <div class="section-label">02 — Carreira</div>
  <h2 class="section-title reveal">Experiência<br>Profissional</h2>
  <div class="exp-list">

    <div class="exp-item reveal">
      <div class="exp-period">
        <strong>Atual</strong>
        2024 — Hoje
      </div>
      <div>
        <div class="exp-company">Newshop & Fácil Atacado</div>
        <div class="exp-role">Supervisor de Cadastro e TI · Grupo New</div>
        <div class="exp-desc">Liderança de equipe com 7 colaboradores. Validação de cadastros, apuração de ICMS, PIS e COFINS, geração do SPED Fiscal e gestão de notas fiscais de entrada, saída e transferência. Suporte de TI, manutenção preventiva e implantação de sistemas ERP.</div>
        <div class="exp-tags">
          <span class="tag">VarejoFácil</span>
          <span class="tag">SPED Fiscal</span>
          <span class="tag">ICMS · PIS · COFINS</span>
          <span class="tag">Liderança</span>
          <span class="tag">Suporte TI</span>
        </div>
      </div>
    </div>

    <div class="exp-item reveal">
      <div class="exp-period">
        <strong>Anterior</strong>
        Set/2023 — Out/2024
      </div>
      <div>
        <div class="exp-company">Fortal Shopee</div>
        <div class="exp-role">Auxiliar de E-commerce</div>
        <div class="exp-desc">Cadastro e otimização de produtos, tratamento de fotos, criação de títulos e descrições com foco em SEO. Atendimento via chat, campanhas Shopee ADS e acompanhamento de metas de vendas.</div>
        <div class="exp-tags">
          <span class="tag">Shopee ADS</span>
          <span class="tag">SEO</span>
          <span class="tag">Cadastro</span>
          <span class="tag">Chat</span>
          <span class="tag">Metas</span>
        </div>
      </div>
    </div>

    <div class="exp-item reveal">
      <div class="exp-period">
        <strong>Início</strong>
        Set/2022 — 2024
      </div>
      <div>
        <div class="exp-company">Grupo New</div>
        <div class="exp-role">Colaborador de Cadastro · Evolução para Supervisor</div>
        <div class="exp-desc">Trabalhei com ERPs como Bling, Olist Tiny, Microvix (Linx) e Omie. Participei de implantações de sistemas e automação de processos internos, construindo base sólida para assumir a supervisão.</div>
        <div class="exp-tags">
          <span class="tag">Bling</span>
          <span class="tag">Olist Tiny</span>
          <span class="tag">Microvix</span>
          <span class="tag">Omie</span>
          <span class="tag">Implantação ERP</span>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- ── VIBE CODE ── -->
<section id="vibes">
  <div class="section-label">03 — Projetos</div>
  <h2 class="section-title reveal">Vibe Code<br><em style="font-family:'Instrument Serif',serif;font-weight:400;color:var(--lilac)">&amp; Soluções</em></h2>
  <p class="vibes-intro reveal">Aqui ficam os projetos que criei com IA, automações e ferramentas que resolvi construir do zero. Cada card é uma solução real para um problema real.</p>

  <div class="vibes-grid">

    <!-- Adicione seus projetos aqui -->
    <div class="vibe-placeholder reveal">
      <div class="plus">+</div>
      <span>Seu projeto aqui</span>
      <p style="color:var(--gray);font-size:12px;max-width:200px;text-align:center">Edite o HTML para adicionar seu primeiro projeto Vibe Code</p>
    </div>

    <div class="vibe-placeholder reveal">
      <div class="plus">+</div>
      <span>Em breve</span>
      <p style="color:var(--gray);font-size:12px;max-width:200px;text-align:center">Mais soluções sendo desenvolvidas</p>
    </div>

    <div class="vibe-placeholder reveal">
      <div class="plus">+</div>
      <span>Em breve</span>
      <p style="color:var(--gray);font-size:12px;max-width:200px;text-align:center">Mais soluções sendo desenvolvidas</p>
    </div>

  </div>

  <!-- EXEMPLO DE CARD (descomente para usar):
  <div class="vibe-card reveal">
    <div class="vibe-icon">⚡</div>
    <h3>Nome do Projeto</h3>
    <p>Descrição breve do que faz, qual problema resolve e qual tecnologia usou.</p>
  </div>
  -->

</section>

<!-- ── GITHUB ── -->
<section id="github">
  <div class="section-label">04 — Código</div>
  <h2 class="section-title reveal">GitHub</h2>
  <div class="github-box reveal">
    <div class="github-left">
      <h2>Meu repositório</h2>
      <p>Acesse meu GitHub para ver os projetos que estou desenvolvendo, experimentos com IA e automações. Cole o link do seu perfil abaixo.</p>
      <div class="github-url">
        <div class="dot"></div>
        <input type="text" id="ghInput" value="github.com/seu-usuario" placeholder="github.com/seu-usuario"/>
        <button onclick="openGh()" style="background:var(--purple);border:none;color:#fff;padding:6px 14px;border-radius:4px;font-size:12px;cursor:pointer;font-family:'Syne',sans-serif;font-weight:600">Ir ↗</button>
      </div>
    </div>
    <div class="github-right">
      <div class="gh-logo">🐙</div>
      <button class="gh-open" onclick="openGh()">Abrir GitHub ↗</button>
    </div>
  </div>
</section>

<!-- ── SKILLS ── -->
<section id="skills-sec">
  <div class="section-label">05 — Competências</div>
  <h2 class="section-title reveal">Stack &<br>Ferramentas</h2>
  <div class="skills-grid">
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Bling ERP</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Olist Tiny</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Microvix (Linx)</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Omie</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">VarejoFácil</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">SPED Fiscal</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">ICMS · PIS · COFINS</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">NF-e (Entrada/Saída)</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Shopee ADS</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">SEO E-commerce</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Gestão de Equipes</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Suporte TI</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Vibe Coding / IA</span></div>
    <div class="skill-pill reveal"><div class="skill-dot"></div><span class="skill-name">Automação de Processos</span></div>
  </div>
</section>

<!-- ── CONTATO ── -->
<section id="contato">
  <div class="section-label" style="justify-content:center">06 — Contato</div>
  <h2 class="section-title reveal">Bora<br><em style="font-family:'Instrument Serif',serif;font-weight:400;color:var(--lilac)">conversar?</em></h2>
  <p class="reveal">Aberto a oportunidades, projetos e colaborações. Chama!</p>
  <div class="contact-links reveal">
    <a href="mailto:diarleyduarte17@gmail.com" class="contact-link">✉ diarleyduarte17@gmail.com</a>
    <a href="tel:+5585992019010" class="contact-link">📞 (85) 99201-9010</a>
    <a href="https://www.linkedin.com/in/diarley-duarte-439393309/" target="_blank" class="contact-link">💼 LinkedIn</a>
  </div>
</section>

<!-- ── FOOTER ── -->
<footer>
  <div>© 2025 <span>Diarley Felipe Duarte Lima</span></div>
  <div>Feito com <span>♥</span> & Vibe Code</div>
</footer>

<script>
  // ── Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursor-ring');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animCursor() {
    cursor.style.transform = `translate(${mx - 6}px, ${my - 6}px)`;
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.transform = `translate(${rx - 18}px, ${ry - 18}px)`;
    requestAnimationFrame(animCursor);
  }
  animCursor();

  // ── Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));

  // ── GitHub open
  function openGh() {
    let url = document.getElementById('ghInput').value.trim();
    if (!url.startsWith('http')) url = 'https://' + url;
    window.open(url, '_blank');
  }
  document.getElementById('ghInput').addEventListener('keydown', e => {
    if (e.key === 'Enter') openGh();
  });
</script>
</body>
</html>
