# html-and-CSS
html and CSS  petalbloom<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PetalBloom — Cape Town Florist</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />

  <style>
    /* ─── Reset & Base ─── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --cream:   #FFFDF5;
      --sage:    #2F5F48;
      --sage-lt: #63866B;
      --blush:   #F5D9CF;
      --blush-dk:#D4917A;
      --bark:    #3A2C24;
      --mist:    #EDF0EC;
      --text:    #2C2218;
      --ff-head: 'Cormorant Garamond', Georgia, serif;
      --ff-body: 'DM Sans', system-ui, sans-serif;
      --max:     1200px;
      --nav-h:   72px;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--cream);
      color: var(--text);
      font-family: var(--ff-body);
      font-weight: 300;
      line-height: 1.65;
      -webkit-font-smoothing: antialiased;
    }

    img { display: block; max-width: 100%; }
    a { color: inherit; text-decoration: none; }
    ul { list-style: none; }

    /* ─── Utility ─── */
    .container {
      width: min(var(--max), 100%);
      margin-inline: auto;
      padding-inline: clamp(1.25rem, 4vw, 3rem);
    }

    .tag {
      display: inline-block;
      font-family: var(--ff-body);
      font-size: 0.65rem;
      font-weight: 500;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--sage);
      margin-bottom: 1rem;
    }

    .btn {
      display: inline-block;
      font-family: var(--ff-body);
      font-size: 0.8rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.85rem 2.2rem;
      border: 1.5px solid currentColor;
      cursor: pointer;
      transition: background 0.25s, color 0.25s;
    }
    .btn-sage { background: var(--sage); color: var(--cream); border-color: var(--sage); }
    .btn-sage:hover { background: var(--bark); border-color: var(--bark); }
    .btn-outline { background: transparent; color: var(--cream); border-color: var(--cream); }
    .btn-outline:hover { background: var(--cream); color: var(--sage); }
    .btn-dark { background: transparent; color: var(--sage); border-color: var(--sage); }
    .btn-dark:hover { background: var(--sage); color: var(--cream); }

    /* ─── NAV ─── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      height: var(--nav-h);
      display: flex;
      align-items: center;
      z-index: 100;
      background: rgba(255,253,245,0.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(47,95,72,0.12);
    }

    .nav-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
    }

    .nav-logo {
      font-family: var(--ff-head);
      font-size: 1.65rem;
      font-weight: 600;
      letter-spacing: 0.02em;
      color: var(--sage);
    }
    .nav-logo span { color: var(--blush-dk); }

    .nav-links {
      display: flex;
      gap: 2.5rem;
      align-items: center;
    }

    .nav-links a {
      font-size: 0.78rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--bark);
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--sage); }

    .nav-cta {
      font-size: 0.75rem !important;
      font-weight: 500 !important;
      background: var(--sage);
      color: var(--cream) !important;
      padding: 0.55rem 1.4rem;
      letter-spacing: 0.12em !important;
      transition: background 0.25s !important;
    }
    .nav-cta:hover { background: var(--bark); color: var(--cream) !important; }

    /* ─── HERO ─── */
    .hero {
      min-height: 100vh;
      padding-top: var(--nav-h);
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      overflow: hidden;
      position: relative;
    }

    .hero-content {
      padding: clamp(3rem, 8vh, 7rem) clamp(1.25rem, 4vw, 3rem) clamp(3rem, 8vh, 7rem) clamp(1.25rem, 6vw, 6rem);
    }

    .hero-content .tag { color: var(--blush-dk); }

    .hero-heading {
      font-family: var(--ff-head);
      font-size: clamp(3.5rem, 7vw, 6.5rem);
      font-weight: 300;
      line-height: 0.92;
      letter-spacing: -0.02em;
      color: var(--bark);
      margin-bottom: 1.5rem;
    }
    .hero-heading em {
      font-style: italic;
      color: var(--sage);
    }

    .hero-body {
      max-width: 36ch;
      font-size: 1rem;
      color: var(--sage-lt);
      margin-bottom: 2.5rem;
      line-height: 1.7;
    }

    .hero-image {
      height: 100vh;
      position: relative;
      overflow: hidden;
    }

    .hero-image::before {
      content: '';
      position: absolute;
      inset: 0;
      background:
        radial-gradient(ellipse 60% 60% at 60% 40%, rgba(245,217,207,0.35) 0%, transparent 70%),
        linear-gradient(135deg, rgba(47,95,72,0.08) 0%, rgba(209,218,208,0.15) 100%);
      z-index: 1;
    }

    /* Decorative floral placeholder when no image is set */
    .hero-floral {
      width: 100%;
      height: 100%;
      background:
        radial-gradient(circle at 30% 25%, rgba(245,217,207,0.7) 0%, transparent 40%),
        radial-gradient(circle at 70% 70%, rgba(209,218,208,0.6) 0%, transparent 45%),
        radial-gradient(circle at 55% 40%, rgba(47,95,72,0.12) 0%, transparent 50%),
        linear-gradient(160deg, var(--mist) 0%, var(--blush) 50%, var(--cream) 100%);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .floral-svg {
      width: 55%;
      opacity: 0.55;
    }

    /* ─── SECTION: Collections ─── */
    .collections {
      padding: clamp(4rem, 10vh, 9rem) 0;
      background: var(--mist);
    }

    .section-header {
      text-align: center;
      margin-bottom: clamp(2.5rem, 5vw, 4rem);
    }

    .section-title {
      font-family: var(--ff-head);
      font-size: clamp(2rem, 4vw, 3.5rem);
      font-weight: 300;
      line-height: 1.1;
      letter-spacing: -0.015em;
      color: var(--bark);
      margin-bottom: 1rem;
    }
    .section-title em { font-style: italic; color: var(--sage); }

    .section-sub {
      max-width: 54ch;
      margin-inline: auto;
      color: var(--sage-lt);
      font-size: 0.95rem;
    }

    .collection-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1.5px;
    }

    .collection-card {
      position: relative;
      aspect-ratio: 3/4;
      overflow: hidden;
      cursor: pointer;
    }

    .collection-card .card-bg {
      width: 100%;
      height: 100%;
      transition: transform 0.5s ease;
    }

    .collection-card:hover .card-bg { transform: scale(1.04); }

    .collection-card .card-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(47,95,72,0.75) 0%, transparent 55%);
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      padding: 2rem;
    }

    .collection-card h3 {
      font-family: var(--ff-head);
      font-size: 1.8rem;
      font-weight: 300;
      color: var(--cream);
      line-height: 1.1;
    }
    .collection-card p {
      font-size: 0.75rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: rgba(255,253,245,0.65);
      margin-top: 0.3rem;
    }

    /* Card backgrounds with CSS gradients */
    .card-wedding .card-bg {
      background: linear-gradient(135deg, #d4b896 0%, #e8cfc0 35%, #c4a882 70%, #9c7b5a 100%);
    }
    .card-birthday .card-bg {
      background: linear-gradient(135deg, #f5c6d0 0%, #e8a0b0 35%, #d4748a 70%, #b85070 100%);
    }
    .card-corporate .card-bg {
      background: linear-gradient(135deg, #a8c5a0 0%, #7aaa80 35%, #4d8a5c 70%, #2f5f3f 100%);
    }

    /* ─── SECTION: Featured Bouquets ─── */
    .featured {
      padding: clamp(4rem, 10vh, 9rem) 0;
      background: var(--cream);
    }

    .bouquet-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2rem;
      margin-top: clamp(2rem, 4vw, 3.5rem);
    }

    .bouquet-card {
      display: flex;
      flex-direction: column;
    }

    .bouquet-img {
      aspect-ratio: 4/5;
      overflow: hidden;
      margin-bottom: 1.2rem;
      position: relative;
    }

    .bouquet-img-inner {
      width: 100%;
      height: 100%;
      transition: transform 0.45s ease;
    }

    .bouquet-card:hover .bouquet-img-inner { transform: scale(1.05); }

    .bouquet-img-1 .bouquet-img-inner {
      background: linear-gradient(155deg, #dde8c8 0%, #b8d4a0 40%, #8cb878 70%, #5a9045 100%);
    }
    .bouquet-img-2 .bouquet-img-inner {
      background: linear-gradient(155deg, #fce4d0 0%, #f4b898 40%, #e8906a 70%, #c05a35 100%);
    }
    .bouquet-img-3 .bouquet-img-inner {
      background: linear-gradient(155deg, #fdf0c8 0%, #f5d878 40%, #e8b830 70%, #c08810 100%);
    }

    .bouquet-badge {
      position: absolute;
      top: 1rem; right: 1rem;
      background: var(--cream);
      color: var(--sage);
      font-size: 0.65rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 0.3rem 0.7rem;
    }

    .bouquet-name {
      font-family: var(--ff-head);
      font-size: 1.35rem;
      font-weight: 400;
      letter-spacing: 0.01em;
      color: var(--bark);
      margin-bottom: 0.3rem;
    }

    .bouquet-price {
      font-size: 0.9rem;
      font-weight: 500;
      color: var(--sage);
      margin-bottom: 1rem;
    }

    /* ─── SECTION: Protea Spotlight ─── */
    .spotlight {
      position: relative;
      padding: clamp(5rem, 12vh, 11rem) 0;
      overflow: hidden;
      background: var(--sage);
    }

    .spotlight::before {
      content: '';
      position: absolute;
      top: -40%; right: -20%;
      width: 70vw; height: 140%;
      background: radial-gradient(ellipse, rgba(47,95,72,0.0) 0%, rgba(209,218,208,0.06) 50%, transparent 80%);
      pointer-events: none;
    }

    .spotlight-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: clamp(2rem, 5vw, 6rem);
      align-items: center;
    }

    .spotlight-label {
      display: inline-block;
      font-size: 0.65rem;
      font-weight: 500;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--blush);
      margin-bottom: 1rem;
    }

    .spotlight-heading {
      font-family: var(--ff-head);
      font-size: clamp(2.5rem, 5vw, 4.5rem);
      font-weight: 300;
      line-height: 0.95;
      color: var(--cream);
      margin-bottom: 1.5rem;
    }

    .spotlight-heading em {
      font-style: italic;
      color: var(--blush);
    }

    .spotlight-body {
      color: rgba(255,253,245,0.72);
      font-size: 0.95rem;
      max-width: 42ch;
      margin-bottom: 2.5rem;
      line-height: 1.75;
    }

    .spotlight-visual {
      aspect-ratio: 1;
      position: relative;
    }

    .spotlight-circle {
      width: 85%;
      aspect-ratio: 1;
      border-radius: 50%;
      margin: auto;
      background:
        radial-gradient(circle at 35% 35%, rgba(245,217,207,0.3) 0%, transparent 55%),
        linear-gradient(145deg, rgba(209,218,208,0.25) 0%, rgba(47,95,72,0.5) 100%);
      border: 1px solid rgba(255,253,245,0.15);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .spotlight-circle-inner {
      width: 65%;
      aspect-ratio: 1;
      border-radius: 50%;
      background:
        radial-gradient(circle at 40% 30%, rgba(245,217,207,0.45) 0%, transparent 60%),
        linear-gradient(145deg, rgba(255,253,245,0.12) 0%, rgba(47,95,72,0.3) 100%);
      border: 1px solid rgba(255,253,245,0.1);
    }

    /* ─── FOOTER ─── */
    footer {
      background: var(--bark);
      color: rgba(255,253,245,0.65);
      padding: clamp(3rem, 6vw, 5rem) 0 2rem;
    }

    .footer-inner {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr;
      gap: clamp(2rem, 5vw, 5rem);
      margin-bottom: 3rem;
    }

    .footer-brand-name {
      font-family: var(--ff-head);
      font-size: 1.5rem;
      font-weight: 600;
      color: var(--cream);
      margin-bottom: 0.75rem;
    }
    .footer-brand-name span { color: var(--blush); }

    .footer-tagline {
      font-size: 0.85rem;
      line-height: 1.7;
      max-width: 32ch;
      margin-bottom: 1.5rem;
    }

    .footer-contact p {
      font-size: 0.82rem;
      line-height: 2;
    }

    .footer-col h4 {
      font-family: var(--ff-body);
      font-size: 0.65rem;
      font-weight: 500;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--cream);
      margin-bottom: 1.2rem;
    }

    .footer-col ul li { margin-bottom: 0.6rem; }
    .footer-col ul a {
      font-size: 0.85rem;
      transition: color 0.2s;
    }
    .footer-col ul a:hover { color: var(--blush); }

    .footer-socials {
      display: flex;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .social-icon {
      width: 36px; height: 36px;
      border: 1px solid rgba(255,253,245,0.2);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.7rem;
      font-weight: 500;
      color: var(--cream);
      transition: background 0.2s, border-color 0.2s;
      text-transform: uppercase;
      letter-spacing: 0;
    }
    .social-icon:hover { background: rgba(255,253,245,0.12); border-color: rgba(255,253,245,0.4); }

    .footer-bottom {
      border-top: 1px solid rgba(255,253,245,0.1);
      padding-top: 1.5rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.75rem;
    }

    /* ─── Animations ─── */
    @keyframes fade-up {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .hero-content > * {
      animation: fade-up 0.8s ease both;
    }
    .hero-content .tag        { animation-delay: 0.1s; }
    .hero-content .hero-heading { animation-delay: 0.25s; }
    .hero-content .hero-body  { animation-delay: 0.4s; }
    .hero-content .btn        { animation-delay: 0.55s; }

    /* ─── Responsive ─── */
    @media (max-width: 900px) {
      .hero { grid-template-columns: 1fr; }
      .hero-image { display: none; }
      .hero-content {
        padding: clamp(6rem, 15vw, 9rem) clamp(1.25rem, 5vw, 3rem) 4rem;
        max-width: 600px;
      }
      .collection-grid { grid-template-columns: 1fr 1fr; }
      .bouquet-grid { grid-template-columns: 1fr 1fr; }
      .spotlight-inner { grid-template-columns: 1fr; }
      .spotlight-visual { display: none; }
      .footer-inner { grid-template-columns: 1fr 1fr; }
    }

    @media (max-width: 600px) {
      .nav-links { display: none; }
      .collection-grid { grid-template-columns: 1fr; }
      .bouquet-grid { grid-template-columns: 1fr; }
      .footer-inner { grid-template-columns: 1fr; }
      .footer-bottom { flex-direction: column; gap: 0.5rem; text-align: center; }
    }
  </style>
</head>
<body>

  <!-- ─── NAV ─── -->
  <nav>
    <div class="container nav-inner">
      <a href="#" class="nav-logo">Petal<span>Bloom</span></a>
      <ul class="nav-links">
        <li><a href="#collections">Shop</a></li>
        <li><a href="#featured">Bouquets</a></li>
        <li><a href="#spotlight">About</a></li>
        <li><a href="#footer">Contact</a></li>
        <li><a href="#featured" class="nav-cta">Order Now</a></li>
      </ul>
    </div>
  </nav>

  <!-- ─── HERO ─── -->
  <section class="hero">
    <div class="hero-content">
      <span class="tag">Cape Town Florist · Est. 2020</span>
      <h1 class="hero-heading">
        Welcome to<br><em>PetalBloom</em>
      </h1>
      <p class="hero-body">
        Your go-to florist in South Africa for stunning arrangements and bouquets. We bring artisanal floral design from Cape Town straight to your door.
      </p>
      <a href="#featured" class="btn btn-sage">Order Now</a>
    </div>

    <div class="hero-image" aria-hidden="true">
      <div class="hero-floral">
        <!-- Decorative botanical SVG -->
        <svg class="floral-svg" viewBox="0 0 300 400" fill="none" xmlns="http://www.w3.org/2000/svg">
          <!-- Stem -->
          <path d="M150 380 C150 380 148 300 155 250 C162 200 145 160 150 100" stroke="#2F5F48" stroke-width="3" stroke-linecap="round"/>
          <!-- Leaves -->
          <path d="M150 260 C130 240 105 245 95 230 C115 218 145 228 150 260Z" fill="#63866B" opacity="0.7"/>
          <path d="M152 200 C172 180 200 182 208 168 C190 155 160 168 152 200Z" fill="#2F5F48" opacity="0.6"/>
          <!-- Protea petals -->
          <ellipse cx="150" cy="95" rx="22" ry="40" fill="#F5D9CF" opacity="0.85"/>
          <ellipse cx="150" cy="95" rx="22" ry="40" fill="#F5D9CF" opacity="0.85" transform="rotate(45 150 95)"/>
          <ellipse cx="150" cy="95" rx="22" ry="40" fill="#D4917A" opacity="0.6" transform="rotate(90 150 95)"/>
          <ellipse cx="150" cy="95" rx="22" ry="40" fill="#F5D9CF" opacity="0.7" transform="rotate(135 150 95)"/>
          <!-- Center -->
          <circle cx="150" cy="95" r="20" fill="#2F5F48" opacity="0.9"/>
          <circle cx="150" cy="95" r="12" fill="#3A2C24" opacity="0.5"/>
          <!-- Small accent blooms -->
          <circle cx="115" cy="230" r="8" fill="#F5D9CF" opacity="0.6"/>
          <circle cx="110" cy="225" r="5" fill="#D4917A" opacity="0.5"/>
          <circle cx="195" cy="168" r="7" fill="#D4917A" opacity="0.5"/>
          <circle cx="200" cy="163" r="4" fill="#2F5F48" opacity="0.6"/>
        </svg>
      </div>
    </div>
  </section>

  <!-- ─── COLLECTIONS ─── -->
  <section class="collections" id="collections">
    <div class="container">
      <header class="section-header">
        <span class="tag">Collections</span>
        <h2 class="section-title">Crafted for <em>Every Highlight</em></h2>
        <p class="section-sub">Discover our curated collections of artisanal arrangements, designed to bring elegance and vibrant life to your Cape Town home or event.</p>
      </header>
    </div>

    <div class="collection-grid">
      <div class="collection-card card-wedding">
        <div class="card-bg"></div>
        <div class="card-overlay">
          <h3>Wedding</h3>
          <p>Arrangements</p>
        </div>
      </div>
      <div class="collection-card card-birthday">
        <div class="card-bg"></div>
        <div class="card-overlay">
          <h3>Birthday</h3>
          <p>Bouquets</p>
        </div>
      </div>
      <div class="collection-card card-corporate">
        <div class="card-bg"></div>
        <div class="card-overlay">
          <h3>Corporate</h3>
          <p>Décors</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ─── FEATURED BOUQUETS ─── -->
  <section class="featured" id="featured">
    <div class="container">
      <header class="section-header">
        <span class="tag">Shop</span>
        <h2 class="section-title"><em>Featured</em> Bouquets</h2>
      </header>

      <div class="bouquet-grid">
        <!-- Card 1 -->
        <div class="bouquet-card">
          <div class="bouquet-img bouquet-img-1">
            <div class="bouquet-img-inner"></div>
            <span class="bouquet-badge">Bestseller</span>
          </div>
          <h3 class="bouquet-name">Cape Town Classic</h3>
          <p class="bouquet-price">R 450.00</p>
          <a href="#" class="btn btn-dark">Order Now</a>
        </div>
        <!-- Card 2 -->
        <div class="bouquet-card">
          <div class="bouquet-img bouquet-img-2">
            <div class="bouquet-img-inner"></div>
            <span class="bouquet-badge">Popular</span>
          </div>
