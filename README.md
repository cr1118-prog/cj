<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Northstar Studio</title>
  <style>
    :root {
      --bg: #0b1020;
      --bg-2: #101a30;
      --panel: #131d35;
      --panel-soft: #f4f7ff;
      --text: #edf3ff;
      --muted: #a9b5d1;
      --primary: #7c9cff;
      --highlight: #8ef0d7;
      --accent: #ff7a90;
      --shadow: 0 20px 60px rgba(3, 8, 20, 0.4);
      --radius: 22px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
      background:
        radial-gradient(circle at top left, rgba(124, 156, 255, 0.18), transparent 28%),
        linear-gradient(180deg, var(--bg) 0%, #0d1427 100%);
      color: var(--text);
      line-height: 1.6;
    }

    a { color: inherit; text-decoration: none; }
    img { max-width: 100%; display: block; }

    .container {
      width: min(1120px, calc(100% - 2rem));
      margin: 0 auto;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 20;
      backdrop-filter: blur(16px);
      background: rgba(11, 16, 32, 0.7);
      border-bottom: 1px solid rgba(255,255,255,0.08);
    }

    .nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      min-height: 76px;
      gap: 1rem;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.02em;
    }

    .brand-mark {
      width: 2rem;
      height: 2rem;
      display: inline-grid;
      place-items: center;
      background: linear-gradient(135deg, var(--primary), var(--highlight));
      color: #051722;
      border-radius: 0.7rem;
      font-weight: 800;
    }

    nav {
      display: flex;
      gap: 1.5rem;
      color: var(--muted);
    }

    nav a:hover { color: var(--text); }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 0.9rem 1.35rem;
      border-radius: 999px;
      border: 1px solid rgba(255,255,255,0.1);
      background: linear-gradient(135deg, var(--primary), var(--highlight));
      color: #03131d;
      font-weight: 700;
      box-shadow: 0 16px 32px rgba(124, 156, 255, 0.32);
      transition: transform 0.2s ease;
    }

    .button:hover {
      transform: translateY(-1px);
    }

    .button.secondary {
      background: transparent;
      color: var(--text);
      box-shadow: none;
    }

    .hero {
      padding: 4.5rem 0 2.5rem;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.1fr 0.9fr;
      align-items: center;
      gap: 2.5rem;
    }

    .eyebrow {
      margin: 0 0 0.8rem;
      color: var(--highlight);
      font-size: 0.75rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.14em;
    }

    h1, h2, h3 {
      margin: 0;
      line-height: 1.08;
      letter-spacing: -0.04em;
    }

    .hero h1 {
      font-size: clamp(3rem, 5vw, 5.2rem);
      max-width: 620px;
    }

    .lead {
      margin-top: 1.1rem;
      color: var(--muted);
      font-size: 1.08rem;
      max-width: 620px;
    }

    .hero-actions {
      margin-top: 2rem;
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
    }

    .stats {
      list-style: none;
      margin: 2rem 0 0;
      padding: 0;
      display: flex;
      flex-wrap: wrap;
      gap: 1.5rem;
    }

    .stats li {
      display: flex;
      flex-direction: column;
      gap: 0.2rem;
    }

    .stats strong {
      font-size: 1.6rem;
    }

    .stats span { color: var(--muted); font-size: 0.85rem; }

    .dash {
      display: flex;
      justify-content: center;
    }

    .panel {
      width: min(520px, 100%);
      background: linear-gradient(180deg, rgba(17, 23, 39, 0.92), rgba(14, 19, 35, 0.8));
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 28px;
      padding: 1rem;
      box-shadow: var(--shadow);
    }

    .panel-top {
      display: flex;
      gap: 0.6rem;
      padding: 0.5rem 0.7rem 1rem;
    }

    .dot {
      width: 0.8rem;
      height: 0.8rem;
      border-radius: 50%;
    }

    .dot.red { background: #ff5a5f; }
    .dot.yellow { background: #ffbf47; }
    .dot.green { background: #43d17c; }

    .panel-body {
      background: rgba(255,255,255,0.02);
      border-radius: 18px;
      padding: 1rem;
      display: grid;
      gap: 1rem;
    }

    .chart {
      padding: 1rem 1rem 0.5rem;
      border-radius: 18px;
      background: linear-gradient(180deg, rgba(124,156,255,0.16), rgba(7,17,25,0.04));
      border: 1px solid rgba(124,156,255,0.18);
    }

    .chart span {
      display: block;
      color: var(--muted);
      font-size: 0.8rem;
      margin-bottom: 0.2rem;
    }

    .chart strong {
      font-size: clamp(1.8rem, 3vw, 2.8rem);
    }

    .bars {
      display: flex;
      align-items: flex-end;
      gap: 0.7rem;
      height: 120px;
      margin-top: 1rem;
    }

    .bars i {
      display: block;
      flex: 1;
      border-radius: 999px 999px 0 0;
      background: linear-gradient(180deg, var(--highlight), var(--primary));
    }

    .mini-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 1rem;
    }

    .mini {
      padding: 1rem;
      border-radius: 18px;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.08);
    }

    .mini span {
      color: var(--muted);
      display: block;
    }

    .mini strong {
      display: block;
      font-size: 1.5rem;
      margin-top: 0.35rem;
    }

    .mini.accent {
      background: linear-gradient(135deg, rgba(255,122,144,0.18), rgba(124,156,255,0.12));
    }

    .logo-bar {
      border-top: 1px solid rgba(255,255,255,0.08);
      border-bottom: 1px solid rgba(255,255,255,0.08);
      padding: 1rem 0;
    }

    .logo-row {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 1rem;
      color: rgba(233,238,255,0.7);
      text-transform: uppercase;
      letter-spacing: 0.16em;
      font-size: 0.72rem;
    }

    .section {
      padding: 5rem 0;
    }

    .muted {
      background: rgba(255,255,255,0.015);
    }

    .two-col {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
      align-items: end;
    }

    .two-col h2, .section-heading h2, .cta h2 {
      font-size: clamp(2.2rem, 4vw, 3.2rem);
    }

    .two-col p:last-child {
      margin: 0;
      color: var(--muted);
      font-size: 1.05rem;
    }

    .section-heading {
      max-width: 760px;
      margin-bottom: 2rem;
    }

    .cards, .pricing, .showcase {
      display: grid;
      gap: 1.5rem;
    }

    .cards { grid-template-columns: repeat(3, minmax(0, 1fr)); }
    .pricing { grid-template-columns: repeat(3, minmax(0, 1fr)); }
    .showcase { grid-template-columns: 1.2fr 1fr 1fr; }

    .card, .price, .showcase-card {
      border-radius: var(--radius);
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.08);
      box-shadow: var(--shadow);
    }

    .card {
      padding: 1.7rem;
    }

    .num {
      display: inline-grid;
      place-items: center;
      width: 3rem;
      height: 3rem;
      border-radius: 0.9rem;
      background: linear-gradient(135deg, rgba(124,156,255,0.3), rgba(142,240,215,0.2));
      color: var(--highlight);
      font-weight: 700;
    }

    .card h3 {
      margin: 1.2rem 0 0.6rem;
      font-size: 1.5rem;
    }

    .card p, .showcase-card p {
      margin: 0;
      color: var(--muted);
    }

    .showcase-card {
      position: relative;
      overflow: hidden;
      min-height: 260px;
      display: flex;
      flex-direction: column;
      justify-content: end;
      padding: 1.4rem;
    }

    .showcase-card::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(180deg, rgba(7,12,20,0.18), rgba(7,12,20,0.88));
    }

    .showcase-card > * {
      position: relative;
      z-index: 1;
    }

    .showcase-card.one { background: linear-gradient(135deg, rgba(124,156,255,0.72), rgba(11,16,32,0.5)); }
    .showcase-card.two { background: linear-gradient(135deg, rgba(255,122,144,0.72), rgba(11,16,32,0.5)); }
    .showcase-card.three { background: linear-gradient(135deg, rgba(142,240,215,0.72), rgba(11,16,32,0.5)); }

    .tag {
      display: inline-flex;
      width: fit-content;
      margin-bottom: 1rem;
      padding: 0.4rem 0.7rem;
      border-radius: 999px;
      background: rgba(8,12,20,0.38);
      border: 1px solid rgba(255,255,255,0.12);
      text-transform: uppercase;
      letter-spacing: 0.1em;
      font-size: 0.7rem;
    }

    .price {
      padding: 2rem 1.5rem;
    }

    .price.featured {
      border-color: rgba(124,156,255,0.4);
      background: linear-gradient(180deg, rgba(124,156,255,0.12), rgba(255,255,255,0.03));
    }

    .plan {
      margin: 0;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.12em;
      font-size: 0.72rem;
    }

    .price h3 {
      margin: 0.75rem 0;
      font-size: clamp(2rem, 4vw, 2.8rem);
    }

    .price ul {
      list-style: none;
      padding: 0;
      margin: 1.2rem 0 1.8rem;
      display: grid;
      gap: 0.7rem;
      color: var(--muted);
    }

    .price li::before {
      content: "•";
      color: var(--highlight);
      margin-right: 0.55rem;
    }

    .cta-box {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 2rem;
      padding: 2rem 2.2rem;
      border-radius: 28px;
      background: linear-gradient(135deg, rgba(124,156,255,0.14), rgba(142,240,215,0.08));
      border: 1px solid rgba(255,255,255,0.08);
      box-shadow: var(--shadow);
    }

    footer {
      padding: 1.4rem 0 2.5rem;
    }

    .footer-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 1rem;
      color: var(--muted);
      border-top: 1px solid rgba(255,255,255,0.08);
      padding-top: 1.2rem;
    }

    .socials {
      display: flex;
      gap: 1rem;
    }

    @media (max-width: 860px) {
      nav {
        display: none;
      }

      .hero-grid,
      .two-col,
      .cards,
      .pricing,
      .showcase,
      .cta-box {
        grid-template-columns: 1fr;
        display: grid;
      }

      .cta-box {
        align-items: flex-start;
      }

      .hero {
        padding-top: 3rem;
      }
    }

    @media (max-width: 480px) {
      .hero h1 {
        font-size: 2.7rem;
      }

      .section {
        padding: 4rem 0;
      }

      .cta-box {
        padding: 1.5rem 1.2rem;
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="container nav">
      <a href="#top" class="brand" aria-label="Northstar Studio">
        <span class="brand-mark">N</span>
        <span>Northstar</span>
      </a>

      <nav aria-label="Main menu">
        <a href="#about">About</a>
        <a href="#services">Services</a>
        <a href="#work">Work</a>
        <a href="#pricing">Pricing</a>
        <a href="#contact">Contact</a>
      </nav>

      <a href="#contact" class="button">Book a call</a>
    </div>
  </header>

  <main id="top">
    <section class="hero">
      <div class="container hero-grid">
        <div>
          <p class="eyebrow">Creative strategy • design • growth</p>
          <h1>Turn attention into action.</h1>
          <p class="lead">
            We build bold digital experiences that help brands stand out, convert more visitors,
            and grow with confidence.
          </p>

          <div class="hero-actions">
            <a href="#contact" class="button">Start a project</a>
            <a href="#work" class="button secondary">See our work</a>
          </div>

          <ul class="stats" aria-label="Company results">
            <li><strong>120+</strong><span>launches</span></li>
            <li><strong>4.9/5</strong><span>client rating</span></li>
            <li><strong>3x</strong><span>average ROI</span></li>
          </ul>
        </div>

        <div class="dash" aria-label="Summary panel">
          <div class="panel">
            <div class="panel-top">
              <span class="dot red"></span>
              <span class="dot yellow"></span>
              <span class="dot green"></span>
            </div>

            <div class="panel-body">
              <div class="chart">
                <span>Revenue</span>
                <strong>$84.2k</strong>
                <div class="bars" aria-hidden="true">
                  <i style="height: 30%;"></i>
                  <i style="height: 48%;"></i>
                  <i style="height: 56%;"></i>
                  <i style="height: 72%;"></i>
                  <i style="height: 90%;"></i>
                  <i style="height: 100%;"></i>
                </div>
              </div>

              <div class="mini-grid">
                <div class="mini">
                  <span>Leads</span>
                  <strong>+64%</strong>
                </div>
                <div class="mini accent">
                  <span>Conversion</span>
                  <strong>7.8%</strong>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="logo-bar">
      <div class="container logo-row" aria-label="Client list">
        <span>NovaPeak</span>
        <span>Summit</span>
        <span>Northwind</span>
        <span>Quanta</span>
        <span>Atelier</span>
      </div>
    </div>

    <section id="about" class="section">
      <div class="container two-col">
        <div>
          <p class="eyebrow">Why teams choose us</p>
          <h2>Strategy first. Design that feels premium.</h2>
        </div>
        <div>
          <p>
            We blend UX strategy, brand thinking, and performance marketing to create digital
            experiences that look exceptional and drive measurable growth.
          </p>
        </div>
      </div>
    </section>

    <section id="services" class="section muted">
      <div class="container">
        <div class="section-heading">
          <p class="eyebrow">What we do</p>
          <h2>Everything your brand needs to grow.</h2>
        </div>

        <div class="cards">
          <article class="card">
            <div class="num">01</div>
            <h3>Brand Systems</h3>
            <p>Positioning, messaging, identity, and strategic direction for standout brands.</p>
          </article>

          <article class="card">
            <div class="num">02</div>
            <h3>Web Design</h3>
            <p>Conversion-focused websites built for clarity, trust, and speed.</p>
          </article>

          <article class="card">
            <div class="num">03</div>
            <h3>Growth Marketing</h3>
            <p>Landing pages, launch support, and experiments that turn traffic into pipeline.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="work" class="section">
      <div class="container">
        <div class="section-heading">
          <p class="eyebrow">Selected work</p>
          <h2>Built to stand out and drive results.</h2>
        </div>

        <div class="showcase">
          <article class="showcase-card one">
            <div class="tag">B2B SaaS</div>
            <h3>NovaPeak</h3>
            <p>Reframed a complex product into a premium sales narrative.</p>
          </article>

          <article class="showcase-card two">
            <div class="tag">E-commerce</div>
            <h3>Atelier</h3>
            <p>Lifted conversion through a cleaner product journey.</p>
          </article>

          <article class="showcase-card three">
            <div class="tag">Advisory</div>
            <h3>Summit</h3>
            <p>Introduced a high-trust brand system for a growing team.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="pricing" class="section muted">
      <div class="container">
        <div class="section-heading">
          <p class="eyebrow">Simple pricing</p>
          <h2>Flexible packages for every stage.</h2>
        </div>

        <div class="pricing">
          <article class="price">
            <p class="plan">Starter</p>
            <h3>$1,500</h3>
            <ul>
              <li>Landing page design</li>
              <li>Brand direction</li>
              <li>Conversion notes</li>
            </ul>
            <a href="#contact" class="button secondary">Get started</a>
          </article>

          <article class="price featured">
            <p class="plan">Growth</p>
            <h3>$3,800</h3>
            <ul>
              <li>Full marketing website</li>
              <li>UX strategy</li>
              <li>Copywriting and launch support</li>
            </ul>
            <a href="#contact" class="button">Most popular</a>
          </article>

          <article class="price">
            <p class="plan">Scale</p>
            <h3>Custom</h3>
            <ul>
              <li>Multi-page web presence</li>
              <li>Ongoing optimization</li>
              <li>Monthly growth experiments</li>
            </ul>
            <a href="#contact" class="button secondary">Talk to us</a>
          </article>
        </div>
      </div>
    </section>

    <section id="contact" class="section">
      <div class="container cta-box">
        <div class="cta">
          <p class="eyebrow">Let’s build something bold</p>
          <h2>Ready for the next chapter of your brand?</h2>
        </div>
        <a href="mailto:hello@northstarstudio.com" class="button">hello@northstarstudio.com</a>
      </div>
    </section>
  </main>

  <footer>
    <div class="container footer-row">
      <p>© <span id="year"></span> Northstar Studio</p>
      <div class="socials" aria-label="Social links">
        <a href="#">Instagram</a>
        <a href="#">LinkedIn</a>
        <a href="#">Dribbble</a>
      </div>
    </div>
  </footer>

  <script>
    document.getElementById("year").textContent = new Date().getFullYear();
  </script>
</body>
</html>