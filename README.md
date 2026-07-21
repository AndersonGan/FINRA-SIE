
<!doctype html>
<html lang="en" data-theme="light">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="SIE Compass is an offline, interactive FINRA SIE preparation course with lessons, adaptive review, analytics, and a 75-question mock exam.">
  <title>SIE Compass — Focused FINRA SIE Prep</title>
  <style>
    :root {
      color-scheme: light;
      --ink: #14231f;
      --muted: #63706b;
      --paper: #f4f2eb;
      --surface: #fffef9;
      --surface-2: #ebe8df;
      --line: #dad8cf;
      --navy: #102a2c;
      --navy-2: #183b3c;
      --green: #0f766e;
      --green-2: #d7eee8;
      --gold: #b77822;
      --gold-2: #f7e8ca;
      --coral: #bd5546;
      --coral-2: #f8dfd9;
      --blue: #4169a5;
      --blue-2: #e0e9f7;
      --shadow: 0 14px 40px rgba(20, 35, 31, .08);
      --shadow-sm: 0 5px 18px rgba(20, 35, 31, .07);
      --radius: 18px;
      --radius-sm: 12px;
      --sidebar: 254px;
    }
    [data-theme="dark"] {
      color-scheme: dark;
      --ink: #edf5f0;
      --muted: #9caaa4;
      --paper: #0d1717;
      --surface: #132221;
      --surface-2: #1a2d2b;
      --line: #2b403d;
      --navy: #081111;
      --navy-2: #142c2c;
      --green: #55c1ad;
      --green-2: #183a36;
      --gold: #e8b45d;
      --gold-2: #3d301b;
      --coral: #f08a7e;
      --coral-2: #452923;
      --blue: #80a9e3;
      --blue-2: #21334c;
      --shadow: 0 14px 40px rgba(0, 0, 0, .22);
      --shadow-sm: 0 5px 18px rgba(0, 0, 0, .18);
    }
    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      min-width: 320px;
      background: var(--paper);
      color: var(--ink);
      font: 15px/1.55 Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      transition: background .25s ease, color .25s ease;
    }
    button, input, select { font: inherit; }
    button { cursor: pointer; }
    a { color: var(--green); }
    :focus-visible { outline: 3px solid color-mix(in srgb, var(--green) 55%, transparent); outline-offset: 3px; }
    .skip { position: fixed; left: 16px; top: -80px; z-index: 100; background: var(--surface); color: var(--ink); padding: 10px 14px; border-radius: 8px; }
    .skip:focus { top: 12px; }
    .shell { min-height: 100vh; display: grid; grid-template-columns: var(--sidebar) minmax(0, 1fr); }
    .sidebar {
      position: fixed; inset: 0 auto 0 0; width: var(--sidebar); padding: 24px 18px;
      background: var(--navy); color: #ecf7f4; display: flex; flex-direction: column; z-index: 20;
    }
    .brand { display: flex; align-items: center; gap: 11px; margin: 0 8px 28px; color: white; }
    .brand-mark { width: 38px; height: 38px; display: grid; place-items: center; border: 1px solid rgba(255,255,255,.24); border-radius: 12px; background: linear-gradient(145deg,#2f8178,#163f40); font-weight: 850; letter-spacing: -.07em; }
    .brand strong { display: block; font-size: 17px; letter-spacing: -.02em; }
    .brand span { display: block; font-size: 10px; color: #a8c5c0; letter-spacing: .12em; text-transform: uppercase; }
    .nav { display: grid; gap: 4px; }
    .nav button {
      width: 100%; border: 0; border-radius: 11px; background: transparent; color: #a8c5c0; text-align: left;
      padding: 10px 12px; display: flex; align-items: center; gap: 11px; transition: .18s ease;
    }
    .nav button:hover { background: rgba(255,255,255,.06); color: white; }
    .nav button.active { background: #214b4a; color: white; box-shadow: inset 3px 0 #5fd1bc; }
    .nav-icon { width: 22px; text-align: center; font-size: 16px; }
    .sidebar-foot { margin-top: auto; padding: 16px 10px 0; border-top: 1px solid rgba(255,255,255,.1); }
    .side-label { color: #84a5a0; font-size: 11px; text-transform: uppercase; letter-spacing: .1em; }
    .side-progress { height: 5px; margin: 9px 0; border-radius: 99px; background: rgba(255,255,255,.12); overflow: hidden; }
    .side-progress span { display: block; height: 100%; background: #55c1ad; border-radius: inherit; transition: width .4s ease; }
    .side-stat { display: flex; justify-content: space-between; color: white; font-size: 12px; }
    .content { grid-column: 2; min-width: 0; }
    .topbar {
      min-height: 74px; padding: 14px clamp(20px,4vw,52px); display: flex; align-items: center; justify-content: space-between; gap: 18px;
      border-bottom: 1px solid var(--line); background: color-mix(in srgb, var(--paper) 86%, transparent); backdrop-filter: blur(14px); position: sticky; top: 0; z-index: 15;
    }
    .eyebrow { color: var(--green); font-size: 11px; font-weight: 800; letter-spacing: .13em; text-transform: uppercase; }
    .top-title { font-size: 14px; font-weight: 730; }
    .top-actions { display: flex; align-items: center; gap: 9px; }
    .icon-btn, .soft-btn, .primary-btn, .danger-btn {
      min-height: 40px; border-radius: 11px; border: 1px solid var(--line); padding: 9px 14px; background: var(--surface); color: var(--ink); font-weight: 720;
      transition: transform .16s ease, border-color .16s ease, background .16s ease;
    }
    .icon-btn { width: 42px; padding: 0; display: grid; place-items: center; }
    .icon-btn:hover, .soft-btn:hover { border-color: var(--green); transform: translateY(-1px); }
    .primary-btn { background: var(--green); border-color: var(--green); color: #fff; box-shadow: 0 8px 20px color-mix(in srgb, var(--green) 25%, transparent); }
    .primary-btn:hover { transform: translateY(-2px); filter: brightness(1.06); }
    .primary-btn:disabled, .soft-btn:disabled { opacity: .48; cursor: not-allowed; transform: none; }
    .danger-btn { background: var(--coral-2); border-color: color-mix(in srgb, var(--coral) 35%, var(--line)); color: var(--coral); }
    .main { max-width: 1500px; margin: 0 auto; padding: clamp(24px,4vw,52px); }
    .view-enter { animation: rise .32s ease both; }
    @keyframes rise { from { opacity: 0; transform: translateY(8px); } }
    .page-head { display: flex; justify-content: space-between; align-items: end; gap: 24px; margin-bottom: 28px; }
    .page-head h1, .hero h1 { margin: 5px 0 7px; font-size: clamp(30px,4.5vw,58px); line-height: 1.03; letter-spacing: -.055em; max-width: 850px; }
    .page-head h1 { font-size: clamp(28px,3.5vw,43px); }
    .page-head p, .hero p { color: var(--muted); max-width: 720px; margin: 0; font-size: 16px; }
    .hero {
      position: relative; overflow: hidden; padding: clamp(28px,5vw,64px); border-radius: 26px; min-height: 500px;
      background: var(--navy); color: white; box-shadow: var(--shadow); display: grid; grid-template-columns: 1.35fr .85fr; gap: 36px; align-items: center;
    }
    .hero::after { content: ""; position: absolute; width: 380px; height: 380px; border-radius: 50%; right: -130px; top: -145px; background: radial-gradient(circle,rgba(85,193,173,.3),transparent 67%); }
    .hero h1 { max-width: 680px; }
    .hero p { color: #b7ceca; max-width: 650px; }
    .hero .eyebrow { color: #7ed5c5; }
    .hero-actions { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 26px; }
    .hero-actions .soft-btn { color: white; border-color: rgba(255,255,255,.19); background: rgba(255,255,255,.06); }
    .hero-note { display: flex; gap: 18px; flex-wrap: wrap; color: #91b2ad; margin-top: 24px; font-size: 12px; }
    .readiness-card { position: relative; z-index: 1; padding: 25px; background: rgba(255,255,255,.08); border: 1px solid rgba(255,255,255,.14); border-radius: 22px; backdrop-filter: blur(8px); }
    .readiness-card .label { color: #a8c5c0; font-size: 12px; text-transform: uppercase; letter-spacing: .11em; }
    .score-ring { --score: 0; width: 156px; aspect-ratio: 1; margin: 18px auto; border-radius: 50%; display: grid; place-items: center; background: conic-gradient(#5fd1bc calc(var(--score)*1%), rgba(255,255,255,.1) 0); position: relative; }
    .score-ring::before { content: ""; position: absolute; inset: 11px; border-radius: 50%; background: var(--navy-2); }
    .score-ring span { position: relative; font-size: 39px; font-weight: 820; letter-spacing: -.05em; }
    .score-ring small { display:block; font-size: 10px; color:#9ebeb9; letter-spacing:.08em; text-align:center; text-transform:uppercase; }
    .mini-metrics { display: grid; grid-template-columns: repeat(3,1fr); gap: 7px; }
    .mini-metrics div { padding: 11px 6px; border-radius: 10px; background: rgba(255,255,255,.06); text-align: center; }
    .mini-metrics strong { display: block; font-size: 15px; }
    .mini-metrics span { display: block; color: #92afab; font-size: 9px; text-transform: uppercase; letter-spacing: .07em; }
    .section { margin-top: 36px; }
    .section-title { display: flex; justify-content: space-between; align-items: end; gap: 18px; margin-bottom: 16px; }
    .section-title h2 { margin: 0; font-size: 23px; letter-spacing: -.03em; }
    .section-title p { color: var(--muted); margin: 2px 0 0; }
    .grid { display: grid; gap: 16px; }
    .grid-4 { grid-template-columns: repeat(4,minmax(0,1fr)); }
    .grid-3 { grid-template-columns: repeat(3,minmax(0,1fr)); }
    .grid-2 { grid-template-columns: repeat(2,minmax(0,1fr)); }
    .card { background: var(--surface); border: 1px solid var(--line); border-radius: var(--radius); padding: 21px; box-shadow: var(--shadow-sm); }
    .card h2, .card h3, .card h4 { margin: 0 0 8px; line-height: 1.2; letter-spacing: -.025em; }
    .card p { color: var(--muted); margin: 0; }
    .metric-card { min-height: 142px; position: relative; overflow: hidden; }
    .metric-card::after { content: ""; position: absolute; inset: auto -30px -50px auto; width: 110px; height: 110px; border-radius: 50%; background: var(--green-2); opacity: .6; }
    .metric-label { color: var(--muted); font-size: 11px; font-weight: 750; letter-spacing: .09em; text-transform: uppercase; }
    .metric-value { display: block; margin: 10px 0 1px; font-size: 32px; font-weight: 820; line-height: 1; letter-spacing: -.05em; }
    .metric-sub { color: var(--muted); font-size: 12px; }
    .weight-card { border-top: 4px solid var(--accent,var(--green)); }
    .weight-head { display:flex; justify-content:space-between; gap:12px; align-items:start; }
    .weight { font-size: 27px; font-weight: 830; letter-spacing: -.05em; color: var(--accent,var(--green)); }
    .question-count { color:var(--muted); font-size:12px; }
    .bar { width:100%; height:7px; background:var(--surface-2); border-radius:99px; overflow:hidden; margin-top:14px; }
    .bar span { display:block; height:100%; border-radius:inherit; background:var(--accent,var(--green)); transition:width .45s ease; }
    .recommendation { background: linear-gradient(120deg,var(--green-2),var(--surface)); border-color: color-mix(in srgb,var(--green) 27%,var(--line)); }
    .recommendation .tag { color: var(--green); }
    .tag, .pill { display:inline-flex; align-items:center; gap:5px; min-height:24px; padding:3px 8px; border-radius:99px; background:var(--surface-2); color:var(--muted); font-size:10px; font-weight:800; letter-spacing:.06em; text-transform:uppercase; }
    .tag.green { color:var(--green); background:var(--green-2); }
    .tag.gold { color:var(--gold); background:var(--gold-2); }
    .tag.coral { color:var(--coral); background:var(--coral-2); }
    .module-list { display:grid; gap:13px; }
    .module-row { display:grid; grid-template-columns:58px minmax(0,1fr) auto; align-items:center; gap:17px; padding:18px; background:var(--surface); border:1px solid var(--line); border-radius:16px; box-shadow:var(--shadow-sm); }
    .module-row:hover { border-color: color-mix(in srgb,var(--domain-color) 50%,var(--line)); }
    .module-num { width:48px; height:48px; display:grid; place-items:center; border-radius:14px; background:color-mix(in srgb,var(--domain-color) 13%,var(--surface)); color:var(--domain-color); font-weight:850; }
    .module-row h3 { margin:0 0 3px; font-size:17px; }
    .module-meta { color:var(--muted); font-size:12px; }
    .module-actions { display:flex; align-items:center; gap:11px; }
    .progress-disc { width:45px; height:45px; border-radius:50%; display:grid; place-items:center; font-size:10px; font-weight:800; background:conic-gradient(var(--domain-color) var(--pct),var(--surface-2) 0); position:relative; }
    .progress-disc::before { content:""; position:absolute; inset:5px; border-radius:50%; background:var(--surface); }
    .progress-disc span { position:relative; }
    .lesson-grid { display:grid; gap:10px; margin-top:14px; }
    .lesson-link { width:100%; text-align:left; border:1px solid var(--line); background:var(--paper); color:var(--ink); border-radius:12px; padding:12px 14px; display:flex; justify-content:space-between; align-items:center; gap:10px; }
    .lesson-link:hover { border-color:var(--green); }
    .lesson-link.done { background:var(--green-2); }
    .lesson-link span:last-child { color:var(--muted); font-size:12px; white-space:nowrap; }
    .lesson-layout { display:grid; grid-template-columns:minmax(0,1fr) 270px; gap:22px; align-items:start; }
    .lesson-hero { padding:clamp(25px,4vw,44px); border-radius:22px; color:white; background:linear-gradient(135deg,var(--navy),var(--navy-2)); margin-bottom:17px; }
    .lesson-hero h1 { font-size:clamp(29px,4vw,48px); line-height:1.04; letter-spacing:-.05em; margin:9px 0 12px; }
    .lesson-hero p { color:#b6cdca; max-width:750px; font-size:16px; }
    .lesson-meta { display:flex; flex-wrap:wrap; gap:8px; margin-top:18px; }
    .lesson-meta span { padding:5px 9px; background:rgba(255,255,255,.08); border:1px solid rgba(255,255,255,.13); border-radius:99px; color:#c8dcd8; font-size:11px; }
    .lesson-block { margin-bottom:16px; }
    .lesson-block h2 { margin:0 0 12px; font-size:21px; }
    .lesson-block ul { padding-left:19px; margin:8px 0; }
    .lesson-block li + li { margin-top:7px; }
    details.deep { border:1px solid var(--line); border-radius:14px; background:var(--surface); }
    details.deep summary { padding:16px 18px; font-weight:780; cursor:pointer; }
    details.deep > div { padding:0 18px 18px; color:var(--muted); }
    .concept-grid { display:grid; grid-template-columns:repeat(2,minmax(0,1fr)); gap:11px; }
    .concept { padding:16px; border:1px solid var(--line); background:var(--surface); border-radius:13px; }
    .concept strong { display:block; color:var(--green); margin-bottom:4px; }
    .concept span { color:var(--muted); }
    .callout { border-left:4px solid var(--green); background:var(--green-2); border-radius:0 13px 13px 0; padding:17px 19px; }
    .callout.trap { border-color:var(--coral); background:var(--coral-2); }
    .callout.gold { border-color:var(--gold); background:var(--gold-2); }
    .callout h3 { margin:0 0 4px; font-size:15px; }
    .callout p, .callout li { color:var(--ink); opacity:.86; }
    .sticky-card { position:sticky; top:94px; }
    .lesson-nav-list { display:grid; gap:6px; margin:14px 0; }
    .lesson-nav-list button { text-align:left; padding:8px 10px; border:0; background:transparent; color:var(--muted); border-radius:9px; }
    .lesson-nav-list button:hover { background:var(--surface-2); color:var(--ink); }
    .check-card { padding:20px; border:1px solid var(--line); border-radius:15px; background:var(--surface); }
    .check-options { display:grid; gap:8px; margin:14px 0; }
    .option-btn { display:flex; gap:10px; align-items:flex-start; width:100%; text-align:left; padding:12px 13px; border:1px solid var(--line); border-radius:11px; background:var(--paper); color:var(--ink); }
    .option-btn:hover { border-color:var(--green); }
    .option-btn.selected { border-color:var(--blue); background:var(--blue-2); }
    .option-btn.correct { border-color:var(--green); background:var(--green-2); }
    .option-btn.incorrect { border-color:var(--coral); background:var(--coral-2); }
    .option-letter { flex:0 0 24px; height:24px; display:grid; place-items:center; border-radius:7px; border:1px solid var(--line); font-size:11px; font-weight:850; }
    .answer-reasons { display:grid; gap:8px; margin-top:14px; }
    .reason { padding:11px 13px; border-radius:10px; background:var(--paper); border-left:3px solid var(--line); color:var(--muted); font-size:13px; }
    .reason.correct { border-color:var(--green); background:var(--green-2); color:var(--ink); }
    .quiz-shell { max-width:920px; margin:0 auto; }
    .quiz-top { display:flex; align-items:center; justify-content:space-between; gap:16px; margin-bottom:16px; }
    .quiz-progress { flex:1; }
    .timer { min-width:95px; text-align:center; padding:8px 12px; background:var(--navy); color:white; border-radius:10px; font-variant-numeric:tabular-nums; font-weight:800; }
    .timer.warning { background:var(--coral); }
    .question-card { padding:clamp(22px,4vw,38px); }
    .question-card h2 { font-size:clamp(21px,3vw,30px); margin:12px 0 20px; line-height:1.3; }
    .quiz-actions { display:flex; justify-content:space-between; gap:10px; margin-top:18px; }
    .setup-card { max-width:860px; }
    .control-grid { display:grid; grid-template-columns:repeat(2,minmax(0,1fr)); gap:15px; margin:18px 0; }
    .field label { display:block; font-size:12px; font-weight:760; margin-bottom:6px; color:var(--muted); }
    .field select { width:100%; padding:11px 12px; border:1px solid var(--line); border-radius:10px; background:var(--paper); color:var(--ink); }
    .toggle-row { display:flex; align-items:center; justify-content:space-between; gap:16px; padding:12px 0; border-top:1px solid var(--line); }
    .switch { position:relative; width:45px; height:26px; }
    .switch input { opacity:0; width:0; height:0; }
    .slider { position:absolute; inset:0; border-radius:99px; background:var(--surface-2); border:1px solid var(--line); transition:.2s; }
    .slider::before { content:""; position:absolute; width:18px; height:18px; top:3px; left:3px; border-radius:50%; background:white; box-shadow:0 1px 4px rgba(0,0,0,.25); transition:.2s; }
    input:checked + .slider { background:var(--green); }
    input:checked + .slider::before { transform:translateX(19px); }
    .flash-stage { max-width:760px; margin:25px auto; perspective:1000px; }
    .flashcard { position:relative; min-height:340px; transform-style:preserve-3d; transition:transform .5s cubic-bezier(.2,.8,.2,1); cursor:pointer; }
    .flashcard.flipped { transform:rotateY(180deg); }
    .flash-face { position:absolute; inset:0; backface-visibility:hidden; padding:clamp(28px,6vw,58px); border-radius:24px; background:var(--surface); border:1px solid var(--line); box-shadow:var(--shadow); display:flex; flex-direction:column; align-items:center; justify-content:center; text-align:center; }
    .flash-face.back { transform:rotateY(180deg); background:var(--navy); color:white; }
    .flash-face h2 { font-size:clamp(25px,4vw,38px); letter-spacing:-.04em; }
    .flash-face.back p { color:#bdd2ce; font-size:17px; }
    .flash-controls { display:flex; justify-content:center; flex-wrap:wrap; gap:9px; }
    .review-item { display:grid; grid-template-columns:44px minmax(0,1fr) auto; gap:14px; align-items:start; }
    .review-icon { width:42px; height:42px; border-radius:12px; display:grid; place-items:center; background:var(--coral-2); color:var(--coral); font-weight:850; }
    .exam-layout { display:grid; grid-template-columns:minmax(0,1fr) 230px; gap:18px; align-items:start; }
    .exam-palette { position:sticky; top:94px; }
    .palette { display:grid; grid-template-columns:repeat(5,1fr); gap:6px; margin-top:13px; }
    .palette button { aspect-ratio:1; border:1px solid var(--line); background:var(--paper); color:var(--ink); border-radius:8px; font-size:11px; }
    .palette button.answered { background:var(--green-2); border-color:var(--green); }
    .palette button.flagged { box-shadow:inset 0 -3px var(--gold); }
    .palette button.current { outline:2px solid var(--blue); }
    .exam-score { text-align:center; padding:30px; }
    .exam-score strong { display:block; font-size:64px; letter-spacing:-.07em; }
    .domain-result { display:grid; grid-template-columns:minmax(140px,1fr) 2fr 65px; align-items:center; gap:12px; margin:11px 0; }
    .plan-cards { display:grid; grid-template-columns:repeat(3,minmax(0,1fr)); gap:14px; }
    .plan-card { position:relative; }
    .plan-card.selected { border-color:var(--green); box-shadow:0 0 0 3px color-mix(in srgb,var(--green) 14%,transparent); }
    .plan-card .duration { color:var(--green); font-weight:850; font-size:29px; }
    .task-list { display:grid; gap:8px; }
    .task { display:grid; grid-template-columns:auto 52px minmax(0,1fr) auto; gap:12px; align-items:center; padding:13px; border:1px solid var(--line); border-radius:12px; background:var(--surface); }
    .task input { width:19px; height:19px; accent-color:var(--green); }
    .task.done .task-title { text-decoration:line-through; color:var(--muted); }
    .day { font-size:10px; font-weight:850; color:var(--muted); text-transform:uppercase; letter-spacing:.07em; }
    .chart { display:flex; align-items:end; gap:8px; height:160px; padding-top:20px; }
    .chart-col { flex:1; min-width:18px; height:100%; display:flex; flex-direction:column; justify-content:end; gap:5px; text-align:center; color:var(--muted); font-size:9px; }
    .chart-bar { min-height:3px; border-radius:5px 5px 2px 2px; background:linear-gradient(var(--green),color-mix(in srgb,var(--green) 45%,var(--blue))); }
    .empty { text-align:center; padding:45px 24px; }
    .empty .empty-icon { width:66px; height:66px; border-radius:20px; margin:0 auto 15px; display:grid; place-items:center; background:var(--green-2); color:var(--green); font-size:25px; }
    .notice { padding:12px 14px; border:1px solid var(--line); background:var(--surface-2); color:var(--muted); border-radius:11px; font-size:12px; }
    .source-note { margin-top:28px; color:var(--muted); font-size:11px; }
    .toast { position:fixed; right:22px; bottom:22px; z-index:100; padding:12px 16px; background:var(--navy); color:white; border-radius:11px; box-shadow:var(--shadow); transform:translateY(90px); opacity:0; transition:.25s; }
    .toast.show { transform:none; opacity:1; }
    dialog { width:min(540px,calc(100vw - 30px)); border:1px solid var(--line); border-radius:20px; background:var(--surface); color:var(--ink); padding:0; box-shadow:var(--shadow); }
    dialog::backdrop { background:rgba(5,17,16,.64); backdrop-filter:blur(4px); }
    .dialog-body { padding:27px; }
    .dialog-body h2 { margin-top:0; }
    .dialog-actions { display:flex; justify-content:flex-end; gap:9px; margin-top:22px; }
    .mobile-menu { display:none; }
    .sr-only { position:absolute!important; width:1px!important; height:1px!important; padding:0!important; margin:-1px!important; overflow:hidden!important; clip:rect(0,0,0,0)!important; white-space:nowrap!important; border:0!important; }
    @media (max-width: 1080px) {
      .grid-4 { grid-template-columns:repeat(2,minmax(0,1fr)); }
      .grid-3 { grid-template-columns:repeat(2,minmax(0,1fr)); }
      .hero { grid-template-columns:1fr; }
      .readiness-card { max-width:480px; }
      .lesson-layout { grid-template-columns:1fr; }
      .sticky-card { position:static; }
      .exam-layout { grid-template-columns:1fr; }
      .exam-palette { position:static; }
    }
    @media (max-width: 780px) {
      :root { --sidebar:0px; }
      .shell { display:block; padding-bottom:69px; }
      .sidebar { inset:auto 0 0; width:auto; height:69px; padding:8px 10px; flex-direction:row; overflow-x:auto; border-top:1px solid rgba(255,255,255,.12); }
      .brand, .sidebar-foot { display:none; }
      .nav { display:flex; min-width:max-content; width:100%; justify-content:space-around; gap:3px; }
      .nav button { width:auto; min-width:62px; padding:7px 9px; flex-direction:column; gap:1px; text-align:center; font-size:9px; }
      .nav-icon { font-size:16px; }
      .nav button.active { box-shadow:inset 0 3px #5fd1bc; }
      .content { grid-column:auto; }
      .topbar { min-height:62px; padding:10px 16px; }
      .top-actions .soft-btn { display:none; }
      .main { padding:22px 15px 35px; }
      .hero { min-height:auto; padding:29px 23px; border-radius:20px; }
      .hero h1 { font-size:38px; }
      .grid-3, .grid-2, .plan-cards { grid-template-columns:1fr; }
      .page-head { align-items:start; flex-direction:column; }
      .module-row { grid-template-columns:48px minmax(0,1fr); }
      .module-actions { grid-column:1/-1; justify-content:flex-end; }
      .concept-grid, .control-grid { grid-template-columns:1fr; }
      .domain-result { grid-template-columns:1fr 50px; }
      .domain-result .bar { grid-column:1/-1; grid-row:2; }
      .task { grid-template-columns:auto 42px minmax(0,1fr); }
      .task .pill { display:none; }
    }
    @media (max-width: 480px) {
      .grid-4 { grid-template-columns:1fr; }
      .top-title { max-width:190px; white-space:nowrap; overflow:hidden; text-overflow:ellipsis; }
      .hero-actions > * { flex:1; }
      .mini-metrics { grid-template-columns:1fr; }
      .mini-metrics div { display:flex; justify-content:space-between; }
      .flashcard { min-height:390px; }
      .review-item { grid-template-columns:38px minmax(0,1fr); }
      .review-item > .soft-btn { grid-column:2; }
    }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { scroll-behavior:auto!important; animation-duration:.01ms!important; transition-duration:.01ms!important; }
    }
    @media print {
      .sidebar,.topbar,.hero-actions,.lesson-actions,.source-note { display:none!important; }
      .shell,.content { display:block; }
      body { background:white; color:black; }
      .main { max-width:none; padding:0; }
      .card,.lesson-hero { box-shadow:none; break-inside:avoid; }
    }
  </style>
</head>
<body>
  <a class="skip" href="#main">Skip to course content</a>
  <div class="shell">
    <aside class="sidebar" aria-label="Primary navigation">
      <div class="brand"><div class="brand-mark">S</div><div><strong>SIE Compass</strong><span>Exam prep system</span></div></div>
      <nav class="nav" id="nav">
        <button data-view="home"><span class="nav-icon">⌂</span><span>Home</span></button>
        <button data-view="dashboard"><span class="nav-icon">◫</span><span>Dashboard</span></button>
        <button data-view="course"><span class="nav-icon">▤</span><span>Course</span></button>
        <button data-view="quiz"><span class="nav-icon">✓</span><span>Quiz</span></button>
        <button data-view="flashcards"><span class="nav-icon">◇</span><span>Cards</span></button>
        <button data-view="review"><span class="nav-icon">↻</span><span>Review</span></button>
        <button data-view="exam"><span class="nav-icon">◷</span><span>Mock exam</span></button>
        <button data-view="planner"><span class="nav-icon">□</span><span>Planner</span></button>
        <button data-view="analytics"><span class="nav-icon">↗</span><span>Analytics</span></button>
      </nav>
      <div class="sidebar-foot">
        <div class="side-label">Course progress</div>
        <div class="side-progress"><span id="sideProgress"></span></div>
        <div class="side-stat"><span id="sideCompleted">0 lessons</span><strong id="sidePercent">0%</strong></div>
      </div>
    </aside>
    <div class="content">
      <header class="topbar">
        <div><div class="eyebrow" id="topEyebrow">SIE study system</div><div class="top-title" id="topTitle">Build exam confidence, one decision at a time.</div></div>
        <div class="top-actions">
          <button class="soft-btn" data-action="quick-study">15-minute focus</button>
          <button class="icon-btn" id="themeToggle" aria-label="Switch color theme" title="Switch color theme">◐</button>
        </div>
      </header>
      <main class="main" id="main" tabindex="-1"></main>
    </div>
  </div>
  <div class="toast" id="toast" role="status" aria-live="polite"></div>
  <dialog id="dialog"><div class="dialog-body" id="dialogBody"></div></dialog>
  <script>
    'use strict';

    const DOMAINS = {
      d1:{short:'Capital Markets',name:'Knowledge of Capital Markets',weight:16,count:12,color:'#4169a5'},
      d2:{short:'Products & Risk',name:'Understanding Products and Their Risks',weight:44,count:33,color:'#0f766e'},
      d3:{short:'Trading & Accounts',name:'Trading, Customer Accounts and Prohibited Activities',weight:31,count:23,color:'#b77822'},
      d4:{short:'Regulatory Framework',name:'Overview of the Regulatory Framework',weight:9,count:7,color:'#bd5546'}
    };
    const L=(id,title,minutes,summary,why,objectives,deep,concepts,trap,example,memory,finra,summaryPoints)=>({id,title,minutes,summary,why,objectives,deep,concepts,trap,example,memory,finra,summaryPoints});
    const modules = [
      {id:'m1',domain:'d1',title:'The regulatory map',description:'Who protects investors, who writes rules, and who performs each market role.',lessons:[
        L('l1','SEC, SROs and investor protection',22,'Start with jurisdiction: the SEC is the federal regulator; FINRA, exchanges and the MSRB are self-regulatory organizations operating under SEC oversight.','FINRA frequently tests which organization has authority—not merely what an acronym stands for.',['Distinguish the SEC from FINRA and other SROs','Match the MSRB, SIPC and FDIC to their actual functions','Avoid protection-limit and jurisdiction traps'],'The SEC administers federal securities laws and oversees SROs. FINRA regulates broker-dealers and their associated persons. The MSRB writes rules for municipal securities firms and professionals, while enforcement is performed by FINRA, the SEC and bank regulators. SIPC is not insurance against investment loss; it helps restore customer cash and securities if a SIPC-member broker-dealer fails. FDIC coverage applies to eligible bank deposits, not securities.',['SEC|Federal regulator; administers securities laws and oversees SROs.','FINRA|SRO for broker-dealers; writes and enforces member rules and administers qualification exams.','MSRB|Writes municipal securities and municipal adviser rules; it does not enforce them.','SIPC|Customer-asset protection when a member broker-dealer fails—not market-loss insurance.'],'Do not choose SIPC merely because a customer lost money. Market declines, unsuitable recommendations and issuer defaults are not SIPC events.','A broker-dealer becomes insolvent and customer securities are missing. SIPC may assist. If a stock simply falls 40%, SIPC does not reimburse the decline.','SEC oversees; SROs supervise. MSRB makes rules; FINRA may enforce them.','Expect role-matching questions. Read the verb: writes, enforces, insures deposits, or protects custody assets.',['SEC = federal securities regulator','FINRA = broker-dealer SRO','MSRB writes municipal rules','SIPC is not market-loss insurance']),
        L('l2','Market participants and plumbing',20,'Markets work because specialized participants issue, distribute, trade, clear, settle and safeguard securities.','Questions often describe a function and ask you to name the participant.',['Differentiate issuers, underwriters, broker-dealers and advisers','Explain principal versus agency capacity','Place DTCC, transfer agents, custodians and OCC in the trade lifecycle'],'An issuer raises capital. An underwriter helps structure and distribute a new offering. A broker executes for customers as agent and may trade from inventory as dealer/principal. An investment adviser gives securities advice for compensation. Market makers publish quotations and stand ready to trade. Clearing corporations compare and settle trades; depositories hold securities in book-entry form. Transfer agents maintain issuer ownership records. The OCC clears and guarantees listed options contracts.',['Broker|Acts as agent for a customer and earns a commission.','Dealer|Acts as principal from its own inventory and earns a markup or markdown.','Transfer agent|Maintains ownership records and handles transfers for an issuer.','DTCC/OCC|Market infrastructure for clearing and settlement; OCC specializes in listed options.'],'An introducing broker can open and service accounts while a clearing broker carries assets and completes settlement.','A firm sells a bond from its own inventory to a customer. It is acting as principal, even if the customer calls the person a broker.','Broker = behalf; dealer = inventory.','Capacity, compensation and custody point to the right participant.',['Issuer creates securities','Underwriter distributes new issues','Agent earns commission; principal earns markup/markdown','Clearing and custody are separate functions'])
      ]},
      {id:'m2',domain:'d1',title:'Markets and new offerings',description:'How securities move from issuers to investors—and then between investors.',lessons:[
        L('l3','Primary, secondary, third and fourth markets',18,'The primary market finances issuers; the secondary market provides liquidity after issuance. Third and fourth markets describe specific institutional trading venues.','A classic exam trap is confusing “new to this investor” with “newly issued.”',['Classify transactions by market','Explain why secondary-market liquidity supports capital formation','Distinguish exchange, OTC, third and fourth markets'],'A primary transaction sends proceeds to the issuer. In a secondary transaction, an investor sells an outstanding security to another investor and the issuer receives no proceeds. The third market is OTC trading of exchange-listed securities. The fourth market is direct institution-to-institution trading, often through electronic networks, without a broker-dealer intermediary.',['Primary|New securities; issuer receives proceeds.','Secondary|Outstanding securities trade; seller receives proceeds.','Third|Exchange-listed securities trade OTC.','Fourth|Institutions trade directly with one another.'],'An IPO stock bought a week later on an exchange is a secondary-market trade, despite the company being newly public.','A pension fund buys stock directly from another institution through a network: fourth market.','Primary = proceeds to producer (issuer).','Follow the money. If proceeds reach the issuer, think primary.',['Primary finances issuers','Secondary supplies liquidity','Third = listed OTC','Fourth = institution to institution']),
        L('l4','Underwriting and offering documents',24,'Underwriters connect issuers with investors and assume different levels of distribution risk depending on the agreement.','Questions pair underwriting methods, offering types and disclosure documents.',['Compare firm commitment and best efforts','Distinguish IPO, follow-on, secondary and private offerings','Match prospectus and official statement to the offering'],'In a firm commitment, the underwriter buys the securities from the issuer and resells them, taking inventory risk. In a best-efforts offering, it acts as agent and sells as much as possible. A syndicate spreads risk; the selling group helps distribute without taking underwriting liability. Registered corporate offerings use a prospectus. Municipal issuers use an official statement because municipal securities are generally exempt from Securities Act registration. Regulation D provides exemptions for certain private offerings.',['Firm commitment|Underwriter purchases the issue and bears resale risk.','Best efforts|Underwriter acts as agent; issuer bears unsold risk.','Prospectus|Disclosure document for a registered offering; not SEC approval.','Official statement|Primary disclosure document for a municipal offering.'],'The SEC allowing a registration statement to become effective does not mean it approves the investment or guarantees disclosure accuracy.','An issuer needs certainty about proceeds. A firm-commitment deal transfers distribution risk to the underwriter.','Firm commitment = firm owns it.','Look for who bears unsold-inventory risk and never equate registration with approval.',['IPO = first public sale by issuer','Follow-on = additional issuer shares','Secondary offering can mean existing holders sell','Disclosure is not endorsement'])
      ]},
      {id:'m3',domain:'d1',title:'Economics for market questions',description:'Rates, policy, cycles and indicators translated into likely security-price effects.',lessons:[
        L('l5','The Fed, rates and policy',24,'Monetary policy changes money and credit conditions; fiscal policy changes government spending and taxation.','FINRA tests direction: what action is tightening or easing, and what usually happens to rates and bond prices.',['Separate monetary from fiscal policy','Predict the effect of open-market purchases and sales','Relate interest rates to bond prices and economic activity'],'The Federal Reserve buys government securities to add reserves, encourage lending and ease credit; it sells to drain reserves and tighten credit. A lower discount rate is generally accommodative. The federal funds rate is the rate banks charge one another for overnight reserve loans. Fiscal policy belongs to Congress and the executive branch. Rising market rates generally pressure existing fixed-rate bond prices downward.',['Open-market purchase|Fed pays dealers, adding reserves and easing credit.','Open-market sale|Removes reserves and tends to tighten credit.','Discount rate|Rate a Reserve Bank charges eligible institutions.','Federal funds rate|Overnight rate banks charge one another for reserves.'],'Do not invert the bond relationship: existing fixed coupons become less attractive when new rates rise, so their prices fall.','The Fed sells Treasuries. Bank reserves shrink, credit tightens and rates tend to face upward pressure.','Fed buys = money multiplies. Rates up, bonds down.','Most questions ask directional relationships, not economic forecasting.',['Monetary = Fed','Fiscal = tax and spending','Fed purchase is easing','Rates and fixed-rate bond prices move oppositely']),
        L('l6','Cycles, indicators and global factors',21,'Economic data help classify where activity is headed, where it is now and what has already happened.','The exam tests category recognition and broad sector effects, not advanced econometrics.',['Order the business cycle','Classify leading, coincident and lagging indicators','Distinguish GDP, GNP and currency effects'],'Expansion leads toward a peak; contraction follows, ending at a trough. Leading indicators tend to turn before the overall economy, coincident indicators move with it, and lagging indicators confirm an established trend. GDP measures production within a country; GNP focuses on production by a country’s nationals. A stronger dollar makes imported goods cheaper for U.S. buyers but can make U.S. exports more expensive abroad.',['Expansion|Rising output and employment toward a peak.','Contraction|Falling activity after a peak toward a trough.','GDP|Output produced within domestic borders.','Inflation|Broad loss of purchasing power; especially harmful to fixed payments.'],'“Leading” does not mean most important; it describes timing relative to the economy.','Rising new building permits may signal future activity, while unemployment duration may confirm weakness after it begins.','Peak → contraction → trough → expansion.','Identify timing words: anticipates, moves with, or confirms.',['Business cycles repeat but are not clockwork','Inflation hurts fixed purchasing power','GDP is domestic location','Currency changes create currency risk'])
      ]},
      {id:'m4',domain:'d2',title:'Equity securities',description:'Ownership, priority, voting and the equity features most likely to be compared.',lessons:[
        L('l7','Common and preferred stock',25,'Common stock is residual ownership with voting rights and variable dividends; preferred stock trades some upside and voting power for dividend and liquidation priority.','Many questions ask which right or risk belongs to which class.',['Compare common and preferred stock','Order claims in liquidation','Recognize cumulative and convertible preferred features'],'Common shareholders generally vote, have limited liability and receive whatever remains after creditors and preferred holders. Preferred dividends are stated but not guaranteed. Cumulative preferred carries unpaid dividends forward before common dividends can resume. Convertible preferred can be exchanged for common stock under stated terms, adding participation potential.',['Common stock|Residual ownership, voting rights and greatest long-run upside.','Preferred stock|Dividend and liquidation priority over common; typically limited voting rights.','Cumulative|Missed preferred dividends accumulate.','Convertible|Holder may exchange the security for common stock.'],'Priority does not make preferred stock a debt security. Dividends may be omitted, and preferred holders are still owners.','If a company skips two cumulative preferred dividends, those arrears must be addressed before a common dividend.','Debt before preferred before common.','Questions focus on the tradeoff between ownership upside and payment priority.',['Common votes; preferred has priority','Both are equity','Dividends are not contractual interest','Limited liability protects personal assets']),
        L('l8','Rights, warrants, ADRs and restricted stock',20,'Rights and warrants can lead to common ownership; ADRs provide U.S.-traded exposure to foreign shares.','Similar-looking equity instruments differ mainly by issuer, life and purpose.',['Compare rights and warrants','Explain ADR currency and political risk','Recognize the purpose of Rule 144 restrictions'],'Existing shareholders may receive short-lived rights to buy new shares, often below market, helping preserve proportionate ownership. Warrants are longer-lived issuer-created instruments, often attached to a bond or preferred offering as a sweetener. ADRs are U.S.-dollar receipts representing foreign shares held by a depositary; they still carry company, country and currency risk. Rule 144 governs certain resales of restricted and control securities.',['Right|Short-term privilege generally issued to existing shareholders.','Warrant|Longer-term issuer security often used as an offering sweetener.','ADR|Receipt trading in the U.S. that represents foreign shares.','Restricted stock|Privately acquired shares subject to resale conditions.'],'ADR dollar trading does not eliminate currency risk in the underlying foreign investment.','A company gives current holders two weeks to buy new shares before the public. Those instruments are rights.','Rights are rapid; warrants wait.','Use time horizon and recipient: short to current holders means rights.',['Rights help preserve ownership percentage','Warrants can dilute when exercised','ADRs add country and currency risk','Restricted is not the same as unregistered forever'])
      ]},
      {id:'m5',domain:'d2',title:'Debt securities',description:'Bond math without the noise: issuer promises, price/yield logic, credit and structure.',lessons:[
        L('l9','Bond anatomy, prices and yields',28,'A bond is an issuer’s promise to pay interest and return principal; its market price changes as rates, credit and time change.','Bond price/yield direction is one of the highest-yield relationships on the SIE.',['Define par, coupon, maturity and current yield','Apply the inverse price-yield relationship','Distinguish nominal, current, YTM and YTC concepts'],'Par is commonly $1,000 for a corporate bond. The coupon rate determines stated annual interest from par. Current yield equals annual interest divided by current market price. Yield to maturity includes coupon income and the gain or loss as price moves toward par by maturity. For a premium callable bond, yield to call is often the most conservative quoted yield because an early call can accelerate the loss of premium.',['Coupon rate|Annual interest divided by par.','Current yield|Annual interest divided by market price.','YTM|Return if held to maturity with stated assumptions.','Basis point|One hundredth of one percentage point: 0.01%.'],'A 6% bond at 120 still pays $60 annually, not 6% of $1,200. Its current yield is 5%.','Rates rise from 5% to 7%; an outstanding 5% fixed coupon must fall in price to compete.','Rates up, bond prices down—and vice versa.','Expect comparison questions more often than long calculations.',['Coupon uses par','Current yield uses market price','Premium price means yield below coupon','Long maturity and low coupon increase rate sensitivity']),
        L('l10','Treasury, corporate and agency debt',23,'Debt sectors shift credit, tax, maturity and prepayment risk rather than eliminating risk.','The test asks for the most relevant risk and the security’s defining backing.',['Classify Treasury bills, notes and bonds','Compare government, agency and corporate credit characteristics','Explain MBS prepayment risk'],'Treasury bills mature in one year or less and are issued at a discount; notes have intermediate maturities and bonds longer maturities. Treasury interest is subject to federal income tax but exempt from state and local income tax. Corporate bonds depend on issuer credit. Mortgage-backed securities pass through borrower payments and expose investors to prepayment risk: falling rates can return principal early just when reinvestment rates are lower.',['T-bill|Short-term Treasury issued at a discount.','Debenture|Corporate bond backed by general credit, not a specific asset.','MBS|Pool-backed security with prepayment and extension risk.','Convertible bond|May be exchanged for common stock; usually offers a lower coupon.'],'Agency sponsorship does not automatically mean every agency security has the full faith and credit of the U.S. government.','Mortgage rates fall, homeowners refinance, and MBS principal returns early. The investor faces prepayment and reinvestment risk.','Falling rates make mortgages flee.','Match the sector to its distinctive risk: corporate credit, mortgage prepayment, Treasury rate/inflation.',['Treasuries still have market and inflation risk','Secured debt has identified collateral','Debentures rely on general credit','Calls benefit issuers when rates fall']),
        L('l11','Municipals and money markets',25,'Municipal bonds finance public purposes; money-market instruments are short-term debt used for liquidity and working capital.','Tax treatment, backing and maturity are frequent comparison points.',['Compare GO and revenue bonds','Recognize common money-market instruments','Use taxable-equivalent reasoning conceptually'],'A general obligation bond is backed by the issuer’s taxing power; a revenue bond is backed by specified project or enterprise revenues. Municipal interest is generally exempt from federal income tax, but capital gains are taxable and state treatment varies. Commercial paper is unsecured short-term corporate debt. Bankers’ acceptances support trade. Negotiable CDs are bank obligations. Treasury bills are short-term federal debt.',['GO bond|Backed by taxes and general municipal credit.','Revenue bond|Backed by facility or project revenues.','Commercial paper|Unsecured short-term corporate financing.','Bankers’ acceptance|Bank-guaranteed time draft often used in international trade.'],'Municipal interest is not “tax free” in every sense. Gains, original-issue discount issues and state taxes may still matter.','A toll-road bond repaid from toll collections is a revenue bond, even though a public authority issued it.','GO = government obligation; revenue = receipts.','Read the source of repayment before the issuer name.',['GO uses taxes','Revenue uses project income','Money-market means short maturity, not no risk','Tax benefits matter most at higher tax rates'])
      ]},
      {id:'m6',domain:'d2',title:'Options essentials',description:'Rights, obligations, moneyness and risk—at the depth the SIE expects.',lessons:[
        L('l12','Calls, puts and moneyness',27,'A call gives its buyer the right to buy; a put gives its buyer the right to sell. Sellers accept the corresponding obligation.','Options questions reward disciplined translation of the contract before any arithmetic.',['State each party’s right or obligation','Identify bullish and bearish positions','Determine basic moneyness and buyer breakeven'],'A call is in the money when market price is above strike; a put is in the money when market price is below strike. Buyers pay premiums and may choose whether to exercise. Sellers receive premiums and can be assigned. A long call is bullish; a long put is bearish or protective. Long-call breakeven at expiration is strike plus premium; long-put breakeven is strike minus premium.',['Long call|Right to buy; bullish; maximum loss is premium.','Long put|Right to sell; bearish/protective; maximum loss is premium.','Short call|Obligation to sell if assigned.','Short put|Obligation to buy if assigned.'],'“Right to buy” belongs to the call owner, not the call writer. Always identify long or short.','A 50 call with stock at 56 has $6 intrinsic value. If its premium was $8, it is in the money but the buyer is not yet profitable at expiration.','Call up; put down. Buyer has a right; writer has a requirement.','The exam separates moneyness from profit. Premium matters for profit, not for ITM status.',['Call ITM above strike','Put ITM below strike','Buyer max loss = premium','American style can exercise before expiration']),
        L('l13','Option risk, coverage and market structure',22,'Coverage pairs an option obligation with an asset or position that can satisfy it; uncovered writing can create substantial risk.','Questions emphasize maximum-loss intuition, hedging purpose and disclosure.',['Explain covered versus uncovered calls','Distinguish equity from index settlement','Place OCC and the ODD in the process'],'A covered call writer owns the underlying shares, limiting delivery risk but capping upside. An uncovered call can have theoretically unlimited loss as the stock rises. A protective put sets a floor under owned stock. Equity options generally settle through delivery of shares; broad-based index options settle in cash. Listed options are issued and guaranteed by the OCC, and customers receive the Options Disclosure Document before approval for options trading.',['Covered call|Stock owned plus short call; income with capped upside.','Protective put|Stock owned plus long put; downside floor.','OCC|Issuer and clearing guarantor for listed options.','ODD|Standardized risk disclosure for options customers.'],'Covered does not mean risk-free: the stock can still fall substantially.','An investor owns 100 shares at $48 and writes one 55 call. The premium cushions some downside, but gains above $55 are surrendered.','Covered call = covered delivery, not covered loss.','FINRA tests the economic purpose and risk more than multi-leg strategy algebra.',['Uncovered calls carry extreme risk','Index options are cash settled','OCC standardizes listed contracts','Options can hedge or speculate'])
      ]},
      {id:'m7',domain:'d2',title:'Funds and exchange-traded products',description:'Structure, pricing, sales charges and the packaged-product comparisons that drive exam questions.',lessons:[
        L('l14','Open-end, closed-end, UIT, ETF and ETN',27,'Packaged products can share diversification benefits while using very different legal structures and pricing mechanisms.','NAV versus market-price questions are frequent and easy points when structure is clear.',['Compare open-end and closed-end pricing','Recognize UIT, ETF and ETN structures','Separate an ETN’s credit risk from an ETF’s portfolio risk'],'An open-end mutual fund continuously issues and redeems shares with the fund at the next computed NAV; public offering price may include a sales charge. A closed-end fund has a fixed share count and trades intraday at a market price that may be above or below NAV. ETFs trade intraday but creation/redemption by authorized participants helps market price track NAV. A UIT has a generally fixed portfolio and a termination date. An ETN is unsecured issuer debt linked to an index.',['Open-end fund|Forward-priced at next NAV; redeemable with the fund.','Closed-end fund|Exchange-traded; market supply and demand set price.','ETF|Exchange-traded portfolio with creation/redemption mechanism.','ETN|Unsecured debt; adds issuer credit risk.'],'ETF and ETN names sound similar, but only the ETN is a debt obligation of its issuer.','Two funds hold the same stocks. One trades at a 7% discount to NAV intraday: it can be a closed-end fund, not an open-end fund.','Open-end opens/redeems at NAV; closed-end closes issuance and trades.','Look first at where the investor buys or sells: fund company versus exchange.',['Mutual funds use forward pricing','Closed-end funds can trade at premiums/discounts','ETFs trade intraday','ETNs have credit risk']),
        L('l15','Fund fees, share classes and discounts',25,'Sales-charge structures change when and how investors pay; breakpoint rules prevent customers from being overcharged.','FINRA tests both product knowledge and the ethical problem of breakpoint sales.',['Compute the conceptual effect of loads','Explain breakpoints, ROA and LOI','Compare common share-class fee patterns without overgeneralizing'],'Class A shares usually have a front-end load and lower ongoing distribution fees than other retail classes. Class C shares commonly have a level load and higher ongoing expenses. Breakpoints reduce front-end sales charges at stated investment levels. Rights of accumulation count eligible existing holdings. A letter of intent lets a customer state an intention to invest enough over a specified period, commonly 13 months, to receive a breakpoint now; missed commitments can cause retroactive adjustment.',['Front-end load|Deducted when shares are purchased.','CDSC|Contingent deferred sales charge paid on certain redemptions.','ROA|Uses qualifying existing holdings toward a breakpoint.','LOI|Uses intended purchases toward a breakpoint; not a binding purchase contract.'],'Recommending smaller separate purchases to keep each below a breakpoint is a prohibited breakpoint sale.','A customer has $45,000 in a fund family and invests $8,000 more. ROA may qualify the purchase for the $50,000 breakpoint.','ROA remembers; LOI looks forward.','Expect facts that reveal an overlooked discount rather than a pure definition.',['NAV excludes a sales load','POP may include a front-end load','Breakpoints apply to quantity purchases','Expenses reduce investor return'])
      ]},
      {id:'m8',domain:'d2',title:'Annuities and municipal fund securities',description:'Tax deferral, life-stage purpose, education accounts and their constraints.',lessons:[
        L('l16','Variable annuities',24,'A variable annuity is an insurance contract whose separate-account value fluctuates with selected investments and whose earnings grow tax deferred.','The exam focuses on tax treatment, surrender charges, suitability concerns and the insurance wrapper.',['Distinguish accumulation and annuitization','Explain separate versus general account exposure','Recognize tax and liquidity tradeoffs'],'Contributions to a nonqualified variable annuity are made after tax. Earnings grow tax deferred; withdrawals of earnings before basis are generally taxable as ordinary income and may face an additional tax before age 59½. The separate account holds variable subaccounts and is not guaranteed by the insurer. A death benefit and lifetime-income options are insurance features. Exchanges and replacements require careful review because surrender periods and expenses can restart.',['Accumulation unit|Measures ownership while contributions grow.','Annuity unit|Determines variable payments after annuitization.','Separate account|Supports variable performance; separate from insurer general assets.','Surrender charge|Declining early-withdrawal charge.'],'Tax deferred does not mean tax free, and placing an annuity inside an IRA usually adds no new tax deferral.','A 42-year-old needs money for a home in two years. A long surrender schedule makes a variable annuity a poor liquidity fit.','Annuity: tax later, liquidity limited.','Look for time horizon, liquidity need and whether tax deferral is already available.',['Variable value is not guaranteed','Earnings are taxed as ordinary income on withdrawal','Annuitization converts value to income','Surrender charges constrain liquidity']),
        L('l17','529 plans, ABLE accounts and LGIPs',20,'Municipal fund securities pool assets for education, disability-related expenses or public cash management.','Questions turn on who owns the account, permitted uses and tax consequences.',['Compare 529 savings and prepaid tuition plans','Separate owner from beneficiary control','Identify ABLE and LGIP purposes'],'A 529 savings plan owner selects investment options and retains control while a beneficiary uses qualified distributions. A prepaid tuition plan purchases future tuition units under plan rules. Contributions are not federally deductible, but qualified withdrawals are generally federally tax free; state benefits vary. ABLE accounts help eligible people with disabilities pay qualified disability expenses. LGIPs pool short-term funds of participating public entities.',['529 savings|Market-based account for qualified education expenses.','Prepaid tuition|Locks in or purchases tuition benefits under plan terms.','ABLE|Tax-advantaged disability-expense account for eligible individuals.','LGIP|Investment pool for state and local governmental entities.'],'The beneficiary does not automatically control a 529 account; the owner generally controls distributions and changes.','A parent opens a 529 for a child and later changes the beneficiary to another qualifying family member. The owner—not the first child—controls that decision.','529: owner controls, beneficiary benefits.','Expect purpose-and-control comparisons, plus qualified versus nonqualified distribution treatment.',['529s are municipal fund securities','Qualified use drives tax benefit','Plan-specific investment choices are limited','Direct- and adviser-sold versions can differ in cost'])
      ]},
      {id:'m9',domain:'d2',title:'Alternatives and investment risk',description:'Illiquidity, pass-through structures and the full risk vocabulary used across products.',lessons:[
        L('l18','DPPs, REITs and hedge funds',22,'Alternatives may provide income or diversification but commonly add illiquidity, complexity and manager or concentration risk.','SIE questions emphasize structure and liquidity—not advanced tax calculations.',['Describe DPP pass-through treatment','Compare listed and non-listed REIT liquidity','Recognize hedge-fund access and risk traits'],'DPPs such as limited partnerships pass income and losses through to investors and are generally illiquid. Limited partners have limited liability if they remain passive. REITs invest in real estate equity, mortgages or both; qualifying REITs can avoid entity-level tax by distributing required income. Listed REITs trade on exchanges; registered non-listed and private REITs can be difficult to value and sell. Hedge funds are private pools with flexible strategies, higher minimums and limited liquidity.',['DPP|Pass-through structure; limited partners provide capital and remain passive.','REIT|Real-estate pool; can be listed, non-listed or private.','Limited partner|Limited liability but no day-to-day management.','Hedge fund|Private, lightly accessible pool using flexible strategies.'],'Pass-through tax treatment does not create liquidity, guarantee income or make losses immediately usable in every circumstance.','A non-listed REIT quotes an estimated value but has no exchange market. The key concern is liquidity and valuation.','Alternative often means access is harder and exits are slower.','Look for the structural tradeoff: pass-through or special income treatment versus liquidity and complexity.',['DPPs generally lack a secondary market','Listed REITs are more liquid','Private funds may limit investors and redemptions','Alternative does not mean uncorrelated']),
        L('l19','Risk map and mitigation',26,'Every product question becomes easier when you name the risk before choosing the answer.','Risk identification accounts for a large share of product questions, directly or indirectly.',['Distinguish systematic from nonsystematic risk','Match products to credit, rate, inflation, liquidity and prepayment risk','Choose an appropriate mitigation strategy'],'Systematic risk affects the broad market and cannot be diversified away. Nonsystematic risk is issuer- or industry-specific and can be reduced through diversification. Credit risk is failure to pay; market risk is price movement; liquidity risk is inability to sell near fair value; inflation risk is loss of purchasing power. Interest-rate risk harms fixed-rate prices when rates rise. Reinvestment risk means cash flows may be reinvested at lower rates. Prepayment risk is especially relevant to mortgage pools.',['Systematic|Broad market risk; remains after diversification.','Nonsystematic|Issuer or industry risk; reducible by diversification.','Reinvestment|Future cash flows may earn less.','Prepayment|Principal returns sooner than expected.'],'Diversification reduces concentration risk, not all risk. It cannot eliminate a market-wide decline.','Owning 40 technology stocks is more diversified by issuer than owning one, but still concentrated by sector.','Systematic stays; specific can scatter.','The best answer identifies the risk most directly created by the stated feature.',['Diversification reduces nonsystematic risk','Long bonds carry more rate risk','Fixed payments carry purchasing-power risk','Hedging exchanges one risk profile for another'])
      ]},
      {id:'m10',domain:'d3',title:'Trading and settlement',description:'Orders, quotes, returns, settlement and corporate actions from entry to completion.',lessons:[
        L('l20','Orders, quotes and trade capacity',27,'Market orders prioritize execution; limit orders prioritize price; stop orders become market orders when triggered.','Order questions hinge on which condition is guaranteed—price or execution—plus whether the firm is agent or principal.',['Compare market, limit and stop orders','Interpret bid and ask from the dealer perspective','Recognize agency and principal trades'],'A market order seeks immediate execution but does not guarantee price. A buy limit sets the maximum purchase price; a sell limit sets the minimum sale price. A buy stop is placed above the market and a sell stop below it; once triggered, a stop order becomes a market order. Customers generally buy at the ask and sell at the bid. An agency confirmation shows a commission; a principal trade may show a markup or markdown.',['Market order|Execution priority; price can move.','Limit order|Price control; execution not guaranteed.','Stop order|Dormant until triggered, then becomes market.','Bid/ask|Dealer buys at bid and sells at ask.'],'A sell stop does not guarantee the stop price. In a fast decline, the execution can be materially lower after activation.','Stock is 48–48.10. A customer enters a buy limit at 47.50; it cannot execute above 47.50 and may never execute.','Buy high side (ask); sell low side (bid). Limit controls price.','Translate the order into a customer objective before applying mechanics.',['Market = execution priority','Limit = price priority','Buy stops sit above; sell stops below','Capacity changes compensation disclosure']),
        L('l21','Returns, settlement and corporate actions',28,'Trade economics continue after execution: positions settle, dividends follow dates and corporate actions adjust ownership units.','The current outline explicitly includes T+1 settlement and split effects.',['Apply regular-way T+1 settlement','Order dividend dates conceptually','Calculate simple split adjustments without changing total value'],'Most U.S. equity and corporate bond trades settle one business day after trade date (T+1). In a cash settlement, payment and delivery occur the same day. For dividends, the declaration date creates the schedule; an investor must purchase before the ex-dividend date to receive the dividend under regular-way settlement. A stock split changes shares and per-share price proportionally but not total position value at the split moment. A reverse split reduces shares and raises price proportionally.',['Trade date|Day the order executes.','Settlement date|Day cash and securities are exchanged.','Ex-dividend date|First day a buyer is not entitled to the declared dividend.','Stock split|Changes units and per-unit price, not immediate total value.'],'T+1 is the regular-way standard in the current outline; do not rely on old T+2 study material.','An investor owns 100 shares at $60. After a 3-for-2 split, the position is 150 shares at about $40, still worth $6,000 initially.','Shares multiply; price divides.','FINRA wants mechanics and investor effect, especially updated settlement rules.',['Regular way is generally T+1','Book entry is electronic ownership','Splits do not create wealth','Total return includes income and price change'])
      ]},
      {id:'m11',domain:'d3',title:'Customer accounts and compliance',description:'Registration, authority, margin, retirement, AML, privacy and communication duties.',lessons:[
        L('l22','Account types, registrations and margin',28,'Account form determines ownership, authority, tax treatment and risk; margin adds broker-dealer credit and amplified outcomes.','Many questions present an account fact and ask who may act or what approval is required.',['Compare individual, joint, custodial, trust and retirement accounts','Distinguish discretionary from nondiscretionary authority','Explain margin leverage at SIE depth'],'An individual account has one owner. Joint registrations define survivorship and ownership interests. UTMA/UGMA accounts are irrevocable gifts managed by a custodian for a minor; the minor is the beneficial owner. Trust authority comes from the trust document. Discretion over time, price or security generally requires written customer authorization and firm acceptance; time-and-price discretion for the same trading day is narrower. Margin uses borrowed funds, increasing gains and losses and permitting forced liquidation under agreement terms.',['UTMA|Irrevocable custodial gift; one custodian manages for one minor.','Discretionary|Representative chooses security, amount or action under written authority.','Cash account|Customer pays in full by settlement.','Margin account|Firm extends credit; customer signs a margin agreement.'],'A custodian controls the account but does not own the property; the minor owns the gift.','A representative chooses which stock and how much to buy. That is discretion even if the customer says “do what you think is best.”','Minor owns; custodian controls. Margin magnifies.','Identify ownership, control and credit separately.',['Account title controls legal ownership','Trustees follow the document','Margin can trigger forced sales','Options accounts need specific approval']),
        L('l23','AML, records and privacy',25,'Firms must know customers, monitor activity, safeguard information and preserve required records.','Scenario questions use red flags and ask the proper compliance response.',['Sequence placement, layering and integration','Distinguish CTR and SAR concepts','Recognize privacy and books-and-records duties'],'Money laundering commonly moves through placement, layering and integration. A Currency Transaction Report generally addresses large cash transactions; a Suspicious Activity Report addresses suspicious conduct and is confidential from the customer. Structuring means breaking transactions into smaller amounts to evade reporting. Customer identification procedures verify identity. OFAC sanctions screening and FinCEN reporting support financial-crime controls. Regulation S-P addresses nonpublic personal information and safeguards.',['Placement|Illicit funds enter the financial system.','Layering|Transactions obscure source and ownership.','Integration|Funds appear to return as legitimate wealth.','Structuring|Breaking transactions up to evade a reporting threshold.'],'Never tell a customer that a SAR was filed. Also, a cash amount below a threshold can still be suspicious.','A customer repeatedly deposits cash just below a reporting level and immediately wires it abroad. Escalate the pattern; do not help redesign it.','Place → layer → integrate. SAR stays secret.','Choose escalation and documentation over confrontation or tipping off.',['AML programs include policies, testing, training and a responsible person','CTR and SAR serve different purposes','OFAC focuses sanctions','Protect nonpublic personal information']),
        L('l24','Communications, KYC and best interest',23,'Firms must communicate fairly and base recommendations on customer facts, costs, risks and reasonably available alternatives.','The exam tests red flags more than lengthy legal standards.',['Recognize fair and balanced communication','Separate KYC from a recommendation analysis','Identify exaggerated, promissory and misleading claims'],'Communications may not be false, exaggerated, unwarranted or misleading. Retail communications generally require principal approval under applicable rules and must present risks and benefits fairly. KYC requires reasonable diligence to know essential facts about a customer and the authority of anyone acting for the customer. Regulation Best Interest applies to broker-dealer recommendations to retail customers and emphasizes disclosure, care, conflicts and compliance. No representative may guarantee against loss.',['KYC|Know essential customer facts and authority.','Recommendation|A call to action reasonably viewed as advice.','Reg BI|Best-interest obligation for broker-dealer recommendations to retail customers.','Fair and balanced|Benefits cannot be presented without material risks.'],'“Approved by the SEC” and “guaranteed not to lose” are red-flag phrases even when the security is registered.','An ad highlights a fund’s return but omits unusual risks and fees. It is not balanced merely because the return number is accurate.','Facts first, recommendation second.','Watch for absolute language, omitted risks and undisclosed conflicts.',['Registration is not approval','Recommendations require a customer profile','Material conflicts require handling','Telemarketing and do-not-call rules apply'])
      ]},
      {id:'m12',domain:'d3',title:'Prohibited activities',description:'Manipulation, insider trading and customer-abuse scenarios you must identify immediately.',lessons:[
        L('l25','Manipulation and insider trading',27,'Manipulation creates false market activity or prices; insider trading uses material nonpublic information in breach of duty or trust.','These are high-consequence questions where the ethical signal should be unmistakable.',['Identify common manipulation patterns','Define material nonpublic information','Recognize tipper, tippee and misappropriation exposure'],'Pump-and-dump promoters create enthusiasm, sell into the rise and leave others with losses. Marking the close uses trades to influence a closing price. Front running trades ahead of a known customer block order. Insider-trading liability can reach a corporate insider, a misappropriator, a tipper and a tippee who knows or should know the information was improperly disclosed. Information is material if a reasonable investor would consider it important and nonpublic until broadly disseminated and absorbed.',['Front running|Trading ahead of a known customer order.','Marking the close|Trading to improperly influence the closing price.','MNPI|Important information not broadly available.','Tippee|Recipient who may inherit liability when aware of an improper tip.'],'A rumor is not safe to trade merely because the person receiving it is outside the issuer. Ask how it was obtained and whether it is public.','An employee learns confidentially that an acquisition will be announced tomorrow and tells a friend to buy. Both the tipper and informed tippee face risk.','Material + nonpublic + duty = stop.','The correct response to possible MNPI is to halt and escalate, not investigate by trading.',['Manipulation distorts genuine supply and demand','Insider rules reach beyond officers','No loss is required for conduct to be prohibited','Penalties can be civil, regulatory and criminal']),
        L('l26','Customer funds, exploitation and other red flags',22,'Commercial honor means protecting customer assets, following authority and keeping truthful records.','The exam often asks for the action a representative must not take, even when a customer appears to consent.',['Spot improper borrowing, sharing and guarantees','Recognize senior-exploitation escalation','Know limits on unregistered activity and records'],'Representatives generally may not borrow from or lend to customers unless a permitted relationship and firm procedures allow it. Sharing in customer profits and losses is restricted and must be proportionate to financial contributions for representatives, with approval. Guarantees against loss are prohibited. Unregistered persons cannot solicit securities business, take orders or receive transaction-based compensation. Suspected exploitation of a specified adult can trigger escalation and permitted temporary holds under firm procedures. Records and signatures must never be fabricated for convenience.',['Guarantee|Promise to reimburse a customer’s investment loss; prohibited.','Sharing|Participation in profits/losses is tightly restricted.','Unregistered person|May perform clerical functions, not solicit or accept orders.','Signature of convenience|Signing for another person; falsification, even if requested.'],'Customer permission does not cure falsified records or a prohibited guarantee.','An elderly customer suddenly wires to a new “caregiver.” Escalate under supervisory procedures; do not ignore the change as the customer’s private matter.','Consent cannot legalize a prohibited act.','When records, customer assets or vulnerable adults are involved, choose supervision and documentation.',['Never use customer funds personally','Do not promise performance','Transaction-based pay usually signals registration','Respond truthfully to regulators'])
      ]},
      {id:'m13',domain:'d4',title:'Registration and professional conduct',description:'Who must register, what gets reported, and how ongoing obligations follow the individual.',lessons:[
        L('l27','Registration, CE and statutory disqualification',23,'Registration establishes permission for securities activities; continuing education maintains knowledge and conduct standards.','FINRA tests which activities require registration and what facts can bar or condition association.',['Distinguish registered and nonregistered activities','Compare Firm and Regulatory Elements of CE','Recognize statutory-disqualification categories conceptually'],'Associated persons performing securities functions generally must hold the appropriate registration. Clerical personnel may perform ministerial work but not solicit or accept orders. Firms investigate applicants, including background and fingerprint checks where required. Statutory disqualification can result from certain securities injunctions, bars, expulsions and specified convictions; it does not automatically describe every customer complaint. The Regulatory Element is FINRA-provided training; the Firm Element is the member’s needs-based annual program.',['Registration|Qualification plus association and required filings for a permitted role.','Firm Element|Firm-designed annual training based on its needs analysis.','Regulatory Element|FINRA-delivered continuing education.','Statutory disqualification|Specified legal/regulatory events that can restrict association.'],'Passing the SIE alone does not authorize securities business or create a registration. A representative-level exam and firm association are also needed.','A receptionist answers procedural questions but starts recommending securities and taking orders. Those activities cross into registration-required work.','SIE shows essentials; sponsorship completes the role.','Look at the activity performed, not the employee’s title.',['SIE credit is not a license by itself','Registrations match functions','Background facts must be accurate','CE is ongoing']),
        L('l28','Forms U4/U5, outside activity and reportable events',25,'The industry expects accurate, timely disclosure of employment, disciplinary and financial events plus advance handling of outside activities.','Conduct questions reward disclosure and supervision, not concealment or informal approval.',['Explain the purposes of Forms U4 and U5','Separate outside business activity from private securities transactions','Recognize gifts, political contribution and complaint issues'],'Form U4 begins and updates an individual’s registration record; required disclosures include specified criminal, regulatory, civil and financial events. Form U5 ends registrations and reports termination information. An outside business activity generally requires prior written notice. A private securities transaction involves securities activity outside the regular scope of employment and can require written notice and firm approval; if compensation is involved, the firm may need to supervise it as its own. Written customer complaints are preserved and reported as required. Gifts to employees of others are subject to applicable limits and records; business entertainment is analyzed differently and requires a legitimate business purpose.',['Form U4|Application and ongoing disclosure record.','Form U5|Termination notice and related disclosure.','OBA|Compensated business outside the member; prior written notice generally required.','PST|Outside securities transaction; approval and supervision can be required.'],'Calling compensation a “consulting fee” does not prevent an outside securities deal from being a private securities transaction.','A representative raises money for a friend’s startup and receives shares. This is an outside securities transaction, not merely a hobby.','U4 begins/updates; U5 ends. Securities outside = PST.','The safest exam answer is timely written disclosure to the firm before acting.',['Disclose changes accurately','Customer complaints create records','PST rules can apply with or without compensation','Political contributions can affect municipal business']),
        L('l29','The federal securities-law framework',22,'The major federal acts divide the regulatory landscape by task: offering disclosure, trading markets, pooled products and compensated advice.','The SIE expects high-level act-to-purpose matching, not law-school detail.',['Match the 1933 and 1934 Acts to primary and secondary-market regulation','Connect the 1940 Acts to investment companies and investment advisers','Explain where state blue-sky law and SIPA fit'],'The Securities Act of 1933 regulates new securities offerings and requires registration and prospectus disclosure unless an exemption applies. The Securities Exchange Act of 1934 created the SEC and regulates secondary trading, exchanges, broker-dealers and anti-fraud conduct. The Investment Company Act of 1940 regulates investment-company structure and operations. The Investment Advisers Act of 1940 regulates investment advisers at the federal level. State blue-sky laws can regulate securities, broker-dealers, advisers and representatives within a state. SIPA created SIPC and a process for customer-asset protection when a member broker-dealer fails.',['Securities Act of 1933|New issues, registration and offering disclosure.','Exchange Act of 1934|SEC, secondary markets, broker-dealers and anti-fraud rules.','Investment Company Act of 1940|Structure and operation of registered investment companies.','Investment Advisers Act of 1940|Federal framework for investment advisers.'],'Do not use “1933 = all regulation” or “1934 = all trading.” The exam rewards the primary purpose of each act, while recognizing overlap.','A question asks which act governs a corporate IPO registration statement: think 1933. A question asks about exchange trading or broker-dealer registration: think 1934.','33 before the sale; 34 after the door. The two 40 Acts regulate funds and advice.','Expect a fact pattern with one regulatory verb—offers, trades, pools or advises—and map that verb to the act.',['1933 centers on new offerings','1934 centers on markets and broker-dealers','Investment Company Act covers pooled-product structure','Advisers Act covers compensated securities advice'])
      ]}
    ];

    const flashcards = [
      ['d1','SEC','Federal securities regulator that administers federal securities laws and oversees SROs.'],['d1','FINRA','SRO regulating broker-dealers and associated persons; also administers the SIE.'],['d1','MSRB','Writes rules for municipal securities firms and municipal advisers; it does not enforce them.'],['d1','SIPC','Helps return customer cash and securities when a member broker-dealer fails; not protection from market loss.'],['d1','Primary market','New securities are sold and issuer receives proceeds.'],['d1','Fourth market','Direct institution-to-institution securities trading without a broker-dealer intermediary.'],['d1','Firm commitment','Underwriter buys the issue and assumes resale risk.'],['d1','Open-market purchase','Fed purchase that adds reserves and tends to ease credit.'],
      ['d2','Common stock','Residual ownership with voting rights, limited liability and variable dividends.'],['d2','Cumulative preferred','Missed preferred dividends accumulate before common dividends may resume.'],['d2','Right vs. warrant','Rights are short-lived and generally for current holders; warrants are longer-lived issuer sweeteners.'],['d2','Inverse bond rule','When market interest rates rise, existing fixed-rate bond prices generally fall.'],['d2','Current yield','Annual bond interest divided by current market price.'],['d2','GO bond','Municipal bond backed by the issuer’s taxing power.'],['d2','Revenue bond','Municipal bond backed by specified project or facility revenues.'],['d2','Prepayment risk','Principal returns earlier than expected, often when reinvestment rates are lower.'],['d2','Long call','Right to buy; bullish; maximum loss is the premium.'],['d2','Long put','Right to sell; bearish or protective; maximum loss is the premium.'],['d2','Covered call','Own stock and write a call; income with capped upside and continuing stock downside.'],['d2','Open-end fund pricing','Purchases and redemptions use the next calculated NAV (plus any applicable sales charge).'],['d2','ETN','Unsecured debt linked to a benchmark; exposes holder to issuer credit risk.'],['d2','ROA vs. LOI','ROA counts existing holdings; LOI counts intended future purchases toward breakpoints.'],['d2','Variable annuity','Tax-deferred insurance contract with separate-account investment performance and possible surrender charges.'],['d2','529 control','The account owner controls assets and distributions; the beneficiary receives qualified benefits.'],['d2','Systematic risk','Broad-market risk that diversification cannot eliminate.'],['d2','Nonsystematic risk','Issuer or industry risk that diversification can reduce.'],
      ['d3','Buy limit','Order to buy at the limit price or lower; price is controlled, execution is not guaranteed.'],['d3','Sell stop','Placed below current market; becomes a market order when triggered.'],['d3','Bid / ask','Dealer buys at bid and sells at ask; customers generally do the reverse.'],['d3','Regular-way settlement','Most U.S. equity and corporate bond trades settle T+1 under the current outline.'],['d3','UTMA account','Irrevocable gift owned by a minor and managed by a custodian.'],['d3','Structuring','Breaking transactions into smaller amounts to evade reporting requirements.'],['d3','SAR confidentiality','A customer must not be told that a Suspicious Activity Report was filed.'],['d3','Front running','Trading ahead of a known customer order to benefit from its expected market impact.'],['d3','MNPI','Information a reasonable investor would consider important that is not broadly public.'],
      ['d4','Form U4','Starts and updates an associated person’s registration and disclosure record.'],['d4','Form U5','Terminates registration and reports termination-related information.'],['d4','Firm Element','Firm-designed annual continuing education based on a needs analysis.'],['d4','Private securities transaction','A securities transaction outside the regular scope of employment; written notice and approval can be required.']
    ].map((x,i)=>({id:'f'+(i+1),domain:x[0],front:x[1],back:x[2]}));

    const allLessons = modules.flatMap(m=>m.lessons.map(l=>({...l,moduleId:m.id,moduleTitle:m.title,domain:m.domain})));

    const Q=(id,domain,topic,difficulty,stem,choices,correct,reasons,takeaway)=>({id,domain,topic,difficulty,stem,choices,correct,reasons,takeaway});
    const qD1 = [
      Q('q01','d1','Regulators','easy','Which organization has primary federal authority to administer U.S. securities laws?',
        ['FINRA','SEC','MSRB','SIPC'],1,
        ['FINRA is an SRO for broker-dealers, tempting because it enforces many industry rules, but it is overseen by the SEC.','Correct. The SEC is the federal securities regulator.','The MSRB writes municipal rules but is not the primary federal regulator.','SIPC protects custody assets in a member-firm failure; it is not a regulator.'],'SEC = federal regulator; FINRA = broker-dealer SRO.'),
      Q('q02','d1','Regulators','medium','Which statement about the MSRB is accurate?',
        ['It insures municipal bonds against default.','It writes rules for municipal securities firms and municipal advisers.','It directly prosecutes all municipal rule violations.','It approves every municipal official statement.'],1,
        ['No federal body automatically insures municipal debt.','Correct. Rulemaking is the MSRB’s central role.','Tempting because MSRB rules are enforced, but enforcement is handled by FINRA, the SEC and bank regulators.','Municipal offering documents are not approved security by security by the MSRB.'],'MSRB writes; other regulators enforce.'),
      Q('q03','d1','Protection','easy','A customer’s stock declines because the issuer reports weak earnings. Which protection normally reimburses this loss?',
        ['SIPC','FDIC','FINRA fidelity coverage','None of these'],3,
        ['SIPC is tempting because the stock is held at a broker, but it does not cover market loss.','FDIC applies to eligible bank deposits, not a stock decline.','FINRA does not provide investor market-loss insurance.','Correct. Investment loss from price movement is borne by the investor.'],'SIPC protects missing custody assets, not investment value.'),
      Q('q04','d1','Markets','easy','In which transaction does the issuer receive the sale proceeds?',
        ['An investor sells listed shares on an exchange.','A dealer sells inventory to a customer.','A corporation sells newly issued bonds through an underwriter.','Two institutions trade directly through an ECN.'],2,
        ['This is a secondary trade; the selling investor receives proceeds.','This is a dealer principal trade in the secondary market.','Correct. A new issue is a primary-market transaction.','Direct institutional trading describes the fourth market and usually involves outstanding securities.'],'Follow proceeds: issuer receipt means primary market.'),
      Q('q05','d1','Markets','medium','Two pension funds trade a large block directly with one another, without a broker-dealer intermediary. This occurs in the',
        ['primary market.','secondary exchange market.','third market.','fourth market.'],3,
        ['No new securities or issuer proceeds are described.','This is secondary trading broadly, but the direct institutional venue has a more specific name.','The third market is OTC trading of exchange-listed securities, usually through dealers.','Correct. Direct institution-to-institution trading is the fourth market.'],'Fourth market = institutions directly.'),
      Q('q06','d1','Offerings','easy','Under a firm-commitment underwriting, who bears the risk that the securities will not be sold to the public?',
        ['The issuer','The underwriter','The transfer agent','The SEC'],1,
        ['The issuer bears more distribution risk in a best-efforts deal, making this tempting but wrong.','Correct. The underwriter buys the issue and owns unsold inventory.','A transfer agent maintains ownership records; it does not distribute inventory.','The SEC administers disclosure law and does not bear market risk.'],'Firm commitment = underwriter owns the issue.'),
      Q('q07','d1','Offering documents','medium','Which document is most closely associated with a new municipal bond offering?',
        ['Official statement','Form U4','Options Disclosure Document','Corporate prospectus mandated for every municipal issue'],0,
        ['Correct. The official statement is the primary municipal offering disclosure.','Form U4 is an individual registration form.','The ODD addresses standardized options risks.','Municipal securities are generally exempt from Securities Act registration, so this absolute wording is wrong.'],'Municipal new issue → official statement.'),
      Q('q08','d1','Federal Reserve','medium','The Federal Reserve sells Treasury securities in the open market. The most likely initial effect is to',
        ['add bank reserves and ease credit.','drain bank reserves and tighten credit.','increase federal spending.','lower corporate tax rates.'],1,
        ['That describes a Fed purchase, the common directional trap.','Correct. Buyers pay the Fed, removing reserves from the banking system.','Spending is fiscal policy set through government budgeting.','Tax rates are fiscal policy, not an open-market operation.'],'Fed sale drains; Fed purchase adds.'),
      Q('q09','d1','Policy','easy','Which action is an example of fiscal policy?',
        ['The Fed lowers the discount rate.','The Fed purchases Treasury securities.','Congress increases infrastructure spending.','A bank lowers its prime rate.'],2,
        ['The discount rate is a monetary-policy tool.','Open-market operations are monetary policy.','Correct. Government spending and taxation are fiscal policy.','A commercial bank decision is neither a direct fiscal action nor a Fed tool.'],'Fiscal = taxes and government spending.'),
      Q('q10','d1','Economics','medium','A statistic that tends to change before the overall economy changes is classified as',
        ['a leading indicator.','a coincident indicator.','a lagging indicator.','a balance-of-payments item.'],0,
        ['Correct. “Leading” describes timing ahead of the cycle.','Coincident indicators move approximately with current activity.','Lagging indicators confirm a trend after it is established.','Balance of payments tracks international transactions, not indicator timing.'],'Leading indicators anticipate; lagging indicators confirm.'),
      Q('q11','d1','Economics','medium','Which statement best distinguishes GDP from GNP?',
        ['GDP measures only government production; GNP measures private production.','GDP focuses on production within domestic borders; GNP focuses on production by a nation’s residents or nationals.','GDP excludes services; GNP includes services.','They are identical measures.'],1,
        ['Both include public and private production.','Correct. Location drives GDP; national ownership/residency drives GNP.','Both measures include qualifying goods and services.','They are related but differ because of cross-border income and production.'],'GDP = geography; GNP = nationality.'),
      Q('q12','d1','Offerings','hard','A registration statement becomes effective. Which statement may a representative properly make?',
        ['The SEC has approved the investment’s merits.','The SEC guarantees that all disclosures are accurate.','The securities may be offered subject to applicable requirements; effectiveness is not an SEC endorsement.','The security is now exempt from state law.'],2,
        ['Registration is often mistaken for merit approval; the SEC does not endorse an investment.','The issuer and other parties remain responsible for disclosure accuracy.','Correct. Effectiveness permits the registered offering but is not approval.','Federal registration does not automatically erase applicable blue-sky obligations.'],'Registration allows an offering; it never means SEC approval.'),
    ];
    const qD2 = [
      Q('q13','d2','Equities','easy','Which right is most commonly associated with common stock?',
        ['A guaranteed dividend','Voting for directors','Priority over all creditors','A fixed maturity date'],1,
        ['Common dividends are declared, not guaranteed.','Correct. Common shareholders generally elect directors.','Creditors and preferred holders rank ahead of common in liquidation.','Common stock is perpetual equity with no maturity.'],'Common shareholders vote and hold the residual claim.'),
      Q('q14','d2','Equities','medium','Which preferred-stock feature requires missed dividends to be paid before common dividends resume?',
        ['Callable','Participating','Cumulative','Convertible'],2,
        ['Callable lets the issuer redeem; it does not accumulate dividends.','Participating may add dividend upside but is not the arrears feature.','Correct. Cumulative preferred carries unpaid dividends forward.','Convertible allows exchange into common stock.'],'Cumulative = dividend arrears accumulate.'),
      Q('q15','d2','Equities','easy','In a corporate liquidation, which security holder is generally paid last?',
        ['Secured bondholder','Debenture holder','Preferred shareholder','Common shareholder'],3,
        ['Secured creditors have a claim on identified collateral and rank ahead.','Unsecured creditors still rank before owners.','Preferred owners have priority over common owners.','Correct. Common equity is the residual claim.'],'Debt first; preferred next; common last.'),
      Q('q16','d2','Equities','medium','An issuer gives existing shareholders a two-week privilege to buy new shares below market. The instrument is a',
        ['warrant.','right.','call option issued by the OCC.','convertible bond.'],1,
        ['Warrants are typically longer-lived and may be offered as a sweetener.','Correct. Rights are short-term and commonly issued to current holders.','OCC options are standardized contracts, not issuer preemptive privileges.','A convertible bond is a debt security exchangeable for stock.'],'Rights are short-lived; warrants are longer-lived.'),
      Q('q17','d2','Equities','medium','A primary risk that remains when a U.S. investor owns an ADR is',
        ['no market risk because it trades in dollars.','currency and political risk tied to the foreign issuer.','no issuer risk because a depositary bank is involved.','guaranteed dividend conversion.'],1,
        ['Dollar trading is tempting, but underlying foreign exposure can still be affected by currency movement.','Correct. ADRs retain foreign company, country and currency risks.','The depositary structure does not eliminate the operating company’s risk.','Dividends may vary and conversion does not create a guarantee.'],'ADR convenience does not remove foreign-investment risks.'),
      Q('q18','d2','Equities','hard','Which statement about preferred stock is accurate?',
        ['It is a creditor claim with mandatory interest.','It generally has dividend and liquidation priority over common stock.','It always has stronger voting rights than common.','Its dividend is guaranteed by the SEC.'],1,
        ['Preferred is equity, despite bond-like characteristics.','Correct. Priority is its core comparative feature.','Preferred typically has limited or contingent voting rights.','No regulator guarantees corporate dividends.'],'Preferred remains equity but ranks ahead of common.'),
      Q('q19','d2','Debt','easy','If market interest rates rise, the price of an existing fixed-rate bond will generally',
        ['rise.','fall.','remain exactly at par.','become unrelated to yield.'],1,
        ['This reverses the core inverse relationship.','Correct. The older coupon is less competitive, so price tends to fall.','Par payment at maturity does not freeze today’s market price.','Price and yield remain inversely related.'],'Rates up, fixed-rate bond prices down.'),
      Q('q20','d2','Debt','medium','A 6% bond with $1,000 par trades at $1,200. Its current yield is',
        ['5%.','6%.','7.2%.','12%.'],0,
        ['$60 annual interest ÷ $1,200 market price = 5%.','6% is the coupon rate based on par, the tempting wrong denominator.','7.2% results from multiplying rather than dividing annual interest by price.','12% confuses the price quotation with a yield.'],'Current yield = annual interest ÷ market price.'),
      Q('q21','d2','Debt','easy','Which Treasury security is issued with an original maturity of one year or less?',
        ['Treasury bill','Treasury note','Treasury bond','Treasury receipt only'],0,
        ['Correct. T-bills are short-term and issued at a discount.','Notes have intermediate maturities.','Treasury bonds have long maturities.','Receipts are separately created interests and not the standard answer for original Treasury maturity.'],'Bill = short, note = intermediate, bond = long.'),
      Q('q22','d2','Municipals','easy','A municipal bond backed primarily by property and other taxes is a',
        ['revenue bond.','general obligation bond.','corporate debenture.','bankers’ acceptance.'],1,
        ['Revenue bonds rely on specified facility or project revenues.','Correct. GO bonds rely on taxing power and general credit.','A debenture is unsecured corporate debt.','A bankers’ acceptance is a trade-finance money-market instrument.'],'GO = taxes; revenue = project receipts.'),
      Q('q23','d2','Municipals','medium','Interest from a typical municipal bond is generally',
        ['exempt from federal income tax, while capital gains can still be taxable.','exempt from every tax in all circumstances.','subject to federal tax but exempt from all state tax.','insured by the MSRB.'],0,
        ['Correct. State treatment varies, and gains can be taxable.','“Tax free” is an exam trap because the exemption is not universal.','This reverses the general federal treatment and overstates state exemption.','The MSRB writes rules; it does not insure municipal bonds.'],'Municipal interest can be federally exempt; gains and state taxes require separate analysis.'),
      Q('q24','d2','Debt','medium','Falling mortgage rates create which distinctive risk for an MBS investor?',
        ['Prepayment risk','Political risk only','No reinvestment risk','Unlimited loss from writing calls'],0,
        ['Correct. Refinancing can return principal earlier, often when new rates are lower.','Political risk can exist broadly but is not the feature driven by falling mortgage rates.','Early principal creates, rather than removes, reinvestment risk.','The investor owns an MBS; no option-writing fact is present.'],'Falling rates can accelerate mortgage prepayments.'),
      Q('q25','d2','Debt','medium','A corporate bond backed only by the issuer’s general credit is a',
        ['debenture.','secured mortgage bond.','revenue bond.','Treasury note.'],0,
        ['Correct. A debenture is unsecured corporate debt.','A mortgage bond has identified real-property collateral.','Revenue bonds are municipal obligations backed by project receipts.','A Treasury note is a U.S. government security.'],'Debenture = unsecured corporate promise.'),
      Q('q26','d2','Debt','medium','When rates fall, which bond feature is most likely to disadvantage the investor?',
        ['A call provision','A put provision held by the investor','A higher credit rating','A restrictive covenant'],0,
        ['Correct. The issuer may refinance and return principal when reinvestment rates are lower.','An investor put can be protective, not an issuer advantage.','A stronger rating generally reduces credit risk.','Covenants generally protect creditor interests.'],'Calls benefit issuers when refinancing becomes attractive.'),
      Q('q27','d2','Debt','easy','Which instrument is unsecured short-term debt issued by a corporation?',
        ['Commercial paper','Treasury bill','Negotiable CD','Bankers’ acceptance'],0,
        ['Correct. Commercial paper finances corporate working-capital needs.','A T-bill is issued by the U.S. Treasury.','A CD is a bank obligation.','A bankers’ acceptance is a bank-guaranteed trade draft.'],'Commercial paper = corporate, short term, unsecured.'),
      Q('q28','d2','Options','easy','The buyer of a call has the',
        ['right to buy the underlying at the strike price.','obligation to buy the underlying.','right to sell the underlying.','obligation to sell the underlying.'],0,
        ['Correct. A long call is a right to buy.','The call writer accepts the obligation to sell if assigned.','A right to sell belongs to a put buyer.','An obligation to sell belongs to a call writer.'],'Call buyer has the right to buy.'),
      Q('q29','d2','Options','easy','The maximum loss for the buyer of an option is generally',
        ['the strike price.','the premium paid.','unlimited.','the market price of 100 shares.'],1,
        ['Strike determines contract terms but is not the long option’s maximum loss.','Correct. A buyer can allow an option to expire and lose the premium.','Unlimited loss is associated with an uncovered short call, not an option buyer.','The option buyer does not necessarily buy the shares.'],'Option buyers risk the premium.'),
      Q('q30','d2','Options','medium','A 50 call is in the money when the underlying stock is',
        ['$44.','$49.','$50.','$56.'],3,
        ['Below strike means a call is out of the money.','Still below the call strike.','At the money, not in the money.','Correct. A call has intrinsic value when market price exceeds strike.'],'Call ITM above strike; put ITM below.'),
      Q('q31','d2','Options','medium','Which position can have theoretically unlimited loss?',
        ['Long call','Long put','Uncovered short call','Covered short call'],2,
        ['A long call loses at most its premium.','A long put loses at most its premium.','Correct. A stock price can rise without a fixed ceiling, increasing the writer’s obligation.','Owning the shares covers delivery, though the stock itself still has downside.'],'Uncovered call writing carries extreme upside-price risk.'),
      Q('q32','d2','Options','medium','An investor owns 100 shares and wants downside protection while retaining upside. The most direct strategy is to',
        ['buy a put.','sell an uncovered call.','buy another 100 shares on margin.','sell a put.'],0,
        ['Correct. A protective put creates a sale-price floor.','An uncovered call adds major risk and does not protect the existing shares below strike.','More leveraged stock increases downside exposure.','A short put adds an obligation to buy more shares.'],'Protective put = owned stock plus long put.'),
      Q('q33','d2','Options','medium','Broad-based index options generally settle through',
        ['delivery of every component stock.','cash.','delivery of a corporate bond.','SIPC reimbursement.'],1,
        ['Delivering all index components would be impractical and is not the standard settlement.','Correct. Index options are typically cash settled.','A stock-index contract does not settle in corporate debt.','SIPC has no role in normal options settlement.'],'Index options generally cash settle.'),
      Q('q34','d2','Options','hard','Which statement about a covered-call writer is accurate?',
        ['The position has no downside risk.','The writer receives premium but gives up stock gains above the strike.','The writer has unlimited loss from a rising stock.','The writer has the right to buy the shares.'],1,
        ['Owned stock can still decline, so coverage does not eliminate downside.','Correct. The premium adds income while the short call caps upside.','Stock ownership covers delivery, eliminating the uncovered call’s unlimited rising-price loss.','A call buyer has the right; the writer has an obligation.'],'Covered means delivery is covered, not every loss.'),
      Q('q35','d2','Funds','easy','Open-end mutual fund shares are purchased at',
        ['the last exchange trade.','the next computed NAV plus any applicable sales charge.','a negotiated bond price.','the previous day’s NAV in every case.'],1,
        ['Open-end shares do not trade on an exchange.','Correct. This is forward pricing.','Mutual-fund shares are not negotiated like individual bonds.','The next calculation, not necessarily the prior NAV, applies.'],'Open-end funds use forward pricing.'),
      Q('q36','d2','Funds','medium','Which product can commonly trade at a market-price discount to NAV?',
        ['An open-end mutual fund redeemed with the fund','A closed-end fund','A fixed annuity accumulation unit','A new-issue Treasury bill at maturity'],1,
        ['Open-end redemptions occur at NAV, so persistent exchange discounts are not its mechanism.','Correct. Supply and demand can put closed-end market price above or below NAV.','Fixed annuities do not use variable accumulation units.','At maturity a Treasury pays its stated amount; NAV is not the relevant measure.'],'Closed-end price can differ from NAV.'),
      Q('q37','d2','Funds','medium','The main additional risk of an ETN compared with an ETF holding a portfolio is',
        ['issuer credit risk.','voting dilution.','preemptive-right risk.','municipal tax risk.'],0,
        ['Correct. An ETN is unsecured debt of its issuer.','ETNs do not create voting dilution in an operating company.','Preemptive rights concern common shareholders.','An ETN is not defined by municipal tax treatment.'],'ETN = note = issuer credit risk.'),
      Q('q38','d2','Funds','medium','Which feature counts a customer’s eligible existing mutual-fund holdings toward a breakpoint?',
        ['Letter of intent','Right of accumulation','Surrender charge','12b-1 fee'],1,
        ['An LOI uses intended future purchases, making it the tempting counterpart.','Correct. ROA looks at qualifying current holdings.','A surrender charge is a withdrawal fee.','A 12b-1 fee is an ongoing distribution expense.'],'ROA remembers existing holdings; LOI looks ahead.'),
      Q('q39','d2','Funds','hard','A representative recommends three separate $20,000 Class A fund purchases to avoid a $50,000 sales-charge breakpoint. This is',
        ['acceptable dollar-cost averaging.','a breakpoint sale and prohibited practice.','required to diversify timing.','acceptable if the fund performs well.'],1,
        ['Timing purchases can be legitimate, but structuring them to avoid a discount is not.','Correct. The customer is deprived of an available quantity discount.','Diversification does not require forfeiting a breakpoint.','Later performance does not cure an improper sales-charge recommendation.'],'Never split purchases to deny a breakpoint.'),
      Q('q40','d2','Funds','medium','A UIT is best described as',
        ['a generally fixed portfolio with a stated termination.','an actively traded hedge fund with unlimited life.','an insurer’s general account.','a bank deposit with FDIC coverage.'],0,
        ['Correct. UITs are supervised rather than actively managed and generally terminate.','That describes neither the legal structure nor access of a UIT.','A general account supports fixed insurance obligations.','A UIT is a security, not an insured bank deposit.'],'UIT = fixed portfolio plus termination date.'),
      Q('q41','d2','Annuities','medium','Which statement about a nonqualified variable annuity is accurate?',
        ['Contributions are federally tax deductible.','Separate-account performance can fluctuate, and earnings are tax deferred.','All withdrawals are tax free.','SIPC guarantees the contract value.'],1,
        ['Nonqualified contributions are generally after tax.','Correct. Investment results vary and tax is deferred until distribution.','Earnings are generally taxable as ordinary income when withdrawn.','Variable values are not guaranteed by SIPC.'],'Variable annuity: after-tax contribution, tax-deferred earnings, market exposure.'),
      Q('q42','d2','Municipal funds','medium','Who generally controls investment selections and distributions in a 529 savings plan?',
        ['The beneficiary','The account owner','The beneficiary’s school','FINRA'],1,
        ['The beneficiary benefits but generally does not control the account.','Correct. The owner retains account control subject to plan rules.','A school may receive payment but does not control the plan account.','FINRA regulates firms; it does not direct family distributions.'],'529 owner controls; beneficiary benefits.'),
      Q('q43','d2','Alternatives','medium','Which feature is most characteristic of a DPP limited partnership?',
        ['Guaranteed liquidity','Pass-through tax treatment and limited secondary trading','FDIC insurance','Daily redemption at NAV'],1,
        ['DPP interests are generally illiquid.','Correct. Pass-through economics and limited liquidity are defining traits.','Partnership interests are not bank deposits.','Daily NAV redemption describes open-end mutual funds.'],'DPPs pass through and are generally illiquid.'),
      Q('q44','d2','Risk','easy','Diversification is most effective at reducing',
        ['systematic market risk.','nonsystematic issuer risk.','inflation for the entire economy.','all possible portfolio losses.'],1,
        ['Broad market risk remains even in a diversified portfolio.','Correct. Spreading issuer and industry exposure reduces specific risk.','A portfolio cannot change economy-wide inflation.','Diversification mitigates risk; it does not guarantee against loss.'],'Diversification reduces specific—not broad-market—risk.'),
      Q('q45','d2','Risk','hard','An investor in a long-duration, low-coupon bond is especially exposed to',
        ['interest-rate risk.','voting risk.','preemptive-right dilution only.','no market risk if held at a broker.'],0,
        ['Correct. Long duration and low coupons make price more sensitive to rate changes.','Bondholders generally do not vote for directors.','Preemptive rights are an equity concept.','Broker custody does not eliminate price risk.'],'Longer maturity and lower coupon generally mean greater rate sensitivity.'),
    ];

    const qD3 = [
      Q('q46','d3','Orders','easy','Which order prioritizes execution over price?',
        ['Market order','Limit order','Stop-limit order','Good-til-canceled limit order'],0,
        ['Correct. A market order seeks prompt execution but price can change.','A limit controls price and may not execute.','A stop-limit adds price conditions and does not guarantee execution.','GTC controls duration, not an execution guarantee.'],'Market order: execution priority, no price guarantee.'),
      Q('q47','d3','Orders','medium','A customer wants to buy a stock only at $42 or lower. The proper order is a',
        ['buy stop at 42.','buy limit at 42.','sell limit at 42.','market order.'],1,
        ['A buy stop is placed above the market and becomes a market order when triggered.','Correct. A buy limit sets the maximum acceptable purchase price.','A sell limit applies to a seller, not a buyer.','A market order could execute above $42.'],'Buy limit = at limit or lower.'),
      Q('q48','d3','Orders','medium','A sell stop is triggered. It then becomes a',
        ['limit order.','market order.','canceled order.','short call.'],1,
        ['A stop-limit would become a limit order, but a plain stop does not.','Correct. Execution then occurs at the next available price.','Triggering activates rather than cancels the order.','An order does not transform into an options position.'],'A stop becomes a market order once triggered.'),
      Q('q49','d3','Quotes','easy','A stock is quoted 24.10 bid—24.18 ask. At which price does a customer generally buy?',
        ['24.10','24.14','24.18','Any price the customer chooses'],2,
        ['The dealer buys from a customer at the bid.','The midpoint is not automatically available.','Correct. A customer buys from the dealer at the ask.','A limit may set a condition, but the displayed asking price is 24.18.'],'Customers buy at ask and sell at bid.'),
      Q('q50','d3','Capacity','medium','A broker-dealer sells a security from its own inventory to a customer. It acts as',
        ['agent and charges only a commission.','principal and may earn a markup.','transfer agent.','investment adviser only.'],1,
        ['Agency means acting on behalf of another party, not using firm inventory.','Correct. Dealer inventory means principal capacity.','A transfer agent maintains issuer ownership records.','Advice is not the capacity described by an inventory sale.'],'Inventory = principal; customer order representation = agency.'),
      Q('q51','d3','Orders','hard','A stock is at $30. Which order could help protect a long position if the price declines but does not guarantee the execution price?',
        ['Sell stop at $27','Buy stop at $33','Sell limit at $35','Buy limit at $27'],0,
        ['Correct. A sell stop below market activates during a decline, then becomes a market order.','A buy stop is typically used to enter or protect a short position as price rises.','A sell limit above market seeks a higher sale, not downside activation.','A buy limit would add stock rather than sell the existing long position.'],'Sell stops can trigger downside exits but can gap below the stop price.'),
      Q('q52','d3','Settlement','easy','Under the current regular-way standard in the FINRA SIE outline, most U.S. stock trades settle',
        ['on trade date.','one business day after trade date.','two business days after trade date.','five calendar days after trade date.'],1,
        ['Same-day settlement is cash settlement, not regular way.','Correct. The standard is T+1.','T+2 is obsolete for these transactions and remains a common outdated-study trap.','Settlement is expressed in business days, and this period is too long.'],'Current regular-way settlement is T+1.'),
      Q('q53','d3','Dividends','medium','To receive a declared regular cash dividend, an investor generally must purchase the stock',
        ['on or after the ex-dividend date.','before the ex-dividend date.','after the payable date.','only on the record date after the close.'],1,
        ['A buyer on or after ex-date does not receive that dividend.','Correct. Buy before the stock goes ex-dividend.','The payable date comes after entitlement is determined.','Waiting until the record date is generally too late under regular-way settlement.'],'Buy before ex-date to receive the dividend.'),
      Q('q54','d3','Corporate actions','easy','An investor owns 100 shares at $60 immediately before a 3-for-2 stock split. Immediately after, the position is approximately',
        ['150 shares at $40.','150 shares at $60.','66 shares at $90.','100 shares at $40.'],0,
        ['Correct. Shares multiply by 1.5 and price divides by 1.5; total value initially remains $6,000.','This would manufacture $3,000 of value from the split.','This resembles an inverse adjustment and uses the wrong share count.','Both the share count and price must adjust.'],'Split: shares multiply, price divides, value initially unchanged.'),
      Q('q55','d3','Returns','medium','Which item is included in an investment’s total return?',
        ['Only realized capital gains','Income plus realized and unrealized price change over the measurement period','Only dividends','Only return of capital'],1,
        ['Ignoring income and unrealized change understates total return.','Correct. Total return combines income and change in value.','Dividends are one component, not the whole measure.','Return of capital has separate basis implications and is not by itself total return.'],'Total return combines income and price change.'),
      Q('q56','d3','Accounts','easy','Assets in a UTMA account legally belong to the',
        ['custodian.','minor.','broker-dealer.','donor until the minor turns 18.'],1,
        ['The custodian manages the property but does not own it.','Correct. The transfer is an irrevocable gift to the minor.','The broker-dealer carries the account but is not beneficial owner.','The donor gives up ownership when the gift is completed.'],'UTMA: minor owns; custodian controls.'),
      Q('q57','d3','Accounts','medium','A representative chooses the security and amount to buy for a customer. This generally requires',
        ['only verbal time-and-price discretion.','written discretionary authority and firm acceptance.','no customer authorization if the trade is profitable.','approval from SIPC.'],1,
        ['Time-and-price discretion is narrower and does not include choosing security and amount.','Correct. These choices are substantive discretion.','Profit does not cure unauthorized trading.','SIPC has no role in account trading authorization.'],'Security or amount discretion requires proper written authority.'),
      Q('q58','d3','Margin','medium','Which statement about a margin account is accurate?',
        ['Losses are limited to the initial deposit in every case.','The firm extends credit and may liquidate positions under the margin agreement.','It is insured against market declines.','It cannot hold equity securities.'],1,
        ['Leverage can produce losses exceeding the initial equity.','Correct. Margin is a lending arrangement with liquidation rights.','No market-loss insurance applies.','Equities are commonly held in margin accounts if eligible.'],'Margin magnifies outcomes and permits forced liquidation.'),
      Q('q59','d3','Accounts','medium','Authority for a trustee to trade a trust account is primarily established by the',
        ['trust document.','beneficiary’s casual instruction.','representative’s discretion.','issuer’s prospectus.'],0,
        ['Correct. The governing document defines trustee powers.','A beneficiary may not have authority to direct the trustee.','The representative cannot create legal authority.','An issuer document describes a security, not trust powers.'],'Account authority comes from the governing registration document.'),
      Q('q60','d3','Retirement','medium','Which statement is most accurate about retirement accounts?',
        ['Every withdrawal is tax free.','Account rules can restrict contributions and distributions, and tax treatment depends on account type.','They may never hold securities.','SIPC guarantees retirement returns.'],1,
        ['Traditional account distributions are often taxable; Roth treatment has conditions.','Correct. The registration and tax status determine the rules.','Retirement accounts commonly invest in securities.','SIPC does not guarantee investment return.'],'Identify the retirement account type before applying tax rules.'),
      Q('q61','d3','AML','easy','Breaking a large cash transaction into smaller transactions to evade reporting is called',
        ['layering only.','structuring.','annuitization.','interpositioning.'],1,
        ['Layering obscures the money trail broadly, but the threshold-evasion pattern has a specific name.','Correct. Structuring is itself suspicious and can be illegal.','Annuitization converts an annuity value into income payments.','Interpositioning inserts an unnecessary party into trade execution.'],'Structuring = breaking up transactions to evade reporting.'),
      Q('q62','d3','AML','medium','After a firm files a Suspicious Activity Report about a customer, the representative should',
        ['tell the customer so the customer can respond.','keep the filing confidential and follow firm procedures.','close every related account immediately without review.','post the filing in the account’s public notes.'],1,
        ['Telling the customer can constitute prohibited tipping off.','Correct. SAR confidentiality is essential.','A SAR does not automatically dictate immediate closure; follow legal and firm procedures.','The report must not be exposed to the customer or public.'],'SAR filed? Do not tip off the customer.'),
      Q('q63','d3','AML','medium','Which sequence reflects the classic stages of money laundering?',
        ['Integration, placement, layering','Placement, layering, integration','Layering, integration, placement','Placement, integration, underwriting'],1,
        ['This reverses entry and legitimization.','Correct. Funds enter, the trail is obscured, then wealth appears legitimate.','Placement must occur before the illicit funds can be layered in the system.','Underwriting is not a money-laundering stage.'],'Place → layer → integrate.'),
      Q('q64','d3','Privacy','medium','Regulation S-P primarily addresses',
        ['customer nonpublic personal information and safeguards.','municipal underwriting spreads.','options strike-price adjustments.','Treasury auctions.'],0,
        ['Correct. It governs privacy notices, disclosure and safeguarding of customer information.','Municipal pricing is addressed by other rules.','Options adjustments are an OCC/market-structure matter.','Treasury auctions are unrelated to consumer financial privacy.'],'Reg S-P = privacy and safeguards.'),
      Q('q65','d3','Communications','easy','Which statement in a retail communication is most clearly improper?',
        ['“Past performance does not guarantee future results.”','“This registered investment is SEC approved and cannot lose money.”','“Fees reduce investment returns.”','“Read the prospectus before investing.”'],1,
        ['This is a proper caution.','Correct. Registration is not approval, and loss cannot be ruled out.','This is accurate and balanced.','Directing review of disclosure is appropriate.'],'No SEC approval claim; no guarantee against loss.'),
      Q('q66','d3','Prohibited activities','medium','A representative buys stock before entering a customer’s known large buy order, expecting the order to raise the price. This is',
        ['front running.','a firm commitment.','a right of accumulation.','permitted hedging in every case.'],0,
        ['Correct. The representative improperly trades ahead of customer order flow.','Firm commitment describes underwriting risk.','ROA is a mutual-fund breakpoint feature.','Labeling conduct hedging does not automatically make trading ahead permissible.'],'Front running abuses knowledge of customer order flow.'),
      Q('q67','d3','Insider trading','hard','An employee tips a friend about a confidential acquisition, and the friend trades knowing the source. Which is most accurate?',
        ['Only the employee can face liability.','Only the friend can face liability.','Both tipper and informed tippee can face liability.','Neither can face liability until the acquisition closes.'],2,
        ['The tippee’s informed trading can also create exposure.','The tipper’s improper disclosure can create exposure even without personally trading.','Correct. Liability can extend to both parties.','The information can be material before closing or even announcement.'],'Insider-trading exposure extends beyond traditional insiders.'),
      Q('q68','d3','Customer protection','hard','A customer asks a representative to sign the customer’s name on a form “for convenience.” The representative should',
        ['sign because the customer gave permission.','decline and follow proper documentation procedures.','sign only if no trade is involved.','ask an unregistered assistant to sign instead.'],1,
        ['Permission does not make a false signature acceptable.','Correct. Records must be authentic and procedures followed.','Falsification remains improper even without an immediate trade.','Delegating the falsification makes it no more permissible.'],'Customer consent cannot cure record falsification.'),
    ];
    const qD4 = [
      Q('q69','d4','Registration','easy','Passing the SIE by itself allows an individual to',
        ['conduct any securities business immediately.','demonstrate basic industry knowledge, but not act in a registered capacity without the required qualification and firm association.','open a broker-dealer without registration.','avoid all representative-level exams.'],1,
        ['The SIE alone is not a license or registration.','Correct. Further qualification and association are required for a registered role.','A broker-dealer and its personnel face separate registration requirements.','The SIE is generally a corequisite, not a replacement for specialized exams.'],'SIE credit alone does not authorize securities business.'),
      Q('q70','d4','Forms','easy','Which form is used to begin and update an associated person’s registration record?',
        ['Form U4','Form U5','Form 10-K','Form CRS only'],0,
        ['Correct. U4 contains registration and disclosure information.','U5 reports termination from registration.','A 10-K is an issuer annual report.','Form CRS is a relationship summary, not the individual registration application.'],'U4 begins/updates; U5 ends.'),
      Q('q71','d4','Forms','medium','A registered representative leaves a member firm. Which form does the firm generally file?',
        ['Form U4','Form U5','CTR','Official statement'],1,
        ['U4 starts or updates registration; it is the tempting pair.','Correct. Form U5 reports termination and related information.','A CTR concerns specified cash transactions.','An official statement is municipal offering disclosure.'],'U5 = uniform termination notice.'),
      Q('q72','d4','Continuing education','medium','Which description correctly distinguishes the two principal continuing-education components?',
        ['The Firm Element is FINRA’s online module; the Regulatory Element is optional firm training.','The Regulatory Element is FINRA-provided; the Firm Element is the member’s needs-based program.','Both apply only after a disciplinary event.','Passing the SIE permanently waives both.'],1,
        ['The two elements are reversed.','Correct. FINRA delivers Regulatory Element content; firms design the Firm Element.','Continuing education is ongoing, not solely remedial.','SIE credit does not waive ongoing obligations.'],'Regulatory Element from FINRA; Firm Element from the firm.'),
      Q('q73','d4','Outside activities','medium','A representative wants to operate a paid weekend tax-preparation business. The representative should generally',
        ['provide prior written notice to the member firm as an outside business activity.','keep it secret because it is not securities work.','file a SAR.','obtain SEC approval directly.'],0,
        ['Correct. Compensated outside work generally requires written notice under firm procedures.','Nonsecurities work can still be an outside business activity.','A SAR concerns suspected financial crime, not ordinary outside employment.','The firm—not the SEC directly—handles the associated-person notice and supervision process.'],'Outside compensated work generally means written notice first.'),
      Q('q74','d4','Private securities transactions','hard','A representative privately raises money for a startup and receives shares as compensation. This most likely is',
        ['a private securities transaction requiring written notice and firm approval before participation.','only an outside hobby with no disclosure implications.','permitted automatically because the securities are private.','a municipal fund security.'],0,
        ['Correct. Compensation and an outside securities sale trigger heightened approval and supervision.','The securities activity prevents treating it as a mere hobby.','Private status does not exempt the representative from member-firm rules.','Startup shares are not 529, ABLE or LGIP interests.'],'Outside securities activity = PST; disclose before acting.'),
      Q('q75','d4','Federal securities acts','medium','Which federal law is most directly associated with registration and disclosure for new securities offerings?',
        ['Securities Act of 1933','Securities Exchange Act of 1934','Investment Company Act of 1940','Securities Investor Protection Act of 1970'],0,
        ['Correct. The 1933 Act centers on new-issue registration and offering disclosure.','The 1934 Act is tempting because it created the SEC, but its center of gravity is secondary markets, exchanges and broker-dealers.','The Investment Company Act governs pooled-product structure and operations, not corporate offerings generally.','SIPA created the broker-dealer customer-protection framework and SIPC.'],'1933 before the sale; 1934 regulates the trading marketplace.'),
    ];
    const questions = [...qD1,...qD2,...qD3,...qD4];

    const STORAGE_KEY='sie-compass-state-v1';
    const defaultState={theme:'light',completedLessons:[],quizHistory:[],missedIds:[],cardRatings:{},plan:'standard',completedTasks:[],lastLesson:'l1',timeSeconds:0,lastExam:null,diagnosticScore:null};
    function loadState(){
      try{return {...defaultState,...JSON.parse(localStorage.getItem(STORAGE_KEY)||'{}')};}
      catch(e){return {...defaultState};}
    }
    let state=loadState();
    let view='home', selectedLesson=state.lastLesson, activeQuiz=null, activeExam=null, timerHandle=null;
    let cardFilter='all', cardDeck=[...flashcards], cardIndex=0, cardFlipped=false;
    let sessionMark=Date.now();
    const $=s=>document.querySelector(s), $$=s=>[...document.querySelectorAll(s)];
    const esc=s=>String(s??'').replace(/[&<>'"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;',"'":'&#39;','"':'&quot;'}[c]));
    const shuffle=a=>{const b=[...a];for(let i=b.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[b[i],b[j]]=[b[j],b[i]];}return b;};
    const clamp=(n,min,max)=>Math.min(max,Math.max(min,n));
    const percent=(n,d)=>d?Math.round(n/d*100):0;
    const letters=['A','B','C','D'];
    function creditTime(){const now=Date.now();state.timeSeconds+=Math.max(0,Math.round((now-sessionMark)/1000));sessionMark=now;}
    function save(){localStorage.setItem(STORAGE_KEY,JSON.stringify(state));updateChrome();}
    function toast(message){const t=$('#toast');t.textContent=message;t.classList.add('show');clearTimeout(t._timer);t._timer=setTimeout(()=>t.classList.remove('show'),2400);}
    function formatTime(seconds){const h=Math.floor(seconds/3600),m=Math.floor((seconds%3600)/60);return h?`${h}h ${m}m`:`${Math.max(1,m)}m`;}
    function formatClock(seconds){const m=Math.floor(Math.max(0,seconds)/60),s=Math.max(0,seconds)%60;return `${String(m).padStart(2,'0')}:${String(s).padStart(2,'0')}`;}
    function domainResults(domain){
      const results=state.quizHistory.flatMap(h=>h.results||[]).filter(r=>r.domain===domain);
      return {correct:results.filter(r=>r.correct).length,total:results.length,accuracy:percent(results.filter(r=>r.correct).length,results.length)};
    }
    function completion(){return percent(state.completedLessons.length,allLessons.length);}
    function readiness(){
      const all=state.quizHistory.flatMap(h=>h.results||[]),accuracy=percent(all.filter(r=>r.correct).length,all.length);
      const evidence=state.lastExam?.percent ?? state.diagnosticScore ?? accuracy;
      const score=Math.round(completion()*.35+accuracy*.45+evidence*.20);
      return clamp(score,0,99);
    }
    function readinessLabel(score=readiness()){return score>=78?'Mock-ready trend':score>=62?'Closing gaps':score>=40?'Building command':'Foundation stage';}
    function weakDomain(){
      const attempted=Object.keys(DOMAINS).map(id=>({id,...domainResults(id)})).filter(x=>x.total);
      return attempted.length?attempted.sort((a,b)=>a.accuracy-b.accuracy)[0].id:'d2';
    }
    function nextLesson(){return allLessons.find(l=>!state.completedLessons.includes(l.id))||allLessons[0];}
    function masteryForDomain(domain){const ls=allLessons.filter(l=>l.domain===domain);return percent(ls.filter(l=>state.completedLessons.includes(l.id)).length,ls.length);}
    function topRecommendation(){
      const w=weakDomain(),d=DOMAINS[w],next=allLessons.find(l=>l.domain===w&&!state.completedLessons.includes(l.id))||nextLesson();
      return {domain:w,title:next.title,lesson:next,reason:domainResults(w).total?`${d.short} is your lowest measured accuracy area.`:`${d.short} carries ${d.weight}% of scored questions and needs baseline evidence.`};
    }
    function sourceNote(){return `<p class="source-note">Coverage blueprint verified against the <a href="https://www.finra.org/sites/default/files/2025-10/SIE_Content_Outline.pdf" target="_blank" rel="noreferrer">2025 FINRA SIE Content Outline</a> and <a href="https://www.finra.org/industry/sie-practice-test" target="_blank" rel="noreferrer">FINRA practice-test guidance</a>. SIE Compass is an independent study tool, not affiliated with or endorsed by FINRA. Readiness is directional and never a guarantee of exam performance.</p>`;}
    function updateChrome(){
      const p=completion();$('#sideProgress').style.width=p+'%';$('#sideCompleted').textContent=`${state.completedLessons.length} of ${allLessons.length} lessons`;$('#sidePercent').textContent=p+'%';
      $$('#nav button').forEach(b=>b.classList.toggle('active',b.dataset.view===view));
      document.documentElement.dataset.theme=state.theme;$('#themeToggle').textContent=state.theme==='dark'?'☀':'◐';
    }
    function clearTimer(){if(timerHandle){clearInterval(timerHandle);timerHandle=null;}}
    function setCountdown(type){
      clearTimer(); timerHandle=setInterval(()=>{
        const session=type==='exam'?activeExam:activeQuiz;if(!session)return clearTimer();
        session.remaining--;const el=$('#timer');if(el){el.textContent=formatClock(session.remaining);el.classList.toggle('warning',session.remaining<=60);}
        if(session.remaining<=0){clearTimer();type==='exam'?finishExam(true):finishQuiz(true);}
      },1000);
    }
    function go(next,arg){
      creditTime(); clearTimer(); view=next;if(next==='lesson'&&arg){selectedLesson=arg;state.lastLesson=arg;save();}
      if(next!=='quiz')activeQuiz=null;if(next!=='exam')activeExam=null;
      history.replaceState(null,'','#'+next+(arg?'/'+arg:''));render();window.scrollTo(0,0);$('#main').focus({preventScroll:true});
    }
    function render(){
      updateChrome();const renderers={home:renderHome,dashboard:renderDashboard,course:renderCourse,lesson:renderLesson,quiz:renderQuiz,flashcards:renderFlashcards,review:renderReview,exam:renderExam,planner:renderPlanner,analytics:renderAnalytics};
      (renderers[view]||renderHome)();$('#main').classList.remove('view-enter');void $('#main').offsetWidth;$('#main').classList.add('view-enter');
    }
    function weightCards(showProgress=false){return Object.entries(DOMAINS).map(([id,d])=>`
      <article class="card weight-card" style="--accent:${d.color}">
        <div class="weight-head"><div><span class="tag">Domain ${id.slice(1)}</span><h3>${esc(d.short)}</h3></div><span class="weight">${d.weight}%</span></div>
        <p class="question-count">${d.count} of 75 scored questions${showProgress?` · ${masteryForDomain(id)}% lessons complete`:''}</p>
        <div class="bar"><span style="width:${showProgress?masteryForDomain(id):d.weight}%"></span></div>
      </article>`).join('');}
    function renderHome(){
      const r=readiness(),next=nextLesson();$('#topEyebrow').textContent='SIE study system';$('#topTitle').textContent='Build exam confidence, one decision at a time.';
      $('#main').innerHTML=`
        <section class="hero">
          <div><div class="eyebrow">FINRA SIE · focused preparation</div><h1>Know the rule. See the trap. Make the call.</h1><p>A complete, offline study system that turns the official exam blueprint into concise lessons, weighted practice, adaptive review and one realistic 75-question mock.</p>
            <div class="hero-actions"><button class="primary-btn" data-action="open-lesson" data-id="${next.id}">${state.completedLessons.length?'Resume studying':'Start the course'} →</button><button class="soft-btn" data-view="planner">Choose a study plan</button></div>
            <div class="hero-note"><span>75 scored questions</span><span>105 minutes</span><span>70 scaled passing score</span><span>5 additional unscored items on the official exam</span></div>
          </div>
          <aside class="readiness-card"><div class="label">Directional readiness</div><div class="score-ring" style="--score:${r}"><span>${r}<small>of 100</small></span></div><div class="mini-metrics"><div><strong>${completion()}%</strong><span>Course</span></div><div><strong>${state.missedIds.length}</strong><span>Review queue</span></div><div><strong>${state.quizHistory.length}</strong><span>Sessions</span></div></div></aside>
        </section>
        <section class="section"><div class="section-title"><div><div class="eyebrow">Official blueprint</div><h2>Study in the proportions the exam uses</h2><p>Products and risks receives the most teaching and practice because it represents 44% of scored questions.</p></div></div><div class="grid grid-4">${weightCards(false)}</div></section>
        <section class="section grid grid-3">
          <article class="card"><span class="tag green">2-week cram</span><h3>High-yield sprint</h3><p>Two lessons daily, daily retrieval and domain checkpoints. Best with a solid finance foundation.</p><button class="soft-btn" style="margin-top:16px" data-action="set-plan" data-plan="cram">Use cram plan</button></article>
          <article class="card"><span class="tag gold">4-week standard</span><h3>Balanced pass plan</h3><p>One lesson daily with interleaved review, checkpoints and a final mock week.</p><button class="primary-btn" style="margin-top:16px" data-action="set-plan" data-plan="standard">Use standard plan</button></article>
          <article class="card"><span class="tag">7-week mastery</span><h3>Deep retention</h3><p>Slower layering, spaced review and two remediation cycles before the full mock.</p><button class="soft-btn" style="margin-top:16px" data-action="set-plan" data-plan="mastery">Use mastery plan</button></article>
        </section>
        ${sourceNote()}`;
    }
    function renderDashboard(){
      const r=readiness(),all=state.quizHistory.flatMap(h=>h.results||[]),acc=percent(all.filter(x=>x.correct).length,all.length),rec=topRecommendation(),next=nextLesson();
      $('#topEyebrow').textContent='Performance center';$('#topTitle').textContent='Your next best move, backed by evidence.';
      $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Dashboard</div><h1>${readinessLabel(r)}</h1><p>Your readiness score blends lesson completion, practice accuracy and diagnostic/mock evidence. It is directional—not a prediction.</p></div><button class="primary-btn" data-action="open-lesson" data-id="${next.id}">Continue: ${esc(next.title)}</button></div>
        <div class="grid grid-4">
          <article class="card metric-card"><span class="metric-label">Readiness</span><strong class="metric-value">${r}/100</strong><span class="metric-sub">${readinessLabel(r)}</span></article>
          <article class="card metric-card"><span class="metric-label">Course complete</span><strong class="metric-value">${completion()}%</strong><span class="metric-sub">${state.completedLessons.length} of ${allLessons.length} lessons</span></article>
          <article class="card metric-card"><span class="metric-label">Practice accuracy</span><strong class="metric-value">${all.length?acc+'%':'—'}</strong><span class="metric-sub">${all.length} answered questions</span></article>
          <article class="card metric-card"><span class="metric-label">Focused time</span><strong class="metric-value">${formatTime(state.timeSeconds)}</strong><span class="metric-sub">Stored on this device</span></article>
        </div>
        <section class="section grid grid-3">
          <article class="card recommendation" style="grid-column:span 2"><span class="tag green">Most likely to improve your score next</span><h2 style="margin-top:12px">${esc(rec.title)}</h2><p>${esc(rec.reason)}</p><div style="margin-top:17px"><button class="primary-btn" data-action="open-lesson" data-id="${rec.lesson.id}">Study this lesson →</button> <button class="soft-btn" data-action="start-domain-quiz" data-domain="${rec.domain}">Practice ${esc(DOMAINS[rec.domain].short)}</button></div></article>
          <article class="card"><span class="tag">Active plan</span><h2 style="margin-top:12px">${planConfig[state.plan].name}</h2><p>${planConfig[state.plan].description}</p><button class="soft-btn" style="margin-top:17px" data-view="planner">Open planner</button></article>
        </section>
        <section class="section"><div class="section-title"><div><h2>Domain command</h2><p>Completion weighted against the official blueprint.</p></div><button class="soft-btn" data-view="analytics">Full analytics</button></div><div class="grid grid-4">${weightCards(true)}</div></section>
        <section class="section grid grid-2"><article class="card"><h3>Review queue</h3><p>${state.missedIds.length?`${state.missedIds.length} missed questions are queued with weakest-domain items first.`:'No misses yet. A diagnostic gives the system evidence to work with.'}</p><button class="soft-btn" style="margin-top:15px" data-view="review">Open smart review</button></article><article class="card"><h3>Mock evidence</h3><p>${state.lastExam?`Latest practice score: ${state.lastExam.percent}%. Use the domain report to remediate before another attempt.`:'Take the full mock after core lessons and at least two domain checkpoints.'}</p><button class="soft-btn" style="margin-top:15px" data-view="exam">${state.lastExam?'Review mock report':'View mock setup'}</button></article></section>${sourceNote()}`;
    }
    function moduleRow(m,index){
      const done=m.lessons.filter(l=>state.completedLessons.includes(l.id)).length,p=percent(done,m.lessons.length),d=DOMAINS[m.domain];
      return `<article class="module-row" style="--domain-color:${d.color}"><div class="module-num">${String(index+1).padStart(2,'0')}</div><div><div class="eyebrow">${esc(d.short)} · ${d.weight}% domain</div><h3>${esc(m.title)}</h3><div class="module-meta">${esc(m.description)} · ${m.lessons.reduce((a,l)=>a+l.minutes,0)} min</div><div class="lesson-grid">${m.lessons.map(l=>`<button class="lesson-link ${state.completedLessons.includes(l.id)?'done':''}" data-action="open-lesson" data-id="${l.id}"><span>${state.completedLessons.includes(l.id)?'✓ ':''}${esc(l.title)}</span><span>${l.minutes} min →</span></button>`).join('')}</div></div><div class="module-actions"><div class="progress-disc" style="--pct:${p}%"><span>${p}%</span></div><button class="soft-btn" data-action="start-domain-quiz" data-domain="${m.domain}">Checkpoint</button></div></article>`;
    }
    function renderCourse(){
      $('#topEyebrow').textContent='Course map';$('#topTitle').textContent=`${allLessons.length} concise lessons across 13 modules.`;
      $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Curriculum architecture</div><h1>The official outline, made learnable.</h1><p>Foundations precede products; trading and compliance then interleave application. Core lessons contain intuition, exam framing, examples, traps and active recall.</p></div><button class="primary-btn" data-action="open-lesson" data-id="${nextLesson().id}">Next lesson →</button></div>
        <section class="grid grid-4" style="margin-bottom:25px">${weightCards(true)}</section>
        <div class="module-list">${modules.map(moduleRow).join('')}</div>${sourceNote()}`;
    }
    function lessonQuestion(lesson){
      const pool=questions.filter(q=>q.domain===lesson.domain);return pool[Math.abs(allLessons.findIndex(l=>l.id===lesson.id)*3)%pool.length];
    }
    function renderLesson(){
      const lesson=allLessons.find(l=>l.id===selectedLesson)||allLessons[0],m=modules.find(x=>x.id===lesson.moduleId),q=lessonQuestion(lesson),done=state.completedLessons.includes(lesson.id);
      $('#topEyebrow').textContent=`${DOMAINS[lesson.domain].short} · ${DOMAINS[lesson.domain].weight}%`;
      $('#topTitle').textContent=lesson.title;
      $('#main').innerHTML=`<div class="lesson-layout"><div>
        <section class="lesson-hero"><div class="eyebrow">${esc(m.title)} · lesson ${m.lessons.findIndex(l=>l.id===lesson.id)+1}</div><h1>${esc(lesson.title)}</h1><p>${esc(lesson.summary)}</p><div class="lesson-meta"><span>◷ ${lesson.minutes} minutes</span><span>${done?'✓ Complete':'Core lesson'}</span><span>Domain weight ${DOMAINS[lesson.domain].weight}%</span></div></section>
        <section class="card lesson-block"><div class="eyebrow">Why this matters on test day</div><h2>Turn the fact into a decision</h2><p>${esc(lesson.why)}</p></section>
        <section class="card lesson-block"><h2>Learning objectives</h2><ul>${lesson.objectives.map(x=>`<li>${esc(x)}</li>`).join('')}</ul></section>
        <details class="deep lesson-block"><summary>Go one layer deeper</summary><div>${esc(lesson.deep)}</div></details>
        <section class="lesson-block"><h2>Core concepts</h2><div class="concept-grid">${lesson.concepts.map(x=>{const [term,detail]=x.split('|');return `<div class="concept"><strong>${esc(term)}</strong><span>${esc(detail)}</span></div>`}).join('')}</div></section>
        <section class="callout trap lesson-block"><h3>Common trap</h3><p>${esc(lesson.trap)}</p></section>
        <section class="callout lesson-block"><h3>Worked example</h3><p>${esc(lesson.example)}</p></section>
        <section class="callout gold lesson-block"><h3>Memory aid</h3><p>${esc(lesson.memory)}</p></section>
        <section class="check-card lesson-block" id="quickCheck"><div class="eyebrow">Mini knowledge check</div><h2>${esc(q.stem)}</h2><div class="check-options">${q.choices.map((c,i)=>`<button class="option-btn" data-action="quick-answer" data-index="${i}" data-qid="${q.id}"><span class="option-letter">${letters[i]}</span><span>${esc(c)}</span></button>`).join('')}</div><div id="quickFeedback" aria-live="polite"></div></section>
        <section class="card lesson-block"><div class="eyebrow">What FINRA is really testing</div><h2>Recognition under pressure</h2><p>${esc(lesson.finra)}</p><hr style="border:0;border-top:1px solid var(--line);margin:18px 0"><h3>Summary sheet</h3><ul>${lesson.summaryPoints.map(x=>`<li>${esc(x)}</li>`).join('')}</ul></section>
        <div class="lesson-actions" style="display:flex;justify-content:space-between;gap:10px;flex-wrap:wrap"><button class="soft-btn" data-action="lesson-quiz" data-domain="${lesson.domain}">End-of-lesson quiz</button><button class="primary-btn" data-action="toggle-complete" data-id="${lesson.id}">${done?'Mark incomplete':'Mark complete'} →</button></div>
      </div><aside class="card sticky-card"><span class="tag green">Lesson navigator</span><div class="lesson-nav-list">${m.lessons.map(l=>`<button data-action="open-lesson" data-id="${l.id}">${state.completedLessons.includes(l.id)?'✓ ':''}${esc(l.title)}</button>`).join('')}</div><div class="bar"><span style="width:${percent(m.lessons.filter(l=>state.completedLessons.includes(l.id)).length,m.lessons.length)}%"></span></div><p style="font-size:12px;margin-top:8px">${m.lessons.filter(l=>state.completedLessons.includes(l.id)).length} of ${m.lessons.length} complete</p><button class="soft-btn" style="width:100%;margin-top:15px" data-view="course">Back to course map</button></aside></div>${sourceNote()}`;
    }

    function quizPool(domain='mixed',difficulty='all'){
      return questions.filter(q=>(domain==='mixed'||q.domain===domain)&&(difficulty==='all'||q.difficulty===difficulty));
    }
    function startQuiz({domain='mixed',difficulty='all',timed=false,count=10,kind='quiz',ids=null}={}){
      let pool=ids?questions.filter(q=>ids.includes(q.id)):quizPool(domain,difficulty);
      if(kind==='diagnostic') pool=[...shuffle(qD1).slice(0,2),...shuffle(qD2).slice(0,5),...shuffle(qD3).slice(0,4),...shuffle(qD4).slice(0,1)];
      activeQuiz={kind,domain,questions:shuffle(pool).slice(0,Math.min(count,pool.length)),index:0,answers:{},remaining:Math.min(count,pool.length)*60,timed,started:Date.now()};
      view='quiz';history.replaceState(null,'','#quiz');renderQuiz();if(timed)setCountdown('quiz');
    }
    function quizAnswerMarkup(q,chosen){
      if(chosen===undefined)return '';
      return `<div class="answer-reasons" aria-live="polite">${q.reasons.map((r,i)=>`<div class="reason ${i===q.correct?'correct':''}"><strong>${letters[i]} · ${i===q.correct?'Correct':'Why tempting but wrong'}</strong><br>${esc(r)}</div>`).join('')}<div class="callout gold"><h3>High-yield takeaway</h3><p>${esc(q.takeaway)}</p></div></div>`;
    }
    function quizQuestionMarkup(session,isExam=false){
      const q=session.questions[session.index],chosen=session.answers[q.id];
      return `<article class="card question-card"><div style="display:flex;justify-content:space-between;gap:12px;align-items:center"><div><span class="tag" style="color:${DOMAINS[q.domain].color}">${esc(DOMAINS[q.domain].short)}</span> <span class="tag">${esc(q.difficulty)}</span></div>${isExam?`<button class="soft-btn" data-action="flag-question">${session.flags.includes(q.id)?'★ Flagged':'☆ Flag'}</button>`:''}</div><h2>${esc(q.stem)}</h2><div class="check-options">${q.choices.map((c,i)=>`<button class="option-btn ${chosen===i?'selected':''} ${!isExam&&chosen!==undefined?(i===q.correct?'correct':chosen===i?'incorrect':''):''}" data-action="${isExam?'exam-answer':'quiz-answer'}" data-index="${i}" ${!isExam&&chosen!==undefined?'disabled':''}><span class="option-letter">${letters[i]}</span><span>${esc(c)}</span></button>`).join('')}</div>${!isExam?quizAnswerMarkup(q,chosen):''}</article>`;
    }
    function renderQuiz(){
      $('#topEyebrow').textContent=activeQuiz?.kind==='diagnostic'?'Diagnostic assessment':'Practice center';$('#topTitle').textContent='Practice decisions, then study every option.';
      if(!activeQuiz){
        $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Quiz mode</div><h1>Targeted practice with full rationales.</h1><p>Every answer choice is explained. Misses automatically enter your review queue and influence recommendations.</p></div><button class="soft-btn" data-action="start-diagnostic">Take 12-question diagnostic</button></div>
          <article class="card setup-card"><h2>Build a practice set</h2><p>Select a domain and difficulty. Mixed sets interleave concepts after foundations are built.</p><div class="control-grid"><div class="field"><label for="quizDomain">Domain</label><select id="quizDomain"><option value="mixed">Mixed, officially weighted pool</option>${Object.entries(DOMAINS).map(([id,d])=>`<option value="${id}">${esc(d.short)} (${d.weight}%)</option>`).join('')}</select></div><div class="field"><label for="quizDifficulty">Difficulty</label><select id="quizDifficulty"><option value="all">All difficulties</option><option value="easy">Easy</option><option value="medium">Medium</option><option value="hard">Hard</option></select></div></div><div class="toggle-row"><div><strong>Timed mode</strong><p style="font-size:12px">One minute per question; explanations pause the pressure only after the set ends? Here the timer continues to build pacing.</p></div><label class="switch"><input id="quizTimed" type="checkbox"><span class="slider"></span></label></div><button class="primary-btn" style="margin-top:17px" data-action="start-custom-quiz">Start 10-question set →</button></article>
          <section class="section grid grid-4">${Object.entries(DOMAINS).map(([id,d])=>{const s=domainResults(id);return `<article class="card"><span class="tag" style="color:${d.color}">${d.weight}% domain</span><h3 style="margin-top:12px">${esc(d.short)}</h3><p>${s.total?`${s.accuracy}% across ${s.total} answers`:'No practice evidence yet'}</p><button class="soft-btn" style="margin-top:14px" data-action="start-domain-quiz" data-domain="${id}">Quick checkpoint</button></article>`}).join('')}</section>${sourceNote()}`;return;
      }
      const s=activeQuiz,q=s.questions[s.index],answered=Object.keys(s.answers).length;
      $('#main').innerHTML=`<div class="quiz-shell"><div class="quiz-top"><div class="quiz-progress"><div style="display:flex;justify-content:space-between;font-size:12px;color:var(--muted)"><span>${s.kind==='diagnostic'?'Diagnostic':'Practice'} · question ${s.index+1} of ${s.questions.length}</span><span>${answered} answered</span></div><div class="bar"><span style="width:${percent(s.index+1,s.questions.length)}%"></span></div></div>${s.timed?`<div class="timer" id="timer">${formatClock(s.remaining)}</div>`:''}</div>${quizQuestionMarkup(s)}<div class="quiz-actions"><button class="soft-btn" data-action="exit-quiz">Exit set</button><button class="primary-btn" data-action="next-quiz" ${s.answers[q.id]===undefined?'disabled':''}>${s.index===s.questions.length-1?'Finish set':'Next question'} →</button></div></div>`;
    }
    function recordResults(session,kind){
      const results=session.questions.map(q=>({id:q.id,domain:q.domain,topic:q.topic,correct:session.answers[q.id]===q.correct}));
      const correct=results.filter(r=>r.correct).length;
      state.quizHistory.push({date:new Date().toISOString(),kind,score:correct,total:results.length,results});
      results.filter(r=>!r.correct).forEach(r=>{if(!state.missedIds.includes(r.id))state.missedIds.push(r.id)});
      results.filter(r=>r.correct).forEach(r=>{if(kind==='review')state.missedIds=state.missedIds.filter(id=>id!==r.id)});
      return {results,correct,total:results.length,percent:percent(correct,results.length)};
    }
    function finishQuiz(timedOut=false){
      clearTimer();const session=activeQuiz,res=recordResults(session,session.kind);
      if(session.kind==='diagnostic')state.diagnosticScore=res.percent;creditTime();save();activeQuiz=null;
      $('#topEyebrow').textContent='Practice report';$('#topTitle').textContent='Use the miss, not just the score.';
      const byDomain=Object.keys(DOMAINS).map(id=>{const rs=res.results.filter(x=>x.domain===id);return rs.length?{id,total:rs.length,correct:rs.filter(x=>x.correct).length}:null}).filter(Boolean);
      $('#main').innerHTML=`<div class="quiz-shell"><article class="card exam-score"><span class="tag ${res.percent>=70?'green':'coral'}">${session.kind==='diagnostic'?'Diagnostic complete':'Set complete'}${timedOut?' · time expired':''}</span><strong>${res.percent}%</strong><h2>${res.percent>=80?'Strong command':res.percent>=70?'Productive pass-range practice':'Useful evidence—now remediate'}</h2><p>${res.correct} of ${res.total} correct. This is practice performance, not a predicted FINRA result.</p></article><section class="card section"><h2>Domain breakdown</h2>${byDomain.map(x=>`<div class="domain-result"><span>${esc(DOMAINS[x.id].short)}</span><div class="bar"><span style="width:${percent(x.correct,x.total)}%;background:${DOMAINS[x.id].color}"></span></div><strong>${percent(x.correct,x.total)}%</strong></div>`).join('')}</section><div style="display:flex;justify-content:center;gap:9px;margin-top:18px;flex-wrap:wrap"><button class="primary-btn" data-view="review">Review misses →</button><button class="soft-btn" data-view="quiz">Build another set</button><button class="soft-btn" data-view="dashboard">Dashboard</button></div></div>`;
    }
    function renderFlashcards(){
      $('#topEyebrow').textContent='Active recall';$('#topTitle').textContent='Fast retrieval, then honest confidence.';
      const available=flashcards.filter(c=>cardFilter==='all'||cardFilter==='hard'?true:c.domain===cardFilter).filter(c=>cardFilter!=='hard'||state.cardRatings[c.id]==='hard');
      if(!available.length){$('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Flashcards</div><h1>Your hard-card deck is clear.</h1><p>Mark cards hard as you study and they will collect here.</p></div></div><div class="card empty"><div class="empty-icon">✓</div><h2>No hard cards yet</h2><button class="primary-btn" data-action="card-filter" data-filter="all">Study all cards</button></div>`;return;}
      if(!cardDeck.length||!available.some(c=>c.id===cardDeck[cardIndex]?.id)){cardDeck=available;cardIndex=0;cardFlipped=false;}
      const card=cardDeck[cardIndex%cardDeck.length],rating=state.cardRatings[card.id];
      $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Flashcards</div><h1>Retrieve before you reveal.</h1><p>Click the card or press Space to flip. Rate the card so difficult concepts return to a focused deck.</p></div><div class="field"><label for="cardDomain">Deck filter</label><select id="cardDomain"><option value="all" ${cardFilter==='all'?'selected':''}>All topics</option><option value="hard" ${cardFilter==='hard'?'selected':''}>Hard cards only</option>${Object.entries(DOMAINS).map(([id,d])=>`<option value="${id}" ${cardFilter===id?'selected':''}>${esc(d.short)}</option>`).join('')}</select></div></div>
        <div class="flash-stage"><div class="flashcard ${cardFlipped?'flipped':''}" data-action="flip-card" role="button" tabindex="0" aria-label="Flashcard. Activate to flip."><div class="flash-face front"><span class="tag" style="color:${DOMAINS[card.domain].color}">${esc(DOMAINS[card.domain].short)}</span><h2>${esc(card.front)}</h2><p>Think first · tap to reveal</p></div><div class="flash-face back"><span class="tag">Answer</span><h2>${esc(card.front)}</h2><p>${esc(card.back)}</p></div></div></div>
        <div class="flash-controls"><button class="soft-btn" data-action="prev-card">← Previous</button><button class="danger-btn" data-action="rate-card" data-rating="hard">${rating==='hard'?'★ Hard':'Mark hard'}</button><button class="primary-btn" data-action="rate-card" data-rating="easy">${rating==='easy'?'✓ Easy':'Mark easy'}</button><button class="soft-btn" data-action="next-card">Next →</button><button class="soft-btn" data-action="shuffle-cards">Shuffle</button></div><p style="text-align:center;color:var(--muted);margin-top:13px">Card ${cardIndex+1} of ${cardDeck.length}</p>`;
    }
    function renderReview(){
      $('#topEyebrow').textContent='Adaptive review';$('#topTitle').textContent='Misses return until you can explain them.';
      const w=weakDomain(),missed=state.missedIds.map(id=>questions.find(q=>q.id===id)).filter(Boolean).sort((a,b)=>(a.domain===w?-1:0)-(b.domain===w?-1:0));
      if(!missed.length){$('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Smart review</div><h1>No questions are waiting.</h1><p>Take the diagnostic or a domain quiz. Every miss will enter this queue with full explanations.</p></div><button class="primary-btn" data-action="start-diagnostic">Start diagnostic →</button></div><div class="card empty"><div class="empty-icon">↻</div><h2>Your queue builds from evidence</h2><p>Correct answers in review mode remove mastered items.</p></div>${highYieldSheets()}`;return;}
      $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Smart review · ${missed.length} queued</div><h1>Start where recovery is worth the most.</h1><p>${esc(DOMAINS[w].short)} is prioritized because it is currently your weakest measured domain.</p></div><button class="primary-btn" data-action="start-review">Review ${Math.min(10,missed.length)} now →</button></div><div class="grid">${missed.slice(0,12).map((q,i)=>`<article class="card review-item"><div class="review-icon">${i+1}</div><div><span class="tag" style="color:${DOMAINS[q.domain].color}">${esc(DOMAINS[q.domain].short)} · ${esc(q.topic)}</span><h3 style="margin-top:9px">${esc(q.stem)}</h3><p>${esc(q.takeaway)}</p></div><button class="soft-btn" data-action="review-one" data-id="${q.id}">Practice</button></article>`).join('')}</div>${highYieldSheets()}`;
    }
    function highYieldSheets(){return `<section class="section"><div class="section-title"><div><div class="eyebrow">Need to know before exam day</div><h2>High-yield sheets</h2></div></div><div class="grid grid-3"><article class="card"><h3>Four instant relationships</h3><p>Rates ↑ → fixed bond prices ↓. Call buyer bullish. Put buyer bearish/protective. Diversification reduces nonsystematic risk.</p></article><article class="card"><h3>Four supervision reflexes</h3><p>Disclose outside activity. Escalate suspicious cash patterns. Never tip off a SAR. Stop and escalate possible MNPI.</p></article><article class="card"><h3>Four structure cues</h3><p>Issuer proceeds = primary. Inventory = principal. Open-end = next NAV. ETN = unsecured debt.</p></article></div></section>`;}

    function startExam(){
      activeExam={questions:shuffle(questions),index:0,answers:{},flags:[],remaining:6300,started:Date.now()};view='exam';history.replaceState(null,'','#exam');renderExam();setCountdown('exam');
    }
    function renderExam(){
      $('#topEyebrow').textContent='Full mock exam';$('#topTitle').textContent='75 scored questions · 105 minutes · four choices.';
      if(!activeExam){
        const last=state.lastExam;
        $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Exam simulator</div><h1>Practice the pressure, not just the content.</h1><p>This mock contains exactly 75 original scored questions in the official 12/33/23/7 domain allocation. The real exam currently adds five unidentified unscored pretest items, for 80 items presented.</p></div></div>
          <section class="grid grid-3"><article class="card"><span class="tag green">Format</span><h2 style="margin-top:12px">75 questions</h2><p>Four choices each. No penalty for guessing, so answer every item.</p></article><article class="card"><span class="tag gold">Pacing</span><h2 style="margin-top:12px">1:24 per scored item</h2><p>105-minute countdown, question palette, flags and free navigation.</p></article><article class="card"><span class="tag coral">Interpretation</span><h2 style="margin-top:12px">Practice evidence</h2><p>A 70 scaled score is official; this app reports raw practice percent and does not predict your result.</p></article></section>
          ${last?`<section class="card section"><div class="section-title"><div><div class="eyebrow">Latest attempt</div><h2>${last.percent}% raw practice score</h2><p>${new Date(last.date).toLocaleDateString()} · ${last.correct} of 75 correct</p></div><button class="soft-btn" data-action="show-last-exam">View report</button></div></section>`:''}
          <section class="card section"><h2>Before you start</h2><ul><li>Set aside a quiet 105-minute block.</li><li>Flag uncertainty, choose your best answer and keep moving.</li><li>Submit manually or let time expire; unanswered items score as incorrect.</li><li>Review the domain report before retaking.</li></ul><button class="primary-btn" data-action="confirm-exam">Start full mock →</button></section>${sourceNote()}`;return;
      }
      if(activeExam.report)return renderExamReport(activeExam.report);
      const s=activeExam,q=s.questions[s.index],answered=Object.keys(s.answers).length;
      $('#main').innerHTML=`<div class="exam-layout"><div><div class="quiz-top"><div class="quiz-progress"><div style="display:flex;justify-content:space-between;font-size:12px;color:var(--muted)"><span>Question ${s.index+1} of 75</span><span>${answered} answered · ${s.flags.length} flagged</span></div><div class="bar"><span style="width:${percent(answered,75)}%"></span></div></div><div class="timer" id="timer">${formatClock(s.remaining)}</div></div>${quizQuestionMarkup(s,true)}<div class="quiz-actions"><button class="soft-btn" data-action="prev-exam" ${s.index===0?'disabled':''}>← Previous</button><div><button class="soft-btn" data-action="submit-exam">Submit exam</button> <button class="primary-btn" data-action="next-exam">${s.index===74?'Review palette':'Next'} →</button></div></div></div>
        <aside class="card exam-palette"><span class="tag">Question map</span><div class="palette">${s.questions.map((item,i)=>`<button class="${s.answers[item.id]!==undefined?'answered':''} ${s.flags.includes(item.id)?'flagged':''} ${i===s.index?'current':''}" data-action="exam-jump" data-index="${i}" aria-label="Question ${i+1}${s.flags.includes(item.id)?', flagged':''}">${i+1}</button>`).join('')}</div><div style="display:grid;gap:7px;margin-top:14px;font-size:11px;color:var(--muted)"><span>Green = answered</span><span>Gold edge = flagged</span></div></aside></div>`;
    }
    function finishExam(timedOut=false){
      clearTimer();const s=activeExam,res=recordResults(s,'exam');
      const byDomain={};Object.keys(DOMAINS).forEach(id=>{const rs=res.results.filter(x=>x.domain===id);byDomain[id]={correct:rs.filter(x=>x.correct).length,total:rs.length,percent:percent(rs.filter(x=>x.correct).length,rs.length)}});
      const report={date:new Date().toISOString(),correct:res.correct,percent:res.percent,byDomain,timedOut,unanswered:75-Object.keys(s.answers).length,results:res.results};
      state.lastExam=report;creditTime();save();activeExam={report};renderExamReport(report);
    }
    function renderExamReport(report){
      $('#topEyebrow').textContent='Mock exam report';$('#topTitle').textContent='Evidence first. Remediation next.';
      const weakest=Object.entries(report.byDomain).sort((a,b)=>a[1].percent-b[1].percent)[0][0];
      $('#main').innerHTML=`<div class="quiz-shell"><article class="card exam-score"><span class="tag ${report.percent>=70?'green':'coral'}">${report.timedOut?'Time expired · ':''}raw practice result</span><strong>${report.percent}%</strong><h2>${report.percent>=80?'Strong readiness trend':report.percent>=70?'Pass-range practice result':'Remediation recommended'}</h2><p>${report.correct} of 75 correct · ${report.unanswered} unanswered. FINRA uses a scaled score; this raw result is directional and is not a pass guarantee.</p></article>
        <section class="card section"><div class="section-title"><div><h2>Domain performance</h2><p>Official question counts are preserved.</p></div></div>${Object.entries(report.byDomain).map(([id,x])=>`<div class="domain-result"><span>${esc(DOMAINS[id].short)} <small>(${x.correct}/${x.total})</small></span><div class="bar"><span style="width:${x.percent}%;background:${DOMAINS[id].color}"></span></div><strong>${x.percent}%</strong></div>`).join('')}</section>
        <section class="card recommendation section"><span class="tag green">Recommended remediation</span><h2 style="margin-top:11px">Rebuild ${esc(DOMAINS[weakest].short)} first</h2><p>Review missed rationales, complete any unfinished lessons in this domain, then score at least 80% on a fresh checkpoint before another full mock.</p><div style="margin-top:16px"><button class="primary-btn" data-action="start-review">Review missed questions →</button> <button class="soft-btn" data-action="start-domain-quiz" data-domain="${weakest}">Domain checkpoint</button></div></section>
        <div style="display:flex;justify-content:center;gap:9px;margin-top:18px;flex-wrap:wrap"><button class="soft-btn" data-action="retake-exam">Retake mock</button><button class="soft-btn" data-view="analytics">Open analytics</button><button class="soft-btn" data-action="exit-exam-report">Back to setup</button></div></div>`;
    }

    const planConfig={
      cram:{name:'2-week cram',days:14,description:'Two lessons most days, daily questions and compact high-yield review.',sessions:'60–90 min/day'},
      standard:{name:'4-week standard',days:28,description:'One lesson most days, spaced review and a measured final week.',sessions:'35–55 min/day'},
      mastery:{name:'7-week mastery',days:49,description:'Deliberate lesson spacing, interleaving and two remediation cycles.',sessions:'25–45 min/day'}
    };
    function plannerTasks(plan=state.plan){
      const cfg=planConfig[plan],tasks=[];
      for(let day=1;day<=cfg.days;day++){
        if(plan==='cram'){
          const ls=allLessons.slice((day-1)*2,day===cfg.days?allLessons.length:(day-1)*2+2);ls.forEach(l=>tasks.push({id:`${plan}-${day}-${l.id}`,day,title:l.title,type:'Core lesson',minutes:l.minutes,lesson:l.id}));
          tasks.push({id:`${plan}-${day}-practice`,day,title:day%3===0?'Cumulative mixed checkpoint':'10-question retrieval set',type:'Practice',minutes:12,view:'quiz'});
        } else if(plan==='standard'){
          const ls=day===cfg.days?allLessons.slice(day-1):allLessons.slice(day-1,day);ls.forEach(l=>tasks.push({id:`${plan}-${day}-${l.id}`,day,title:l.title,type:'Core lesson',minutes:l.minutes,lesson:l.id}));
          if(day%3===0)tasks.push({id:`${plan}-${day}-review`,day,title:'Spaced review queue',type:'Review',minutes:15,view:'review'});
          if([7,14,21,25].includes(day))tasks.push({id:`${plan}-${day}-check`,day,title:'Domain checkpoint',type:'Checkpoint',minutes:15,view:'quiz'});
          if(day===27)tasks.push({id:`${plan}-${day}-mock`,day,title:'Full 75-question mock',type:'Mock exam',minutes:105,view:'exam'});
          if(day===28)tasks.push({id:`${plan}-${day}-remediate`,day,title:'Mock remediation and final recall',type:'Review',minutes:35,view:'review'});
        } else {
          const lessonIndex=(day-1)-Math.floor((day-1)/3),l=allLessons[lessonIndex];if(day%3!==0&&l)tasks.push({id:`${plan}-${day}-${l.id}`,day,title:l.title,type:'Core lesson',minutes:l.minutes,lesson:l.id});
          if(day%3===0)tasks.push({id:`${plan}-${day}-review`,day,title:'Spaced recall + hard cards',type:'Reinforcement',minutes:25,view:'review'});
          if(day%7===0)tasks.push({id:`${plan}-${day}-check`,day,title:'Interleaved weekly checkpoint',type:'Checkpoint',minutes:22,view:'quiz'});
          if(day===42)tasks.push({id:`${plan}-${day}-mock`,day,title:'Full 75-question mock',type:'Mock exam',minutes:105,view:'exam'});
          if(day>42&&day%2===1)tasks.push({id:`${plan}-${day}-repair`,day,title:'Weak-domain remediation',type:'Targeted review',minutes:30,view:'review'});
        }
      }return tasks;
    }
    function renderPlanner(){
      const cfg=planConfig[state.plan],tasks=plannerTasks(),done=tasks.filter(t=>state.completedTasks.includes(t.id)).length,rec=topRecommendation();
      $('#topEyebrow').textContent='Study planner';$('#topTitle').textContent='A plan that responds to evidence.';
      $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Study paths</div><h1>Choose the pace. Keep the sequence.</h1><p>Plans move from foundation to interleaving to simulated performance. Your weakest domain is added to the daily recommendation layer.</p></div><button class="soft-btn" data-action="start-diagnostic">Take diagnostic</button></div>
        <div class="plan-cards">${Object.entries(planConfig).map(([id,p])=>`<article class="card plan-card ${state.plan===id?'selected':''}"><span class="tag ${state.plan===id?'green':''}">${state.plan===id?'Active plan':'Study option'}</span><div class="duration">${p.days} days</div><h3>${esc(p.name)}</h3><p>${esc(p.description)}</p><p style="margin-top:8px"><strong>${p.sessions}</strong></p><button class="${state.plan===id?'soft-btn':'primary-btn'}" style="margin-top:14px" data-action="set-plan" data-plan="${id}">${state.plan===id?'Selected':'Choose plan'}</button></article>`).join('')}</div>
        <section class="card recommendation section"><span class="tag green">Auto-adjusted focus</span><h2 style="margin-top:10px">Add ${esc(rec.title)} to your next session</h2><p>${esc(rec.reason)} This recommendation changes as new quiz and mock evidence arrives.</p><button class="soft-btn" style="margin-top:14px" data-action="open-lesson" data-id="${rec.lesson.id}">Open recommendation</button></section>
        <section class="section"><div class="section-title"><div><div class="eyebrow">${esc(cfg.name)}</div><h2>Daily task generator</h2><p>${done} of ${tasks.length} tasks complete · ${percent(done,tasks.length)}%</p></div><button class="soft-btn" data-action="reset-plan-tasks">Reset task checks</button></div><div class="task-list">${tasks.map(t=>`<label class="task ${state.completedTasks.includes(t.id)?'done':''}"><input type="checkbox" data-task-id="${t.id}" ${state.completedTasks.includes(t.id)?'checked':''}><span class="day">Day ${t.day}</span><span class="task-title">${esc(t.title)} <small style="display:block;color:var(--muted)">${esc(t.type)} · ${t.minutes} min</small></span><button type="button" class="pill" data-action="open-task" data-lesson="${t.lesson||''}" data-target="${t.view||''}">Open →</button></label>`).join('')}</div></section>${sourceNote()}`;
    }
    function renderAnalytics(){
      const all=state.quizHistory.flatMap(h=>h.results||[]),acc=percent(all.filter(x=>x.correct).length,all.length),rec=topRecommendation(),history=state.quizHistory.slice(-10);
      const topicMap={};all.forEach(r=>{topicMap[r.topic]??={c:0,t:0};topicMap[r.topic].t++;if(r.correct)topicMap[r.topic].c++;});
      const weakTopics=Object.entries(topicMap).map(([topic,x])=>({topic,accuracy:percent(x.c,x.t),total:x.t})).sort((a,b)=>a.accuracy-b.accuracy).slice(0,6);
      $('#topEyebrow').textContent='Learning analytics';$('#topTitle').textContent='Signals, not false precision.';
      $('#main').innerHTML=`<div class="page-head"><div><div class="eyebrow">Analytics</div><h1>Know what your score needs next.</h1><p>Analytics use only your activity on this device. Readiness is advisory and intentionally avoids certainty claims.</p></div></div>
        <div class="grid grid-4"><article class="card metric-card"><span class="metric-label">Directional readiness</span><strong class="metric-value">${readiness()}</strong><span class="metric-sub">${readinessLabel()}</span></article><article class="card metric-card"><span class="metric-label">Practice accuracy</span><strong class="metric-value">${all.length?acc+'%':'—'}</strong><span class="metric-sub">${all.length} total answers</span></article><article class="card metric-card"><span class="metric-label">Lessons</span><strong class="metric-value">${state.completedLessons.length}/${allLessons.length}</strong><span class="metric-sub">${completion()}% complete</span></article><article class="card metric-card"><span class="metric-label">Hard flashcards</span><strong class="metric-value">${Object.values(state.cardRatings).filter(x=>x==='hard').length}</strong><span class="metric-sub">Targeted recall deck</span></article></div>
        <section class="section grid grid-2"><article class="card"><h2>Accuracy by domain</h2>${Object.entries(DOMAINS).map(([id,d])=>{const x=domainResults(id);return `<div class="domain-result"><span>${esc(d.short)}</span><div class="bar"><span style="width:${x.accuracy}%;background:${d.color}"></span></div><strong>${x.total?x.accuracy+'%':'—'}</strong></div>`}).join('')}</article>
          <article class="card"><h2>Accuracy trend</h2>${history.length?`<div class="chart">${history.map((h,i)=>`<div class="chart-col"><div class="chart-bar" style="height:${Math.max(4,percent(h.score,h.total))}%" title="${percent(h.score,h.total)}%"></div><span>${i+1}</span></div>`).join('')}</div><p style="font-size:11px">Last ${history.length} sessions · raw practice accuracy</p>`:'<div class="empty"><div class="empty-icon">↗</div><p>Complete a quiz to build the trend.</p></div>'}</article></section>
        <section class="card recommendation section"><span class="tag green">Most likely to improve your score next</span><h2 style="margin-top:10px">${esc(rec.title)}</h2><p>${esc(rec.reason)}</p><button class="primary-btn" style="margin-top:14px" data-action="open-lesson" data-id="${rec.lesson.id}">Act on recommendation →</button></section>
        <section class="section grid grid-2"><article class="card"><h2>Weak concept tags</h2>${weakTopics.length?weakTopics.map(x=>`<div style="display:flex;justify-content:space-between;padding:9px 0;border-bottom:1px solid var(--line)"><span>${esc(x.topic)}</span><strong>${x.accuracy}% <small style="color:var(--muted)">(${x.total})</small></strong></div>`).join(''):'<p>No topic evidence yet.</p>'}</article><article class="card"><h2>Readiness ingredients</h2><p>35% lesson completion + 45% practice accuracy + 20% diagnostic or latest mock evidence. The output is capped at 99 and is not a probability of passing.</p><div class="bar" style="height:12px;margin-top:20px"><span style="width:${readiness()}%"></span></div><button class="soft-btn" style="margin-top:16px" data-action="export-progress">Export progress JSON</button></article></section>${sourceNote()}`;
    }

    function showDialog(html){$('#dialogBody').innerHTML=html;$('#dialog').showModal();}
    function closeDialog(){$('#dialog').close();}
    function quickAnswer(btn){
      const q=questions.find(x=>x.id===btn.dataset.qid),chosen=Number(btn.dataset.index),wrap=btn.closest('.check-card');
      wrap.querySelectorAll('.option-btn').forEach((b,i)=>{b.disabled=true;b.classList.toggle('correct',i===q.correct);b.classList.toggle('incorrect',i===chosen&&i!==q.correct)});
      wrap.querySelector('#quickFeedback').innerHTML=`<div class="callout ${chosen===q.correct?'':'trap'}"><h3>${chosen===q.correct?'Correct':'Not quite'}</h3><p>${esc(q.reasons[chosen])}</p><p><strong>Takeaway:</strong> ${esc(q.takeaway)}</p></div>`;
    }
    function exportProgress(){
      const payload={exportedAt:new Date().toISOString(),app:'SIE Compass',readiness:readiness(),note:'Directional study metric; not a pass prediction.',state};
      const blob=new Blob([JSON.stringify(payload,null,2)],{type:'application/json'}),url=URL.createObjectURL(blob),a=document.createElement('a');a.href=url;a.download='sie-compass-progress.json';a.click();setTimeout(()=>URL.revokeObjectURL(url),500);toast('Progress export downloaded');
    }
    document.addEventListener('click',e=>{
      const btn=e.target.closest('button,[data-action]');if(!btn)return;
      if(btn.dataset.view){go(btn.dataset.view);return;}
      const a=btn.dataset.action;
      if(a==='open-lesson')go('lesson',btn.dataset.id);
      else if(a==='quick-study')startQuiz({domain:weakDomain(),count:10});
      else if(a==='set-plan'){state.plan=btn.dataset.plan;state.completedTasks=[];save();toast(`${planConfig[state.plan].name} activated`);go('planner');}
      else if(a==='toggle-complete'){
        const id=btn.dataset.id;if(state.completedLessons.includes(id))state.completedLessons=state.completedLessons.filter(x=>x!==id);else state.completedLessons.push(id);creditTime();save();renderLesson();toast(state.completedLessons.includes(id)?'Lesson marked complete':'Lesson reopened');
      }
      else if(a==='quick-answer')quickAnswer(btn);
      else if(a==='start-diagnostic')startQuiz({kind:'diagnostic',count:12});
      else if(a==='start-custom-quiz')startQuiz({domain:$('#quizDomain').value,difficulty:$('#quizDifficulty').value,timed:$('#quizTimed').checked,count:10});
      else if(a==='start-domain-quiz')startQuiz({domain:btn.dataset.domain,count:10});
      else if(a==='lesson-quiz')startQuiz({domain:btn.dataset.domain,count:5});
      else if(a==='quiz-answer'){
        if(!activeQuiz)return;const q=activeQuiz.questions[activeQuiz.index];activeQuiz.answers[q.id]=Number(btn.dataset.index);renderQuiz();
      }
      else if(a==='next-quiz'){
        if(!activeQuiz)return;const q=activeQuiz.questions[activeQuiz.index];if(activeQuiz.answers[q.id]===undefined)return toast('Choose an answer first');
        if(activeQuiz.index===activeQuiz.questions.length-1)finishQuiz();else{activeQuiz.index++;renderQuiz();window.scrollTo(0,0);}
      }
      else if(a==='exit-quiz')go('quiz');
      else if(a==='flip-card'){cardFlipped=!cardFlipped;renderFlashcards();}
      else if(a==='prev-card'){cardIndex=(cardIndex-1+cardDeck.length)%cardDeck.length;cardFlipped=false;renderFlashcards();}
      else if(a==='next-card'){cardIndex=(cardIndex+1)%cardDeck.length;cardFlipped=false;renderFlashcards();}
      else if(a==='shuffle-cards'){cardDeck=shuffle(cardDeck);cardIndex=0;cardFlipped=false;renderFlashcards();toast('Deck shuffled');}
      else if(a==='rate-card'){
        const card=cardDeck[cardIndex];state.cardRatings[card.id]=btn.dataset.rating;save();cardIndex=(cardIndex+1)%cardDeck.length;cardFlipped=false;renderFlashcards();
      }
      else if(a==='card-filter'){cardFilter=btn.dataset.filter;cardDeck=[];renderFlashcards();}
      else if(a==='start-review'){
        if(!state.missedIds.length)return toast('Your review queue is clear');const w=weakDomain(),ids=state.missedIds.map(id=>questions.find(q=>q.id===id)).filter(Boolean).sort((a,b)=>Number(b.domain===w)-Number(a.domain===w)).slice(0,10).map(q=>q.id);startQuiz({kind:'review',ids,count:10});
      }
      else if(a==='review-one')startQuiz({kind:'review',ids:[btn.dataset.id],count:1});
      else if(a==='confirm-exam')showDialog(`<h2>Start the 105-minute mock?</h2><p>The timer begins immediately. Your local progress is safe, but the active attempt is not preserved if the browser closes.</p><div class="dialog-actions"><button class="soft-btn" data-action="close-dialog">Not yet</button><button class="primary-btn" data-action="start-exam-now">Start timer</button></div>`);
      else if(a==='close-dialog')closeDialog();
      else if(a==='start-exam-now'){closeDialog();startExam();}
      else if(a==='exam-answer'){
        if(!activeExam||activeExam.report)return;const q=activeExam.questions[activeExam.index];activeExam.answers[q.id]=Number(btn.dataset.index);renderExam();
      }
      else if(a==='flag-question'){
        const id=activeExam.questions[activeExam.index].id;activeExam.flags=activeExam.flags.includes(id)?activeExam.flags.filter(x=>x!==id):[...activeExam.flags,id];renderExam();
      }
      else if(a==='prev-exam'){activeExam.index=Math.max(0,activeExam.index-1);renderExam();window.scrollTo(0,0);}
      else if(a==='next-exam'){activeExam.index=Math.min(74,activeExam.index+1);renderExam();window.scrollTo(0,0);}
      else if(a==='exam-jump'){activeExam.index=Number(btn.dataset.index);renderExam();window.scrollTo(0,0);}
      else if(a==='submit-exam'){
        const unanswered=75-Object.keys(activeExam.answers).length;showDialog(`<h2>Submit this mock?</h2><p>${unanswered?`${unanswered} question${unanswered===1?' is':'s are'} unanswered and will score as incorrect.`:'All 75 questions are answered.'}</p><div class="dialog-actions"><button class="soft-btn" data-action="close-dialog">Keep working</button><button class="danger-btn" data-action="submit-exam-now">Submit exam</button></div>`);
      }
      else if(a==='submit-exam-now'){closeDialog();finishExam();}
      else if(a==='retake-exam')showDialog(`<h2>Retake the full mock?</h2><p>Your previous report remains in analytics until this new attempt is submitted.</p><div class="dialog-actions"><button class="soft-btn" data-action="close-dialog">Cancel</button><button class="primary-btn" data-action="start-exam-now">Start retake</button></div>`);
      else if(a==='show-last-exam'){activeExam={report:state.lastExam};renderExam();}
      else if(a==='exit-exam-report'){activeExam=null;renderExam();}
      else if(a==='open-task'){if(btn.dataset.lesson)go('lesson',btn.dataset.lesson);else if(btn.dataset.target)go(btn.dataset.target);}
      else if(a==='reset-plan-tasks')showDialog(`<h2>Reset task checks?</h2><p>This clears planner checkmarks but keeps lesson completion, quiz history and review evidence.</p><div class="dialog-actions"><button class="soft-btn" data-action="close-dialog">Cancel</button><button class="danger-btn" data-action="reset-plan-now">Reset checks</button></div>`);
      else if(a==='reset-plan-now'){state.completedTasks=[];save();closeDialog();renderPlanner();toast('Planner checks reset');}
      else if(a==='export-progress')exportProgress();
    });
    document.addEventListener('change',e=>{
      if(e.target.id==='cardDomain'){cardFilter=e.target.value;cardDeck=[];cardIndex=0;cardFlipped=false;renderFlashcards();}
      if(e.target.matches('[data-task-id]')){const id=e.target.dataset.taskId;if(e.target.checked&&!state.completedTasks.includes(id))state.completedTasks.push(id);if(!e.target.checked)state.completedTasks=state.completedTasks.filter(x=>x!==id);save();renderPlanner();}
    });
    document.addEventListener('keydown',e=>{
      if(view==='flashcards'&&(e.code==='Space'||e.key==='Enter')&&!['INPUT','SELECT','BUTTON'].includes(document.activeElement.tagName)){e.preventDefault();cardFlipped=!cardFlipped;renderFlashcards();}
      if(view==='exam'&&activeExam&&!activeExam.report&&/^[1-4]$/.test(e.key)){const q=activeExam.questions[activeExam.index];activeExam.answers[q.id]=Number(e.key)-1;renderExam();}
    });
    $('#themeToggle').addEventListener('click',()=>{state.theme=state.theme==='dark'?'light':'dark';save();});
    window.addEventListener('beforeunload',()=>{creditTime();localStorage.setItem(STORAGE_KEY,JSON.stringify(state));});
    setInterval(()=>{creditTime();save();},60000);
    (function init(){
      const parts=location.hash.replace('#','').split('/');if(parts[0]&&['home','dashboard','course','lesson','quiz','flashcards','review','exam','planner','analytics'].includes(parts[0]))view=parts[0];if(view==='lesson'&&parts[1])selectedLesson=parts[1];
      const expected={d1:12,d2:33,d3:23,d4:7};Object.keys(expected).forEach(id=>{const actual=questions.filter(q=>q.domain===id).length;if(actual!==expected[id])console.error(`Question weighting error for ${id}: ${actual}`)});
      render();
    })();
  </script>
</body>
</html>
