<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Abhinav Maurya — Java Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;700;800&family=DM+Mono:ital,wght@0,400;0,500;1,400&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #060810;
    --bg2: #0c1020;
    --bg3: #111827;
    --surface: rgba(255,255,255,0.04);
    --surface2: rgba(255,255,255,0.07);
    --border: rgba(255,255,255,0.08);
    --border2: rgba(255,255,255,0.14);
    --sky: #38bdf8;
    --violet: #a78bfa;
    --indigo: #6366f1;
    --emerald: #34d399;
    --rose: #fb7185;
    --amber: #fbbf24;
    --text: #f1f5f9;
    --muted: #64748b;
    --muted2: #94a3b8;
    --font-display: 'Syne', sans-serif;
    --font-body: 'Outfit', sans-serif;
    --font-mono: 'DM Mono', monospace;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── NOISE GRAIN OVERLAY ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.6;
  }

  /* ── AMBIENT GLOW ORBS ── */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
    opacity: 0.18;
  }
  .orb-1 { width: 600px; height: 600px; background: var(--sky); top: -200px; left: -200px; animation: drift1 18s ease-in-out infinite; }
  .orb-2 { width: 500px; height: 500px; background: var(--violet); bottom: -150px; right: -150px; animation: drift2 22s ease-in-out infinite; }
  .orb-3 { width: 350px; height: 350px; background: var(--indigo); top: 40%; left: 50%; transform: translate(-50%,-50%); animation: drift3 15s ease-in-out infinite; }

  @keyframes drift1 { 0%,100%{transform:translate(0,0)} 50%{transform:translate(60px,40px)} }
  @keyframes drift2 { 0%,100%{transform:translate(0,0)} 50%{transform:translate(-50px,-60px)} }
  @keyframes drift3 { 0%,100%{transform:translate(-50%,-50%)} 50%{transform:translate(-44%,-56%)} }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--indigo); border-radius: 2px; }

  /* ── LAYOUT ── */
  .wrap { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 0 28px; }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 18px 0;
    background: rgba(6,8,16,0.7);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    transition: all 0.3s;
  }
  nav .inner { max-width: 900px; margin: 0 auto; padding: 0 28px; display: flex; align-items: center; justify-content: space-between; }
  .nav-logo { font-family: var(--font-display); font-weight: 800; font-size: 18px; letter-spacing: -0.5px; background: linear-gradient(135deg, var(--sky), var(--violet)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .nav-links { display: flex; gap: 28px; }
  .nav-links a { font-size: 13px; font-weight: 500; color: var(--muted2); text-decoration: none; letter-spacing: 0.03em; transition: color 0.2s; }
  .nav-links a:hover { color: var(--text); }

  /* ── HERO ── */
  #hero { padding: 160px 0 100px; }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--surface); border: 1px solid var(--border2);
    border-radius: 100px; padding: 7px 16px 7px 10px;
    font-size: 12px; font-weight: 500; color: var(--muted2);
    margin-bottom: 32px; letter-spacing: 0.04em;
  }
  .badge-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--emerald); animation: pulse-dot 2s ease-in-out infinite; }
  @keyframes pulse-dot { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.6;transform:scale(0.8)} }

  .hero-name {
    font-family: var(--font-display);
    font-size: clamp(52px, 9vw, 84px);
    font-weight: 800;
    line-height: 1.0;
    letter-spacing: -2px;
    background: linear-gradient(135deg, #ffffff 0%, #94a3b8 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
    margin-bottom: 12px;
  }
  .hero-name span {
    background: linear-gradient(135deg, var(--sky) 0%, var(--violet) 50%, var(--indigo) 100%);
    -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent;
  }

  .hero-title {
    font-family: var(--font-display);
    font-size: clamp(18px, 3vw, 26px);
    font-weight: 500;
    color: var(--muted2);
    letter-spacing: -0.3px;
    margin-bottom: 28px;
  }
  .hero-title .accent { color: var(--sky); }

  .hero-desc { max-width: 560px; color: var(--muted2); font-size: 16px; line-height: 1.8; margin-bottom: 44px; }

  .hero-cta { display: flex; gap: 14px; flex-wrap: wrap; }
  .btn-primary {
    display: inline-flex; align-items: center; gap: 8px;
    background: linear-gradient(135deg, var(--indigo), var(--violet));
    color: #fff; font-family: var(--font-body); font-weight: 600;
    font-size: 14px; padding: 12px 24px; border-radius: 10px;
    text-decoration: none; border: none; cursor: pointer;
    transition: all 0.25s; letter-spacing: 0.01em;
    position: relative; overflow: hidden;
  }
  .btn-primary::after { content:''; position:absolute; inset:0; background:rgba(255,255,255,0.1); opacity:0; transition:opacity 0.2s; }
  .btn-primary:hover::after { opacity:1; }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 12px 40px rgba(99,102,241,0.4); }

  .btn-ghost {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--surface); border: 1px solid var(--border2);
    color: var(--muted2); font-family: var(--font-body); font-weight: 500;
    font-size: 14px; padding: 12px 24px; border-radius: 10px;
    text-decoration: none; cursor: pointer;
    transition: all 0.25s; letter-spacing: 0.01em;
  }
  .btn-ghost:hover { color: var(--text); border-color: var(--violet); background: rgba(167,139,250,0.08); transform: translateY(-1px); }

  .hero-scroll { margin-top: 80px; display: flex; align-items: center; gap: 16px; }
  .scroll-line { height: 1px; width: 60px; background: var(--border2); }
  .scroll-text { font-size: 11px; color: var(--muted); letter-spacing: 0.1em; text-transform: uppercase; }

  /* ── CODE BLOCK ── */
  .code-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
    margin-top: 60px;
  }
  .code-header {
    display: flex; align-items: center; gap: 8px;
    padding: 12px 18px;
    border-bottom: 1px solid var(--border);
    background: rgba(255,255,255,0.02);
  }
  .dot-red { width: 12px; height: 12px; border-radius: 50%; background: #ff5f57; }
  .dot-yellow { width: 12px; height: 12px; border-radius: 50%; background: #febc2e; }
  .dot-green { width: 12px; height: 12px; border-radius: 50%; background: #28c840; }
  .code-filename { margin-left: auto; font-family: var(--font-mono); font-size: 11px; color: var(--muted); }
  .code-body { padding: 24px 28px; font-family: var(--font-mono); font-size: 13px; line-height: 1.9; overflow-x: auto; }
  .c-key { color: var(--violet); }
  .c-str { color: var(--emerald); }
  .c-arr { color: var(--sky); }
  .c-val { color: var(--amber); }
  .c-muted { color: var(--muted); }
  .c-comment { color: #475569; font-style: italic; }

  /* ── SECTION ── */
  section { padding: 100px 0; }
  .section-label {
    display: inline-flex; align-items: center; gap: 10px;
    font-size: 11px; font-weight: 600; letter-spacing: 0.12em;
    text-transform: uppercase; color: var(--violet);
    margin-bottom: 16px;
  }
  .section-label::before { content:''; display:block; width:24px; height:1px; background:var(--violet); }
  .section-title {
    font-family: var(--font-display);
    font-size: clamp(32px, 5vw, 48px);
    font-weight: 700;
    letter-spacing: -1px;
    line-height: 1.1;
    margin-bottom: 48px;
    color: var(--text);
  }
  .section-title em { font-style: normal; background: linear-gradient(135deg, var(--sky), var(--violet)); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; }

  /* ── DIVIDER ── */
  .divider { height: 1px; background: linear-gradient(90deg, transparent, var(--border2), transparent); margin: 0; }

  /* ── TECH STACK ── */
  .tech-grid { display: flex; flex-wrap: wrap; gap: 12px; }
  .tech-pill {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 100px;
    padding: 9px 18px;
    font-size: 13px; font-weight: 500; color: var(--muted2);
    transition: all 0.25s;
    cursor: default;
  }
  .tech-pill:hover {
    color: var(--text); border-color: var(--border2);
    background: var(--surface2); transform: translateY(-2px);
  }
  .tech-pill .icon { font-size: 16px; }

  .tech-category { margin-bottom: 40px; }
  .tech-cat-label { font-size: 11px; font-weight: 600; letter-spacing: 0.1em; text-transform: uppercase; color: var(--muted); margin-bottom: 14px; }

  /* ── CERTS ── */
  .cert-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 16px; }
  .cert-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px 24px;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .cert-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--sky), var(--violet));
    opacity: 0;
    transition: opacity 0.3s;
  }
  .cert-card:hover { border-color: var(--border2); transform: translateY(-3px); box-shadow: 0 20px 60px rgba(0,0,0,0.4); }
  .cert-card:hover::before { opacity: 1; }
  .cert-icon { font-size: 26px; margin-bottom: 14px; }
  .cert-name { font-family: var(--font-display); font-size: 15px; font-weight: 700; color: var(--text); margin-bottom: 6px; }
  .cert-platform { font-size: 12px; color: var(--muted); font-weight: 500; letter-spacing: 0.04em; }

  /* ── PROJECTS ── */
  .project-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
  @media(max-width:600px){ .project-grid{ grid-template-columns:1fr; } }
  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .project-card:hover { border-color: var(--border2); transform: translateY(-4px); box-shadow: 0 24px 70px rgba(0,0,0,0.5); }
  .project-emoji { font-size: 32px; margin-bottom: 18px; display: block; }
  .project-name { font-family: var(--font-display); font-size: 18px; font-weight: 700; color: var(--text); margin-bottom: 10px; }
  .project-desc { font-size: 14px; color: var(--muted2); line-height: 1.7; }
  .project-tag {
    display: inline-block; margin-top: 18px;
    background: rgba(99,102,241,0.15); border: 1px solid rgba(99,102,241,0.3);
    color: #a5b4fc; font-size: 11px; font-weight: 600; letter-spacing: 0.07em;
    text-transform: uppercase; padding: 4px 12px; border-radius: 100px;
  }

  /* ── CONNECT ── */
  .connect-grid { display: flex; gap: 16px; flex-wrap: wrap; }
  .social-card {
    display: inline-flex; align-items: center; gap: 12px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px 22px;
    text-decoration: none;
    color: var(--muted2);
    font-size: 14px; font-weight: 500;
    transition: all 0.25s;
    flex: 1; min-width: 180px;
  }
  .social-card:hover { color: var(--text); border-color: var(--border2); transform: translateY(-2px); background: var(--surface2); }
  .social-icon { font-size: 20px; }

  /* ── STATS ── */
  .stats-row { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 16px; margin-bottom: 48px; }
  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px 20px;
    text-align: center;
    transition: all 0.3s;
  }
  .stat-card:hover { border-color: var(--border2); transform: translateY(-3px); }
  .stat-num { font-family: var(--font-display); font-size: 36px; font-weight: 800; letter-spacing: -1px; background: linear-gradient(135deg, var(--sky), var(--violet)); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; }
  .stat-label { font-size: 12px; color: var(--muted); font-weight: 500; letter-spacing: 0.06em; text-transform: uppercase; margin-top: 6px; }

  /* ── FOOTER ── */
  footer {
    padding: 60px 0 40px;
    border-top: 1px solid var(--border);
    text-align: center;
  }
  .footer-logo { font-family: var(--font-display); font-size: 22px; font-weight: 800; background: linear-gradient(135deg, var(--sky), var(--violet)); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; margin-bottom: 12px; }
  .footer-sub { font-size: 13px; color: var(--muted); }
  .footer-tagline { margin-top: 32px; font-family: var(--font-mono); font-size: 13px; color: var(--muted); letter-spacing: 0.04em; }
  .footer-tagline span { color: var(--sky); }

  /* ── ANIMATIONS ── */
  .fade-up {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .fade-up.visible { opacity: 1; transform: translateY(0); }

  @media(max-width:768px){
    .nav-links { display: none; }
    #hero { padding: 120px 0 80px; }
  }
</style>
</head>
<body>

<!-- Ambient Orbs -->
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<!-- Navigation -->
<nav>
  <div class="inner">
    <div class="nav-logo">AM</div>
    <div class="nav-links">
      <a href="#about">About</a>
      <a href="#stack">Stack</a>
      <a href="#projects">Projects</a>
      <a href="#certs">Certs</a>
      <a href="#connect">Connect</a>
    </div>
  </div>
</nav>

<!-- Hero -->
<div class="wrap">
  <section id="hero">
    <div class="hero-badge fade-up">
      <span class="badge-dot"></span>
      Available for opportunities · India 🇮🇳
    </div>

    <h1 class="hero-name fade-up">
      Abhinav<br/><span>Maurya</span>
    </h1>

    <p class="hero-title fade-up">
      Java Full Stack Developer <span class="accent">·</span> PHP <span class="accent">·</span> WordPress <span class="accent">·</span> UI/UX
    </p>

    <p class="hero-desc fade-up">
      Building modern digital experiences through clean code, thoughtful UI, and performant backends.
      Currently leveling up with React, Node.js, and MongoDB.
    </p>

    <div class="hero-cta fade-up">
      <a href="https://github.com/abhinavmaurya12" target="_blank" class="btn-primary">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>
        GitHub Profile
      </a>
      <a href="https://www.linkedin.com/in/abhinav-maurya-25162b338" target="_blank" class="btn-ghost">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
    </div>

    <div class="hero-scroll fade-up">
      <div class="scroll-line"></div>
      <span class="scroll-text">Scroll to explore</span>
    </div>
  </section>
</div>

<div class="divider"></div>

<!-- About Code Block -->
<div class="wrap">
  <section id="about">
    <div class="section-label fade-up">About Me</div>
    <h2 class="section-title fade-up">Developer <em>Profile</em></h2>

    <div class="code-card fade-up">
      <div class="code-header">
        <div class="dot-red"></div>
        <div class="dot-yellow"></div>
        <div class="dot-green"></div>
        <span class="code-filename">abhinav_maurya.js</span>
      </div>
      <div class="code-body">
<span class="c-key">const</span> <span style="color:var(--sky)">abhinav_maurya</span> = {<br/>
&nbsp;&nbsp;<span class="c-key">role:</span> <span class="c-str">"Java Full Stack Developer"</span>,<br/>
&nbsp;&nbsp;<span class="c-key">location:</span> <span class="c-str">"India 🇮🇳"</span>,<br/>
<br/>
&nbsp;&nbsp;<span class="c-key">currentlyLearning:</span> [<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"Advanced Java"</span>, <span class="c-str">"React"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"Node.js"</span>, <span class="c-str">"MongoDB"</span><br/>
&nbsp;&nbsp;],<br/>
<br/>
&nbsp;&nbsp;<span class="c-key">expertise:</span> [<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"Frontend Development"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"Backend Development"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"UI/UX Design"</span>,<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"SEO Optimization"</span><br/>
&nbsp;&nbsp;],<br/>
<br/>
&nbsp;&nbsp;<span class="c-key">techStack:</span> {<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">frontend:</span> [<span class="c-str">"HTML"</span>, <span class="c-str">"CSS"</span>, <span class="c-str">"JavaScript"</span>],<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">backend:</span> [<span class="c-str">"PHP"</span>, <span class="c-str">"Java"</span>],<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">database:</span> [<span class="c-str">"MySQL"</span>],<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-key">cms:</span> [<span class="c-str">"WordPress"</span>]<br/>
&nbsp;&nbsp;},<br/>
<br/>
&nbsp;&nbsp;<span class="c-key">hobbies:</span> [<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-str">"Coding 💻"</span>, <span class="c-str">"Gaming 🎮"</span>, <span class="c-str">"Tech Exploration 🚀"</span><br/>
&nbsp;&nbsp;]<br/>
};<br/>
<br/>
<span class="c-comment">// Code • Create • Innovate • Repeat</span>
      </div>
    </div>
  </section>
</div>

<div class="divider"></div>

<!-- Tech Stack -->
<div class="wrap">
  <section id="stack">
    <div class="section-label fade-up">Technologies</div>
    <h2 class="section-title fade-up">Tech <em>Stack</em></h2>

    <div class="tech-category fade-up">
      <div class="tech-cat-label">Frontend</div>
      <div class="tech-grid">
        <div class="tech-pill"><span class="icon">🌐</span> HTML5</div>
        <div class="tech-pill"><span class="icon">🎨</span> CSS3</div>
        <div class="tech-pill"><span class="icon">⚡</span> JavaScript</div>
        <div class="tech-pill"><span class="icon">🔷</span> UI / UX Design</div>
      </div>
    </div>

    <div class="tech-category fade-up">
      <div class="tech-cat-label">Backend</div>
      <div class="tech-grid">
        <div class="tech-pill"><span class="icon">☕</span> Java</div>
        <div class="tech-pill"><span class="icon">🐘</span> PHP</div>
        <div class="tech-pill"><span class="icon">🔧</span> WordPress</div>
      </div>
    </div>

    <div class="tech-category fade-up">
      <div class="tech-cat-label">Database & Tools</div>
      <div class="tech-grid">
        <div class="tech-pill"><span class="icon">🗄️</span> MySQL</div>
        <div class="tech-pill"><span class="icon">🐙</span> GitHub</div>
        <div class="tech-pill"><span class="icon">💻</span> VS Code</div>
        <div class="tech-pill"><span class="icon">📈</span> SEO Optimization</div>
      </div>
    </div>

    <div class="tech-category fade-up">
      <div class="tech-cat-label">Currently Learning</div>
      <div class="tech-grid">
        <div class="tech-pill" style="border-color:rgba(56,189,248,0.3);color:var(--sky)"><span class="icon">⚛️</span> React</div>
        <div class="tech-pill" style="border-color:rgba(52,211,153,0.3);color:var(--emerald)"><span class="icon">🟢</span> Node.js</div>
        <div class="tech-pill" style="border-color:rgba(251,191,36,0.3);color:var(--amber)"><span class="icon">🍃</span> MongoDB</div>
        <div class="tech-pill" style="border-color:rgba(167,139,250,0.3);color:var(--violet)"><span class="icon">☕</span> Advanced Java</div>
      </div>
    </div>
  </section>
</div>

<div class="divider"></div>

<!-- Projects -->
<div class="wrap">
  <section id="projects">
    <div class="section-label fade-up">Work</div>
    <h2 class="section-title fade-up">Featured <em>Projects</em></h2>

    <div class="project-grid">
      <div class="project-card fade-up">
        <span class="project-emoji">😷</span>
        <div class="project-name">Face Mask Detection System</div>
        <p class="project-desc">AI-powered real-time mask detection system leveraging computer vision to identify mask usage accurately.</p>
        <span class="project-tag">AI · Computer Vision</span>
      </div>
      <div class="project-card fade-up">
        <span class="project-emoji">🌿</span>
        <div class="project-name">Yoga & Ayurveda Website</div>
        <p class="project-desc">A health and wellness platform focused on holistic living, featuring rich UI and a fully responsive design.</p>
        <span class="project-tag">WordPress · UI/UX</span>
      </div>
      <div class="project-card fade-up" style="grid-column: 1 / -1;">
        <span class="project-emoji">💼</span>
        <div class="project-name">Portfolio Website</div>
        <p class="project-desc">A modern, animated developer portfolio showcasing projects, certifications, and skills with cutting-edge frontend techniques.</p>
        <span class="project-tag">HTML · CSS · JavaScript</span>
      </div>
    </div>
  </section>
</div>

<div class="divider"></div>

<!-- Certifications -->
<div class="wrap">
  <section id="certs">
    <div class="section-label fade-up">Credentials</div>
    <h2 class="section-title fade-up">Achievements & <em>Certifications</em></h2>

    <div class="cert-grid">
      <div class="cert-card fade-up">
        <div class="cert-icon">☕</div>
        <div class="cert-name">Java Programming</div>
        <div class="cert-platform">Codec Technologies</div>
      </div>
      <div class="cert-card fade-up">
        <div class="cert-icon">🗄️</div>
        <div class="cert-name">MySQL Database</div>
        <div class="cert-platform">Lets Upgrade</div>
      </div>
      <div class="cert-card fade-up">
        <div class="cert-icon">⚡</div>
        <div class="cert-name">HTML, CSS & JS Bootcamp</div>
        <div class="cert-platform">Lets Upgrade</div>
      </div>
      <div class="cert-card fade-up">
        <div class="cert-icon">📈</div>
        <div class="cert-name">SEO Fundamentals</div>
        <div class="cert-platform">Pankaj Kumar SEO</div>
      </div>
      <div class="cert-card fade-up">
        <div class="cert-icon">🤖</div>
        <div class="cert-name">AI Masterclass</div>
        <div class="cert-platform">Freedom with AI</div>
      </div>
    </div>
  </section>
</div>

<div class="divider"></div>

<!-- GitHub Stats -->
<div class="wrap">
  <section>
    <div class="section-label fade-up">Analytics</div>
    <h2 class="section-title fade-up">GitHub <em>Analytics</em></h2>

    <div class="stats-row">
      <div class="stat-card fade-up">
        <div class="stat-num" id="followers-count">—</div>
        <div class="stat-label">Followers</div>
      </div>
      <div class="stat-card fade-up">
        <div class="stat-num" id="repos-count">—</div>
        <div class="stat-label">Repositories</div>
      </div>
      <div class="stat-card fade-up">
        <div class="stat-num" id="stars-count">—</div>
        <div class="stat-label">Stars Earned</div>
      </div>
    </div>

    <div class="fade-up" style="display:grid;gap:16px;">
      <div style="border-radius:16px;overflow:hidden;border:1px solid var(--border);">
        <img width="100%" src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=abhinavmaurya12&theme=tokyonight" style="display:block;" alt="GitHub profile summary"/>
      </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;">
        <div style="border-radius:16px;overflow:hidden;border:1px solid var(--border);">
          <img width="100%" src="https://streak-stats.demolab.com?user=abhinavmaurya12&theme=tokyonight&hide_border=true&border_radius=0" style="display:block;" alt="Streak stats"/>
        </div>
        <div style="border-radius:16px;overflow:hidden;border:1px solid var(--border);">
          <img width="100%" src="https://github-readme-activity-graph.vercel.app/graph?username=abhinavmaurya12&theme=tokyo-night&hide_border=true&radius=0" style="display:block;" alt="Contribution graph"/>
        </div>
      </div>
      <div style="border-radius:16px;overflow:hidden;border:1px solid var(--border);">
        <img width="100%" src="https://github-profile-trophy.vercel.app/?username=abhinavmaurya12&theme=tokyonight&no-frame=true&row=1&column=5&margin-w=15" style="display:block;" alt="Trophies"/>
      </div>
    </div>
  </section>
</div>

<div class="divider"></div>

<!-- Connect -->
<div class="wrap">
  <section id="connect">
    <div class="section-label fade-up">Social</div>
    <h2 class="section-title fade-up">Connect <em>With Me</em></h2>
    <div class="connect-grid">
      <a href="https://github.com/abhinavmaurya12" target="_blank" class="social-card fade-up">
        <span class="social-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>
        </span>
        <div>
          <div style="font-size:13px;font-weight:600;color:var(--text);margin-bottom:2px;">GitHub</div>
          <div style="font-size:12px;color:var(--muted);">@abhinavmaurya12</div>
        </div>
      </a>
      <a href="https://www.linkedin.com/in/abhinav-maurya-25162b338" target="_blank" class="social-card fade-up">
        <span class="social-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="#0077b5"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        </span>
        <div>
          <div style="font-size:13px;font-weight:600;color:var(--text);margin-bottom:2px;">LinkedIn</div>
          <div style="font-size:12px;color:var(--muted);">Abhinav Maurya</div>
        </div>
      </a>
      <a href="https://www.instagram.com/_abhinav_830_" target="_blank" class="social-card fade-up">
        <span class="social-icon">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="url(#ig-grad)">
            <defs><linearGradient id="ig-grad" x1="0" y1="1" x2="1" y2="0"><stop offset="0%" stop-color="#f09433"/><stop offset="25%" stop-color="#e6683c"/><stop offset="50%" stop-color="#dc2743"/><stop offset="75%" stop-color="#cc2366"/><stop offset="100%" stop-color="#bc1888"/></linearGradient></defs>
            <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/>
          </svg>
        </span>
        <div>
          <div style="font-size:13px;font-weight:600;color:var(--text);margin-bottom:2px;">Instagram</div>
          <div style="font-size:12px;color:var(--muted);">@_abhinav_830_</div>
        </div>
      </a>
    </div>
  </section>
</div>

<!-- Footer -->
<footer>
  <div class="wrap">
    <div class="footer-logo">Abhinav Maurya</div>
    <div class="footer-sub">Java Full Stack Developer · PHP · WordPress · UI/UX</div>
    <div class="footer-tagline">
      <span>Code</span> • <span>Create</span> • <span>Innovate</span> • <span>Repeat</span>
    </div>
  </div>
</footer>

<script>
  // Intersection Observer for fade-up
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.classList.add('visible');
        }, 60 * (Array.from(entry.target.parentElement.querySelectorAll('.fade-up')).indexOf(entry.target)));
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.12 });

  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

  // GitHub API stats
  fetch('https://api.github.com/users/abhinavmaurya12')
    .then(r => r.json())
    .then(data => {
      const fmt = n => n >= 1000 ? (n/1000).toFixed(1)+'k' : n;
      document.getElementById('followers-count').textContent = fmt(data.followers || 0);
      document.getElementById('repos-count').textContent = fmt(data.public_repos || 0);
    })
    .catch(() => {
      document.getElementById('followers-count').textContent = '—';
      document.getElementById('repos-count').textContent = '—';
    });

  fetch('https://api.github.com/users/abhinavmaurya12/repos?per_page=100')
    .then(r => r.json())
    .then(repos => {
      const stars = repos.reduce((acc, r) => acc + (r.stargazers_count || 0), 0);
      document.getElementById('stars-count').textContent = stars;
    })
    .catch(() => { document.getElementById('stars-count').textContent = '—'; });

  // Smooth nav highlighting
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => { if (window.scrollY >= s.offsetTop - 120) current = s.id; });
    navLinks.forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + current ? 'var(--text)' : '';
    });
  });
</script>
</body>
</html>
