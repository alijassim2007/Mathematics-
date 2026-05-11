# Mathematics-
الرياضيات مع علي 
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>الرياضيات مع علي | Math With Ali</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/11.8.0/math.js"></script>
<script src="https://cdn.plot.ly/plotly-2.24.1.min.js"></script>
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@400;700;900&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300&family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --gold-100: #FFF8DC;
  --gold-300: #FFD700;
  --gold-500: #D4AF37;
  --gold-700: #996515;
  --gold-900: #4A3000;
  --black-0: #000000;
  --black-100: #080808;
  --black-200: #111111;
  --black-300: #1a1a1a;
  --black-400: #222222;
  --white-dim: rgba(255,255,255,0.06);
  --glow-gold: 0 0 40px rgba(212,175,55,0.35), 0 0 80px rgba(212,175,55,0.15);
  --glow-sm: 0 0 20px rgba(212,175,55,0.25);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
  background: var(--black-0);
  color: #e8e0cc;
  font-family: 'Cairo', sans-serif;
  overflow-x: hidden;
  min-height: 100vh;
}

/* ── NOISE OVERLAY ── */
body::before {
  content: '';
  position: fixed; inset: 0; z-index: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
}

/* ── ANIMATED BACKGROUND ── */
.bg-orbs {
  position: fixed; inset: 0; z-index: 0; pointer-events: none; overflow: hidden;
}
.orb {
  position: absolute; border-radius: 50%;
  filter: blur(120px); opacity: 0.07; animation: orb-drift 18s ease-in-out infinite;
}
.orb-1 { width: 600px; height: 600px; background: var(--gold-500); top: -200px; right: -200px; animation-delay: 0s; }
.orb-2 { width: 400px; height: 400px; background: var(--gold-300); bottom: -150px; left: -100px; animation-delay: -7s; }
.orb-3 { width: 300px; height: 300px; background: var(--gold-700); top: 50%; left: 50%; animation-delay: -12s; }

@keyframes orb-drift {
  0%,100% { transform: translate(0,0) scale(1); }
  33% { transform: translate(60px,-40px) scale(1.1); }
  66% { transform: translate(-40px,60px) scale(0.9); }
}

/* ── LOGIN SCREEN ── */
#login-screen {
  position: fixed; inset: 0; z-index: 100;
  display: flex; align-items: center; justify-content: center;
  background: radial-gradient(ellipse at center, #0e0900 0%, #000 70%);
}

.login-wrapper {
  position: relative; width: 440px;
}

.login-ornament {
  position: absolute; top: -60px; left: 50%; transform: translateX(-50%);
  width: 120px; height: 120px;
  border: 1px solid var(--gold-700);
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  animation: spin-slow 20s linear infinite;
}
.login-ornament::before {
  content: '';
  position: absolute; inset: 8px;
  border: 1px solid var(--gold-500);
  border-radius: 50%;
}
.login-ornament-inner {
  font-size: 48px;
  animation: spin-slow 20s linear infinite reverse;
}

@keyframes spin-slow { to { transform: translateX(-50%) rotate(360deg); } }

.login-card {
  background: linear-gradient(160deg, #141008 0%, #0a0700 60%, #000 100%);
  border: 1px solid var(--gold-700);
  border-radius: 4px;
  padding: 90px 50px 50px;
  position: relative;
  overflow: hidden;
}
.login-card::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; height: 1px;
  background: linear-gradient(90deg, transparent, var(--gold-500), transparent);
}
.login-card::after {
  content: '';
  position: absolute; bottom: 0; left: 0; right: 0; height: 1px;
  background: linear-gradient(90deg, transparent, var(--gold-700), transparent);
}

.login-title {
  font-family: 'Cinzel Decorative', serif;
  font-size: 1.1rem;
  color: var(--gold-500);
  text-align: center;
  letter-spacing: 0.2em;
  margin-bottom: 8px;
}
.login-subtitle {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  color: var(--gold-700);
  text-align: center;
  font-size: 1.3rem;
  margin-bottom: 40px;
}

.field-group {
  position: relative; margin-bottom: 20px;
}
.field-label {
  display: block; font-size: 0.7rem;
  color: var(--gold-700); letter-spacing: 0.15em;
  text-transform: uppercase; margin-bottom: 6px;
}
.field-input {
  width: 100%; padding: 14px 18px;
  background: rgba(255,255,255,0.03);
  border: 1px solid #2a2010;
  border-radius: 2px;
  color: #e8e0cc;
  font-family: 'Cairo', sans-serif;
  font-size: 0.95rem;
  transition: border-color 0.3s, box-shadow 0.3s;
  outline: none;
}
.field-input:focus {
  border-color: var(--gold-700);
  box-shadow: 0 0 0 3px rgba(212,175,55,0.08), inset 0 0 20px rgba(212,175,55,0.03);
}

.btn-login {
  width: 100%; padding: 16px;
  background: linear-gradient(135deg, var(--gold-900) 0%, var(--gold-700) 50%, var(--gold-500) 100%);
  border: none; border-radius: 2px;
  color: #000; font-family: 'Cinzel Decorative', serif;
  font-size: 0.85rem; letter-spacing: 0.2em;
  cursor: pointer; margin-top: 10px;
  position: relative; overflow: hidden;
  transition: opacity 0.3s, transform 0.2s;
}
.btn-login::before {
  content: ''; position: absolute; inset: 0;
  background: linear-gradient(135deg, transparent 40%, rgba(255,255,255,0.15) 60%, transparent 70%);
  transform: translateX(-100%); transition: transform 0.6s;
}
.btn-login:hover::before { transform: translateX(200%); }
.btn-login:hover { opacity: 0.9; transform: translateY(-1px); }
.btn-login:active { transform: translateY(0); }

/* ── MAIN APP ── */
#main-app { display: none; position: relative; z-index: 1; min-height: 100vh; }

/* ── HEADER ── */
header {
  display: flex; justify-content: space-between; align-items: center;
  padding: 0 50px; height: 80px;
  border-bottom: 1px solid #1a1200;
  background: linear-gradient(180deg, rgba(10,7,0,0.95) 0%, rgba(0,0,0,0.85) 100%);
  backdrop-filter: blur(20px);
  position: sticky; top: 0; z-index: 50;
}

.header-logo {
  display: flex; align-items: center; gap: 14px;
}
.logo-emblem {
  width: 44px; height: 44px;
  border: 1px solid var(--gold-700);
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 20px;
  position: relative;
}
.logo-emblem::after {
  content: '';
  position: absolute; inset: -4px;
  border: 1px solid var(--gold-900);
  border-radius: 50%;
}
.logo-text {
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.9rem;
  color: var(--gold-500);
  letter-spacing: 0.1em;
  line-height: 1.3;
}
.logo-sub {
  font-family: 'Cormorant Garamond', serif;
  font-size: 0.75rem;
  color: var(--gold-700);
  font-style: italic;
  letter-spacing: 0.05em;
}

.header-right {
  display: flex; align-items: center; gap: 24px;
}
.user-badge {
  display: flex; align-items: center; gap: 8px;
  background: rgba(212,175,55,0.06);
  border: 1px solid #2a2010;
  border-radius: 30px; padding: 6px 16px;
}
.user-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--gold-500); animation: pulse 2s infinite; }
@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }
.user-name { font-size: 0.8rem; color: var(--gold-700); }

.lang-btn {
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.7rem; letter-spacing: 0.15em;
  color: var(--gold-700); cursor: pointer;
  padding: 6px 14px;
  border: 1px solid #2a2010; border-radius: 30px;
  transition: all 0.3s;
}
.lang-btn:hover { border-color: var(--gold-700); color: var(--gold-500); }

/* ── HOME VIEW ── */
#home-view { padding: 80px 60px; }

.hero {
  text-align: center; margin-bottom: 80px;
}
.hero-title {
  font-family: 'Cinzel Decorative', serif;
  font-size: clamp(2rem, 5vw, 3.5rem);
  background: linear-gradient(135deg, var(--gold-700) 0%, var(--gold-300) 50%, var(--gold-700) 100%);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: 0.05em; line-height: 1.2;
  margin-bottom: 16px;
}
.hero-subtitle {
  font-family: 'Cormorant Garamond', serif;
  font-size: 1.4rem; font-style: italic;
  color: var(--gold-700); letter-spacing: 0.08em;
}
.hero-divider {
  display: flex; align-items: center; gap: 20px;
  justify-content: center; margin-top: 30px;
}
.divider-line { width: 120px; height: 1px; background: linear-gradient(90deg, transparent, var(--gold-700)); }
.divider-line.rev { background: linear-gradient(90deg, var(--gold-700), transparent); }
.divider-diamond { width: 8px; height: 8px; background: var(--gold-500); transform: rotate(45deg); }

/* ── MENU CARDS ── */
.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2px; max-width: 1100px; margin: 0 auto;
}

.card {
  background: linear-gradient(160deg, #0d0a04, #070500);
  padding: 50px 30px;
  text-align: center;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
  border: 1px solid #150f04;
  animation: card-in 0.8s ease both;
}
.card:nth-child(1) { animation-delay: 0.1s; }
.card:nth-child(2) { animation-delay: 0.2s; }
.card:nth-child(3) { animation-delay: 0.3s; }
.card:nth-child(4) { animation-delay: 0.4s; }

@keyframes card-in {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

.card::before {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(circle at 50% 0%, rgba(212,175,55,0.12) 0%, transparent 70%);
  opacity: 0; transition: opacity 0.5s;
}
.card::after {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; height: 1px;
  background: linear-gradient(90deg, transparent, var(--gold-700), transparent);
  opacity: 0; transition: opacity 0.5s;
}
.card:hover::before, .card:hover::after { opacity: 1; }
.card:hover {
  transform: translateY(-8px);
  background: linear-gradient(160deg, #130e05, #0a0700);
  border-color: #2a1e08;
  box-shadow: 0 30px 60px rgba(0,0,0,0.6), 0 0 40px rgba(212,175,55,0.08);
}

.card-number {
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.65rem; letter-spacing: 0.3em;
  color: var(--gold-900); margin-bottom: 20px;
}
.card-icon {
  font-size: 44px; margin-bottom: 20px; display: block;
  filter: drop-shadow(0 0 20px rgba(212,175,55,0.3));
  transition: transform 0.4s, filter 0.4s;
}
.card:hover .card-icon {
  transform: scale(1.1);
  filter: drop-shadow(0 0 30px rgba(212,175,55,0.5));
}
.card-title {
  font-family: 'Cinzel Decorative', serif;
  font-size: 1rem; letter-spacing: 0.1em;
  color: var(--gold-500); margin-bottom: 10px;
}
.card-desc {
  font-size: 0.8rem; color: #666;
  font-style: italic; font-family: 'Cormorant Garamond', serif;
  font-size: 1rem;
}
.card-arrow {
  margin-top: 24px; color: var(--gold-900);
  font-size: 1.2rem; transition: all 0.3s;
}
.card:hover .card-arrow { color: var(--gold-500); transform: translateX(-6px); }

/* ── SECTION VIEWS ── */
.section-view {
  display: none; min-height: calc(100vh - 80px);
  padding: 60px;
  animation: section-in 0.6s cubic-bezier(0.23, 1, 0.32, 1) both;
}
@keyframes section-in {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.back-btn {
  display: inline-flex; align-items: center; gap: 10px;
  color: var(--gold-700); cursor: pointer;
  font-size: 0.8rem; letter-spacing: 0.15em;
  font-family: 'Cinzel Decorative', serif;
  margin-bottom: 50px;
  padding: 10px 20px;
  border: 1px solid #1a1200; border-radius: 30px;
  transition: all 0.3s;
}
.back-btn:hover { border-color: var(--gold-700); color: var(--gold-500); }

.section-header {
  margin-bottom: 50px;
}
.section-number {
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.6rem; letter-spacing: 0.4em;
  color: var(--gold-900); margin-bottom: 12px;
}
.section-title {
  font-family: 'Cinzel Decorative', serif;
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  background: linear-gradient(135deg, var(--gold-700), var(--gold-300));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: 0.05em;
}
.section-line {
  width: 60px; height: 1px;
  background: linear-gradient(90deg, var(--gold-700), transparent);
  margin-top: 16px;
}

/* ── PANEL ── */
.panel {
  background: linear-gradient(160deg, #0d0a04, #070500);
  border: 1px solid #1a1200; border-radius: 2px;
  padding: 40px; max-width: 900px;
  position: relative;
}
.panel::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; height: 1px;
  background: linear-gradient(90deg, transparent, var(--gold-700), transparent);
}

/* ── INPUTS ── */
.input-gold {
  width: 100%; padding: 16px 22px;
  background: rgba(255,255,255,0.02);
  border: 1px solid #1a1200; border-radius: 2px;
  color: #e8e0cc;
  font-family: 'Cairo', sans-serif; font-size: 1rem;
  outline: none; transition: all 0.3s;
  margin-bottom: 16px;
}
.input-gold:focus {
  border-color: var(--gold-700);
  background: rgba(212,175,55,0.03);
  box-shadow: 0 0 0 3px rgba(212,175,55,0.06);
}
.input-gold::placeholder { color: #444; }

.textarea-gold {
  width: 100%; padding: 16px 22px;
  background: rgba(255,255,255,0.02);
  border: 1px solid #1a1200; border-radius: 2px;
  color: #e8e0cc;
  font-family: 'Cairo', sans-serif; font-size: 0.95rem;
  outline: none; transition: all 0.3s;
  resize: vertical; min-height: 120px;
}
.textarea-gold:focus {
  border-color: var(--gold-700);
  background: rgba(212,175,55,0.03);
  box-shadow: 0 0 0 3px rgba(212,175,55,0.06);
}

/* ── BUTTON ── */
.btn-primary {
  display: inline-flex; align-items: center; gap: 10px;
  padding: 14px 36px;
  background: linear-gradient(135deg, var(--gold-900) 0%, var(--gold-700) 50%, var(--gold-500) 100%);
  border: none; border-radius: 2px;
  color: #000; font-family: 'Cinzel Decorative', serif;
  font-size: 0.75rem; letter-spacing: 0.2em;
  cursor: pointer; position: relative; overflow: hidden;
  transition: all 0.3s; margin-top: 8px;
}
.btn-primary::before {
  content: ''; position: absolute; inset: 0;
  background: linear-gradient(135deg, transparent 40%, rgba(255,255,255,0.2) 60%, transparent 70%);
  transform: translateX(-100%); transition: transform 0.6s;
}
.btn-primary:hover::before { transform: translateX(200%); }
.btn-primary:hover { box-shadow: var(--glow-sm); transform: translateY(-2px); }

/* ── CALCULATOR DISPLAY ── */
.calc-display {
  background: rgba(0,0,0,0.5);
  border: 1px solid #1a1200; border-radius: 2px;
  padding: 24px 28px; margin: 20px 0;
  min-height: 80px; display: flex;
  align-items: center; justify-content: flex-end;
  position: relative;
}
.calc-display::before {
  content: 'RESULT';
  position: absolute; top: 10px; right: 14px;
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.55rem; letter-spacing: 0.3em;
  color: var(--gold-900);
}
.calc-result {
  font-family: 'Cormorant Garamond', serif;
  font-size: 3rem; font-weight: 300;
  color: var(--gold-300);
  text-shadow: var(--glow-sm);
}

/* ── AI RESULT ── */
.ai-result {
  margin-top: 24px;
  padding: 28px;
  background: rgba(0,0,0,0.4);
  border: 1px solid #1a1200; border-radius: 2px;
  border-right: 2px solid var(--gold-700);
  display: none;
  animation: section-in 0.5s ease both;
}
.ai-result.active { display: block; }
.ai-step {
  display: flex; gap: 16px; margin-bottom: 20px;
  padding-bottom: 20px; border-bottom: 1px solid #1a1200;
}
.ai-step:last-child { border-bottom: none; margin-bottom: 0; padding-bottom: 0; }
.ai-step-num {
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.7rem; color: var(--gold-700);
  min-width: 24px; margin-top: 2px;
}
.ai-step-text { font-size: 0.95rem; color: #c8b89a; line-height: 1.8; }
.ai-final {
  margin-top: 20px; padding: 20px;
  background: rgba(212,175,55,0.06);
  border: 1px solid var(--gold-900); border-radius: 2px;
  text-align: center;
}
.ai-final-label {
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.65rem; letter-spacing: 0.3em;
  color: var(--gold-700); margin-bottom: 8px;
}
.ai-final-value {
  font-family: 'Cormorant Garamond', serif;
  font-size: 2.5rem; color: var(--gold-300);
  font-weight: 300;
}

/* ── LOADING ── */
.loading-dots {
  display: flex; gap: 6px; justify-content: center; padding: 20px;
}
.loading-dots span {
  width: 8px; height: 8px; border-radius: 50%;
  background: var(--gold-700);
  animation: dot-bounce 1.4s ease-in-out infinite;
}
.loading-dots span:nth-child(2) { animation-delay: 0.2s; }
.loading-dots span:nth-child(3) { animation-delay: 0.4s; }
@keyframes dot-bounce {
  0%,80%,100%{transform:scale(0.6);opacity:0.3}
  40%{transform:scale(1);opacity:1}
}

/* ── GRAPH ── */
#plot-area {
  width: 100%; height: 450px; border-radius: 2px;
  overflow: hidden; margin-top: 20px;
  border: 1px solid #1a1200;
}

/* ── HISTORY ── */
.hist-item {
  display: flex; align-items: center; gap: 16px;
  padding: 16px 20px;
  border-bottom: 1px solid #0e0900;
  transition: background 0.2s;
}
.hist-item:hover { background: rgba(212,175,55,0.03); }
.hist-time {
  font-family: 'Cormorant Garamond', serif;
  font-size: 0.85rem; color: var(--gold-900);
  min-width: 80px; font-style: italic;
}
.hist-text { font-size: 0.9rem; color: #888; }
.hist-dot { width: 4px; height: 4px; border-radius: 50%; background: var(--gold-700); min-width: 4px; }
.hist-empty {
  text-align: center; padding: 60px;
  font-family: 'Cormorant Garamond', serif;
  font-style: italic; color: #333; font-size: 1.2rem;
}

/* ── FILE INPUT ── */
.file-drop {
  border: 1px dashed #2a1e08;
  border-radius: 2px; padding: 40px;
  text-align: center; cursor: pointer;
  transition: all 0.3s; margin-bottom: 16px;
  position: relative;
}
.file-drop:hover { border-color: var(--gold-700); background: rgba(212,175,55,0.03); }
.file-drop input { position: absolute; inset: 0; opacity: 0; cursor: pointer; }
.file-drop-icon { font-size: 32px; margin-bottom: 10px; }
.file-drop-text { font-family: 'Cormorant Garamond', serif; font-style: italic; color: #555; }

/* ── SCROLLBAR ── */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: #000; }
::-webkit-scrollbar-thumb { background: var(--gold-900); border-radius: 2px; }

/* ── FOOTER LINE ── */
.section-footer {
  margin-top: 60px; padding-top: 20px;
  border-top: 1px solid #0e0900;
  display: flex; align-items: center; gap: 12px;
}
.footer-line { flex: 1; height: 1px; background: linear-gradient(90deg, var(--gold-900), transparent); }
.footer-text {
  font-family: 'Cinzel Decorative', serif;
  font-size: 0.55rem; letter-spacing: 0.3em; color: var(--gold-900);
}
</style>
</head>
<body>

<div class="bg-orbs">
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>
</div>

<!-- LOGIN -->
<div id="login-screen">
  <div class="login-wrapper">
    <div class="login-ornament">
      <div class="login-ornament-inner">∑</div>
    </div>
    <div class="login-card">
      <div class="login-title">MATH WITH ALI</div>
      <div class="login-subtitle">بوابة الرياضيات المتقدمة</div>

      <div class="field-group">
        <label class="field-label" id="lbl-email">البريد الإلكتروني</label>
        <input type="email" id="userEmail" class="field-input" placeholder="name@example.com">
      </div>
      <div class="field-group">
        <label class="field-label" id="lbl-pass">كلمة المرور</label>
        <input type="password" id="userPass" class="field-input" placeholder="••••••••">
      </div>
      <button class="btn-login" onclick="login()" id="login-btn">ENTER — دخول</button>
    </div>
  </div>
</div>

<!-- MAIN APP -->
<div id="main-app">
  <header>
    <div class="header-logo">
      <div class="logo-emblem">∑</div>
      <div>
        <div class="logo-text" id="logo-text-main">MATH WITH ALI</div>
        <div class="logo-sub" id="logo-sub-text">الرياضيات مع علي</div>
      </div>
    </div>
    <div class="header-right">
      <div class="user-badge">
        <div class="user-dot"></div>
        <div class="user-name" id="welcome-msg"></div>
      </div>
      <div class="lang-btn" onclick="toggleLang()" id="lang-btn">العربية</div>
    </div>
  </header>

  <!-- HOME -->
  <div id="home-view" style="padding:80px 60px;">
    <div class="hero">
      <div class="hero-title" data-ar="الرياضيات مع علي" data-en="Mathematics With Ali">الرياضيات مع علي</div>
      <div class="hero-subtitle" data-ar="منصتك الرياضية المتقدمة" data-en="Your Advanced Mathematics Platform">منصتك الرياضية المتقدمة</div>
      <div class="hero-divider">
        <div class="divider-line"></div>
        <div class="divider-diamond"></div>
        <div class="divider-line rev"></div>
      </div>
    </div>

    <div class="menu-grid">
      <div class="card" onclick="openSection('calc')">
        <div class="card-number">01</div>
        <span class="card-icon">🔢</span>
        <div class="card-title" data-ar="الحاسبة العلمية" data-en="Scientific Calculator">الحاسبة العلمية</div>
        <div class="card-desc" data-ar="حسابات متقدمة ومعقدة" data-en="Advanced Mathematical Computations">حسابات متقدمة ومعقدة</div>
        <div class="card-arrow">←</div>
      </div>
      <div class="card" onclick="openSection('graph')">
        <div class="card-number">02</div>
        <span class="card-icon">📈</span>
        <div class="card-title" data-ar="رسم الدوال" data-en="Graph Plotter">رسم الدوال</div>
        <div class="card-desc" data-ar="تمثيل بياني تفاعلي" data-en="Interactive Visual Graphing">تمثيل بياني تفاعلي</div>
        <div class="card-arrow">←</div>
      </div>
      <div class="card" onclick="openSection('ai')">
        <div class="card-number">03</div>
        <span class="card-icon">🤖</span>
        <div class="card-title" data-ar="الذكاء الاصطناعي" data-en="AI Math Solver">الذكاء الاصطناعي</div>
        <div class="card-desc" data-ar="تحليل عميق للمعادلات" data-en="Deep Equation Analysis">تحليل عميق للمعادلات</div>
        <div class="card-arrow">←</div>
      </div>
      <div class="card" onclick="openSection('history')">
        <div class="card-number">04</div>
        <span class="card-icon">📜</span>
        <div class="card-title" data-ar="سجل العمليات" data-en="Operation History">سجل العمليات</div>
        <div class="card-desc" data-ar="تاريخك الخاص والمحمي" data-en="Your Private Protected Log">تاريخك الخاص والمحمي</div>
        <div class="card-arrow">←</div>
      </div>
    </div>

    <div class="section-footer">
      <div class="footer-line"></div>
      <div class="footer-text">MATH WITH ALI — ADVANCED PLATFORM</div>
      <div class="footer-line" style="background:linear-gradient(90deg,transparent,var(--gold-900))"></div>
    </div>
  </div>

  <!-- CALCULATOR -->
  <div id="calc" class="section-view">
    <span class="back-btn" onclick="goHome()">← <span data-ar="عودة" data-en="Back">عودة</span></span>
    <div class="section-header">
      <div class="section-number">01 — CALCULATOR</div>
      <div class="section-title" data-ar="الحاسبة المتقدمة" data-en="Advanced Calculator">الحاسبة المتقدمة</div>
      <div class="section-line"></div>
    </div>
    <div class="panel">
      <input type="text" class="input-gold" id="calc-input" placeholder="sin(pi/2) * sqrt(25)  |  log(100)  |  integrate(x^2, x)">
      <div class="calc-display">
        <div class="calc-result" id="calc-res">—</div>
      </div>
      <button class="btn-primary" onclick="doCalc()">
        <span>✦</span>
        <span data-ar="احسب" data-en="Calculate">احسب</span>
      </button>
    </div>
  </div>

  <!-- GRAPH -->
  <div id="graph" class="section-view">
    <span class="back-btn" onclick="goHome()">← <span data-ar="عودة" data-en="Back">عودة</span></span>
    <div class="section-header">
      <div class="section-number">02 — GRAPH PLOTTER</div>
      <div class="section-title" data-ar="رسم الدوال البيانية" data-en="Mathematical Graphing">رسم الدوال البيانية</div>
      <div class="section-line"></div>
    </div>
    <div class="panel">
      <input type="text" class="input-gold" id="graph-input" placeholder="x^3 - 2*x  |  sin(x)  |  e^(-x^2)">
      <button class="btn-primary" onclick="doGraph()">
        <span>✦</span>
        <span data-ar="ارسم الدالة" data-en="Plot Function">ارسم الدالة</span>
      </button>
      <div id="plot-area"></div>
    </div>
  </div>

  <!-- AI -->
  <div id="ai" class="section-view">
    <span class="back-btn" onclick="goHome()">← <span data-ar="عودة" data-en="Back">عودة</span></span>
    <div class="section-header">
      <div class="section-number">03 — AI ENGINE</div>
      <div class="section-title" data-ar="محرك الذكاء الاصطناعي" data-en="AI Analysis Engine">محرك الذكاء الاصطناعي</div>
      <div class="section-line"></div>
    </div>
    <div class="panel">
      <div class="file-drop">
        <input type="file" accept="image/*" id="file-input">
        <div class="file-drop-icon">📷</div>
        <div class="file-drop-text" data-ar="أسقط صورة المعادلة هنا أو انقر للاختيار" data-en="Drop equation image here or click to select">أسقط صورة المعادلة هنا أو انقر للاختيار</div>
      </div>
      <textarea class="textarea-gold" id="text-eq" placeholder="أو اكتب المعادلة: ∫x² dx | d/dx(sin x) | ∑ من n=1 إلى ∞..."></textarea>
      <button class="btn-primary" onclick="aiSolve()">
        <span>✦</span>
        <span data-ar="تحليل عميق" data-en="Deep Analysis">تحليل عميق</span>
      </button>
      <div id="ai-res" class="ai-result"></div>
    </div>
  </div>

  <!-- HISTORY -->
  <div id="history" class="section-view">
    <span class="back-btn" onclick="goHome()">← <span data-ar="عودة" data-en="Back">عودة</span></span>
    <div class="section-header">
      <div class="section-number">04 — HISTORY</div>
      <div class="section-title" data-ar="سجل عملياتك" data-en="Your Operation Log">سجل عملياتك</div>
      <div class="section-line"></div>
    </div>
    <div class="panel" style="padding:0; overflow:hidden;">
      <div id="hist-list"></div>
    </div>
  </div>

</div><!-- end main-app -->

<script>
let currentLang = 'en';
let currentUser = "";

function login() {
  const email = document.getElementById('userEmail').value;
  if(email.includes('@')) {
    currentUser = email;
    document.getElementById('login-screen').style.display = 'none';
    document.getElementById('main-app').style.display = 'block';
    document.getElementById('welcome-msg').innerText = email.split('@')[0].toUpperCase();
    updateUI();
  } else {
    const card = document.querySelector('.login-card');
    card.style.borderColor = '#8B0000';
    card.style.boxShadow = '0 0 30px rgba(139,0,0,0.3)';
    setTimeout(() => {
      card.style.borderColor = 'var(--gold-700)';
      card.style.boxShadow = '';
    }, 1200);
  }
}

function toggleLang() {
  currentLang = currentLang === 'ar' ? 'en' : 'ar';
  document.documentElement.lang = currentLang;
  document.documentElement.dir = currentLang === 'ar' ? 'rtl' : 'ltr';
  updateUI();
}

function updateUI() {
  const btn = document.getElementById('lang-btn');
  btn.innerText = currentLang === 'ar' ? 'English' : 'العربية';

  document.querySelectorAll('[data-ar]').forEach(el => {
    const key = currentLang === 'ar' ? 'data-ar' : 'data-en';
    if(el.getAttribute(key)) el.innerText = el.getAttribute(key);
  });

  // RTL arrows
  document.querySelectorAll('.card-arrow').forEach(a => {
    a.innerText = currentLang === 'ar' ? '←' : '→';
  });

  // Section lines
  document.querySelectorAll('.section-line').forEach(l => {
    l.style.background = currentLang === 'ar'
      ? 'linear-gradient(90deg, var(--gold-700), transparent)'
      : 'linear-gradient(90deg, transparent, var(--gold-700))';
  });
}

function openSection(id) {
  document.getElementById('home-view').style.display = 'none';
  document.querySelectorAll('.section-view').forEach(s => s.style.display = 'none');
  const el = document.getElementById(id);
  el.style.display = 'block';
  if(id === 'history') renderHistory();
}

function goHome() {
  document.getElementById('home-view').style.display = 'block';
  document.querySelectorAll('.section-view').forEach(s => s.style.display = 'none');
}

function doCalc() {
  const val = document.getElementById('calc-input').value;
  const resEl = document.getElementById('calc-res');
  try {
    const res = math.evaluate(val);
    resEl.style.opacity = '0';
    setTimeout(() => {
      resEl.innerText = typeof res === 'number' ? parseFloat(res.toFixed(8)).toString() : res;
      resEl.style.opacity = '1';
      resEl.style.transition = 'opacity 0.4s';
    }, 200);
    saveData(`Calc: ${val} = ${res}`);
  } catch(e) {
    resEl.innerText = 'Error';
    resEl.style.color = '#8B0000';
    setTimeout(() => resEl.style.color = 'var(--gold-300)', 1500);
  }
}

function doGraph() {
  const expr = document.getElementById('graph-input').value;
  try {
    const xValues = math.range(-10, 10, 0.1).toArray();
    const yValues = xValues.map(x => {
      try { return math.evaluate(expr, {x}); }
      catch(e) { return null; }
    });
    const trace = {
      x: xValues, y: yValues, type: 'scatter', mode: 'lines',
      line: { color: '#D4AF37', width: 2.5 },
      name: `f(x) = ${expr}`
    };
    const layout = {
      paper_bgcolor: 'transparent',
      plot_bgcolor: 'rgba(0,0,0,0.4)',
      font: { color: '#776040', family: 'Cairo' },
      xaxis: { gridcolor: '#111', zerolinecolor: '#2a1e08', color: '#555' },
      yaxis: { gridcolor: '#111', zerolinecolor: '#2a1e08', color: '#555' },
      margin: { l: 40, r: 20, t: 20, b: 40 }
    };
    Plotly.newPlot('plot-area', [trace], layout, { responsive: true, displayModeBar: false });
    saveData(`Graph: f(x) = ${expr}`);
  } catch(e) { alert('Expression error'); }
}

function aiSolve() {
  const question = document.getElementById('text-eq').value;
  const resDiv = document.getElementById('ai-res');
  resDiv.className = 'ai-result active';
  resDiv.innerHTML = `<div class="loading-dots"><span></span><span></span><span></span></div>`;

  const apiMessages = [
    {
      role: "user",
      content: question
        ? `أنت مساعد رياضيات متقدم. حلل وأشرح هذه المعادلة خطوة بخطوة بشكل مفصل ودقيق، واذكر القوانين والمبرهنات المستخدمة، ثم أعط النتيجة النهائية. المعادلة: "${question}"`
        : `أنت مساعد رياضيات. قدم مثالاً على حل تكامل بخطوات تفصيلية، واذكر المبرهنات المستخدمة.`
    }
  ];

  fetch("https://api.anthropic.com/v1/messages", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      model: "claude-sonnet-4-20250514",
      max_tokens: 1000,
      messages: apiMessages
    })
  })
  .then(r => r.json())
  .then(data => {
    const text = data.content?.map(b => b.text || '').join('') || 'لا يوجد رد';
    // Format response
    const lines = text.split('\n').filter(l => l.trim());
    let html = '';
    let stepCount = 0;
    lines.forEach(line => {
      if(line.match(/^\d+\.|^-|^•|^خطوة|^Step/)) {
        stepCount++;
        html += `<div class="ai-step">
          <div class="ai-step-num">${String(stepCount).padStart(2,'0')}</div>
          <div class="ai-step-text">${line.replace(/^\d+\.\s*|-\s*|•\s*/,'')}</div>
        </div>`;
      }
    });
    if(!html) {
      html = `<div class="ai-step"><div class="ai-step-num">∑</div><div class="ai-step-text">${text}</div></div>`;
    }
    resDiv.innerHTML = html;
    saveData(`AI: ${(question || 'Analysis').substring(0,50)}`);
  })
  .catch(err => {
    resDiv.innerHTML = `<div class="ai-step">
      <div class="ai-step-num">!</div>
      <div class="ai-step-text" style="color:#8B0000">Connection error. Check API access.</div>
    </div>`;
  });
}

function saveData(msg) {
  let logs = JSON.parse(localStorage.getItem('logs_' + currentUser) || '[]');
  logs.push({ time: new Date().toLocaleTimeString(), msg });
  localStorage.setItem('logs_' + currentUser, JSON.stringify(logs));
}

function renderHistory() {
  const list = document.getElementById('hist-list');
  let logs = JSON.parse(localStorage.getItem('logs_' + currentUser) || '[]');
  if(!logs.length) {
    list.innerHTML = `<div class="hist-empty">لا توجد عمليات سابقة — No history yet</div>`;
    return;
  }
  list.innerHTML = [...logs].reverse().map(l => `
    <div class="hist-item">
      <div class="hist-time">${l.time}</div>
      <div class="hist-dot"></div>
      <div class="hist-text">${l.msg}</div>
    </div>
  `).join('');
}

// Enter key support
document.addEventListener('keydown', e => {
  if(e.key === 'Enter') {
    if(document.getElementById('calc').style.display === 'block') doCalc();
    if(document.getElementById('graph').style.display === 'block') doGraph();
  }
});

// Initial UI
updateUI();
</script>
</body>
</html>
