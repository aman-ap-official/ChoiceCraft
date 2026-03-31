<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>ChoiceCraft - Interactive Story Engine</title>
  <!-- Bootstrap 5 CSS + Icons + Google Fonts -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
  <!-- GSAP Library -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
  <style>
    body {
      font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif;
      background: linear-gradient(145deg, #f8fafc 0%, #eef2f6 100%);
      scroll-behavior: smooth;
    }
    .hero-section {
      background: linear-gradient(135deg, #0b1120 0%, #19233c 100%);
      color: white;
      border-bottom: 4px solid #ffb347;
      position: relative;
      overflow: hidden;
    }
    .hero-section::before {
      content: '';
      position: absolute;
      top: -30%;
      right: -10%;
      width: 300px;
      height: 300px;
      background: radial-gradient(circle, rgba(255,180,71,0.2) 0%, rgba(0,0,0,0) 70%);
      border-radius: 50%;
      pointer-events: none;
    }
    .btn-glow {
      transition: all 0.2s ease;
      box-shadow: 0 4px 14px 0 rgba(0,0,0,0.2);
    }
    .btn-glow:hover {
      transform: translateY(-3px);
      box-shadow: 0 10px 20px -5px rgba(0,0,0,0.3);
    }
    .feature-card {
      border: none;
      border-radius: 28px;
      background: rgba(255,255,255,0.75);
      backdrop-filter: blur(4px);
      transition: all 0.25s ease;
      box-shadow: 0 10px 25px -12px rgba(0,0,0,0.1);
    }
    .feature-card:hover {
      transform: translateY(-8px);
      background: white;
      box-shadow: 0 25px 35px -12px rgba(0,0,0,0.15);
    }
    .screenshot-img {
      transition: transform 0.3s ease, box-shadow 0.3s;
      cursor: pointer;
      border-radius: 20px;
      box-shadow: 0 12px 20px -12px rgba(0,0,0,0.25);
    }
    .screenshot-img:hover {
      transform: scale(1.02);
      box-shadow: 0 20px 30px -12px rgba(0,0,0,0.3);
    }
    .code-block {
      background: #1e293b;
      color: #e2e8f0;
      border-radius: 18px;
      padding: 1rem 1.5rem;
      font-family: 'Fira Code', monospace;
      font-size: 0.85rem;
      border-left: 5px solid #ffb347;
    }
    .badge-soft {
      background: #eef2ff;
      color: #1e293b;
      padding: 8px 16px;
      border-radius: 40px;
      font-weight: 500;
    }
    .open-source-heart {
      background: #0f172a;
      color: #facc15;
    }
    footer a {
      text-decoration: none;
      color: #ffb347;
      transition: 0.2s;
    }
    footer a:hover {
      color: white;
      text-decoration: underline;
    }
    .gsap-fade {
      opacity: 0;
      transform: translateY(20px);
    }
  </style>
</head>
<body>

<div class="container-lg px-4 py-5">
  
  <!-- Hero Section with GSAP animation trigger -->
  <div class="hero-section rounded-4 p-4 p-md-5 mb-5 text-center text-md-start">
    <div class="row align-items-center g-4">
      <div class="col-md-8 gsap-fade" id="heroTitle">
        <h1 class="display-2 fw-bold mb-3">
          <i class="bi bi-controller"></i> ChoiceCraft
          <span class="badge bg-warning text-dark ms-3 fs-6">v1.0</span>
        </h1>
        <p class="lead fs-4">An Interactive Story Engine — build branching narratives with pure JSON.</p>
        <div class="d-flex flex-wrap gap-3 mt-4">
          <a href="https://aman-ap-official.github.io/ChoiceCraft/" target="_blank" class="btn btn-warning btn-lg btn-glow px-4 fw-semibold">
            <i class="bi bi-play-fill"></i> Live Demo
          </a>
          <a href="#contribute" class="btn btn-outline-light btn-lg px-4">
            <i class="bi bi-github"></i> Contribute Now
          </a>
        </div>
        <div class="mt-4">
          <span class="badge-soft me-2"><i class="bi bi-star-fill text-warning"></i> Open Source</span>
          <span class="badge-soft me-2"><i class="bi bi-code-slash"></i> Vanilla JS</span>
          <span class="badge-soft"><i class="bi bi-journal-bookmark-fill"></i> Writer Friendly</span>
        </div>
      </div>
      <div class="col-md-4 text-center gsap-fade" id="heroIcon">
        <i class="bi bi-book-half" style="font-size: 8rem; opacity: 0.85;"></i>
      </div>
    </div>
  </div>

  <!-- BADGES + OPEN SOURCE shout -->
  <div class="d-flex flex-wrap justify-content-center gap-3 mb-5">
    <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="MIT License"></a>
    <a href="http://makeapullrequest.com"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" alt="PRs Welcome"></a>
    <img src="https://img.shields.io/badge/Open%20Source-❤️-red" alt="Open Source Love">
    <img src="https://img.shields.io/badge/contributions-welcome-8A2BE2" alt="Contributions Welcome">
  </div>

  <!-- FEATURES SECTION: cards with Bootstrap grid -->
  <div class="row g-4 mb-5">
    <div class="col-md-3 col-sm-6 gsap-fade feature-card-ani">
      <div class="feature-card card h-100 p-4">
        <div class="card-body text-center">
          <i class="bi bi-filetype-json fs-1 text-warning"></i>
          <h4 class="card-title mt-3">Data‑Driven</h4>
          <p class="card-text">Entire story logic lives inside a single <code>story.json</code> — no coding required for writers.</p>
        </div>
      </div>
    </div>
    <div class="col-md-3 col-sm-6 gsap-fade feature-card-ani">
      <div class="feature-card card h-100 p-4">
        <div class="card-body text-center">
          <i class="bi bi-images fs-1 text-primary"></i>
          <h4 class="card-title mt-3">Dynamic Visuals</h4>
          <p class="card-text">Every scene supports unique background images. Immersive storytelling made easy.</p>
        </div>
      </div>
    </div>
    <div class="col-md-3 col-sm-6 gsap-fade feature-card-ani">
      <div class="feature-card card h-100 p-4">
        <div class="card-body text-center">
          <i class="bi bi-phone fs-1 text-success"></i>
          <h4 class="card-title mt-3">Fully Responsive</h4>
          <p class="card-text">Plays beautifully on desktop, tablet, or mobile — fluid UI out of the box.</p>
        </div>
      </div>
    </div>
    <div class="col-md-3 col-sm-6 gsap-fade feature-card-ani">
      <div class="feature-card card h-100 p-4">
        <div class="card-body text-center">
          <i class="bi bi-gem fs-1 text-info"></i>
          <h4 class="card-title mt-3">Minimalist Core</h4>
          <p class="card-text">Zero heavy dependencies — just vanilla HTML, CSS, and modern JavaScript.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- SCREENSHOTS GALLERY (from ss folder) -->
  <div class="my-5 pt-3">
    <div class="text-center mb-4">
      <h2 class="fw-bold"><i class="bi bi-camera-reels"></i> Gameplay Previews</h2>
      <p class="lead text-secondary">See ChoiceCraft in action — branching choices & rich visuals</p>
    </div>
    <div class="row g-4 justify-content-center">
      <div class="col-md-4">
        <img src="ss/game ss 1.png" class="img-fluid screenshot-img w-100" alt="ChoiceCraft scene 1" loading="lazy">
        <p class="text-center mt-2 fw-semibold">📖 Scene with dynamic choices</p>
      </div>
      <div class="col-md-4">
        <img src="ss/game ss 2.png" class="img-fluid screenshot-img w-100" alt="ChoiceCraft scene 2" loading="lazy">
        <p class="text-center mt-2 fw-semibold">🎨 Thematic backgrounds</p>
      </div>
      <div class="col-md-4">
        <img src="ss/game ss 3.png" class="img-fluid screenshot-img w-100" alt="ChoiceCraft scene 3" loading="lazy">
        <p class="text-center mt-2 fw-semibold">⚡ Clean, modern UI</p>
      </div>
    </div>
  </div>

  <!-- WHY CONTRIBUTE + OPEN SOURCE MESSAGE -->
  <div class="bg-light rounded-4 p-4 p-md-5 my-5 shadow-sm" id="contribute">
    <div class="row align-items-center">
      <div class="col-md-7">
        <h2 class="fw-bold"><i class="bi bi-heart-fill text-danger"></i> Open Source & Contributions</h2>
        <p class="fs-5 mt-3">ChoiceCraft is built for <strong>writers, storytellers, and developers</strong>. Whether you want to craft a new adventure or improve the engine, every contribution matters.</p>
        <ul class="list-unstyled">
          <li class="mb-2"><i class="bi bi-pencil-square text-warning me-2"></i> <strong>For Writers:</strong> No need to touch the JS — just edit <code>story.json</code> and expand your narrative universe.</li>
          <li class="mb-2"><i class="bi bi-brush text-info me-2"></i> <strong>For UI/UX lovers:</strong> Experiment with themes, animations, and better UX flows.</li>
          <li class="mb-2"><i class="bi bi-megaphone text-success me-2"></i> <strong>For Devs:</strong> Add inventory systems, sound effects, or local save states — the sandbox is yours.</li>
        </ul>
        <a href="https://github.com/aman-ap-official/ChoiceCraft" class="btn btn-dark btn-lg mt-2"><i class="bi bi-star-fill"></i> Star & Fork on GitHub</a>
      </div>
      <div class="col-md-5 text-center">
        <i class="bi bi-github" style="font-size: 7rem; color: #1e293b;"></i>
        <div class="mt-3 p-3 open-source-heart rounded-3 text-white">
          <i class="bi bi-box-arrow-up-right"></i> Pull Requests? → Always welcome!
        </div>
      </div>
    </div>
  </div>

  <!-- TECH STACK & HOW TO ADD SCENE -->
  <div class="row g-5 mb-5">
    <div class="col-md-5">
      <div class="bg-white rounded-4 p-4 h-100 shadow-sm">
        <h3><i class="bi bi-tools"></i> Tech Stack</h3>
        <hr>
        <div class="d-flex flex-wrap gap-2 mb-3">
          <span class="badge bg-dark fs-6 p-2"><i class="bi bi-filetype-html"></i> HTML5</span>
          <span class="badge bg-dark fs-6 p-2"><i class="bi bi-filetype-css"></i> CSS3 (Flexbox/Grid)</span>
          <span class="badge bg-dark fs-6 p-2"><i class="bi bi-filetype-js"></i> Vanilla JS (ES6+)</span>
          <span class="badge bg-dark fs-6 p-2"><i class="bi bi-filetype-json"></i> JSON State</span>
          <span class="badge bg-dark fs-6 p-2"><i class="bi bi-cloud-arrow-up"></i> Fetch API</span>
        </div>
        <p class="mt-3">Lightweight, modern, and ready for your next interactive epic.</p>
        <div class="alert alert-warning mt-3">
          <i class="bi bi-info-circle"></i> <strong>Demo-ready</strong> — check the <a href="https://aman-ap-official.github.io/ChoiceCraft/" target="_blank">Live Demo</a> to see the engine in action.
        </div>
      </div>
    </div>
    <div class="col-md-7">
      <div class="bg-white rounded-4 p-4 shadow-sm">
        <h3><i class="bi bi-node-plus"></i> How to add a new scene</h3>
        <p>Simply add a new JSON object inside your <code>story.json</code> file. Each scene can contain text, image URL, and choices:</p>
        <div class="code-block">
          <pre style="margin:0; color:#facc15;">"scene_example": {
  "text": "You stand before an ancient doorway...",
  "image": "https://example.com/doorway.jpg",
  "choices": [
    { "text": "Open the door", "next": "scene_hall" },
    { "text": "Walk away", "next": "scene_start" }
  ]
}</pre>
        </div>
        <p class="mt-3 text-muted"><i class="bi bi-git"></i> Pro tip: Link scenes with unique IDs and watch your branching story come to life!</p>
      </div>
    </div>
  </div>

  <!-- LICENSE & FOOTER -->
  <div class="text-center pt-4 border-top">
    <p class="mb-2">📜 <strong>ChoiceCraft</strong> is released under the <a href="LICENSE">MIT License</a> — free for personal & commercial use.</p>
    <p class="mb-0">
      <i class="bi bi-github"></i> <a href="https://github.com/aman-ap-official/ChoiceCraft" class="text-decoration-none">GitHub Repository</a> &nbsp;|&nbsp;
      <i class="bi bi-chat-heart-fill text-danger"></i> Open Source — <strong>every contribution builds better stories</strong>
    </p>
    <p class="mt-2 text-secondary small">Built with 💻 Vanilla JS &nbsp;|&nbsp; ✨ README styled with Bootstrap 5 + GSAP micro-animations</p>
  </div>
</div>

<!-- GSAP Animation for smooth reveal -->
<script>
  gsap.registerPlugin(); 
  window.addEventListener('load', () => {
    // fade-up animation for hero and feature cards
    gsap.fromTo(".gsap-fade", 
      { opacity: 0, y: 30 },
      { opacity: 1, y: 0, duration: 1, stagger: 0.15, ease: "power3.out" }
    );
    gsap.fromTo(".feature-card-ani", 
      { scale: 0.95, opacity: 0 },
      { scale: 1, opacity: 1, duration: 0.6, stagger: 0.1, delay: 0.3, ease: "backOut" }
    );
    // tiny floating effect for hero icon
    gsap.to("#heroIcon i", {
      y: -8,
      duration: 2,
      repeat: -1,
      yoyo: true,
      ease: "sine.inOut"
    });
  });
</script>

<!-- Bootstrap JS Bundle (optional for toggles etc) -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>