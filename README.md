<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Devansh Mishra — DevOps Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=VT323&display=swap" rel="stylesheet"/>
<style>
:root {
  --green: #00FF41;
  --cyan: #00FFFF;
  --blue: #0066FF;
  --dark-green: #003300;
  --darker: #000a00;
  --bg: #000000;
  --card-bg: rgba(0, 20, 0, 0.85);
  --border: rgba(0, 255, 65, 0.3);
  --glow-green: 0 0 10px #00FF41, 0 0 20px #00FF41, 0 0 40px rgba(0,255,65,0.4);
  --glow-cyan: 0 0 10px #00FFFF, 0 0 20px #00FFFF, 0 0 40px rgba(0,255,255,0.4);
  --font-mono: 'Share Tech Mono', monospace;
  --font-display: 'Orbitron', monospace;
  --font-retro: 'VT323', monospace;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--green);
  font-family: var(--font-mono);
  overflow-x: hidden;
  cursor: none;
}

/* ── CUSTOM CURSOR ── */
#cursor {
  position: fixed; width: 20px; height: 20px; z-index: 99999;
  pointer-events: none; transform: translate(-50%, -50%);
  transition: transform 0.1s ease;
}
#cursor::before {
  content: '';
  position: absolute; inset: 0;
  border: 2px solid var(--cyan);
  clip-path: polygon(0 0, 40% 0, 40% 40%, 0 40%);
  animation: cursorSpin 3s linear infinite;
}
#cursor::after {
  content: '';
  position: absolute; inset: 6px;
  background: var(--cyan);
  border-radius: 50%;
  box-shadow: var(--glow-cyan);
}
#cursor-trail {
  position: fixed; width: 8px; height: 8px;
  background: var(--green); border-radius: 50%;
  pointer-events: none; z-index: 99998;
  transform: translate(-50%, -50%);
  transition: all 0.15s ease;
  opacity: 0.6;
}
@keyframes cursorSpin { to { transform: rotate(360deg); } }

/* ── CANVAS ── */
#matrix-canvas {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 0; opacity: 0.12;
  pointer-events: none;
}

/* ── SCANLINES ── */
#scanlines {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%; z-index: 1;
  background: repeating-linear-gradient(
    0deg, transparent, transparent 2px,
    rgba(0,0,0,0.08) 2px, rgba(0,0,0,0.08) 4px
  );
  pointer-events: none;
}

/* ── CRT VIGNETTE ── */
#vignette {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%; z-index: 1;
  background: radial-gradient(ellipse at center,
    transparent 60%, rgba(0,0,0,0.7) 100%);
  pointer-events: none;
}

/* ── MAIN LAYOUT ── */
main {
  position: relative; z-index: 2;
  max-width: 1100px; margin: 0 auto;
  padding: 0 24px 80px;
}

/* ── BOOT SCREEN ── */
#boot-screen {
  position: fixed; inset: 0; z-index: 1000;
  background: #000; display: flex;
  align-items: center; justify-content: center;
  flex-direction: column; gap: 8px;
  font-family: var(--font-mono); font-size: 14px;
  transition: opacity 0.8s ease;
}
#boot-screen.hidden { opacity: 0; pointer-events: none; }
.boot-line { color: var(--green); opacity: 0; white-space: nowrap; }
.boot-line.show { animation: bootReveal 0.1s ease forwards; }
.boot-line.ok::before { content: '[ '; color: #666; }
.boot-line.ok::after { content: ' ]'; color: #666; }
.boot-line .ok-tag { color: var(--cyan); margin-left: 8px; }
@keyframes bootReveal { to { opacity: 1; } }

/* ── HERO ── */
#hero {
  min-height: 100vh; display: flex;
  flex-direction: column; align-items: center;
  justify-content: center; text-align: center;
  padding-top: 40px; gap: 16px;
}

.glitch-name {
  font-family: var(--font-display);
  font-size: clamp(36px, 7vw, 80px);
  font-weight: 900;
  color: var(--green);
  text-shadow: var(--glow-green);
  position: relative;
  letter-spacing: 0.08em;
  animation: glitchBase 4s infinite;
}
.glitch-name::before, .glitch-name::after {
  content: attr(data-text);
  position: absolute; top: 0; left: 0;
  width: 100%; height: 100%;
}
.glitch-name::before {
  color: var(--cyan);
  clip: rect(0,0,0,0);
  animation: glitch1 4s infinite;
  text-shadow: -3px 0 var(--cyan);
}
.glitch-name::after {
  color: #ff003c;
  clip: rect(0,0,0,0);
  animation: glitch2 4s infinite;
  text-shadow: 3px 0 #ff003c;
}
@keyframes glitchBase {
  0%,90%,100% { transform: none; }
  92% { transform: skewX(-1deg); }
  94% { transform: skewX(1deg); }
}
@keyframes glitch1 {
  0%,85%,100% { clip: rect(0,0,0,0); transform: none; }
  87% { clip: rect(20px, 9999px, 30px, 0); transform: translate(-3px); }
  89% { clip: rect(60px, 9999px, 70px, 0); transform: translate(3px); }
  91% { clip: rect(0,0,0,0); }
}
@keyframes glitch2 {
  0%,88%,100% { clip: rect(0,0,0,0); transform: none; }
  90% { clip: rect(40px, 9999px, 50px, 0); transform: translate(3px); }
  92% { clip: rect(10px, 9999px, 20px, 0); transform: translate(-3px); }
  94% { clip: rect(0,0,0,0); }
}

.hero-subtitle {
  font-family: var(--font-retro);
  font-size: clamp(18px, 3vw, 28px);
  color: var(--cyan);
  text-shadow: var(--glow-cyan);
  letter-spacing: 4px;
}

.typewriter-wrap {
  height: 28px; overflow: hidden;
  font-size: 16px; color: #00AA33;
  font-family: var(--font-mono);
}
#typewriter::after {
  content: '█';
  animation: blink 0.7s step-end infinite;
}
@keyframes blink { 50% { opacity: 0; } }

.hero-badges {
  display: flex; flex-wrap: wrap;
  gap: 10px; justify-content: center;
  margin-top: 12px;
}
.badge {
  padding: 6px 16px;
  border: 1px solid var(--border);
  background: rgba(0,255,65,0.05);
  font-family: var(--font-mono);
  font-size: 12px; color: var(--green);
  letter-spacing: 2px;
  transition: all 0.3s ease;
  position: relative; overflow: hidden;
  cursor: default;
}
.badge::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(90deg, transparent, rgba(0,255,65,0.15), transparent);
  transform: translateX(-100%);
  transition: transform 0.4s ease;
}
.badge:hover {
  border-color: var(--cyan);
  color: var(--cyan);
  box-shadow: var(--glow-cyan);
  transform: translateY(-2px);
}
.badge:hover::before { transform: translateX(100%); }

.scroll-indicator {
  margin-top: 40px;
  display: flex; flex-direction: column;
  align-items: center; gap: 8px;
  font-size: 11px; letter-spacing: 3px;
  color: #005500;
  animation: fadeUpDown 2s ease infinite;
}
.scroll-indicator::after {
  content: '▼'; font-size: 20px;
  color: var(--green);
}
@keyframes fadeUpDown {
  0%,100% { opacity: 0.4; transform: translateY(0); }
  50% { opacity: 1; transform: translateY(6px); }
}

/* ── SECTION HEADERS ── */
.section { margin-bottom: 60px; opacity: 0; transform: translateY(30px); transition: all 0.6s ease; }
.section.visible { opacity: 1; transform: translateY(0); }

.section-header {
  font-family: var(--font-mono);
  font-size: 13px; color: #005500;
  margin-bottom: 24px;
  display: flex; align-items: center; gap: 12px;
}
.section-header .cmd {
  color: var(--green);
  font-size: 16px;
  text-shadow: var(--glow-green);
}
.section-header::after {
  content: '';
  flex: 1; height: 1px;
  background: linear-gradient(90deg, var(--border), transparent);
}

/* ── WHOAMI CARD ── */
.identity-card {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 28px 32px;
  position: relative;
  backdrop-filter: blur(10px);
  transition: all 0.4s ease;
  overflow: hidden;
}
.identity-card::before {
  content: '';
  position: absolute; top: 0; left: 0;
  width: 4px; height: 100%;
  background: linear-gradient(180deg, var(--green), var(--cyan));
}
.identity-card::after {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(0,255,65,0.03) 0%, transparent 60%);
  pointer-events: none;
}
.identity-card:hover {
  border-color: var(--cyan);
  box-shadow: 0 0 30px rgba(0,255,255,0.15), inset 0 0 30px rgba(0,255,65,0.03);
  transform: translateY(-3px);
}
.identity-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px 40px;
  font-size: 14px;
}
.id-row { display: flex; gap: 12px; }
.id-key { color: var(--cyan); min-width: 110px; }
.id-val { color: var(--green); }
.status-bar {
  margin-top: 16px;
  padding-top: 16px;
  border-top: 1px solid var(--border);
  font-size: 13px;
}
.progress-track {
  display: inline-block;
  width: 160px; height: 12px;
  background: #001100;
  border: 1px solid #003300;
  vertical-align: middle;
  position: relative; overflow: hidden;
  margin: 0 8px;
}
.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--dark-green), var(--green));
  width: 0%;
  transition: width 2s ease;
  position: relative;
}
.progress-fill::after {
  content: '';
  position: absolute; top: 0; right: 0;
  width: 3px; height: 100%;
  background: var(--cyan);
  box-shadow: var(--glow-cyan);
}

/* ── SKILLS ── */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 16px;
}
.skill-category {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 20px;
  transition: all 0.4s ease;
  position: relative; overflow: hidden;
  backdrop-filter: blur(8px);
}
.skill-category::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--green), var(--cyan), transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
}
.skill-category:hover { border-color: rgba(0,255,65,0.6); transform: translateY(-4px); box-shadow: 0 8px 30px rgba(0,255,65,0.1); }
.skill-category:hover::before { opacity: 1; }
.skill-cat-title {
  font-size: 11px; letter-spacing: 3px;
  color: var(--cyan); margin-bottom: 14px;
  text-shadow: var(--glow-cyan);
}
.skill-item {
  display: flex; align-items: center;
  gap: 12px; margin-bottom: 12px;
}
.skill-name {
  font-size: 13px; min-width: 130px;
  color: var(--green);
}
.skill-bar-track {
  flex: 1; height: 6px;
  background: #001a00;
  border: 1px solid #002200;
  position: relative; overflow: hidden;
}
.skill-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #004400, var(--green));
  width: 0%;
  transition: width 1.5s cubic-bezier(0.4,0,0.2,1);
  position: relative;
}
.skill-bar-fill::after {
  content: '';
  position: absolute; top: 0; right: 0;
  width: 4px; height: 100%;
  background: var(--cyan);
  box-shadow: var(--glow-cyan);
  animation: barPulse 2s ease infinite;
}
@keyframes barPulse { 0%,100% { opacity: 1; } 50% { opacity: 0.3; } }
.skill-pct { font-size: 11px; color: #005500; min-width: 35px; text-align: right; }

/* ── PIPELINE DIAGRAM ── */
.pipeline-container {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 28px;
  font-family: var(--font-mono);
  font-size: 12px;
  overflow-x: auto;
  position: relative;
  backdrop-filter: blur(8px);
  transition: all 0.4s ease;
}
.pipeline-container:hover {
  border-color: rgba(0,255,65,0.6);
  box-shadow: 0 0 40px rgba(0,255,65,0.08);
}
.pipeline-title {
  text-align: center;
  font-family: var(--font-display);
  font-size: 11px; letter-spacing: 4px;
  color: var(--cyan); margin-bottom: 20px;
  text-shadow: var(--glow-cyan);
}
.pipeline-flow {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0;
  flex-wrap: wrap;
  margin-bottom: 24px;
}
.p-node {
  border: 1px solid var(--border);
  padding: 10px 14px;
  text-align: center;
  min-width: 100px;
  background: rgba(0,30,0,0.9);
  transition: all 0.3s ease;
  cursor: default;
  position: relative;
}
.p-node:hover {
  border-color: var(--cyan);
  background: rgba(0,50,0,0.9);
  box-shadow: var(--glow-cyan);
  transform: scale(1.05);
  z-index: 2;
}
.p-node-icon { font-size: 18px; display: block; margin-bottom: 4px; }
.p-node-label { font-size: 10px; color: var(--green); letter-spacing: 1px; }
.p-node-sub { font-size: 9px; color: #006600; }
.p-arrow {
  color: var(--green); font-size: 18px;
  padding: 0 4px;
  animation: arrowPulse 1.5s ease infinite;
}
@keyframes arrowPulse {
  0%,100% { color: var(--green); opacity: 1; }
  50% { color: var(--cyan); opacity: 0.6; }
}
.p-gates {
  display: flex; gap: 12px;
  justify-content: center;
  margin-top: 16px;
}
.p-gate {
  border: 1px solid #003300;
  padding: 8px 16px;
  font-size: 11px; color: #00AA33;
  display: flex; align-items: center; gap: 6px;
  transition: all 0.3s ease;
  cursor: default;
}
.p-gate:hover {
  border-color: var(--green);
  color: var(--green);
  box-shadow: var(--glow-green);
}
.p-gate .check { color: var(--cyan); }

/* ── PROJECT CARDS ── */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 20px;
}
.project-card {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 24px;
  position: relative; overflow: hidden;
  backdrop-filter: blur(8px);
  transition: all 0.4s cubic-bezier(0.4,0,0.2,1);
  cursor: default;
}
.project-card::before {
  content: '';
  position: absolute; top: 0; left: 0;
  width: 100%; height: 100%;
  background: linear-gradient(135deg, rgba(0,255,65,0.05) 0%, transparent 50%);
  opacity: 0;
  transition: opacity 0.4s ease;
}
.project-card::after {
  content: '';
  position: absolute; bottom: 0; left: 0;
  width: 0%; height: 2px;
  transition: width 0.4s ease;
}
.project-card.red::after { background: linear-gradient(90deg, #ff003c, var(--green)); }
.project-card.yellow::after { background: linear-gradient(90deg, #ffaa00, var(--green)); }
.project-card.green::after { background: linear-gradient(90deg, var(--green), var(--cyan)); }

.project-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 40px rgba(0,255,65,0.12);
}
.project-card:hover::before { opacity: 1; }
.project-card:hover::after { width: 100%; }
.project-card.red:hover { border-color: #ff003c; }
.project-card.yellow:hover { border-color: #ffaa00; }
.project-card.green:hover { border-color: var(--cyan); }

.project-status {
  font-size: 10px; letter-spacing: 3px;
  margin-bottom: 10px; display: flex;
  align-items: center; gap: 6px;
}
.status-dot {
  width: 8px; height: 8px; border-radius: 50%;
  animation: dotPulse 2s ease infinite;
}
.red .status-dot { background: #ff003c; box-shadow: 0 0 8px #ff003c; }
.yellow .status-dot { background: #ffaa00; box-shadow: 0 0 8px #ffaa00; }
.green .status-dot { background: var(--green); box-shadow: var(--glow-green); }
@keyframes dotPulse { 0%,100% { transform: scale(1); } 50% { transform: scale(1.3); } }

.project-title {
  font-family: var(--font-display);
  font-size: 13px; font-weight: 700;
  color: var(--green); margin-bottom: 10px;
  letter-spacing: 1px; line-height: 1.4;
}
.project-desc { font-size: 12px; color: #006600; line-height: 1.7; margin-bottom: 14px; }
.project-metrics {
  display: flex; flex-wrap: wrap; gap: 6px;
  margin-bottom: 14px;
}
.metric {
  font-size: 11px;
  padding: 3px 10px;
  background: rgba(0,255,65,0.06);
  border: 1px solid #003300;
  color: var(--cyan);
  transition: all 0.2s ease;
}
.metric:hover {
  background: rgba(0,255,255,0.1);
  border-color: var(--cyan);
}
.project-tags { display: flex; flex-wrap: wrap; gap: 5px; }
.tag {
  font-size: 10px; padding: 2px 8px;
  border: 1px solid #002200;
  color: #004400;
  transition: all 0.2s ease;
}
.tag:hover { border-color: var(--green); color: var(--green); }

/* ── EXPERIENCE ── */
.exp-item {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 24px 28px;
  margin-bottom: 16px;
  position: relative; overflow: hidden;
  backdrop-filter: blur(8px);
  transition: all 0.4s ease;
}
.exp-item::before {
  content: '';
  position: absolute; left: 0; top: 0;
  width: 3px; height: 0%;
  background: linear-gradient(180deg, var(--cyan), var(--green));
  transition: height 0.5s ease;
}
.exp-item:hover { border-color: rgba(0,255,65,0.5); transform: translateX(6px); }
.exp-item:hover::before { height: 100%; }

.exp-header { display: flex; justify-content: space-between; align-items: flex-start; flex-wrap: wrap; gap: 8px; margin-bottom: 12px; }
.exp-role { font-family: var(--font-display); font-size: 14px; color: var(--cyan); letter-spacing: 1px; }
.exp-company { font-size: 13px; color: var(--green); }
.exp-meta { font-size: 11px; color: #004400; text-align: right; }
.exp-list { list-style: none; }
.exp-list li {
  font-size: 13px; color: #007700;
  padding: 4px 0; padding-left: 20px;
  position: relative; line-height: 1.6;
}
.exp-list li::before {
  content: '├──'; position: absolute;
  left: 0; color: #003300; font-size: 11px;
}
.exp-list li:last-child::before { content: '└──'; }
.exp-list li span { color: var(--green); }

/* ── ACHIEVEMENTS ── */
.achievements-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 16px;
}
.achievement-card {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 20px;
  display: flex; align-items: center; gap: 16px;
  transition: all 0.4s ease;
  cursor: default; position: relative;
  overflow: hidden;
}
.achievement-card::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(0,255,65,0.0) 0%, rgba(0,255,255,0.04) 100%);
  opacity: 0; transition: opacity 0.3s ease;
}
.achievement-card:hover {
  border-color: var(--cyan);
  transform: translateY(-4px) scale(1.02);
  box-shadow: 0 8px 30px rgba(0,255,255,0.1);
}
.achievement-card:hover::before { opacity: 1; }
.ach-icon { font-size: 28px; flex-shrink: 0; }
.ach-title { font-size: 13px; color: var(--green); margin-bottom: 3px; }
.ach-year { font-size: 11px; color: var(--cyan); }

.cert-card {
  border: 1px solid #002200;
  background: rgba(0,10,0,0.7);
  padding: 14px 18px;
  display: flex; align-items: center; gap: 12px;
  transition: all 0.3s ease;
  cursor: default;
}
.cert-card:hover {
  border-color: var(--green);
  background: rgba(0,20,0,0.9);
  transform: translateX(4px);
}
.cert-icon { color: var(--cyan); font-size: 16px; }
.cert-text { font-size: 13px; color: #007700; }
.cert-issuer { font-size: 11px; color: #004400; }

/* ── STATS ── */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 16px;
}
.stat-card {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 20px;
  text-align: center;
  transition: all 0.4s ease;
  position: relative; overflow: hidden;
}
.stat-card::after {
  content: '';
  position: absolute; bottom: 0; left: 50%;
  transform: translateX(-50%);
  width: 0; height: 2px;
  background: var(--cyan);
  transition: width 0.4s ease;
}
.stat-card:hover {
  border-color: var(--cyan);
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0,255,255,0.1);
}
.stat-card:hover::after { width: 80%; }
.stat-number {
  font-family: var(--font-display);
  font-size: 36px; font-weight: 900;
  color: var(--green);
  text-shadow: var(--glow-green);
  line-height: 1;
}
.stat-label { font-size: 11px; color: #005500; letter-spacing: 2px; margin-top: 6px; }

/* ── CONTACT ── */
.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 14px;
}
.contact-card {
  border: 1px solid var(--border);
  background: var(--card-bg);
  padding: 18px 22px;
  display: flex; align-items: center; gap: 14px;
  text-decoration: none;
  transition: all 0.4s ease;
  position: relative; overflow: hidden;
}
.contact-card::before {
  content: '';
  position: absolute; left: 0; top: 0;
  width: 0; height: 100%;
  background: rgba(0,255,255,0.05);
  transition: width 0.4s ease;
}
.contact-card:hover {
  border-color: var(--cyan);
  transform: translateX(6px);
  box-shadow: var(--glow-cyan);
}
.contact-card:hover::before { width: 100%; }
.contact-icon { font-size: 22px; }
.contact-label { font-size: 11px; color: #005500; letter-spacing: 2px; }
.contact-value { font-size: 13px; color: var(--green); }

/* ── FOOTER ── */
footer {
  text-align: center; padding: 40px 0 60px;
  font-size: 12px; color: #003300;
  border-top: 1px solid #001100;
  position: relative; z-index: 2;
}
footer .footer-quote {
  font-family: var(--font-retro);
  font-size: 18px; color: #005500;
  margin-bottom: 10px;
}
footer .footer-sig {
  color: var(--green);
  text-shadow: var(--glow-green);
}

/* ── SCROLL REVEAL ── */
@keyframes revealUp {
  from { opacity: 0; transform: translateY(40px); }
  to { opacity: 1; transform: translateY(0); }
}

/* ── NAV ── */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 100; padding: 12px 32px;
  display: flex; align-items: center; justify-content: space-between;
  background: rgba(0,0,0,0.85);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid #001a00;
}
.nav-brand {
  font-family: var(--font-display);
  font-size: 13px; color: var(--green);
  letter-spacing: 3px;
  text-shadow: var(--glow-green);
}
.nav-links { display: flex; gap: 24px; }
.nav-links a {
  font-size: 11px; color: #005500;
  text-decoration: none; letter-spacing: 2px;
  transition: all 0.2s ease;
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute; bottom: -3px; left: 0;
  width: 0; height: 1px;
  background: var(--cyan);
  transition: width 0.3s ease;
}
.nav-links a:hover { color: var(--cyan); }
.nav-links a:hover::after { width: 100%; }

/* ── RESPONSIVE ── */
@media (max-width: 600px) {
  .identity-grid { grid-template-columns: 1fr; }
  .p-node { min-width: 70px; padding: 8px; }
  .p-node-label { font-size: 9px; }
  nav { padding: 10px 16px; }
  .nav-links { gap: 14px; }
}
</style>
</head>
<body>

<canvas id="matrix-canvas"></canvas>
<div id="scanlines"></div>
<div id="vignette"></div>
<div id="cursor"></div>
<div id="cursor-trail"></div>

<!-- BOOT SCREEN -->
<div id="boot-screen">
  <div style="font-family:'Orbitron',monospace;font-size:20px;color:#00FF41;margin-bottom:20px;text-shadow:0 0 20px #00FF41;">DEVANSH-OS v2.5</div>
  <div class="boot-line ok" id="b0">Loading kernel modules <span class="ok-tag">OK</span></div>
  <div class="boot-line ok" id="b1">Mounting cloud volumes (AWS/GCP/Azure) <span class="ok-tag">OK</span></div>
  <div class="boot-line ok" id="b2">Starting Kubernetes cluster (EKS) <span class="ok-tag">OK</span></div>
  <div class="boot-line ok" id="b3">Initialising CI/CD daemon (Jenkins + ArgoCD) <span class="ok-tag">OK</span></div>
  <div class="boot-line ok" id="b4">Loading security scanners (Trivy, SonarQube, OWASP) <span class="ok-tag">OK</span></div>
  <div class="boot-line ok" id="b5">Connecting observability stack (Prometheus + Grafana) <span class="ok-tag">OK</span></div>
  <div class="boot-line ok" id="b6">Spawning AI automation workflows (Temporal) <span class="ok-tag">OK</span></div>
  <div class="boot-line" id="b7" style="color:#00FFFF;margin-top:14px;font-size:16px;">All systems nominal. Welcome to the Matrix.</div>
</div>

<!-- NAV -->
<nav>
  <div class="nav-brand">DEV-COMETT</div>
  <div class="nav-links">
    <a href="#whoami">WHOAMI</a>
    <a href="#skills">SKILLS</a>
    <a href="#projects">PROJECTS</a>
    <a href="#experience">EXP</a>
    <a href="#contact">CONTACT</a>
  </div>
</nav>

<main>

  <!-- HERO -->
  <section id="hero">
    <div class="glitch-name" data-text="DEVANSH MISHRA">DEVANSH MISHRA</div>
    <div class="hero-subtitle">> DEVOPS ENGINEER // CLOUD NATIVE // DEVSECOPS</div>
    <div class="typewriter-wrap"><span id="typewriter"></span></div>
    <div class="hero-badges">
      <div class="badge">☁️ AWS · GCP · AZURE</div>
      <div class="badge">⎈ KUBERNETES + EKS</div>
      <div class="badge">🔐 DEVSECOPS</div>
      <div class="badge">⚙️ CI/CD · ARGOCD</div>
      <div class="badge">🤖 AI AUTOMATION</div>
      <div class="badge">📍 INDIA 🇮🇳</div>
    </div>
    <div class="scroll-indicator">SCROLL DOWN</div>
  </section>

  <!-- WHOAMI -->
  <section id="whoami" class="section">
    <div class="section-header">
      <span class="cmd">> cat /proc/identity</span>
    </div>
    <div class="identity-card">
      <div class="identity-grid">
        <div class="id-row"><span class="id-key">operator</span><span class="id-val">Devansh Mishra (@dev-comett)</span></div>
        <div class="id-row"><span class="id-key">clearance</span><span class="id-val">DevOps Engineer — Cloud Native</span></div>
        <div class="id-row"><span class="id-key">base</span><span class="id-val">India 🇮🇳</span></div>
        <div class="id-row"><span class="id-key">education</span><span class="id-val">B.Tech CSE · TMU (2021–2025)</span></div>
        <div class="id-row"><span class="id-key">mission_1</span><span class="id-val">Scale cloud-native microservices</span></div>
        <div class="id-row"><span class="id-key">mission_2</span><span class="id-val">Secure pipelines w/ DevSecOps</span></div>
        <div class="id-row"><span class="id-key">mission_3</span><span class="id-val">Automate everything possible</span></div>
        <div class="id-row"><span class="id-key">mission_4</span><span class="id-val">AI-assisted IaC workflows</span></div>
      </div>
      <div class="status-bar">
        current_load: <div class="progress-track"><div class="progress-fill" data-width="78"></div></div> 78% — MISSION ACTIVE
      </div>
    </div>
  </section>

  <!-- STATS -->
  <section class="section">
    <div class="section-header"><span class="cmd">> ./metrics --summary</span></div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-number" data-count="5000">0</div><div class="stat-label">RECORDS/DAY AUTOMATED</div></div>
      <div class="stat-card"><div class="stat-number" data-count="90">0</div><div class="stat-label">% CI/CD AUTOMATED</div></div>
      <div class="stat-card"><div class="stat-number" data-count="99">0</div><div class="stat-label">% SYSTEM RELIABILITY</div></div>
      <div class="stat-card"><div class="stat-number" data-count="3">0</div><div class="stat-label">SECURITY GATE LAYERS</div></div>
      <div class="stat-card"><div class="stat-number" data-count="80">0</div><div class="stat-label">% OPS REDUCTION</div></div>
      <div class="stat-card"><div class="stat-number" data-count="4">0</div><div class="stat-label">YEARS ENGINEERING</div></div>
    </div>
  </section>

  <!-- PIPELINE -->
  <section class="section">
    <div class="section-header"><span class="cmd">> ./pipeline --show-architecture</span></div>
    <div class="pipeline-container">
      <div class="pipeline-title">◈ PRODUCTION DEVSECOPS CI/CD — MERN ON AWS EKS ◈</div>
      <div class="pipeline-flow">
        <div class="p-node"><span class="p-node-icon">✍️</span><span class="p-node-label">CODE</span><span class="p-node-sub">Developer</span></div>
        <div class="p-arrow">──►</div>
        <div class="p-node"><span class="p-node-icon">🐙</span><span class="p-node-label">GITHUB</span><span class="p-node-sub">PR Trigger</span></div>
        <div class="p-arrow">──►</div>
        <div class="p-node"><span class="p-node-icon">⚙️</span><span class="p-node-label">JENKINS</span><span class="p-node-sub">CI Pipeline</span></div>
        <div class="p-arrow">──►</div>
        <div class="p-node"><span class="p-node-icon">🐳</span><span class="p-node-label">DOCKER</span><span class="p-node-sub">Build & Push</span></div>
        <div class="p-arrow">──►</div>
        <div class="p-node"><span class="p-node-icon">🔱</span><span class="p-node-label">ARGOCD</span><span class="p-node-sub">GitOps Sync</span></div>
        <div class="p-arrow">──►</div>
        <div class="p-node"><span class="p-node-icon">⎈</span><span class="p-node-label">EKS</span><span class="p-node-sub">Production</span></div>
      </div>
      <div class="p-gates">
        <div class="p-gate"><span class="check">✓</span> Trivy Container Scan</div>
        <div class="p-gate"><span class="check">✓</span> SonarQube Code Quality</div>
        <div class="p-gate"><span class="check">✓</span> OWASP Dependency Check</div>
        <div class="p-gate"><span class="check">✓</span> Prometheus + Grafana</div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills" class="section">
    <div class="section-header"><span class="cmd">> cat /etc/skills.conf</span></div>
    <div class="skills-grid">

      <div class="skill-category">
        <div class="skill-cat-title">☁️ CLOUD & IAC</div>
        <div class="skill-item"><span class="skill-name">AWS</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="92"></div></div><span class="skill-pct">92%</span></div>
        <div class="skill-item"><span class="skill-name">Terraform</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="85"></div></div><span class="skill-pct">85%</span></div>
        <div class="skill-item"><span class="skill-name">GCP</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="70"></div></div><span class="skill-pct">70%</span></div>
        <div class="skill-item"><span class="skill-name">Azure</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="65"></div></div><span class="skill-pct">65%</span></div>
      </div>

      <div class="skill-category">
        <div class="skill-cat-title">🐳 CONTAINERS & ORCHESTRATION</div>
        <div class="skill-item"><span class="skill-name">Docker</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="90"></div></div><span class="skill-pct">90%</span></div>
        <div class="skill-item"><span class="skill-name">Kubernetes</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="85"></div></div><span class="skill-pct">85%</span></div>
        <div class="skill-item"><span class="skill-name">Helm</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="80"></div></div><span class="skill-pct">80%</span></div>
        <div class="skill-item"><span class="skill-name">ArgoCD</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="82"></div></div><span class="skill-pct">82%</span></div>
      </div>

      <div class="skill-category">
        <div class="skill-cat-title">⚙️ CI/CD & GITOPS</div>
        <div class="skill-item"><span class="skill-name">Jenkins</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="88"></div></div><span class="skill-pct">88%</span></div>
        <div class="skill-item"><span class="skill-name">GitHub Actions</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="85"></div></div><span class="skill-pct">85%</span></div>
        <div class="skill-item"><span class="skill-name">GitLab CI</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="75"></div></div><span class="skill-pct">75%</span></div>
        <div class="skill-item"><span class="skill-name">GitOps</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="82"></div></div><span class="skill-pct">82%</span></div>
      </div>

      <div class="skill-category">
        <div class="skill-cat-title">🔐 SECURITY</div>
        <div class="skill-item"><span class="skill-name">SonarQube</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="82"></div></div><span class="skill-pct">82%</span></div>
        <div class="skill-item"><span class="skill-name">Trivy</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="80"></div></div><span class="skill-pct">80%</span></div>
        <div class="skill-item"><span class="skill-name">OWASP</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="78"></div></div><span class="skill-pct">78%</span></div>
        <div class="skill-item"><span class="skill-name">DevSecOps</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="85"></div></div><span class="skill-pct">85%</span></div>
      </div>

      <div class="skill-category">
        <div class="skill-cat-title">📊 OBSERVABILITY</div>
        <div class="skill-item"><span class="skill-name">Prometheus</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="80"></div></div><span class="skill-pct">80%</span></div>
        <div class="skill-item"><span class="skill-name">Grafana</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="78"></div></div><span class="skill-pct">78%</span></div>
      </div>

      <div class="skill-category">
        <div class="skill-cat-title">💻 LANGUAGES</div>
        <div class="skill-item"><span class="skill-name">Python</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="85"></div></div><span class="skill-pct">85%</span></div>
        <div class="skill-item"><span class="skill-name">Bash</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="88"></div></div><span class="skill-pct">88%</span></div>
        <div class="skill-item"><span class="skill-name">Groovy</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="72"></div></div><span class="skill-pct">72%</span></div>
        <div class="skill-item"><span class="skill-name">Java</span><div class="skill-bar-track"><div class="skill-bar-fill" data-width="68"></div></div><span class="skill-pct">68%</span></div>
      </div>

    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects" class="section">
    <div class="section-header"><span class="cmd">> ls -la ./projects/ --details</span></div>
    <div class="projects-grid">

      <div class="project-card red">
        <div class="project-status"><div class="status-dot"></div><span style="color:#ff6666">ACTIVE</span></div>
        <div class="project-title">PRODUCTION-GRADE DEVSECOPS CI/CD — AWS EKS</div>
        <div class="project-desc">Fully automated, secure CI/CD pipeline for MERN stack applications on AWS EKS with multi-layer security gates and full GitOps adoption.</div>
        <div class="project-metrics">
          <span class="metric">90%+ CI/CD Automated</span>
          <span class="metric">~80% Less Effort</span>
          <span class="metric">3 Security Gates</span>
        </div>
        <div class="project-tags">
          <span class="tag">AWS EKS</span><span class="tag">Jenkins</span><span class="tag">ArgoCD</span><span class="tag">Helm</span><span class="tag">SonarQube</span><span class="tag">Trivy</span><span class="tag">Prometheus</span><span class="tag">Grafana</span>
        </div>
      </div>

      <div class="project-card yellow">
        <div class="project-status"><div class="status-dot"></div><span style="color:#ffcc66">STABLE</span></div>
        <div class="project-title">AI-ASSISTED AUTOMATED IAC REVIEW PIPELINE</div>
        <div class="project-desc">AI-driven pipeline automating Terraform PR checks with LLM-based feedback and shift-left security via Terrascan static analysis.</div>
        <div class="project-metrics">
          <span class="metric">~50% Review Effort Saved</span>
          <span class="metric">LLM Auto-Feedback</span>
          <span class="metric">Shift-Left Security</span>
        </div>
        <div class="project-tags">
          <span class="tag">Terraform</span><span class="tag">GitHub Actions</span><span class="tag">Python</span><span class="tag">Terrascan</span><span class="tag">LLMs</span><span class="tag">DevSecOps</span>
        </div>
      </div>

      <div class="project-card green">
        <div class="project-status"><div class="status-dot"></div><span style="color:#00FF41">RUNNING</span></div>
        <div class="project-title">FAULT-TOLERANT AI AUTOMATION — TEMPORAL + DOCKER</div>
        <div class="project-desc">Reliable AI automation workflows with Temporal for retries, state persistence and self-healing Docker containers reducing failures and manual ops.</div>
        <div class="project-metrics">
          <span class="metric">+25% Stability</span>
          <span class="metric">~40% Less Manual Ops</span>
          <span class="metric">Self-Healing</span>
        </div>
        <div class="project-tags">
          <span class="tag">Python</span><span class="tag">Temporal</span><span class="tag">Docker</span><span class="tag">Agentic Workflows</span><span class="tag">LLMs</span>
        </div>
      </div>

    </div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience" class="section">
    <div class="section-header"><span class="cmd">> tail -f /var/log/experience.log</span></div>

    <div class="exp-item">
      <div class="exp-header">
        <div>
          <div class="exp-role">SWE INTERN</div>
          <div class="exp-company">National Technical Research Organisation (NTRO)</div>
        </div>
        <div class="exp-meta">📍 New Delhi, India<br>Jul 2025 – Oct 2025</div>
      </div>
      <ul class="exp-list">
        <li>Automated pipelines processing <span>5,000+ records/day</span> with <span>>99% reliability</span></li>
        <li>Reduced manual operations by <span>~80%</span> through automation enhancements</li>
        <li>Deployed & operated applications on cloud VMs — provisioning, config, monitoring</li>
        <li>Improved deployment reliability by <span>50%</span> via CI/CD improvements</li>
      </ul>
    </div>

    <div class="exp-item">
      <div class="exp-header">
        <div>
          <div class="exp-role">SWE INTERN</div>
          <div class="exp-company">Physics Wallah</div>
        </div>
        <div class="exp-meta">📍 Noida, India<br>Jun 2024 – Jul 2024</div>
      </div>
      <ul class="exp-list">
        <li>Built real-time URL security scanner processing <span>~500 req/day</span></li>
        <li>Integrated <span>VirusTotal</span> and <span>Google Safe Browsing APIs</span></li>
        <li>Enabled auditability via logging, persistence and replayable workflows</li>
        <li>Reduced manual effort by <span>~40%</span> via Streamlit automation interface</li>
      </ul>
    </div>
  </section>

  <!-- ACHIEVEMENTS -->
  <section class="section">
    <div class="section-header"><span class="cmd">> sudo cat /root/achievements.txt</span></div>
    <div class="achievements-grid" style="margin-bottom:20px">
      <div class="achievement-card"><div class="ach-icon">🏆</div><div><div class="ach-title">Smart India Hackathon — Grand Finalist</div><div class="ach-year">2022 & 2024</div></div></div>
      <div class="achievement-card"><div class="ach-icon">🥈</div><div><div class="ach-title">Yukti Innovation Challenge — Finalist</div><div class="ach-year">2023</div></div></div>
      <div class="achievement-card"><div class="ach-icon">🥇</div><div><div class="ach-title">IBM Project Contest — Winner</div><div class="ach-year">2024 & 2025</div></div></div>
    </div>
    <div style="display:flex;flex-direction:column;gap:10px">
      <div class="cert-card"><span class="cert-icon">📜</span><div><div class="cert-text">Google Cloud Platform Foundations</div><div class="cert-issuer">NPTEL Certification</div></div></div>
      <div class="cert-card"><span class="cert-icon">📜</span><div><div class="cert-text">Certified in Cybersecurity (CC)</div><div class="cert-issuer">ISC2 Certification</div></div></div>
      <div class="cert-card"><span class="cert-icon">📜</span><div><div class="cert-text">Agile Methodology</div><div class="cert-issuer">IBM Certification</div></div></div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" class="section">
    <div class="section-header"><span class="cmd">> ./contact.sh --open-channels</span></div>
    <div class="contact-grid">
      <a class="contact-card" href="https://linkedin.com/in/dev-ice" target="_blank">
        <div class="contact-icon">💼</div>
        <div><div class="contact-label">LINKEDIN</div><div class="contact-value">dev-ice</div></div>
      </a>
      <a class="contact-card" href="mailto:imdev411@gmail.com">
        <div class="contact-icon">📧</div>
        <div><div class="contact-label">EMAIL</div><div class="contact-value">imdev411@gmail.com</div></div>
      </a>
      <a class="contact-card" href="https://github.com/dev-comett" target="_blank">
        <div class="contact-icon">🐙</div>
        <div><div class="contact-label">GITHUB</div><div class="contact-value">dev-comett</div></div>
      </a>
      <a class="contact-card" href="tel:+918384831545">
        <div class="contact-icon">📱</div>
        <div><div class="contact-label">PHONE</div><div class="contact-value">+91 8384831545</div></div>
      </a>
    </div>
  </section>

</main>

<footer>
  <div class="footer-quote">> "The cloud is just someone else's computer. I make sure it never goes down."</div>
  <div style="margin-bottom:6px">— <span class="footer-sig">dev-comett</span></div>
  <div>[SESSION ACTIVE] [CONNECTION SECURE] █▒░</div>
</footer>

<script>
/* ── CURSOR ── */
const cursor = document.getElementById('cursor');
const trail = document.getElementById('cursor-trail');
let mx = 0, my = 0, tx = 0, ty = 0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; cursor.style.left = mx+'px'; cursor.style.top = my+'px'; });
setInterval(() => {
  tx += (mx - tx) * 0.15;
  ty += (my - ty) * 0.15;
  trail.style.left = tx+'px'; trail.style.top = ty+'px';
}, 16);

/* ── MATRIX RAIN ── */
const canvas = document.getElementById('matrix-canvas');
const ctx = canvas.getContext('2d');
let cols, drops;
const chars = 'アイウエオカキクケコサシスセソタチツテトナニヌネノ0123456789ABCDEF>_[]{}|/\\'.split('');

function initMatrix() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  cols = Math.floor(canvas.width / 18);
  drops = Array(cols).fill(1).map(() => Math.random() * -100);
}

function drawMatrix() {
  ctx.fillStyle = 'rgba(0,0,0,0.04)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  for (let i = 0; i < cols; i++) {
    const char = chars[Math.floor(Math.random() * chars.length)];
    const x = i * 18;
    const y = drops[i] * 18;
    // Color: mix of green and cyan
    const isCyan = Math.random() < 0.15;
    const brightness = Math.random();
    if (isCyan) {
      ctx.fillStyle = `rgba(0, ${Math.floor(180+brightness*75)}, ${Math.floor(180+brightness*75)}, ${0.6+brightness*0.4})`;
    } else {
      ctx.fillStyle = `rgba(0, ${Math.floor(180+brightness*75)}, ${Math.floor(30+brightness*30)}, ${0.5+brightness*0.5})`;
    }
    ctx.font = `${12 + Math.random()*4}px Share Tech Mono`;
    ctx.fillText(char, x, y);
    if (y > canvas.height && Math.random() > 0.975) drops[i] = 0;
    drops[i] += 0.4 + Math.random() * 0.3;
  }
}
initMatrix();
setInterval(drawMatrix, 40);
window.addEventListener('resize', initMatrix);

/* ── BOOT SEQUENCE ── */
const bootLines = document.querySelectorAll('.boot-line');
const bootScreen = document.getElementById('boot-screen');
let idx = 0;
function showNextBoot() {
  if (idx < bootLines.length) {
    bootLines[idx].classList.add('show');
    idx++;
    setTimeout(showNextBoot, idx === bootLines.length ? 600 : 260);
  } else {
    setTimeout(() => {
      bootScreen.classList.add('hidden');
      setTimeout(() => bootScreen.remove(), 800);
      startAnimations();
    }, 600);
  }
}
setTimeout(showNextBoot, 300);

/* ── TYPEWRITER ── */
const lines = [
  '> kubectl get pods --all-namespaces',
  '> terraform apply --auto-approve',
  '> docker build -t devansh:latest .',
  '> argocd app sync production',
  '> sudo deploy --env prod --force',
  '> Automating the world, one pipeline at a time...'
];
let li = 0, ci = 0, deleting = false;
const tw = document.getElementById('typewriter');
function type() {
  const current = lines[li];
  if (!deleting) {
    tw.textContent = current.slice(0, ci++);
    if (ci > current.length) { deleting = true; setTimeout(type, 1800); return; }
  } else {
    tw.textContent = current.slice(0, ci--);
    if (ci < 0) { deleting = false; li = (li+1) % lines.length; ci = 0; setTimeout(type, 400); return; }
  }
  setTimeout(type, deleting ? 30 : 60);
}

/* ── SCROLL REVEAL + ANIMATIONS ── */
function startAnimations() {
  type();
  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        // Animate skill bars
        e.target.querySelectorAll('.skill-bar-fill').forEach(bar => {
          setTimeout(() => { bar.style.width = bar.dataset.width + '%'; }, 200);
        });
        // Animate progress bar
        e.target.querySelectorAll('.progress-fill').forEach(bar => {
          setTimeout(() => { bar.style.width = bar.dataset.width + '%'; }, 400);
        });
        // Count up stats
        e.target.querySelectorAll('[data-count]').forEach(el => {
          const target = +el.dataset.count;
          let current = 0;
          const step = target / 60;
          const timer = setInterval(() => {
            current = Math.min(current + step, target);
            el.textContent = target >= 1000
              ? (current/1000).toFixed(1)+'K+'
              : Math.floor(current) + (target === 99 ? '%' : target === 90 ? '%+' : target === 80 ? '%' : '');
            if (current >= target) clearInterval(timer);
          }, 25);
        });
      }
    });
  }, { threshold: 0.15 });

  document.querySelectorAll('.section').forEach(s => observer.observe(s));
}

/* ── HOVER SPARK EFFECT ON CARDS ── */
document.querySelectorAll('.project-card, .skill-category, .stat-card').forEach(card => {
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    const x = ((e.clientX - rect.left) / rect.width) * 100;
    const y = ((e.clientY - rect.top) / rect.height) * 100;
    card.style.setProperty('--mx', x+'%');
    card.style.setProperty('--my', y+'%');
  });
});

/* ── GLITCH ON HOVER: NAME ── */
document.querySelector('.glitch-name').addEventListener('mouseenter', function() {
  this.style.animation = 'none';
  setTimeout(() => this.style.animation = '', 50);
});
</script>
</body>
</html>
