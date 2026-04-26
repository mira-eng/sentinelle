# sentinelle
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SentinelleCI — Transparence Citoyenne</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    :root {
      --green-deep: #0A2E1C;
      --green-mid: #0F4A2B;
      --green-vivid: #1A7A48;
      --green-bright: #22A45D;
      --green-light: #4BC982;
      --orange: #F5842A;
      --orange-light: #FF9F4A;
      --cream: #F9F5EE;
      --cream-dark: #EDE8DE;
      --white: #FFFFFF;
      --text-dark: #0A1F12;
      --text-mid: #2D5040;
      --text-light: #6B8F79;
    }
 
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
 
    html { scroll-behavior: smooth; }
 
    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--cream);
      color: var(--text-dark);
      overflow-x: hidden;
    }
 
    /* ---- NOISE TEXTURE OVERLAY ---- */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 1000;
      opacity: 0.5;
    }
 
    h1, h2, h3, h4 {
      font-family: 'Syne', sans-serif;
    }
 
    /* ---- NAVBAR ---- */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 900;
      padding: 0 48px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      height: 72px;
      background: rgba(249, 245, 238, 0.85);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid rgba(10, 46, 28, 0.08);
      transition: background 0.3s;
    }
 
    .nav-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1.4rem;
      letter-spacing: -0.03em;
      color: var(--green-deep);
      text-decoration: none;
    }
    .nav-logo span { color: var(--orange); }
 
    .nav-links {
      display: flex;
      gap: 36px;
      align-items: center;
    }
    .nav-links a {
      text-decoration: none;
      font-size: 0.9rem;
      font-weight: 500;
      color: var(--text-mid);
      transition: color 0.2s;
      letter-spacing: 0.01em;
    }
    .nav-links a:hover { color: var(--green-vivid); }
 
    .nav-cta {
      background: var(--green-deep) !important;
      color: var(--cream) !important;
      padding: 10px 22px;
      border-radius: 40px;
      font-weight: 600 !important;
      transition: background 0.2s, transform 0.2s !important;
    }
    .nav-cta:hover {
      background: var(--green-vivid) !important;
      transform: translateY(-1px);
    }
 
    /* ---- HERO ---- */
    .hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 120px 48px 80px;
      position: relative;
      overflow: hidden;
    }
 
    .hero-bg-circle {
      position: absolute;
      border-radius: 50%;
      pointer-events: none;
    }
    .hero-bg-circle-1 {
      width: 700px; height: 700px;
      background: radial-gradient(circle, rgba(34,164,93,0.12) 0%, transparent 70%);
      top: -200px; right: -100px;
      animation: pulse 8s ease-in-out infinite;
    }
    .hero-bg-circle-2 {
      width: 400px; height: 400px;
      background: radial-gradient(circle, rgba(245,132,42,0.08) 0%, transparent 70%);
      bottom: 0; left: -100px;
      animation: pulse 10s ease-in-out infinite reverse;
    }
 
    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.08); opacity: 0.7; }
    }
 
    .hero-label {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(10, 46, 28, 0.07);
      border: 1px solid rgba(10, 46, 28, 0.12);
      padding: 7px 16px;
      border-radius: 40px;
      font-size: 0.82rem;
      font-weight: 500;
      color: var(--green-vivid);
      letter-spacing: 0.05em;
      text-transform: uppercase;
      margin-bottom: 32px;
      width: fit-content;
      animation: fadeUp 0.8s ease both;
    }
    .hero-label .dot {
      width: 7px; height: 7px;
      background: var(--green-bright);
      border-radius: 50%;
      animation: blink 1.5s infinite;
    }
    @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0.2; } }
 
    .hero-title {
      font-size: clamp(3rem, 7vw, 6.5rem);
      font-weight: 800;
      line-height: 1.0;
      letter-spacing: -0.04em;
      color: var(--green-deep);
      max-width: 900px;
      animation: fadeUp 0.8s 0.1s ease both;
    }
    .hero-title .accent { color: var(--orange); display: block; }
 
    .hero-sub {
      font-size: 1.15rem;
      color: var(--text-mid);
      max-width: 560px;
      line-height: 1.7;
      margin-top: 28px;
      font-weight: 300;
      animation: fadeUp 0.8s 0.2s ease both;
    }
 
    .hero-actions {
      display: flex;
      gap: 16px;
      margin-top: 48px;
      flex-wrap: wrap;
      animation: fadeUp 0.8s 0.3s ease both;
    }
 
    .btn-primary {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      background: var(--orange);
      color: white;
      padding: 16px 32px;
      border-radius: 40px;
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 0.95rem;
      text-decoration: none;
      letter-spacing: 0.01em;
      transition: all 0.25s;
      box-shadow: 0 8px 24px rgba(245,132,42,0.35);
    }
    .btn-primary:hover {
      background: var(--orange-light);
      transform: translateY(-3px);
      box-shadow: 0 14px 32px rgba(245,132,42,0.4);
    }
 
    .btn-ghost {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      border: 1.5px solid rgba(10, 46, 28, 0.25);
      color: var(--green-deep);
      padding: 16px 32px;
      border-radius: 40px;
      font-family: 'Syne', sans-serif;
      font-weight: 600;
      font-size: 0.95rem;
      text-decoration: none;
      transition: all 0.25s;
    }
    .btn-ghost:hover {
      background: var(--green-deep);
      color: var(--cream);
      border-color: var(--green-deep);
    }
 
    .hero-stats-row {
      display: flex;
      gap: 48px;
      margin-top: 80px;
      padding-top: 48px;
      border-top: 1px solid rgba(10, 46, 28, 0.1);
      flex-wrap: wrap;
      animation: fadeUp 0.8s 0.4s ease both;
    }
    .hero-stat { }
    .hero-stat-num {
      font-family: 'Syne', sans-serif;
      font-size: 2.4rem;
      font-weight: 800;
      color: var(--green-deep);
      letter-spacing: -0.04em;
      line-height: 1;
    }
    .hero-stat-num span { color: var(--orange); }
    .hero-stat-label {
      font-size: 0.85rem;
      color: var(--text-light);
      margin-top: 6px;
      letter-spacing: 0.02em;
    }
 
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to { opacity: 1; transform: translateY(0); }
    }
 
    /* ---- MARQUEE BAND ---- */
    .marquee-band {
      background: var(--green-deep);
      padding: 16px 0;
      overflow: hidden;
      white-space: nowrap;
    }
    .marquee-inner {
      display: inline-flex;
      animation: marquee 20s linear infinite;
    }
    .marquee-item {
      display: inline-flex;
      align-items: center;
      gap: 16px;
      padding: 0 32px;
      font-family: 'Syne', sans-serif;
      font-weight: 600;
      font-size: 0.85rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--cream);
    }
    .marquee-dot {
      width: 6px; height: 6px;
      background: var(--orange);
      border-radius: 50%;
      flex-shrink: 0;
    }
    @keyframes marquee {
      from { transform: translateX(0); }
      to { transform: translateX(-50%); }
    }
 
    /* ---- SECTION TEMPLATE ---- */
    section {
      padding: 120px 48px;
    }
 
    .section-label {
      font-size: 0.78rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--orange);
      margin-bottom: 16px;
    }
    .section-title {
      font-size: clamp(2rem, 4vw, 3.2rem);
      font-weight: 800;
      letter-spacing: -0.03em;
      color: var(--green-deep);
      line-height: 1.1;
    }
    .section-sub {
      font-size: 1.05rem;
      color: var(--text-mid);
      max-width: 580px;
      line-height: 1.75;
      margin-top: 16px;
      font-weight: 300;
    }
 
    /* ---- PROBLEMES ---- */
    #problemes {
      background: var(--white);
    }
    .prob-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin-bottom: 64px;
      flex-wrap: wrap;
      gap: 24px;
    }
 
    .prob-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 24px;
    }
 
    .prob-card {
      background: var(--cream);
      border-radius: 28px;
      padding: 36px;
      border: 1px solid var(--cream-dark);
      transition: all 0.3s;
      position: relative;
      overflow: hidden;
    }
    .prob-card::after {
      content: '';
      position: absolute;
      bottom: 0; left: 0; right: 0;
      height: 3px;
      background: var(--orange);
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.3s;
    }
    .prob-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 24px 48px rgba(10,46,28,0.1);
    }
    .prob-card:hover::after {
      transform: scaleX(1);
    }
 
    .prob-icon {
      width: 56px; height: 56px;
      border-radius: 16px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.4rem;
      margin-bottom: 24px;
    }
    .prob-icon-road { background: rgba(245,132,42,0.12); color: var(--orange); }
    .prob-icon-trash { background: rgba(26,122,72,0.12); color: var(--green-vivid); }
    .prob-icon-water { background: rgba(30,136,229,0.12); color: #1E88E5; }
    .prob-icon-light { background: rgba(142,36,170,0.12); color: #8E24AA; }
 
    .prob-card h3 {
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--green-deep);
      margin-bottom: 10px;
      letter-spacing: -0.02em;
    }
    .prob-card p {
      font-size: 0.9rem;
      color: var(--text-light);
      line-height: 1.65;
    }
    .prob-impact {
      margin-top: 20px;
      padding: 12px 16px;
      background: rgba(245,132,42,0.08);
      border-radius: 12px;
      font-size: 0.83rem;
      font-weight: 500;
      color: var(--orange);
    }
 
    /* ---- HOW IT WORKS ---- */
    #fonctionnement {
      background: var(--green-deep);
      color: var(--cream);
      position: relative;
      overflow: hidden;
    }
    #fonctionnement::before {
      content: '';
      position: absolute;
      width: 600px; height: 600px;
      background: radial-gradient(circle, rgba(34,164,93,0.15) 0%, transparent 70%);
      top: -200px; right: -100px;
      border-radius: 50%;
    }
 
    #fonctionnement .section-title { color: var(--cream); }
    #fonctionnement .section-sub { color: rgba(249,245,238,0.6); }
 
    .steps-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
      gap: 2px;
      margin-top: 64px;
      background: rgba(255,255,255,0.06);
      border-radius: 32px;
      overflow: hidden;
    }
 
    .step {
      padding: 48px 36px;
      background: var(--green-deep);
      transition: background 0.3s;
    }
    .step:hover {
      background: var(--green-mid);
    }
    .step-num {
      font-family: 'Syne', sans-serif;
      font-size: 3.5rem;
      font-weight: 800;
      color: rgba(255,255,255,0.08);
      line-height: 1;
      margin-bottom: 24px;
      letter-spacing: -0.05em;
    }
    .step-icon {
      width: 48px; height: 48px;
      border-radius: 14px;
      background: rgba(245,132,42,0.15);
      color: var(--orange);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2rem;
      margin-bottom: 20px;
    }
    .step h3 {
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--cream);
      margin-bottom: 10px;
      letter-spacing: -0.02em;
    }
    .step p {
      font-size: 0.88rem;
      color: rgba(249,245,238,0.55);
      line-height: 1.7;
    }
 
    /* ---- BLOCKCHAIN ---- */
    #blockchain {
      background: var(--cream);
    }
 
    .blockchain-layout {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 64px;
      align-items: center;
      margin-top: 64px;
    }
 
    .blockchain-visual {
      background: var(--green-deep);
      border-radius: 32px;
      padding: 48px;
      position: relative;
      overflow: hidden;
      min-height: 400px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }
    .blockchain-visual::before {
      content: '';
      position: absolute;
      inset: 0;
      background: 
        radial-gradient(circle at 20% 50%, rgba(34,164,93,0.2) 0%, transparent 60%),
        radial-gradient(circle at 80% 50%, rgba(245,132,42,0.1) 0%, transparent 60%);
    }
 
    .chain-blocks {
      display: flex;
      flex-direction: column;
      gap: 12px;
      position: relative;
      z-index: 1;
    }
    .chain-block {
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 16px;
      padding: 16px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      animation: slideIn 0.5s ease both;
    }
    .chain-block:nth-child(1) { animation-delay: 0.1s; }
    .chain-block:nth-child(2) { animation-delay: 0.2s; }
    .chain-block:nth-child(3) { animation-delay: 0.3s; }
 
    @keyframes slideIn {
      from { opacity: 0; transform: translateX(-20px); }
      to { opacity: 1; transform: translateX(0); }
    }
 
    .chain-block-info { }
    .chain-block-type {
      font-size: 0.78rem;
      font-weight: 600;
      color: var(--orange);
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }
    .chain-block-hash {
      font-family: monospace;
      font-size: 0.75rem;
      color: rgba(255,255,255,0.4);
      margin-top: 3px;
    }
    .chain-block-badge {
      background: rgba(75,201,130,0.15);
      color: var(--green-light);
      border: 1px solid rgba(75,201,130,0.2);
      padding: 4px 10px;
      border-radius: 20px;
      font-size: 0.72rem;
      font-weight: 600;
      white-space: nowrap;
    }
    .chain-connector {
      width: 2px; height: 12px;
      background: rgba(255,255,255,0.1);
      margin-left: 24px;
    }
 
    .blockchain-features {
      display: flex;
      flex-direction: column;
      gap: 28px;
    }
    .bc-feature {
      display: flex;
      gap: 20px;
      align-items: flex-start;
    }
    .bc-feature-icon {
      width: 44px; height: 44px;
      border-radius: 12px;
      background: rgba(10,46,28,0.08);
      color: var(--green-vivid);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      flex-shrink: 0;
    }
    .bc-feature h4 {
      font-size: 1rem;
      font-weight: 700;
      color: var(--green-deep);
      margin-bottom: 6px;
      letter-spacing: -0.02em;
    }
    .bc-feature p {
      font-size: 0.88rem;
      color: var(--text-light);
      line-height: 1.65;
    }
 
    /* ---- TESTIMONIALS / IMPACT ---- */
    #impact {
      background: var(--white);
    }
 
    .impact-grid {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr;
      gap: 20px;
      margin-top: 64px;
    }
 
    .impact-card {
      border-radius: 28px;
      padding: 40px;
      position: relative;
      overflow: hidden;
    }
    .impact-card-main {
      background: var(--orange);
      color: white;
      grid-row: span 2;
    }
    .impact-card-dark {
      background: var(--green-deep);
      color: var(--cream);
    }
    .impact-card-light {
      background: var(--cream);
      border: 1px solid var(--cream-dark);
      color: var(--green-deep);
    }
 
    .impact-big-num {
      font-family: 'Syne', sans-serif;
      font-size: 4.5rem;
      font-weight: 800;
      letter-spacing: -0.05em;
      line-height: 1;
      margin-bottom: 8px;
    }
    .impact-card-main .impact-big-num { color: white; }
    .impact-card-dark .impact-big-num { color: var(--green-light); }
    .impact-card-light .impact-big-num { color: var(--green-deep); }
 
    .impact-card-label {
      font-size: 0.88rem;
      opacity: 0.75;
      font-weight: 300;
      line-height: 1.5;
    }
 
    .impact-card-main h3 {
      font-size: 1.4rem;
      font-weight: 700;
      margin-bottom: 16px;
      letter-spacing: -0.02em;
    }
    .impact-card-main p {
      font-size: 0.95rem;
      opacity: 0.85;
      line-height: 1.7;
      font-weight: 300;
      margin-bottom: 32px;
    }
 
    .impact-communes {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 24px;
    }
    .commune-tag {
      background: rgba(255,255,255,0.2);
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 0.78rem;
      font-weight: 600;
    }
 
    /* ---- CTA ---- */
    #cta {
      background: var(--green-deep);
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    #cta::before {
      content: '';
      position: absolute;
      width: 800px; height: 800px;
      background: radial-gradient(circle, rgba(34,164,93,0.15) 0%, transparent 60%);
      top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      border-radius: 50%;
    }
 
    #cta .section-label { color: rgba(249,245,238,0.5); }
    #cta .section-title {
      color: var(--cream);
      font-size: clamp(2.5rem, 5vw, 4rem);
      max-width: 700px;
      margin: 0 auto;
    }
    #cta .section-sub {
      color: rgba(249,245,238,0.55);
      margin: 16px auto 0;
      text-align: center;
    }
    #cta .hero-actions { justify-content: center; margin-top: 48px; }
    #cta .btn-ghost {
      border-color: rgba(249,245,238,0.3);
      color: var(--cream);
    }
    #cta .btn-ghost:hover {
      background: var(--cream);
      color: var(--green-deep);
    }
 
    /* ---- FOOTER ---- */
    footer {
      background: #060F09;
      padding: 64px 48px 40px;
    }
 
    .footer-top {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 56px;
      flex-wrap: wrap;
      gap: 40px;
    }
 
    .footer-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1.5rem;
      color: var(--cream);
      letter-spacing: -0.03em;
    }
    .footer-logo span { color: var(--orange); }
    .footer-tagline {
      color: rgba(249,245,238,0.35);
      font-size: 0.88rem;
      margin-top: 10px;
      max-width: 300px;
      line-height: 1.6;
    }
 
    .footer-links-group { }
    .footer-links-group h4 {
      font-family: 'Syne', sans-serif;
      font-size: 0.78rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: rgba(249,245,238,0.35);
      margin-bottom: 20px;
    }
    .footer-links-group a {
      display: block;
      color: rgba(249,245,238,0.6);
      text-decoration: none;
      font-size: 0.9rem;
      margin-bottom: 12px;
      transition: color 0.2s;
    }
    .footer-links-group a:hover { color: var(--cream); }
 
    .footer-bottom {
      border-top: 1px solid rgba(255,255,255,0.06);
      padding-top: 32px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 16px;
    }
    .footer-bottom p {
      color: rgba(249,245,238,0.2);
      font-size: 0.82rem;
    }
    .footer-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(75,201,130,0.1);
      border: 1px solid rgba(75,201,130,0.15);
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 0.78rem;
      color: var(--green-light);
    }
    .footer-badge-dot {
      width: 6px; height: 6px;
      background: var(--green-light);
      border-radius: 50%;
      animation: blink 1.5s infinite;
    }
 
    /* ---- SCROLL REVEAL ---- */
    .reveal {
      opacity: 0;
      transform: translateY(32px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: none;
    }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.4s; }
 
    /* ---- RESPONSIVE ---- */
    @media (max-width: 900px) {
      nav { padding: 0 24px; }
      .nav-links { gap: 20px; }
      .nav-links a:not(.nav-cta) { display: none; }
      section { padding: 80px 24px; }
      .hero { padding: 100px 24px 60px; }
      .hero-stats-row { gap: 28px; }
      .blockchain-layout { grid-template-columns: 1fr; }
      .impact-grid { grid-template-columns: 1fr 1fr; }
      .impact-card-main { grid-column: span 2; grid-row: span 1; }
      .footer-top { flex-direction: column; }
      footer { padding: 48px 24px 32px; }
    }
    @media (max-width: 600px) {
      .impact-grid { grid-template-columns: 1fr; }
      .impact-card-main { grid-column: span 1; }
      .steps-grid { grid-template-columns: 1fr; }
      .prob-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
 
<!-- NAVBAR -->
<nav>
  <a href="#" class="nav-logo">SENTINELLE<span>CI</span></a>
  <div class="nav-links">
    <a href="#problemes">Problèmes</a>
    <a href="#fonctionnement">Comment ça marche</a>
    <a href="#blockchain">Blockchain</a>
    <a href="#impact">Impact</a>
    <a href="#cta" class="nav-cta">Signaler un problème</a>
  </div>
</nav>
 
<!-- HERO -->
<section class="hero">
  <div class="hero-bg-circle hero-bg-circle-1"></div>
  <div class="hero-bg-circle hero-bg-circle-2"></div>
 
  <div class="hero-label">
    <div class="dot"></div>
    Initiative citoyenne · Côte d'Ivoire
  </div>
 
  <h1 class="hero-title">
    Signalez.<br>Suivez.
    <span class="accent">Responsabilisez.</span>
  </h1>
 
  <p class="hero-sub">
    SentinelleCI transforme chaque signalement citoyen en preuve immuable sur la blockchain. 
    Nids-de-poule, décharges sauvages, canaux bouchés — aucune commune ne peut plus ignorer.
  </p>
 
  <div class="hero-actions">
    <a href="#fonctionnement" class="btn-primary">
      <i class="fas fa-play-circle"></i>
      Découvrir la plateforme
    </a>
    <a href="#impact" class="btn-ghost">
      <i class="fas fa-chart-line"></i>
      Voir l'impact réel
    </a>
  </div>
 
  <div class="hero-stats-row">
    <div class="hero-stat">
      <div class="hero-stat-num">1<span>,</span>240<span>+</span></div>
      <div class="hero-stat-label">Signalements enregistrés</div>
    </div>
    <div class="hero-stat">
      <div class="hero-stat-num">12</div>
      <div class="hero-stat-label">Communes couvertes</div>
    </div>
    <div class="hero-stat">
      <div class="hero-stat-num">47<span>%</span></div>
      <div class="hero-stat-label">Taux de résolution</div>
    </div>
    <div class="hero-stat">
      <div class="hero-stat-num">0</div>
      <div class="hero-stat-label">Signalement supprimé</div>
    </div>
  </div>
</section>
 
<!-- MARQUEE -->
<div class="marquee-band">
  <div class="marquee-inner">
    <div class="marquee-item"><div class="marquee-dot"></div>Transparence totale</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Immuabilité blockchain</div>
    <div class="marquee-item"><div class="marquee-dot"></div>12 communes d'Abidjan</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Données publiques</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Signalements géolocalisés</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Responsabilité municipale</div>
    <!-- Duplicate for seamless loop -->
    <div class="marquee-item"><div class="marquee-dot"></div>Transparence totale</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Immuabilité blockchain</div>
    <div class="marquee-item"><div class="marquee-dot"></div>12 communes d'Abidjan</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Données publiques</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Signalements géolocalisés</div>
    <div class="marquee-item"><div class="marquee-dot"></div>Responsabilité municipale</div>
  </div>
</div>
 
<!-- PROBLEMES -->
<section id="problemes">
  <div class="prob-header">
    <div>
      <div class="section-label reveal">Problèmes documentés</div>
      <h2 class="section-title reveal reveal-delay-1">Des dysfonctionnements<br>trop longtemps ignorés</h2>
    </div>
    <p class="section-sub reveal reveal-delay-2">
      SentinelleCI documente et rend public chaque défaillance des infrastructures urbaines ivoiriennes.
    </p>
  </div>
 
  <div class="prob-grid">
    <div class="prob-card reveal">
      <div class="prob-icon prob-icon-road"><i class="fas fa-road"></i></div>
      <h3>Nids-de-poule critiques — Yopougon</h3>
      <p>Carrefour Sicogi : 3 mois sans réfection, 12 accidents recensés sur cet axe majeur.</p>
      <div class="prob-impact"><i class="fas fa-exclamation-circle"></i> Impact estimé : 45M FCFA de perte économique</div>
    </div>
    <div class="prob-card reveal reveal-delay-1">
      <div class="prob-icon prob-icon-trash"><i class="fas fa-trash-alt"></i></div>
      <h3>Décharge sauvage — Port-Bouët</h3>
      <p>Quartier Vridi Canal : dépotoir à ciel ouvert depuis 8 mois sans intervention.</p>
      <div class="prob-impact"><i class="fas fa-lungs"></i> Impact : +300 cas de maladies respiratoires</div>
    </div>
    <div class="prob-card reveal reveal-delay-2">
      <div class="prob-icon prob-icon-water"><i class="fas fa-water"></i></div>
      <h3>Canal bouché — Treichville</h3>
      <p>Rue des pêcheurs : inondations récurrentes à chaque pluie, école inaccessible.</p>
      <div class="prob-impact"><i class="fas fa-school"></i> Impact : 340 élèves affectés, école fermée</div>
    </div>
    <div class="prob-card reveal reveal-delay-3">
      <div class="prob-icon prob-icon-light"><i class="fas fa-lightbulb"></i></div>
      <h3>Éclairage public — Korhogo</h3>
      <p>Zone commerciale plongée dans le noir depuis 6 mois, insécurité croissante.</p>
      <div class="prob-impact"><i class="fas fa-shield-alt"></i> Impact : baisse d'activité de 40%</div>
    </div>
  </div>
</section>
 
<!-- FONCTIONNEMENT -->
<section id="fonctionnement">
  <div class="section-label reveal">Comment ça marche</div>
  <h2 class="section-title reveal reveal-delay-1">Simple pour le citoyen.<br>Irréfutable pour la commune.</h2>
  <p class="section-sub reveal reveal-delay-2">Quatre étapes pour transformer une plainte en preuve juridique permanente.</p>
 
  <div class="steps-grid">
    <div class="step reveal">
      <div class="step-num">01</div>
      <div class="step-icon"><i class="fas fa-camera"></i></div>
      <h3>Documentez</h3>
      <p>Prenez une photo du problème. La capture devient une preuve visuelle horodatée, jointe au signalement.</p>
    </div>
    <div class="step reveal reveal-delay-1">
      <div class="step-num">02</div>
      <div class="step-icon"><i class="fas fa-map-marker-alt"></i></div>
      <h3>Géolocalisez</h3>
      <p>Cliquez précisément sur la carte interactive pour indiquer l'emplacement exact du problème.</p>
    </div>
    <div class="step reveal reveal-delay-2">
      <div class="step-num">03</div>
      <div class="step-icon"><i class="fas fa-link"></i></div>
      <h3>Enregistrez</h3>
      <p>Le signalement génère un hash cryptographique unique, inscrit en blockchain. Immuable, public, traçable.</p>
    </div>
    <div class="step reveal reveal-delay-3">
      <div class="step-num">04</div>
      <div class="step-icon"><i class="fas fa-eye"></i></div>
      <h3>Suivez</h3>
      <p>Chaque signalement est visible sur la carte publique. La commune est tenue de justifier son inaction.</p>
    </div>
  </div>
</section>
 
<!-- BLOCKCHAIN -->
<section id="blockchain">
  <div class="section-label reveal">Infrastructure</div>
  <h2 class="section-title reveal reveal-delay-1">Aucune donnée ne peut<br>être effacée.</h2>
 
  <div class="blockchain-layout">
    <div class="blockchain-visual reveal">
      <div class="chain-blocks">
        <div class="chain-block">
          <div class="chain-block-info">
            <div class="chain-block-type">🛣️ Voirie — Yopougon</div>
            <div class="chain-block-hash">0x8f3a2b1c9d4e5f6a7b8c9d0e...</div>
          </div>
          <div class="chain-block-badge">✓ Immuable</div>
        </div>
        <div class="chain-connector"></div>
        <div class="chain-block">
          <div class="chain-block-info">
            <div class="chain-block-type">🗑️ Décharge — Port-Bouët</div>
            <div class="chain-block-hash">0x2c9d4e5f6a7b8c9d0e1f2a3b...</div>
          </div>
          <div class="chain-block-badge">✓ Immuable</div>
        </div>
        <div class="chain-connector"></div>
        <div class="chain-block">
          <div class="chain-block-info">
            <div class="chain-block-type">💧 Canal — Treichville</div>
            <div class="chain-block-hash">0x7e6f5a4b3c2d1e0f9a8b7c6d...</div>
          </div>
          <div class="chain-block-badge">✓ Immuable</div>
        </div>
        <div class="chain-connector"></div>
        <div class="chain-block">
          <div class="chain-block-info">
            <div class="chain-block-type">⚡ Éclairage — Plateau</div>
            <div class="chain-block-hash">0x1a2b3c4d5e6f7a8b9c0d1e2f...</div>
          </div>
          <div class="chain-block-badge">✓ Immuable</div>
        </div>
      </div>
    </div>
 
    <div class="blockchain-features">
      <div class="bc-feature reveal">
        <div class="bc-feature-icon"><i class="fas fa-lock"></i></div>
        <div>
          <h4>Immuabilité totale</h4>
          <p>Chaque signalement génère un hash cryptographique unique. Aucune commune, aucun acteur politique ne peut supprimer ou modifier l'enregistrement.</p>
        </div>
      </div>
      <div class="bc-feature reveal reveal-delay-1">
        <div class="bc-feature-icon"><i class="fas fa-gavel"></i></div>
        <div>
          <h4>Preuve juridique recevable</h4>
          <p>L'horodatage blockchain constitue une preuve légale de l'existence et de la durée d'un dysfonctionnement. Utilisable en recours administratif.</p>
        </div>
      </div>
      <div class="bc-feature reveal reveal-delay-2">
        <div class="bc-feature-icon"><i class="fas fa-globe"></i></div>
        <div>
          <h4>Audit public en temps réel</h4>
          <p>Toutes les données sont accessibles sur une carte publique ouverte. Journalistes, ONG, citoyens — tout le monde peut auditer et vérifier.</p>
        </div>
      </div>
      <div class="bc-feature reveal reveal-delay-3">
        <div class="bc-feature-icon"><i class="fas fa-user-secret"></i></div>
        <div>
          <h4>Signalement anonyme possible</h4>
          <p>Les citoyens qui craignent des représailles peuvent signaler de manière anonyme tout en conservant l'intégrité cryptographique du dépôt.</p>
        </div>
      </div>
    </div>
  </div>
</section>
 
<!-- IMPACT -->
<section id="impact">
  <div class="section-label reveal">Chiffres clés</div>
  <h2 class="section-title reveal reveal-delay-1">Un impact mesurable<br>sur les communes</h2>
 
  <div class="impact-grid">
    <div class="impact-card impact-card-main reveal">
      <h3>Transparence citoyenne<br>pour la Côte d'Ivoire</h3>
      <p>SentinelleCI couvre aujourd'hui 12 communes dont Yopougon, Cocody, Treichville, Marcory, Port-Bouët et Plateau. La plateforme s'étend progressivement à Bouaké, Daloa et San-Pédro.</p>
      <div class="impact-communes">
        <span class="commune-tag">Yopougon</span>
        <span class="commune-tag">Cocody</span>
        <span class="commune-tag">Treichville</span>
        <span class="commune-tag">Marcory</span>
        <span class="commune-tag">Plateau</span>
        <span class="commune-tag">Port-Bouët</span>
        <span class="commune-tag">Angré</span>
        <span class="commune-tag">+ 5 autres</span>
      </div>
    </div>
    <div class="impact-card impact-card-dark reveal reveal-delay-1">
      <div class="impact-big-num">47%</div>
      <div class="impact-card-label">Taux de résolution des signalements dans les communes actives</div>
    </div>
    <div class="impact-card impact-card-light reveal reveal-delay-2">
      <div class="impact-big-num">1 240</div>
      <div class="impact-card-label">Signalements enregistrés sur la blockchain — 0 supprimé</div>
    </div>
    <div class="impact-card impact-card-light reveal reveal-delay-1">
      <div class="impact-big-num">8</div>
      <div class="impact-card-label">Mois depuis le lancement public de la plateforme</div>
    </div>
    <div class="impact-card impact-card-dark reveal reveal-delay-2">
      <div class="impact-big-num">12+</div>
      <div class="impact-card-label">Communes couvertes et en expansion vers l'intérieur du pays</div>
    </div>
  </div>
</section>
 
<!-- CTA -->
<section id="cta">
  <div class="section-label">Passez à l'action</div>
  <h2 class="section-title">Votre commune vous doit<br>des comptes.</h2>
  <p class="section-sub">Signalez un problème en 3 minutes. Créez une preuve permanente que personne ne peut effacer.</p>
  <div class="hero-actions">
    <a href="#" class="btn-primary">
      <i class="fas fa-plus-circle"></i>
      Faire un signalement
    </a>
    <a href="#" class="btn-ghost">
      <i class="fas fa-map-marked-alt"></i>
      Voir la carte publique
    </a>
  </div>
</section>
 
<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div>
      <div class="footer-logo">SENTINELLE<span>CI</span></div>
      <p class="footer-tagline">Transparence totale. Responsabilisation des communes ivoiriennes grâce à la blockchain.</p>
    </div>
 
    <div class="footer-links-group">
      <h4>Plateforme</h4>
      <a href="#problemes">Problèmes documentés</a>
      <a href="#fonctionnement">Comment ça marche</a>
      <a href="#blockchain">Technologie blockchain</a>
      <a href="#impact">Impact & chiffres</a>
    </div>
 
    <div class="footer-links-group">
      <h4>Contact</h4>
      <a href="mailto:contact@sentinelleci.ci">contact@sentinelleci.ci</a>
      <a href="tel:+22507591234">+225 07 59 12 34 56</a>
      <a href="#">Presse & médias</a>
      <a href="#">Partenariats ONG</a>
    </div>
  </div>
 
  <div class="footer-bottom">
    <p>© 2026 SentinelleCI — Initiative citoyenne, Côte d'Ivoire</p>
    <div class="footer-badge">
      <div class="footer-badge-dot"></div>
      Plateforme active · Blockchain opérationnelle
    </div>
  </div>
</footer>
 
<script>
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });
  reveals.forEach(el => observer.observe(el));
 
  // Navbar scroll style
  window.addEventListener('scroll', () => {
    const nav = document.querySelector('nav');
    if (window.scrollY > 60) {
      nav.style.boxShadow = '0 4px 32px rgba(10,46,28,0.08)';
    } else {
      nav.style.boxShadow = 'none';
    }
  });
 
  // Counter animation
  function animateCounter(el, target, suffix = '') {
    let current = 0;
    const step = target / 60;
    const timer = setInterval(() => {
      current += step;
      if (current >= target) {
        current = target;
        clearInterval(timer);
      }
      el.textContent = Math.floor(current).toLocaleString('fr-FR') + suffix;
    }, 20);
  }
 
  // Smooth scroll for nav links
  document.querySelectorAll('a[href^="#"]').forEach(link => {
    link.addEventListener('click', e => {
      const href = link.getAttribute('href');
      if (href === '#') return;
      const target = document.querySelector(href);
      if (target) {
        e.preventDefault();
        target.scrollIntoView({ behavior: 'smooth' });
      }
    });
  });
</script>
</body>
</html>
 
