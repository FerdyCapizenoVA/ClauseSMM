<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Claude for Social Media Managers — A Practical Course</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,500;0,9..144,600;0,9..144,700;0,9..144,900;1,9..144,400;1,9..144,500&family=DM+Sans:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #f1e9d8;
    --bg-soft: #ebe2cf;
    --bg-warm: #e6dcc4;
    --ink: #1a1714;
    --ink-soft: #3a342c;
    --ink-mute: #6b6358;
    --rust: #b8401a;
    --rust-deep: #8e2f10;
    --moss: #2d3a23;
    --line: #c9bfa9;
    --line-soft: #d8cfba;
    --paper: #faf5e8;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'DM Sans', system-ui, sans-serif;
    background: var(--bg);
    color: var(--ink);
    line-height: 1.55;
    font-size: 17px;
    overflow-x: hidden;
    background-image:
      radial-gradient(circle at 20% 10%, rgba(184,64,26,0.04) 0%, transparent 40%),
      radial-gradient(circle at 80% 60%, rgba(45,58,35,0.04) 0%, transparent 40%);
  }
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100'%3E%3Cfilter id='n'%3E%3CfeTurbulence baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3CfeColorMatrix values='0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.06 0'/%3E%3C/filter%3E%3Crect width='100' height='100' filter='url(%23n)'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1;
    mix-blend-mode: multiply;
  }
  body.modal-open { overflow: hidden; }
  main, header, nav, footer { position: relative; z-index: 2; }

  .display {
    font-family: 'Fraunces', serif;
    font-optical-sizing: auto;
    font-weight: 500;
    line-height: 0.95;
    letter-spacing: -0.02em;
  }
  .smallcaps {
    text-transform: uppercase;
    letter-spacing: 0.18em;
    font-size: 0.72rem;
    font-weight: 500;
  }

  .topbar {
    border-bottom: 1px solid var(--line);
    position: sticky;
    top: 0;
    z-index: 100;
    backdrop-filter: blur(8px);
    background: rgba(241, 233, 216, 0.92);
  }
  .topbar-inner {
    max-width: 1280px;
    margin: 0 auto;
    padding: 14px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 24px;
  }
  .brand { display: flex; align-items: baseline; gap: 10px; }
  .brand-mark {
    font-family: 'Fraunces', serif;
    font-weight: 600;
    font-style: italic;
    font-size: 1.4rem;
    color: var(--rust);
  }
  .brand-name { font-family: 'Fraunces', serif; font-size: 1.05rem; font-weight: 500; }
  .nav-links { display: flex; gap: 28px; list-style: none; }
  .nav-links a { color: var(--ink-soft); text-decoration: none; font-size: 0.92rem; transition: color 0.2s; }
  .nav-links a:hover { color: var(--rust); }
  @media (max-width: 720px) { .nav-links { display: none; } }

  .hero {
    max-width: 1280px;
    margin: 0 auto;
    padding: 80px 32px 60px;
    display: grid;
    grid-template-columns: 1fr 380px;
    gap: 60px;
    align-items: end;
  }
  @media (max-width: 960px) {
    .hero { grid-template-columns: 1fr; gap: 40px; padding: 60px 24px 40px; }
  }
  .hero-eyebrow {
    color: var(--rust);
    margin-bottom: 28px;
    display: flex;
    align-items: center;
    gap: 14px;
  }
  .hero-eyebrow::before { content: ''; width: 40px; height: 1px; background: var(--rust); }
  .hero h1 { font-size: clamp(3rem, 8vw, 6.5rem); margin-bottom: 32px; }
  .hero h1 em { font-style: italic; color: var(--rust); font-weight: 400; }
  .hero-lede {
    font-size: 1.15rem;
    max-width: 540px;
    color: var(--ink-soft);
    line-height: 1.55;
  }
  .hero-side {
    border-left: 1px solid var(--line);
    padding-left: 28px;
    color: var(--ink-mute);
    font-size: 0.9rem;
  }
  .hero-side .smallcaps { color: var(--ink); margin-bottom: 12px; display: block; }
  .hero-side ul { list-style: none; margin-top: 8px; }
  .hero-side li {
    padding: 10px 0;
    border-bottom: 1px solid var(--line-soft);
    display: flex;
    justify-content: space-between;
    gap: 12px;
    cursor: pointer;
    transition: color 0.2s, padding 0.2s;
  }
  .hero-side li:last-child { border-bottom: none; }
  .hero-side li:hover { color: var(--rust); padding-left: 6px; }
  .hero-side .num {
    font-family: 'Fraunces', serif;
    font-style: italic;
    color: var(--rust);
    font-weight: 500;
  }

  .manifesto {
    border-top: 1px solid var(--line);
    border-bottom: 1px solid var(--line);
    background: var(--bg-soft);
    padding: 28px 32px;
    overflow: hidden;
    white-space: nowrap;
  }
  .manifesto-track {
    display: flex;
    gap: 60px;
    animation: scroll 40s linear infinite;
    width: max-content;
  }
  .manifesto-item {
    font-family: 'Fraunces', serif;
    font-style: italic;
    font-size: 1.4rem;
    color: var(--ink-soft);
  }
  .manifesto-item span { color: var(--rust); margin-right: 14px; font-weight: 600; }
  @keyframes scroll {
    0% { transform: translateX(0); }
    100% { transform: translateX(-50%); }
  }

  .intro {
    max-width: 1280px;
    margin: 0 auto;
    padding: 100px 32px 80px;
    display: grid;
    grid-template-columns: 280px 1fr;
    gap: 80px;
  }
  @media (max-width: 880px) {
    .intro { grid-template-columns: 1fr; gap: 32px; padding: 60px 24px; }
  }
  .intro-label {
    font-family: 'Fraunces', serif;
    font-size: 0.95rem;
    color: var(--rust);
    font-weight: 500;
  }
  .intro-label::before { content: '§'; margin-right: 8px; font-style: italic; }
  .intro-body p {
    font-family: 'Fraunces', serif;
    font-size: 1.65rem;
    line-height: 1.35;
    margin-bottom: 24px;
    font-weight: 400;
  }
  .intro-body p:last-child { margin-bottom: 0; }
  .intro-body strong {
    background: linear-gradient(transparent 60%, rgba(184,64,26,0.18) 60%);
    font-weight: 500;
  }

  .modules-section {
    border-top: 1px solid var(--line);
    background: var(--bg-warm);
    padding: 80px 32px;
  }
  .modules-header {
    max-width: 1280px;
    margin: 0 auto 60px;
    display: flex;
    justify-content: space-between;
    align-items: end;
    gap: 40px;
    flex-wrap: wrap;
  }
  .modules-header h2 { font-size: clamp(2.5rem, 5vw, 4rem); line-height: 1; }
  .modules-header h2 em { font-style: italic; color: var(--rust); }
  .modules-meta { color: var(--ink-mute); font-size: 0.9rem; text-align: right; }
  .modules-meta strong {
    font-family: 'Fraunces', serif;
    font-size: 2rem;
    font-style: italic;
    color: var(--rust);
    display: block;
    font-weight: 500;
  }

  .modules-grid {
    max-width: 1280px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: var(--line);
    border: 1px solid var(--line);
  }
  @media (max-width: 760px) { .modules-grid { grid-template-columns: 1fr; } }

  .module {
    background: var(--paper);
    padding: 36px 32px 28px;
    position: relative;
    transition: background 0.3s;
    cursor: pointer;
    border: none;
    width: 100%;
    text-align: left;
    font: inherit;
    color: inherit;
    display: flex;
    flex-direction: column;
  }
  .module:hover { background: #fdfaef; }
  .module:hover .module-cta { color: var(--rust-deep); padding-left: 6px; }
  .module:hover .module-num { transform: rotate(-4deg) scale(1.05); }
  .module:focus-visible { outline: 2px solid var(--rust); outline-offset: -4px; }

  .module-num {
    font-family: 'Fraunces', serif;
    font-style: italic;
    font-size: 4rem;
    color: var(--rust);
    line-height: 1;
    font-weight: 500;
    position: absolute;
    top: 24px;
    right: 32px;
    opacity: 0.85;
    transition: transform 0.3s;
  }
  .module-tag { color: var(--ink-mute); margin-bottom: 14px; }
  .module h3 {
    font-family: 'Fraunces', serif;
    font-size: 1.85rem;
    line-height: 1.1;
    margin-bottom: 18px;
    font-weight: 500;
    max-width: 75%;
    letter-spacing: -0.01em;
  }
  .module-desc { color: var(--ink-soft); margin-bottom: 24px; line-height: 1.55; }
  .module-list { list-style: none; margin-bottom: 24px; }
  .module-list li {
    padding: 10px 0 10px 24px;
    border-top: 1px solid var(--line-soft);
    position: relative;
    font-size: 0.93rem;
    color: var(--ink-soft);
  }
  .module-list li:last-child { border-bottom: 1px solid var(--line-soft); }
  .module-list li::before { content: '→'; position: absolute; left: 0; color: var(--rust); }
  .module-cta {
    margin-top: auto;
    padding-top: 8px;
    color: var(--rust);
    font-weight: 500;
    font-size: 0.9rem;
    transition: color 0.2s, padding 0.2s;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .module-cta::after { content: '→'; transition: transform 0.2s; }
  .module:hover .module-cta::after { transform: translateX(4px); }

  /* Modal */
  .modal-backdrop {
    position: fixed;
    inset: 0;
    background: rgba(26, 23, 20, 0.78);
    backdrop-filter: blur(6px);
    z-index: 200;
    display: none;
    align-items: flex-start;
    justify-content: center;
    padding: 40px 20px;
    overflow-y: auto;
    animation: fadeIn 0.25s ease-out;
  }
  .modal-backdrop.open { display: flex; }
  @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

  .modal {
    background: var(--paper);
    max-width: 820px;
    width: 100%;
    border-radius: 4px;
    position: relative;
    animation: modalIn 0.35s cubic-bezier(0.2, 0.8, 0.3, 1);
    box-shadow: 0 30px 80px rgba(0,0,0,0.4);
    margin: auto 0;
  }
  @keyframes modalIn {
    from { opacity: 0; transform: translateY(20px) scale(0.98); }
    to { opacity: 1; transform: translateY(0) scale(1); }
  }
  .modal-close {
    position: absolute;
    top: 20px;
    right: 20px;
    background: var(--bg-warm);
    border: 1px solid var(--line);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    cursor: pointer;
    font-family: 'Fraunces', serif;
    font-size: 1.4rem;
    color: var(--ink);
    line-height: 1;
    transition: background 0.2s, transform 0.2s, color 0.2s;
    z-index: 5;
  }
  .modal-close:hover {
    background: var(--rust);
    color: var(--paper);
    transform: rotate(90deg);
  }

  .modal-header {
    padding: 56px 56px 32px;
    border-bottom: 1px solid var(--line-soft);
    background: var(--bg-soft);
    border-radius: 4px 4px 0 0;
  }
  @media (max-width: 600px) { .modal-header { padding: 48px 28px 28px; } }
  .modal-num {
    font-family: 'Fraunces', serif;
    font-style: italic;
    font-size: 5rem;
    color: var(--rust);
    line-height: 1;
    margin-bottom: 12px;
    font-weight: 500;
  }
  .modal-tag { color: var(--ink-mute); margin-bottom: 12px; }
  .modal-header h2 {
    font-family: 'Fraunces', serif;
    font-size: clamp(2rem, 4vw, 2.8rem);
    line-height: 1.05;
    font-weight: 500;
    letter-spacing: -0.01em;
    margin-bottom: 16px;
  }
  .modal-header .lede {
    font-family: 'Fraunces', serif;
    font-size: 1.15rem;
    color: var(--ink-soft);
    line-height: 1.5;
    font-style: italic;
    max-width: 600px;
  }

  .modal-body { padding: 40px 56px 48px; }
  @media (max-width: 600px) { .modal-body { padding: 32px 28px 36px; } }

  .modal-section { margin-bottom: 40px; }
  .modal-section:last-child { margin-bottom: 0; }
  .modal-section-label {
    color: var(--rust);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .modal-section-label::before {
    content: '';
    width: 30px;
    height: 1px;
    background: var(--rust);
  }
  .modal-section p {
    color: var(--ink-soft);
    margin-bottom: 16px;
    line-height: 1.65;
  }
  .modal-section p:last-child { margin-bottom: 0; }
  .modal-section strong { color: var(--ink); font-weight: 600; }
  .modal-section em {
    background: linear-gradient(transparent 60%, rgba(184,64,26,0.18) 60%);
    font-style: normal;
    font-weight: 500;
  }

  .tasks { list-style: none; counter-reset: task; }
  .tasks li {
    counter-increment: task;
    padding: 20px 0 20px 60px;
    border-top: 1px solid var(--line-soft);
    position: relative;
  }
  .tasks li:last-child { border-bottom: 1px solid var(--line-soft); }
  .tasks li::before {
    content: counter(task, decimal-leading-zero);
    position: absolute;
    left: 0;
    top: 18px;
    font-family: 'Fraunces', serif;
    font-style: italic;
    font-size: 1.6rem;
    color: var(--rust);
    font-weight: 500;
  }
  .tasks .task-title {
    font-family: 'Fraunces', serif;
    font-size: 1.15rem;
    font-weight: 500;
    margin-bottom: 6px;
    color: var(--ink);
    line-height: 1.3;
  }
  .tasks .task-detail { font-size: 0.92rem; color: var(--ink-mute); line-height: 1.5; }

  .prompt-block {
    background: var(--ink);
    color: var(--bg);
    padding: 24px 28px;
    margin: 0;
    border-radius: 3px;
    position: relative;
  }
  .prompt-block .smallcaps {
    color: var(--rust);
    margin-bottom: 14px;
    display: block;
    font-size: 0.7rem;
  }
  .prompt-block code {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.82rem;
    line-height: 1.7;
    white-space: pre-wrap;
    color: #ede2c8;
    display: block;
  }
  .prompt-block code .var { color: #e8a87c; font-style: italic; }
  .prompt-copy {
    position: absolute;
    top: 16px;
    right: 16px;
    background: transparent;
    color: var(--paper);
    border: 1px solid rgba(250, 245, 232, 0.3);
    padding: 6px 12px;
    border-radius: 2px;
    font-size: 0.7rem;
    cursor: pointer;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    transition: background 0.2s, border-color 0.2s;
    font-family: 'DM Sans', sans-serif;
  }
  .prompt-copy:hover { background: var(--rust); border-color: var(--rust); }

  .module-warning {
    font-size: 0.92rem;
    color: var(--ink-mute);
    border-left: 3px solid var(--rust);
    padding: 12px 0 12px 18px;
    font-style: italic;
    background: linear-gradient(90deg, rgba(184,64,26,0.05), transparent);
  }
  .module-warning strong {
    font-style: normal;
    color: var(--rust-deep);
    font-weight: 600;
  }

  .modal-nav {
    border-top: 1px solid var(--line-soft);
    padding: 20px 56px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: var(--bg-soft);
    border-radius: 0 0 4px 4px;
    gap: 16px;
  }
  @media (max-width: 600px) { .modal-nav { padding: 20px 28px; } }
  .modal-nav button {
    background: transparent;
    border: none;
    color: var(--ink-soft);
    cursor: pointer;
    font-family: inherit;
    font-size: 0.9rem;
    transition: color 0.2s;
    padding: 8px;
  }
  .modal-nav button:hover:not(:disabled) { color: var(--rust); }
  .modal-nav button:disabled { opacity: 0.3; cursor: not-allowed; }
  .modal-nav .progress {
    font-family: 'Fraunces', serif;
    font-style: italic;
    color: var(--rust);
    font-size: 0.95rem;
  }

  .closing {
    max-width: 1280px;
    margin: 0 auto;
    padding: 100px 32px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
  }
  @media (max-width: 880px) {
    .closing { grid-template-columns: 1fr; padding: 60px 24px; gap: 40px; }
  }
  .closing-quote {
    font-family: 'Fraunces', serif;
    font-style: italic;
    font-size: clamp(2rem, 4vw, 3.2rem);
    line-height: 1.15;
    font-weight: 400;
  }
  .closing-quote::before {
    content: '"';
    font-size: 5rem;
    color: var(--rust);
    line-height: 0;
    vertical-align: -0.3em;
    margin-right: 8px;
  }
  .closing-cta {
    background: var(--ink);
    color: var(--bg);
    padding: 40px;
    border-radius: 2px;
  }
  .closing-cta .smallcaps { color: var(--rust); margin-bottom: 16px; display: block; }
  .closing-cta h3 {
    font-family: 'Fraunces', serif;
    font-size: 2rem;
    line-height: 1.15;
    margin-bottom: 20px;
    font-weight: 500;
  }
  .closing-cta p { color: #c4b8a3; margin-bottom: 28px; font-size: 0.95rem; }
  .btn {
    display: inline-block;
    background: var(--rust);
    color: var(--paper);
    padding: 14px 28px;
    text-decoration: none;
    font-weight: 500;
    font-size: 0.95rem;
    border-radius: 2px;
    transition: background 0.2s;
    border: none;
    cursor: pointer;
    font-family: inherit;
  }
  .btn:hover { background: var(--rust-deep); }

  footer {
    border-top: 1px solid var(--line);
    background: var(--bg-soft);
    padding: 40px 32px;
  }
  .footer-inner {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 20px;
    color: var(--ink-mute);
    font-size: 0.88rem;
  }
  .footer-inner .display { font-style: italic; color: var(--rust); font-size: 1.1rem; }

  .module { animation: rise 0.8s ease-out backwards; }
  @keyframes rise {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .module:nth-child(1) { animation-delay: 0.05s; }
  .module:nth-child(2) { animation-delay: 0.1s; }
  .module:nth-child(3) { animation-delay: 0.15s; }
  .module:nth-child(4) { animation-delay: 0.2s; }
  .module:nth-child(5) { animation-delay: 0.25s; }
  .module:nth-child(6) { animation-delay: 0.3s; }
  .module:nth-child(7) { animation-delay: 0.35s; }
  .module:nth-child(8) { animation-delay: 0.4s; }
</style>
</head>
<body>

<header class="topbar">
  <div class="topbar-inner">
    <div class="brand">
      <span class="brand-mark">C</span>
      <span class="brand-name">Claude for SMMs</span>
    </div>
    <nav>
      <ul class="nav-links">
        <li><a href="#intro">The Premise</a></li>
        <li><a href="#modules">Modules</a></li>
        <li><a href="#closing">Get Started</a></li>
      </ul>
    </nav>
  </div>
</header>

<main>

  <section class="hero">
    <div>
      <div class="hero-eyebrow smallcaps">A practical course · 8 modules</div>
      <h1 class="display">
        How to use<br>
        <em>Claude</em> as your<br>
        social media manager.
      </h1>
      <p class="hero-lede">
        Not "AI tips and tricks." A working playbook for Filipino freelancers, agency owners, and in-house SMMs who want to ship more, faster — without sounding like a chatbot wrote it. Real prompts. Real workflows. Honest limits.
      </p>
    </div>
    <aside class="hero-side">
      <span class="smallcaps">In this course</span>
      <ul id="hero-toc">
        <li data-open="1"><span>The Foundations</span><span class="num">01</span></li>
        <li data-open="2"><span>Content Creation</span><span class="num">02</span></li>
        <li data-open="3"><span>Audience &amp; Research</span><span class="num">03</span></li>
        <li data-open="4"><span>Strategy &amp; Planning</span><span class="num">04</span></li>
        <li data-open="5"><span>Client Communication</span><span class="num">05</span></li>
        <li data-open="6"><span>Scripts &amp; Long-form</span><span class="num">06</span></li>
        <li data-open="7"><span>Engagement &amp; DMs</span><span class="num">07</span></li>
        <li data-open="8"><span>Systems &amp; SOPs</span><span class="num">08</span></li>
      </ul>
    </aside>
  </section>

  <div class="manifesto">
    <div class="manifesto-track">
      <span class="manifesto-item"><span>※</span>Prompt like a strategist, not a beggar.</span>
      <span class="manifesto-item"><span>※</span>Context beats cleverness.</span>
      <span class="manifesto-item"><span>※</span>Edit everything Claude gives you.</span>
      <span class="manifesto-item"><span>※</span>Use it as a thinking partner, not a ghost-writer.</span>
      <span class="manifesto-item"><span>※</span>Prompt like a strategist, not a beggar.</span>
      <span class="manifesto-item"><span>※</span>Context beats cleverness.</span>
      <span class="manifesto-item"><span>※</span>Edit everything Claude gives you.</span>
      <span class="manifesto-item"><span>※</span>Use it as a thinking partner, not a ghost-writer.</span>
    </div>
  </div>

  <section class="intro" id="intro">
    <div><span class="intro-label">The premise</span></div>
    <div class="intro-body">
      <p>Most SMMs use Claude wrong. They paste in "write me 5 captions for a coffee shop" and get back five captions that sound like every other AI caption ever written. Then they blame the tool.</p>
      <p>Claude isn't a vending machine. It's <strong>a junior strategist who's read everything but knows nothing about your client</strong>. Your job is to onboard it. Brief it. Push back on it. Edit it.</p>
      <p>This course teaches you exactly that — eight modules covering the full SMM workflow. Click any module below to open the full lesson with explanation, tasks, and a copy-paste prompt.</p>
    </div>
  </section>

  <section class="modules-section" id="modules">
    <div class="modules-header">
      <h2 class="display">The <em>Eight</em><br>Modules.</h2>
      <div class="modules-meta">
        <strong>~6 hrs</strong>
        Self-paced · Click any module to open
      </div>
    </div>

    <div class="modules-grid" id="modules-grid"></div>
  </section>

  <section class="closing" id="closing">
    <div class="closing-quote">
      The SMMs who win the next two years aren't the ones using AI the most. They're the ones using it best — with taste, judgment, and editing fingers.
    </div>
    <div class="closing-cta">
      <span class="smallcaps">Start the course</span>
      <h3>Begin with Module One.</h3>
      <p>The Foundations module is the most important one. Skip it and every other module will hurt. Open it, read for 20 minutes, then try the first task on a real client today.</p>
      <button class="btn" onclick="openModule(1)">Open Module 01 →</button>
    </div>
  </section>

</main>

<div class="modal-backdrop" id="modal-backdrop" role="dialog" aria-modal="true" aria-labelledby="modal-title">
  <div class="modal" id="modal" role="document">
    <button class="modal-close" id="modal-close" aria-label="Close lesson">×</button>
    <div class="modal-header">
      <div class="modal-num" id="modal-num"></div>
      <div class="modal-tag smallcaps" id="modal-tag"></div>
      <h2 id="modal-title"></h2>
      <p class="lede" id="modal-lede"></p>
    </div>
    <div class="modal-body" id="modal-body"></div>
    <div class="modal-nav">
      <button id="modal-prev">← Previous</button>
      <span class="progress" id="modal-progress"></span>
      <button id="modal-next">Next →</button>
    </div>
  </div>
</div>

<footer>
  <div class="footer-inner">
    <div><span class="display">Claude for SMMs</span> · A course by Ferdy Capizenova</div>
    <div>© 2026 · Built for Filipino freelancers and the global SMM community</div>
  </div>
</footer>

<script>
const modules = [
  {
    n: 1,
    tag: "Module One · Foundations",
    title: "How to actually talk to Claude.",
    lede: "Before any prompt template, learn the four ingredients every good SMM prompt needs.",
    cardDesc: "Skip these and you get generic. Include them and you get usable. The R-C-A-F structure is the foundation everything else in this course is built on.",
    cardList: [
      "The R-C-A-F prompt structure",
      "Feeding Claude brand voice without 20 paragraphs",
      "Why 'act as' prompts often hurt more than help"
    ],
    explanation: `
      <p>The single biggest reason your AI output sounds generic isn't the model — it's the brief. Claude has read more marketing content than you ever will. What it doesn't know is <strong>your client</strong>. So your job, every single prompt, is to onboard it fast.</p>
      <p>Use what I call the <em>R-C-A-F structure</em> for any prompt longer than a one-liner:</p>
      <p><strong>Role</strong> — who Claude is in this conversation (a strategist, an editor, a critic). Skip the "act as a world-class expert" theatrics. Just say "you're helping me write." <strong>Context</strong> — the brand, the niche, what you're trying to do. <strong>Audience</strong> — who this content is for, what they care about, what they hate. <strong>Format</strong> — exact output you want: word count, channel, voice, what to leave out.</p>
      <p>The "leave out" part is underrated. Telling Claude "no emojis, no rhetorical questions, no 'in today's fast-paced world' openers" eliminates 80% of generic AI tells in one line.</p>
    `,
    tasks: [
      { title: "Pick a real client (or yourself).", detail: "Write down their R-C-A-F in 4 lines. Don't overthink it — keep each line under 20 words." },
      { title: "Take a vague prompt you've used before and rewrite it.", detail: "Use the R-C-A-F structure. The new prompt should be 3–5x longer than the original." },
      { title: "Run both versions and compare.", detail: "Save both outputs side by side. Notice what changes when context is fed in. This is your proof of concept." },
      { title: "Build a 'banned phrases' list.", detail: "Write down 10 AI tells you'll always tell Claude to avoid (e.g. 'in today's digital landscape,' 'unleash,' 'elevate'). Save it — you'll paste it into every brief." }
    ],
    prompt: `You're helping me write copy for <span class="var">[brand]</span>, a 
<span class="var">[niche]</span> business targeting <span class="var">[audience]</span>.
Voice: <span class="var">[3 adjectives + 1 anti-word]</span>.
Goal of this post: <span class="var">[awareness / save / DM]</span>.
Format: IG caption, max 150 words, no emojis.
Avoid these phrases: <span class="var">[paste banned list]</span>

Draft 3 versions with different hooks.`,
    warning: "If your brief is vague, the output will be vague. Spend 80% on the prompt, 20% on editing."
  },
  {
    n: 2,
    tag: "Module Two · Content",
    title: "Captions, hooks, and post copy that doesn't sound AI.",
    lede: "Use Claude to break writer's block, not to replace your judgment.",
    cardDesc: "Generate hooks in bulk, then cut ruthlessly. The output you ship should sound like the brand — not like Claude.",
    cardList: [
      "Hook formulas that still work in 2026",
      "Caption variants for A/B testing",
      "Repurposing one idea into 5 platforms"
    ],
    explanation: `
      <p>Here's the trap: you ask Claude for "5 captions" and ship one. That's three minutes of work and zero strategy. The captions ship looking like AI because you didn't filter.</p>
      <p>Better workflow: ask for <em>15 hooks</em>, not 5 captions. Hooks are the part that decides whether anyone reads the rest. Generate volume, then cut to the 3 you'd actually be proud to post. Then write the captions yourself, using those hooks as starting points.</p>
      <p>The mental model: <strong>Claude is your idea machine, you're the editor</strong>. Editors cut 12 of 15 ideas. That's the job. If you ship everything Claude gives you, you're not editing — you're just publishing.</p>
      <p>Same logic for repurposing. One core idea → 5 different channel-specific takes is something Claude is genuinely great at, because the constraint (channel format) does the work for you.</p>
    `,
    tasks: [
      { title: "Pick one client post idea.", detail: "Just one. Something you're already planning to post this week." },
      { title: "Generate 15 hooks using the prompt below.", detail: "Don't stop at 5. The 6th–15th are usually where the interesting ones live." },
      { title: "Cut down to 3 you'd actually use.", detail: "Read each hook out loud. If it sounds like a LinkedIn influencer, cut it. If it sounds like your client at a coffee shop, keep it." },
      { title: "Rewrite each in your client's voice — by hand.", detail: "Don't ask Claude to do this step. The hand-rewrite is what kills the AI smell." },
      { title: "Repurpose the winner across 3 platforms.", detail: "IG caption → LinkedIn post → X thread. Same idea, different formats. Claude handles the format-shifting well." }
    ],
    prompt: `Give me 15 hooks for a post about <span class="var">[topic]</span>.
Audience: <span class="var">[describe]</span>. Pain point: <span class="var">[specific]</span>.

Mix these styles: contrarian take, question, 
specific number, mistake/myth, before-after.
No clickbait. No "stop scrolling."
One line each.`,
    warning: "Claude defaults to safe, polished copy. If it sounds boring, your prompt was boring. Add edge — name names, take positions, get specific."
  },
  {
    n: 3,
    tag: "Module Three · Research",
    title: "Audience and competitor research, faster.",
    lede: "Claude can't browse a competitor in real time, but it can synthesize what you already have.",
    cardDesc: "Feed Claude messy notes, screenshots, and pasted captions. It turns them into clean audience profiles and competitor breakdowns.",
    cardList: [
      "Building a sharper ICP from existing data",
      "Auditing a competitor from pasted samples",
      "Surfacing content gaps you can own"
    ],
    explanation: `
      <p>Most SMMs treat research like a chore. They scroll through a competitor's feed for 20 minutes, write a vague "they post a lot of carousels" note, and call it audit. Claude can't do the scrolling for you, but if you give it the raw material, it'll spot patterns you missed.</p>
      <p>The trick is in the inputs. <strong>Garbage in, garbage out.</strong> Don't ask "audit my competitor." Instead: paste 20 of their captions, 5 of their best-performing posts, and a screenshot of their bio. Then ask Claude to identify pillars, voice, and gaps.</p>
      <p>Same for your client's audience. Don't ask Claude to "describe my audience." Paste in 30 comments from their posts, 10 DMs they've received, and any survey data. Claude is excellent at synthesis — bad at fabrication. So feed it real data and it'll give you real insight.</p>
      <p>The output you want isn't "your audience is millennial women." It's <em>"your audience asks the same three questions in DMs, your captions answer two of them, and the third one is where your next 5 posts should live."</em></p>
    `,
    tasks: [
      { title: "Pick one competitor in your client's niche.", detail: "Not a giant. A peer-sized one — same scale, similar offer." },
      { title: "Copy 20 of their captions into a doc.", detail: "Take the 10 most-engaged and 10 random recent posts. A mixed sample matters." },
      { title: "Run the audit prompt below.", detail: "Read the output critically. What does Claude get right? What does it miss? Note both." },
      { title: "Identify one content gap you can own.", detail: "From the audit, pick one angle the competitor doesn't cover. Plan 3 posts around it for next month." },
      { title: "Repeat for your client's audience.", detail: "Paste 30 of their comments / DMs. Run the same kind of analysis. Look for repeating questions — those are post ideas." }
    ],
    prompt: `Below are 20 captions from <span class="var">[competitor]</span>'s feed.
Analyze: 
1. Their content pillars (be specific, not "education")
2. Their voice in 5 adjectives
3. What they avoid talking about
4. 3 angles they're missing that we could own.

[paste captions]`,
    warning: "Don't ask Claude what's 'trending.' It doesn't know in real time. Feed it the data first, then ask for patterns."
  },
  {
    n: 4,
    tag: "Module Four · Strategy",
    title: "Content calendars and pillars that hold up.",
    lede: "Anyone can ask for a 30-day content calendar. Few people get one that's actually shippable.",
    cardDesc: "The difference is feeding Claude your strategy first — pillars, cadence, campaign goals — instead of asking it to invent them.",
    cardList: [
      "Going from positioning → pillars → calendar",
      "Building campaigns around launches and seasonal moments",
      "Stress-testing a calendar against client goals"
    ],
    explanation: `
      <p>"Make me a content calendar" is the laziest prompt in social media. The output will be 30 generic posts that match no client, no goal, no strategy. The tool gets blamed. The tool didn't fail you — the brief did.</p>
      <p>A calendar is the <em>output</em> of strategy, not the input. You need to feed Claude four things first: <strong>positioning</strong> (what makes this brand different in one sentence), <strong>pillars</strong> (3–4 buckets of content), <strong>cadence</strong> (how often, what formats), and <strong>this month's priority</strong> (one big goal, not five).</p>
      <p>Once Claude has those, the calendar it produces is actually a plan, not a list. You can argue with it. You can ladder it toward an outcome. You can show it to a client and they'll see strategy, not Mad Libs.</p>
      <p>One more thing: ask Claude to <em>stress-test</em> the calendar after it produces one. "Where does this calendar fail to ladder toward [goal]?" The self-critique is often more useful than the calendar itself.</p>
    `,
    tasks: [
      { title: "Write your client's positioning in one sentence.", detail: "Format: '[Brand] helps [audience] [outcome] without [common pain].' If you can't, you don't have positioning yet — fix that before the calendar." },
      { title: "List 3–4 content pillars.", detail: "Each pillar should be specific. Not 'education' — 'how to spot insurance scams in the Philippines.' Specific pillars produce specific posts." },
      { title: "Define this month's one priority.", detail: "Lead generation? Audience growth? Launch? Pick ONE. A calendar with five priorities has no priority." },
      { title: "Run the calendar prompt.", detail: "Use all four inputs above. Read the output and circle posts that don't ladder toward the priority — those are weak posts." },
      { title: "Stress-test it.", detail: "Ask Claude: 'Where does this calendar fail my priority?' The answer becomes your editing checklist." },
      { title: "Send it to your client BEFORE you start producing.", detail: "Calendar approval is the cheapest revision round you'll ever do." }
    ],
    prompt: `Here's our positioning: <span class="var">[1-2 sentences]</span>
Pillars: <span class="var">[list 3-4]</span>
Cadence: <span class="var">[e.g. 4 IG posts + 3 reels weekly]</span>
This month's priority: <span class="var">[launch/lead-gen/etc]</span>

Build a 4-week calendar. Each post: pillar tag, 
format, hook, brief description, CTA.
Ladder posts toward the priority.

Then critique your own calendar — where does 
it fail the priority?`,
    warning: "A calendar from Claude is a draft. Your client's brain, the algorithm, and your own judgment do the final cut."
  },
  {
    n: 5,
    tag: "Module Five · Client Comms",
    title: "Discovery calls, proposals, and reports.",
    lede: "Most SMMs lose hours every month writing the same emails from scratch.",
    cardDesc: "Claude is excellent at this — once. After that, save the structure as a template and reuse it across clients.",
    cardList: [
      "Discovery call question banks tailored to the niche",
      "Proposals that match scope to outcomes (not deliverables)",
      "Monthly reports that read like strategy, not analytics"
    ],
    explanation: `
      <p>If you're writing your monthly report from a blank page, you're losing two hours a client. That's eight hours a month at four clients. That's a full day. Wasted.</p>
      <p>Client comms — discovery questions, proposals, monthly reports, kickoff emails, contract addendums — are the highest-leverage place Claude can save you time, because the structure repeats. The content changes; the skeleton doesn't.</p>
      <p>The move is to write each one <em>once</em>, with Claude's help, and save the prompt-plus-output as a template. Next month, you swap the data, run the prompt, edit lightly. Five minutes instead of two hours.</p>
      <p>The one place to be careful: <strong>monthly reports</strong>. Claude wants to make every month sound like a win. That's bad for client trust. Tell it explicitly: "Be honest about what didn't work. Don't inflate small wins. If a metric dropped, say so and propose what to test next month."</p>
    `,
    tasks: [
      { title: "Pick your most painful recurring email.", detail: "Whatever you write the most often. Discovery questions, kickoff doc, monthly report — start with the one that takes you longest." },
      { title: "Run the prompt with your real client data.", detail: "Don't use a hypothetical. Use last month's actual numbers, real wins, real misses." },
      { title: "Edit the output until it sounds like you.", detail: "Read it out loud. Cut anything that sounds 'generic SMM' or overly polished." },
      { title: "Save the prompt as a fill-in-the-blank template.", detail: "Replace specifics with [variables]. Now you have a reusable asset." },
      { title: "Use it next month — and time yourself.", detail: "If it takes more than 30 minutes, the template needs more variables. Iterate." }
    ],
    prompt: `I'm sending a monthly report to <span class="var">[client]</span>.
Numbers: <span class="var">[paste from analytics]</span>
What we shipped: <span class="var">[bullet list]</span>
What didn't work: <span class="var">[be honest]</span>
Next month's focus: <span class="var">[1-2 priorities]</span>

Write the report in 3 sections — Wins, What 
the data says, Next month. Tone: confident, 
plain English. No fluff. No emojis. Around 
350 words. Don't inflate small wins.`,
    warning: "Claude will inflate small wins if you let it. Tell it to be honest about what didn't work — clients trust you more for it."
  },
  {
    n: 6,
    tag: "Module Six · Long-form",
    title: "Reel scripts, carousels, and long-form posts.",
    lede: "Long-form is where SMMs spend the most time and get the worst AI output.",
    cardDesc: "The fix isn't a longer prompt — it's a structural prompt that tells Claude exactly how the format works.",
    cardList: [
      "Reel scripts with hook, payoff, and CTA structure",
      "Carousel outlines that work slide-by-slide",
      "LinkedIn / blog posts with a real argument"
    ],
    explanation: `
      <p>Carousels and reels fail under generic prompts because Claude doesn't know the format constraints unless you tell it. Slide 1 has a different job than slide 7. The first 3 seconds of a reel determine whether anyone watches the rest.</p>
      <p>So don't ask for "a carousel about [topic]." Ask for a <em>structure</em>: 7 slides, each with a specific role. Slide 1 is the hook. Slides 2–6 build one argument. Slide 7 is the CTA. Then constrain word counts: title ≤ 8 words, body ≤ 25 words. Claude follows constraints well.</p>
      <p>Same for reels. Tell Claude the script needs: hook (first 2 seconds, must promise a payoff), build (3–8 seconds, set up the tension), payoff (8–15 seconds, deliver), CTA (last 2 seconds). Now you've given it a job, not a vibe.</p>
      <p>For long-form blog or LinkedIn posts: tell Claude the <strong>argument</strong> you want to make in one sentence. Not the topic — the argument. "AI is changing SMM" is a topic. "Most SMMs are using AI as a typewriter when it's actually a sparring partner" is an argument. The second one writes itself.</p>
    `,
    tasks: [
      { title: "Pick one carousel idea you've been sitting on.", detail: "Don't start fresh. Use one that's been in your client's content backlog for two weeks." },
      { title: "Write the ONE insight in a single sentence.", detail: "Before you prompt, write what the carousel exists to land. If you can't, the carousel isn't ready." },
      { title: "Run the carousel prompt.", detail: "Pay attention to slide 1. If the hook 'announces' the carousel ('In this carousel...'), kill it and ask Claude for 5 alternatives." },
      { title: "Edit slide 1 by hand until it earns the swipe.", detail: "Hooks are the part where AI writing is most obvious. Hand-write this one." },
      { title: "Now do a reel script for the same idea.", detail: "Run the reel version of the prompt. Same insight, different format. Compare the two — which one lands harder?" }
    ],
    prompt: `Write a 7-slide IG carousel.
Topic: <span class="var">[topic]</span>
Audience: <span class="var">[describe]</span>
Insight to land: <span class="var">[the one takeaway]</span>

Slide 1: hook (curiosity gap, not clickbait)
Slides 2-6: build the argument, one idea per slide
Slide 7: simple CTA

Each slide: title (max 8 words) + body 
(max 25 words). No emojis on titles.`,
    warning: "If Claude writes 'in this carousel we'll explore...' kill that slide. Hooks promise a payoff; they don't announce one."
  },
  {
    n: 7,
    tag: "Module Seven · Engagement",
    title: "DMs, comment replies, and outreach.",
    lede: "The risky module — because lazy AI DMs are how brands lose trust.",
    cardDesc: "Used well, Claude helps you draft personalized outreach faster. Used badly, it gets you blocked or worse.",
    cardList: [
      "Personalized cold outreach (with research, not templates)",
      "Handling objections in DMs without sounding scripted",
      "Comment-reply systems for community building"
    ],
    explanation: `
      <p>Cold DMs are where AI most damages brand trust. The pattern is obvious within two lines, recipients screenshot it to their followers, and your client looks worse than if you'd never reached out. So before this module: <strong>if your DM doesn't reference something specific the recipient actually said or did, don't send it.</strong> No exceptions.</p>
      <p>Used right, though, Claude is excellent at the <em>structure</em> of a DM — it just shouldn't write the personalization. Your job: do the research (5 minutes per prospect, minimum). Note one specific thing — a post they made, a project they shipped, a take they had. Feed that into the prompt. Claude builds the DM around your research.</p>
      <p>For comment replies, the use case is slightly different. You're not personalizing 1-to-1; you're maintaining a consistent voice across hundreds of replies. Build a "voice doc" — 10 examples of your client replying in their voice — and feed it to Claude when drafting batch replies. Then edit, always.</p>
      <p>For objections (cost, timing, fit), Claude is genuinely useful at finding the underlying concern. Paste the objection, ask "what is this person really worried about?" — the answer points to the real reply.</p>
    `,
    tasks: [
      { title: "Pick 3 prospects whose work you actually admire.", detail: "Not 30. Three. Quality over quantity is the entire point of this module." },
      { title: "Research each for 5 minutes minimum.", detail: "Note one specific thing each one has said or shipped. Screenshot it if you have to." },
      { title: "Run the outreach prompt for each.", detail: "Feed in your research. Get a draft. Don't send it yet." },
      { title: "Rewrite each DM by hand in your voice.", detail: "Cut anything that could be sent to anyone else. The DM should ONLY make sense to that one person." },
      { title: "Send one this week.", detail: "Just one. Track the response rate over 30 days. Compare it to your old template-DM approach." },
      { title: "For objection-handling: save 3 common objections.", detail: "Cost, timing, scope. Build a Claude-assisted reply for each. Save them. Edit each before sending." }
    ],
    prompt: `I'm reaching out to <span class="var">[name]</span>, who runs 
<span class="var">[business]</span>. Their recent post was about 
<span class="var">[specific thing they posted]</span>.

Draft a DM under 60 words that:
- Opens by referencing the actual post (not generic praise)
- Connects to one specific thing I offer: <span class="var">[your service]</span>
- Ends with a low-pressure question, not a pitch

Tone: peer, not vendor.`,
    warning: "Never paste a Claude DM without rewriting it in your voice. Prospects can smell AI within two lines — and so can their followers when they screenshot you."
  },
  {
    n: 8,
    tag: "Module Eight · Systems",
    title: "Building your prompt library and SOPs.",
    lede: "One-off prompts are fine. A prompt library compounds.",
    cardDesc: "Save the prompts that work, version them by client, and turn them into SOPs your team or future self can use.",
    cardList: [
      "Folder structure: prompts by client, by task",
      "Turning a working prompt into a fill-in-the-blank template",
      "Onboarding a VA or junior to your AI workflow"
    ],
    explanation: `
      <p>Here's what most SMMs do: they write a great prompt, get a great output, ship it, then forget the prompt existed. Next month they rewrite the same prompt from scratch. That's not an AI workflow — that's just typing twice.</p>
      <p>The compounding move is the <strong>prompt library</strong>. Every time a prompt produces output you actually shipped, save it. Tag it with the task and the client. Over six months, you'll have 30–50 battle-tested prompts. Onboarding a VA becomes "here's the library — read it." Onboarding a new client becomes "fork these prompts, swap the variables."</p>
      <p>Structure matters less than the habit. A simple Notion page or Google Doc with sections — Content, Strategy, Comms, Research — works fine. The killer move is naming each prompt by what it produces, not what it does. Not "captions prompt." Instead: <em>"IG caption variants — voice-matched."</em></p>
      <p>The advanced move: turn each saved prompt into a template with explicit variables. Then anyone on your team can fill it in. That's how solo SMMs scale to small agencies — by turning their best prompts into reusable assets.</p>
    `,
    tasks: [
      { title: "Open a fresh Notion page or Google Doc.", detail: "Title it 'Prompt Library — [Your Name].' Create 4 sections: Content, Strategy, Comms, Research." },
      { title: "Pick your 3 best prompts from the past month.", detail: "Best = produced output you actually shipped without major rewrites. If you don't have 3, you're prompting too rarely." },
      { title: "Turn each into a template using the prompt below.", detail: "Replace specifics with [variables]. Add a one-line 'when to use' note. Add a 'what to edit by hand' note." },
      { title: "Save them in your library by task.", detail: "Don't tag by client. Tag by task. The same caption-prompt should work across multiple clients with different variables." },
      { title: "Pick the prompt you use most often and add a 'voice' variable.", detail: "If you serve 5 clients, that one prompt now has 5 variations — same structure, different voice notes." },
      { title: "Schedule a 30-min review every month.", detail: "Add new prompts. Kill ones you stopped using. Refine ones that need it. The library only compounds if you maintain it." }
    ],
    prompt: `I want to turn this working prompt into a 
reusable template:

[paste your prompt + the output you got]

Help me:
1. Identify which parts should become 
   variables (in [brackets])
2. Add a 1-line "when to use" note
3. List the inputs I need to gather first
4. Flag anything in the output that I 
   should always edit by hand`,
    warning: "A prompt library only pays off if you actually open it. Keep it where your work lives — not buried in a Notion subpage you'll forget about."
  }
];

const grid = document.getElementById('modules-grid');
modules.forEach(m => {
  const btn = document.createElement('button');
  btn.className = 'module';
  btn.setAttribute('data-module', m.n);
  btn.setAttribute('aria-label', `Open ${m.tag}: ${m.title}`);
  btn.innerHTML = `
    <span class="module-num">${String(m.n).padStart(2, '0')}</span>
    <span class="module-tag smallcaps">${m.tag}</span>
    <h3>${m.title}</h3>
    <p class="module-desc">${m.cardDesc}</p>
    <ul class="module-list">
      ${m.cardList.map(item => `<li>${item}</li>`).join('')}
    </ul>
    <span class="module-cta">Open lesson</span>
  `;
  btn.addEventListener('click', () => openModule(m.n));
  grid.appendChild(btn);
});

document.querySelectorAll('#hero-toc li').forEach(li => {
  li.addEventListener('click', () => openModule(parseInt(li.getAttribute('data-open'))));
});

const backdrop = document.getElementById('modal-backdrop');
const modal = document.getElementById('modal');
let currentModule = null;

function openModule(n) {
  const m = modules.find(x => x.n === n);
  if (!m) return;
  currentModule = n;

  document.getElementById('modal-num').textContent = String(m.n).padStart(2, '0');
  document.getElementById('modal-tag').textContent = m.tag;
  document.getElementById('modal-title').textContent = m.title;
  document.getElementById('modal-lede').textContent = m.lede;

  document.getElementById('modal-body').innerHTML = `
    <div class="modal-section">
      <div class="modal-section-label smallcaps">The Lesson</div>
      ${m.explanation}
    </div>

    <div class="modal-section">
      <div class="modal-section-label smallcaps">Your Tasks</div>
      <ol class="tasks">
        ${m.tasks.map(t => `
          <li>
            <div class="task-title">${t.title}</div>
            <div class="task-detail">${t.detail}</div>
          </li>
        `).join('')}
      </ol>
    </div>

    <div class="modal-section">
      <div class="modal-section-label smallcaps">The Prompt</div>
      <div class="prompt-block">
        <button class="prompt-copy" data-prompt-n="${m.n}">Copy</button>
        <span class="smallcaps">Copy &amp; customize</span>
        <code>${m.prompt}</code>
      </div>
    </div>

    <div class="modal-section">
      <div class="modal-section-label smallcaps">Watch For</div>
      <p class="module-warning"><strong>Heads up:</strong> ${m.warning}</p>
    </div>
  `;

  document.getElementById('modal-progress').textContent = `Module ${m.n} of ${modules.length}`;
  document.getElementById('modal-prev').disabled = m.n === 1;
  document.getElementById('modal-next').disabled = m.n === modules.length;

  document.querySelectorAll('.prompt-copy').forEach(btn => {
    btn.addEventListener('click', e => {
      e.stopPropagation();
      const n = parseInt(btn.getAttribute('data-prompt-n'));
      const mod = modules.find(x => x.n === n);
      const tmp = document.createElement('div');
      tmp.innerHTML = mod.prompt;
      const text = tmp.textContent;
      navigator.clipboard.writeText(text).then(() => {
        btn.textContent = 'Copied!';
        setTimeout(() => { btn.textContent = 'Copy'; }, 1500);
      }).catch(() => {
        btn.textContent = 'Press Ctrl+C';
      });
    });
  });

  backdrop.classList.add('open');
  document.body.classList.add('modal-open');
  modal.scrollTop = 0;
  backdrop.scrollTop = 0;
}

function closeModal() {
  backdrop.classList.remove('open');
  document.body.classList.remove('modal-open');
  currentModule = null;
}

document.getElementById('modal-close').addEventListener('click', closeModal);
backdrop.addEventListener('click', e => { if (e.target === backdrop) closeModal(); });
document.addEventListener('keydown', e => {
  if (!backdrop.classList.contains('open')) return;
  if (e.key === 'Escape') closeModal();
  if (e.key === 'ArrowLeft' && currentModule > 1) openModule(currentModule - 1);
  if (e.key === 'ArrowRight' && currentModule < modules.length) openModule(currentModule + 1);
});
document.getElementById('modal-prev').addEventListener('click', () => {
  if (currentModule > 1) openModule(currentModule - 1);
});
document.getElementById('modal-next').addEventListener('click', () => {
  if (currentModule < modules.length) openModule(currentModule + 1);
});
</script>

</body>
</html>
