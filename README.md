<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sanjay C — AI/ML Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --cyan: #00F7FF;
    --green: #00FF41;
    --dark: #000000;
    --mid: #0f2027;
    --glass: rgba(0,247,255,0.05);
    --border: rgba(0,247,255,0.2);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: #000;
    color: #c0c0c0;
    font-family: 'Rajdhani', sans-serif;
    overflow-x: hidden;
    min-height: 100vh;
  }

  /* ── CANVAS RAIN ── */
  #matrix-canvas {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 0;
    opacity: 0.18;
  }

  /* ── SCANLINE OVERLAY ── */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.08) 2px,
      rgba(0,0,0,0.08) 4px
    );
    pointer-events: none;
    z-index: 1;
  }

  /* ── WRAPPER ── */
  .wrapper {
    position: relative;
    z-index: 2;
    max-width: 900px;
    margin: 0 auto;
    padding: 0 24px 80px;
  }

  /* ── HEADER WAVE ── */
  .header-wave {
    width: calc(100% + 48px);
    margin-left: -24px;
    overflow: hidden;
    line-height: 0;
    position: relative;
  }
  .header-wave svg { display: block; }

  .header-content {
    text-align: center;
    padding: 56px 24px 40px;
    position: relative;
  }
  .header-content::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 0%, rgba(0,247,255,0.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .glitch-name {
    font-family: 'Orbitron', monospace;
    font-size: clamp(2.4rem, 6vw, 4rem);
    font-weight: 900;
    color: var(--cyan);
    text-shadow: 0 0 20px var(--cyan), 0 0 40px rgba(0,247,255,0.4);
    letter-spacing: 0.06em;
    position: relative;
    display: inline-block;
    animation: glitch 4s infinite;
  }
  @keyframes glitch {
    0%,94%,100% { text-shadow: 0 0 20px var(--cyan), 0 0 40px rgba(0,247,255,0.4); transform: none; }
    95% { transform: translate(-2px, 0) skewX(-5deg); text-shadow: -3px 0 #FF0055, 3px 0 var(--green); }
    97% { transform: translate(2px, 0) skewX(3deg); text-shadow: 3px 0 #FF0055, -3px 0 var(--cyan); }
  }

  .role-tag {
    font-family: 'Share Tech Mono', monospace;
    font-size: 1rem;
    color: var(--green);
    letter-spacing: 0.14em;
    margin-top: 10px;
    opacity: 0;
    animation: fadeUp 0.8s 0.6s ease forwards;
  }

  /* ── TYPING LINE ── */
  .typing-wrap {
    display: flex;
    justify-content: center;
    margin: 24px 0;
  }
  .typing-text {
    font-family: 'Share Tech Mono', monospace;
    font-size: 1.05rem;
    color: var(--green);
    border-right: 2px solid var(--green);
    white-space: nowrap;
    overflow: hidden;
    width: 0;
    animation: typeIn 2.8s steps(40,end) 1s forwards, blink 0.7s step-end infinite;
  }
  @keyframes typeIn { to { width: 28ch; } }
  @keyframes blink { 50% { border-color: transparent; } }

  /* ── SECTION ── */
  .section {
    margin-top: 48px;
    opacity: 0;
    transform: translateY(24px);
    animation: fadeUp 0.7s ease forwards;
  }
  .section:nth-child(2) { animation-delay: 0.2s; }
  .section:nth-child(3) { animation-delay: 0.35s; }
  .section:nth-child(4) { animation-delay: 0.5s; }
  .section:nth-child(5) { animation-delay: 0.65s; }
  .section:nth-child(6) { animation-delay: 0.8s; }
  .section:nth-child(7) { animation-delay: 0.95s; }
  .section:nth-child(8) { animation-delay: 1.1s; }
  @keyframes fadeUp { to { opacity: 1; transform: none; } }

  .section-title {
    font-family: 'Orbitron', monospace;
    font-size: 0.78rem;
    letter-spacing: 0.22em;
    color: var(--cyan);
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 18px;
  }
  .section-title::before { content: '//'; color: var(--green); }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ── YAML CARD ── */
  .yaml-card {
    background: var(--glass);
    border: 1px solid var(--border);
    border-left: 3px solid var(--cyan);
    border-radius: 6px;
    padding: 22px 28px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.88rem;
    line-height: 2;
    position: relative;
    overflow: hidden;
  }
  .yaml-card::before {
    content: '';
    position: absolute;
    top: -40px; right: -40px;
    width: 180px; height: 180px;
    background: radial-gradient(circle, rgba(0,247,255,0.06), transparent 70%);
    pointer-events: none;
  }
  .yaml-key { color: var(--cyan); }
  .yaml-val { color: #e0e0e0; }
  .yaml-val.green { color: var(--green); }

  /* ── STATS ROW ── */
  .stats-row {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
  }
  .stats-row img {
    flex: 1;
    min-width: 220px;
    border-radius: 8px;
    border: 1px solid var(--border);
    transition: border-color 0.3s, box-shadow 0.3s;
  }
  .stats-row img:hover {
    border-color: var(--cyan);
    box-shadow: 0 0 18px rgba(0,247,255,0.25);
  }

  /* ── PROJECT CARDS ── */
  .project-card {
    background: var(--glass);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 22px 26px;
    margin-bottom: 16px;
    transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
    position: relative;
    overflow: hidden;
  }
  .project-card:hover {
    border-color: var(--cyan);
    transform: translateX(4px);
    box-shadow: -4px 0 24px rgba(0,247,255,0.15), 0 0 24px rgba(0,247,255,0.06);
  }
  .project-card::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 3px;
    background: var(--cyan);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .project-card:hover::before { opacity: 1; }

  .project-star {
    position: absolute;
    top: 12px; right: 16px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.7rem;
    color: #FFD700;
    background: rgba(255,215,0,0.08);
    border: 1px solid rgba(255,215,0,0.3);
    padding: 2px 10px;
    border-radius: 20px;
    letter-spacing: 0.1em;
  }

  .project-title {
    font-family: 'Orbitron', monospace;
    font-size: 0.95rem;
    color: var(--cyan);
    font-weight: 700;
    margin-bottom: 6px;
  }
  .project-link {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.75rem;
    color: var(--green);
    text-decoration: none;
    opacity: 0.7;
    transition: opacity 0.2s;
    display: block;
    margin-bottom: 12px;
  }
  .project-link:hover { opacity: 1; }

  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 12px;
  }
  .tag {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.72rem;
    color: var(--cyan);
    border: 1px solid var(--border);
    padding: 3px 10px;
    border-radius: 20px;
    opacity: 0.8;
    transition: opacity 0.2s, border-color 0.2s;
  }
  .project-card:hover .tag { opacity: 1; border-color: rgba(0,247,255,0.5); }

  .bullet-list { list-style: none; padding: 0; }
  .bullet-list li {
    font-size: 0.9rem;
    padding: 3px 0 3px 18px;
    position: relative;
    color: #b0b8c0;
    line-height: 1.6;
  }
  .bullet-list li::before {
    content: '›';
    position: absolute;
    left: 0;
    color: var(--cyan);
    font-size: 1rem;
  }

  /* ── TECH ICONS ROW ── */
  .tech-img {
    display: block;
    margin: 0 auto 12px;
    border-radius: 6px;
  }
  .badges-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
  }
  .badges-row img { border-radius: 4px; }

  /* ── CONNECT ── */
  .connect-row {
    display: flex;
    justify-content: center;
  }
  .connect-row a img { border-radius: 6px; transition: transform 0.25s; }
  .connect-row a:hover img { transform: translateY(-3px); }

  /* ── MOTTO TYPING ── */
  .motto-lines {
    text-align: center;
    font-family: 'Share Tech Mono', monospace;
    font-size: 1.02rem;
    line-height: 2.4;
  }
  .motto-line {
    display: block;
    color: var(--cyan);
    opacity: 0;
    animation: fadeUp 0.6s ease forwards;
  }
  .motto-line:nth-child(1) { animation-delay: 1.5s; }
  .motto-line:nth-child(2) { animation-delay: 2s; }
  .motto-line:nth-child(3) { animation-delay: 2.5s; }

  /* ── FOOTER WAVE ── */
  .footer-wave {
    width: calc(100% + 48px);
    margin-left: -24px;
    margin-top: 60px;
    overflow: hidden;
    line-height: 0;
  }
  .footer-wave svg { display: block; }

  /* ── DIVIDER ── */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 0;
  }

  /* ── SCROLL GLOW ── */
  .glow-dot {
    display: inline-block;
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--green);
    box-shadow: 0 0 8px var(--green);
    animation: pulse 1.4s ease-in-out infinite;
    margin-right: 8px;
  }
  @keyframes pulse { 50% { transform: scale(1.6); opacity: 0.5; } }

  /* ── SNAKE PLACEHOLDER ── */
  .snake-wrap {
    text-align: center;
    padding: 24px;
    border: 1px dashed var(--border);
    border-radius: 8px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.82rem;
    color: var(--green);
    opacity: 0.6;
  }
</style>
</head>
<body>

<canvas id="matrix-canvas"></canvas>

<div class="wrapper">

  <!-- HEADER -->
  <div class="header-content">
    <h1 class="glitch-name">SANJAY C</h1>
    <p class="role-tag">🌙 &nbsp;MACHINE LEARNING ENGINEER &nbsp;|&nbsp; AI DEVELOPER</p>
    <div class="typing-wrap">
      <span class="typing-text">Building AI That Matters 🚀</span>
    </div>
    <div class="typing-wrap" style="margin-top:6px;">
      <img src="https://readme-typing-svg.herokuapp.com?size=18&duration=3000&color=00FF00&center=true&vCenter=true&width=600&lines=01010101010101010101;Entering+the+Matrix...;AI+%26+ML+Engineer;Building+Intelligent+Systems" alt="Matrix typing effect"/>
    </div>
  </div>

  <div class="divider"></div>

  <!-- AI PROFILE -->
  <div class="section">
    <div class="section-title">AI PROFILE</div>
    <div class="yaml-card">
      <div><span class="yaml-key">Name:</span>       <span class="yaml-val">Sanjay C</span></div>
      <div><span class="yaml-key">Role:</span>       <span class="yaml-val">Machine Learning Engineer</span></div>
      <div><span class="yaml-key">Education:</span>  <span class="yaml-val">B.Tech AI &amp; ML <span style="color:#FFD700">(CGPA: 8.35)</span></span></div>
      <div><span class="yaml-key">College:</span>    <span class="yaml-val">Saveetha Engineering College</span></div>
      <div><span class="yaml-key">Focus:</span>      <span class="yaml-val">AI, ML, Data Science</span></div>
      <div><span class="yaml-key">Status:</span>     <span class="yaml-val green"><span class="glow-dot"></span>Learning | Building | Growing 🚀</span></div>
    </div>
  </div>

  <!-- LIVE STATS -->
  <div class="section">
    <div class="section-title">LIVE STATUS</div>
    <div class="stats-row">
      <img src="https://github-readme-stats.vercel.app/api?username=c-sanjay&show_icons=true&theme=tokyonight&hide_border=true&bg_color=000000" alt="GitHub Stats"/>
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=c-sanjay&layout=compact&theme=tokyonight&hide_border=true&bg_color=000000" alt="Top Languages"/>
    </div>
  </div>

  <!-- STAR PROJECT -->
  <div class="section">
    <div class="section-title">STAR PROJECT</div>
    <div class="project-card">
      <span class="project-star">🔥 FEATURED</span>
      <div class="project-title">📚 BookVision RAG Chatbot</div>
      <a class="project-link" href="https://github.com/c-sanjay/BookVision-RAG-Chatbot" target="_blank">
        github.com/c-sanjay/BookVision-RAG-Chatbot
      </a>
      <ul class="bullet-list">
        <li>FastAPI-based RAG chatbot for PDFs &amp; images</li>
        <li>Async ingestion with background processing</li>
        <li>Embedding-based semantic search</li>
        <li>Context-aware intelligent responses</li>
        <li>Book summarization &amp; analytics APIs</li>
      </ul>
      <div class="project-tags">
        <span class="tag">FastAPI</span>
        <span class="tag">RAG</span>
        <span class="tag">Embeddings</span>
        <span class="tag">LLM</span>
        <span class="tag">PDF</span>
      </div>
    </div>
  </div>

  <!-- OTHER PROJECTS -->
  <div class="section">
    <div class="section-title">OTHER PROJECTS</div>

    <div class="project-card">
      <div class="project-title">🐶 AI Classifier (CNN – PyTorch)</div>
      <a class="project-link" href="https://github.com/c-sanjay/AI-Classifier-Identifying-Cats-Dogs-Pandas-with-PyTorch" target="_blank">
        github.com/c-sanjay/AI-Classifier-Identifying-Cats-Dogs-Pandas-with-PyTorch
      </a>
      <ul class="bullet-list">
        <li>Deep learning image classifier</li>
        <li>Data preprocessing &amp; augmentation</li>
        <li>CNN architecture design</li>
        <li>Model training &amp; evaluation</li>
      </ul>
      <div class="project-tags">
        <span class="tag">PyTorch</span>
        <span class="tag">CNN</span>
        <span class="tag">Computer Vision</span>
        <span class="tag">Deep Learning</span>
      </div>
    </div>

    <div class="project-card">
      <div class="project-title">📧 Spam Mail Detection (SVM)</div>
      <a class="project-link" href="https://github.com/c-sanjay/Implementation-of-SVM-For-Spam-Mail-Detection" target="_blank">
        github.com/c-sanjay/Implementation-of-SVM-For-Spam-Mail-Detection
      </a>
      <ul class="bullet-list">
        <li>SVM-based spam classifier</li>
        <li>Text vectorization (CountVectorizer)</li>
        <li>Data preprocessing &amp; analysis</li>
        <li>Prediction system</li>
      </ul>
      <div class="project-tags">
        <span class="tag">SVM</span>
        <span class="tag">NLP</span>
        <span class="tag">Scikit-Learn</span>
        <span class="tag">Classification</span>
      </div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-title">TECH STACK</div>
    <img class="tech-img" src="https://skillicons.dev/icons?i=python,java,c,mysql,git,github,vscode&theme=dark" alt="Tech icons"/>
    <div class="badges-row">
      <img src="https://img.shields.io/badge/NumPy-000000?style=for-the-badge&logo=numpy&logoColor=00F7FF" alt="NumPy"/>
      <img src="https://img.shields.io/badge/Pandas-000000?style=for-the-badge&logo=pandas&logoColor=00F7FF" alt="Pandas"/>
      <img src="https://img.shields.io/badge/ScikitLearn-000000?style=for-the-badge&logo=scikit-learn&logoColor=00F7FF" alt="Scikit Learn"/>
      <img src="https://img.shields.io/badge/PyTorch-000000?style=for-the-badge&logo=pytorch&logoColor=00F7FF" alt="PyTorch"/>
      <img src="https://img.shields.io/badge/FastAPI-000000?style=for-the-badge&logo=fastapi&logoColor=00F7FF" alt="FastAPI"/>
    </div>
  </div>

  <!-- CONTRIBUTION SNAKE -->
  <div class="section">
    <div class="section-title">CONTRIBUTION MATRIX</div>
    <div class="snake-wrap">
      🐍 Matrix snake animation loads from:<br/>
      github.com/c-sanjay/c-sanjay → output branch → github-contribution-grid-snake.svg
    </div>
    <img src="https://github.com/c-sanjay/c-sanjay/blob/output/github-contribution-grid-snake.svg" alt="Snake animation" style="display:block;max-width:100%;margin:12px auto 0;border-radius:6px;" onerror="this.style.display='none'"/>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-title">CONNECT</div>
    <div class="connect-row">
      <a href="https://www.linkedin.com/in/sanjayc2006" target="_blank">
        <img src="https://img.shields.io/badge/LinkedIn-000000?style=for-the-badge&logo=linkedin&logoColor=00F7FF" alt="LinkedIn"/>
      </a>
    </div>
  </div>

  <!-- MOTTO -->
  <div class="section" style="margin-top:52px;">
    <div class="motto-lines">
      <span class="motto-line">▸ Turning Data Into Intelligence</span>
      <span class="motto-line">▸ Building AI That Matters</span>
      <span class="motto-line">▸ Welcome to the Future 🚀</span>
    </div>
  </div>

  <!-- FOOTER WAVE -->
  <div class="footer-wave">
    <svg viewBox="0 0 1440 120" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none" height="80">
      <defs>
        <linearGradient id="waveGrad2" x1="0%" y1="0%" x2="100%" y2="0%">
          <stop offset="0%" stop-color="#000000"/>
          <stop offset="50%" stop-color="#0f2027"/>
          <stop offset="100%" stop-color="#000000"/>
        </linearGradient>
      </defs>
      <path d="M0,60 C360,120 1080,0 1440,60 L1440,120 L0,120 Z" fill="url(#waveGrad2)"/>
    </svg>
  </div>

</div><!-- /wrapper -->

<script>
/* ── MATRIX RAIN ── */
const canvas = document.getElementById('matrix-canvas');
const ctx = canvas.getContext('2d');
let cols, drops;

function resize() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  cols = Math.floor(canvas.width / 18);
  drops = Array(cols).fill(1);
}
resize();
window.addEventListener('resize', resize);

const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノ@#$%^&*()[]{}';

function rain() {
  ctx.fillStyle = 'rgba(0,0,0,0.05)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.fillStyle = '#00FF41';
  ctx.font = '14px Share Tech Mono, monospace';

  for (let i = 0; i < drops.length; i++) {
    const ch = chars[Math.floor(Math.random() * chars.length)];
    ctx.fillText(ch, i * 18, drops[i] * 18);
    if (drops[i] * 18 > canvas.height && Math.random() > 0.975) drops[i] = 0;
    drops[i]++;
  }
}
setInterval(rain, 40);
</script>
</body>
</html>
