<!-- 
  Mitu & Dilip Wedding RSVP Site
  
  HOW TO EDIT:
  • Names, dates, venue, parents → search for [EDIT] in this file
  • Host passcode for RSVP dashboard → const HOST_PASSCODE below (default: "mitudilip2026")
  • To view all RSVPs → scroll to footer, click the small gold dot, enter passcode
  • Or visit the URL with #host at the end
-->
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Mitu & Dilip · 16-17 July 2026</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300..900;1,9..144,300..900&family=Manrope:wght@300;400;500;600;700&family=Tiro+Devanagari+Hindi:ital@0;1&display=swap" rel="stylesheet">

<style>
  :root {
    --cream:       #F5EDDF;
    --cream-deep:  #EBE2CE;
    --cream-soft:  #FAF5EA;
    --ink:         #2B1814;
    --ink-soft:    #5A4A42;
    --burgundy:    #6B1F2E;
    --burgundy-dp: #4F1422;
    --marigold:    #D89A3F;
    --gold:        #B8893C;
    --gold-soft:   #DBBC7A;
    --blush:       #E8B4B8;

    --serif:  "Fraunces", "Cormorant Garamond", Georgia, serif;
    --sans:   "Manrope", -apple-system, BlinkMacSystemFont, sans-serif;
    --hindi:  "Tiro Devanagari Hindi", "Fraunces", serif;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--cream);
    color: var(--ink);
    font-family: var(--sans);
    font-weight: 400;
    line-height: 1.6;
    overflow-x: hidden;
    -webkit-font-smoothing: antialiased;
  }

  ::selection { background: var(--burgundy); color: var(--cream); }

  /* ============ HEADER NAV ============ */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 18px 32px;
    display: flex; justify-content: space-between; align-items: center;
    background: rgba(245, 237, 223, 0);
    transition: background 0.4s, padding 0.4s, box-shadow 0.4s;
    backdrop-filter: blur(0px);
  }
  nav.scrolled {
    background: rgba(245, 237, 223, 0.92);
    backdrop-filter: blur(14px);
    padding: 12px 32px;
    box-shadow: 0 1px 0 rgba(43,24,20,0.06);
  }
  .nav-mark {
    font-family: var(--serif);
    font-style: italic;
    font-size: 22px;
    color: var(--burgundy);
    letter-spacing: 0.02em;
  }
  .nav-links { display: flex; gap: 28px; }
  .nav-links a {
    color: var(--ink);
    text-decoration: none;
    font-size: 12px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    font-weight: 500;
    position: relative;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--burgundy); }
  .nav-links a::after {
    content: "";
    position: absolute; bottom: -4px; left: 0;
    width: 0; height: 1px; background: var(--burgundy);
    transition: width 0.3s;
  }
  .nav-links a:hover::after { width: 100%; }

  @media (max-width: 700px) {
    .nav-links { display: none; }
    nav { padding: 14px 20px; }
  }

  /* ============ HERO ============ */
  .hero {
    min-height: 100vh;
    padding: 120px 40px 60px;
    display: flex; flex-direction: column;
    justify-content: center; align-items: center;
    position: relative;
    text-align: center;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 20% 20%, rgba(216,154,63,0.10), transparent 50%),
      radial-gradient(ellipse at 80% 80%, rgba(107,31,46,0.08), transparent 50%);
    z-index: 0;
  }

  .hero > * { position: relative; z-index: 1; }

  .hero-blessing {
    font-family: var(--hindi);
    color: var(--burgundy);
    font-size: 18px;
    letter-spacing: 0.08em;
    margin-bottom: 8px;
    opacity: 0; transform: translateY(20px);
    animation: rise 1s 0.2s forwards;
  }
  .hero-blessing-en {
    font-family: var(--serif);
    font-style: italic;
    font-size: 13px;
    color: var(--ink-soft);
    letter-spacing: 0.25em;
    text-transform: uppercase;
    margin-bottom: 60px;
    opacity: 0; transform: translateY(20px);
    animation: rise 1s 0.35s forwards;
  }

  .hero-eyebrow {
    font-family: var(--serif);
    font-style: italic;
    font-size: 15px;
    color: var(--ink-soft);
    letter-spacing: 0.12em;
    margin-bottom: 24px;
    opacity: 0; transform: translateY(20px);
    animation: rise 1s 0.5s forwards;
  }
  .hero-eyebrow .ornament {
    color: var(--marigold);
    margin: 0 14px;
    font-size: 18px;
    vertical-align: middle;
  }

  .hero-names {
    font-family: var(--serif);
    font-size: clamp(60px, 13vw, 168px);
    font-weight: 300;
    line-height: 0.92;
    color: var(--ink);
    letter-spacing: -0.02em;
    margin-bottom: 30px;
    opacity: 0; transform: translateY(30px);
    animation: rise 1.4s 0.7s forwards;
  }
  .hero-names .amp {
    font-family: var(--serif);
    font-style: italic;
    font-weight: 300;
    color: var(--burgundy);
    font-size: 0.7em;
    vertical-align: 0.05em;
    padding: 0 0.05em;
    display: inline-block;
    transform: rotate(-2deg);
  }

  .hero-tag {
    font-family: var(--serif);
    font-style: italic;
    font-size: clamp(16px, 2vw, 22px);
    color: var(--burgundy);
    letter-spacing: 0.04em;
    margin-bottom: 48px;
    opacity: 0; transform: translateY(20px);
    animation: rise 1s 1.1s forwards;
  }

  .hero-meta {
    display: flex; align-items: center; gap: 28px;
    font-family: var(--sans);
    font-size: 13px;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--ink);
    font-weight: 500;
    opacity: 0; transform: translateY(20px);
    animation: rise 1s 1.3s forwards;
  }
  .hero-meta .divider {
    width: 40px; height: 1px; background: var(--gold);
  }

  .hero-venue {
    margin-top: 16px;
    font-family: var(--serif);
    font-style: italic;
    color: var(--ink-soft);
    font-size: 16px;
    letter-spacing: 0.04em;
    opacity: 0; transform: translateY(20px);
    animation: rise 1s 1.5s forwards;
  }

  .hero-scroll {
    position: absolute; bottom: 32px; left: 50%;
    transform: translateX(-50%);
    font-size: 11px; letter-spacing: 0.3em;
    color: var(--ink-soft);
    opacity: 0;
    animation: rise 1s 2s forwards;
    text-transform: uppercase;
  }
  .hero-scroll::after {
    content: ""; display: block;
    width: 1px; height: 32px; background: var(--ink-soft);
    margin: 10px auto 0;
    animation: scrollPulse 2s infinite;
  }

  @keyframes rise {
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes scrollPulse {
    0%, 100% { transform: scaleY(1); opacity: 0.5; }
    50% { transform: scaleY(0.4); opacity: 1; }
  }

  @media (max-width: 600px) {
    .hero-meta { flex-direction: column; gap: 14px; }
    .hero-meta .divider { width: 60px; }
  }

  /* ============ SECTION SCAFFOLD ============ */
  section {
    padding: 110px 40px;
    max-width: 1200px;
    margin: 0 auto;
    position: relative;
  }
  @media (max-width: 700px) {
    section { padding: 80px 24px; }
  }

  .eyebrow {
    font-family: var(--sans);
    font-size: 11px;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 600;
    margin-bottom: 18px;
    display: inline-flex; align-items: center; gap: 12px;
  }
  .eyebrow::before {
    content: ""; display: inline-block;
    width: 28px; height: 1px; background: var(--gold);
  }

  .section-title {
    font-family: var(--serif);
    font-weight: 300;
    font-size: clamp(38px, 5vw, 64px);
    line-height: 1.05;
    color: var(--ink);
    letter-spacing: -0.01em;
    margin-bottom: 28px;
  }
  .section-title em {
    font-style: italic;
    color: var(--burgundy);
  }

  .lede {
    font-family: var(--serif);
    font-size: clamp(18px, 1.8vw, 22px);
    line-height: 1.65;
    color: var(--ink-soft);
    max-width: 620px;
    font-weight: 300;
  }

  .divider-ornament {
    display: flex; align-items: center; justify-content: center;
    gap: 16px; margin: 0 auto;
    color: var(--marigold);
  }
  .divider-ornament .line {
    width: 60px; height: 1px; background: var(--gold);
  }
  .divider-ornament svg { width: 24px; height: 24px; }

  /* ============ COUNTDOWN ============ */
  .countdown-section {
    background: var(--cream-deep);
    max-width: none;
    padding: 70px 40px;
    margin: 0;
    text-align: center;
  }
  .countdown-label {
    font-family: var(--serif);
    font-style: italic;
    color: var(--ink-soft);
    font-size: 16px;
    letter-spacing: 0.05em;
    margin-bottom: 28px;
  }
  .countdown {
    display: flex; justify-content: center; gap: clamp(20px, 6vw, 60px);
    flex-wrap: wrap;
  }
  .countdown-unit { text-align: center; }
  .countdown-num {
    font-family: var(--serif);
    font-size: clamp(48px, 8vw, 88px);
    font-weight: 300;
    line-height: 1;
    color: var(--burgundy);
    letter-spacing: -0.02em;
  }
  .countdown-label-unit {
    font-family: var(--sans);
    font-size: 11px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--ink-soft);
    margin-top: 8px;
    font-weight: 500;
  }

  /* ============ STORY ============ */
  .story {
    display: grid;
    grid-template-columns: 1fr 1.2fr;
    gap: 80px;
    align-items: center;
  }
  @media (max-width: 850px) {
    .story { grid-template-columns: 1fr; gap: 40px; }
  }

  .story-visual {
    aspect-ratio: 4/5;
    background: var(--burgundy);
    position: relative;
    overflow: hidden;
    border-radius: 4px;
  }
  .story-visual .pincode-art {
    position: absolute; inset: 0;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    color: var(--cream);
    padding: 40px;
    text-align: center;
  }
  .story-visual .pincode-art .pin-label {
    font-family: var(--sans);
    font-size: 11px;
    letter-spacing: 0.4em;
    text-transform: uppercase;
    color: var(--gold-soft);
    margin-bottom: 16px;
  }
  .story-visual .pincode-art .pin-number {
    font-family: var(--serif);
    font-size: clamp(60px, 10vw, 110px);
    font-weight: 300;
    line-height: 1;
    letter-spacing: 0.04em;
    color: var(--cream);
    margin-bottom: 18px;
  }
  .story-visual .pincode-art .pin-tag {
    font-family: var(--serif);
    font-style: italic;
    font-size: 18px;
    color: var(--gold-soft);
    letter-spacing: 0.04em;
  }
  .story-visual .pincode-art .pin-divider {
    width: 50px; height: 1px;
    background: var(--gold);
    margin: 14px 0;
  }
  .story-visual::before {
    content: "";
    position: absolute; inset: 14px;
    border: 1px solid rgba(216,188,122,0.35);
    pointer-events: none;
  }

  .story-text p {
    font-family: var(--serif);
    font-size: clamp(17px, 1.6vw, 20px);
    line-height: 1.75;
    color: var(--ink);
    margin-bottom: 22px;
    font-weight: 300;
  }
  .story-text p em {
    font-style: italic;
    color: var(--burgundy);
  }
  .story-text .signature {
    font-family: var(--serif);
    font-style: italic;
    color: var(--marigold);
    font-size: 22px;
    margin-top: 30px;
    display: block;
  }

  /* ============ FAMILIES ============ */
  .families-section {
    background: var(--cream-soft);
    max-width: none;
    margin: 0; padding: 100px 40px;
  }
  .families-inner { max-width: 1200px; margin: 0 auto; text-align: center; }

  .families-grid {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 60px;
    align-items: center;
    margin-top: 50px;
  }
  @media (max-width: 800px) {
    .families-grid { grid-template-columns: 1fr; gap: 30px; }
    .families-grid .joining { transform: rotate(90deg); }
  }

  .family-block { text-align: center; }
  .family-block .role {
    font-family: var(--sans);
    font-size: 11px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 600;
    margin-bottom: 16px;
  }
  .family-block .first-name {
    font-family: var(--serif);
    font-size: clamp(36px, 5vw, 56px);
    font-weight: 300;
    color: var(--burgundy);
    font-style: italic;
    line-height: 1;
    margin-bottom: 18px;
    letter-spacing: -0.01em;
  }
  .family-block .parents {
    font-family: var(--serif);
    font-size: 15px;
    color: var(--ink-soft);
    line-height: 1.6;
    font-style: italic;
  }
  .family-block .parents strong {
    color: var(--ink);
    font-weight: 500;
    font-style: normal;
  }
  .family-block .parents-label {
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--ink-soft);
    font-style: normal;
    display: block;
    margin-bottom: 6px;
  }

  .joining svg { width: 50px; height: 50px; color: var(--marigold); }

  /* ============ EVENTS ============ */
  .events-intro { text-align: center; margin-bottom: 70px; }
  .events-intro .lede { margin: 0 auto; }

  .day-card {
    background: var(--cream-soft);
    border: 1px solid rgba(184,137,60,0.2);
    border-radius: 6px;
    padding: 50px;
    margin-bottom: 30px;
    position: relative;
  }
  @media (max-width: 700px) {
    .day-card { padding: 32px 22px; }
  }

  .day-header {
    display: flex;
    align-items: baseline;
    gap: 24px;
    margin-bottom: 40px;
    padding-bottom: 30px;
    border-bottom: 1px solid rgba(184,137,60,0.3);
  }
  @media (max-width: 600px) {
    .day-header { flex-direction: column; gap: 8px; align-items: flex-start; }
  }
  .day-number {
    font-family: var(--serif);
    font-style: italic;
    font-size: 14px;
    color: var(--gold);
    letter-spacing: 0.2em;
    text-transform: uppercase;
  }
  .day-date {
    font-family: var(--serif);
    font-size: clamp(28px, 3.5vw, 40px);
    font-weight: 300;
    color: var(--burgundy);
    letter-spacing: -0.01em;
    line-height: 1;
  }
  .day-date .day-name {
    font-style: italic;
    color: var(--ink-soft);
    font-size: 0.55em;
    display: block;
    margin-top: 6px;
    letter-spacing: 0.1em;
  }

  .events-list {
    display: grid;
    gap: 4px;
  }

  .event-row {
    display: grid;
    grid-template-columns: 110px 1fr auto;
    gap: 24px;
    align-items: baseline;
    padding: 22px 0;
    border-bottom: 1px dashed rgba(43,24,20,0.12);
    transition: background 0.3s, padding-left 0.3s;
  }
  .event-row:hover {
    background: rgba(216,154,63,0.05);
    padding-left: 16px;
  }
  .event-row:last-child { border-bottom: none; }

  @media (max-width: 600px) {
    .event-row {
      grid-template-columns: 80px 1fr;
      gap: 14px;
    }
    .event-row .event-icon { display: none; }
  }

  .event-time {
    font-family: var(--serif);
    font-style: italic;
    color: var(--burgundy);
    font-size: 17px;
    font-weight: 400;
  }
  .event-name {
    font-family: var(--serif);
    font-size: 22px;
    color: var(--ink);
    font-weight: 400;
    letter-spacing: -0.01em;
  }
  .event-name .secondary {
    display: block;
    font-size: 14px;
    color: var(--ink-soft);
    font-style: italic;
    margin-top: 3px;
    letter-spacing: 0.02em;
  }
  .event-icon {
    color: var(--marigold);
    opacity: 0.7;
  }
  .event-icon svg { width: 22px; height: 22px; }

  /* ============ VENUE ============ */
  .venue-section { text-align: center; }
  .venue-card {
    background: var(--burgundy);
    color: var(--cream);
    padding: 60px 40px;
    border-radius: 6px;
    margin-top: 40px;
    max-width: 700px;
    margin-left: auto; margin-right: auto;
    position: relative;
    overflow: hidden;
  }
  .venue-card::before {
    content: "";
    position: absolute; inset: 14px;
    border: 1px solid rgba(216,188,122,0.3);
    pointer-events: none;
  }
  .venue-card .eyebrow { color: var(--gold-soft); }
  .venue-card .eyebrow::before { background: var(--gold-soft); }
  .venue-name {
    font-family: var(--serif);
    font-size: clamp(36px, 5vw, 52px);
    font-weight: 300;
    color: var(--cream);
    letter-spacing: -0.01em;
    margin: 14px 0 8px;
    font-style: italic;
  }
  .venue-city {
    font-family: var(--sans);
    font-size: 13px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold-soft);
    margin-bottom: 30px;
  }
  .venue-link {
    display: inline-flex; align-items: center; gap: 10px;
    color: var(--cream);
    text-decoration: none;
    border: 1px solid var(--gold-soft);
    padding: 14px 28px;
    border-radius: 999px;
    font-family: var(--sans);
    font-size: 12px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    font-weight: 500;
    transition: background 0.3s, color 0.3s;
  }
  .venue-link:hover {
    background: var(--gold-soft);
    color: var(--burgundy-dp);
  }

  /* ============ RSVP ============ */
  .rsvp-section {
    background: var(--cream-deep);
    max-width: none;
    margin: 0; padding: 110px 40px;
  }
  .rsvp-inner { max-width: 760px; margin: 0 auto; }
  .rsvp-intro { text-align: center; margin-bottom: 50px; }
  .rsvp-intro .lede { margin: 0 auto; }

  .rsvp-form {
    background: var(--cream-soft);
    padding: 50px;
    border-radius: 6px;
    border: 1px solid rgba(184,137,60,0.25);
  }
  @media (max-width: 700px) {
    .rsvp-form { padding: 32px 22px; }
  }

  .field-group {
    margin-bottom: 28px;
  }
  .field-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 28px;
  }
  @media (max-width: 600px) {
    .field-row { grid-template-columns: 1fr; }
  }

  label {
    display: block;
    font-family: var(--sans);
    font-size: 11px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--burgundy);
    font-weight: 600;
    margin-bottom: 10px;
  }
  label .req { color: var(--marigold); margin-left: 4px; }

  input[type="text"],
  input[type="tel"],
  input[type="number"],
  select,
  textarea {
    width: 100%;
    padding: 14px 16px;
    background: transparent;
    border: none;
    border-bottom: 1px solid rgba(43,24,20,0.25);
    font-family: var(--serif);
    font-size: 17px;
    color: var(--ink);
    transition: border-color 0.2s, background 0.2s;
    border-radius: 0;
  }
  textarea {
    border: 1px solid rgba(43,24,20,0.25);
    border-radius: 4px;
    resize: vertical;
    min-height: 90px;
    background: rgba(255,255,255,0.5);
  }
  select {
    appearance: none;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%236B1F2E' stroke-width='1.5' fill='none'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 10px center;
    padding-right: 38px;
  }
  input:focus, select:focus, textarea:focus {
    outline: none;
    border-color: var(--burgundy);
    background: rgba(255,255,255,0.6);
  }
  input::placeholder, textarea::placeholder { color: rgba(43,24,20,0.35); }

  .radio-group, .checkbox-group {
    display: flex; flex-wrap: wrap; gap: 12px;
  }
  .radio-pill, .check-pill {
    position: relative;
    cursor: pointer;
    user-select: none;
  }
  .radio-pill input, .check-pill input {
    position: absolute; opacity: 0; pointer-events: none;
  }
  .radio-pill span, .check-pill span {
    display: inline-block;
    padding: 10px 18px;
    border: 1px solid rgba(43,24,20,0.25);
    border-radius: 999px;
    font-family: var(--sans);
    font-size: 13px;
    color: var(--ink);
    transition: all 0.2s;
    background: rgba(255,255,255,0.5);
  }
  .radio-pill:hover span, .check-pill:hover span {
    border-color: var(--burgundy);
  }
  .radio-pill input:checked + span,
  .check-pill input:checked + span {
    background: var(--burgundy);
    color: var(--cream);
    border-color: var(--burgundy);
  }

  .event-checks {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 10px;
  }
  .event-check {
    cursor: pointer;
    position: relative;
  }
  .event-check input {
    position: absolute; opacity: 0; pointer-events: none;
  }
  .event-check .check-content {
    border: 1px solid rgba(43,24,20,0.2);
    border-radius: 4px;
    padding: 14px;
    background: rgba(255,255,255,0.5);
    transition: all 0.2s;
    display: flex; align-items: center; gap: 12px;
  }
  .event-check .check-content::before {
    content: "";
    width: 16px; height: 16px;
    border: 1.5px solid rgba(107,31,46,0.4);
    border-radius: 3px;
    flex-shrink: 0;
    transition: all 0.2s;
  }
  .event-check:hover .check-content {
    border-color: var(--burgundy);
  }
  .event-check input:checked + .check-content {
    background: rgba(107,31,46,0.05);
    border-color: var(--burgundy);
  }
  .event-check input:checked + .check-content::before {
    background: var(--burgundy);
    border-color: var(--burgundy);
    box-shadow: inset 0 0 0 3px var(--cream-soft);
  }
  .event-check .ec-name {
    font-family: var(--serif);
    font-size: 15px;
    color: var(--ink);
    display: block;
    line-height: 1.2;
  }
  .event-check .ec-date {
    font-family: var(--sans);
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--ink-soft);
    margin-top: 3px;
    display: block;
  }

  .submit-btn {
    margin-top: 32px;
    width: 100%;
    padding: 18px 28px;
    background: var(--burgundy);
    color: var(--cream);
    border: none;
    border-radius: 999px;
    font-family: var(--sans);
    font-size: 13px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s, transform 0.1s;
    position: relative;
  }
  .submit-btn:hover { background: var(--burgundy-dp); }
  .submit-btn:active { transform: translateY(1px); }
  .submit-btn:disabled { opacity: 0.6; cursor: not-allowed; }

  .form-message {
    margin-top: 18px;
    padding: 14px 18px;
    border-radius: 4px;
    font-family: var(--serif);
    font-size: 15px;
    text-align: center;
    display: none;
  }
  .form-message.success {
    background: rgba(107,31,46,0.08);
    color: var(--burgundy);
    border: 1px solid rgba(107,31,46,0.2);
    display: block;
    font-style: italic;
  }
  .form-message.error {
    background: rgba(216,154,63,0.1);
    color: var(--ink);
    border: 1px solid var(--marigold);
    display: block;
  }

  /* RSVP confirmation state */
  .rsvp-confirmation {
    text-align: center;
    padding: 60px 40px;
  }
  .rsvp-confirmation .check-circle {
    width: 70px; height: 70px;
    border: 2px solid var(--marigold);
    border-radius: 50%;
    display: inline-flex; align-items: center; justify-content: center;
    color: var(--marigold);
    margin-bottom: 24px;
  }
  .rsvp-confirmation h3 {
    font-family: var(--serif);
    font-size: 38px;
    font-weight: 300;
    color: var(--burgundy);
    font-style: italic;
    margin-bottom: 12px;
  }
  .rsvp-confirmation p {
    font-family: var(--serif);
    font-size: 18px;
    color: var(--ink-soft);
    margin-bottom: 24px;
  }
  .rsvp-edit-btn {
    background: none;
    border: 1px solid var(--burgundy);
    color: var(--burgundy);
    padding: 12px 24px;
    border-radius: 999px;
    font-family: var(--sans);
    font-size: 11px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    cursor: pointer;
    font-weight: 500;
    transition: all 0.2s;
  }
  .rsvp-edit-btn:hover {
    background: var(--burgundy);
    color: var(--cream);
  }

  /* ============ FOOTER ============ */
  footer {
    padding: 80px 40px 50px;
    text-align: center;
    background: var(--ink);
    color: var(--cream);
    position: relative;
  }
  .footer-monogram {
    font-family: var(--serif);
    font-style: italic;
    font-size: 56px;
    font-weight: 300;
    color: var(--marigold);
    margin-bottom: 18px;
    letter-spacing: -0.02em;
  }
  .footer-blessing {
    font-family: var(--hindi);
    color: var(--gold-soft);
    font-size: 16px;
    margin-bottom: 10px;
    letter-spacing: 0.04em;
  }
  .footer-line {
    font-family: var(--serif);
    font-style: italic;
    color: rgba(245,237,223,0.7);
    font-size: 14px;
    letter-spacing: 0.04em;
  }
  .host-dot {
    position: absolute;
    bottom: 18px; right: 22px;
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--gold);
    opacity: 0.3;
    cursor: pointer;
    transition: opacity 0.3s, transform 0.3s;
  }
  .host-dot:hover { opacity: 1; transform: scale(1.4); }

  /* ============ HOST DASHBOARD ============ */
  .host-overlay {
    position: fixed; inset: 0;
    background: rgba(43,24,20,0.85);
    backdrop-filter: blur(8px);
    z-index: 200;
    display: none;
    align-items: center;
    justify-content: center;
    padding: 20px;
  }
  .host-overlay.active { display: flex; }
  .host-modal {
    background: var(--cream);
    border-radius: 8px;
    width: 100%;
    max-width: 1100px;
    max-height: 90vh;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    box-shadow: 0 30px 80px rgba(0,0,0,0.4);
  }
  .host-header {
    padding: 24px 32px;
    border-bottom: 1px solid rgba(184,137,60,0.25);
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 14px;
  }
  .host-title {
    font-family: var(--serif);
    font-size: 26px;
    color: var(--burgundy);
    font-style: italic;
    font-weight: 300;
  }
  .host-actions { display: flex; gap: 10px; }
  .host-btn {
    padding: 10px 18px;
    border-radius: 999px;
    font-family: var(--sans);
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    border: 1px solid var(--burgundy);
    background: transparent;
    color: var(--burgundy);
  }
  .host-btn.primary { background: var(--burgundy); color: var(--cream); }
  .host-btn:hover { background: var(--burgundy-dp); color: var(--cream); border-color: var(--burgundy-dp); }
  .host-body {
    flex: 1;
    overflow: auto;
    padding: 24px 32px 32px;
  }

  .host-passcode-prompt {
    text-align: center;
    padding: 50px 30px;
  }
  .host-passcode-prompt h2 {
    font-family: var(--serif);
    font-size: 28px;
    font-style: italic;
    color: var(--burgundy);
    font-weight: 300;
    margin-bottom: 14px;
  }
  .host-passcode-prompt p {
    color: var(--ink-soft);
    margin-bottom: 24px;
    font-family: var(--serif);
  }
  .host-passcode-prompt input {
    text-align: center;
    letter-spacing: 0.2em;
    font-family: var(--sans) !important;
    font-size: 15px !important;
    max-width: 280px;
    margin: 0 auto;
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 14px;
    margin-bottom: 28px;
  }
  .stat-card {
    background: var(--cream-soft);
    padding: 18px 20px;
    border-radius: 6px;
    border: 1px solid rgba(184,137,60,0.2);
  }
  .stat-card .num {
    font-family: var(--serif);
    font-size: 36px;
    font-weight: 300;
    color: var(--burgundy);
    line-height: 1;
  }
  .stat-card .lbl {
    font-family: var(--sans);
    font-size: 10px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--ink-soft);
    margin-top: 6px;
    font-weight: 500;
  }

  .rsvp-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  .rsvp-table th {
    text-align: left;
    padding: 12px 10px;
    background: var(--cream-soft);
    font-family: var(--sans);
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--burgundy);
    font-weight: 600;
    border-bottom: 2px solid rgba(184,137,60,0.25);
    position: sticky; top: 0;
  }
  .rsvp-table td {
    padding: 14px 10px;
    border-bottom: 1px dashed rgba(43,24,20,0.12);
    font-family: var(--sans);
    color: var(--ink);
    vertical-align: top;
  }
  .rsvp-table tr:hover td { background: rgba(216,154,63,0.05); }
  .rsvp-table .nm { font-family: var(--serif); font-size: 15px; font-weight: 500; }
  .rsvp-table .ev-pills { display: flex; flex-wrap: wrap; gap: 4px; }
  .rsvp-table .ev-pill {
    background: rgba(107,31,46,0.08);
    color: var(--burgundy);
    padding: 2px 8px;
    border-radius: 999px;
    font-size: 10px;
    letter-spacing: 0.05em;
  }
  .rsvp-table .msg-cell {
    max-width: 220px;
    font-family: var(--serif);
    font-style: italic;
    color: var(--ink-soft);
    font-size: 13px;
  }
  .empty-state {
    text-align: center;
    padding: 60px 30px;
    color: var(--ink-soft);
    font-family: var(--serif);
    font-style: italic;
    font-size: 18px;
  }

  /* Reveal on scroll */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.9s ease, transform 0.9s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }
</style>

<body>

<!-- NAV -->
<nav id="nav">
  <div class="nav-mark">M &amp; D</div>
  <div class="nav-links">
    <a href="#story">Story</a>
    <a href="#events">Events</a>
    <a href="#venue">Venue</a>
    <a href="#rsvp">RSVP</a>
  </div>
</nav>

<!-- HERO -->
<header class="hero">
  <div class="hero-bg"></div>

  <!-- [EDIT] Hindi blessing — Jain tradition -->
  <div class="hero-blessing">|| श्री महावीराय नमः ||</div>
  <div class="hero-blessing-en">Jai Jinendra</div>

  <div class="hero-eyebrow">
    Together with our families
    <span class="ornament">✦</span>
    we joyfully invite you
  </div>

  <!-- [EDIT] Bride & groom names -->
  <h1 class="hero-names">
    Mitu <span class="amp">&amp;</span> Dilip
  </h1>

  <div class="hero-tag">— same pincode, same forever —</div>

  <div class="hero-meta">
    <span>16 · 17 July</span>
    <span class="divider"></span>
    <span>2026</span>
  </div>

  <!-- [EDIT] Venue -->
  <div class="hero-venue">at Agra Exotica, Surat</div>

  <div class="hero-scroll">scroll</div>
</header>

<!-- COUNTDOWN -->
<div class="countdown-section reveal">
  <div class="countdown-label">— counting the days until forever —</div>
  <div class="countdown" id="countdown">
    <div class="countdown-unit"><div class="countdown-num" id="cd-days">—</div><div class="countdown-label-unit">Days</div></div>
    <div class="countdown-unit"><div class="countdown-num" id="cd-hours">—</div><div class="countdown-label-unit">Hours</div></div>
    <div class="countdown-unit"><div class="countdown-num" id="cd-mins">—</div><div class="countdown-label-unit">Minutes</div></div>
    <div class="countdown-unit"><div class="countdown-num" id="cd-secs">—</div><div class="countdown-label-unit">Seconds</div></div>
  </div>
</div>

<!-- STORY -->
<section id="story">
  <div class="story">
    <div class="story-visual reveal">
      <div class="pincode-art">
        <div class="pin-label">Pin · Code</div>
        <div class="pin-divider"></div>
        <div class="pin-number">SAME</div>
        <div class="pin-divider"></div>
        <div class="pin-tag">two homes · one address ahead</div>
      </div>
    </div>

    <div class="story-text reveal">
      <div class="eyebrow">Our Story</div>
      <h2 class="section-title">The shortest love story <em>we know.</em></h2>

      <p>They say love is meant to travel — across cities, across countries, across the long miles between two strangers.</p>

      <p><em>Ours travelled across the lane.</em></p>

      <p>Same pincode. Same streets. Same chaiwala. Different doorbells, different families, different stories — until somewhere between the temple bell and the everyday hello, the two stories quietly became one.</p>

      <p>The pincode stays. The address changes. And what was once <em>her side of the road</em> is, finally, simply, ours.</p>

      <span class="signature">— Mitu &amp; Dilip</span>
    </div>
  </div>
</section>

<!-- FAMILIES -->
<div class="families-section">
  <div class="families-inner reveal">
    <div class="eyebrow" style="justify-content:center;">With Blessings From</div>
    <h2 class="section-title">Our <em>families</em></h2>

    <div class="families-grid">
      <!-- [EDIT] Bride's family -->
      <div class="family-block">
        <div class="role">The Bride</div>
        <div class="first-name">Mitu</div>
        <div class="parents">
          <span class="parents-label">Daughter of</span>
          <strong>Manoj Jain</strong> &amp; <strong>Mamta Jain</strong>
        </div>
      </div>

      <div class="joining">
        <svg viewBox="0 0 50 50" fill="none" stroke="currentColor" stroke-width="1">
          <circle cx="25" cy="25" r="18"/>
          <circle cx="25" cy="25" r="12"/>
          <text x="25" y="32" text-anchor="middle" font-family="Fraunces, serif" font-size="22" font-style="italic" fill="currentColor" stroke="none">&amp;</text>
        </svg>
      </div>

      <!-- [EDIT] Groom's family — update names here -->
      <div class="family-block">
        <div class="role">The Groom</div>
        <div class="first-name">Dilip</div>
        <div class="parents">
          <span class="parents-label">Son of</span>
          <strong>[Father's Name]</strong> &amp; <strong>[Mother's Name]</strong>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- EVENTS -->
<section id="events">
  <div class="events-intro reveal">
    <div class="eyebrow" style="justify-content:center;">Festivities</div>
    <h2 class="section-title">Two days of <em>celebration.</em></h2>
    <p class="lede">Seven sacred rituals. Countless laughs. A pinch of haldi and a lifetime of memories — we'd love for you to be part of every moment.</p>
  </div>

  <div class="day-card reveal">
    <div class="day-header">
      <div class="day-number">Day One</div>
      <div class="day-date">
        16<sup style="font-size:0.5em;">th</sup> July, 2026
        <span class="day-name">Thursday</span>
      </div>
    </div>
    <div class="events-list">

      <div class="event-row">
        <div class="event-time">9:00 AM</div>
        <div class="event-name">Pila Chawal<span class="secondary">The day begins with golden grains &amp; blessings</span></div>
        <div class="event-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><circle cx="12" cy="12" r="9"/><path d="M12 3v18M3 12h18"/></svg>
        </div>
      </div>

      <div class="event-row">
        <div class="event-time">11:00 AM</div>
        <div class="event-name">Haldi<span class="secondary">Turmeric, sunshine, and a whole lot of yellow</span></div>
        <div class="event-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><circle cx="12" cy="12" r="4"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3M4.93 4.93l2.12 2.12M16.95 16.95l2.12 2.12M4.93 19.07l2.12-2.12M16.95 7.05l2.12-2.12"/></svg>
        </div>
      </div>

      <div class="event-row">
        <div class="event-time">2:00 PM</div>
        <div class="event-name">Mayara<span class="secondary">Maternal blessings — a beloved Marwadi-Jain tradition</span></div>
        <div class="event-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><path d="M12 21s-7-4.5-7-10a4 4 0 017-2.65A4 4 0 0119 11c0 5.5-7 10-7 10z"/></svg>
        </div>
      </div>

      <div class="event-row">
        <div class="event-time">6:00 PM</div>
        <div class="event-name">Tilak &amp; Sagai · Sangeet Sandhya<span class="secondary">Vows of the families followed by music, dance &amp; dinner</span></div>
        <div class="event-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><path d="M9 18V5l12-2v13M6 21a3 3 0 100-6 3 3 0 000 6zM18 19a3 3 0 100-6 3 3 0 000 6z"/></svg>
        </div>
      </div>

    </div>
  </div>

  <div class="day-card reveal">
    <div class="day-header">
      <div class="day-number">Day Two · The Big Day</div>
      <div class="day-date">
        17<sup style="font-size:0.5em;">th</sup> July, 2026
        <span class="day-name">Friday</span>
      </div>
    </div>
    <div class="events-list">

      <div class="event-row">
        <div class="event-time">10:00 AM</div>
        <div class="event-name">Nikasi<span class="secondary">The groom's grand departure — band, baaja, baraat</span></div>
        <div class="event-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><path d="M3 12h13l-3-3M3 12l-1 0M3 12h13l-3 3"/><circle cx="18" cy="14" r="4"/></svg>
        </div>
      </div>

      <div class="event-row">
        <div class="event-time">2:15 PM</div>
        <div class="event-name">Phere<span class="secondary">Seven sacred vows around the holy fire</span></div>
        <div class="event-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><path d="M12 22c4-2 6-6 6-10 0-3-2-6-6-10-4 4-6 7-6 10 0 4 2 8 6 10z"/></svg>
        </div>
      </div>

      <div class="event-row">
        <div class="event-time">7:00 PM</div>
        <div class="event-name">Reception<span class="secondary">An evening of celebration, congratulations &amp; cuisine</span></div>
        <div class="event-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2"><path d="M8 2v6a4 4 0 008 0V2M12 14v8M8 22h8"/></svg>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- VENUE -->
<section id="venue" class="venue-section">
  <div class="reveal">
    <div class="eyebrow" style="justify-content:center;">The Place</div>
    <h2 class="section-title">Where it all <em>happens.</em></h2>
  </div>

  <div class="venue-card reveal">
    <div class="eyebrow" style="justify-content:center;">Wedding Venue</div>
    <div class="venue-name">Agra Exotica</div>
    <div class="venue-city">Surat · Gujarat</div>
    <a class="venue-link" href="https://www.google.com/maps/search/?api=1&query=Agra+Exotica+Surat" target="_blank" rel="noopener">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
      Open in Maps
    </a>
  </div>
</section>

<!-- RSVP -->
<div id="rsvp" class="rsvp-section">
  <div class="rsvp-inner">
    <div class="rsvp-intro reveal">
      <div class="eyebrow" style="justify-content:center;">Kindly Respond</div>
      <h2 class="section-title">Will you <em>join us?</em></h2>
      <p class="lede">Please RSVP by <strong style="color:var(--burgundy);">30 June 2026</strong>. Your presence — and your hunger for Surti food — is requested.</p>
    </div>

    <div class="rsvp-form reveal" id="rsvpFormWrap">
      <form id="rsvpForm">

        <div class="field-row">
          <div class="field-group" style="margin:0;">
            <label>Your Name <span class="req">*</span></label>
            <input type="text" name="name" required placeholder="Full name">
          </div>
          <div class="field-group" style="margin:0;">
            <label>Phone <span class="req">*</span></label>
            <input type="tel" name="phone" required placeholder="+91 ...">
          </div>
        </div>

        <div class="field-group">
          <label>Will you be celebrating with us? <span class="req">*</span></label>
          <div class="radio-group">
            <label class="radio-pill">
              <input type="radio" name="attending" value="yes" required>
              <span>✦ Yes, with joy</span>
            </label>
            <label class="radio-pill">
              <input type="radio" name="attending" value="no">
              <span>Sending blessings from afar</span>
            </label>
          </div>
        </div>

        <div id="attendingFields">

          <div class="field-row">
            <div class="field-group" style="margin:0;">
              <label>Number of Guests <span class="req">*</span></label>
              <input type="number" name="attendees" min="1" max="20" value="1" placeholder="Including yourself">
            </div>
            <div class="field-group" style="margin:0;">
              <label>Travelling From</label>
              <input type="text" name="fromCity" placeholder="City / town">
            </div>
          </div>

          <div class="field-group">
            <label>Which events will you attend?</label>
            <div class="event-checks">
              <label class="event-check">
                <input type="checkbox" name="events" value="Pila Chawal">
                <div class="check-content"><div><span class="ec-name">Pila Chawal</span><span class="ec-date">Jul 16 · 9 AM</span></div></div>
              </label>
              <label class="event-check">
                <input type="checkbox" name="events" value="Haldi">
                <div class="check-content"><div><span class="ec-name">Haldi</span><span class="ec-date">Jul 16 · 11 AM</span></div></div>
              </label>
              <label class="event-check">
                <input type="checkbox" name="events" value="Mayara">
                <div class="check-content"><div><span class="ec-name">Mayara</span><span class="ec-date">Jul 16 · 2 PM</span></div></div>
              </label>
              <label class="event-check">
                <input type="checkbox" name="events" value="Tilak & Sangeet">
                <div class="check-content"><div><span class="ec-name">Tilak &amp; Sangeet</span><span class="ec-date">Jul 16 · 6 PM</span></div></div>
              </label>
              <label class="event-check">
                <input type="checkbox" name="events" value="Nikasi">
                <div class="check-content"><div><span class="ec-name">Nikasi</span><span class="ec-date">Jul 17 · 10 AM</span></div></div>
              </label>
              <label class="event-check">
                <input type="checkbox" name="events" value="Phere">
                <div class="check-content"><div><span class="ec-name">Phere</span><span class="ec-date">Jul 17 · 2:15 PM</span></div></div>
              </label>
              <label class="event-check">
                <input type="checkbox" name="events" value="Reception">
                <div class="check-content"><div><span class="ec-name">Reception</span><span class="ec-date">Jul 17 · 7 PM</span></div></div>
              </label>
            </div>
          </div>

          <div class="field-row">
            <div class="field-group" style="margin:0;">
              <label>Meal Preference</label>
              <select name="dietary">
                <option value="">Select…</option>
                <option>Jain (no root vegetables)</option>
                <option>Jain</option>
                <option>Pure Vegetarian</option>
                <option>Vegan</option>
                <option>Other (mention in message)</option>
              </select>
            </div>
            <div class="field-group" style="margin:0;">
              <label>Accommodation Help?</label>
              <select name="accommodation">
                <option value="">Select…</option>
                <option>No, I'll arrange my own</option>
                <option>Yes, please help</option>
                <option>Maybe — will confirm</option>
              </select>
            </div>
          </div>

          <div class="field-group">
            <label>Song Request for Sangeet 🎶</label>
            <input type="text" name="song" placeholder="Get the DJ ready…">
          </div>

        </div>

        <div class="field-group">
          <label>A Note for the Couple</label>
          <textarea name="message" placeholder="Blessings, memories, or just a sweet hello…"></textarea>
        </div>

        <button type="submit" class="submit-btn" id="submitBtn">Send My RSVP →</button>
        <div class="form-message" id="formMsg"></div>
      </form>
    </div>

    <!-- Confirmation -->
    <div class="rsvp-form reveal" id="rsvpConfirm" style="display:none;">
      <div class="rsvp-confirmation">
        <div class="check-circle">
          <svg width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="20 6 9 17 4 12"/></svg>
        </div>
        <h3 id="confirmName">Thank you</h3>
        <p>Your RSVP has been received. We can't wait to celebrate with you.</p>
        <button class="rsvp-edit-btn" id="editRsvpBtn">Edit My RSVP</button>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-blessing">|| जय जिनेन्द्र ||</div>
  <div class="footer-monogram">M &amp; D</div>
  <div class="footer-line">— with love, from the same pincode —</div>
  <div class="host-dot" id="hostDot" title="Host"></div>
</footer>

<!-- HOST DASHBOARD -->
<div class="host-overlay" id="hostOverlay">
  <div class="host-modal">

    <div id="hostPasscodeView" class="host-passcode-prompt">
      <h2>Host Dashboard</h2>
      <p>Enter passcode to view RSVPs</p>
      <input type="password" id="passcodeInput" placeholder="passcode" autocomplete="off">
      <div style="margin-top:20px;">
        <button class="host-btn primary" id="passcodeSubmit">Enter</button>
        <button class="host-btn" id="passcodeCancel">Cancel</button>
      </div>
      <div id="passcodeError" style="color:var(--burgundy); margin-top:14px; font-family:var(--serif); font-style:italic; min-height:20px;"></div>
    </div>

    <div id="hostDashboardView" style="display:none; flex-direction:column; flex:1; overflow:hidden;">
      <div class="host-header">
        <div class="host-title">RSVP Dashboard</div>
        <div class="host-actions">
          <button class="host-btn" id="exportBtn">Export CSV</button>
          <button class="host-btn" id="refreshBtn">Refresh</button>
          <button class="host-btn primary" id="closeHostBtn">Close</button>
        </div>
      </div>
      <div class="host-body" id="hostBody"></div>
    </div>

  </div>
</div>

<script>
  // ============================================
  // CONFIG
  // ============================================
  const HOST_PASSCODE = "mitudilip2026";   // [EDIT] Change this to your secret
  const WEDDING_DATE = new Date("2026-07-17T14:15:00+05:30"); // Phere time
  const RSVP_KEY_PREFIX = "rsvp:";

  // ============================================
  // NAV scroll state
  // ============================================
  const nav = document.getElementById("nav");
  window.addEventListener("scroll", () => {
    nav.classList.toggle("scrolled", window.scrollY > 50);
  });

  // ============================================
  // COUNTDOWN
  // ============================================
  function tickCountdown() {
    const now = new Date();
    const diff = WEDDING_DATE - now;
    if (diff <= 0) {
      ["cd-days","cd-hours","cd-mins","cd-secs"].forEach(id => {
        document.getElementById(id).textContent = "0";
      });
      document.querySelector(".countdown-label").textContent = "— the day is here —";
      return;
    }
    const d = Math.floor(diff / 86400000);
    const h = Math.floor((diff % 86400000) / 3600000);
    const m = Math.floor((diff % 3600000) / 60000);
    const s = Math.floor((diff % 60000) / 1000);
    document.getElementById("cd-days").textContent  = d;
    document.getElementById("cd-hours").textContent = h;
    document.getElementById("cd-mins").textContent  = m;
    document.getElementById("cd-secs").textContent  = s;
  }
  tickCountdown();
  setInterval(tickCountdown, 1000);

  // ============================================
  // Reveal on scroll
  // ============================================
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add("visible"); obs.unobserve(e.target); }
    });
  }, { threshold: 0.1, rootMargin: "0px 0px -50px 0px" });
  document.querySelectorAll(".reveal").forEach(el => obs.observe(el));

  // ============================================
  // RSVP — attendance toggle
  // ============================================
  const attendingFields = document.getElementById("attendingFields");
  document.querySelectorAll('input[name="attending"]').forEach(r => {
    r.addEventListener("change", e => {
      const showFields = e.target.value === "yes";
      attendingFields.style.opacity = showFields ? "1" : "0.4";
      attendingFields.style.pointerEvents = showFields ? "auto" : "none";
    });
  });

  // ============================================
  // RSVP — submit, storage, dedupe by phone (within this device)
  // ============================================
  const form = document.getElementById("rsvpForm");
  const submitBtn = document.getElementById("submitBtn");
  const formMsg = document.getElementById("formMsg");
  const formWrap = document.getElementById("rsvpFormWrap");
  const confirmWrap = document.getElementById("rsvpConfirm");
  const confirmName = document.getElementById("confirmName");

  function showMsg(text, type) {
    formMsg.textContent = text;
    formMsg.className = "form-message " + type;
  }

  async function getMyExistingKey() {
    // Stored per-user (non-shared) so this device knows what it submitted
    try {
      const r = await window.storage.get("my-rsvp-key");
      return r ? r.value : null;
    } catch { return null; }
  }

  async function saveMyKey(key) {
    try { await window.storage.set("my-rsvp-key", key); } catch {}
  }

  async function showConfirmation(name) {
    formWrap.style.display = "none";
    confirmWrap.style.display = "block";
    confirmWrap.classList.add("visible");
    confirmName.textContent = `Thank you, ${name.split(" ")[0]}`;
  }

  document.getElementById("editRsvpBtn").addEventListener("click", async () => {
    confirmWrap.style.display = "none";
    formWrap.style.display = "block";
    // Pre-fill from existing
    const myKey = await getMyExistingKey();
    if (!myKey) return;
    try {
      const existing = await window.storage.get(myKey, true);
      if (!existing) return;
      const data = JSON.parse(existing.value);
      form.name.value = data.name || "";
      form.phone.value = data.phone || "";
      form.attendees.value = data.attendees || 1;
      form.fromCity.value = data.fromCity || "";
      form.dietary.value = data.dietary || "";
      form.accommodation.value = data.accommodation || "";
      form.song.value = data.song || "";
      form.message.value = data.message || "";
      if (data.attending) {
        const radio = form.querySelector(`input[name="attending"][value="${data.attending}"]`);
        if (radio) { radio.checked = true; radio.dispatchEvent(new Event("change")); }
      }
      (data.events || []).forEach(ev => {
        const box = form.querySelector(`input[name="events"][value="${ev}"]`);
        if (box) box.checked = true;
      });
    } catch {}
  });

  form.addEventListener("submit", async e => {
    e.preventDefault();
    submitBtn.disabled = true;
    submitBtn.textContent = "Sending…";

    const fd = new FormData(form);
    const events = Array.from(form.querySelectorAll('input[name="events"]:checked')).map(c => c.value);

    const data = {
      name: (fd.get("name") || "").trim(),
      phone: (fd.get("phone") || "").trim(),
      attending: fd.get("attending") || "",
      attendees: parseInt(fd.get("attendees")) || 1,
      fromCity: (fd.get("fromCity") || "").trim(),
      events,
      dietary: fd.get("dietary") || "",
      accommodation: fd.get("accommodation") || "",
      song: (fd.get("song") || "").trim(),
      message: (fd.get("message") || "").trim(),
      submittedAt: new Date().toISOString()
    };

    if (!data.name || !data.phone || !data.attending) {
      showMsg("Please fill in your name, phone, and attendance.", "error");
      submitBtn.disabled = false;
      submitBtn.textContent = "Send My RSVP →";
      return;
    }

    try {
      let key = await getMyExistingKey();
      if (!key) {
        const stamp = Date.now();
        const rand = Math.random().toString(36).slice(2, 8);
        key = `${RSVP_KEY_PREFIX}${stamp}_${rand}`;
      }
      await window.storage.set(key, JSON.stringify(data), true);
      await saveMyKey(key);

      showMsg("RSVP received with love. See you in July! 🌼", "success");
      setTimeout(() => showConfirmation(data.name), 800);
    } catch (err) {
      console.error(err);
      showMsg("Hmm, something went wrong. Please try again in a moment.", "error");
      submitBtn.disabled = false;
      submitBtn.textContent = "Send My RSVP →";
    }
  });

  // If user already submitted, jump to confirmation
  (async () => {
    const myKey = await getMyExistingKey();
    if (!myKey) return;
    try {
      const existing = await window.storage.get(myKey, true);
      if (!existing) return;
      const data = JSON.parse(existing.value);
      formWrap.style.display = "none";
      confirmWrap.style.display = "block";
      confirmWrap.classList.add("visible");
      confirmName.textContent = `Thank you, ${data.name.split(" ")[0]}`;
    } catch {}
  })();

  // ============================================
  // HOST DASHBOARD
  // ============================================
  const hostDot = document.getElementById("hostDot");
  const hostOverlay = document.getElementById("hostOverlay");
  const passcodeView = document.getElementById("hostPasscodeView");
  const dashView = document.getElementById("hostDashboardView");
  const passcodeInput = document.getElementById("passcodeInput");
  const passcodeError = document.getElementById("passcodeError");

  function openHost() {
    hostOverlay.classList.add("active");
    passcodeView.style.display = "block";
    dashView.style.display = "none";
    passcodeInput.value = "";
    passcodeError.textContent = "";
    setTimeout(() => passcodeInput.focus(), 100);
  }
  function closeHost() {
    hostOverlay.classList.remove("active");
    // Clear hash so refresh doesn't re-open
    if (location.hash === "#host") history.replaceState(null, "", location.pathname);
  }

  hostDot.addEventListener("click", openHost);
  if (location.hash === "#host") openHost();

  document.getElementById("passcodeCancel").addEventListener("click", closeHost);
  document.getElementById("closeHostBtn").addEventListener("click", closeHost);
  hostOverlay.addEventListener("click", e => { if (e.target === hostOverlay) closeHost(); });

  document.getElementById("passcodeSubmit").addEventListener("click", tryPasscode);
  passcodeInput.addEventListener("keydown", e => { if (e.key === "Enter") tryPasscode(); });

  function tryPasscode() {
    if (passcodeInput.value === HOST_PASSCODE) {
      passcodeView.style.display = "none";
      dashView.style.display = "flex";
      loadRsvps();
    } else {
      passcodeError.textContent = "Wrong passcode. Try again.";
      passcodeInput.value = "";
    }
  }

  async function loadRsvps() {
    const body = document.getElementById("hostBody");
    body.innerHTML = '<div class="empty-state">Loading RSVPs…</div>';

    let rsvps = [];
    try {
      const listResult = await window.storage.list(RSVP_KEY_PREFIX, true);
      if (listResult && listResult.keys && listResult.keys.length) {
        for (const key of listResult.keys) {
          try {
            const r = await window.storage.get(key, true);
            if (r) rsvps.push({ key, ...JSON.parse(r.value) });
          } catch {}
        }
      }
    } catch (err) {
      console.error(err);
      body.innerHTML = '<div class="empty-state">Could not load RSVPs.</div>';
      return;
    }

    if (!rsvps.length) {
      body.innerHTML = '<div class="empty-state">No RSVPs yet. Share the link! 💌</div>';
      return;
    }

    rsvps.sort((a, b) => new Date(b.submittedAt) - new Date(a.submittedAt));

    const yes = rsvps.filter(r => r.attending === "yes");
    const totalAttending = yes.reduce((s, r) => s + (r.attendees || 1), 0);
    const eventCounts = {};
    yes.forEach(r => (r.events || []).forEach(e => {
      eventCounts[e] = (eventCounts[e] || 0) + (r.attendees || 1);
    }));

    let html = `
      <div class="stats-grid">
        <div class="stat-card"><div class="num">${rsvps.length}</div><div class="lbl">Total RSVPs</div></div>
        <div class="stat-card"><div class="num">${yes.length}</div><div class="lbl">Attending</div></div>
        <div class="stat-card"><div class="num">${totalAttending}</div><div class="lbl">Total Guests</div></div>
        <div class="stat-card"><div class="num">${rsvps.length - yes.length}</div><div class="lbl">Regrets</div></div>
      </div>

      <h3 style="font-family:var(--serif); font-style:italic; color:var(--burgundy); font-weight:300; font-size:18px; margin-bottom:10px;">Per Event</h3>
      <div class="stats-grid" style="margin-bottom:36px;">
        ${Object.entries(eventCounts).map(([e, c]) =>
          `<div class="stat-card"><div class="num">${c}</div><div class="lbl">${e}</div></div>`).join("") ||
          '<div style="color:var(--ink-soft); font-style:italic;">No event selections yet.</div>'}
      </div>

      <h3 style="font-family:var(--serif); font-style:italic; color:var(--burgundy); font-weight:300; font-size:18px; margin-bottom:14px;">All Responses</h3>
      <div style="overflow:auto;">
        <table class="rsvp-table">
          <thead><tr>
            <th>Name</th><th>Phone</th><th>Status</th><th>Guests</th>
            <th>From</th><th>Events</th><th>Diet</th><th>Stay</th><th>Note</th><th>Song</th><th>When</th>
          </tr></thead>
          <tbody>
          ${rsvps.map(r => `
            <tr>
              <td class="nm">${esc(r.name)}</td>
              <td>${esc(r.phone)}</td>
              <td>${r.attending === "yes" ? "✓ Yes" : "Regrets"}</td>
              <td>${r.attending === "yes" ? (r.attendees || 1) : "—"}</td>
              <td>${esc(r.fromCity || "—")}</td>
              <td><div class="ev-pills">${(r.events || []).map(e =>
                  `<span class="ev-pill">${esc(e)}</span>`).join("") || "—"}</div></td>
              <td>${esc(r.dietary || "—")}</td>
              <td>${esc(r.accommodation || "—")}</td>
              <td class="msg-cell">${esc(r.message || "—")}</td>
              <td>${esc(r.song || "—")}</td>
              <td style="white-space:nowrap; font-size:11px; color:var(--ink-soft);">${fmtDate(r.submittedAt)}</td>
            </tr>
          `).join("")}
          </tbody>
        </table>
      </div>
    `;
    body.innerHTML = html;

    // Stash for export
    window._rsvpData = rsvps;
  }

  document.getElementById("refreshBtn").addEventListener("click", loadRsvps);

  document.getElementById("exportBtn").addEventListener("click", () => {
    const rsvps = window._rsvpData || [];
    if (!rsvps.length) return alert("No RSVPs to export.");
    const headers = ["Name","Phone","Status","Guests","From City","Events","Diet","Accommodation","Song","Message","Submitted"];
    const rows = rsvps.map(r => [
      r.name, r.phone, r.attending, r.attendees || 1, r.fromCity || "",
      (r.events || []).join("; "), r.dietary || "", r.accommodation || "",
      r.song || "", r.message || "", r.submittedAt || ""
    ]);
    const csv = [headers, ...rows].map(row =>
      row.map(v => `"${String(v).replace(/"/g, '""')}"`).join(",")
    ).join("\n");
    const blob = new Blob([csv], { type: "text/csv" });
    const a = document.createElement("a");
    a.href = URL.createObjectURL(blob);
    a.download = `mitu-dilip-rsvps-${new Date().toISOString().slice(0,10)}.csv`;
    a.click();
  });

  function esc(s) {
    return String(s == null ? "" : s)
      .replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;")
      .replace(/"/g, "&quot;");
  }
  function fmtDate(iso) {
    try {
      const d = new Date(iso);
      return d.toLocaleDateString("en-IN", { day: "numeric", month: "short" }) + " " +
             d.toLocaleTimeString("en-IN", { hour: "2-digit", minute: "2-digit" });
    } catch { return ""; }
  }
</script>
</body>
