<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
  <title>Julie Pédeville - Account Manager</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Playfair+Display:ital,wght@0,600;1,600&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --navy: #0e0a0a;
      --navy-light: #1a1010;
      --maroon: #7d2d2d;
      --maroon-light: #9e3a3a;
      --beige: #f3ece8;
      --white: #ffffff;
      --gray-50: #f8f4f2;
      --gray-100: #ede6e2;
      --gray-200: #d6ccc8;
      --gray-400: #8a7c78;
      --gray-600: #4a3c3a;
      --gray-800: #1a0e0e;
      --safe-top: env(safe-area-inset-top, 0px);
      --safe-bottom: env(safe-area-inset-bottom, 0px);
      --safe-left: env(safe-area-inset-left, 0px);
      --safe-right: env(safe-area-inset-right, 0px);
    }

    html { scroll-behavior: smooth; -webkit-text-size-adjust: 100%; }

    body {
      font-family: 'Inter', -apple-system, sans-serif;
      color: var(--gray-800);
      background: var(--gray-50);
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* ===== NAVIGATION ===== */
    nav {
      position: fixed; top: 0; width: 100%; z-index: 100;
      background: rgba(14,10,10,0.96);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(255,255,255,0.06);
      transition: transform 0.3s;
      padding-top: var(--safe-top);
    }
    nav.hidden { transform: translateY(-100%); }
    .nav-inner {
      max-width: 1100px; margin: 0 auto; padding: 0 2rem;
      display: flex; align-items: center; justify-content: space-between; height: 60px;
    }
    .nav-logo { font-weight: 700; font-size: 1.05rem; color: var(--white); letter-spacing: -0.02em; }
    .nav-logo span { color: var(--maroon-light); }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a {
      color: var(--gray-400); text-decoration: none; font-size: 0.85rem;
      font-weight: 500; letter-spacing: 0.03em; text-transform: uppercase; transition: color 0.2s;
    }
    .nav-links a:hover, .nav-links a.active { color: var(--white); }

    .nav-toggle { display: none; background: none; border: none; cursor: pointer; padding: 0.5rem; min-width: 44px; min-height: 44px; }
    .nav-toggle span {
      display: block; width: 22px; height: 2px; background: var(--white);
      margin: 5px auto; border-radius: 2px; transition: all 0.3s;
    }
    .nav-toggle.active span:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
    .nav-toggle.active span:nth-child(2) { opacity: 0; }
    .nav-toggle.active span:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }

    /* ===== HERO ===== */
    .hero {
      min-height: 100vh; min-height: 100dvh;
      background: linear-gradient(160deg, #0a0606 0%, #130a0a 50%, #1e1010 100%);
      display: flex; align-items: center; justify-content: center;
      position: relative; overflow: hidden;
      padding-top: calc(60px + var(--safe-top));
    }
    .hero::before {
      content: ''; position: absolute; width: 600px; height: 600px;
      background: radial-gradient(circle, rgba(125,45,45,0.15) 0%, transparent 70%);
      top: -100px; right: -100px; border-radius: 50%;
    }
    .hero::after {
      content: ''; position: absolute; width: 400px; height: 400px;
      background: radial-gradient(circle, rgba(125,45,45,0.08) 0%, transparent 70%);
      bottom: -50px; left: -50px; border-radius: 50%;
    }
    .hero-content { text-align: center; position: relative; z-index: 2; padding: 2rem; max-width: 800px; }
    .hero-photo {
      width: 140px; height: 140px; border-radius: 50%;
      background: linear-gradient(135deg, #7d2d2d, #5a1a1a);
      padding: 3px; margin: 0 auto 2rem;
      opacity: 0; transform: scale(0.8); animation: fadeScale 0.8s 0.2s forwards;
    }
    .hero-photo-placeholder {
      width: 100%; height: 100%; border-radius: 50%; background: var(--navy-light);
      display: flex; align-items: center; justify-content: center;
      font-size: 3rem; font-weight: 700; color: var(--white); font-family: 'Playfair Display', serif;
    }
    .hero h1 {
      font-family: 'Playfair Display', serif; font-size: clamp(2.5rem, 6vw, 4rem);
      font-weight: 600; color: var(--white); letter-spacing: -0.02em; margin-bottom: 0.5rem;
      opacity: 0; transform: translateY(20px); animation: fadeUp 0.8s 0.4s forwards;
    }
    .hero-tagline {
      font-size: 1.15rem; color: #c08080; margin-bottom: 1.5rem;
      opacity: 0; transform: translateY(20px); animation: fadeUp 0.8s 0.6s forwards;
    }
    .hero-summary {
      font-size: 1.05rem; color: rgba(255,255,255,0.7); max-width: 620px;
      margin: 0 auto 2.5rem; line-height: 1.7;
      opacity: 0; transform: translateY(20px); animation: fadeUp 0.8s 0.8s forwards;
    }
    .hero-stats {
      display: flex; justify-content: center; gap: 3rem; flex-wrap: wrap;
      opacity: 0; transform: translateY(20px); animation: fadeUp 0.8s 1s forwards;
    }
    .stat { text-align: center; }
    .stat-number { font-size: 2rem; font-weight: 800; color: var(--white); line-height: 1; }
    .stat-number span { color: var(--maroon-light); }
    .stat-label { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--gray-400); margin-top: 0.3rem; }
    .hero-contact {
      margin-top: 2.5rem; display: flex; justify-content: center; gap: 1rem; flex-wrap: wrap;
      opacity: 0; transform: translateY(20px); animation: fadeUp 0.8s 1.2s forwards;
    }
    .hero-contact a {
      display: inline-flex; align-items: center; gap: 0.5rem;
      padding: 0.65rem 1.4rem; border-radius: 999px;
      font-size: 0.85rem; font-weight: 500; text-decoration: none; transition: all 0.25s;
      min-height: 44px;
    }
    .btn-primary { background: var(--maroon); color: var(--white); }
    .btn-primary:hover { background: var(--maroon-light); transform: translateY(-2px); }
    .btn-outline { border: 1px solid rgba(255,255,255,0.25); color: var(--white); }
    .btn-outline:hover { border-color: var(--white); background: rgba(255,255,255,0.05); }
    .scroll-indicator {
      position: absolute; bottom: 2rem; left: 50%; transform: translateX(-50%);
      opacity: 0; animation: fadeUp 0.8s 1.5s forwards;
    }
    .scroll-indicator span {
      display: block; width: 2px; height: 30px; background: rgba(255,255,255,0.3);
      margin: 0 auto; border-radius: 2px; animation: scrollPulse 2s infinite;
    }

    /* ===== SECTIONS ===== */
    section { padding: 5rem 2rem; }
    .section-inner { max-width: 900px; margin: 0 auto; }
    .section-label {
      font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.15em;
      color: var(--maroon); font-weight: 600; margin-bottom: 0.5rem;
    }
    .section-title {
      font-family: 'Playfair Display', serif; font-size: clamp(1.8rem, 4vw, 2.5rem);
      font-weight: 600; color: var(--gray-800); margin-bottom: 3rem; letter-spacing: -0.02em;
    }

    /* ===== EXPERIENCE ===== */
    #experience { background: var(--white); }
    .timeline { position: relative; }
    .timeline::before {
      content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 2px; background: var(--gray-200);
    }
    .timeline-item {
      position: relative; padding-left: 2.5rem; margin-bottom: 3rem;
      opacity: 0; transform: translateX(-20px);
    }
    .timeline-item.visible { animation: slideRight 0.6s forwards; }
    .timeline-dot {
      position: absolute; left: -6px; top: 6px; width: 14px; height: 14px;
      border-radius: 50%; background: var(--maroon); border: 3px solid var(--white);
      box-shadow: 0 0 0 2px var(--maroon);
    }
    .timeline-item:first-child .timeline-dot {
      background: var(--maroon-light); box-shadow: 0 0 0 2px var(--maroon-light);
    }
    .job-header {
      display: flex; justify-content: space-between; align-items: flex-start;
      flex-wrap: wrap; gap: 0.5rem; margin-bottom: 0.5rem;
    }
    .job-title { font-size: 1.15rem; font-weight: 700; color: var(--gray-800); }
    .job-date {
      font-size: 0.8rem; font-weight: 600; color: var(--maroon);
      background: var(--beige); padding: 0.2rem 0.7rem; border-radius: 999px; white-space: nowrap;
    }
    .job-company { font-size: 0.95rem; color: var(--gray-600); margin-bottom: 0.75rem; }
    .job-company strong { color: var(--gray-800); font-weight: 600; }
    .job-bullets { list-style: none; display: flex; flex-direction: column; gap: 0.5rem; }
    .job-bullets li {
      position: relative; padding-left: 1.25rem;
      font-size: 0.92rem; color: var(--gray-600); line-height: 1.6;
    }
    .job-bullets li::before {
      content: ''; position: absolute; left: 0; top: 0.6em;
      width: 6px; height: 6px; border-radius: 50%; background: var(--maroon);
    }
    .job-tag {
      display: inline-block; font-size: 0.7rem; font-weight: 600;
      text-transform: uppercase; letter-spacing: 0.05em;
      padding: 0.15rem 0.5rem; border-radius: 4px; margin-right: 0.3rem; margin-top: 0.5rem;
    }
    .tag-a { background: #1a0808; color: #c07070; }
    .tag-b { background: #1a0808; color: #e0cdc8; }
    .tag-c { background: #1a0808; color: #9e4040; }
    .tag-d { background: #1a0808; color: #a08888; }

    /* ===== SKILLS ===== */
    #skills { background: var(--gray-50); }
    .skills-intro {
      max-width: 700px; margin: 0 auto 3rem; text-align: center;
      font-size: 1rem; color: var(--gray-600); line-height: 1.7;
    }
    .skills-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem; }
    .skill-card {
      background: var(--white); border-radius: 12px; padding: 1.75rem;
      border: 1px solid var(--gray-200); transition: all 0.3s;
      opacity: 0; transform: translateY(20px);
    }
    .skill-card.visible { animation: fadeUp 0.5s forwards; }
    .skill-card:hover { transform: translateY(-4px); box-shadow: 0 12px 40px rgba(125,45,45,0.12); border-color: var(--maroon); }
    .skill-icon {
      width: 48px; height: 48px; border-radius: 10px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.4rem; margin-bottom: 1rem;
    }
    .skill-card h3 { font-size: 1.05rem; font-weight: 700; color: var(--gray-800); margin-bottom: 0.65rem; line-height: 1.3; }
    .skill-desc { font-size: 0.88rem; color: var(--gray-600); line-height: 1.6; margin-bottom: 1rem; }
    .skill-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
    .skill-tags span {
      font-size: 0.75rem; color: var(--gray-600); background: var(--gray-100);
      padding: 0.25rem 0.65rem; border-radius: 6px; font-weight: 500;
    }

    /* ===== INTERNSHIPS ===== */
    #internships { background: var(--white); }
    .internship-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 1.5rem; }
    .internship-card {
      background: var(--gray-50); border-radius: 12px; padding: 1.75rem;
      border: 1px solid var(--gray-200); transition: all 0.3s;
      opacity: 0; transform: translateY(20px);
    }
    .internship-card.visible { animation: fadeUp 0.5s forwards; }
    .internship-card:hover { transform: translateY(-4px); box-shadow: 0 12px 40px rgba(125,45,45,0.1); border-color: var(--maroon); }
    .internship-header { display: flex; align-items: flex-start; gap: 1rem; margin-bottom: 1rem; }
    .internship-icon {
      width: 42px; height: 42px; border-radius: 10px; flex-shrink: 0;
      background: #1a0808; display: flex; align-items: center; justify-content: center;
      color: var(--maroon-light);
    }
    .internship-company { font-size: 1rem; font-weight: 700; color: var(--gray-800); line-height: 1.2; }
    .internship-role { font-size: 0.8rem; color: var(--maroon); font-weight: 600; margin-top: 0.2rem; }
    .internship-duration {
      display: inline-block; font-size: 0.72rem; font-weight: 600;
      background: var(--beige); color: var(--maroon); padding: 0.15rem 0.55rem;
      border-radius: 999px; margin-bottom: 0.75rem;
    }
    .internship-bullets { list-style: none; display: flex; flex-direction: column; gap: 0.4rem; }
    .internship-bullets li {
      position: relative; padding-left: 1.1rem;
      font-size: 0.87rem; color: var(--gray-600); line-height: 1.55;
    }
    .internship-bullets li::before {
      content: ''; position: absolute; left: 0; top: 0.58em;
      width: 5px; height: 5px; border-radius: 50%; background: var(--maroon);
    }

    /* ===== EDUCATION ===== */
    #education { background: var(--gray-50); }
    .edu-card {
      background: linear-gradient(135deg, #110808 0%, #1e1010 100%);
      border-radius: 16px; padding: 2.5rem; color: var(--white);
      position: relative; overflow: hidden;
    }
    .edu-card::before {
      content: ''; position: absolute; top: -50px; right: -50px; width: 200px; height: 200px;
      background: radial-gradient(circle, rgba(125,45,45,0.18) 0%, transparent 70%); border-radius: 50%;
    }
    .edu-card h3 { font-family: 'Playfair Display', serif; font-size: 1.5rem; font-weight: 600; margin-bottom: 0.4rem; }
    .edu-school { color: #c08080; font-size: 0.95rem; margin-bottom: 0.25rem; }
    .edu-date { font-size: 0.8rem; color: rgba(255,255,255,0.4); margin-bottom: 1.25rem; }
    .edu-details { list-style: none; display: flex; flex-direction: column; gap: 0.6rem; }
    .edu-details li {
      font-size: 0.9rem; color: rgba(255,255,255,0.75);
      padding-left: 1.2rem; position: relative; line-height: 1.6;
    }
    .edu-details li::before {
      content: ''; position: absolute; left: 0; top: 0.6em;
      width: 5px; height: 5px; border-radius: 50%; background: #9e3a3a;
    }

    /* ===== LANGUAGES ===== */
    #languages { background: var(--white); }
    .lang-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
    .lang-card {
      background: var(--gray-50); border-radius: 12px; padding: 1.75rem;
      border: 1px solid var(--gray-200); text-align: center;
      opacity: 0; transform: translateY(20px); transition: all 0.3s;
    }
    .lang-card.visible { animation: fadeUp 0.5s forwards; }
    .lang-card:hover { box-shadow: 0 8px 30px rgba(125,45,45,0.1); border-color: var(--maroon); }
    .lang-flag { font-size: 2.5rem; display: block; margin-bottom: 0.75rem; }
    .lang-card h3 { font-size: 1.1rem; font-weight: 700; color: var(--gray-800); margin-bottom: 0.25rem; }
    .lang-level { font-size: 0.85rem; color: var(--gray-400); margin-bottom: 0.75rem; }
    .lang-bar { height: 4px; background: var(--gray-100); border-radius: 2px; overflow: hidden; }
    .lang-bar-fill {
      height: 100%; width: var(--level);
      background: linear-gradient(90deg, var(--maroon), var(--maroon-light)); border-radius: 2px;
    }

    /* ===== CONTACT ===== */
    #contact { background: linear-gradient(160deg, #0a0606 0%, #130a0a 60%, #1e1010 100%); }
    #contact .section-label { color: #c08080; }
    #contact .section-title { color: var(--white); }
    .contact-text { color: rgba(255,255,255,0.65); font-size: 1.05rem; max-width: 560px; margin-bottom: 2.5rem; line-height: 1.7; }
    .contact-links { display: flex; flex-wrap: wrap; gap: 1rem; }
    .contact-links a {
      display: inline-flex; align-items: center; gap: 0.5rem;
      padding: 0.75rem 1.6rem; border-radius: 999px;
      font-size: 0.9rem; font-weight: 600; text-decoration: none; transition: all 0.25s;
      min-height: 44px;
    }
    .cta-email { background: var(--maroon); color: var(--white); }
    .cta-email:hover { background: var(--maroon-light); transform: translateY(-2px); }
    .cta-linkedin { border: 1px solid rgba(255,255,255,0.3); color: var(--white); }
    .cta-linkedin:hover { border-color: var(--white); background: rgba(255,255,255,0.05); }

    /* ===== FOOTER ===== */
    footer {
      background: #080404; border-top: 1px solid rgba(255,255,255,0.06);
      text-align: center; padding: 1.5rem; padding-bottom: calc(1.5rem + var(--safe-bottom));
      font-size: 0.8rem; color: var(--gray-400);
    }

    /* ===== ANIMATIONS ===== */
    @keyframes fadeUp { to { opacity: 1; transform: translateY(0); } }
    @keyframes fadeScale { to { opacity: 1; transform: scale(1); } }
    @keyframes slideRight { to { opacity: 1; transform: translateX(0); } }
    @keyframes scrollPulse {
      0%, 100% { opacity: 0.3; transform: scaleY(1); }
      50% { opacity: 1; transform: scaleY(1.3); }
    }

    /* ===== RESPONSIVE: Tablet landscape & small desktops ===== */
    @media (max-width: 1024px) {
      .section-inner { max-width: 100%; }
      .skills-grid { grid-template-columns: repeat(2, 1fr); }
      .internship-grid { grid-template-columns: repeat(2, 1fr); }
    }

    /* ===== RESPONSIVE: Tablet portrait ===== */
    @media (max-width: 768px) {
      .nav-links {
        display: flex; flex-direction: column; position: absolute;
        top: calc(60px + var(--safe-top)); left: 0; right: 0;
        background: rgba(14,10,10,0.98); padding: 0 2rem;
        gap: 0; max-height: 0; overflow: hidden;
        transition: max-height 0.35s ease, padding 0.35s ease;
      }
      .nav-links.open {
        max-height: 400px; padding: 1rem 2rem 1.5rem;
      }
      .nav-links a {
        display: block; padding: 0.75rem 0;
        min-height: 44px; display: flex; align-items: center;
      }
      .nav-toggle { display: flex; align-items: center; justify-content: center; }

      .hero { min-height: auto; min-height: auto; padding: 7rem 1.5rem 4rem; }
      .hero-content { max-width: 100%; }
      .hero-photo { width: 110px; height: 110px; margin-bottom: 1.5rem; }
      .hero-photo-placeholder { font-size: 2.4rem; }
      .hero-tagline { font-size: 1rem; }
      .hero-summary { font-size: 0.95rem; margin-bottom: 2rem; }
      .hero-stats { gap: 1.5rem; }
      .stat-number { font-size: 1.6rem; }
      .hero-contact { flex-direction: column; align-items: center; }
      .hero-contact a { width: 100%; max-width: 280px; justify-content: center; }

      section { padding: 3.5rem 1.25rem; }
      .section-title { margin-bottom: 2rem; }
      .skills-grid { grid-template-columns: 1fr; gap: 1rem; }
      .internship-grid { grid-template-columns: 1fr; gap: 1rem; }
      .lang-grid { grid-template-columns: repeat(3, 1fr); gap: 1rem; }
      .edu-card { padding: 1.75rem; }
      .edu-card h3 { font-size: 1.25rem; }
      .job-header { flex-direction: column; gap: 0.25rem; }
      .job-date { align-self: flex-start; }
      .contact-links { flex-direction: column; }
      .contact-links a { width: 100%; justify-content: center; }
      .timeline-item { padding-left: 2rem; }
    }

    /* ===== RESPONSIVE: Large phones ===== */
    @media (max-width: 540px) {
      .hero { padding: 6rem 1rem 3rem; }
      .hero h1 { font-size: 2rem; }
      .hero-tagline { font-size: 0.9rem; }
      .hero-summary { font-size: 0.9rem; line-height: 1.6; }
      .hero-stats { gap: 1rem; }
      .stat-number { font-size: 1.4rem; }
      .stat-label { font-size: 0.68rem; }

      section { padding: 2.5rem 1rem; }
      .section-title { font-size: 1.5rem; margin-bottom: 1.5rem; }
      .skills-intro { font-size: 0.9rem; margin-bottom: 2rem; }
      .skill-card { padding: 1.25rem; }
      .skill-card h3 { font-size: 0.95rem; }
      .skill-desc { font-size: 0.82rem; }
      .skill-tags span { font-size: 0.7rem; padding: 0.2rem 0.5rem; }
      .internship-card { padding: 1.25rem; }
      .internship-header { gap: 0.75rem; }
      .internship-company { font-size: 0.92rem; }
      .internship-bullets li { font-size: 0.82rem; }
      .lang-grid { grid-template-columns: 1fr 1fr 1fr; gap: 0.75rem; }
      .lang-card { padding: 1.25rem 0.75rem; }
      .lang-card h3 { font-size: 0.95rem; }
      .lang-flag { font-size: 2rem; }
      .edu-card { padding: 1.5rem; }
      .edu-card h3 { font-size: 1.15rem; }
      .edu-details li { font-size: 0.82rem; }
      .job-bullets li { font-size: 0.85rem; }
      .job-title { font-size: 1.05rem; }
      .job-tag { font-size: 0.65rem; }
      .timeline::before { left: 0; }
      .timeline-item { padding-left: 1.5rem; margin-bottom: 2.5rem; }
      .timeline-dot { left: -6px; width: 12px; height: 12px; }
      .contact-text { font-size: 0.92rem; }
      .contact-links a { font-size: 0.85rem; padding: 0.65rem 1.2rem; }
      .scroll-indicator { bottom: 1rem; }
    }

    /* ===== RESPONSIVE: Small phones ===== */
    @media (max-width: 380px) {
      .nav-inner { padding: 0 1rem; }
      .hero { padding: 5.5rem 0.75rem 2.5rem; }
      .hero-photo { width: 90px; height: 90px; margin-bottom: 1.25rem; }
      .hero-photo-placeholder { font-size: 2rem; }
      .hero h1 { font-size: 1.7rem; }
      .hero-tagline { font-size: 0.82rem; }
      .hero-summary { font-size: 0.82rem; }
      .hero-stats { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
      .stat-number { font-size: 1.3rem; }
      .hero-contact a { padding: 0.6rem 1rem; font-size: 0.8rem; }

      section { padding: 2rem 0.75rem; }
      .section-label { font-size: 0.7rem; }
      .section-title { font-size: 1.3rem; }
      .lang-grid { grid-template-columns: 1fr; }
      .lang-card { display: flex; align-items: center; gap: 1rem; text-align: left; padding: 1rem 1.25rem; }
      .lang-flag { font-size: 1.8rem; margin-bottom: 0; flex-shrink: 0; }
      .lang-card h3 { margin-bottom: 0.1rem; }
      .lang-bar { flex: 1; }
      .lang-info { flex: 1; }
      .edu-card { padding: 1.25rem; }
      .edu-card h3 { font-size: 1.05rem; }
      .edu-school { font-size: 0.85rem; }
      .edu-details li { font-size: 0.8rem; padding-left: 1rem; }
      .contact-text { font-size: 0.85rem; }
      .internship-icon { width: 36px; height: 36px; }
      .skill-icon { width: 40px; height: 40px; }
    }

    /* ===== RESPONSIVE: Landscape phones ===== */
    @media (max-height: 500px) and (orientation: landscape) {
      .hero { min-height: auto; padding: 5rem 2rem 2rem; }
      .hero-photo { width: 80px; height: 80px; margin-bottom: 1rem; }
      .hero-photo-placeholder { font-size: 1.8rem; }
      .hero h1 { font-size: 1.8rem; }
      .hero-tagline { font-size: 0.85rem; margin-bottom: 0.75rem; }
      .hero-summary { font-size: 0.85rem; margin-bottom: 1.5rem; }
      .hero-stats { gap: 1.5rem; }
      .stat-number { font-size: 1.4rem; }
      .hero-contact { margin-top: 1.5rem; }
      .scroll-indicator { display: none; }
    }

    /* ===== Disable hover effects on touch devices ===== */
    @media (hover: none) {
      .skill-card:hover,
      .internship-card:hover,
      .lang-card:hover { transform: none; box-shadow: none; }
      .btn-primary:hover, .btn-outline:hover,
      .cta-email:hover, .cta-linkedin:hover { transform: none; }
    }

    /* ===== Reduced motion ===== */
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
      html { scroll-behavior: auto; }
    }
  </style>
</head>
<body>

<nav id="navbar">
  <div class="nav-inner">
    <div class="nav-logo">Julie<span>.</span></div>
    <button class="nav-toggle" id="navToggle" aria-label="Toggle menu" aria-expanded="false">
      <span></span><span></span><span></span>
    </button>
    <ul class="nav-links" id="navLinks" role="navigation">
      <li><a href="#experience">Experience</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#internships">Internships</a></li>
      <li><a href="#education">Education</a></li>
      <li><a href="#languages">Languages</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </div>
</nav>

<section class="hero" id="hero">
  <div class="hero-content">
    <div class="hero-photo">
      <div class="hero-photo-placeholder">JP</div>
    </div>
    <h1>Julie P&eacute;deville</h1>
    <p class="hero-tagline">Account Manager &bull; CRM Strategist &bull; Revenue Growth Partner</p>
    <p class="hero-summary">
      Bilingual French-English professional with 7+ years of international experience driving revenue growth, managing strategic client relationships, and leading cross-functional teams across Europe, North America, and the Middle East.
    </p>
    <div class="hero-stats">
      <div class="stat">
        <div class="stat-number">7<span>+</span></div>
        <div class="stat-label">Years Experience</div>
      </div>
      <div class="stat">
        <div class="stat-number">35<span>%+</span></div>
        <div class="stat-label">Client Revenue Driven</div>
      </div>
      <div class="stat">
        <div class="stat-number">4</div>
        <div class="stat-label">Countries Worked</div>
      </div>
      <div class="stat">
        <div class="stat-number">2</div>
        <div class="stat-label">Languages Fluent</div>
      </div>
    </div>
    <div class="hero-contact">
      <a href="mailto:julie.pedeville@gmail.com" class="btn-primary">
        <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        Get in Touch
      </a>
      <a href="https://www.linkedin.com/in/julie-pedeville" target="_blank" rel="noopener noreferrer" class="btn-outline">
        <svg width="16" height="16" fill="currentColor" viewBox="0 0 24 24"><path d="M20.5 2h-17A1.5 1.5 0 002 3.5v17A1.5 1.5 0 003.5 22h17a1.5 1.5 0 001.5-1.5v-17A1.5 1.5 0 0020.5 2zM8 19H5v-9h3zM6.5 8.25A1.75 1.75 0 118.3 6.5a1.78 1.78 0 01-1.8 1.75zM19 19h-3v-4.74c0-1.42-.6-1.93-1.38-1.93A1.74 1.74 0 0013 14.19V19h-3v-9h2.9v1.3a3.11 3.11 0 012.7-1.4c1.55 0 3.36.86 3.36 3.66z"/></svg>
        LinkedIn
      </a>
    </div>
  </div>
  <div class="scroll-indicator"><span></span></div>
</section>

<section id="experience">
  <div class="section-inner">
    <p class="section-label">Career</p>
    <h2 class="section-title">Professional Experience</h2>
    <div class="timeline">

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="job-header">
          <div class="job-title">Team Leader &ndash; Account Manager</div>
          <span class="job-date">Feb. 2025 &ndash; Jan. 2026</span>
        </div>
        <div class="job-company"><strong>Emailclub Agency LLP</strong> &bull; Remote</div>
        <ul class="job-bullets">
          <li>Owned end-to-end client relationships for top French e-commerce brands, acting as the strategic point of contact and generating over 35% of client revenue through multichannel lifecycle marketing.</li>
          <li>Led a cross-functional squad of CRM specialists and designers, orchestrating delivery of high-impact customer journeys that consistently improve engagement, retention, and ROI.</li>
          <li>Deployed AI-powered automation (Klaviyo, Customer.io, etc.) to optimize segmentation, accelerate campaign velocity, and unlock new growth levers for client accounts.</li>
          <li>Acted as a trusted commercial advisor to clients, identifying upsell and expansion opportunities, aligning digital strategy with revenue goals, and delivering measurable business outcomes.</li>
        </ul>
        <div>
          <span class="job-tag tag-a">Revenue Growth</span>
          <span class="job-tag tag-b">Cross-Functional Team Leadership</span>
          <span class="job-tag tag-c">CRM Strategy &amp; Client Segmentation</span>
          <span class="job-tag tag-d">Data-Driven Decision Making</span>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="job-header">
          <div class="job-title">Bilingual CRM Manager &amp; Email Marketing Specialist</div>
          <span class="job-date">Sept. 2023 &ndash; Jan. 2025</span>
        </div>
        <div class="job-company"><strong>Emailclub Agency LLP</strong> &bull; Remote</div>
        <ul class="job-bullets">
          <li>Designed and launched high-conversion, bilingual (FR/EN) omnichannel campaigns &mdash; email, WhatsApp, SMS &mdash; along with loyalty programs that lifted engagement and customer lifetime value across key segments.</li>
          <li>Mined CRM data and ran rigorous A/B testing to sharpen targeting, improve acquisition efficiency, and systematically increase campaign ROI.</li>
        </ul>
        <div>
          <span class="job-tag tag-a">Lifecycle &amp; Multichannel Marketing</span>
          <span class="job-tag tag-b">Marketing Automation &amp; AI Tools</span>
          <span class="job-tag tag-c">Performance Marketing</span>
          <span class="job-tag tag-d">A/B Testing &amp; Optimization</span>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="job-header">
          <div class="job-title">Bilingual Equipment Finance Associate</div>
          <span class="job-date">Jan. 2022 &ndash; June 2023</span>
        </div>
        <div class="job-company"><strong>Royal Bank of Canada</strong> &bull; Burlington, Canada</div>
        <ul class="job-bullets">
          <li>Managed a portfolio of commercial clients end-to-end &mdash; from lease origination through closing &mdash; ensuring exceptional service across bilingual (EN/FR) accounts and consistently meeting deal targets.</li>
          <li>Partnered cross-functionally with Sales, VPs, and Legal to accelerate deal velocity, streamline compliance, and remove friction from the client experience.</li>
          <li>Built trusted advisor relationships that improved client satisfaction scores and contributed to long-term account retention and expansion.</li>
        </ul>
        <div>
          <span class="job-tag tag-a">Deal Execution</span>
          <span class="job-tag tag-b">Commercial Banking</span>
          <span class="job-tag tag-c">Client Relationship Management</span>
          <span class="job-tag tag-d">Customer Success</span>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="job-header">
          <div class="job-title">Bilingual Client Services Specialist</div>
          <span class="job-date">Aug. 2020 &ndash; Dec. 2021</span>
        </div>
        <div class="job-company"><strong>Royal Bank of Canada</strong> &bull; Burlington, Canada</div>
        <ul class="job-bullets">
          <li>Delivered responsive, solutions-oriented support to commercial clients &mdash; managing payment deferrals, resolving complex service escalations, and safeguarding account health.</li>
          <li>Strengthened client loyalty and satisfaction through proactive outreach, empathetic communication, and resourceful problem-solving during pandemic-related disruptions.</li>
        </ul>
        <div>
          <span class="job-tag tag-a">Client Support</span>
          <span class="job-tag tag-b">Bilingual Communication</span>
          <span class="job-tag tag-c">Problem Solving</span>
          <span class="job-tag tag-d">Retention</span>
        </div>
      </div>

      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="job-header">
          <div class="job-title">Marketing Executive</div>
          <span class="job-date">May 2017 &ndash; Sept. 2019</span>
        </div>
        <div class="job-company"><strong>Integral Shopper Agency</strong> &bull; Dubai, UAE</div>
        <ul class="job-bullets">
          <li>Planned and executed digital and experiential B2C campaigns for global FMCG and retail brands (Nestle, Johnson &amp; Johnson, Carrefour, Spinneys etc.) &mdash; driving measurable gains in customer acquisition, engagement, and brand loyalty.</li>
          <li>Coordinated in-store promotional projects across retail locations in Dubai and Abu Dhabi, ensuring smooth execution and a positive client and customer experience.</li>
          <li>Collaborated with regional stakeholders to translate data-driven insights into customer-centric initiatives that strengthened brand positioning and market share.</li>
        </ul>
        <div>
          <span class="job-tag tag-a">Gamification &amp; Customer Engagement</span>
          <span class="job-tag tag-b">Customer Retention &amp; Loyalty</span>
          <span class="job-tag tag-c">Trade Marketing &amp; Events</span>
          <span class="job-tag tag-d">Digital Marketing Strategy</span>
        </div>
      </div>

    </div>
  </div>
</section>

<section id="skills">
  <div class="section-inner">
    <p class="section-label">Capabilities</p>
    <h2 class="section-title">Skills &amp; Expertise</h2>
    <p class="skills-intro">
      A proven track record of driving client success through strategic account management, data-driven marketing, and cross-functional collaboration — from e-commerce agencies to global banking.
    </p>
    <div class="skills-grid">

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#7d2d2d;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M16 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="8.5" cy="7" r="4"/><line x1="20" y1="8" x2="20" y2="14"/><line x1="23" y1="11" x2="17" y2="11"/></svg>
        </div>
        <h3>Strategic Account Management &amp; Revenue Growth</h3>
        <p class="skill-desc">
          Owner of high-value client portfolios, consistently identifying expansion opportunities and delivering 35%+ revenue contributions through consultative selling and strategic upselling.
        </p>
        <div class="skill-tags">
          <span>Client Relationship Management</span>
          <span>Consultative Selling</span>
          <span>Upsell & Cross-Sell</span>
          <span>Revenue Attribution</span>
          <span>Commercial Strategy</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#9e3a3a;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
        </div>
        <h3>CRM Strategy &amp; Marketing Automation</h3>
        <p class="skill-desc">
          Expert in designing and deploying AI-powered lifecycle campaigns across Klaviyo, Customer.io, and Shopify — driving engagement, retention, and measurable ROI through segmentation and testing.
        </p>
        <div class="skill-tags">
          <span>Klaviyo</span>
          <span>Customer.io</span>
          <span>Shopify</span>
          <span>Salesforce</span>
          <span>Lifecycle Marketing</span>
          <span>Email & SMS Campaigns</span>
          <span>Customer Segmentation</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#c09080;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>
        </div>
        <h3>Data-Driven Growth &amp; Performance Optimization</h3>
        <p class="skill-desc">
          Translate CRM data and A/B test results into actionable insights that systematically improve campaign performance, customer acquisition efficiency, and long-term retention.
        </p>
        <div class="skill-tags">
          <span>A/B Testing</span>
          <span>Performance Analytics</span>
          <span>Customer Journey Mapping</span>
          <span>Retention Programs</span>
          <span>ROI Tracking</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#a07878;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
        </div>
        <h3>Cross-Functional Team Leadership &amp; Project Management</h3>
        <p class="skill-desc">
          Lead cross-functional squads of CRM specialists, designers, and developers to deliver high-impact customer journeys on time and aligned with business goals.
        </p>
        <div class="skill-tags">
          <span>Team Leadership</span>
          <span>Agile Delivery</span>
          <span>Stakeholder Management</span>
          <span>ClickUp</span>
          <span>Asana</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#7d2d2d;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><polyline points="22 4 12 14.01 9 11.01"/></svg>
        </div>
        <h3>Customer Success &amp; Client Retention</h3>
        <p class="skill-desc">
          Proven ability to proactively resolve client challenges, manage escalations, and strengthen loyalty through empathetic communication and resourceful problem-solving.
        </p>
        <div class="skill-tags">
          <span>Client Support</span>
          <span>Escalation Management</span>
          <span>Account Health Monitoring</span>
          <span>Churn Prevention</span>
          <span>Customer Satisfaction</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#9e3a3a;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg>
        </div>
        <h3>Multichannel Campaign Execution &amp; Brand Strategy</h3>
        <p class="skill-desc">
          Design and execute integrated B2C and B2B campaigns across email, WhatsApp, SMS, in-store activations, and digital channels for global FMCG and retail brands.
        </p>
        <div class="skill-tags">
          <span>Omnichannel Marketing</span>
          <span>Campaign Management</span>
          <span>Trade Marketing</span>
          <span>Event Coordination</span>
          <span>Brand Positioning</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#c09080;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
        </div>
        <h3>Bilingual Communication &amp; International Business</h3>
        <p class="skill-desc">
          Fluent in French and English with experience managing client relationships and campaigns across EMEA, North America, and the Middle East in B2B and B2C contexts.
        </p>
        <div class="skill-tags">
          <span>Bilingual (FR/EN)</span>
          <span>Multicultural Teams</span>
          <span>Remote Collaboration</span>
          <span>EMEA & APAC Markets</span>
        </div>
      </div>

      <div class="skill-card">
        <div class="skill-icon" style="background:#1a0808;color:#a07878;">
          <svg width="24" height="24" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M12 19l7-7 3 3-7 7-3-3z"/><path d="M18 13l-1.5-7.5L2 2l3.5 14.5L13 18l5-5z"/><path d="M2 2l7.586 7.586"/><circle cx="11" cy="11" r="2"/></svg>
        </div>
        <h3>Content Creation &amp; Design Collaboration</h3>
        <p class="skill-desc">
          Collaborate with designers and create bilingual marketing content using Figma and Canva, ensuring brand consistency and compelling messaging across channels.
        </p>
        <div class="skill-tags">
          <span>Bilingual Copywriting</span>
          <span>Figma</span>
          <span>Canva</span>
          <span>Brand Guidelines</span>
        </div>
      </div>

    </div>
  </div>
</section>

<section id="internships">
  <div class="section-inner">
    <p class="section-label">Early Career</p>
    <h2 class="section-title">Internships</h2>
    <div class="internship-grid">

      <div class="internship-card">
        <div class="internship-header">
          <div class="internship-icon">
            <svg width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
          </div>
          <div>
            <div class="internship-company">Groupe Bel</div>
            <div class="internship-role">Responsible Procurement &amp; Subcontracting Assistant</div>
          </div>
        </div>
        <span class="internship-duration">6 months &bull; France</span>
        <ul class="internship-bullets">
          <li>Adapted the subcontracting procurement strategy to meet growth challenges and evolving business needs.</li>
          <li>Applied the Responsible Purchasing Charter through supplier evaluations via EcoVadis and produced communication materials promoting CSR and HSE initiatives.</li>
        </ul>
      </div>

      <div class="internship-card">
        <div class="internship-header">
          <div class="internship-icon">
            <svg width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M19.07 4.93a10 10 0 0 1 0 14.14M4.93 4.93a10 10 0 0 0 0 14.14"/><path d="M15.54 8.46a5 5 0 0 1 0 7.07M8.46 8.46a5 5 0 0 0 0 7.07"/></svg>
          </div>
          <div>
            <div class="internship-company">Precicast</div>
            <div class="internship-role">Aerospace Spare Parts Logistics Agent</div>
          </div>
        </div>
        <span class="internship-duration">3 months &bull; France</span>
        <ul class="internship-bullets">
          <li>Handled scheduling, planning, and production tracking for aerospace spare parts.</li>
          <li>Monitored raw material stock levels to ensure supply continuity and production efficiency.</li>
        </ul>
      </div>

      <div class="internship-card">
        <div class="internship-header">
          <div class="internship-icon">
            <svg width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M6 2L3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"/><line x1="3" y1="6" x2="21" y2="6"/><path d="M16 10a4 4 0 0 1-8 0"/></svg>
          </div>
          <div>
            <div class="internship-company">Fnac Darty</div>
            <div class="internship-role">Sales Advisor</div>
          </div>
        </div>
        <span class="internship-duration">3 months &bull; France</span>
        <ul class="internship-bullets">
          <li>Provided expert product advice and consultative selling support to customers across multiple categories.</li>
          <li>Consistently met and exceeded ambitious sales targets during a high-traffic retail period.</li>
        </ul>
      </div>

    </div>
  </div>
</section>

<section id="education">
  <div class="section-inner">
    <p class="section-label">Foundation</p>
    <h2 class="section-title">Education</h2>
    <div class="edu-card">
      <h3>Master's in Business Development &amp; Strategy</h3>
      <p class="edu-school">Ipag Business School &bull; Paris, France</p>
      <p class="edu-date">2012 &ndash; 2017</p>
      <ul class="edu-details">
        <li>International exchange at Yunnan Normal University (China) &mdash; developing cross-cultural acumen and global business perspective.</li>
        <li>Volunteered in Sri Lanka supporting children with autism &mdash; strengthening empathy, adaptability, and communication skills.</li>
      </ul>
    </div>
  </div>
</section>

<section id="languages">
  <div class="section-inner">
    <p class="section-label">Communication</p>
    <h2 class="section-title">Languages</h2>
    <div class="lang-grid">
      <div class="lang-card">
        <span class="lang-flag">&#127467;&#127479;</span>
        <div class="lang-info">
          <h3>French</h3>
          <p class="lang-level">Native</p>
          <div class="lang-bar"><div class="lang-bar-fill" style="--level:100%"></div></div>
        </div>
      </div>
      <div class="lang-card">
        <span class="lang-flag">&#127468;&#127463;</span>
        <div class="lang-info">
          <h3>English</h3>
          <p class="lang-level">Fluent / Bilingual</p>
          <div class="lang-bar"><div class="lang-bar-fill" style="--level:95%"></div></div>
        </div>
      </div>
      <div class="lang-card">
        <span class="lang-flag">&#127466;&#127480;</span>
        <div class="lang-info">
          <h3>Spanish</h3>
          <p class="lang-level">Actively Learning</p>
          <div class="lang-bar"><div class="lang-bar-fill" style="--level:35%"></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="contact">
  <div class="section-inner">
    <p class="section-label">Let's Connect</p>
    <h2 class="section-title">Ready to Drive Results Together?</h2>
    <p class="contact-text">
      I'm looking for my next Account Manager opportunity where I can combine strategic relationship management with data-driven growth. Let's talk.
    </p>
    <div class="contact-links">
      <a href="mailto:julie.pedeville@gmail.com" class="cta-email">
        <svg width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        julie.pedeville@gmail.com
      </a>
      <a href="https://www.linkedin.com/in/julie-pedeville" target="_blank" rel="noopener noreferrer" class="cta-linkedin">
        <svg width="18" height="18" fill="currentColor" viewBox="0 0 24 24"><path d="M20.5 2h-17A1.5 1.5 0 002 3.5v17A1.5 1.5 0 003.5 22h17a1.5 1.5 0 001.5-1.5v-17A1.5 1.5 0 0020.5 2zM8 19H5v-9h3zM6.5 8.25A1.75 1.75 0 118.3 6.5a1.78 1.78 0 01-1.8 1.75zM19 19h-3v-4.74c0-1.42-.6-1.93-1.38-1.93A1.74 1.74 0 0013 14.19V19h-3v-9h2.9v1.3a3.11 3.11 0 012.7-1.4c1.55 0 3.36.86 3.36 3.66z"/></svg>
        LinkedIn Profile
      </a>
      <a href="tel:+34695937333" class="cta-linkedin">
        <svg width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" viewBox="0 0 24 24"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
        +34 695 937 333
      </a>
    </div>
  </div>
</section>

<footer>
  &copy; 2026 Julie P&eacute;deville. Built with purpose.
</footer>

<script>
  // Mobile nav toggle with animated hamburger
  const toggle = document.getElementById('navToggle');
  const links = document.getElementById('navLinks');
  toggle.addEventListener('click', () => {
    const isOpen = links.classList.toggle('open');
    toggle.classList.toggle('active', isOpen);
    toggle.setAttribute('aria-expanded', isOpen);
  });
  links.querySelectorAll('a').forEach(a => a.addEventListener('click', () => {
    links.classList.remove('open');
    toggle.classList.remove('active');
    toggle.setAttribute('aria-expanded', 'false');
  }));

  // Close mobile menu on outside click
  document.addEventListener('click', (e) => {
    if (!e.target.closest('nav') && links.classList.contains('open')) {
      links.classList.remove('open');
      toggle.classList.remove('active');
      toggle.setAttribute('aria-expanded', 'false');
    }
  });

  // Intersection observer for scroll animations
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });
  document.querySelectorAll('.timeline-item, .skill-card, .lang-card, .internship-card').forEach(el => observer.observe(el));

  // Active nav link tracking + hide-on-scroll navbar
  const sections = document.querySelectorAll('section[id]');
  const navAnchors = document.querySelectorAll('.nav-links a');
  let lastScroll = 0;
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => { if (window.scrollY >= s.offsetTop - 200) current = s.id; });
    navAnchors.forEach(a => { a.classList.toggle('active', a.getAttribute('href') === '#' + current); });
    const cs = window.scrollY;
    navbar.classList.toggle('hidden', cs > lastScroll && cs > 100);
    lastScroll = cs;
  }, { passive: true });
</script>
</body>
</html>
