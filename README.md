<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vikasam — Technology & Strategy Consulting</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --ink: #0d0d0d; --mist: #f4f2ee; --bone: #ece9e3;
    --navy: #1a2535; --navy-mid: #253449; --navy-accent: #8eb8d8;
    --rust: #c05a2e; --rust-light: #f5e5de;
    --white: #fefefe; --text-muted: #7a7570;
  }
  html { scroll-behavior: smooth; }
  body { font-family: 'DM Sans', sans-serif; background: var(--white); color: var(--ink); font-size: 15px; line-height: 1.6; overflow-x: hidden; }

  nav { position: fixed; top: 0; left: 0; right: 0; z-index: 100; display: flex; align-items: center; justify-content: space-between; padding: 0.85rem 3rem; background: rgba(26,37,53,0.94); backdrop-filter: blur(12px); }
  .logo { font-family: 'DM Serif Display', serif; font-size: 1.3rem; letter-spacing: -0.02em; color: var(--white); text-decoration: none; }
  .logo span { color: var(--navy-accent); }
  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a { font-size: 0.82rem; color: rgba(255,255,255,0.55); text-decoration: none; transition: color 0.2s; }
  .nav-links a:hover { color: var(--white); }
  .nav-cta { background: var(--white) !important; color: var(--navy) !important; padding: 0.42rem 1.1rem; border-radius: 100px; font-weight: 500; transition: background 0.2s !important; }
  .nav-cta:hover { background: var(--navy-accent) !important; color: var(--navy) !important; }

  .hero { width: 100%; min-height: 100vh; max-height: 760px; background: var(--navy); display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 6rem 4rem 3rem; overflow: hidden; }
  .hero-inner { width: 100%; max-width: 960px; display: flex; flex-direction: column; align-items: flex-start; }
  .eyebrow { display: inline-flex; align-items: center; gap: 7px; font-size: 0.68rem; font-weight: 500; letter-spacing: 0.14em; text-transform: uppercase; color: var(--navy-accent); margin-bottom: 1.1rem; opacity: 0.85; }
  .eyebrow::before { content: ''; display: block; width: 18px; height: 1px; background: var(--navy-accent); }
  h1 { font-family: 'DM Serif Display', serif; font-size: clamp(2.8rem, 5vw, 4.2rem); line-height: 1.06; letter-spacing: -0.03em; color: var(--white); margin-bottom: 1.25rem; max-width: 700px; }
  h1 em { font-style: italic; color: var(--navy-accent); }
  .hero-sub { font-size: 1rem; color: rgba(255,255,255,0.55); font-weight: 300; max-width: 520px; margin-bottom: 2rem; line-height: 1.75; }
  .btn-group { display: flex; gap: 0.9rem; align-items: center; margin-bottom: 3rem; }
  .btn-white { background: var(--white); color: var(--navy); padding: 0.72rem 1.75rem; border-radius: 100px; font-size: 0.82rem; font-weight: 500; cursor: pointer; border: none; text-decoration: none; display: inline-block; transition: background 0.2s, transform 0.15s; }
  .btn-white:hover { background: var(--navy-accent); transform: translateY(-1px); }
  .btn-ghost { font-size: 0.82rem; color: rgba(255,255,255,0.45); text-decoration: none; display: inline-flex; align-items: center; gap: 5px; transition: color 0.2s; }
  .btn-ghost:hover { color: var(--white); }

  .pillars-row { width: 100%; display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px; border-top: 0.5px solid rgba(255,255,255,0.1); padding-top: 1.75rem; }
  .pillar { display: flex; align-items: flex-start; gap: 0.9rem; padding: 1.25rem 1.25rem 1.25rem 0; opacity: 0; transform: translateY(10px); transition: opacity 0.5s ease, transform 0.5s ease; }
  .pillar.visible { opacity: 1; transform: translateY(0); }
  .pillar-icon { width: 34px; height: 34px; border-radius: 8px; background: rgba(142,184,216,0.15); display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
  .pillar-icon svg { width: 14px; height: 14px; stroke: var(--navy-accent); fill: none; stroke-width: 1.5; stroke-linecap: round; stroke-linejoin: round; }
  .pillar-title { font-family: 'DM Serif Display', serif; font-size: 0.95rem; color: var(--white); margin-bottom: 3px; line-height: 1.2; }
  .pillar-desc { font-size: 0.72rem; color: rgba(255,255,255,0.45); line-height: 1.5; }

  .services { padding: 5rem 3rem; background: var(--white); }
  .section-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 2.5rem; }
  .section-label { font-size: 0.68rem; letter-spacing: 0.14em; text-transform: uppercase; color: var(--text-muted); margin-bottom: 0.6rem; }
  h2 { font-family: 'DM Serif Display', serif; font-size: clamp(1.8rem, 3vw, 2.5rem); line-height: 1.1; letter-spacing: -0.02em; color: var(--ink); }
  h2 em { font-style: italic; color: var(--navy); }
  .section-note { font-size: 0.82rem; color: var(--text-muted); max-width: 240px; text-align: right; line-height: 1.6; }
  .services-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5px; background: var(--bone); border: 1.5px solid var(--bone); border-radius: 18px; overflow: hidden; }
  .service-card { background: var(--white); padding: 2rem; transition: background 0.2s; }
  .service-card:hover { background: var(--mist); }
  .service-icon { width: 40px; height: 40px; border-radius: 10px; margin-bottom: 1.2rem; display: flex; align-items: center; justify-content: center; font-size: 18px; }
  .icon-navy { background: #e6eef5; }
  .icon-rust { background: var(--rust-light); }
  .service-title { font-family: 'DM Serif Display', serif; font-size: 1.2rem; color: var(--ink); margin-bottom: 0.6rem; line-height: 1.2; }
  .service-desc { font-size: 0.82rem; color: var(--text-muted); line-height: 1.7; }
  .service-link { display: inline-flex; align-items: center; gap: 4px; font-size: 0.76rem; color: var(--navy); font-weight: 500; margin-top: 1rem; cursor: pointer; transition: gap 0.2s; }
  .service-link:hover { gap: 9px; }

  .about { padding: 5rem 3rem; background: var(--mist); display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center; }
  .about-visual { position: relative; height: 380px; }
  .about-block { position: absolute; border-radius: 14px; }
  .ab1 { top: 0; left: 0; width: 70%; height: 72%; background: var(--navy); display: flex; align-items: flex-end; padding: 1.75rem; }
  .ab1-text { font-family: 'DM Serif Display', serif; font-size: 1.3rem; color: var(--white); line-height: 1.2; }
  .ab2 { bottom: 0; right: 0; width: 58%; height: 46%; background: var(--bone); padding: 1.5rem; display: flex; align-items: center; }
  .ab2-label { font-size: 0.66rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--text-muted); margin-bottom: 0.4rem; }
  .ab2-text { font-family: 'DM Serif Display', serif; font-size: 1.1rem; color: var(--ink); line-height: 1.3; }
  .ab3 { bottom: 36%; left: 58%; width: 40%; height: 30%; background: var(--rust-light); padding: 1rem; display: flex; align-items: center; justify-content: center; text-align: center; }
  .ab3-text { font-family: 'DM Serif Display', serif; font-size: 0.95rem; color: var(--rust); line-height: 1.3; }
  .about-text p { font-size: 0.88rem; color: var(--text-muted); line-height: 1.8; margin-bottom: 1rem; font-weight: 300; }
  .about-list { list-style: none; margin: 1.5rem 0; }
  .about-list li { display: flex; align-items: center; gap: 9px; font-size: 0.82rem; color: var(--ink); padding: 0.5rem 0; border-bottom: 0.5px solid rgba(0,0,0,0.07); }
  .about-list li::before { content: ''; width: 5px; height: 5px; border-radius: 50%; background: var(--navy); flex-shrink: 0; }
  .btn-primary { background: var(--navy); color: var(--white); padding: 0.72rem 1.75rem; border-radius: 100px; font-size: 0.82rem; font-weight: 500; cursor: pointer; border: none; text-decoration: none; display: inline-block; transition: background 0.2s, transform 0.15s; }
  .btn-primary:hover { background: var(--navy-mid); transform: translateY(-1px); }

  .process { padding: 5rem 3rem; background: var(--ink); }
  .process .section-label { color: rgba(255,255,255,0.4); }
  .process h2 { color: var(--white); }
  .process h2 em { color: var(--navy-accent); }
  .process-steps { display: grid; grid-template-columns: repeat(4, 1fr); gap: 2px; margin-top: 2.5rem; background: rgba(255,255,255,0.06); border-radius: 14px; overflow: hidden; }
  .process-step { padding: 2rem; transition: background 0.2s; }
  .process-step:hover { background: rgba(255,255,255,0.04); }
  .step-num { font-family: 'DM Serif Display', serif; font-size: 3rem; color: rgba(255,255,255,0.07); line-height: 1; margin-bottom: 1.2rem; }
  .step-title { font-family: 'DM Serif Display', serif; font-size: 1.05rem; color: var(--white); margin-bottom: 0.6rem; }
  .step-desc { font-size: 0.76rem; color: rgba(255,255,255,0.42); line-height: 1.7; }

  .contact { padding: 5rem 3rem; background: var(--mist); display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: start; }
  .contact-intro p { font-size: 0.88rem; color: var(--text-muted); line-height: 1.8; font-weight: 300; margin-top: 1rem; }
  .contact-form { background: var(--white); border: 0.5px solid rgba(0,0,0,0.09); border-radius: 18px; padding: 2rem; }
  .form-group { margin-bottom: 1rem; }
  label { display: block; font-size: 0.7rem; font-weight: 500; letter-spacing: 0.05em; text-transform: uppercase; color: var(--text-muted); margin-bottom: 5px; }
  input, textarea, select { width: 100%; padding: 0.65rem 0.9rem; border: 0.5px solid rgba(0,0,0,0.12); border-radius: 9px; font-family: 'DM Sans', sans-serif; font-size: 0.85rem; color: var(--ink); background: var(--white); outline: none; transition: border-color 0.2s; }
  input:focus, textarea:focus, select:focus { border-color: var(--navy); }
  textarea { resize: vertical; min-height: 90px; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 0.9rem; }
  .submit-btn { width: 100%; background: var(--navy); color: var(--white); border: none; border-radius: 100px; padding: 0.8rem; font-family: 'DM Sans', sans-serif; font-size: 0.85rem; font-weight: 500; cursor: pointer; margin-top: 0.4rem; transition: background 0.2s, transform 0.15s; }
  .submit-btn:hover { background: var(--navy-mid); transform: translateY(-1px); }

  footer { background: var(--ink); padding: 2.5rem 3rem; display: flex; justify-content: space-between; align-items: center; }
  .footer-logo { font-family: 'DM Serif Display', serif; font-size: 1.1rem; color: var(--white); }
  .footer-logo span { color: var(--navy-accent); }
  .footer-copy { font-size: 0.72rem; color: rgba(255,255,255,0.3); }
  .footer-links { display: flex; gap: 2rem; list-style: none; }
  .footer-links a { font-size: 0.72rem; color: rgba(255,255,255,0.35); text-decoration: none; transition: color 0.2s; }
  .footer-links a:hover { color: rgba(255,255,255,0.7); }

  .fade-up { opacity: 0; transform: translateY(20px); transition: opacity 0.6s ease, transform 0.6s ease; }
  .fade-up.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 768px) {
    nav { padding: 0.85rem 1.5rem; }
    .nav-links { display: none; }
    .hero { padding: 5rem 1.5rem 2.5rem; min-height: auto; }
    .pillars-row { grid-template-columns: 1fr; gap: 0; }
    .pillar { padding: 1rem 0; border-bottom: 0.5px solid rgba(255,255,255,0.08); }
    .services, .about, .process, .contact { padding: 3.5rem 1.5rem; }
    .services-grid { grid-template-columns: 1fr; }
    .section-header { flex-direction: column; align-items: flex-start; gap: 0.75rem; }
    .section-note { text-align: left; max-width: 100%; }
    .about { grid-template-columns: 1fr; gap: 2.5rem; }
    .about-visual { height: 260px; }
    .process-steps { grid-template-columns: 1fr 1fr; }
    .contact { grid-template-columns: 1fr; gap: 2.5rem; }
    footer { flex-direction: column; gap: 1rem; text-align: center; padding: 2rem 1.5rem; }
  }
</style>
</head>
<body>

<nav>
  <a class="logo" href="#">Vikasam<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#services">Services</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#process">Process</a></li>
    <li><a class="nav-cta" href="#contact">Get in touch</a></li>
  </ul>
</nav>

<section class="hero" id="hero">
  <div class="hero-inner">
    <div class="eyebrow">Technology &amp; Strategy</div>
    <h1>We make <em>complex</em> tech<br>work for your business</h1>
    <p class="hero-sub">From digital transformation to strategic technology consulting, Vikasam guides organisations through the decisions that matter most.</p>
    <div class="btn-group">
      <a class="btn-white" href="#contact">Start a conversation</a>
      <a class="btn-ghost" href="#services">Explore services &rarr;</a>
    </div>
    <div class="pillars-row">
      <div class="pillar" id="p1">
        <div class="pillar-icon"><svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg></div>
        <div class="pillar-body">
          <div class="pillar-title">Strategy before technology</div>
          <div class="pillar-desc">We align on business goals first. Technology is the vehicle, never the destination.</div>
        </div>
      </div>
      <div class="pillar" id="p2">
        <div class="pillar-icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg></div>
        <div class="pillar-body">
          <div class="pillar-title">Embedded alongside your team</div>
          <div class="pillar-desc">We work inside your organisation, not at arm's length from it.</div>
        </div>
      </div>
      <div class="pillar" id="p3">
        <div class="pillar-icon"><svg viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg></div>
        <div class="pillar-body">
          <div class="pillar-title">Clarity, roadmaps, results</div>
          <div class="pillar-desc">Every engagement ends with something tangible &mdash; a path cleared, a system improved.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<section class="services" id="services">
  <div class="section-header fade-up">
    <div>
      <div class="section-label">What we do</div>
      <h2>Capabilities built for <em>real</em> outcomes</h2>
    </div>
    <p class="section-note">We work across sectors &mdash; from scale-ups to enterprises &mdash; wherever technology creates leverage.</p>
  </div>
  <div class="services-grid fade-up">
    <div class="service-card">
      <div class="service-icon icon-navy">&#x1F501;</div>
      <div class="service-title">Digital Transformation</div>
      <p class="service-desc">Modernise legacy systems and processes without disrupting operations. We map the journey, manage the risk, and deliver the change.</p>
      <a class="service-link">Learn more &rarr;</a>
    </div>
    <div class="service-card">
      <div class="service-icon icon-rust">&#x2601;&#xFE0F;</div>
      <div class="service-title">Cloud Architecture</div>
      <p class="service-desc">Design and migrate to cloud infrastructure that's scalable, secure, and cost-optimised for your specific workloads.</p>
      <a class="service-link">Learn more &rarr;</a>
    </div>
    <div class="service-card">
      <div class="service-icon icon-navy">&#x1F4CA;</div>
      <div class="service-title">Data &amp; Analytics</div>
      <p class="service-desc">Turn raw data into strategic intelligence. We build data pipelines, dashboards, and decision frameworks that drive action.</p>
      <a class="service-link">Learn more &rarr;</a>
    </div>
    <div class="service-card">
      <div class="service-icon icon-rust">&#x1F9ED;</div>
      <div class="service-title">Technology Strategy</div>
      <p class="service-desc">Align your technology investments with business goals. We provide the clarity and roadmap your leadership team needs.</p>
      <a class="service-link">Learn more &rarr;</a>
    </div>
  </div>
</section>

<section class="about" id="about">
  <div class="about-visual fade-up">
    <div class="about-block ab1">
      <div class="ab1-text">Technology that serves <em>people</em>, not the other way around.</div>
    </div>
    <div class="about-block ab2">
      <div>
        <div class="ab2-label">Our promise</div>
        <div class="ab2-text">No billable-hour padding. Ever.</div>
      </div>
    </div>
    <div class="about-block ab3">
      <div class="ab3-text">Embedded. Honest. Effective.</div>
    </div>
  </div>
  <div class="about-text fade-up">
    <div class="section-label">About Vikasam</div>
    <h2 style="margin-bottom: 1rem;">Strategy first. <em>Technology</em> second.</h2>
    <p>We believe most tech projects fail not because of bad technology, but because of unclear strategy. Vikasam was founded to close that gap &mdash; bridging executive vision with pragmatic technical execution.</p>
    <p>Our consultants bring deep expertise from both enterprise and startup environments, which means we understand the constraints your team is actually working within.</p>
    <ul class="about-list">
      <li>Sector expertise in finance, healthcare, logistics &amp; retail</li>
      <li>Embedded delivery model &mdash; we work alongside your team</li>
      <li>Outcome-based engagements, not billable-hour padding</li>
      <li>Transparent progress reporting throughout every engagement</li>
    </ul>
    <a class="btn-primary" href="#contact" style="margin-top: 1rem; display: inline-block;">Work with us</a>
  </div>
</section>

<section class="process" id="process">
  <div class="fade-up">
    <div class="section-label">How we work</div>
    <h2>A clear path from <em>problem</em> to solution</h2>
  </div>
  <div class="process-steps fade-up">
    <div class="process-step">
      <div class="step-num">01</div>
      <div class="step-title">Discovery</div>
      <p class="step-desc">We invest time understanding your business context, constraints, and what success genuinely looks like for your team.</p>
    </div>
    <div class="process-step">
      <div class="step-num">02</div>
      <div class="step-title">Diagnosis</div>
      <p class="step-desc">Technical and operational audit to surface the real blockers &mdash; not just the symptoms your team has reported.</p>
    </div>
    <div class="process-step">
      <div class="step-num">03</div>
      <div class="step-title">Roadmap</div>
      <p class="step-desc">A prioritised, costed plan with clear milestones. Realistic timelines, not aspirational ones designed to win the pitch.</p>
    </div>
    <div class="process-step">
      <div class="step-num">04</div>
      <div class="step-title">Delivery</div>
      <p class="step-desc">Embedded execution alongside your team, with regular checkpoints and transparent progress reporting throughout.</p>
    </div>
  </div>
</section>

<section class="contact" id="contact">
  <div class="contact-intro fade-up">
    <div class="section-label">Get in touch</div>
    <h2>Let's talk about what's <em>possible</em></h2>
    <p>Whether you have a specific challenge in mind or just want to explore where technology could create more leverage in your business, we'd love to hear from you. Fill in the form and we'll be in touch shortly.</p>
  </div>
  <div class="contact-form fade-up">
    <div class="form-row">
      <div class="form-group"><label>First name</label><input type="text" placeholder="Alex"></div>
      <div class="form-group"><label>Last name</label><input type="text" placeholder="Morgan"></div>
    </div>
    <div class="form-group"><label>Work email</label><input type="email" placeholder="alex@company.com"></div>
    <div class="form-group"><label>Company</label><input type="text" placeholder="Your organisation"></div>
    <div class="form-group">
      <label>How can we help?</label>
      <select>
        <option value="">Select a service...</option>
        <option>Digital Transformation</option>
        <option>Cloud Architecture</option>
        <option>Data &amp; Analytics</option>
        <option>Technology Strategy</option>
      </select>
    </div>
    <div class="form-group"><label>Tell us more</label><textarea placeholder="Brief description of your challenge or project..."></textarea></div>
    <button class="submit-btn">Send message</button>
  </div>
</section>

<footer>
  <div class="footer-logo">Vikasam<span>.</span></div>
  <span class="footer-copy">&copy; 2026 Vikasam Technology Consulting Ltd.</span>
  <ul class="footer-links">
    <li><a href="#">Privacy</a></li>
    <li><a href="#">Terms</a></li>
    <li><a href="#">LinkedIn</a></li>
  </ul>
</footer>

<script>
  const pillars = [document.getElementById('p1'), document.getElementById('p2'), document.getElementById('p3')];
  setTimeout(() => {
    pillars.forEach((p, i) => { setTimeout(() => { p.classList.add('visible'); }, i * 200); });
  }, 400);
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); } });
  }, { threshold: 0.12 });
  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));
  document.querySelector('.submit-btn').addEventListener('click', function(e) {
    e.preventDefault();
    this.textContent = 'Message sent \u2713';
    this.style.background = '#1a2535';
    setTimeout(() => { this.textContent = 'Send message'; this.style.background = ''; }, 3000);
  });
</script>
</body>
</html>
