<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>LuaU Academy — Roblox Scripting Course</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;900&family=Exo+2:ital,wght@0,300;0,400;0,500;0,600;1,400&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
/* ============================================================
   CSS VARIABLES & RESET
   ============================================================ */
:root {
  --bg-primary:   #070a10;
  --bg-secondary: #0d1220;
  --bg-card:      #111827;
  --bg-card-hover:#161f35;
  --sidebar-bg:   #0a0f1e;
  --accent:       #00d4ff;
  --accent-dim:   rgba(0,212,255,0.15);
  --accent-glow:  rgba(0,212,255,0.4);
  --gold:         #ffc84a;
  --gold-dim:     rgba(255,200,74,0.15);
  --green:        #00e5a0;
  --green-dim:    rgba(0,229,160,0.15);
  --red:          #ff4d6d;
  --red-dim:      rgba(255,77,109,0.15);
  --purple:       #a78bfa;
  --purple-dim:   rgba(167,139,250,0.15);
  --text-primary: #e8edf8;
  --text-secondary:#8fa3c7;
  --text-muted:   #4a5a78;
  --border:       rgba(255,255,255,0.07);
  --border-accent:rgba(0,212,255,0.3);
  --radius:       12px;
  --radius-sm:    8px;
  --sidebar-w:    280px;
  --header-h:     64px;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  font-family: 'Exo 2', sans-serif;
  background: var(--bg-primary);
  color: var(--text-primary);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ============================================================
   BACKGROUND GRID TEXTURE
   ============================================================ */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image:
    linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
  background-size: 40px 40px;
  pointer-events: none;
  z-index: 0;
}

/* ============================================================
   HEADER
   ============================================================ */
#header {
  position: fixed;
  top: 0; left: 0; right: 0;
  height: var(--header-h);
  background: rgba(7,10,16,0.95);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  padding: 0 24px;
  gap: 16px;
  z-index: 100;
}

#header-logo {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.2rem;
  font-weight: 900;
  color: var(--accent);
  text-shadow: 0 0 20px var(--accent-glow);
  letter-spacing: 2px;
  white-space: nowrap;
}

#header-logo span { color: var(--gold); }

#header-progress-wrap {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 12px;
  max-width: 500px;
  margin: 0 auto;
}

#header-progress-label {
  font-size: 0.75rem;
  color: var(--text-secondary);
  white-space: nowrap;
  font-weight: 500;
}

#header-progress-bar {
  flex: 1;
  height: 6px;
  background: rgba(255,255,255,0.08);
  border-radius: 99px;
  overflow: hidden;
}

#header-progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--accent), var(--green));
  border-radius: 99px;
  transition: width 0.6s cubic-bezier(0.34,1.56,0.64,1);
  box-shadow: 0 0 10px var(--accent-glow);
}

#header-points {
  font-family: 'Orbitron', sans-serif;
  font-size: 0.85rem;
  font-weight: 700;
  color: var(--gold);
  text-shadow: 0 0 10px rgba(255,200,74,0.4);
  white-space: nowrap;
}

#hamburger {
  display: none;
  background: none;
  border: 1px solid var(--border);
  color: var(--text-primary);
  padding: 8px;
  border-radius: var(--radius-sm);
  cursor: pointer;
  font-size: 1.2rem;
  transition: border-color 0.2s;
}
#hamburger:hover { border-color: var(--accent); color: var(--accent); }

/* ============================================================
   LAYOUT
   ============================================================ */
#app {
  display: flex;
  margin-top: var(--header-h);
  min-height: calc(100vh - var(--header-h));
  position: relative;
  z-index: 1;
}

/* ============================================================
   SIDEBAR
   ============================================================ */
#sidebar {
  width: var(--sidebar-w);
  min-height: 100%;
  background: var(--sidebar-bg);
  border-right: 1px solid var(--border);
  position: fixed;
  top: var(--header-h);
  left: 0;
  bottom: 0;
  overflow-y: auto;
  overflow-x: hidden;
  z-index: 50;
  transition: transform 0.3s ease;
  padding-bottom: 40px;
}

#sidebar::-webkit-scrollbar { width: 4px; }
#sidebar::-webkit-scrollbar-track { background: transparent; }
#sidebar::-webkit-scrollbar-thumb { background: var(--border); border-radius: 99px; }

.sidebar-section-header {
  padding: 20px 20px 8px;
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--text-muted);
}

.sidebar-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 11px 20px;
  cursor: pointer;
  border-left: 3px solid transparent;
  transition: all 0.2s;
  position: relative;
  user-select: none;
}

.sidebar-item:hover:not(.locked) {
  background: rgba(0,212,255,0.05);
  border-left-color: rgba(0,212,255,0.3);
}

.sidebar-item.active {
  background: var(--accent-dim);
  border-left-color: var(--accent);
}

.sidebar-item.locked {
  opacity: 0.45;
  cursor: not-allowed;
}

.sidebar-item.completed {
  border-left-color: rgba(0,229,160,0.4);
}

.sidebar-item.special {
  background: linear-gradient(90deg, rgba(255,200,74,0.08), transparent);
}

.sidebar-item.special:hover:not(.locked) {
  background: linear-gradient(90deg, rgba(255,200,74,0.15), transparent);
  border-left-color: var(--gold);
}

.sidebar-item.special.active {
  background: linear-gradient(90deg, rgba(255,200,74,0.15), transparent);
  border-left-color: var(--gold);
}

.s-icon {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  font-weight: 700;
  flex-shrink: 0;
  font-family: 'Orbitron', sans-serif;
  transition: all 0.2s;
}

.s-icon.section-icon { background: var(--accent-dim); color: var(--accent); border: 1px solid var(--border-accent); }
.s-icon.special-icon { background: var(--gold-dim); color: var(--gold); border: 1px solid rgba(255,200,74,0.3); }
.s-icon.locked-icon { background: rgba(255,255,255,0.04); color: var(--text-muted); border: 1px solid var(--border); }
.s-icon.completed-icon { background: var(--green-dim); color: var(--green); border: 1px solid rgba(0,229,160,0.3); }
.s-icon.failed-icon { background: var(--red-dim); color: var(--red); border: 1px solid rgba(255,77,109,0.3); }

.s-text { flex: 1; min-width: 0; }
.s-title {
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--text-primary);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.s-subtitle {
  font-size: 0.68rem;
  color: var(--text-muted);
  margin-top: 2px;
}

.s-score-badge {
  font-family: 'Orbitron', sans-serif;
  font-size: 0.65rem;
  font-weight: 700;
  padding: 2px 7px;
  border-radius: 99px;
  flex-shrink: 0;
}
.s-score-badge.pass { background: var(--green-dim); color: var(--green); }
.s-score-badge.fail { background: var(--red-dim); color: var(--red); }

/* ============================================================
   MAIN CONTENT
   ============================================================ */
#main {
  margin-left: var(--sidebar-w);
  flex: 1;
  padding: 40px;
  max-width: 900px;
}

/* ============================================================
   DASHBOARD / HOME
   ============================================================ */
#dashboard {
  animation: fadeUp 0.5s ease;
}

.dash-hero {
  text-align: center;
  margin-bottom: 48px;
}

.dash-hero h1 {
  font-family: 'Orbitron', sans-serif;
  font-size: 2.8rem;
  font-weight: 900;
  background: linear-gradient(135deg, var(--accent), var(--purple), var(--gold));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 16px;
  line-height: 1.2;
}

.dash-hero p {
  font-size: 1.1rem;
  color: var(--text-secondary);
  max-width: 560px;
  margin: 0 auto;
  line-height: 1.7;
}

.stats-row {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-bottom: 40px;
}

.stat-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 24px;
  text-align: center;
  transition: all 0.3s;
}

.stat-card:hover {
  border-color: var(--border-accent);
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(0,212,255,0.1);
}

.stat-value {
  font-family: 'Orbitron', sans-serif;
  font-size: 2rem;
  font-weight: 900;
  color: var(--accent);
  text-shadow: 0 0 20px var(--accent-glow);
  display: block;
}

.stat-label {
  font-size: 0.75rem;
  color: var(--text-muted);
  margin-top: 6px;
  letter-spacing: 1px;
  text-transform: uppercase;
  font-weight: 600;
}

.section-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 16px;
}

.section-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 24px;
  cursor: pointer;
  transition: all 0.3s;
  position: relative;
  overflow: hidden;
}

.section-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--accent), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}

.section-card:hover:not(.card-locked) { 
  border-color: var(--border-accent);
  transform: translateY(-3px);
  box-shadow: 0 12px 40px rgba(0,212,255,0.12);
  background: var(--bg-card-hover);
}

.section-card:hover:not(.card-locked)::before { opacity: 1; }

.section-card.card-locked { opacity: 0.4; cursor: not-allowed; }
.section-card.card-completed { border-color: rgba(0,229,160,0.3); }
.section-card.card-completed::before { background: linear-gradient(90deg, var(--green), transparent); opacity: 1; }
.section-card.card-failed { border-color: rgba(255,77,109,0.3); }
.section-card.card-failed::before { background: linear-gradient(90deg, var(--red), transparent); opacity: 1; }
.section-card.card-special { border-color: rgba(255,200,74,0.2); }
.section-card.card-special::before { background: linear-gradient(90deg, var(--gold), transparent); opacity: 0.5; }

.card-number {
  font-family: 'Orbitron', sans-serif;
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 2px;
  color: var(--text-muted);
  text-transform: uppercase;
  margin-bottom: 10px;
}

.card-title {
  font-family: 'Orbitron', sans-serif;
  font-size: 0.9rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 10px;
  line-height: 1.4;
}

.card-desc {
  font-size: 0.78rem;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 16px;
}

.card-status {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 0.72rem;
  font-weight: 600;
  padding: 4px 10px;
  border-radius: 99px;
}

.card-status.unlocked { background: var(--accent-dim); color: var(--accent); }
.card-status.locked { background: rgba(255,255,255,0.05); color: var(--text-muted); }
.card-status.completed { background: var(--green-dim); color: var(--green); }
.card-status.failed { background: var(--red-dim); color: var(--red); }
.card-status.special { background: var(--gold-dim); color: var(--gold); }

/* ============================================================
   LESSON VIEW
   ============================================================ */
#lesson-view {
  display: none;
  animation: fadeUp 0.4s ease;
}

.breadcrumb {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.78rem;
  color: var(--text-muted);
  margin-bottom: 24px;
}
.breadcrumb span { cursor: pointer; transition: color 0.2s; }
.breadcrumb span:hover { color: var(--accent); }
.breadcrumb .sep { color: var(--text-muted); }
.breadcrumb .current { color: var(--text-secondary); cursor: default; }

.lesson-header {
  margin-bottom: 32px;
}

.lesson-tag {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: var(--accent);
  background: var(--accent-dim);
  border: 1px solid var(--border-accent);
  padding: 4px 12px;
  border-radius: 99px;
  margin-bottom: 16px;
}

.lesson-title {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.8rem;
  font-weight: 900;
  color: var(--text-primary);
  margin-bottom: 12px;
  line-height: 1.3;
}

.lesson-subtitle {
  font-size: 1rem;
  color: var(--text-secondary);
  line-height: 1.7;
}

/* TABS */
.tabs {
  display: flex;
  gap: 4px;
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 4px;
  margin-bottom: 32px;
}

.tab-btn {
  flex: 1;
  padding: 10px 16px;
  background: none;
  border: none;
  border-radius: var(--radius-sm);
  color: var(--text-secondary);
  font-family: 'Exo 2', sans-serif;
  font-size: 0.85rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}

.tab-btn:hover { color: var(--text-primary); background: rgba(255,255,255,0.04); }
.tab-btn.active { background: var(--accent-dim); color: var(--accent); border: 1px solid var(--border-accent); }
.tab-btn.tab-gold.active { background: var(--gold-dim); color: var(--gold); border-color: rgba(255,200,74,0.3); }
.tab-btn.tab-disabled { opacity: 0.35; cursor: not-allowed; }

/* LESSON CONTENT */
.lesson-content {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 32px;
  margin-bottom: 24px;
  line-height: 1.8;
  font-size: 0.95rem;
  color: var(--text-secondary);
}

.lesson-content h2 {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--accent);
  margin: 32px 0 16px;
  padding-bottom: 8px;
  border-bottom: 1px solid var(--border);
}

.lesson-content h2:first-child { margin-top: 0; }

.lesson-content h3 {
  font-size: 1rem;
  font-weight: 600;
  color: var(--text-primary);
  margin: 24px 0 10px;
}

.lesson-content p {
  margin-bottom: 16px;
}

.lesson-content ul, .lesson-content ol {
  margin: 12px 0 20px 24px;
}

.lesson-content li {
  margin-bottom: 8px;
}

.lesson-content strong { color: var(--text-primary); font-weight: 600; }
.lesson-content em { color: var(--purple); font-style: normal; }

.code-block {
  background: #0d1117;
  border: 1px solid rgba(0,212,255,0.15);
  border-radius: var(--radius-sm);
  padding: 20px;
  margin: 16px 0;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.85rem;
  line-height: 1.7;
  overflow-x: auto;
  position: relative;
}

.code-block::before {
  content: 'LuaU';
  position: absolute;
  top: 8px;
  right: 12px;
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 1px;
  color: var(--accent);
  opacity: 0.6;
  font-family: 'Orbitron', sans-serif;
}

.code-block .kw { color: #ff79c6; }
.code-block .fn { color: #50fa7b; }
.code-block .str { color: #f1fa8c; }
.code-block .num { color: #bd93f9; }
.code-block .com { color: #6272a4; font-style: italic; }
.code-block .var { color: #8be9fd; }
.code-block .op { color: #ff79c6; }

.info-box {
  border-radius: var(--radius-sm);
  padding: 16px 20px;
  margin: 20px 0;
  display: flex;
  gap: 14px;
  align-items: flex-start;
  font-size: 0.88rem;
}
.info-box.tip { background: var(--accent-dim); border-left: 3px solid var(--accent); }
.info-box.warning { background: var(--gold-dim); border-left: 3px solid var(--gold); }
.info-box.important { background: var(--purple-dim); border-left: 3px solid var(--purple); }
.info-box-icon { font-size: 1.2rem; flex-shrink: 0; margin-top: 1px; }
.info-box-text { color: var(--text-secondary); line-height: 1.6; }
.info-box-text strong { color: var(--text-primary); }

/* ASSIGNMENT */
.assignment-card {
  background: var(--bg-card);
  border: 1px solid rgba(167,139,250,0.25);
  border-radius: var(--radius);
  padding: 32px;
  margin-bottom: 24px;
}

.assignment-card h2 {
  font-family: 'Orbitron', sans-serif;
  font-size: 1rem;
  font-weight: 700;
  color: var(--purple);
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  gap: 10px;
}

.assignment-steps {
  counter-reset: step;
  list-style: none;
  margin: 0;
  padding: 0;
}

.assignment-steps li {
  counter-increment: step;
  display: flex;
  gap: 16px;
  margin-bottom: 20px;
  padding-bottom: 20px;
  border-bottom: 1px solid var(--border);
}

.assignment-steps li:last-child { border-bottom: none; margin-bottom: 0; padding-bottom: 0; }

.assignment-steps li::before {
  content: counter(step);
  width: 28px;
  height: 28px;
  background: var(--purple-dim);
  border: 1px solid rgba(167,139,250,0.3);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Orbitron', sans-serif;
  font-size: 0.72rem;
  font-weight: 700;
  color: var(--purple);
  flex-shrink: 0;
}

.assignment-steps li p { color: var(--text-secondary); line-height: 1.7; font-size: 0.92rem; }

/* QUIZ */
.quiz-wrap {
  display: none;
}

.quiz-header {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 24px 28px;
  margin-bottom: 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
}

.quiz-meta { display: flex; flex-direction: column; gap: 6px; }

.quiz-title {
  font-family: 'Orbitron', sans-serif;
  font-size: 1rem;
  font-weight: 700;
  color: var(--text-primary);
}

.quiz-info { font-size: 0.8rem; color: var(--text-secondary); }

.quiz-progress-dots {
  display: flex;
  gap: 6px;
}

.q-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--border);
  transition: all 0.3s;
}

.q-dot.answered { background: var(--accent); box-shadow: 0 0 6px var(--accent-glow); }
.q-dot.current { background: var(--gold); box-shadow: 0 0 6px rgba(255,200,74,0.4); transform: scale(1.3); }

.quiz-question-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 32px;
  margin-bottom: 16px;
  animation: fadeUp 0.3s ease;
}

.q-number {
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-bottom: 14px;
}

.q-text {
  font-size: 1.05rem;
  font-weight: 500;
  color: var(--text-primary);
  line-height: 1.6;
  margin-bottom: 24px;
}

.q-options {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.q-option {
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 14px 18px;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  gap: 14px;
  font-size: 0.9rem;
  color: var(--text-secondary);
  user-select: none;
}

.q-option:hover:not(.disabled) {
  border-color: var(--border-accent);
  background: var(--accent-dim);
  color: var(--text-primary);
}

.q-option.selected {
  border-color: var(--accent);
  background: var(--accent-dim);
  color: var(--accent);
}

.q-option.correct {
  border-color: var(--green);
  background: var(--green-dim);
  color: var(--green);
}

.q-option.wrong {
  border-color: var(--red);
  background: var(--red-dim);
  color: var(--red);
}

.q-option.disabled { cursor: default; }

.opt-letter {
  width: 28px;
  height: 28px;
  border-radius: 6px;
  background: rgba(255,255,255,0.06);
  border: 1px solid rgba(255,255,255,0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Orbitron', sans-serif;
  font-size: 0.7rem;
  font-weight: 700;
  flex-shrink: 0;
  transition: all 0.2s;
}

.q-option.selected .opt-letter { background: var(--accent-dim); border-color: var(--accent); color: var(--accent); }
.q-option.correct .opt-letter { background: var(--green-dim); border-color: var(--green); color: var(--green); }
.q-option.wrong .opt-letter { background: var(--red-dim); border-color: var(--red); color: var(--red); }

.quiz-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
}

/* BUTTONS */
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 24px;
  border-radius: var(--radius-sm);
  font-family: 'Exo 2', sans-serif;
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: all 0.2s;
  text-decoration: none;
}

.btn-primary {
  background: var(--accent);
  color: #060a14;
  box-shadow: 0 4px 20px rgba(0,212,255,0.3);
}
.btn-primary:hover { background: #00b8d9; box-shadow: 0 6px 28px rgba(0,212,255,0.45); transform: translateY(-1px); }

.btn-secondary {
  background: rgba(255,255,255,0.06);
  color: var(--text-secondary);
  border: 1px solid var(--border);
}
.btn-secondary:hover { background: rgba(255,255,255,0.1); color: var(--text-primary); border-color: rgba(255,255,255,0.15); }

.btn-gold {
  background: var(--gold);
  color: #1a0f00;
  box-shadow: 0 4px 20px rgba(255,200,74,0.3);
}
.btn-gold:hover { background: #e5b43f; transform: translateY(-1px); }

.btn-green {
  background: var(--green);
  color: #001a0f;
  box-shadow: 0 4px 20px rgba(0,229,160,0.3);
}
.btn-green:hover { background: #00cc8e; transform: translateY(-1px); }

.btn-red {
  background: var(--red);
  color: #fff;
  box-shadow: 0 4px 20px rgba(255,77,109,0.3);
}

.btn-outline {
  background: transparent;
  color: var(--accent);
  border: 1px solid var(--border-accent);
}
.btn-outline:hover { background: var(--accent-dim); }

.btn:disabled { opacity: 0.4; cursor: not-allowed; transform: none !important; }

/* QUIZ RESULT */
.quiz-result {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 48px 32px;
  text-align: center;
  animation: fadeUp 0.5s ease;
}

.result-icon {
  font-size: 4rem;
  margin-bottom: 16px;
  display: block;
  animation: bounceIn 0.6s cubic-bezier(0.34,1.56,0.64,1);
}

.result-score {
  font-family: 'Orbitron', sans-serif;
  font-size: 3.5rem;
  font-weight: 900;
  margin-bottom: 8px;
}

.result-score.pass { color: var(--green); text-shadow: 0 0 30px rgba(0,229,160,0.4); }
.result-score.fail { color: var(--red); text-shadow: 0 0 30px rgba(255,77,109,0.4); }

.result-label {
  font-size: 1.1rem;
  color: var(--text-secondary);
  margin-bottom: 8px;
}

.result-message {
  font-size: 0.9rem;
  color: var(--text-muted);
  margin-bottom: 32px;
  max-width: 400px;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.7;
}

.result-actions {
  display: flex;
  justify-content: center;
  gap: 12px;
  flex-wrap: wrap;
}

.result-breakdown {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin: 24px 0;
}

.breakdown-item {
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 16px;
  text-align: center;
}

.breakdown-val {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.4rem;
  font-weight: 900;
  margin-bottom: 4px;
}

.breakdown-key {
  font-size: 0.72rem;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* SECTION 9 GRADING */
.grading-rubric {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  overflow: hidden;
  margin-bottom: 24px;
}

.rubric-header {
  background: var(--bg-secondary);
  padding: 16px 24px;
  font-family: 'Orbitron', sans-serif;
  font-size: 0.85rem;
  font-weight: 700;
  color: var(--text-primary);
  border-bottom: 1px solid var(--border);
}

.rubric-row {
  display: flex;
  align-items: center;
  padding: 16px 24px;
  border-bottom: 1px solid var(--border);
  gap: 16px;
}

.rubric-row:last-child { border-bottom: none; }

.rubric-item { flex: 1; font-size: 0.88rem; color: var(--text-secondary); }
.rubric-pts {
  font-family: 'Orbitron', sans-serif;
  font-size: 0.9rem;
  font-weight: 700;
  color: var(--gold);
  white-space: nowrap;
}

.rubric-check {
  display: flex;
  gap: 6px;
}

.check-btn {
  padding: 5px 12px;
  border-radius: var(--radius-sm);
  font-size: 0.75rem;
  font-weight: 700;
  cursor: pointer;
  border: 1px solid;
  transition: all 0.2s;
  font-family: 'Exo 2', sans-serif;
}

.check-btn.yes-btn { border-color: rgba(0,229,160,0.4); color: var(--green); background: transparent; }
.check-btn.yes-btn:hover, .check-btn.yes-btn.selected { background: var(--green-dim); }
.check-btn.no-btn { border-color: rgba(255,77,109,0.4); color: var(--red); background: transparent; }
.check-btn.no-btn:hover, .check-btn.no-btn.selected { background: var(--red-dim); }

#final-proj-score {
  font-family: 'Orbitron', sans-serif;
  font-size: 2rem;
  font-weight: 900;
  color: var(--gold);
  text-align: center;
  margin: 24px 0;
}

/* TOAST */
.toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 16px 20px;
  font-size: 0.88rem;
  color: var(--text-primary);
  z-index: 9999;
  transform: translateY(100px);
  opacity: 0;
  transition: all 0.4s cubic-bezier(0.34,1.56,0.64,1);
  display: flex;
  align-items: center;
  gap: 12px;
  max-width: 320px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.4);
}

.toast.show { transform: translateY(0); opacity: 1; }
.toast.toast-success { border-color: rgba(0,229,160,0.4); }
.toast.toast-error { border-color: rgba(255,77,109,0.4); }
.toast.toast-gold { border-color: rgba(255,200,74,0.4); }

/* OVERLAY for locked sections */
.locked-overlay {
  text-align: center;
  padding: 80px 40px;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
}

.locked-overlay .lock-icon {
  font-size: 4rem;
  display: block;
  margin-bottom: 20px;
  opacity: 0.4;
}

.locked-overlay h2 {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.2rem;
  color: var(--text-muted);
  margin-bottom: 12px;
}

.locked-overlay p { color: var(--text-muted); font-size: 0.9rem; }

/* ANIMATIONS */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes bounceIn {
  from { transform: scale(0); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}

/* SCROLLBAR */
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: var(--border); border-radius: 99px; }

/* RESPONSIVE */
@media (max-width: 768px) {
  :root { --sidebar-w: 0px; }
  #sidebar {
    transform: translateX(-280px);
    width: 280px;
  }
  #sidebar.open { transform: translateX(0); }
  #main { margin-left: 0; padding: 20px 16px; }
  #hamburger { display: flex; align-items: center; }
  .stats-row { grid-template-columns: 1fr; }
  .dash-hero h1 { font-size: 1.8rem; }
  .result-breakdown { grid-template-columns: 1fr 1fr; }
  .quiz-header { flex-direction: column; align-items: flex-start; }
}

.sidebar-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.5);
  z-index: 40;
}
.sidebar-overlay.show { display: block; }

/* Final Exam special header */
.final-exam-banner {
  background: linear-gradient(135deg, rgba(255,200,74,0.1), rgba(255,77,109,0.1));
  border: 1px solid rgba(255,200,74,0.3);
  border-radius: var(--radius);
  padding: 24px 28px;
  margin-bottom: 28px;
  display: flex;
  align-items: center;
  gap: 20px;
}

.final-exam-banner .fex-icon { font-size: 3rem; }
.final-exam-banner h2 {
  font-family: 'Orbitron', sans-serif;
  font-size: 1.2rem;
  font-weight: 900;
  color: var(--gold);
  margin-bottom: 6px;
}
.final-exam-banner p { font-size: 0.85rem; color: var(--text-secondary); line-height: 1.6; }

/* Code inline */
code {
  background: rgba(0,212,255,0.1);
  border: 1px solid rgba(0,212,255,0.2);
  border-radius: 4px;
  padding: 2px 6px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.83em;
  color: var(--accent);
}
</style>
</head>
<body>

<!-- TOAST -->
<div class="toast" id="toast">
  <span id="toast-icon">✅</span>
  <span id="toast-text">Message</span>
</div>

<!-- SIDEBAR OVERLAY (mobile) -->
<div class="sidebar-overlay" id="sidebar-overlay" onclick="closeSidebar()"></div>

<!-- HEADER -->
<div id="header">
  <button id="hamburger" onclick="toggleSidebar()">☰</button>
  <div id="header-logo">LuaU<span>Academy</span></div>
  <div id="header-progress-wrap">
    <span id="header-progress-label">Progress</span>
    <div id="header-progress-bar"><div id="header-progress-fill" style="width:0%"></div></div>
    <span id="header-progress-pct">0%</span>
  </div>
  <div id="header-points">⭐ <span id="header-pts-val">0</span> pts</div>
</div>

<!-- SIDEBAR -->
<div id="sidebar">
  <div class="sidebar-section-header">Navigation</div>
  <div class="sidebar-item active" onclick="showDashboard()" id="nav-home">
    <div class="s-icon section-icon">🏠</div>
    <div class="s-text">
      <div class="s-title">Dashboard</div>
      <div class="s-subtitle">Overview & Progress</div>
    </div>
  </div>
  <div id="sidebar-nav-list"></div>
</div>

<!-- MAIN CONTENT -->
<div id="app">
  <div id="main">

    <!-- DASHBOARD -->
    <div id="dashboard">
      <div class="dash-hero">
        <h1>LuaU Scripting Academy</h1>
        <p>Master Roblox scripting from the ground up. Each section builds on the last — complete lessons, submit assignments, and pass quizzes to unlock the next chapter.</p>
      </div>
      <div class="stats-row" id="stats-row">
        <div class="stat-card">
          <span class="stat-value" id="stat-completed">0</span>
          <span class="stat-label">Sections Completed</span>
        </div>
        <div class="stat-card">
          <span class="stat-value" id="stat-points">0</span>
          <span class="stat-label">Total Points</span>
        </div>
        <div class="stat-card">
          <span class="stat-value" id="stat-avg">—</span>
          <span class="stat-label">Average Score</span>
        </div>
      </div>
      <div class="section-grid" id="section-grid"></div>
    </div>

    <!-- LESSON VIEW -->
    <div id="lesson-view">
      <div class="breadcrumb">
        <span onclick="showDashboard()">🏠 Dashboard</span>
        <span class="sep">›</span>
        <span class="current" id="breadcrumb-label">Section</span>
      </div>

      <div class="lesson-header">
        <div class="lesson-tag" id="lesson-tag">📘 Section</div>
        <div class="lesson-title" id="lesson-title">Title</div>
        <div class="lesson-subtitle" id="lesson-subtitle">Subtitle</div>
      </div>

      <div class="tabs" id="tabs-bar"></div>

      <div id="tab-content"></div>
    </div>

  </div>
</div>

<script>
// ============================================================
// COURSE DATA
// ============================================================
const COURSE = {
  sections: [
    // ─── SECTION 1 ───────────────────────────────────────────
    {
      id: 1,
      title: "Foundations of LuaU",
      subtitle: "Variables, data types, and your first script",
      icon: "01",
      lessons: [
        {
          title: "Variables — Storing Data in Your Script",
          content: `
<h2>What Is a Variable?</h2>
<p>At its most fundamental level, a <strong>variable</strong> is a named container that holds a piece of data. Imagine a box with a label on it. The label is your variable name, and whatever is inside the box is your variable's value. You can change what's inside the box at any time, and you can look at what's inside whenever you need to.</p>
<p>In LuaU (the scripting language used in Roblox), variables are how you store and manage every piece of information your game works with — a player's name, their score, whether a door is open or closed, how fast a car moves, and so on. Without variables, a script would be completely static and useless.</p>

<h2>Declaring Variables in LuaU</h2>
<p>In LuaU, you declare a variable using the <em>local</em> keyword. Here's the syntax:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">variableName</span> <span class="op">=</span> value
</div>

<p>The keyword <code>local</code> tells Lua that this variable is <strong>local in scope</strong> — meaning it can only be used within the block of code where it was declared. This is considered best practice in LuaU and prevents accidental interference between different parts of your code. Later we'll talk more about scope, but for now always start with <code>local</code>.</p>

<p>Let's look at some real examples:</p>

<div class="code-block">
<span class="com">-- Storing a player's name</span>
<span class="kw">local</span> <span class="var">playerName</span> <span class="op">=</span> <span class="str">"Alex"</span>

<span class="com">-- Storing a score</span>
<span class="kw">local</span> <span class="var">playerScore</span> <span class="op">=</span> 0

<span class="com">-- Storing whether a door is open</span>
<span class="kw">local</span> <span class="var">isDoorOpen</span> <span class="op">=</span> <span class="kw">false</span>

<span class="com">-- Storing a speed value</span>
<span class="kw">local</span> <span class="var">walkSpeed</span> <span class="op">=</span> 16
</div>

<h2>Naming Your Variables</h2>
<p>Variable names in LuaU follow specific rules:</p>
<ul>
  <li>Must start with a <strong>letter</strong> or an <strong>underscore</strong> (<code>_</code>)</li>
  <li>Can contain letters, numbers, and underscores</li>
  <li>Are <strong>case-sensitive</strong> — <code>playerScore</code> and <code>PlayerScore</code> are two completely different variables</li>
  <li>Cannot be a reserved keyword like <code>local</code>, <code>if</code>, <code>then</code>, <code>end</code>, <code>function</code>, etc.</li>
</ul>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>Naming Convention:</strong> In Roblox scripting, most developers use <em>camelCase</em> — start with a lowercase letter, and capitalize the first letter of each subsequent word. For example: <code>playerName</code>, <code>coinCount</code>, <code>maxSpeed</code>.</div>
</div>

<h2>Updating Variable Values</h2>
<p>Once a variable is declared, you can change its value at any time simply by assigning it a new one:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">score</span> <span class="op">=</span> <span class="num">0</span>
<span class="fn">print</span>(<span class="var">score</span>)    <span class="com">-- prints: 0</span>

<span class="var">score</span> <span class="op">=</span> <span class="num">50</span>      <span class="com">-- update the value</span>
<span class="fn">print</span>(<span class="var">score</span>)    <span class="com">-- prints: 50</span>

<span class="var">score</span> <span class="op">=</span> <span class="var">score</span> <span class="op">+</span> <span class="num">10</span>   <span class="com">-- increase by 10</span>
<span class="fn">print</span>(<span class="var">score</span>)         <span class="com">-- prints: 60</span>
</div>

<p>Notice on the last line — <code>score = score + 10</code>. The right side is evaluated <em>first</em>, so Lua reads the current value of <code>score</code> (which is 50), adds 10 to it, and stores the result (60) back into <code>score</code>. This is an extremely common pattern in game scripting.</p>

<h2>Multiple Variables at Once</h2>
<p>LuaU allows you to declare multiple variables in a single line using a comma:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">x</span>, <span class="var">y</span>, <span class="var">z</span> <span class="op">=</span> <span class="num">0</span>, <span class="num">5</span>, <span class="num">10</span>
<span class="fn">print</span>(<span class="var">x</span>, <span class="var">y</span>, <span class="var">z</span>)   <span class="com">-- prints: 0 5 10</span>
</div>

<p>This is handy when you have several related values that naturally belong together.</p>

<div class="info-box important">
  <div class="info-box-icon">⚠️</div>
  <div class="info-box-text"><strong>Global vs Local:</strong> If you write a variable WITHOUT the <code>local</code> keyword, it becomes a <em>global</em> variable — accessible from anywhere in all scripts. While globals sound powerful, they are dangerous and can cause hard-to-find bugs. Always use <code>local</code> unless you have a very specific reason not to.</div>
</div>
`
        },
        {
          title: "Data Types — What Kind of Data Can You Store?",
          content: `
<h2>Understanding Data Types</h2>
<p>Not all data is the same. The number <code>42</code> is fundamentally different from the text <code>"Hello"</code>, which is different from the value <code>true</code>. In programming, we call these distinctions <strong>data types</strong>. LuaU is a <em>dynamically typed</em> language, meaning you don't have to explicitly tell it what type a variable will hold — Lua figures it out automatically. But understanding types is still essential to writing correct code.</p>

<h2>The Core Data Types in LuaU</h2>

<h3>1. Number</h3>
<p>Numbers represent any numeric value — integers (whole numbers) and decimals alike. LuaU doesn't distinguish between them; it uses a single <em>number</em> type for both.</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">coins</span> <span class="op">=</span> <span class="num">100</span>
<span class="kw">local</span> <span class="var">speed</span> <span class="op">=</span> <span class="num">16.5</span>
<span class="kw">local</span> <span class="var">health</span> <span class="op">=</span> <span class="num">100</span>
<span class="kw">local</span> <span class="var">damage</span> <span class="op">=</span> <span class="num">-25</span>      <span class="com">-- negative numbers work too</span>
</div>

<p>You can perform all the arithmetic you'd expect on numbers:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">a</span> <span class="op">=</span> <span class="num">10</span>
<span class="kw">local</span> <span class="var">b</span> <span class="op">=</span> <span class="num">3</span>

<span class="fn">print</span>(<span class="var">a</span> <span class="op">+</span> <span class="var">b</span>)   <span class="com">-- 13  (addition)</span>
<span class="fn">print</span>(<span class="var">a</span> <span class="op">-</span> <span class="var">b</span>)   <span class="com">-- 7   (subtraction)</span>
<span class="fn">print</span>(<span class="var">a</span> <span class="op">*</span> <span class="var">b</span>)   <span class="com">-- 30  (multiplication)</span>
<span class="fn">print</span>(<span class="var">a</span> <span class="op">/</span> <span class="var">b</span>)   <span class="com">-- 3.333... (division)</span>
<span class="fn">print</span>(<span class="var">a</span> <span class="op">%</span> <span class="var">b</span>)   <span class="com">-- 1   (modulo: remainder)</span>
<span class="fn">print</span>(<span class="var">a</span> <span class="op">^</span> <span class="var">b</span>)   <span class="com">-- 1000 (exponentiation: 10 to the power of 3)</span>
</div>

<h3>2. String</h3>
<p>A <strong>string</strong> is a sequence of characters — text. Strings are always wrapped in quotation marks (either double <code>"</code> or single <code>'</code> — both work in Lua).</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">greeting</span> <span class="op">=</span> <span class="str">"Welcome to the game!"</span>
<span class="kw">local</span> <span class="var">username</span> <span class="op">=</span> <span class="str">'Player123'</span>
<span class="kw">local</span> <span class="var">empty</span> <span class="op">=</span> <span class="str">""</span>      <span class="com">-- this is a valid empty string</span>
</div>

<p>You can <strong>concatenate</strong> (join) strings using the <code>..</code> operator:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">first</span> <span class="op">=</span> <span class="str">"Hello, "</span>
<span class="kw">local</span> <span class="var">name</span>  <span class="op">=</span> <span class="str">"Roblox"</span>
<span class="kw">local</span> <span class="var">full</span>  <span class="op">=</span> <span class="var">first</span> <span class="op">..</span> <span class="var">name</span> <span class="op">..</span> <span class="str">"!"</span>
<span class="fn">print</span>(<span class="var">full</span>)   <span class="com">-- prints: Hello, Roblox!</span>
</div>

<p>You can convert a number to a string using <code>tostring()</code>, and a string to a number using <code>tonumber()</code>:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">num</span> <span class="op">=</span> <span class="num">42</span>
<span class="kw">local</span> <span class="var">str</span> <span class="op">=</span> <span class="fn">tostring</span>(<span class="var">num</span>)   <span class="com">-- "42"</span>
<span class="kw">local</span> <span class="var">back</span> <span class="op">=</span> <span class="fn">tonumber</span>(<span class="var">str</span>)  <span class="com">-- 42</span>
</div>

<h3>3. Boolean</h3>
<p>A <strong>boolean</strong> can only be one of two values: <code>true</code> or <code>false</code>. These are invaluable for logic — turning conditions on or off, storing states (is the player alive? is the chest open?), and controlling the flow of your code.</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">isAlive</span>     <span class="op">=</span> <span class="kw">true</span>
<span class="kw">local</span> <span class="var">hasKey</span>      <span class="op">=</span> <span class="kw">false</span>
<span class="kw">local</span> <span class="var">gameStarted</span> <span class="op">=</span> <span class="kw">false</span>
</div>

<h3>4. Nil</h3>
<p><strong>nil</strong> represents the <em>absence</em> of a value. If you declare a variable but don't assign it anything, it is <code>nil</code> by default. It's also used to explicitly "empty" a variable.</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">nothing</span>    <span class="com">-- automatically nil</span>
<span class="fn">print</span>(<span class="var">nothing</span>)   <span class="com">-- prints: nil</span>

<span class="kw">local</span> <span class="var">data</span> <span class="op">=</span> <span class="str">"some data"</span>
<span class="var">data</span> <span class="op">=</span> <span class="kw">nil</span>        <span class="com">-- erase the data</span>
</div>

<h3>5. Table (Preview)</h3>
<p>Tables are LuaU's most powerful data structure — they're like arrays and dictionaries combined. We won't go deep into tables in this section, but know they exist:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">inventory</span> <span class="op">=</span> {<span class="str">"Sword"</span>, <span class="str">"Shield"</span>, <span class="str">"Potion"</span>}
</div>

<h2>Checking the Type of a Variable</h2>
<p>LuaU provides a built-in function called <code>type()</code> that tells you what type a variable is:</p>

<div class="code-block">
<span class="fn">print</span>(<span class="fn">type</span>(<span class="str">"hello"</span>))   <span class="com">-- string</span>
<span class="fn">print</span>(<span class="fn">type</span>(<span class="num">42</span>))        <span class="com">-- number</span>
<span class="fn">print</span>(<span class="fn">type</span>(<span class="kw">true</span>))      <span class="com">-- boolean</span>
<span class="fn">print</span>(<span class="fn">type</span>(<span class="kw">nil</span>))       <span class="com">-- nil</span>
</div>

<div class="info-box warning">
  <div class="info-box-icon">⚠️</div>
  <div class="info-box-text"><strong>Type Errors:</strong> Mixing types carelessly causes bugs. For example, you can't concatenate a number and a string without converting: <code>"Score: " .. 10</code> actually works in standard Lua, but in LuaU (strict mode), you should use <code>tostring()</code> to be explicit: <code>"Score: " .. tostring(10)</code>.</div>
</div>
`
        },
        {
          title: "print() and Debugging Your Scripts",
          content: `
<h2>The Power of print()</h2>
<p>When you're learning to code, your most important tool is the ability to <em>see</em> what's happening inside your script. In Roblox, the <code>print()</code> function sends output to the <strong>Output window</strong> in Roblox Studio. It doesn't affect the game itself — players never see print messages — but it is absolutely essential for you, the developer, to understand what your code is doing at any given moment.</p>

<div class="code-block">
<span class="fn">print</span>(<span class="str">"Hello from my script!"</span>)
<span class="fn">print</span>(<span class="num">42</span>)
<span class="fn">print</span>(<span class="kw">true</span>)
<span class="fn">print</span>(<span class="kw">nil</span>)
</div>

<p>Each call to <code>print()</code> outputs on a new line in the Output window. You can print multiple values at once by separating them with commas — Lua will insert a tab character between each:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">name</span>  <span class="op">=</span> <span class="str">"Alex"</span>
<span class="kw">local</span> <span class="var">score</span> <span class="op">=</span> <span class="num">150</span>
<span class="fn">print</span>(<span class="str">"Player:"</span>, <span class="var">name</span>, <span class="str">"Score:"</span>, <span class="var">score</span>)
<span class="com">-- Output: Player:   Alex    Score:  150</span>
</div>

<h2>warn() and error()</h2>
<p>LuaU provides two additional output functions that are color-coded in the Output window for easy identification:</p>

<p><code>warn()</code> outputs a <strong>yellow warning message</strong>. Use it to flag non-critical issues that the developer should know about:</p>

<div class="code-block">
<span class="fn">warn</span>(<span class="str">"Player health is very low!"</span>)
</div>

<p><code>error()</code> outputs a <strong>red error message</strong> and stops the current script's execution at that point. Use it when something has gone seriously wrong:</p>

<div class="code-block">
<span class="fn">error</span>(<span class="str">"This function requires a number, not nil!"</span>)
</div>

<h2>Debugging: Finding and Fixing Problems</h2>
<p><strong>Debugging</strong> is the process of finding and correcting errors (called "bugs") in your code. As a Roblox developer, you'll spend a significant portion of your time debugging. Here are the core techniques:</p>

<h3>Technique 1: Print Everything</h3>
<p>When something isn't working, add <code>print()</code> statements to track what values are going where:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">health</span> <span class="op">=</span> <span class="num">100</span>
<span class="fn">print</span>(<span class="str">"Before damage, health ="</span>, <span class="var">health</span>)

<span class="var">health</span> <span class="op">=</span> <span class="var">health</span> <span class="op">-</span> <span class="num">25</span>
<span class="fn">print</span>(<span class="str">"After damage, health ="</span>, <span class="var">health</span>)
<span class="com">-- Lets you verify the math is correct</span>
</div>

<h3>Technique 2: Check if Code Runs at All</h3>
<p>Sometimes you're not sure if a section of code is even being reached. Put a print at the start to verify:</p>

<div class="code-block">
<span class="fn">print</span>(<span class="str">"=== Script started ==="</span>)

<span class="com">-- rest of your code...</span>
</div>

<h3>Technique 3: Track Variable States</h3>
<p>Bugs often come from variables having unexpected values. Print them at key checkpoints:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">speed</span> <span class="op">=</span> <span class="num">16</span>
<span class="fn">print</span>(<span class="str">"Speed type:"</span>, <span class="fn">type</span>(<span class="var">speed</span>), <span class="str">"Value:"</span>, <span class="var">speed</span>)
</div>

<h2>The Output Window in Roblox Studio</h2>
<p>To see your print statements in Roblox Studio:</p>
<ol>
  <li>Open Roblox Studio</li>
  <li>Click on the <strong>View</strong> menu in the top bar</li>
  <li>Select <strong>Output</strong> from the dropdown</li>
  <li>A panel will appear (usually at the bottom of the screen)</li>
  <li>Press <strong>Play</strong> and your print statements will appear there</li>
</ol>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>Clean up your prints:</strong> Once your script is working correctly, consider removing or commenting out your debug print statements. Leaving them in can clutter the Output and make it harder to spot real issues later. You can comment a line with <code>--</code> at the start.</div>
</div>

<h2>Putting It All Together</h2>

<div class="code-block">
<span class="com">-- Section 1 example: Variables + Types + print</span>
<span class="kw">local</span> <span class="var">playerName</span>  <span class="op">=</span> <span class="str">"StarRaider"</span>
<span class="kw">local</span> <span class="var">playerScore</span> <span class="op">=</span> <span class="num">0</span>
<span class="kw">local</span> <span class="var">isAlive</span>      <span class="op">=</span> <span class="kw">true</span>
<span class="kw">local</span> <span class="var">faction</span>      <span class="op">=</span> <span class="kw">nil</span>     <span class="com">-- not assigned yet</span>

<span class="fn">print</span>(<span class="str">"Player:"</span>,   <span class="var">playerName</span>)
<span class="fn">print</span>(<span class="str">"Score:"</span>,    <span class="var">playerScore</span>)
<span class="fn">print</span>(<span class="str">"Alive:"</span>,    <span class="var">isAlive</span>)
<span class="fn">print</span>(<span class="str">"Faction:"</span>,  <span class="var">faction</span>)

<span class="com">-- Update score</span>
<span class="var">playerScore</span> <span class="op">=</span> <span class="var">playerScore</span> <span class="op">+</span> <span class="num">50</span>
<span class="fn">print</span>(<span class="str">"New score:"</span>, <span class="var">playerScore</span>)

<span class="com">-- Build a message</span>
<span class="kw">local</span> <span class="var">message</span> <span class="op">=</span> <span class="str">"Welcome, "</span> <span class="op">..</span> <span class="var">playerName</span> <span class="op">..</span> <span class="str">"! Your score is: "</span> <span class="op">..</span> <span class="fn">tostring</span>(<span class="var">playerScore</span>)
<span class="fn">print</span>(<span class="var">message</span>)
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Your First Welcome Script",
        description: "Put your Section 1 knowledge to work. Build a script that introduces itself and greets a player.",
        steps: [
          "<p>Create a new <strong>Script</strong> inside <code>ServerScriptService</code> in Roblox Studio.</p>",
          "<p>Declare a <code>local</code> variable called <strong>playerName</strong> and assign it your own name as a string.</p>",
          "<p>Declare a <code>local</code> variable called <strong>playerScore</strong> and assign it the number <code>0</code>.</p>",
          "<p>Declare a <code>local</code> variable called <strong>isVIP</strong> and set it to <code>false</code>.</p>",
          "<p>Use <code>print()</code> to output each variable individually — one per line — with a label (e.g., <code>print(\"Name:\", playerName)</code>).</p>",
          "<p>Increase <code>playerScore</code> by <strong>100</strong>, then print a message like <code>\"Welcome, [name]! You now have [score] points.\"</code> using string concatenation.</p>",
          "<p>Use <code>type()</code> to print the data type of each of your three variables.</p>"
        ]
      },
      quiz: [
        {
          question: "What is a variable in LuaU?",
          options: ["A type of loop that repeats code", "A named container that stores a value", "A built-in function like print()", "A keyword that ends a code block"],
          correct: 1
        },
        {
          question: "Which of the following is an example of a string?",
          options: ["42", "true", '"Hello, World!"', "nil"],
          correct: 2
        },
        {
          question: "What does the print() function do in Roblox Studio?",
          options: ["Saves data to the player's device", "Sends text output to the Output window for debugging", "Creates a text label on screen for players to see", "Stops the script from running"],
          correct: 1
        },
        {
          question: "Which keyword should you use to declare a variable in LuaU as best practice?",
          options: ["var", "let", "local", "global"],
          correct: 2
        },
        {
          question: "What data type does the value false belong to?",
          options: ["String", "Number", "Boolean", "Nil"],
          correct: 2
        },
        {
          question: "What operator is used to join (concatenate) two strings in LuaU?",
          options: ["+", "&", "..", "++"],
          correct: 2
        }
      ]
    },

    // ─── SECTION 2 ───────────────────────────────────────────
    {
      id: 2,
      title: "Logic & Decisions",
      subtitle: "Control your script's behaviour with conditions",
      icon: "02",
      lessons: [
        {
          title: "if, elseif, and else — Branching Your Code",
          content: `
<h2>Making Decisions in Code</h2>
<p>Real games constantly make decisions: Is the player's health zero? Did they just pick up a coin? Is the door unlocked? Every one of these questions in LuaU is handled with <strong>conditional statements</strong>. The most fundamental is the <code>if</code> statement.</p>

<p>The structure looks like this:</p>

<div class="code-block">
<span class="kw">if</span> <em>condition</em> <span class="kw">then</span>
    <span class="com">-- code that runs if condition is true</span>
<span class="kw">end</span>
</div>

<p>LuaU evaluates the condition. If it's <code>true</code>, the code inside runs. If it's <code>false</code>, the block is skipped entirely. The <code>end</code> keyword marks where the if block finishes.</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">health</span> <span class="op">=</span> <span class="num">0</span>

<span class="kw">if</span> <span class="var">health</span> <span class="op">==</span> <span class="num">0</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"The player has died!"</span>)
<span class="kw">end</span>
</div>

<h2>Adding else — A Default Path</h2>
<p>Sometimes you want code to run if the condition is <em>not</em> met. That's what <code>else</code> is for:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">health</span> <span class="op">=</span> <span class="num">50</span>

<span class="kw">if</span> <span class="var">health</span> <span class="op">==</span> <span class="num">0</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"The player has died!"</span>)
<span class="kw">else</span>
    <span class="fn">print</span>(<span class="str">"The player is still alive."</span>)
<span class="kw">end</span>
</div>

<h2>elseif — Multiple Branches</h2>
<p><code>elseif</code> lets you check additional conditions after the first <code>if</code>. Only the <em>first</em> branch whose condition is true will execute — the rest are skipped:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">health</span> <span class="op">=</span> <span class="num">30</span>

<span class="kw">if</span> <span class="var">health</span> <span class="op">>=</span> <span class="num">75</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Healthy!"</span>)
<span class="kw">elseif</span> <span class="var">health</span> <span class="op">>=</span> <span class="num">25</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Caution: low health."</span>)
<span class="kw">elseif</span> <span class="var">health</span> <span class="op">></span> <span class="num">0</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Critical! Near death!"</span>)
<span class="kw">else</span>
    <span class="fn">print</span>(<span class="str">"Player is dead."</span>)
<span class="kw">end</span>
</div>

<p>You can chain as many <code>elseif</code> blocks as you need. The final <code>else</code> is optional — use it when you want a catch-all fallback.</p>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>Order matters!</strong> LuaU checks each condition <em>in order, from top to bottom</em>. Once a true condition is found, it runs that block and skips all the remaining ones. Place the most specific conditions first and the most general last.</div>
</div>

<h2>Nesting — Conditions Inside Conditions</h2>
<p>You can nest if statements inside each other to check multiple layers of conditions:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">hasKey</span>  <span class="op">=</span> <span class="kw">true</span>
<span class="kw">local</span> <span class="var">isAlive</span> <span class="op">=</span> <span class="kw">true</span>

<span class="kw">if</span> <span class="var">isAlive</span> <span class="kw">then</span>
    <span class="kw">if</span> <span class="var">hasKey</span> <span class="kw">then</span>
        <span class="fn">print</span>(<span class="str">"Player opens the door!"</span>)
    <span class="kw">else</span>
        <span class="fn">print</span>(<span class="str">"Player needs a key."</span>)
    <span class="kw">end</span>
<span class="kw">else</span>
    <span class="fn">print</span>(<span class="str">"Player is not alive."</span>)
<span class="kw">end</span>
</div>
`
        },
        {
          title: "Comparison Operators",
          content: `
<h2>Comparing Values</h2>
<p>Every <code>if</code> condition needs to evaluate to either <code>true</code> or <code>false</code>. The primary tool for creating these conditions is the <strong>comparison operator</strong>. LuaU provides six of them:</p>

<div class="code-block">
<span class="com">-- Equal to</span>
<span class="fn">print</span>(<span class="num">5</span> <span class="op">==</span> <span class="num">5</span>)    <span class="com">-- true</span>
<span class="fn">print</span>(<span class="num">5</span> <span class="op">==</span> <span class="num">6</span>)    <span class="com">-- false</span>

<span class="com">-- NOT equal to (LuaU uses ~= instead of !=)</span>
<span class="fn">print</span>(<span class="num">5</span> <span class="op">~=</span> <span class="num">6</span>)    <span class="com">-- true</span>

<span class="com">-- Greater than / Less than</span>
<span class="fn">print</span>(<span class="num">10</span> <span class="op">></span> <span class="num">5</span>)    <span class="com">-- true</span>
<span class="fn">print</span>(<span class="num">3</span>  <span class="op">&lt;</span> <span class="num">8</span>)    <span class="com">-- true</span>

<span class="com">-- Greater than or equal / Less than or equal</span>
<span class="fn">print</span>(<span class="num">5</span> <span class="op">>=</span> <span class="num">5</span>)    <span class="com">-- true</span>
<span class="fn">print</span>(<span class="num">4</span> <span class="op">&lt;=</span> <span class="num">5</span>)    <span class="com">-- true</span>
</div>

<div class="info-box warning">
  <div class="info-box-icon">⚠️</div>
  <div class="info-box-text"><strong>Common mistake:</strong> Don't confuse <code>=</code> (assignment) with <code>==</code> (comparison). Writing <code>if x = 5 then</code> is a syntax error. You must write <code>if x == 5 then</code>.</div>
</div>

<h2>Practical Examples</h2>

<div class="code-block">
<span class="kw">local</span> <span class="var">score</span>    <span class="op">=</span> <span class="num">80</span>
<span class="kw">local</span> <span class="var">passing</span>  <span class="op">=</span> <span class="num">75</span>
<span class="kw">local</span> <span class="var">username</span> <span class="op">=</span> <span class="str">"DevMaster"</span>

<span class="com">-- Number comparison</span>
<span class="kw">if</span> <span class="var">score</span> <span class="op">>=</span> <span class="var">passing</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Passed the test!"</span>)
<span class="kw">end</span>

<span class="com">-- String comparison</span>
<span class="kw">if</span> <span class="var">username</span> <span class="op">==</span> <span class="str">"Admin"</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Welcome, admin."</span>)
<span class="kw">else</span>
    <span class="fn">print</span>(<span class="str">"Welcome, player."</span>)
<span class="kw">end</span>
</div>
`
        },
        {
          title: "Boolean Logic — and, or, not",
          content: `
<h2>Combining Conditions</h2>
<p>Real game logic often requires <em>multiple</em> conditions to be true at once, or only <em>one</em> of several conditions. LuaU provides three <strong>logical operators</strong> to combine boolean values: <code>and</code>, <code>or</code>, and <code>not</code>.</p>

<h3>and — Both Must Be True</h3>
<div class="code-block">
<span class="kw">local</span> <span class="var">hasGun</span>  <span class="op">=</span> <span class="kw">true</span>
<span class="kw">local</span> <span class="var">hasBullets</span> <span class="op">=</span> <span class="kw">true</span>

<span class="kw">if</span> <span class="var">hasGun</span> <span class="kw">and</span> <span class="var">hasBullets</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Can shoot!"</span>)
<span class="kw">end</span>
</div>

<h3>or — At Least One Must Be True</h3>
<div class="code-block">
<span class="kw">local</span> <span class="var">isAdmin</span> <span class="op">=</span> <span class="kw">false</span>
<span class="kw">local</span> <span class="var">isMod</span>   <span class="op">=</span> <span class="kw">true</span>

<span class="kw">if</span> <span class="var">isAdmin</span> <span class="kw">or</span> <span class="var">isMod</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Has elevated permissions."</span>)
<span class="kw">end</span>
</div>

<h3>not — Flip the Truth Value</h3>
<div class="code-block">
<span class="kw">local</span> <span class="var">isDead</span> <span class="op">=</span> <span class="kw">false</span>

<span class="kw">if</span> <span class="kw">not</span> <span class="var">isDead</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Player is alive and active."</span>)
<span class="kw">end</span>
</div>

<h2>Combining All Three</h2>
<div class="code-block">
<span class="kw">local</span> <span class="var">level</span>    <span class="op">=</span> <span class="num">15</span>
<span class="kw">local</span> <span class="var">hasQuest</span> <span class="op">=</span> <span class="kw">true</span>
<span class="kw">local</span> <span class="var">isBanned</span> <span class="op">=</span> <span class="kw">false</span>

<span class="kw">if</span> (<span class="var">level</span> <span class="op">>=</span> <span class="num">10</span> <span class="kw">and</span> <span class="var">hasQuest</span>) <span class="kw">and</span> <span class="kw">not</span> <span class="var">isBanned</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"Player can enter the dungeon!"</span>)
<span class="kw">end</span>
</div>

<div class="info-box important">
  <div class="info-box-icon">🔮</div>
  <div class="info-box-text"><strong>Truthy and Falsy:</strong> In LuaU, only <code>false</code> and <code>nil</code> are "falsy" — everything else, including <code>0</code> and <code>""</code> (empty string), is considered "truthy". This is different from some other languages where 0 is false.</div>
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Number Checker Script",
        description: "Practice using conditions by building a script that classifies a number.",
        steps: [
          "<p>Declare a <code>local</code> variable called <strong>number</strong> and set it to any integer you choose.</p>",
          "<p>Using an <code>if / elseif / else</code> block, check if the number is greater than 10, equal to 10, or less than 10. Print a different message for each case.</p>",
          "<p>Add a second check: if the number is <em>even</em> (divisible by 2 with no remainder — use the <code>%</code> modulo operator), print <code>\"[number] is even\"</code>. Otherwise print <code>\"[number] is odd\"</code>.</p>",
          "<p>Add a third check: if the number is both greater than 5 <strong>and</strong> less than 20, print <code>\"Number is in the mid-range\"</code>. Use the <code>and</code> logical operator.</p>",
          "<p>Run your script in Roblox Studio and verify the output in the Output window.</p>"
        ]
      },
      quiz: [
        {
          question: "What does the == operator check in LuaU?",
          options: ["Assigns a value to a variable", "Checks if two values are equal", "Checks if two values are NOT equal", "Compares which value is larger"],
          correct: 1
        },
        {
          question: "What does an elseif block do?",
          options: ["Ends the if statement", "Creates a loop", "Checks an additional condition if all previous conditions were false", "Always runs regardless of conditions"],
          correct: 2
        },
        {
          question: "What operator means 'not equal to' in LuaU?",
          options: ["!=", "<>", "~=", "=/="],
          correct: 2
        },
        {
          question: "If condition A is false and condition B is true, what does 'A and B' evaluate to?",
          options: ["true", "false", "nil", "error"],
          correct: 1
        },
        {
          question: "Which values are considered 'falsy' in LuaU?",
          options: ["0 and empty string", "false and nil only", "false, nil, and 0", "nil only"],
          correct: 1
        }
      ]
    },

    // ─── SECTION 3 ───────────────────────────────────────────
    {
      id: 3,
      title: "Loops",
      subtitle: "Repeat actions automatically with while and for",
      icon: "03",
      lessons: [
        {
          title: "while Loops — Repeat While True",
          content: `
<h2>Why Loops?</h2>
<p>Imagine you need to move a platform back and forth every second, or count down from 10 to zero, or check every second whether a player has reached the finish line. Writing the same code over and over by hand is not just tedious — it's impossible for tasks of indefinite length. That's where <strong>loops</strong> come in. A loop lets you run a block of code repeatedly with minimal code.</p>

<h2>The while Loop</h2>
<p>A <code>while</code> loop keeps running its body as long as its condition remains <code>true</code>. The moment the condition becomes <code>false</code>, the loop stops and execution continues with the code after the loop.</p>

<div class="code-block">
<span class="kw">while</span> <em>condition</em> <span class="kw">do</span>
    <span class="com">-- code to repeat</span>
<span class="kw">end</span>
</div>

<p>Simple countdown example:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">count</span> <span class="op">=</span> <span class="num">5</span>

<span class="kw">while</span> <span class="var">count</span> <span class="op">></span> <span class="num">0</span> <span class="kw">do</span>
    <span class="fn">print</span>(<span class="str">"Countdown:"</span>, <span class="var">count</span>)
    <span class="var">count</span> <span class="op">=</span> <span class="var">count</span> <span class="op">-</span> <span class="num">1</span>
<span class="kw">end</span>

<span class="fn">print</span>(<span class="str">"Blast off!"</span>)
<span class="com">-- Output: Countdown: 5, 4, 3, 2, 1 then Blast off!</span>
</div>

<h2>Infinite Loops with task.wait()</h2>
<p>In Roblox, <strong>while true do</strong> is the standard pattern for game loops that run continuously — like a respawn loop or a constant health regeneration system. However, you <em>must</em> include a <code>task.wait()</code> call inside to prevent the loop from freezing the game:</p>

<div class="code-block">
<span class="kw">while</span> <span class="kw">true</span> <span class="kw">do</span>
    <span class="fn">print</span>(<span class="str">"Game is running..."</span>)
    <span class="fn">task.wait</span>(<span class="num">1</span>)   <span class="com">-- waits 1 second before repeating</span>
<span class="kw">end</span>
</div>

<div class="info-box warning">
  <div class="info-box-icon">⚠️</div>
  <div class="info-box-text"><strong>Infinite Loop Warning:</strong> A <code>while true do</code> loop without <code>task.wait()</code> will run millions of times per second and completely freeze Roblox Studio. Always use <code>task.wait()</code> inside any loop that's meant to repeat continuously.</div>
</div>

<h2>The break Keyword</h2>
<p>You can exit a while loop early using <code>break</code>:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">searching</span> <span class="op">=</span> <span class="kw">true</span>
<span class="kw">local</span> <span class="var">found</span>     <span class="op">=</span> <span class="kw">false</span>
<span class="kw">local</span> <span class="var">attempts</span>  <span class="op">=</span> <span class="num">0</span>

<span class="kw">while</span> <span class="var">searching</span> <span class="kw">do</span>
    <span class="var">attempts</span> <span class="op">=</span> <span class="var">attempts</span> <span class="op">+</span> <span class="num">1</span>
    <span class="fn">print</span>(<span class="str">"Attempt"</span>, <span class="var">attempts</span>)

    <span class="kw">if</span> <span class="var">attempts</span> <span class="op">>=</span> <span class="num">3</span> <span class="kw">then</span>
        <span class="var">found</span> <span class="op">=</span> <span class="kw">true</span>
        <span class="kw">break</span>   <span class="com">-- exits loop immediately</span>
    <span class="kw">end</span>
<span class="kw">end</span>

<span class="fn">print</span>(<span class="str">"Search complete. Found:"</span>, <span class="var">found</span>)
</div>
`
        },
        {
          title: "for Loops — Count-Controlled Repetition",
          content: `
<h2>The Numeric for Loop</h2>
<p>When you know <em>exactly</em> how many times you want to repeat something, a <code>for</code> loop is cleaner than a <code>while</code> loop. The numeric <code>for</code> loop automatically manages a counter variable for you:</p>

<div class="code-block">
<span class="kw">for</span> <span class="var">i</span> <span class="op">=</span> <em>start</em>, <em>end</em>, <em>step</em> <span class="kw">do</span>
    <span class="com">-- i counts from start to end, incrementing by step each time</span>
<span class="kw">end</span>
</div>

<p>The <code>step</code> is optional — it defaults to <code>1</code> if omitted.</p>

<div class="code-block">
<span class="com">-- Count 1 to 10</span>
<span class="kw">for</span> <span class="var">i</span> <span class="op">=</span> <span class="num">1</span>, <span class="num">10</span> <span class="kw">do</span>
    <span class="fn">print</span>(<span class="var">i</span>)
<span class="kw">end</span>

<span class="com">-- Count 0 to 100 in steps of 10</span>
<span class="kw">for</span> <span class="var">i</span> <span class="op">=</span> <span class="num">0</span>, <span class="num">100</span>, <span class="num">10</span> <span class="kw">do</span>
    <span class="fn">print</span>(<span class="var">i</span>)   <span class="com">-- 0, 10, 20, 30... 100</span>
<span class="kw">end</span>

<span class="com">-- Count DOWN from 10 to 1 using a negative step</span>
<span class="kw">for</span> <span class="var">i</span> <span class="op">=</span> <span class="num">10</span>, <span class="num">1</span>, <span class="op">-</span><span class="num">1</span> <span class="kw">do</span>
    <span class="fn">print</span>(<span class="var">i</span>)   <span class="com">-- 10, 9, 8... 1</span>
<span class="kw">end</span>
</div>

<h2>Generic for Loop — Iterating Tables</h2>
<p>LuaU also has a <strong>generic for</strong> loop that iterates over the contents of a table:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">fruits</span> <span class="op">=</span> {<span class="str">"Apple"</span>, <span class="str">"Banana"</span>, <span class="str">"Cherry"</span>}

<span class="kw">for</span> <span class="var">index</span>, <span class="var">fruit</span> <span class="kw">in</span> <span class="fn">ipairs</span>(<span class="var">fruits</span>) <span class="kw">do</span>
    <span class="fn">print</span>(<span class="var">index</span>, <span class="var">fruit</span>)
<span class="kw">end</span>
<span class="com">-- Output:  1  Apple   2  Banana   3  Cherry</span>
</div>

<h2>Combining Loops with Conditions</h2>
<div class="code-block">
<span class="com">-- Print only even numbers 1-20</span>
<span class="kw">for</span> <span class="var">i</span> <span class="op">=</span> <span class="num">1</span>, <span class="num">20</span> <span class="kw">do</span>
    <span class="kw">if</span> <span class="var">i</span> <span class="op">%</span> <span class="num">2</span> <span class="op">==</span> <span class="num">0</span> <span class="kw">then</span>
        <span class="fn">print</span>(<span class="var">i</span>, <span class="str">"is even"</span>)
    <span class="kw">end</span>
<span class="kw">end</span>
</div>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>When to use which:</strong> Use a <code>for</code> loop when you know the number of iterations in advance. Use a <code>while</code> loop when the number of iterations depends on a condition that changes during runtime.</div>
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Loop Counter",
        description: "Use both loop types to solve a number-printing challenge.",
        steps: [
          "<p>Using a <strong>for loop</strong>, print all numbers from 1 to 10, each on its own line.</p>",
          "<p>Modify the loop to also print whether each number is <strong>odd</strong> or <strong>even</strong> using an if statement inside the loop.</p>",
          "<p>Now use a <strong>while loop</strong> to count from 10 down to 1, printing each number. Include a print statement saying <code>\"Liftoff!\"</code> after the loop ends.</p>",
          "<p>Create a for loop from 1 to 100 that only prints numbers divisible by both 3 and 5 (hint: use the <code>%</code> operator and the <code>and</code> keyword).</p>",
          "<p>Test all loops in Roblox Studio and verify the output matches what you expect.</p>"
        ]
      },
      quiz: [
        {
          question: "What is the key difference between a while loop and a for loop?",
          options: ["While loops are faster", "A for loop uses a counter; a while loop runs while a condition is true", "For loops never end", "There is no difference"],
          correct: 1
        },
        {
          question: "When does a while loop stop executing?",
          options: ["After exactly 10 iterations", "When break is called OR the condition becomes false", "Immediately after running once", "After task.wait() is called"],
          correct: 1
        },
        {
          question: "What does this output? for i = 1, 3 do print(i) end",
          options: ["1 2", "1 2 3", "0 1 2 3", "3 2 1"],
          correct: 1
        },
        {
          question: "What keyword exits a loop immediately?",
          options: ["stop", "exit", "break", "end"],
          correct: 2
        },
        {
          question: "Why must you include task.wait() inside a while true do loop in Roblox?",
          options: ["It makes the loop run faster", "Without it, the loop runs millions of times per second and freezes the game", "It's optional — just a convention", "It saves memory"],
          correct: 1
        }
      ]
    },

    // ─── MIDTERM ───────────────────────────────────────────
    {
      id: "midterm",
      title: "Midterm Exam",
      subtitle: "Combining variables, logic, and loops",
      icon: "MT",
      isSpecial: true,
      lessons: [
        {
          title: "Midterm Review — Everything So Far",
          content: `
<h2>What the Midterm Covers</h2>
<p>The midterm combines everything from Sections 1–3. Before attempting the quiz, review these core concepts:</p>

<h3>Section 1: Foundations Review</h3>
<p>Variables are declared with <code>local</code>. Data types include <em>number</em>, <em>string</em>, <em>boolean</em>, and <em>nil</em>. Use <code>print()</code> to output values to the Output window. String concatenation uses <code>..</code>. The <code>type()</code> function returns the data type of any value.</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">name</span>  <span class="op">=</span> <span class="str">"Roblox"</span>     <span class="com">-- string</span>
<span class="kw">local</span> <span class="var">score</span> <span class="op">=</span> <span class="num">100</span>           <span class="com">-- number</span>
<span class="kw">local</span> <span class="var">alive</span> <span class="op">=</span> <span class="kw">true</span>          <span class="com">-- boolean</span>
<span class="fn">print</span>(<span class="str">"Hello, "</span> <span class="op">..</span> <span class="var">name</span>)
</div>

<h3>Section 2: Logic Review</h3>
<p>Use <code>if / elseif / else / end</code> to branch your code. Comparison operators: <code>==</code>, <code>~=</code>, <code>&lt;</code>, <code>&gt;</code>, <code>&lt;=</code>, <code>&gt;=</code>. Logical operators: <code>and</code>, <code>or</code>, <code>not</code>. Only <code>false</code> and <code>nil</code> are falsy.</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">x</span> <span class="op">=</span> <span class="num">15</span>
<span class="kw">if</span> <span class="var">x</span> <span class="op">></span> <span class="num">10</span> <span class="kw">and</span> <span class="var">x</span> <span class="op">&lt;</span> <span class="num">20</span> <span class="kw">then</span>
    <span class="fn">print</span>(<span class="str">"x is between 10 and 20"</span>)
<span class="kw">end</span>
</div>

<h3>Section 3: Loops Review</h3>
<p>For loops count automatically. While loops run while a condition is true. Use <code>break</code> to exit early. Always use <code>task.wait()</code> in infinite while loops to prevent freezing.</p>

<div class="code-block">
<span class="com">-- Combined example: loops + logic</span>
<span class="kw">for</span> <span class="var">i</span> <span class="op">=</span> <span class="num">1</span>, <span class="num">10</span> <span class="kw">do</span>
    <span class="kw">if</span> <span class="var">i</span> <span class="op">%</span> <span class="num">2</span> <span class="op">==</span> <span class="num">0</span> <span class="kw">then</span>
        <span class="fn">print</span>(<span class="var">i</span>, <span class="str">"is even"</span>)
    <span class="kw">else</span>
        <span class="fn">print</span>(<span class="var">i</span>, <span class="str">"is odd"</span>)
    <span class="kw">end</span>
<span class="kw">end</span>
</div>

<h2>Midterm Assignment</h2>
<p>Before taking the quiz, try this combined coding challenge in Roblox Studio:</p>
<ul>
  <li>Declare a variable <code>target</code> set to any number between 1–20</li>
  <li>Loop from 1 to 20 using a <code>for</code> loop</li>
  <li>Inside the loop: if the current number equals <code>target</code>, print <code>"Found it: [number]"</code> and break</li>
  <li>If the number is less than target, print <code>"[number]: too low"</code></li>
  <li>If the number is greater than target, print <code>"[number]: too high"</code> and break</li>
</ul>
`
        }
      ],
      assignment: {
        title: "Midterm Assignment: Combined Script",
        description: "Write a script that uses all three concepts from Sections 1–3.",
        steps: [
          "<p>Declare three variables: a <code>playerName</code> (string), a <code>startHealth</code> (number, set to 100), and an <code>isShielded</code> (boolean, set to true).</p>",
          "<p>Print all three variables with descriptive labels.</p>",
          "<p>Use an <code>if/elseif/else</code> block to print different messages based on <code>startHealth</code>: above 75 is \"Healthy\", 26–75 is \"Damaged\", 1–25 is \"Critical\", and 0 is \"Dead\".</p>",
          "<p>Write a <code>for</code> loop from 1 to 5 that simulates taking damage: each iteration reduces health by 15. Print health after each hit. If health drops below 0, set it to 0 and break the loop.</p>",
          "<p>After the loop, use a <code>while</code> loop to regenerate health by 10 each iteration (using task.wait(1) between each) until health reaches 100 again or you've regenerated 5 times — whichever comes first.</p>"
        ]
      },
      quiz: [
        {
          question: "What keyword declares a local variable in LuaU?",
          options: ["var", "local", "let", "dim"],
          correct: 1
        },
        {
          question: "What does this print?  local x = 5  if x > 3 then print(\"yes\") end",
          options: ["Nothing — condition is false", "yes", "no", "Error — missing else"],
          correct: 1
        },
        {
          question: "A for loop written as 'for i = 1, 5 do' runs how many times?",
          options: ["4 times", "6 times", "5 times", "1 time"],
          correct: 2
        },
        {
          question: "Which of these is a boolean value?",
          options: ['"false"', "0", "false", "nil"],
          correct: 2
        },
        {
          question: "What does the ~= operator check?",
          options: ["Greater than or equal", "Not equal to", "Equal to", "Less than"],
          correct: 1
        },
        {
          question: "What does 'while true do ... end' (with task.wait) do in Roblox?",
          options: ["Runs once then stops", "Creates a syntax error", "Runs indefinitely until break is called or the script is stopped", "Runs backwards"],
          correct: 2
        },
        {
          question: "What is string concatenation in LuaU?",
          options: ["Adding two numbers", "Joining two strings with the .. operator", "Comparing two strings", "Converting a string to a number"],
          correct: 1
        }
      ]
    },

    // ─── SECTION 4 ───────────────────────────────────────────
    {
      id: 4,
      title: "Functions",
      subtitle: "Reusable code blocks that make your scripts modular",
      icon: "04",
      lessons: [
        {
          title: "Creating Functions",
          content: `
<h2>What Is a Function?</h2>
<p>A <strong>function</strong> is a named, reusable block of code. Think of it like a machine: you feed it some input, it does some work, and it gives you back a result (or performs an action). Instead of writing the same code five times in different places, you write it <em>once</em> as a function and <em>call</em> it wherever you need it.</p>

<div class="code-block">
<span class="kw">local</span> <span class="kw">function</span> <span class="fn">greetPlayer</span>()
    <span class="fn">print</span>(<span class="str">"Welcome to the game!"</span>)
<span class="kw">end</span>

<span class="com">-- Call the function</span>
<span class="fn">greetPlayer</span>()   <span class="com">-- prints: Welcome to the game!</span>
<span class="fn">greetPlayer</span>()   <span class="com">-- prints again</span>
</div>

<p>Functions are defined using the <code>function</code> keyword, followed by the function name, parentheses <code>()</code>, the body of the function, and <code>end</code> to close it.</p>

<h2>Parameters — Passing Data In</h2>
<p><strong>Parameters</strong> are variables listed inside the parentheses of a function definition. They act as placeholders for values you'll pass when calling the function. This makes functions flexible and reusable:</p>

<div class="code-block">
<span class="kw">local</span> <span class="kw">function</span> <span class="fn">greetPlayer</span>(<span class="var">name</span>)
    <span class="fn">print</span>(<span class="str">"Welcome, "</span> <span class="op">..</span> <span class="var">name</span> <span class="op">..</span> <span class="str">"!"</span>)
<span class="kw">end</span>

<span class="fn">greetPlayer</span>(<span class="str">"Alex"</span>)     <span class="com">-- Welcome, Alex!</span>
<span class="fn">greetPlayer</span>(<span class="str">"Maria"</span>)    <span class="com">-- Welcome, Maria!</span>
<span class="fn">greetPlayer</span>(<span class="str">"Roblox"</span>)   <span class="com">-- Welcome, Roblox!</span>
</div>

<p>You can have multiple parameters, separated by commas:</p>

<div class="code-block">
<span class="kw">local</span> <span class="kw">function</span> <span class="fn">displayStats</span>(<span class="var">playerName</span>, <span class="var">score</span>, <span class="var">level</span>)
    <span class="fn">print</span>(<span class="var">playerName</span> <span class="op">..</span> <span class="str">" | Score: "</span> <span class="op">..</span> <span class="var">score</span> <span class="op">..</span> <span class="str">" | Level: "</span> <span class="op">..</span> <span class="var">level</span>)
<span class="kw">end</span>

<span class="fn">displayStats</span>(<span class="str">"Hero"</span>, <span class="num">500</span>, <span class="num">12</span>)
</div>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>Arguments vs Parameters:</strong> The variables listed in the function <em>definition</em> are called <em>parameters</em>. The actual values you pass when <em>calling</em> the function are called <em>arguments</em>. People often use these terms interchangeably — don't stress about it.</div>
</div>
`
        },
        {
          title: "Return Values",
          content: `
<h2>The return Statement</h2>
<p>Functions can <em>give back</em> a value using the <code>return</code> statement. This allows you to use the result of a function in other parts of your code:</p>

<div class="code-block">
<span class="kw">local</span> <span class="kw">function</span> <span class="fn">addNumbers</span>(<span class="var">a</span>, <span class="var">b</span>)
    <span class="kw">return</span> <span class="var">a</span> <span class="op">+</span> <span class="var">b</span>
<span class="kw">end</span>

<span class="kw">local</span> <span class="var">result</span> <span class="op">=</span> <span class="fn">addNumbers</span>(<span class="num">10</span>, <span class="num">25</span>)
<span class="fn">print</span>(<span class="var">result</span>)   <span class="com">-- 35</span>

<span class="com">-- You can also use it directly</span>
<span class="fn">print</span>(<span class="fn">addNumbers</span>(<span class="num">3</span>, <span class="num">7</span>))   <span class="com">-- 10</span>
</div>

<p>Functions can return multiple values:</p>

<div class="code-block">
<span class="kw">local</span> <span class="kw">function</span> <span class="fn">getMinMax</span>(<span class="var">a</span>, <span class="var">b</span>)
    <span class="kw">if</span> <span class="var">a</span> <span class="op">&lt;</span> <span class="var">b</span> <span class="kw">then</span>
        <span class="kw">return</span> <span class="var">a</span>, <span class="var">b</span>
    <span class="kw">else</span>
        <span class="kw">return</span> <span class="var">b</span>, <span class="var">a</span>
    <span class="kw">end</span>
<span class="kw">end</span>

<span class="kw">local</span> <span class="var">min</span>, <span class="var">max</span> <span class="op">=</span> <span class="fn">getMinMax</span>(<span class="num">15</span>, <span class="num">7</span>)
<span class="fn">print</span>(<span class="str">"Min:"</span>, <span class="var">min</span>, <span class="str">"Max:"</span>, <span class="var">max</span>)   <span class="com">-- Min: 7  Max: 15</span>
</div>

<h2>Practical Roblox Function Example</h2>

<div class="code-block">
<span class="kw">local</span> <span class="kw">function</span> <span class="fn">calculateDamage</span>(<span class="var">baseDamage</span>, <span class="var">isCritical</span>)
    <span class="kw">if</span> <span class="var">isCritical</span> <span class="kw">then</span>
        <span class="kw">return</span> <span class="var">baseDamage</span> <span class="op">*</span> <span class="num">2</span>
    <span class="kw">else</span>
        <span class="kw">return</span> <span class="var">baseDamage</span>
    <span class="kw">end</span>
<span class="kw">end</span>

<span class="kw">local</span> <span class="var">normalHit</span>   <span class="op">=</span> <span class="fn">calculateDamage</span>(<span class="num">20</span>, <span class="kw">false</span>)
<span class="kw">local</span> <span class="var">criticalHit</span> <span class="op">=</span> <span class="fn">calculateDamage</span>(<span class="num">20</span>, <span class="kw">true</span>)

<span class="fn">print</span>(<span class="str">"Normal:"</span>, <span class="var">normalHit</span>)     <span class="com">-- 20</span>
<span class="fn">print</span>(<span class="str">"Critical:"</span>, <span class="var">criticalHit</span>) <span class="com">-- 40</span>
</div>

<div class="info-box important">
  <div class="info-box-icon">🔮</div>
  <div class="info-box-text"><strong>return exits the function:</strong> As soon as Lua hits a <code>return</code> statement, it exits the function immediately — no more code in that function runs. This is useful for early exits when conditions are met.</div>
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Calculator Functions",
        description: "Create a set of mathematical functions and use them together.",
        steps: [
          "<p>Create a function called <code>add(a, b)</code> that returns the sum of two numbers.</p>",
          "<p>Create a function called <code>multiply(a, b)</code> that returns the product.</p>",
          "<p>Create a function called <code>isEven(n)</code> that returns <code>true</code> if the number is even, <code>false</code> otherwise.</p>",
          "<p>Create a function called <code>clamp(value, min, max)</code> that returns <code>value</code> if it's between min and max, <code>min</code> if it's below, or <code>max</code> if it's above.</p>",
          "<p>Call each function with test values and print the results to verify they work correctly.</p>"
        ]
      },
      quiz: [
        {
          question: "What is a function in LuaU?",
          options: ["A type of loop", "A named, reusable block of code", "A special variable type", "A comparison operator"],
          correct: 1
        },
        {
          question: "What does the return statement do in a function?",
          options: ["Prints a value", "Exits the script entirely", "Sends a value back to the caller and exits the function", "Creates a new variable"],
          correct: 2
        },
        {
          question: "What keyword is used to define a function in LuaU?",
          options: ["def", "func", "function", "method"],
          correct: 2
        },
        {
          question: "What are parameters in a function definition?",
          options: ["The values returned by the function", "Placeholder variables that receive argument values when called", "Global variables", "Loop counters"],
          correct: 1
        },
        {
          question: "Can a LuaU function return more than one value?",
          options: ["No, only one value can be returned", "Yes, multiple values separated by commas", "Only if they are the same type", "Only using tables"],
          correct: 1
        }
      ]
    },

    // ─── SECTION 5 ───────────────────────────────────────────
    {
      id: 5,
      title: "Roblox Basics",
      subtitle: "Scripts, Workspace, Parts, and Properties",
      icon: "05",
      lessons: [
        {
          title: "Scripts vs LocalScripts — Where Does Code Run?",
          content: `
<h2>The Roblox Client-Server Architecture</h2>
<p>Roblox games run on two sides simultaneously: the <strong>server</strong> and the <strong>client</strong>. Understanding this split is one of the most important concepts in Roblox development.</p>

<p>The <strong>server</strong> is Roblox's computer — it's the "source of truth" for the game. It manages game state, player data, physics, and everything that needs to be consistent for all players. The <strong>client</strong> is the player's computer or device — it renders graphics, handles input, and shows the UI.</p>

<h2>Script — Server-Side Code</h2>
<p>A <strong>Script</strong> (the plain Script object in Roblox Studio) runs on the <strong>server</strong>. It can:</p>
<ul>
  <li>Modify game state for all players</li>
  <li>Access and change player data</li>
  <li>Handle important game logic (awarding coins, managing teams)</li>
  <li>Read from and write to DataStores (saving data)</li>
</ul>

<p>Scripts are typically placed in <code>ServerScriptService</code> (the recommended location), or inside <code>Workspace</code> attached to objects.</p>

<div class="code-block">
<span class="com">-- Server Script: runs on Roblox's servers</span>
<span class="com">-- Place in ServerScriptService</span>

<span class="kw">local</span> <span class="var">Players</span> <span class="op">=</span> <span class="var">game</span>.<span class="var">Players</span>

<span class="var">Players</span>.<span class="var">PlayerAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="fn">print</span>(<span class="var">player</span>.<span class="var">Name</span> <span class="op">..</span> <span class="str">" joined the server!"</span>)
<span class="kw">end</span>)
</div>

<h2>LocalScript — Client-Side Code</h2>
<p>A <strong>LocalScript</strong> runs on each individual player's client. It's ideal for:</p>
<ul>
  <li>Handling GUI interactions (button clicks, menus)</li>
  <li>Processing player input (keyboard, mouse)</li>
  <li>Visual effects that don't need to be synced to other players</li>
  <li>Camera control and character animations</li>
</ul>

<p>LocalScripts must be in specific locations to run: <code>StarterPlayerScripts</code>, <code>StarterCharacterScripts</code>, <code>StarterGui</code>, or inside the player's character.</p>

<div class="info-box warning">
  <div class="info-box-icon">⚠️</div>
  <div class="info-box-text"><strong>Never trust the client:</strong> Because LocalScripts run on the player's machine, a hacker could potentially modify them. Never put important game logic (giving currency, verifying wins) in a LocalScript. That all goes server-side.</div>
</div>

<h2>ModuleScript — Shared Logic</h2>
<p>A <strong>ModuleScript</strong> is a special type that doesn't run on its own — it's required by other scripts to share functions and data across multiple scripts without duplicating code. We'll explore these more in advanced topics.</p>
`
        },
        {
          title: "Workspace, Parts, and Properties",
          content: `
<h2>The Workspace</h2>
<p><code>game.Workspace</code> (often just called <code>workspace</code>) is the 3D environment of your Roblox game — it's where all visible objects live. Think of it as the physical world that players see and interact with. Every Part, Model, Terrain, and character in the game is a descendant of the Workspace.</p>

<div class="code-block">
<span class="com">-- Access workspace from a Script</span>
<span class="kw">local</span> <span class="var">ws</span> <span class="op">=</span> <span class="var">game</span>.<span class="var">Workspace</span>
<span class="com">-- or simply:</span>
<span class="kw">local</span> <span class="var">ws</span> <span class="op">=</span> <span class="var">workspace</span>
</div>

<h2>Parts — The Building Blocks of Roblox</h2>
<p>A <strong>Part</strong> is the most fundamental 3D object in Roblox. It's a box (by default) with a set of properties you can modify to change its appearance and behaviour.</p>

<p>Key Part properties:</p>
<ul>
  <li><strong>Size</strong> — A Vector3 value: width, height, depth (e.g., <code>Vector3.new(4, 1, 4)</code>)</li>
  <li><strong>Position</strong> — A Vector3: where it is in the world</li>
  <li><strong>BrickColor</strong> — The color of the part (legacy system)</li>
  <li><strong>Color</strong> — A Color3 value (modern system)</li>
  <li><strong>Material</strong> — The surface material (Plastic, Wood, Concrete, etc.)</li>
  <li><strong>Anchored</strong> — If true, physics won't move it</li>
  <li><strong>CanCollide</strong> — If false, players pass through it</li>
  <li><strong>Transparency</strong> — 0 is opaque, 1 is invisible</li>
</ul>

<h2>Accessing Parts from Scripts</h2>

<div class="code-block">
<span class="com">-- Access a Part named "Platform" inside Workspace</span>
<span class="kw">local</span> <span class="var">platform</span> <span class="op">=</span> <span class="var">workspace</span>.<span class="var">Platform</span>
<span class="com">-- or using FindFirstChild (safer):</span>
<span class="kw">local</span> <span class="var">platform</span> <span class="op">=</span> <span class="var">workspace</span>:<span class="fn">FindFirstChild</span>(<span class="str">"Platform"</span>)

<span class="com">-- Modify properties</span>
<span class="var">platform</span>.<span class="var">BrickColor</span>   <span class="op">=</span> <span class="fn">BrickColor</span>.<span class="kw">new</span>(<span class="str">"Bright red"</span>)
<span class="var">platform</span>.<span class="var">Anchored</span>     <span class="op">=</span> <span class="kw">true</span>
<span class="var">platform</span>.<span class="var">Transparency</span> <span class="op">=</span> <span class="num">0.5</span>
<span class="var">platform</span>.<span class="var">Size</span>         <span class="op">=</span> <span class="fn">Vector3</span>.<span class="kw">new</span>(<span class="num">10</span>, <span class="num">1</span>, <span class="num">10</span>)
</div>

<h2>Creating Parts with Scripts</h2>
<p>You can create entirely new Parts at runtime using <code>Instance.new()</code>:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">newPart</span> <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"Part"</span>)
<span class="var">newPart</span>.<span class="var">Name</span>         <span class="op">=</span> <span class="str">"MyCoin"</span>
<span class="var">newPart</span>.<span class="var">Size</span>         <span class="op">=</span> <span class="fn">Vector3</span>.<span class="kw">new</span>(<span class="num">2</span>, <span class="num">2</span>, <span class="num">2</span>)
<span class="var">newPart</span>.<span class="var">Position</span>     <span class="op">=</span> <span class="fn">Vector3</span>.<span class="kw">new</span>(<span class="num">0</span>, <span class="num">5</span>, <span class="num">0</span>)
<span class="var">newPart</span>.<span class="var">BrickColor</span>   <span class="op">=</span> <span class="fn">BrickColor</span>.<span class="kw">new</span>(<span class="str">"Bright yellow"</span>)
<span class="var">newPart</span>.<span class="var">Anchored</span>     <span class="op">=</span> <span class="kw">true</span>
<span class="var">newPart</span>.<span class="var">Parent</span>       <span class="op">=</span> <span class="var">workspace</span>   <span class="com">-- add it to the world</span>

<span class="fn">print</span>(<span class="str">"Part created!"</span>)
</div>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>Set Parent last:</strong> When creating instances, always set all properties <em>before</em> setting the <code>Parent</code>. Once a Part is parented into Workspace, Roblox begins replicating it to clients. Setting properties before parenting is more efficient and avoids visual glitches.</div>
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Your First Roblox Script",
        description: "Create a part and a script that interact when the game starts.",
        steps: [
          "<p>Open Roblox Studio and create a new baseplate game.</p>",
          "<p>Add a <strong>Part</strong> to the Workspace. Rename it to <code>WelcomePad</code>. Make it large (e.g., 10×1×10) and bright green.</p>",
          "<p>Add a <strong>Script</strong> inside <code>ServerScriptService</code>.</p>",
          "<p>In the script, use <code>workspace:FindFirstChild(\"WelcomePad\")</code> to get a reference to your part.</p>",
          "<p>When the script runs, change the part's <code>BrickColor</code> to bright blue, set its <code>Transparency</code> to 0.3, and print <code>\"Game started! WelcomePad ready.\"</code>.</p>",
          "<p>Play the game and verify the part changes colour and the message appears in Output.</p>"
        ]
      },
      quiz: [
        {
          question: "Where does a regular Script run in Roblox?",
          options: ["On the player's computer (client-side)", "On Roblox's servers (server-side)", "On both client and server simultaneously", "Nowhere — it's just stored"],
          correct: 1
        },
        {
          question: "What is workspace in Roblox?",
          options: ["A folder where scripts are stored", "The 3D environment container holding all visible game objects", "A type of event system", "A GUI container"],
          correct: 1
        },
        {
          question: "What is the difference between a Script and a LocalScript?",
          options: ["No difference — they work the same", "Scripts run server-side; LocalScripts run on each player's client", "LocalScripts run on the server", "Scripts can only print text"],
          correct: 1
        },
        {
          question: "Which Instance.new() call correctly creates a Part?",
          options: ['Instance.new("Block")', 'Instance.new("Part")', 'Instance.new("Object")', 'Part.new()'],
          correct: 1
        },
        {
          question: "What does setting a Part's Anchored property to true do?",
          options: ["Makes it invisible", "Prevents physics from moving it", "Allows players to walk through it", "Deletes it after 5 seconds"],
          correct: 1
        }
      ]
    },

    // ─── SECTION 6 ───────────────────────────────────────────
    {
      id: 6,
      title: "Events",
      subtitle: "Respond to things that happen in your game",
      icon: "06",
      lessons: [
        {
          title: "Understanding Events in Roblox",
          content: `
<h2>What Is an Event?</h2>
<p>Roblox is an event-driven environment. Almost everything that happens in the game — a player joining, a part being touched, a button being clicked, a character dying — fires an <strong>event</strong>. An event is a signal that broadcasts "this thing just happened." You can write code that <em>listens</em> for that signal and responds when it fires.</p>

<p>This is far more efficient than constantly checking ("polling") whether something has happened. Instead of running a loop every frame to ask "did the player touch the part?", you just say "tell me when someone touches it" and your code automatically runs at that moment.</p>

<h2>The .Touched Event</h2>
<p>Every BasePart in Roblox has a <code>Touched</code> event that fires when another object makes contact with it. This is the bread and butter of interaction in Roblox games — coins, kill bricks, checkpoints, speed pads — they all use <code>Touched</code>.</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">part</span> <span class="op">=</span> <span class="var">workspace</span>.<span class="var">MyPart</span>

<span class="var">part</span>.<span class="var">Touched</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">otherPart</span>)
    <span class="fn">print</span>(<span class="var">otherPart</span>.<span class="var">Name</span> <span class="op">..</span> <span class="str">" touched the part!"</span>)
<span class="kw">end</span>)
</div>

<p>The parameter <code>otherPart</code> is the Part (or limb) that touched our Part. If a player walks onto the part, <code>otherPart</code> would be one of their limbs (e.g., "Left Leg" or "HumanoidRootPart").</p>

<h2>Finding the Player from a Touch</h2>
<p>Since <code>otherPart</code> is just a limb, we need to navigate from it to find the actual Player. We do this using the Humanoid and then the Players service:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">Players</span> <span class="op">=</span> <span class="var">game</span>.<span class="var">Players</span>
<span class="kw">local</span> <span class="var">part</span>    <span class="op">=</span> <span class="var">workspace</span>.<span class="var">MyPart</span>

<span class="var">part</span>.<span class="var">Touched</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">hit</span>)
    <span class="kw">local</span> <span class="var">player</span> <span class="op">=</span> <span class="var">Players</span>:<span class="fn">GetPlayerFromCharacter</span>(<span class="var">hit</span>.<span class="var">Parent</span>)
    <span class="kw">if</span> <span class="var">player</span> <span class="kw">then</span>
        <span class="fn">print</span>(<span class="var">player</span>.<span class="var">Name</span> <span class="op">..</span> <span class="str">" touched the part!"</span>)
    <span class="kw">end</span>
<span class="kw">end</span>)
</div>

<p><code>hit.Parent</code> gives us the character model (e.g., the "Alex" model), and <code>GetPlayerFromCharacter()</code> converts that to a Player object. The <code>if player then</code> guard ensures we only respond to actual players (not falling debris touching the part).</p>
`
        },
        {
          title: "Connecting Functions to Events",
          content: `
<h2>The :Connect() Method</h2>
<p><code>:Connect()</code> is how you attach a function to an event. Every RBXScriptSignal (which is what events are) has this method. The function you pass to Connect is called the <strong>event handler</strong> or <strong>callback</strong>. It runs every time the event fires.</p>

<div class="code-block">
<span class="com">-- Connect a named function</span>
<span class="kw">local</span> <span class="kw">function</span> <span class="fn">onPartTouched</span>(<span class="var">hit</span>)
    <span class="fn">print</span>(<span class="str">"Touched by:"</span>, <span class="var">hit</span>.<span class="var">Name</span>)
<span class="kw">end</span>

<span class="kw">local</span> <span class="var">part</span> <span class="op">=</span> <span class="var">workspace</span>.<span class="var">MyPart</span>
<span class="var">part</span>.<span class="var">Touched</span>:<span class="fn">Connect</span>(<span class="fn">onPartTouched</span>)
</div>

<h2>Other Common Events</h2>

<div class="code-block">
<span class="com">-- Player joining</span>
<span class="var">game</span>.<span class="var">Players</span>.<span class="var">PlayerAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="fn">print</span>(<span class="var">player</span>.<span class="var">Name</span> <span class="op">..</span> <span class="str">" joined!"</span>)
<span class="kw">end</span>)

<span class="com">-- Player leaving</span>
<span class="var">game</span>.<span class="var">Players</span>.<span class="var">PlayerRemoving</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="fn">print</span>(<span class="var">player</span>.<span class="var">Name</span> <span class="op">..</span> <span class="str">" left!"</span>)
<span class="kw">end</span>)

<span class="com">-- Character spawning</span>
<span class="var">game</span>.<span class="var">Players</span>.<span class="var">PlayerAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="var">player</span>.<span class="var">CharacterAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">character</span>)
        <span class="fn">print</span>(<span class="var">player</span>.<span class="var">Name</span> <span class="op">..</span> <span class="str">"'s character spawned!"</span>)
    <span class="kw">end</span>)
<span class="kw">end</span>)
</div>

<h2>Debounce — Preventing Event Spam</h2>
<p>The <code>Touched</code> event fires many times per second while something is in contact. This can cause your code to run hundreds of times when you only want it to run once. The solution is a <strong>debounce</strong> (a simple lock variable):</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">part</span>     <span class="op">=</span> <span class="var">workspace</span>.<span class="var">Coin</span>
<span class="kw">local</span> <span class="var">debounce</span> <span class="op">=</span> <span class="kw">false</span>

<span class="var">part</span>.<span class="var">Touched</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">hit</span>)
    <span class="kw">if</span> <span class="var">debounce</span> <span class="kw">then</span> <span class="kw">return</span> <span class="kw">end</span>   <span class="com">-- exit if already running</span>
    <span class="var">debounce</span> <span class="op">=</span> <span class="kw">true</span>

    <span class="fn">print</span>(<span class="str">"Coin collected!"</span>)
    <span class="var">part</span>.<span class="var">Transparency</span> <span class="op">=</span> <span class="num">1</span>         <span class="com">-- hide the coin</span>

    <span class="fn">task.wait</span>(<span class="num">2</span>)                   <span class="com">-- wait 2 seconds before allowing again</span>
    <span class="var">debounce</span> <span class="op">=</span> <span class="kw">false</span>
    <span class="var">part</span>.<span class="var">Transparency</span> <span class="op">=</span> <span class="num">0</span>         <span class="com">-- show the coin again</span>
<span class="kw">end</span>)
</div>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>Debounce is essential:</strong> Nearly every Touched handler in a professional Roblox game uses a debounce. Without it, collecting a coin would fire dozens of events simultaneously, potentially giving the player coins many times instead of once.</div>
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Touch Detector",
        description: "Build a script that detects when a player steps on a special part.",
        steps: [
          "<p>In Roblox Studio, create a large Part in Workspace named <code>TouchZone</code>. Make it flat (e.g., 10×0.2×10) and coloured bright orange.</p>",
          "<p>Create a Script in <code>ServerScriptService</code>.</p>",
          "<p>Write code that connects to the <code>Touched</code> event of <code>TouchZone</code>.</p>",
          "<p>Inside the handler, use <code>Players:GetPlayerFromCharacter(hit.Parent)</code> to identify the player. If a player is found, print their name and a welcome message.</p>",
          "<p>Add a debounce so the message only appears once per 3 seconds per touch event, not continuously while standing on it.</p>",
          "<p>Test by running the game and walking onto the TouchZone. Verify the message appears exactly once per touch.</p>"
        ]
      },
      quiz: [
        {
          question: "What is an event in Roblox scripting?",
          options: ["A type of variable", "A signal that fires when something happens in the game", "A loop that runs every frame", "A type of Part property"],
          correct: 1
        },
        {
          question: "What does :Connect() do?",
          options: ["Creates a new Part", "Links a function to an event so it runs when the event fires", "Connects two Parts together physically", "Sends data to the server"],
          correct: 1
        },
        {
          question: "Which event fires when a player's body part touches a Part?",
          options: [".Clicked", ".Touched", ".Hit", ".Contact"],
          correct: 1
        },
        {
          question: "What parameter does the Touched event pass to its handler function?",
          options: ["The player object", "The part that made contact", "The position of the touch", "A boolean"],
          correct: 1
        },
        {
          question: "What is debounce and why is it used with Touched events?",
          options: ["A way to make events fire faster", "A lock variable that prevents the handler from running too many times in rapid succession", "A method to connect multiple events at once", "A way to disconnect an event"],
          correct: 1
        }
      ]
    },

    // ─── SECTION 7 ───────────────────────────────────────────
    {
      id: 7,
      title: "Game Systems",
      subtitle: "Leaderstats, currency, and core game progression",
      icon: "07",
      lessons: [
        {
          title: "leaderstats — Showing Player Stats",
          content: `
<h2>What Are Leaderstats?</h2>
<p><strong>Leaderstats</strong> is a Roblox convention for displaying player statistics on the in-game leaderboard (the panel that appears when you press Tab or the leaderboard button). When Roblox detects a <code>Folder</code> named exactly <code>leaderstats</code> inside a player object, it automatically shows the values inside on the leaderboard.</p>

<p>This is one of the simplest but most powerful built-in systems in Roblox — it requires no special API calls to get working, just the right folder structure.</p>

<h2>The leaderstats Structure</h2>
<p>Inside the <code>leaderstats</code> folder, you place <strong>Value objects</strong>. Roblox provides several:</p>
<ul>
  <li><code>IntValue</code> — Stores an integer (whole number). Best for coins, kills, level.</li>
  <li><code>NumberValue</code> — Stores a floating-point number. Good for distances, percentages.</li>
  <li><code>StringValue</code> — Stores text. Good for team names, ranks.</li>
  <li><code>BoolValue</code> — Stores true/false. Good for flags like "isVIP".</li>
</ul>

<h2>Setting Up leaderstats</h2>
<p>The standard approach is to create leaderstats inside a <code>PlayerAdded</code> handler so every player who joins gets their own set of stats:</p>

<div class="code-block">
<span class="kw">local</span> <span class="var">Players</span> <span class="op">=</span> <span class="var">game</span>.<span class="var">Players</span>

<span class="var">Players</span>.<span class="var">PlayerAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="com">-- Create the leaderstats folder</span>
    <span class="kw">local</span> <span class="var">leaderstats</span> <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"Folder"</span>)
    <span class="var">leaderstats</span>.<span class="var">Name</span>   <span class="op">=</span> <span class="str">"leaderstats"</span>   <span class="com">-- exact name required!</span>
    <span class="var">leaderstats</span>.<span class="var">Parent</span> <span class="op">=</span> <span class="var">player</span>

    <span class="com">-- Create a Coins stat</span>
    <span class="kw">local</span> <span class="var">coins</span> <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"IntValue"</span>)
    <span class="var">coins</span>.<span class="var">Name</span>   <span class="op">=</span> <span class="str">"Coins"</span>
    <span class="var">coins</span>.<span class="var">Value</span>  <span class="op">=</span> <span class="num">0</span>
    <span class="var">coins</span>.<span class="var">Parent</span> <span class="op">=</span> <span class="var">leaderstats</span>

    <span class="com">-- Create a Level stat</span>
    <span class="kw">local</span> <span class="var">level</span> <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"IntValue"</span>)
    <span class="var">level</span>.<span class="var">Name</span>   <span class="op">=</span> <span class="str">"Level"</span>
    <span class="var">level</span>.<span class="var">Value</span>  <span class="op">=</span> <span class="num">1</span>
    <span class="var">level</span>.<span class="var">Parent</span> <span class="op">=</span> <span class="var">leaderstats</span>

    <span class="fn">print</span>(<span class="var">player</span>.<span class="var">Name</span> <span class="op">..</span> <span class="str">"'s stats created."</span>)
<span class="kw">end</span>)
</div>

<div class="info-box warning">
  <div class="info-box-icon">⚠️</div>
  <div class="info-box-text"><strong>Name is case-sensitive:</strong> The folder MUST be named exactly <code>leaderstats</code> — lowercase 'l', no spaces. Any variation like <code>Leaderstats</code> or <code>leader_stats</code> will not be recognized by Roblox's leaderboard system.</div>
</div>
`
        },
        {
          title: "Currency Systems — Coins and Rewards",
          content: `
<h2>Building a Coin System</h2>
<p>Currency systems are at the heart of almost every successful Roblox game. Players collect coins, spend them on upgrades or items, and this loop drives engagement. Let's build a complete coin collection system using everything we've learned.</p>

<div class="code-block">
<span class="com">-- Server Script in ServerScriptService</span>
<span class="kw">local</span> <span class="var">Players</span>   <span class="op">=</span> <span class="var">game</span>.<span class="var">Players</span>
<span class="kw">local</span> <span class="var">coinFolder</span> <span class="op">=</span> <span class="var">workspace</span>:<span class="fn">FindFirstChild</span>(<span class="str">"Coins"</span>)

<span class="com">-- Setup leaderstats for each player</span>
<span class="var">Players</span>.<span class="var">PlayerAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="kw">local</span> <span class="var">ls</span>    <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"Folder"</span>)
    <span class="var">ls</span>.<span class="var">Name</span>     <span class="op">=</span> <span class="str">"leaderstats"</span>
    <span class="var">ls</span>.<span class="var">Parent</span>   <span class="op">=</span> <span class="var">player</span>

    <span class="kw">local</span> <span class="var">coins</span>  <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"IntValue"</span>)
    <span class="var">coins</span>.<span class="var">Name</span>   <span class="op">=</span> <span class="str">"Coins"</span>
    <span class="var">coins</span>.<span class="var">Value</span>  <span class="op">=</span> <span class="num">0</span>
    <span class="var">coins</span>.<span class="var">Parent</span> <span class="op">=</span> <span class="var">ls</span>
<span class="kw">end</span>)

<span class="com">-- Connect each coin in the Coins folder</span>
<span class="kw">if</span> <span class="var">coinFolder</span> <span class="kw">then</span>
    <span class="kw">for</span> <span class="var">_</span>, <span class="var">coin</span> <span class="kw">in</span> <span class="fn">ipairs</span>(<span class="var">coinFolder</span>:<span class="fn">GetChildren</span>()) <span class="kw">do</span>
        <span class="kw">local</span> <span class="var">debounce</span> <span class="op">=</span> <span class="kw">false</span>

        <span class="var">coin</span>.<span class="var">Touched</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">hit</span>)
            <span class="kw">if</span> <span class="var">debounce</span> <span class="kw">then</span> <span class="kw">return</span> <span class="kw">end</span>
            <span class="kw">local</span> <span class="var">player</span> <span class="op">=</span> <span class="var">Players</span>:<span class="fn">GetPlayerFromCharacter</span>(<span class="var">hit</span>.<span class="var">Parent</span>)
            <span class="kw">if</span> <span class="kw">not</span> <span class="var">player</span> <span class="kw">then</span> <span class="kw">return</span> <span class="kw">end</span>

            <span class="var">debounce</span> <span class="op">=</span> <span class="kw">true</span>
            <span class="var">player</span>.<span class="var">leaderstats</span>.<span class="var">Coins</span>.<span class="var">Value</span> <span class="op">+=</span> <span class="num">10</span>
            <span class="fn">print</span>(<span class="var">player</span>.<span class="var">Name</span>, <span class="str">"collected a coin!"</span>)
            <span class="var">coin</span>.<span class="var">Transparency</span> <span class="op">=</span> <span class="num">1</span>
            <span class="var">coin</span>.<span class="var">CanCollide</span>   <span class="op">=</span> <span class="kw">false</span>
            <span class="fn">task.wait</span>(<span class="num">5</span>)
            <span class="var">coin</span>.<span class="var">Transparency</span> <span class="op">=</span> <span class="num">0</span>
            <span class="var">coin</span>.<span class="var">CanCollide</span>   <span class="op">=</span> <span class="kw">true</span>
            <span class="var">debounce</span> <span class="op">=</span> <span class="kw">false</span>
        <span class="kw">end</span>)
    <span class="kw">end</span>
<span class="kw">end</span>
</div>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>The += shorthand:</strong> <code>value += 10</code> is shorthand for <code>value = value + 10</code>. LuaU supports <code>+=</code>, <code>-=</code>, <code>*=</code>, and <code>/=</code> operators.</div>
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Coin Collection System",
        description: "Build a functional coin system with leaderstats.",
        steps: [
          "<p>Create a <code>Folder</code> in Workspace named <code>Coins</code>. Inside it, create several small yellow parts to act as coins. Name them <code>Coin1</code>, <code>Coin2</code>, etc.</p>",
          "<p>Create a Script in <code>ServerScriptService</code> that sets up <code>leaderstats</code> for each player with a <code>Coins</code> IntValue starting at 0.</p>",
          "<p>Loop through all children of the Coins folder and connect a <code>Touched</code> event to each one.</p>",
          "<p>When a player touches a coin, add 10 to their <code>Coins</code> value, hide the coin for 5 seconds, then show it again. Use debounce!</p>",
          "<p>Test in Roblox Studio, press Play, and walk into the coins. Verify your coin count increases on the leaderboard.</p>"
        ]
      },
      quiz: [
        {
          question: "What is leaderstats in Roblox?",
          options: ["A GUI element for UI design", "A Folder named exactly 'leaderstats' inside a Player that Roblox uses to show stats on the leaderboard", "A type of event", "A script location"],
          correct: 1
        },
        {
          question: "Why use a currency system in a Roblox game?",
          options: ["It's required by Roblox Terms of Service", "To give players goals, reward engagement, and drive a progression loop", "To prevent server lag", "To enable saving data automatically"],
          correct: 1
        },
        {
          question: "Where should the leaderstats folder be parented?",
          options: ["Inside workspace", "Inside the Player object", "Inside ReplicatedStorage", "Inside ServerScriptService"],
          correct: 1
        },
        {
          question: "Which Value type is most appropriate for storing a whole-number coin count?",
          options: ["StringValue", "BoolValue", "IntValue", "NumberValue"],
          correct: 2
        },
        {
          question: "What does the shorthand coins.Value += 10 do?",
          options: ["Sets coins.Value to 10", "Multiplies coins.Value by 10", "Adds 10 to coins.Value", "Creates a new value named 10"],
          correct: 2
        }
      ]
    },

    // ─── SECTION 8 ───────────────────────────────────────────
    {
      id: 8,
      title: "UI Systems",
      subtitle: "GUIs, buttons, and on-screen interfaces",
      icon: "08",
      lessons: [
        {
          title: "GUI Basics — Building On-Screen Interfaces",
          content: `
<h2>What Is a GUI?</h2>
<p>GUI stands for <strong>Graphical User Interface</strong> — the visual elements that players see overlaid on the game screen. This includes health bars, shop menus, inventory panels, buttons, labels, and any other 2D visual element. In Roblox, GUIs are built using a hierarchy of UI objects.</p>

<h2>The GUI Hierarchy</h2>
<p>Roblox GUIs follow a clear parent-child structure:</p>
<ul>
  <li><strong>ScreenGui</strong> — The root container for any GUI that stays fixed on the player's screen. Placed in <code>StarterGui</code>.</li>
  <li><strong>Frame</strong> — A rectangular container. Used to group and position other elements.</li>
  <li><strong>TextLabel</strong> — Displays non-interactive text.</li>
  <li><strong>TextButton</strong> — A clickable button with text.</li>
  <li><strong>ImageLabel</strong> — Displays an image.</li>
  <li><strong>ImageButton</strong> — A clickable button with an image.</li>
</ul>

<h2>Key GUI Properties</h2>
<p>All GUI elements share several important properties:</p>
<ul>
  <li><strong>Size</strong> — A <code>UDim2</code> value. UDim2 takes both scale (0 to 1, relative to parent) and offset (pixels).</li>
  <li><strong>Position</strong> — A <code>UDim2</code> value for where it is inside its parent.</li>
  <li><strong>AnchorPoint</strong> — A Vector2 that sets the pivot point (0.5, 0.5 = centered).</li>
  <li><strong>BackgroundColor3</strong> — The background color.</li>
  <li><strong>Text</strong> — The displayed text (TextLabel, TextButton).</li>
  <li><strong>TextColor3</strong> — Text color.</li>
  <li><strong>Font</strong> — The font style.</li>
  <li><strong>TextScaled</strong> — Automatically resize text to fit the element.</li>
</ul>

<div class="code-block">
<span class="com">-- Creating a ScreenGui with a Label via Script</span>
<span class="kw">local</span> <span class="var">Players</span> <span class="op">=</span> <span class="var">game</span>.<span class="var">Players</span>

<span class="var">Players</span>.<span class="var">PlayerAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="var">player</span>.<span class="var">CharacterAdded</span>:<span class="fn">Connect</span>(<span class="kw">function</span>()
        <span class="kw">local</span> <span class="var">gui</span>   <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"ScreenGui"</span>)
        <span class="var">gui</span>.<span class="var">Name</span>   <span class="op">=</span> <span class="str">"MyGui"</span>
        <span class="var">gui</span>.<span class="var">Parent</span> <span class="op">=</span> <span class="var">player</span>.<span class="var">PlayerGui</span>

        <span class="kw">local</span> <span class="var">label</span>              <span class="op">=</span> <span class="fn">Instance</span>.<span class="kw">new</span>(<span class="str">"TextLabel"</span>)
        <span class="var">label</span>.<span class="var">Size</span>              <span class="op">=</span> <span class="fn">UDim2</span>.<span class="kw">new</span>(<span class="num">0.3</span>, <span class="num">0</span>, <span class="num">0.1</span>, <span class="num">0</span>)
        <span class="var">label</span>.<span class="var">Position</span>          <span class="op">=</span> <span class="fn">UDim2</span>.<span class="kw">new</span>(<span class="num">0.35</span>, <span class="num">0</span>, <span class="num">0</span>, <span class="num">10</span>)
        <span class="var">label</span>.<span class="var">Text</span>              <span class="op">=</span> <span class="str">"Welcome, "</span> <span class="op">..</span> <span class="var">player</span>.<span class="var">Name</span>
        <span class="var">label</span>.<span class="var">TextScaled</span>        <span class="op">=</span> <span class="kw">true</span>
        <span class="var">label</span>.<span class="var">BackgroundColor3</span> <span class="op">=</span> <span class="fn">Color3</span>.<span class="fn">fromRGB</span>(<span class="num">30</span>, <span class="num">30</span>, <span class="num">30</span>)
        <span class="var">label</span>.<span class="var">TextColor3</span>       <span class="op">=</span> <span class="fn">Color3</span>.<span class="fn">fromRGB</span>(<span class="num">255</span>, <span class="num">255</span>, <span class="num">255</span>)
        <span class="var">label</span>.<span class="var">Parent</span>            <span class="op">=</span> <span class="var">gui</span>
    <span class="kw">end</span>)
<span class="kw">end</span>)
</div>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>StarterGui vs PlayerGui:</strong> Objects in <code>StarterGui</code> are copied to each player's <code>PlayerGui</code> when they join. For GUI scripts (LocalScripts interacting with UI), you typically work inside <code>StarterGui</code>.</div>
</div>
`
        },
        {
          title: "Buttons — Making GUI Interactive",
          content: `
<h2>TextButton and ImageButton</h2>
<p>A <code>TextButton</code> is a GUI element that players can click. When clicked, it fires the <code>MouseButton1Click</code> event (or the <code>Activated</code> event, which also works for mobile touch). You connect a function to this event just like any other event.</p>

<div class="code-block">
<span class="com">-- LocalScript inside StarterGui</span>
<span class="kw">local</span> <span class="var">button</span> <span class="op">=</span> <span class="var">script</span>.<span class="var">Parent</span>.<span class="var">MyButton</span>   <span class="com">-- or find it</span>

<span class="var">button</span>.<span class="var">MouseButton1Click</span>:<span class="fn">Connect</span>(<span class="kw">function</span>()
    <span class="fn">print</span>(<span class="str">"Button was clicked!"</span>)
<span class="kw">end</span>)
</div>

<p>Let's build a complete button that counts how many times it's been clicked:</p>

<div class="code-block">
<span class="com">-- LocalScript inside a ScreenGui</span>
<span class="kw">local</span> <span class="var">button</span>    <span class="op">=</span> <span class="var">script</span>.<span class="var">Parent</span>:<span class="fn">FindFirstChild</span>(<span class="str">"ClickBtn"</span>)
<span class="kw">local</span> <span class="var">label</span>     <span class="op">=</span> <span class="var">script</span>.<span class="var">Parent</span>:<span class="fn">FindFirstChild</span>(<span class="str">"CountLabel"</span>)
<span class="kw">local</span> <span class="var">clickCount</span> <span class="op">=</span> <span class="num">0</span>

<span class="var">button</span>.<span class="var">MouseButton1Click</span>:<span class="fn">Connect</span>(<span class="kw">function</span>()
    <span class="var">clickCount</span> <span class="op">+=</span> <span class="num">1</span>
    <span class="var">label</span>.<span class="var">Text</span> <span class="op">=</span> <span class="str">"Clicks: "</span> <span class="op">..</span> <span class="fn">tostring</span>(<span class="var">clickCount</span>)
    <span class="fn">print</span>(<span class="str">"Total clicks:"</span>, <span class="var">clickCount</span>)
<span class="kw">end</span>)
</div>

<h2>Sending Data from Client to Server</h2>
<p>When a button is clicked (client-side), you often need to do something server-side (like awarding coins). This is done using <code>RemoteEvent</code>. The client fires the event; the server listens for it:</p>

<div class="code-block">
<span class="com">-- CLIENT (LocalScript):</span>
<span class="kw">local</span> <span class="var">remote</span> <span class="op">=</span> <span class="var">game</span>.<span class="var">ReplicatedStorage</span>.<span class="var">GiveCoinsEvent</span>

<span class="var">button</span>.<span class="var">MouseButton1Click</span>:<span class="fn">Connect</span>(<span class="kw">function</span>()
    <span class="var">remote</span>:<span class="fn">FireServer</span>()
<span class="kw">end</span>)

<span class="com">-- SERVER (Script):</span>
<span class="var">remote</span>.<span class="var">OnServerEvent</span>:<span class="fn">Connect</span>(<span class="kw">function</span>(<span class="var">player</span>)
    <span class="var">player</span>.<span class="var">leaderstats</span>.<span class="var">Coins</span>.<span class="var">Value</span> <span class="op">+=</span> <span class="num">5</span>
<span class="kw">end</span>)
</div>

<div class="info-box warning">
  <div class="info-box-icon">⚠️</div>
  <div class="info-box-text"><strong>Never reward on the client:</strong> If you give coins directly in a LocalScript, hackers can exploit it. Always use RemoteEvents to send the request to the server, and handle the actual reward logic server-side. Always validate on the server!</div>
</div>
`
        }
      ],
      assignment: {
        title: "Assignment: Interactive Button",
        description: "Create a ScreenGui with a button that triggers visible feedback.",
        steps: [
          "<p>In Roblox Studio, go to <code>StarterGui</code> and insert a <code>ScreenGui</code>.</p>",
          "<p>Inside the ScreenGui, add a <code>TextButton</code> centered on the screen with the text <code>\"Click Me!\"</code>. Style it with a background color and large text.</p>",
          "<p>Add a <code>TextLabel</code> above the button that starts with the text <code>\"Not clicked yet\"</code>.</p>",
          "<p>Create a <strong>LocalScript</strong> inside the ScreenGui. Connect to the button's <code>MouseButton1Click</code> event.</p>",
          "<p>Each time the button is clicked: change the label text to <code>\"Clicked [n] times!\"</code> where n is the running click count. Also change the button's background color to a random Color3.</p>",
          "<p>Play the game and test your interactive button.</p>"
        ]
      },
      quiz: [
        {
          question: "What is a GUI in Roblox?",
          options: ["A type of server script", "A graphical user interface — visual 2D elements displayed on the player's screen", "A folder that holds part models", "A type of event system"],
          correct: 1
        },
        {
          question: "What does a TextButton do in Roblox?",
          options: ["Moves a Part in the world", "Displays text and fires an event when the player clicks it", "Stores a numerical value", "Controls camera movement"],
          correct: 1
        },
        {
          question: "Where are ScreenGuis typically placed to appear for all players?",
          options: ["Workspace", "ServerStorage", "StarterGui", "ReplicatedStorage"],
          correct: 2
        },
        {
          question: "Which event fires when a player clicks a TextButton?",
          options: [".Touched", ".MouseButton1Click", ".Clicked", ".Pressed"],
          correct: 1
        },
        {
          question: "Why should you use a RemoteEvent when a button click should reward coins?",
          options: ["RemoteEvents are faster", "So the server handles the reward — exploiters cannot manipulate server-side code", "LocalScripts cannot access IntValues", "It is required by the Roblox API"],
          correct: 1
        }
      ]
    },

    // ─── SECTION 9 ───────────────────────────────────────────
    {
      id: 9,
      title: "Final Project",
      subtitle: "Build a complete mini-game from scratch",
      icon: "09",
      lessons: [
        {
          title: "Project Brief — Your Mini-Game",
          content: `
<h2>Congratulations — You've Made It!</h2>
<p>You've completed all the core sections of the LuaU Academy. Now it's time to put <em>everything</em> together into a real, playable Roblox mini-game. This is your final project — there's no quiz here. Instead, you'll self-assess your work using the rubric provided.</p>

<h2>Project Requirements</h2>
<p>Your final project must include <strong>all of the following</strong>:</p>

<h3>1. A Playable Game World</h3>
<p>Build a small but complete game map in Roblox Studio. This could be an obstacle course, a coin-collecting arena, a simple platformer, or anything you can imagine. The map should make sense as a game environment — not just random parts.</p>

<h3>2. A Working Script (server-side)</h3>
<p>At minimum one Script in <code>ServerScriptService</code> that handles core game logic. This might set up leaderstats, spawn enemies, control doors, manage a timer, or anything game-related.</p>

<h3>3. At Least One Event</h3>
<p>Your game must respond to at least one event — whether that's <code>Touched</code>, <code>PlayerAdded</code>, <code>MouseButton1Click</code>, or any other event. The event must actually do something meaningful in your game.</p>

<h3>4. A System</h3>
<p>Include a trackable progression system — coins, points, health, kills, time survived, etc. This should be visible via leaderstats or a GUI.</p>

<h3>5. A GUI Element</h3>
<p>Include at least one GUI element that provides information or interaction for the player. A welcome screen, a coin counter HUD, a shop button, or similar.</p>

<h2>Project Ideas</h2>
<ul>
  <li><strong>Coin Rush:</strong> A timed arena where players collect coins scattered around the map. Leaderstats show coin count. Coins respawn after collection.</li>
  <li><strong>Obstacle Course (Obby):</strong> A series of platforms. Touching a kill brick resets position. Reaching the end awards points.</li>
  <li><strong>Clicker Game:</strong> A button that gives coins on click. Coins can be "spent" on a speed upgrade using another button.</li>
  <li><strong>Platformer Arena:</strong> Platforms at different heights. A speed pad that boosts the player. Coin rewards for exploration.</li>
</ul>

<h2>How You'll Be Graded</h2>
<p>Use the rubric in the Assignment tab to self-assess your project. Check each criterion honestly — this is about learning, not just passing.</p>

<div class="info-box important">
  <div class="info-box-icon">🔮</div>
  <div class="info-box-text"><strong>Code Quality Matters:</strong> Use meaningful variable names, include comments explaining your logic, and keep your scripts organized. Good habits now will save you hours of debugging later in larger projects.</div>
</div>

<h2>Final Checklist Before Submitting</h2>
<ul>
  <li>✅ Script runs without errors in Output</li>
  <li>✅ At least one event fires and does something</li>
  <li>✅ Leaderstats or GUI shows player data</li>
  <li>✅ Game is actually playable (has a goal)</li>
  <li>✅ Code uses functions, variables, and conditions</li>
  <li>✅ Comments explain major sections of your code</li>
</ul>
`
        }
      ],
      assignment: {
        title: "Final Project: Build Your Mini-Game",
        description: "Create a complete, playable Roblox mini-game incorporating all course concepts.",
        steps: [
          "<p>Design and build your game map in Roblox Studio. Include terrain or baseplate, several Parts, and at least one interactive area.</p>",
          "<p>Write a server Script that sets up <code>leaderstats</code> for each player with at least one trackable stat (coins, score, etc.).</p>",
          "<p>Implement at least one collectible or interaction using a <code>Touched</code> event with debounce that updates the player's stat.</p>",
          "<p>Create a ScreenGui with a HUD that shows the player's current stat value, updating in real-time.</p>",
          "<p>Add at least one additional feature of your choice: a kill brick, a speed pad, a shop button, an NPC, a timer countdown, respawn mechanics, etc.</p>",
          "<p>Test thoroughly: play the game, collect items, verify leaderstats update, check the GUI displays correctly, and make sure no errors appear in Output.</p>",
          "<p>Add comments throughout your scripts explaining what each major section does. Use the rubric below to self-grade your project.</p>"
        ]
      },
      isFinalProject: true,
      rubric: [
        { item: "Game map is built and playable", points: 15 },
        { item: "leaderstats set up correctly for each player", points: 15 },
        { item: "At least one Touched event with debounce works", points: 15 },
        { item: "Stat updates correctly when event fires", points: 15 },
        { item: "GUI displays player data and updates in real-time", points: 15 },
        { item: "At least one additional feature implemented", points: 10 },
        { item: "Code uses functions, variables, loops, and conditions", points: 10 },
        { item: "Comments present and explain code logic", points: 5 }
      ]
    },

    // ─── FINAL EXAM ───────────────────────────────────────────
    {
      id: "final",
      title: "Final Exam",
      subtitle: "Prove your mastery of all LuaU Academy content",
      icon: "FE",
      isSpecial: true,
      isFinalExam: true,
      lessons: [
        {
          title: "Final Exam Preparation",
          content: `
<h2>What to Expect</h2>
<p>The Final Exam covers material from all 9 sections plus the Midterm. It tests your understanding of:</p>
<ul>
  <li><strong>Section 1:</strong> Variables, data types, print(), debugging</li>
  <li><strong>Section 2:</strong> if/elseif/else, comparison operators, boolean logic</li>
  <li><strong>Section 3:</strong> while loops, for loops, break</li>
  <li><strong>Midterm:</strong> Combined application of above</li>
  <li><strong>Section 4:</strong> Functions, parameters, return values</li>
  <li><strong>Section 5:</strong> Scripts vs LocalScripts, Workspace, Parts, Instance.new()</li>
  <li><strong>Section 6:</strong> Events, .Touched, :Connect(), debounce</li>
  <li><strong>Section 7:</strong> leaderstats, currency systems, IntValue</li>
  <li><strong>Section 8:</strong> GUIs, TextButton, MouseButton1Click, RemoteEvents</li>
  <li><strong>Section 9:</strong> Project design, code organization, best practices</li>
</ul>

<h2>Tips for Success</h2>
<ul>
  <li>Re-read lesson content you feel uncertain about</li>
  <li>Try writing code from memory in Roblox Studio to solidify concepts</li>
  <li>Focus on the "why" behind each concept, not just the syntax</li>
  <li>Think through each question carefully — some are designed to test edge cases</li>
</ul>

<div class="info-box tip">
  <div class="info-box-icon">💡</div>
  <div class="info-box-text"><strong>You need 75% to pass.</strong> That's 9 out of 12 questions correct. Read each question carefully, eliminate clearly wrong answers, and trust what you've learned throughout this course. Good luck!</div>
</div>
`
        }
      ],
      assignment: {
        title: "Final Exam Preparation",
        description: "Review all sections before taking the final exam.",
        steps: [
          "<p>Review your notes and any scripts you built throughout the course.</p>",
          "<p>Open Roblox Studio and try building a small test script from scratch without looking at any reference — test your recall.</p>",
          "<p>When ready, click the Quiz tab to take the Final Exam. You need 75% or above to pass.</p>"
        ]
      },
      quiz: [
        {
          question: "Which keyword declares a local variable in LuaU?",
          options: ["var", "local", "let", "private"],
          correct: 1
        },
        {
          question: "What is the correct way to check if two values are equal in LuaU?",
          options: ["=", "===", "==", "equals()"],
          correct: 2
        },
        {
          question: "What does this code output?\n\nfor i = 1, 5 do\n  if i == 3 then break end\n  print(i)\nend",
          options: ["1 2 3 4 5", "1 2", "1 2 3", "Nothing"],
          correct: 1
        },
        {
          question: "What does a function's return statement do?",
          options: ["Prints a value to the output", "Exits the script entirely", "Sends a value back to the caller and exits the function", "Creates a new global variable"],
          correct: 2
        },
        {
          question: "Where do LocalScripts run in Roblox?",
          options: ["On Roblox's servers", "On each individual player's client device", "In both server and client simultaneously", "Only in Workspace"],
          correct: 1
        },
        {
          question: "Which event fires when a Part is physically contacted by another object?",
          options: [".Clicked", ".Touched", ".Hit", ".Activated"],
          correct: 1
        },
        {
          question: "What must the leaderstats folder be named EXACTLY for Roblox's leaderboard to recognize it?",
          options: ["LeaderStats", "Leaderstats", "leaderstats", "leader_stats"],
          correct: 2
        },
        {
          question: "Why should important game logic like awarding coins always run on the server?",
          options: ["The server is faster", "LocalScripts cannot use IntValues", "Client-side code can be exploited by hackers — server code cannot be modified by players", "Only servers have access to the Players service"],
          correct: 2
        },
        {
          question: "What does :Connect() do when called on an event?",
          options: ["Creates a new event", "Links a function to the event so it runs when the event fires", "Stops all other events from firing", "Connects two parts in the workspace"],
          correct: 1
        },
        {
          question: "What is a debounce and why is it used?",
          options: ["A timer that speeds up loops", "A boolean lock variable that prevents an event handler from running too many times rapidly", "A way to permanently disconnect an event", "A type of GUI element"],
          correct: 1
        },
        {
          question: "Which Value type stores whole numbers and is best for a coin counter?",
          options: ["NumberValue", "StringValue", "BoolValue", "IntValue"],
          correct: 3
        },
        {
          question: "In LuaU, what are the ONLY two values considered 'falsy'?",
          options: ["0 and empty string", "false and nil", "nil and NaN", "false and 0"],
          correct: 1
        }
      ]
    }
  ]
};

// ============================================================
// PROGRESS MANAGEMENT
// ============================================================
const STORAGE_KEY = 'luau_academy_progress';

function loadProgress() {
  try {
    const raw = localStorage.getItem(STORAGE_KEY);
    return raw ? JSON.parse(raw) : { sections: {}, totalPoints: 0 };
  } catch { return { sections: {}, totalPoints: 0 }; }
}

function saveProgress(progress) {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(progress));
}

let progress = loadProgress();

function getSectionProgress(id) {
  return progress.sections[id] || { status: 'locked', score: null, attempts: 0 };
}

function setSectionProgress(id, data) {
  progress.sections[id] = { ...(progress.sections[id] || {}), ...data };
  recalcPoints();
  saveProgress(progress);
  renderSidebar();
  updateHeader();
}

function recalcPoints() {
  let pts = 0, scores = [], count = 0;
  COURSE.sections.forEach(s => {
    const sp = getSectionProgress(s.id);
    if (sp.status === 'passed') {
      pts += 100;
      scores.push(sp.score);
      count++;
    }
  });
  progress.totalPoints = pts;
  document.getElementById('stat-points').textContent = pts;
  document.getElementById('stat-completed').textContent = count;
  document.getElementById('stat-avg').textContent = scores.length
    ? Math.round(scores.reduce((a, b) => a + b, 0) / scores.length) + '%'
    : '—';
}

function isUnlocked(sectionIndex) {
  const s = COURSE.sections[sectionIndex];
  if (sectionIndex === 0) return true;
  // check previous section passed
  const prev = COURSE.sections[sectionIndex - 1];
  const prevP = getSectionProgress(prev.id);
  return prevP.status === 'passed';
}

function updateHeader() {
  const total = COURSE.sections.length;
  const passed = COURSE.sections.filter(s => getSectionProgress(s.id).status === 'passed').length;
  const pct = Math.round((passed / total) * 100);
  document.getElementById('header-progress-fill').style.width = pct + '%';
  document.getElementById('header-progress-pct').textContent = pct + '%';
  document.getElementById('header-pts-val').textContent = progress.totalPoints || 0;
}

// ============================================================
// SIDEBAR RENDERING
// ============================================================
function renderSidebar() {
  const list = document.getElementById('sidebar-nav-list');
  list.innerHTML = '';

  COURSE.sections.forEach((section, idx) => {
    const sp = getSectionProgress(section.id);
    const unlocked = isUnlocked(idx);

    const item = document.createElement('div');
    item.className = 'sidebar-item' +
      (section.isSpecial ? ' special' : '') +
      (!unlocked ? ' locked' : '') +
      (sp.status === 'passed' ? ' completed' : '');
    item.id = `nav-s-${section.id}`;

    // Icon
    let iconClass = 'section-icon';
    let iconContent = section.icon;
    if (!unlocked) { iconClass = 'locked-icon'; iconContent = '🔒'; }
    else if (sp.status === 'passed') { iconClass = 'completed-icon'; iconContent = '✓'; }
    else if (sp.status === 'failed') { iconClass = 'failed-icon'; iconContent = '✗'; }
    else if (section.isSpecial) { iconClass = 'special-icon'; }

    // Score badge
    let badgeHtml = '';
    if (sp.score !== null && sp.score !== undefined) {
      const cls = sp.status === 'passed' ? 'pass' : 'fail';
      badgeHtml = `<span class="s-score-badge ${cls}">${sp.score}%</span>`;
    }

    item.innerHTML = `
      <div class="s-icon ${iconClass}">${iconContent}</div>
      <div class="s-text">
        <div class="s-title">${section.title}</div>
        <div class="s-subtitle">${section.isSpecial ? '⭐ Special' : `${section.lessons.length} lesson${section.lessons.length !== 1 ? 's' : ''}`}</div>
      </div>
      ${badgeHtml}
    `;

    if (unlocked) {
      item.addEventListener('click', () => openSection(idx));
    }

    list.appendChild(item);
  });
}

// ============================================================
// SECTION CARDS (DASHBOARD)
// ============================================================
function renderDashboard() {
  const grid = document.getElementById('section-grid');
  grid.innerHTML = '';
  recalcPoints();

  COURSE.sections.forEach((section, idx) => {
    const sp = getSectionProgress(section.id);
    const unlocked = isUnlocked(idx);

    let cardClass = 'section-card';
    let statusHtml = '';

    if (!unlocked) {
      cardClass += ' card-locked';
      statusHtml = `<span class="card-status locked">🔒 Locked</span>`;
    } else if (sp.status === 'passed') {
      cardClass += ' card-completed';
      statusHtml = `<span class="card-status completed">✅ ${sp.score}% — Passed</span>`;
    } else if (sp.status === 'failed') {
      cardClass += ' card-failed';
      statusHtml = `<span class="card-status failed">❌ ${sp.score}% — Retry</span>`;
    } else if (section.isSpecial) {
      cardClass += ' card-special';
      statusHtml = `<span class="card-status special">⭐ Available</span>`;
    } else {
      statusHtml = `<span class="card-status unlocked">▶ Start</span>`;
    }

    const card = document.createElement('div');
    card.className = cardClass;
    card.innerHTML = `
      <div class="card-number">${section.isSpecial ? '⭐ Special' : `Section ${idx + 1} of ${COURSE.sections.length}`}</div>
      <div class="card-title">${section.title}</div>
      <div class="card-desc">${section.subtitle}</div>
      ${statusHtml}
    `;

    if (unlocked) {
      card.addEventListener('click', () => openSection(idx));
    }

    grid.appendChild(card);
  });
}

// ============================================================
// SHOW DASHBOARD
// ============================================================
function showDashboard() {
  document.getElementById('dashboard').style.display = 'block';
  document.getElementById('lesson-view').style.display = 'none';
  renderDashboard();
  setActiveNav('nav-home');
  closeSidebar();
}

// ============================================================
// OPEN SECTION
// ============================================================
let currentSectionIdx = -1;
let currentTab = 'lessons';
let quizState = {};

function openSection(idx) {
  currentSectionIdx = idx;
  currentTab = 'lessons';
  const section = COURSE.sections[idx];
  const sp = getSectionProgress(section.id);

  document.getElementById('dashboard').style.display = 'none';
  document.getElementById('lesson-view').style.display = 'block';

  document.getElementById('breadcrumb-label').textContent = section.title;
  document.getElementById('lesson-tag').textContent =
    section.isSpecial ? '⭐ Special Section' : `📘 Section ${idx + 1}`;
  document.getElementById('lesson-title').textContent = section.title;
  document.getElementById('lesson-subtitle').textContent = section.subtitle;

  // Set active nav
  setActiveNav(`nav-s-${section.id}`);
  closeSidebar();

  buildTabs(section, sp);
  showTab('lessons');
}

function setActiveNav(id) {
  document.querySelectorAll('.sidebar-item').forEach(el => el.classList.remove('active'));
  const el = document.getElementById(id);
  if (el) el.classList.add('active');
}

function buildTabs(section, sp) {
  const bar = document.getElementById('tabs-bar');
  bar.innerHTML = '';

  const tabs = [
    { id: 'lessons', label: '📖 Lessons', cls: '' },
    { id: 'assignment', label: '📝 Assignment', cls: '' },
  ];

  if (section.isFinalProject) {
    tabs.push({ id: 'quiz', label: '🏆 Grading', cls: 'tab-gold' });
  } else {
    tabs.push({ id: 'quiz', label: '🎯 Quiz', cls: 'tab-gold' });
  }

  tabs.forEach(t => {
    const btn = document.createElement('button');
    btn.className = `tab-btn ${t.cls}`;
    btn.id = `tab-${t.id}`;
    btn.textContent = t.label;
    btn.onclick = () => showTab(t.id);
    bar.appendChild(btn);
  });
}

function showTab(tab) {
  currentTab = tab;
  const section = COURSE.sections[currentSectionIdx];
  const sp = getSectionProgress(section.id);

  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  const activeBtn = document.getElementById(`tab-${tab}`);
  if (activeBtn) activeBtn.classList.add('active');

  const content = document.getElementById('tab-content');
  content.innerHTML = '';

  if (tab === 'lessons') {
    renderLessons(section, content);
  } else if (tab === 'assignment') {
    renderAssignment(section, content);
  } else if (tab === 'quiz') {
    if (section.isFinalProject) {
      renderFinalProjectGrading(section, content, sp);
    } else {
      // Check if already passed
      if (sp.status === 'passed' && sp.score !== null) {
        renderQuizResult(content, sp.score, section, true);
      } else {
        renderQuiz(section, content, sp);
      }
    }
  }
}

// ============================================================
// LESSONS RENDERER
// ============================================================
function renderLessons(section, container) {
  section.lessons.forEach((lesson, i) => {
    const wrap = document.createElement('div');
    wrap.innerHTML = `
      <div class="lesson-content">
        <h2>${lesson.title}</h2>
        ${lesson.content}
      </div>
    `;
    container.appendChild(wrap);
  });

  const nextBtn = document.createElement('div');
  nextBtn.style.cssText = 'display:flex;justify-content:flex-end;margin-top:8px;';
  nextBtn.innerHTML = `<button class="btn btn-primary" onclick="showTab('assignment')">Next: Assignment →</button>`;
  container.appendChild(nextBtn);
}

// ============================================================
// ASSIGNMENT RENDERER
// ============================================================
function renderAssignment(section, container) {
  const a = section.assignment;
  const stepsHtml = a.steps.map(s => `<li>${s}</li>`).join('');

  const wrap = document.createElement('div');
  wrap.className = 'assignment-card';
  wrap.innerHTML = `
    <h2>📝 ${a.title}</h2>
    <p style="color:var(--text-secondary);margin-bottom:20px;line-height:1.7;font-size:0.92rem;">${a.description}</p>
    <ol class="assignment-steps">${stepsHtml}</ol>
  `;
  container.appendChild(wrap);

  const nav = document.createElement('div');
  nav.style.cssText = 'display:flex;justify-content:space-between;margin-top:8px;';
  const quizLabel = section.isFinalProject ? '🏆 Go to Grading' : '🎯 Take the Quiz';
  nav.innerHTML = `
    <button class="btn btn-secondary" onclick="showTab('lessons')">← Back to Lessons</button>
    <button class="btn btn-gold" onclick="showTab('quiz')">${quizLabel}</button>
  `;
  container.appendChild(nav);
}

// ============================================================
// QUIZ RENDERER
// ============================================================
function renderQuiz(section, container, sp) {
  const quiz = section.quiz;
  quizState = {
    answers: new Array(quiz.length).fill(null),
    submitted: false,
    currentQ: 0
  };

  function render() {
    container.innerHTML = '';

    // Header
    const header = document.createElement('div');
    header.className = 'quiz-header';

    const dots = quiz.map((_, i) => {
      let cls = 'q-dot';
      if (i < quizState.currentQ) cls += ' answered';
      if (i === quizState.currentQ) cls += ' current';
      return `<div class="${cls}"></div>`;
    }).join('');

    header.innerHTML = `
      <div class="quiz-meta">
        <div class="quiz-title">${section.isSpecial ? '⭐' : '🎯'} ${section.title} — Quiz</div>
        <div class="quiz-info">Question ${quizState.currentQ + 1} of ${quiz.length} · Pass with 75% or higher</div>
      </div>
      <div class="quiz-progress-dots">${dots}</div>
    `;
    container.appendChild(header);

    // Question card
    const q = quiz[quizState.currentQ];
    const card = document.createElement('div');
    card.className = 'quiz-question-card';

    const optHtml = q.options.map((opt, oi) => {
      const letter = String.fromCharCode(65 + oi); // A, B, C, D
      let cls = 'q-option';
      if (quizState.submitted || quizState.answers[quizState.currentQ] !== null) {
        // show result if this q was answered
        if (quizState.answers[quizState.currentQ] !== null) {
          cls += ' disabled';
          if (oi === q.correct) cls += ' correct';
          else if (oi === quizState.answers[quizState.currentQ] && oi !== q.correct) cls += ' wrong';
        }
      } else if (quizState.answers[quizState.currentQ] === oi) {
        cls += ' selected';
      }
      return `<div class="${cls}" data-opt="${oi}">
        <span class="opt-letter">${letter}</span>
        <span>${opt}</span>
      </div>`;
    }).join('');

    card.innerHTML = `
      <div class="q-number">Question ${quizState.currentQ + 1} / ${quiz.length}</div>
      <div class="q-text">${q.question}</div>
      <div class="q-options">${optHtml}</div>
    `;

    // Handle clicks
    card.querySelectorAll('.q-option').forEach(el => {
      el.addEventListener('click', () => {
        if (quizState.answers[quizState.currentQ] !== null) return;
        const oi = parseInt(el.dataset.opt);
        quizState.answers[quizState.currentQ] = oi;
        render();
      });
    });

    container.appendChild(card);

    // Nav
    const nav = document.createElement('div');
    nav.className = 'quiz-nav';

    const answered = quizState.answers[quizState.currentQ] !== null;

    nav.innerHTML = `
      <button class="btn btn-secondary" ${quizState.currentQ === 0 ? 'disabled' : ''} id="q-prev">← Previous</button>
      <span style="font-size:0.8rem;color:var(--text-muted);">${quizState.answers.filter(a => a !== null).length}/${quiz.length} answered</span>
      ${quizState.currentQ < quiz.length - 1
        ? `<button class="btn btn-primary" ${answered ? '' : 'disabled'} id="q-next">Next →</button>`
        : `<button class="btn btn-gold" ${quizState.answers.every(a => a !== null) ? '' : 'disabled'} id="q-submit">Submit Quiz</button>`
      }
    `;

    container.appendChild(nav);

    nav.querySelector('#q-prev')?.addEventListener('click', () => {
      quizState.currentQ--;
      render();
    });

    nav.querySelector('#q-next')?.addEventListener('click', () => {
      if (answered) { quizState.currentQ++; render(); }
    });

    nav.querySelector('#q-submit')?.addEventListener('click', () => {
      submitQuiz(section, container);
    });
  }

  render();
}

function submitQuiz(section, container) {
  const quiz = section.quiz;
  let correct = 0;
  quiz.forEach((q, i) => {
    if (quizState.answers[i] === q.correct) correct++;
  });

  const score = Math.round((correct / quiz.length) * 100);
  const passed = score >= 75;

  // Save progress
  setSectionProgress(section.id, {
    status: passed ? 'passed' : 'failed',
    score: score,
    attempts: (getSectionProgress(section.id).attempts || 0) + 1
  });

  // Unlock next if passed
  if (passed) {
    showToast(`🎉 ${score}% — Section Passed! +100 pts`, 'success');
  } else {
    showToast(`❌ ${score}% — Need 75% to pass. Try again!`, 'error');
  }

  renderQuizResult(container, score, section, passed);
  updateHeader();
}

function renderQuizResult(container, score, section, passed) {
  container.innerHTML = '';
  const correct = section.quiz ? Math.round((score / 100) * section.quiz.length) : 0;
  const total = section.quiz ? section.quiz.length : 0;

  const res = document.createElement('div');
  res.className = 'quiz-result';

  const sp = getSectionProgress(section.id);

  res.innerHTML = `
    <span class="result-icon">${passed ? '🏆' : '💔'}</span>
    <div class="result-score ${passed ? 'pass' : 'fail'}">${score}%</div>
    <div class="result-label">${passed ? 'Section Passed!' : 'Not Quite There'}</div>
    <div class="result-message">${passed
      ? 'Excellent work! You\'ve demonstrated a solid understanding of this section. The next section is now unlocked.'
      : 'You needed 75% to pass. Review the lessons and assignment, then try again. You\'ve got this!'
    }</div>
    <div class="result-breakdown">
      <div class="breakdown-item">
        <div class="breakdown-val" style="color:${passed ? 'var(--green)' : 'var(--red)'}">${score}%</div>
        <div class="breakdown-key">Score</div>
      </div>
      <div class="breakdown-item">
        <div class="breakdown-val" style="color:var(--accent)">${correct}/${total}</div>
        <div class="breakdown-key">Correct</div>
      </div>
      <div class="breakdown-item">
        <div class="breakdown-val" style="color:var(--gold)">${sp.attempts || 1}</div>
        <div class="breakdown-key">Attempts</div>
      </div>
    </div>
    <div class="result-actions">
      ${!passed ? `<button class="btn btn-primary" onclick="showTab('quiz')">🔄 Retry Quiz</button>` : ''}
      <button class="btn btn-secondary" onclick="showTab('lessons')">📖 Review Lessons</button>
      ${passed && currentSectionIdx < COURSE.sections.length - 1
        ? `<button class="btn btn-green" onclick="openSection(${currentSectionIdx + 1})">Next Section →</button>`
        : ''
      }
      <button class="btn btn-outline" onclick="showDashboard()">🏠 Dashboard</button>
    </div>
  `;

  container.appendChild(res);
}

// ============================================================
// FINAL PROJECT GRADING
// ============================================================
function renderFinalProjectGrading(section, container, sp) {
  const rubric = section.rubric;
  let checks = {};

  if (sp.checks) checks = sp.checks;

  function calcScore() {
    let earned = 0;
    let total = rubric.reduce((a, r) => a + r.points, 0);
    rubric.forEach((r, i) => {
      if (checks[i] === 'yes') earned += r.points;
    });
    return { earned, total, pct: Math.round((earned / total) * 100) };
  }

  function render() {
    container.innerHTML = '';

    const sc = calcScore();

    const table = document.createElement('div');
    table.className = 'grading-rubric';
    table.innerHTML = `<div class="rubric-header">📋 Project Grading Rubric — Self Assessment</div>`;

    rubric.forEach((r, i) => {
      const row = document.createElement('div');
      row.className = 'rubric-row';
      row.innerHTML = `
        <div class="rubric-item">${r.item}</div>
        <div class="rubric-pts">${r.points} pts</div>
        <div class="rubric-check">
          <button class="check-btn yes-btn ${checks[i] === 'yes' ? 'selected' : ''}" data-idx="${i}" data-val="yes">✓ Yes</button>
          <button class="check-btn no-btn ${checks[i] === 'no' ? 'selected' : ''}" data-idx="${i}" data-val="no">✗ No</button>
        </div>
      `;
      table.appendChild(row);
    });

    container.appendChild(table);

    const scoreDiv = document.createElement('div');
    scoreDiv.id = 'final-proj-score';
    const passed = sc.pct >= 75;
    scoreDiv.innerHTML = `<span style="color:${passed ? 'var(--green)' : 'var(--red)'}">${sc.earned}/${sc.total} pts (${sc.pct}%)</span>`;
    container.appendChild(scoreDiv);

    const allAnswered = Object.keys(checks).length === rubric.length;

    const nav = document.createElement('div');
    nav.style.cssText = 'display:flex;justify-content:center;gap:12px;margin-top:8px;flex-wrap:wrap;';
    nav.innerHTML = `
      <button class="btn btn-secondary" onclick="showTab('assignment')">← Back</button>
      <button class="btn btn-gold" id="submit-proj" ${allAnswered ? '' : 'disabled'}>Submit Self-Assessment</button>
    `;
    container.appendChild(nav);

    // Event listeners for check buttons
    container.querySelectorAll('.check-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        const idx = parseInt(btn.dataset.idx);
        checks[idx] = btn.dataset.val;
        setSectionProgress(section.id, { checks });
        render();
      });
    });

    container.querySelector('#submit-proj')?.addEventListener('click', () => {
      const sc = calcScore();
      const passed = sc.pct >= 75;
      setSectionProgress(section.id, {
        status: passed ? 'passed' : 'failed',
        score: sc.pct,
        checks
      });
      updateHeader();
      if (passed) {
        showToast(`🎉 Project: ${sc.pct}% — Final Project Passed!`, 'success');
      } else {
        showToast(`Keep working! ${sc.pct}% — 75% needed to pass.`, 'error');
      }
      render();
    });
  }

  render();
}

// ============================================================
// TOAST
// ============================================================
function showToast(msg, type = 'success') {
  const toast = document.getElementById('toast');
  const icon = document.getElementById('toast-icon');
  const text = document.getElementById('toast-text');

  icon.textContent = type === 'success' ? '✅' : type === 'error' ? '❌' : '⭐';
  text.textContent = msg;
  toast.className = `toast toast-${type} show`;

  clearTimeout(toast._timer);
  toast._timer = setTimeout(() => { toast.className = 'toast'; }, 4000);
}

// ============================================================
// SIDEBAR MOBILE TOGGLE
// ============================================================
function toggleSidebar() {
  document.getElementById('sidebar').classList.toggle('open');
  document.getElementById('sidebar-overlay').classList.toggle('show');
}

function closeSidebar() {
  document.getElementById('sidebar').classList.remove('open');
  document.getElementById('sidebar-overlay').classList.remove('show');
}

// ============================================================
// INITIALIZATION
// ============================================================
function init() {
  // Unlock first section by default
  const firstSp = getSectionProgress(COURSE.sections[0].id);
  if (!firstSp.status || firstSp.status === 'locked') {
    setSectionProgress(COURSE.sections[0].id, { status: 'unlocked' });
  }

  renderSidebar();
  renderDashboard();
  updateHeader();
}

init();
</script>
</body>
</html>
