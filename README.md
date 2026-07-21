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
