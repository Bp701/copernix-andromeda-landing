<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <title>Copernix OS · NeuroEduLabs · TRL 6 Demo</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Copernix OS – lokalny system Edge AI do wsparcia dzieci ze SPE. Demo TRL 7 NeuroEduLabs.">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@700&family=Rajdhani:wght@400;600;700&display=swap');
    * { margin:0; padding:0; box-sizing:border-box; }
    body {
      background:
        radial-gradient(circle at top left, rgba(56,189,248,0.14) 0, transparent 55%),
        radial-gradient(circle at bottom right, rgba(236,72,153,0.14) 0, transparent 55%),
        #020617;
      color:#e5e7eb;
      font-family:'Rajdhani',sans-serif;
      min-height:100vh;
    }
    .shell { max-width:1200px; margin:0 auto; padding:32px 16px 48px; }
    header { display:flex; justify-content:space-between; align-items:center; gap:16px; margin-bottom:32px; }
    .logo-main {
      font-family:'Orbitron',sans-serif; font-size:1.6rem; letter-spacing:0.2em;
      text-transform:uppercase;
      background:linear-gradient(135deg,#06b6d4,#a855f7);
      -webkit-background-clip:text; -webkit-text-fill-color:transparent;
    }
    .nav { display:flex; gap:16px; font-size:0.85rem; text-transform:uppercase; letter-spacing:0.18em; }
    .nav a { color:#9ca3af; text-decoration:none; padding:4px 0; border-bottom:1px solid transparent; }
    .nav a:hover { color:#e5e7eb; border-bottom-color:#06b6d4; }
    .hero { display:grid; grid-template-columns: minmax(0,2.1fr) minmax(0,2.2fr); gap:28px; align-items:stretch; }
    @media (max-width:900px){ header {flex-direction:column; align-items:flex-start;} .hero {grid-template-columns:1fr;} }
    .hero-left h1 { font-family:'Orbitron',sans-serif; font-size:clamp(2.2rem,4.8vw,3.4rem); letter-spacing:0.18em; margin-bottom:10px; }
    .hero-left .tagline { font-size:0.85rem; text-transform:uppercase; letter-spacing:0.22em; color:#9ca3af; margin-bottom:22px; }
    .hero-left .lead { font-size:1.05rem; line-height:1.7; color:#cbd5f5; margin-bottom:18px; }
    .hero-left .sub { font-size:0.95rem; line-height:1.6; color:#9ca3af; margin-bottom:24px; }
    .badges { display:flex; flex-wrap:wrap; gap:10px; margin-bottom:24px; }
    .badge { display:inline-flex; align-items:center; gap:6px; padding:4px 10px; border-radius:999px; background:rgba(15,23,42,0.9); border:1px solid rgba(148,163,184,0.5); font-size:0.75rem; letter-spacing:0.14em; text-transform:uppercase; color:#cbd5e1; }
    .badge span {font-size:0.9rem;}
    .btn-row { display:flex; flex-wrap:wrap; gap:12px; margin-bottom:24px; }
    .btn { display:inline-flex; align-items:center; justify-content:center; gap:8px; padding:10px 18px; border-radius:12px; border:none; font-size:0.95rem; font-weight:700; cursor:pointer; text-decoration:none; transition:all .25s ease; white-space:nowrap; }
    .btn-primary { background:linear-gradient(135deg,#06b6d4,#0891b2); color:white; box-shadow:0 12px 30px rgba(6,182,212,0.4); }
    .btn-primary:hover { transform:translateY(-1px); box-shadow:0 16px 40px rgba(6,182,212,0.6); }
    .btn-ghost { background:rgba(15,23,42,0.85); border:1px solid rgba(148,163,184,0.6); color:#e5e7eb; }
    .btn-ghost:hover { border-color:#06b6d4; color:#bae6fd; }
    .note { font-size:0.8rem; color:#9ca3af; }
    .card { background:rgba(15,23,42,0.82); backdrop-filter:blur(16px); border-radius:22px; padding:22px 20px; border:1px solid rgba(148,163,184,0.35); box-shadow:0 20px 55px rgba(0,0,0,0.7); position:relative; overflow:hidden; }
    .card::before { content:""; position:absolute; inset:-40%; background:radial-gradient(circle at 20% 0%,rgba(56,189,248,0.16),transparent 60%); opacity:0.7; pointer-events:none; }
    .card-inner { position:relative; z-index:1; }
    .scan { font-family:"Courier New",monospace; font-size:0.8rem; padding:10px 12px; border-radius:10px; background:rgba(2,6,23,0.92); border:1px solid rgba(56,189,248,0.5); margin-bottom:14px; position:relative; overflow:hidden; }
    .scan::after { content:""; position:absolute; top:0; left:-100%; width:100%; height:100%; background:linear-gradient(90deg,transparent,rgba(56,189,248,0.25),transparent); animation:scan 2.8s linear infinite; }
    @keyframes scan { from{left:-100%;} to{left:100%;} }
    .scan-line { display:flex; justify-content:space-between; margin-bottom:4px; }
    .scan-label { color:#64748b; }
    .scan-value { color:#4ade80; font-weight:700; }
    .list { display:grid; grid-template-columns:repeat(auto-fit,minmax(230px,1fr)); gap:14px; margin-top:14px; }
    .list-item-title { font-size:0.9rem; font-weight:700; margin-bottom:4px; }
    .list-item-desc { font-size:0.8rem; color:#9ca3af; line-height:1.4; }
    footer { margin-top:36px; padding-top:18px; border-top:1px solid rgba(51,65,85,0.9); font-size:0.8rem; color:#6b7280; display:flex; flex-wrap:wrap; gap:12px; justify-content:space-between; align-items:center; }
    .footer-links { display:flex; gap:16px; flex-wrap:wrap; }
    .footer-links a { color:#9ca3af; text-decoration:none; }
    .footer-links a:hover { color:#e5e7eb; }
  </style>
</head>
<body>
  <div class="shell">
    <header>
      <div>
        <div class="logo-main">NEUROEDULABS</div>
        <div style="font-size:0.8rem;color:#9ca3af;letter-spacing:0.14em;text-transform:uppercase;">Copernix OS · Edge AI dla dzieci ZE SPE</div>
      </div>
      <nav class="nav">
        <a href="https://neuroedulabs.onrender.com" target="_blank">Misja</a>
        <a href="#modules">Moduły</a>
        <a href="#docs">Materiały</a>
        <a href="#contact">Kontakt</a>
      </nav>
    </header>
    <main class="hero">
      <section class="hero-left">
        <h1>COPERNIX&nbsp;OS</h1>
        <div class="tagline">Neuro‑Inżynieria jutra, dziś</div>
        <p class="lead">Lokalny system Edge&nbsp;AI dla dzieci ze SPE, łączący regulację emocji z edukacją STEM. Zero‑cloud, pełna kontrola szkoły, projektowany wokół historii Dominika.</p>
        <p class="sub">Na tym etapie Copernix OS jest działającym <strong>demo TRL&nbsp;7</strong> – uruchamianym lokalnie na komputerze szkoły (MSI / PC z GPU), z modułami: Luna Mini Coach V2, Luna Architect (Roblox), Andromeda Bridge 3D i Cosmic Lab.</p>
        <div class="badges">
          <div class="badge">🛡️ <span>100% Local Computing</span></div>
          <div class="badge">🧬 <span>RODO / Art. 8 ready</span></div>
          <div class="badge">🛰️ <span>TRL 7 – Demo Stack</span></div>
        </div>
        <div class="btn-row">
          <a class="btn btn-primary" href="#" onclick="alert('System uruchamiany jest lokalnie na adresie http://localhost:8000/index.html na komputerze szkoly/Operatora. Ta strona jest tylko prezentacja online.'); return false;">🚀 Uruchom System (Demo lokalne)</a>
          <a class="btn btn-ghost" href="docs/Executive_Summary.pdf" target="_blank">📄 Pobierz Executive Summary (PDF)</a>
          <a class="btn btn-ghost" href="https://neuroedulabs.onrender.com" target="_blank">🏠 Przejdź do NeuroEduLabs</a>
        </div>
        <p class="note">Uwaga: Ta strona prezentuje Copernix OS dla grantodawców i partnerów. Pełne demo działa offline na urządzeniu szkoły (Edge&nbsp;AI, bez wysyłania danych dzieci do chmury).</p>
      </section>
      <section class="card" id="modules">
        <div class="card-inner">
          <div class="scan">
            <div class="scan-line"><span class="scan-label">SYSTEM STATUS</span><span class="scan-value">OPERATIONAL · DEMO MODE</span></div>
            <div class="scan-line"><span class="scan-label">AI ENGINES</span><span class="scan-value">Luna (DeepSeek-R1 8B) / Titan (Qwen-Coder 7B)</span></div>
            <div class="scan-line"><span class="scan-label">PROFILE</span><span class="scan-value">SPE / WWO · 6–12 LAT</span></div>
            <div class="scan-line"><span class="scan-label">PLATFORM</span><span class="scan-value">MSI / PC z GPU · Edge AI</span></div>
          </div>
          <h2 style="font-size:1.05rem;margin-bottom:8px;">Moduły Copernix OS (demo TRL 7)</h2>
          <p style="font-size:0.85rem;color:#9ca3af;margin-bottom:10px;">Jeden ekosystem, dwa wymiary: regulacja emocji + eksploracja 3D / kodowanie.</p>
          <div class="list">
            <div><div class="list-item-title">🧠 Luna Mini Coach V2</div><div class="list-item-desc">Grywalizowany coach regulacji emocji dla dzieci w wieku szkolnym. Misje "Ratunek po przerwie", "Przed sprawdzianem", punkty i nagrody.</div></div>
            <div><div class="list-item-title">🌍 Andromeda Bridge</div><div class="list-item-desc">Mostek 3D – mapa Olsztyna, ISS, Mars. Dziecko wydaje komendy głosowe, a system reaguje.</div></div>
            <div><div class="list-item-title">🪐 Cosmic Lab</div><div class="list-item-desc">Symulator fizyki – zderzanie planet, zmiana masy i orbit. Luna tłumaczy skutki w prostym języku (edukacja STEM + zabawa).</div></div>
            <div><div class="list-item-title">🧩 Luna Architect (Roblox)</div><div class="list-item-desc">Tryb "Twój głos tworzy światy". Komendy dziecka kod Lua prototypowy świat w Roblox Studio (offline, pod nadzorem nauczyciela).</div></div>
            <div><div class="list-item-title">💚 ChildEmotion AI</div><div class="list-item-desc">Edge-vision do analizy rysunków dziecka. Wspiera rozmowę rodzic–dziecko o emocjach (nie jest narzędziem diagnostycznym).</div></div>
            <div id="docs"><div class="list-item-title">📊 Panel Nauczyciela</div><div class="list-item-desc">Podgląd wykorzystania modułów, raporty z sesji i agregaty do IPET. W wersji produkcyjnej dane pozostają w szkole (RODO by design).</div></div>
          </div>
        </div>
      </section>
    </main>
    <footer id="contact">
      <div>© 2026 NeuroEduLabs · Copernix OS · Olsztyn, Warmia-Mazury</div>
      <div class="footer-links">
        <a href="mailto:kontakt@neuroedulabs.pl">kontakt@neuroedulabs.pl</a>
        <a href="https://neuroedulabs.onrender.com" target="_blank">Strona NeuroEduLabs</a>
        <a href="docs/Executive_Summary.pdf" target="_blank">Executive Summary</a>
      </div>
    </footer>
  </div>
</body>
</html>
