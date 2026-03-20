[index.html.html](https://github.com/user-attachments/files/26138699/index.html.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CivicPulse — Report & Resolve</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0e1a;
    --surface: #111827;
    --surface2: #1a2235;
    --border: rgba(255,255,255,0.07);
    --accent: #00e5a0;
    --accent2: #ff6b35;
    --accent3: #4f8bff;
    --text: #e8edf5;
    --muted: #5a6680;
    --red: #ff4757;
    --yellow: #ffd32a;
    --green: #00e5a0;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,229,160,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,160,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* ─── NAV ─── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 40px;
    background: rgba(10,14,26,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }

  .logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.35rem;
    letter-spacing: -0.02em;
  }
  .logo span { color: var(--accent); }

  .nav-links {
    display: flex;
    gap: 32px;
    list-style: none;
  }
  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.875rem;
    font-weight: 500;
    transition: color 0.2s;
  }
  .nav-links a:hover, .nav-links a.active { color: var(--text); }

  .nav-actions {
    display: flex;
    gap: 12px;
    align-items: center;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 9px 20px;
    border-radius: 8px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.875rem;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    border: none;
    text-decoration: none;
  }
  .btn-ghost {
    background: transparent;
    color: var(--muted);
    border: 1px solid var(--border);
  }
  .btn-ghost:hover { border-color: rgba(255,255,255,0.2); color: var(--text); }

  .btn-primary {
    background: var(--accent);
    color: #000;
    font-weight: 600;
  }
  .btn-primary:hover { background: #00ffb3; transform: translateY(-1px); }

  /* ─── HERO ─── */
  .hero {
    position: relative;
    z-index: 1;
    padding: 160px 40px 80px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,229,160,0.08);
    border: 1px solid rgba(0,229,160,0.2);
    border-radius: 100px;
    padding: 6px 14px;
    font-size: 0.78rem;
    color: var(--accent);
    font-weight: 500;
    margin-bottom: 28px;
    animation: fadeUp 0.6s ease forwards;
  }
  .badge-dot {
    width: 6px; height: 6px;
    background: var(--accent);
    border-radius: 50%;
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.4); }
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.8rem, 6vw, 5rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.03em;
    margin-bottom: 24px;
    animation: fadeUp 0.6s 0.1s ease both;
  }
  .hero h1 em {
    font-style: normal;
    color: var(--accent);
    position: relative;
  }

  .hero p {
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 520px;
    line-height: 1.7;
    margin-bottom: 40px;
    font-weight: 300;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-cta {
    display: flex;
    gap: 14px;
    flex-wrap: wrap;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .btn-large {
    padding: 14px 28px;
    font-size: 1rem;
    border-radius: 10px;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ─── STATS BAR ─── */
  .stats-bar {
    position: relative;
    z-index: 1;
    background: var(--surface);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 28px 40px;
  }
  .stats-inner {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
  }
  .stat-item {
    padding: 0 32px;
    border-right: 1px solid var(--border);
    text-align: center;
  }
  .stat-item:last-child { border-right: none; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    color: var(--text);
    line-height: 1;
    margin-bottom: 4px;
  }
  .stat-num span { color: var(--accent); }
  .stat-label { font-size: 0.8rem; color: var(--muted); font-weight: 400; }

  /* ─── MAIN LAYOUT ─── */
  .main {
    position: relative;
    z-index: 1;
    max-width: 1200px;
    margin: 0 auto;
    padding: 60px 40px;
    display: grid;
    grid-template-columns: 1fr 380px;
    gap: 32px;
    align-items: start;
  }

  /* ─── FILTER BAR ─── */
  .section-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 24px;
    gap: 16px;
    flex-wrap: wrap;
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 1.3rem;
    font-weight: 700;
  }

  .filters {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
  }
  .filter-btn {
    padding: 6px 14px;
    border-radius: 6px;
    font-size: 0.8rem;
    font-weight: 500;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--muted);
    cursor: pointer;
    transition: all 0.2s;
    font-family: 'DM Sans', sans-serif;
  }
  .filter-btn:hover { border-color: rgba(255,255,255,0.2); color: var(--text); }
  .filter-btn.active {
    background: var(--accent);
    color: #000;
    border-color: var(--accent);
    font-weight: 600;
  }

  /* ─── ISSUE CARDS ─── */
  .issues-list {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .issue-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    transition: all 0.25s;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    animation: fadeUp 0.5s ease both;
  }
  .issue-card::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 3px;
    background: var(--card-accent, var(--accent));
    border-radius: 3px 0 0 3px;
  }
  .issue-card:hover {
    border-color: rgba(255,255,255,0.15);
    transform: translateY(-2px);
    box-shadow: 0 12px 40px rgba(0,0,0,0.4);
  }

  .issue-top {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 12px;
  }

  .issue-meta {
    display: flex;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
  }

  .category-tag {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    padding: 4px 10px;
    border-radius: 5px;
    font-size: 0.72rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .status-badge {
    padding: 4px 10px;
    border-radius: 100px;
    font-size: 0.72rem;
    font-weight: 600;
  }
  .status-open { background: rgba(255,71,87,0.12); color: var(--red); border: 1px solid rgba(255,71,87,0.25); }
  .status-progress { background: rgba(255,211,42,0.1); color: var(--yellow); border: 1px solid rgba(255,211,42,0.2); }
  .status-resolved { background: rgba(0,229,160,0.1); color: var(--accent); border: 1px solid rgba(0,229,160,0.2); }

  .issue-title {
    font-family: 'Syne', sans-serif;
    font-size: 1.05rem;
    font-weight: 700;
    line-height: 1.3;
    margin-bottom: 8px;
    color: var(--text);
  }

  .issue-desc {
    font-size: 0.875rem;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 16px;
  }

  .issue-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
  }

  .issue-location {
    display: flex;
    align-items: center;
    gap: 5px;
    font-size: 0.8rem;
    color: var(--muted);
  }

  .issue-actions {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .vote-btn {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 0.82rem;
    color: var(--muted);
    cursor: pointer;
    transition: all 0.2s;
    background: none;
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 5px 10px;
    font-family: 'DM Sans', sans-serif;
  }
  .vote-btn:hover { color: var(--accent); border-color: var(--accent); }
  .vote-btn.voted { color: var(--accent); border-color: var(--accent); background: rgba(0,229,160,0.07); }

  .comment-count {
    display: flex;
    align-items: center;
    gap: 5px;
    font-size: 0.82rem;
    color: var(--muted);
  }

  .issue-time {
    font-size: 0.78rem;
    color: var(--muted);
    margin-left: auto;
  }

  /* ─── PRIORITY INDICATOR ─── */
  .priority-ring {
    width: 42px; height: 42px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.7rem;
    font-weight: 700;
    flex-shrink: 0;
  }
  .priority-critical { background: rgba(255,71,87,0.15); color: var(--red); border: 2px solid var(--red); }
  .priority-high { background: rgba(255,107,53,0.15); color: var(--accent2); border: 2px solid var(--accent2); }
  .priority-medium { background: rgba(255,211,42,0.1); color: var(--yellow); border: 2px solid var(--yellow); }
  .priority-low { background: rgba(0,229,160,0.1); color: var(--accent); border: 2px solid var(--accent); }

  /* ─── SIDEBAR ─── */
  .sidebar {
    display: flex;
    flex-direction: column;
    gap: 20px;
    position: sticky;
    top: 90px;
  }

  .sidebar-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
  }

  .sidebar-card-header {
    padding: 18px 20px;
    border-bottom: 1px solid var(--border);
    font-family: 'Syne', sans-serif;
    font-size: 0.95rem;
    font-weight: 700;
  }

  .sidebar-card-body { padding: 20px; }

  /* Report Form */
  .form-group { margin-bottom: 16px; }
  .form-label {
    display: block;
    font-size: 0.8rem;
    font-weight: 500;
    color: var(--muted);
    margin-bottom: 6px;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }
  .form-input, .form-select, .form-textarea {
    width: 100%;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 10px 14px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.875rem;
    transition: border-color 0.2s;
    outline: none;
    -webkit-appearance: none;
  }
  .form-input:focus, .form-select:focus, .form-textarea:focus {
    border-color: rgba(0,229,160,0.4);
    box-shadow: 0 0 0 3px rgba(0,229,160,0.06);
  }
  .form-textarea { resize: vertical; min-height: 80px; line-height: 1.5; }
  .form-select option { background: var(--surface2); }

  .upload-zone {
    border: 2px dashed var(--border);
    border-radius: 8px;
    padding: 24px;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s;
  }
  .upload-zone:hover { border-color: var(--accent); background: rgba(0,229,160,0.03); }
  .upload-icon { font-size: 1.5rem; margin-bottom: 6px; }
  .upload-text { font-size: 0.8rem; color: var(--muted); }
  .upload-text strong { color: var(--accent); }

  .submit-btn {
    width: 100%;
    padding: 12px;
    background: var(--accent);
    color: #000;
    border: none;
    border-radius: 8px;
    font-family: 'Syne', sans-serif;
    font-size: 0.95rem;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
    margin-top: 4px;
  }
  .submit-btn:hover { background: #00ffb3; transform: translateY(-1px); }

  /* Leaderboard */
  .leaderboard-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
  }
  .leaderboard-item:last-child { border-bottom: none; }
  .lb-rank {
    width: 24px;
    text-align: center;
    font-family: 'Syne', sans-serif;
    font-size: 0.8rem;
    font-weight: 800;
    color: var(--muted);
  }
  .lb-rank.gold { color: #ffd700; }
  .lb-rank.silver { color: #c0c0c0; }
  .lb-rank.bronze { color: #cd7f32; }
  .lb-avatar {
    width: 32px; height: 32px;
    border-radius: 50%;
    background: var(--surface2);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.75rem;
    font-weight: 600;
    border: 1.5px solid var(--border);
    flex-shrink: 0;
  }
  .lb-info { flex: 1; min-width: 0; }
  .lb-name { font-size: 0.82rem; font-weight: 500; truncate: true; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .lb-pts { font-size: 0.72rem; color: var(--muted); }
  .lb-score {
    font-family: 'Syne', sans-serif;
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--accent);
  }

  /* District map placeholder */
  .map-placeholder {
    height: 180px;
    background: var(--surface2);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 8px;
    color: var(--muted);
    font-size: 0.85rem;
    position: relative;
    overflow: hidden;
  }
  .map-placeholder svg { opacity: 0.3; }

  /* Hot tags */
  .tags-cloud {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .hot-tag {
    padding: 5px 12px;
    border-radius: 6px;
    font-size: 0.78rem;
    font-weight: 500;
    background: var(--surface2);
    color: var(--muted);
    border: 1px solid var(--border);
    cursor: pointer;
    transition: all 0.2s;
  }
  .hot-tag:hover { color: var(--text); border-color: rgba(255,255,255,0.2); }
  .hot-tag .count { color: var(--accent); margin-left: 4px; font-weight: 600; }

  /* ─── TOAST ─── */
  .toast {
    position: fixed;
    bottom: 32px;
    right: 32px;
    background: var(--surface);
    border: 1px solid rgba(0,229,160,0.3);
    border-radius: 10px;
    padding: 14px 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    z-index: 999;
    transform: translateY(80px);
    opacity: 0;
    transition: all 0.35s cubic-bezier(0.34,1.56,0.64,1);
    box-shadow: 0 8px 32px rgba(0,0,0,0.4);
    max-width: 320px;
  }
  .toast.show { transform: translateY(0); opacity: 1; }
  .toast-icon { font-size: 1.2rem; }
  .toast-text { font-size: 0.875rem; }
  .toast-title { font-weight: 600; margin-bottom: 2px; }
  .toast-sub { color: var(--muted); font-size: 0.8rem; }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 900px) {
    nav { padding: 14px 20px; }
    .nav-links { display: none; }
    .hero { padding: 120px 20px 60px; }
    .stats-inner { grid-template-columns: repeat(2, 1fr); }
    .stat-item:nth-child(2) { border-right: none; }
    .main { grid-template-columns: 1fr; padding: 40px 20px; }
    .sidebar { position: static; }
  }

  /* MAP MODAL */
  .map-modal { display:none; position:fixed; inset:0; z-index:500; background:rgba(5,8,18,0.85); backdrop-filter:blur(8px); align-items:center; justify-content:center; padding:20px; }
  .map-modal.open { display:flex; animation:modalIn 0.3s cubic-bezier(0.34,1.4,0.64,1); }
  @keyframes modalIn { from{opacity:0;transform:scale(0.95)} to{opacity:1;transform:scale(1)} }
  .map-container { background:var(--surface); border:1px solid var(--border); border-radius:18px; width:100%; max-width:1100px; max-height:90vh; display:flex; flex-direction:column; overflow:hidden; box-shadow:0 30px 80px rgba(0,0,0,0.6); }
  .map-modal-header { display:flex; align-items:center; justify-content:space-between; padding:18px 24px; border-bottom:1px solid var(--border); flex-shrink:0; }
  .map-modal-title { font-family:'Syne',sans-serif; font-size:1.1rem; font-weight:700; }
  .map-modal-sub { font-size:0.8rem; color:var(--muted); margin-top:2px; }
  .map-legend { display:flex; align-items:center; gap:6px; font-size:0.78rem; color:var(--muted); }
  .legend-dot { width:8px; height:8px; border-radius:50%; display:inline-block; vertical-align:middle; }
  .map-close { width:32px; height:32px; border-radius:50%; background:var(--surface2); border:1px solid var(--border); color:var(--muted); font-size:0.8rem; cursor:pointer; display:flex; align-items:center; justify-content:center; transition:all 0.2s; }
  .map-close:hover { background:var(--red); color:white; border-color:var(--red); }
  .map-body { display:grid; grid-template-columns:1fr 280px; flex:1; min-height:0; overflow:hidden; }
  .map-svg-wrap { position:relative; background:#0d1422; overflow:hidden; border-right:1px solid var(--border); }
  .mpin { transition:transform 0.15s; }
  .pin-tooltip { position:absolute; bottom:20px; left:20px; background:var(--surface); border:1px solid rgba(255,255,255,0.12); border-radius:10px; padding:14px 16px; width:240px; display:none; box-shadow:0 8px 24px rgba(0,0,0,0.5); pointer-events:none; animation:fadeUp 0.2s ease; }
  .pin-tooltip.visible { display:block; }
  .pin-tooltip-cat { font-size:0.72rem; font-weight:600; text-transform:uppercase; letter-spacing:0.04em; color:var(--accent); margin-bottom:4px; }
  .pin-tooltip-title { font-family:'Syne',sans-serif; font-size:0.9rem; font-weight:700; margin-bottom:4px; line-height:1.3; }
  .pin-tooltip-loc { font-size:0.78rem; color:var(--muted); margin-bottom:10px; }
  .pin-tooltip-footer { display:flex; align-items:center; justify-content:space-between; }
  .pin-votes { font-size:0.78rem; color:var(--muted); }
  .map-side { overflow-y:auto; padding:16px; display:flex; flex-direction:column; gap:10px; }
  .map-side-title { font-family:'Syne',sans-serif; font-size:0.85rem; font-weight:700; color:var(--muted); text-transform:uppercase; letter-spacing:0.05em; margin-bottom:4px; }
  .map-issue-item { background:var(--surface2); border:1px solid var(--border); border-radius:8px; padding:10px 12px; cursor:pointer; transition:all 0.2s; border-left:3px solid var(--item-accent,var(--accent)); }
  .map-issue-item:hover { border-color:rgba(255,255,255,0.15); transform:translateX(2px); }
  .map-issue-item-title { font-size:0.8rem; font-weight:600; margin-bottom:4px; line-height:1.3; }
  .map-issue-item-meta { font-size:0.72rem; color:var(--muted); display:flex; justify-content:space-between; align-items:center; }


  /* ─── AUTH MODAL ─── */
  .auth-overlay {
    display: none; position: fixed; inset: 0; z-index: 600;
    background: rgba(5,8,18,0.92); backdrop-filter: blur(12px);
    align-items: center; justify-content: center; padding: 20px;
  }
  .auth-overlay.open { display: flex; animation: modalIn 0.35s cubic-bezier(0.34,1.4,0.64,1); }
  .auth-box {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 20px; width: 100%; max-width: 440px;
    overflow: hidden; box-shadow: 0 40px 100px rgba(0,0,0,0.7);
  }
  .auth-top {
    padding: 32px 32px 0;
    text-align: center;
  }
  .auth-icon {
    width: 56px; height: 56px; border-radius: 16px;
    background: rgba(0,229,160,0.1); border: 1px solid rgba(0,229,160,0.25);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.6rem; margin: 0 auto 16px;
  }
  .auth-title {
    font-family: 'Syne', sans-serif; font-size: 1.5rem;
    font-weight: 800; margin-bottom: 6px; letter-spacing: -0.02em;
  }
  .auth-sub { font-size: 0.875rem; color: var(--muted); line-height: 1.5; margin-bottom: 28px; }
  .auth-body { padding: 0 32px 32px; }
  .auth-tabs {
    display: flex; background: var(--surface2); border-radius: 10px;
    padding: 4px; margin-bottom: 24px; gap: 4px;
  }
  .auth-tab {
    flex: 1; padding: 8px; border-radius: 7px; border: none;
    font-family: 'DM Sans', sans-serif; font-size: 0.875rem; font-weight: 600;
    cursor: pointer; transition: all 0.2s; background: transparent; color: var(--muted);
  }
  .auth-tab.active { background: var(--surface); color: var(--text); box-shadow: 0 2px 8px rgba(0,0,0,0.3); }
  .auth-form { display: none; flex-direction: column; gap: 14px; }
  .auth-form.active { display: flex; }
  .auth-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .auth-input-wrap { position: relative; }
  .auth-input-icon {
    position: absolute; left: 12px; top: 50%; transform: translateY(-50%);
    font-size: 0.9rem; pointer-events: none;
  }
  .auth-input {
    width: 100%; background: var(--surface2); border: 1px solid var(--border);
    border-radius: 9px; padding: 11px 14px 11px 36px;
    color: var(--text); font-family: 'DM Sans', sans-serif; font-size: 0.875rem;
    outline: none; transition: border-color 0.2s;
  }
  .auth-input:focus { border-color: rgba(0,229,160,0.4); box-shadow: 0 0 0 3px rgba(0,229,160,0.06); }
  .auth-input.no-icon { padding-left: 14px; }
  .ward-select { padding-left: 36px; -webkit-appearance: none; }
  .auth-divider {
    display: flex; align-items: center; gap: 10px;
    font-size: 0.75rem; color: var(--muted); margin: 4px 0;
  }
  .auth-divider::before, .auth-divider::after {
    content: ''; flex: 1; height: 1px; background: var(--border);
  }
  .auth-btn {
    width: 100%; padding: 13px; background: var(--accent); color: #000;
    border: none; border-radius: 9px; font-family: 'Syne', sans-serif;
    font-size: 1rem; font-weight: 700; cursor: pointer; transition: all 0.2s;
    display: flex; align-items: center; justify-content: center; gap: 8px;
  }
  .auth-btn:hover { background: #00ffb3; transform: translateY(-1px); }
  .auth-btn:disabled { opacity: 0.5; cursor: not-allowed; transform: none; }
  .auth-error {
    background: rgba(255,71,87,0.1); border: 1px solid rgba(255,71,87,0.25);
    border-radius: 8px; padding: 10px 14px; font-size: 0.8rem; color: var(--red);
    display: none;
  }
  .auth-error.show { display: block; }
  .auth-close {
    position: absolute; top: 16px; right: 16px;
    width: 30px; height: 30px; border-radius: 50%;
    background: var(--surface2); border: 1px solid var(--border);
    color: var(--muted); font-size: 0.75rem; cursor: pointer;
    display: flex; align-items: center; justify-content: center; transition: all 0.2s;
  }
  .auth-close:hover { background: var(--red); color: white; border-color: var(--red); }
  .auth-box { position: relative; }
  /* gate banner on report form */
  .gate-banner {
    background: rgba(0,229,160,0.07); border: 1px solid rgba(0,229,160,0.2);
    border-radius: 10px; padding: 16px; text-align: center; margin-bottom: 0;
  }
  .gate-banner-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.95rem; margin-bottom: 4px; }
  .gate-banner-sub { font-size: 0.8rem; color: var(--muted); margin-bottom: 12px; }
  .gate-btn { width: 100%; }
  /* user chip in nav */
  .user-chip {
    display: flex; align-items: center; gap: 8px;
    background: var(--surface2); border: 1px solid var(--border);
    border-radius: 100px; padding: 5px 14px 5px 5px;
    font-size: 0.82rem; font-weight: 500;
  }
  .user-avatar {
    width: 26px; height: 26px; border-radius: 50%;
    background: var(--accent); color: #000;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.72rem; font-weight: 700;
  }
  .spinner {
    width: 16px; height: 16px; border: 2px solid rgba(0,0,0,0.3);
    border-top-color: #000; border-radius: 50%;
    animation: spin 0.7s linear infinite;
  }
  @keyframes spin { to { transform: rotate(360deg); } }

</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">Civic<span>Pulse</span></div>
  <ul class="nav-links">
    <li><a href="#" class="active">Issues</a></li>
    <li><a href="#">Map View</a></li>
    <li><a href="#">Analytics</a></li>
    <li><a href="#">Departments</a></li>
  </ul>
  <div class="nav-actions">
    <div id="navAuthArea"><button class="btn btn-ghost" onclick="openAuth('login')">Log In</button></div>
    <button class="btn btn-primary" onclick="requireAuth('report')">+ Report Issue</button>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-badge">
    <div class="badge-dot"></div>
    Live · Bengaluru, KA
  </div>
  <h1>Your city.<br><em>Your voice.</em><br>Real change.</h1>
  <p>Report civic issues, track resolutions, and hold authorities accountable — together. Every submission counts.</p>
  <div class="hero-cta">
    <button class="btn btn-primary btn-large" onclick="requireAuth('report')">📍 Report an Issue</button>
    <button class="btn btn-ghost btn-large" onclick="openMap()">View Live Map →</button>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stats-inner">
    <div class="stat-item">
      <div class="stat-num">2,<span>841</span></div>
      <div class="stat-label">Issues Reported</div>
    </div>
    <div class="stat-item">
      <div class="stat-num"><span>1,</span>209</div>
      <div class="stat-label">Resolved This Month</div>
    </div>
    <div class="stat-item">
      <div class="stat-num"><span>73</span>%</div>
      <div class="stat-label">Resolution Rate</div>
    </div>
    <div class="stat-item">
      <div class="stat-num"><span>8.4</span>k</div>
      <div class="stat-label">Active Citizens</div>
    </div>
  </div>
</div>

<!-- MAIN -->
<div class="main">

  <!-- LEFT: ISSUES -->
  <div>
    <div class="section-header">
      <div class="section-title">Recent Issues</div>
      <div class="filters">
        <button class="filter-btn active" onclick="setFilter(this,'all')">All</button>
        <button class="filter-btn" onclick="setFilter(this,'open')">Open</button>
        <button class="filter-btn" onclick="setFilter(this,'progress')">In Progress</button>
        <button class="filter-btn" onclick="setFilter(this,'resolved')">Resolved</button>
      </div>
    </div>

    <div class="issues-list" id="issuesList"></div>
  </div>

  <!-- RIGHT: SIDEBAR -->
  <div class="sidebar">


    <!-- GATE BANNER (guests) -->
    <div class="sidebar-card" id="gateBanner">
      <div class="sidebar-card-body">
        <div class="gate-banner">
          <div class="gate-banner-title">Want to report an issue?</div>
          <div class="gate-banner-sub">Sign up free to report problems, upvote issues, and track resolutions in your ward.</div>
          <button class="btn btn-primary gate-btn" onclick="openAuth('signup')">Join CivicPulse — It's Free</button>
        </div>
      </div>
    </div>

    <!-- Report Form -->
    <div class="sidebar-card" id="reportForm" style="display:none">
      <div class="sidebar-card-header">📝 Report an Issue</div>
      <div class="sidebar-card-body">
        <div class="form-group">
          <label class="form-label">Category</label>
          <select class="form-select" id="catSelect">
            <option value="">Select category…</option>
            <option>🚧 Roads & Potholes</option>
            <option>💡 Street Lighting</option>
            <option>🗑️ Garbage & Sanitation</option>
            <option>🌊 Water & Drainage</option>
            <option>🌳 Parks & Green Spaces</option>
            <option>🚌 Public Transport</option>
            <option>🏗️ Illegal Construction</option>
            <option>🐕 Stray Animals</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">Issue Title</label>
          <input type="text" class="form-input" id="issueTitle" placeholder="Brief, clear title…">
        </div>
        <div class="form-group">
          <label class="form-label">Description</label>
          <textarea class="form-textarea" id="issueDesc" placeholder="Describe the problem in detail…"></textarea>
        </div>
        <div class="form-group">
          <label class="form-label">Location</label>
          <input type="text" class="form-input" id="issueLocation" placeholder="Area, landmark, or address…">
        </div>
        <div class="form-group">
          <label class="form-label">Photo Evidence</label>
          <div class="upload-zone" onclick="this.querySelector('input').click()">
            <div class="upload-icon">📷</div>
            <div class="upload-text"><strong>Click to upload</strong> or drag & drop</div>
            <input type="file" style="display:none" accept="image/*">
          </div>
        </div>
        <button class="submit-btn" onclick="submitIssue()">Submit Report →</button>
      </div>
    </div>

    <!-- Hot Topics -->
    <div class="sidebar-card">
      <div class="sidebar-card-header">🔥 Trending Issues</div>
      <div class="sidebar-card-body">
        <div class="tags-cloud">
          <span class="hot-tag">Potholes<span class="count">234</span></span>
          <span class="hot-tag">Waterlogging<span class="count">189</span></span>
          <span class="hot-tag">Streetlight<span class="count">142</span></span>
          <span class="hot-tag">Garbage<span class="count">128</span></span>
          <span class="hot-tag">Encroachment<span class="count">97</span></span>
          <span class="hot-tag">Drainage<span class="count">85</span></span>
          <span class="hot-tag">Footpath<span class="count">74</span></span>
          <span class="hot-tag">Park Upkeep<span class="count">61</span></span>
        </div>
      </div>
    </div>

    <!-- Leaderboard -->
    <div class="sidebar-card">
      <div class="sidebar-card-header">🏆 Top Contributors</div>
      <div class="sidebar-card-body" style="padding:16px 20px">
        <div id="leaderboard"></div>
      </div>
    </div>

  </div>
</div>

<!-- MAP MODAL -->
<div class="map-modal" id="mapModal" onclick="closeMapOnBg(event)">
  <div class="map-container">
    <div class="map-modal-header">
      <div>
        <div class="map-modal-title">Live Issue Map</div>
        <div class="map-modal-sub">Bengaluru &middot; <span>6</span> active issues</div>
      </div>
      <div style="display:flex;gap:10px;align-items:center">
        <div class="map-legend">
          <span class="legend-dot" style="background:#ff4757"></span>Open
          <span class="legend-dot" style="background:#ffd32a;margin-left:10px"></span>In Progress
          <span class="legend-dot" style="background:#00e5a0;margin-left:10px"></span>Resolved
        </div>
        <button class="map-close" onclick="closeMap()">&#x2715;</button>
      </div>
    </div>
    <div class="map-body">
      <div class="map-svg-wrap">
        <svg viewBox="0 0 700 520" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:100%">
          <rect width="700" height="520" fill="#0d1422"/>
          <g stroke="rgba(255,255,255,0.04)" stroke-width="1">
            <line x1="0" y1="65" x2="700" y2="65"/><line x1="0" y1="130" x2="700" y2="130"/>
            <line x1="0" y1="195" x2="700" y2="195"/><line x1="0" y1="260" x2="700" y2="260"/>
            <line x1="0" y1="325" x2="700" y2="325"/><line x1="0" y1="390" x2="700" y2="390"/>
            <line x1="0" y1="455" x2="700" y2="455"/>
            <line x1="100" y1="0" x2="100" y2="520"/><line x1="200" y1="0" x2="200" y2="520"/>
            <line x1="300" y1="0" x2="300" y2="520"/><line x1="400" y1="0" x2="400" y2="520"/>
            <line x1="500" y1="0" x2="500" y2="520"/><line x1="600" y1="0" x2="600" y2="520"/>
          </g>
          <path d="M120,60 L200,40 L320,30 L450,45 L560,70 L620,140 L640,240 L620,340 L580,420 L490,470 L370,490 L250,480 L150,450 L90,380 L70,280 L80,170 Z" fill="rgba(79,139,255,0.05)" stroke="rgba(79,139,255,0.15)" stroke-width="1.5"/>
          <g stroke="rgba(255,255,255,0.12)" stroke-width="2.5" fill="none">
            <ellipse cx="350" cy="260" rx="220" ry="190" stroke="rgba(79,139,255,0.25)" stroke-width="1.5" stroke-dasharray="6,4"/>
            <line x1="150" y1="240" x2="540" y2="240"/>
            <line x1="350" y1="240" x2="540" y2="420"/>
            <line x1="350" y1="240" x2="140" y2="100"/>
            <line x1="350" y1="240" x2="320" y2="460"/>
            <line x1="350" y1="240" x2="380" y2="60"/>
            <line x1="350" y1="240" x2="560" y2="130"/>
            <line x1="350" y1="240" x2="100" y2="290"/>
          </g>
          <g stroke="rgba(255,255,255,0.06)" stroke-width="1.2">
            <line x1="200" y1="150" x2="500" y2="150"/><line x1="200" y1="340" x2="500" y2="340"/>
            <line x1="200" y1="150" x2="200" y2="380"/><line x1="480" y1="150" x2="480" y2="360"/>
            <line x1="160" y1="200" x2="540" y2="200"/><line x1="160" y1="290" x2="540" y2="290"/>
          </g>
          <ellipse cx="310" cy="320" rx="28" ry="22" fill="rgba(0,229,160,0.12)" stroke="rgba(0,229,160,0.3)" stroke-width="1"/>
          <text x="310" y="324" text-anchor="middle" font-size="7" fill="rgba(0,229,160,0.6)" font-family="DM Sans,sans-serif">Lalbagh</text>
          <ellipse cx="390" cy="225" rx="22" ry="16" fill="rgba(0,229,160,0.1)" stroke="rgba(0,229,160,0.25)" stroke-width="1"/>
          <text x="390" y="228" text-anchor="middle" font-size="7" fill="rgba(0,229,160,0.5)" font-family="DM Sans,sans-serif">Cubbon</text>
          <ellipse cx="530" cy="310" rx="30" ry="16" fill="rgba(79,139,255,0.12)" stroke="rgba(79,139,255,0.25)" stroke-width="1"/>
          <text x="530" y="313" text-anchor="middle" font-size="7" fill="rgba(79,139,255,0.5)" font-family="DM Sans,sans-serif">Bellandur</text>
          <g font-family="DM Sans,sans-serif" fill="rgba(255,255,255,0.2)" font-size="9.5" font-weight="500">
            <text x="430" y="185">Indiranagar</text>
            <text x="155" y="165">Rajajinagar</text>
            <text x="410" y="330">Koramangala</text>
            <text x="255" y="400">JP Nagar</text>
            <text x="165" y="240">Malleswaram</text>
            <text x="330" y="165">Sadashivnagar</text>
            <text x="460" y="255">HAL</text>
            <text x="130" y="310">Vijayanagar</text>
            <text x="375" y="435">BTM Layout</text>
          </g>
          <circle cx="350" cy="240" r="4" fill="rgba(255,255,255,0.3)"/>
          <text x="358" y="244" font-size="8" fill="rgba(255,255,255,0.4)" font-family="DM Sans,sans-serif">City Centre</text>
          <!-- Issue Pins -->
          <g class="mpin" onclick="showPinInfo(0)" style="cursor:pointer" id="pin0">
            <circle cx="455" cy="198" r="16" fill="rgba(255,71,87,0.18)"><animate attributeName="r" values="12;18;12" dur="2s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0.1;0.6" dur="2s" repeatCount="indefinite"/></circle>
            <circle cx="455" cy="198" r="9" fill="#ff4757" stroke="#fff" stroke-width="1.5"/>
            <text x="455" y="202" text-anchor="middle" font-size="10" fill="white" font-weight="bold">!</text>
          </g>
          <g class="mpin" onclick="showPinInfo(1)" style="cursor:pointer" id="pin1">
            <circle cx="195" cy="178" r="16" fill="rgba(255,211,42,0.15)"><animate attributeName="r" values="12;18;12" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0.1;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
            <circle cx="195" cy="178" r="9" fill="#ffd32a" stroke="#fff" stroke-width="1.5"/>
            <text x="195" y="182" text-anchor="middle" font-size="10" fill="#000" font-weight="bold">~</text>
          </g>
          <g class="mpin" onclick="showPinInfo(2)" style="cursor:pointer" id="pin2">
            <circle cx="435" cy="322" r="16" fill="rgba(255,71,87,0.18)"><animate attributeName="r" values="12;18;12" dur="1.8s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0.1;0.6" dur="1.8s" repeatCount="indefinite"/></circle>
            <circle cx="435" cy="322" r="9" fill="#ff4757" stroke="#fff" stroke-width="1.5"/>
            <text x="435" y="326" text-anchor="middle" font-size="10" fill="white" font-weight="bold">!</text>
          </g>
          <g class="mpin" onclick="showPinInfo(3)" style="cursor:pointer" id="pin3">
            <circle cx="295" cy="390" r="9" fill="#00e5a0" stroke="#fff" stroke-width="1.5"/>
            <text x="295" y="394" text-anchor="middle" font-size="10" fill="#000" font-weight="bold">&#x2713;</text>
          </g>
          <g class="mpin" onclick="showPinInfo(4)" style="cursor:pointer" id="pin4">
            <circle cx="210" cy="248" r="16" fill="rgba(255,107,53,0.18)"><animate attributeName="r" values="12;18;12" dur="2.2s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0.1;0.6" dur="2.2s" repeatCount="indefinite"/></circle>
            <circle cx="210" cy="248" r="9" fill="#ff6b35" stroke="#fff" stroke-width="1.5"/>
            <text x="210" y="252" text-anchor="middle" font-size="10" fill="white" font-weight="bold">!</text>
          </g>
          <g class="mpin" onclick="showPinInfo(5)" style="cursor:pointer" id="pin5">
            <circle cx="308" cy="335" r="16" fill="rgba(255,211,42,0.15)"><animate attributeName="r" values="12;18;12" dur="3s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0.1;0.6" dur="3s" repeatCount="indefinite"/></circle>
            <circle cx="308" cy="335" r="9" fill="#ffd32a" stroke="#fff" stroke-width="1.5"/>
            <text x="308" y="339" text-anchor="middle" font-size="10" fill="#000" font-weight="bold">~</text>
          </g>
        </svg>
        <div class="pin-tooltip" id="pinTooltip">
          <div class="pin-tooltip-cat" id="ptCat"></div>
          <div class="pin-tooltip-title" id="ptTitle"></div>
          <div class="pin-tooltip-loc" id="ptLoc"></div>
          <div class="pin-tooltip-footer">
            <span id="ptStatus"></span>
            <span class="pin-votes" id="ptVotes"></span>
          </div>
        </div>
      </div>
      <div class="map-side">
        <div class="map-side-title">Issues on Map</div>
        <div id="mapIssueList"></div>
      </div>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast">
  <div class="toast-icon" id="toastIcon">✅</div>
  <div class="toast-text">
    <div class="toast-title" id="toastTitle">Issue Submitted!</div>
    <div class="toast-sub" id="toastSub">Ref #CP-2845 · Authorities notified</div>
  </div>
</div>

<script>
const issues = [
  {
    id: 1,
    title: "Massive pothole on 100 Feet Road near CMH Hospital",
    desc: "A 2-foot wide pothole has appeared after last week's rain. Three motorcycles have already been damaged. Needs urgent attention.",
    category: "Roads", catColor: "#ff6b35", catBg: "rgba(255,107,53,0.12)",
    status: "open", statusLabel: "Open",
    location: "Indiranagar, Ward 81",
    votes: 142, comments: 23,
    priority: "critical", priorityLabel: "CRIT",
    time: "2h ago",
    cardAccent: "#ff4757"
  },
  {
    id: 2,
    title: "Street lights non-functional for 3 weeks on 12th Cross",
    desc: "Entire stretch of 12th Cross near Rajajinagar market has been dark at night. Women feel unsafe walking after 7 PM.",
    category: "Lighting", catColor: "#ffd32a", catBg: "rgba(255,211,42,0.1)",
    status: "progress", statusLabel: "In Progress",
    location: "Rajajinagar, Ward 34",
    votes: 89, comments: 14,
    priority: "high", priorityLabel: "HIGH",
    time: "5h ago",
    cardAccent: "#ffd32a"
  },
  {
    id: 3,
    title: "Overflowing garbage bins at Koramangala BDA Complex",
    desc: "Garbage bins haven't been cleared for 5 days. The stench is unbearable and attracting stray dogs. Children's park nearby is unusable.",
    category: "Sanitation", catColor: "#00e5a0", catBg: "rgba(0,229,160,0.1)",
    status: "open", statusLabel: "Open",
    location: "Koramangala, Ward 68",
    votes: 67, comments: 11,
    priority: "high", priorityLabel: "HIGH",
    time: "8h ago",
    cardAccent: "#00e5a0"
  },
  {
    id: 4,
    title: "Stormwater drain blocked causing flooding in rainy season",
    desc: "The stormwater drain on 3rd Main has been blocked with silt and debris. Last monsoon, 6 houses were flooded.",
    category: "Drainage", catColor: "#4f8bff", catBg: "rgba(79,139,255,0.1)",
    status: "resolved", statusLabel: "Resolved",
    location: "JP Nagar, Ward 176",
    votes: 211, comments: 42,
    priority: "medium", priorityLabel: "MED",
    time: "2d ago",
    cardAccent: "#4f8bff"
  },
  {
    id: 5,
    title: "Encroachment on footpath by commercial vendor",
    desc: "A permanent structure has been built on the public footpath forcing pedestrians to walk on the road. Children and elderly are at risk.",
    category: "Roads", catColor: "#ff6b35", catBg: "rgba(255,107,53,0.12)",
    status: "open", statusLabel: "Open",
    location: "Malleswaram, Ward 9",
    votes: 45, comments: 7,
    priority: "medium", priorityLabel: "MED",
    time: "1d ago",
    cardAccent: "#ff6b35"
  },
  {
    id: 6,
    title: "Park benches broken, safety hazard for children",
    desc: "All 4 benches at Lalbagh East Gate park are broken with exposed metal rods. A child was injured last week.",
    category: "Parks", catColor: "#00e5a0", catBg: "rgba(0,229,160,0.1)",
    status: "progress", statusLabel: "In Progress",
    location: "Mavalli, Ward 162",
    votes: 38, comments: 5,
    priority: "low", priorityLabel: "LOW",
    time: "3d ago",
    cardAccent: "#00e5a0"
  }
];

const leaderboardData = [
  { name: "Priya Nair", pts: "148 pts", score: 148, initials: "PN", color: "#ff6b35" },
  { name: "Kiran Rao", pts: "134 pts", score: 134, initials: "KR", color: "#4f8bff" },
  { name: "Ananya M.", pts: "119 pts", score: 119, initials: "AM", color: "#ffd32a" },
  { name: "Vikram S.", pts: "97 pts", score: 97, initials: "VS", color: "#00e5a0" },
  { name: "Deepa K.", pts: "84 pts", score: 84, initials: "DK", color: "#ff4757" }
];

let currentFilter = 'all';
let votedIds = new Set();

function renderIssues() {
  const list = document.getElementById('issuesList');
  let filtered = issues;
  if (currentFilter !== 'all') {
    const map = { open: 'open', progress: 'progress', resolved: 'resolved' };
    filtered = issues.filter(i => i.status === map[currentFilter]);
  }
  list.innerHTML = filtered.map((issue, idx) => `
    <div class="issue-card" style="--card-accent: ${issue.cardAccent}; animation-delay: ${idx * 0.07}s">
      <div class="issue-top">
        <div>
          <div class="issue-meta" style="margin-bottom:10px">
            <span class="category-tag" style="color:${issue.catColor}; background:${issue.catBg}">${issue.category}</span>
            <span class="status-badge status-${issue.status}">${issue.statusLabel}</span>
          </div>
          <div class="issue-title">${issue.title}</div>
        </div>
        <div class="priority-ring priority-${issue.priority}">${issue.priorityLabel}</div>
      </div>
      <div class="issue-desc">${issue.desc}</div>
      <div class="issue-footer">
        <div class="issue-location">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/>
          </svg>
          ${issue.location}
        </div>
        <div class="issue-actions">
          <button class="vote-btn ${votedIds.has(issue.id) ? 'voted' : ''}" onclick="requireAuth('vote', event, ${issue.id})">
            <svg width="12" height="12" viewBox="0 0 24 24" fill="${votedIds.has(issue.id) ? 'currentColor' : 'none'}" stroke="currentColor" stroke-width="2">
              <path d="M14 9V5a3 3 0 00-3-3l-4 9v11h11.28a2 2 0 002-1.7l1.38-9a2 2 0 00-2-2.3H14z"/>
              <path d="M7 22H4a2 2 0 01-2-2v-7a2 2 0 012-2h3"/>
            </svg>
            <span id="votes-${issue.id}">${issue.votes}</span>
          </button>
          <div class="comment-count">
            <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/>
            </svg>
            ${issue.comments}
          </div>
          <span class="issue-time">${issue.time}</span>
        </div>
      </div>
    </div>
  `).join('');
}

function renderLeaderboard() {
  const lb = document.getElementById('leaderboard');
  const rankClasses = ['gold', 'silver', 'bronze', '', ''];
  lb.innerHTML = leaderboardData.map((u, i) => `
    <div class="leaderboard-item">
      <div class="lb-rank ${rankClasses[i]}">${i === 0 ? '🥇' : i === 1 ? '🥈' : i === 2 ? '🥉' : i+1}</div>
      <div class="lb-avatar" style="color:${u.color}; border-color:${u.color}30">${u.initials}</div>
      <div class="lb-info">
        <div class="lb-name">${u.name}</div>
        <div class="lb-pts">${u.pts}</div>
      </div>
      <div class="lb-score">${u.score}</div>
    </div>
  `).join('');
}

function setFilter(btn, filter) {
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  currentFilter = filter;
  renderIssues();
}

function vote(e, id) {
  e.stopPropagation();
  const issue = issues.find(i => i.id === id);
  const el = document.getElementById('votes-' + id);
  if (votedIds.has(id)) {
    votedIds.delete(id);
    issue.votes--;
    showToast('👍', 'Vote Removed', 'Your upvote has been withdrawn');
  } else {
    votedIds.add(id);
    issue.votes++;
    showToast('⬆️', 'Upvoted!', 'Thanks for highlighting this issue');
  }
  el.textContent = issue.votes;
  e.currentTarget.classList.toggle('voted');
  const svg = e.currentTarget.querySelector('svg');
  svg.setAttribute('fill', votedIds.has(id) ? 'currentColor' : 'none');
}

function submitIssue() {
  const title = document.getElementById('issueTitle').value.trim();
  const loc = document.getElementById('issueLocation').value.trim();
  const cat = document.getElementById('catSelect').value;

  if (!title || !loc || !cat) {
    showToast('⚠️', 'Missing Fields', 'Please fill in category, title, and location');
    return;
  }

  const refNum = 'CP-' + (2800 + Math.floor(Math.random()*100));
  showToast('✅', 'Issue Submitted!', `Ref #${refNum} · Authorities notified`);

  // Reset
  document.getElementById('issueTitle').value = '';
  document.getElementById('issueDesc').value = '';
  document.getElementById('issueLocation').value = '';
  document.getElementById('catSelect').value = '';
}

function scrollToForm() {
  document.getElementById('reportForm').scrollIntoView({ behavior: 'smooth', block: 'center' });
}

function showToast(icon, title, sub) {
  const t = document.getElementById('toast');
  document.getElementById('toastIcon').textContent = icon;
  document.getElementById('toastTitle').textContent = title;
  document.getElementById('toastSub').textContent = sub;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3500);
}

renderIssues();
renderLeaderboard();

function openMap() {
  document.getElementById('mapModal').classList.add('open');
  renderMapList();
}
function closeMap() {
  document.getElementById('mapModal').classList.remove('open');
  document.getElementById('pinTooltip').classList.remove('visible');
}
function closeMapOnBg(e) {
  if (e.target === document.getElementById('mapModal')) closeMap();
}

const pinData = [
  { idx:0, title:"Massive pothole on 100 Feet Road", category:"Roads", location:"Indiranagar, Ward 81", status:"Open", statusClass:"status-open", votes:142, accent:"#ff4757" },
  { idx:1, title:"Street lights non-functional on 12th Cross", category:"Lighting", location:"Rajajinagar, Ward 34", status:"In Progress", statusClass:"status-progress", votes:89, accent:"#ffd32a" },
  { idx:2, title:"Overflowing garbage bins at BDA Complex", category:"Sanitation", location:"Koramangala, Ward 68", status:"Open", statusClass:"status-open", votes:67, accent:"#ff4757" },
  { idx:3, title:"Stormwater drain blocking causing flooding", category:"Drainage", location:"JP Nagar, Ward 176", status:"Resolved", statusClass:"status-resolved", votes:211, accent:"#00e5a0" },
  { idx:4, title:"Encroachment on footpath by vendor", category:"Roads", location:"Malleswaram, Ward 9", status:"Open", statusClass:"status-open", votes:45, accent:"#ff6b35" },
  { idx:5, title:"Park benches broken near Lalbagh", category:"Parks", location:"Mavalli, Ward 162", status:"In Progress", statusClass:"status-progress", votes:38, accent:"#ffd32a" }
];

function showPinInfo(idx) {
  const p = pinData[idx];
  document.getElementById('ptCat').textContent = p.category;
  document.getElementById('ptTitle').textContent = p.title;
  document.getElementById('ptLoc').textContent = '📍 ' + p.location;
  const st = document.getElementById('ptStatus');
  st.className = 'status-badge ' + p.statusClass;
  st.textContent = p.status;
  document.getElementById('ptVotes').textContent = '▲ ' + p.votes + ' votes';
  document.getElementById('pinTooltip').classList.add('visible');
}

function renderMapList() {
  const el = document.getElementById('mapIssueList');
  el.innerHTML = pinData.map(p => `
    <div class="map-issue-item" style="--item-accent:${p.accent}" onclick="showPinInfo(${p.idx})">
      <div class="map-issue-item-title">${p.title}</div>
      <div class="map-issue-item-meta">
        <span>${p.location.split(',')[0]}</span>
        <span class="status-badge ${p.statusClass}">${p.status}</span>
      </div>
    </div>
  `).join('');
}


// ═══════════════════════════════════════════════
// FIREBASE + AUTH
// ═══════════════════════════════════════════════
// NOTE: Replace this config with your own from Firebase Console
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};

// Dynamically load Firebase SDK
(function loadFirebase() {
  const sdks = [
    'https://www.gstatic.com/firebasejs/10.12.0/firebase-app-compat.js',
    'https://www.gstatic.com/firebasejs/10.12.0/firebase-auth-compat.js',
    'https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore-compat.js',
    'https://www.gstatic.com/firebasejs/10.12.0/firebase-storage-compat.js'
  ];
  let loaded = 0;
  sdks.forEach(src => {
    const s = document.createElement('script');
    s.src = src;
    s.onload = () => { if (++loaded === sdks.length) initFirebase(); };
    document.head.appendChild(s);
  });
})();

let db, auth, storage, currentUser = null;

function initFirebase() {
  if (!firebase.apps.length) firebase.initializeApp(firebaseConfig);
  db      = firebase.firestore();
  auth    = firebase.auth();
  storage = firebase.storage();

  auth.onAuthStateChanged(user => {
    currentUser = user;
    updateNavForUser(user);
    if (user) {
      document.getElementById('gateBanner').style.display = 'none';
      document.getElementById('reportForm').style.display = 'block';
      loadIssuesFromFirestore();
    } else {
      document.getElementById('gateBanner').style.display = 'block';
      document.getElementById('reportForm').style.display = 'none';
    }
  });
}

function updateNavForUser(user) {
  const area = document.getElementById('navAuthArea');
  if (user) {
    const initials = (user.displayName || user.email || 'U').slice(0,2).toUpperCase();
    area.innerHTML = `
      <div class="user-chip">
        <div class="user-avatar">${initials}</div>
        <span>${user.displayName || user.email.split('@')[0]}</span>
        <button onclick="handleLogout()" style="background:none;border:none;color:var(--muted);cursor:pointer;font-size:0.75rem;margin-left:4px;">✕</button>
      </div>`;
  } else {
    area.innerHTML = `<button class="btn btn-ghost" onclick="openAuth('login')">Log In</button>`;
  }
}

// ── Auth modal controls ──────────────────────────────────────────────────────
let pendingAction = null;

function openAuth(tab = 'signup', action = null) {
  pendingAction = action;
  switchTab(tab);
  document.getElementById('authOverlay').classList.add('open');
}
function closeAuth() {
  document.getElementById('authOverlay').classList.remove('open');
  clearAuthErrors();
}
function closeAuthOnBg(e) {
  if (e.target === document.getElementById('authOverlay')) closeAuth();
}
function switchTab(tab) {
  document.querySelectorAll('.auth-tab').forEach((t,i) =>
    t.classList.toggle('active', (i===0 && tab==='signup') || (i===1 && tab==='login'))
  );
  document.getElementById('formSignup').classList.toggle('active', tab==='signup');
  document.getElementById('formLogin').classList.toggle('active', tab==='login');
  clearAuthErrors();
}
function clearAuthErrors() {
  ['su-error','li-error'].forEach(id => {
    const el = document.getElementById(id);
    if (el) { el.classList.remove('show'); el.textContent = ''; }
  });
}
function showError(id, msg) {
  const el = document.getElementById(id);
  if (el) { el.textContent = msg; el.classList.add('show'); }
}
function setLoading(btnId, loading) {
  const btn = document.getElementById(btnId);
  if (!btn) return;
  btn.disabled = loading;
  btn.innerHTML = loading
    ? '<div class="spinner"></div>'
    : btnId === 'su-btn' ? '<span>Create Account</span>' : '<span>Log In</span>';
}

async function handleSignup() {
  const name  = document.getElementById('su-name').value.trim();
  const ward  = document.getElementById('su-ward').value;
  const email = document.getElementById('su-email').value.trim();
  const pass  = document.getElementById('su-pass').value;
  if (!name || !ward || !email || !pass) return showError('su-error','Please fill in all fields.');
  if (pass.length < 6) return showError('su-error','Password must be at least 6 characters.');
  setLoading('su-btn', true);
  try {
    const cred = await auth.createUserWithEmailAndPassword(email, pass);
    await cred.user.updateProfile({ displayName: name });
    await db.collection('users').doc(cred.user.uid).set({
      name, ward, email, createdAt: firebase.firestore.FieldValue.serverTimestamp(), points: 0
    });
    closeAuth();
    showToast('🎉', 'Welcome to CivicPulse!', `Hey ${name}, your account is ready.`);
    if (pendingAction === 'report') scrollToForm();
  } catch(e) {
    showError('su-error', friendlyError(e.code));
  }
  setLoading('su-btn', false);
}

async function handleLogin() {
  const email = document.getElementById('li-email').value.trim();
  const pass  = document.getElementById('li-pass').value;
  if (!email || !pass) return showError('li-error','Please enter email and password.');
  setLoading('li-btn', true);
  try {
    await auth.signInWithEmailAndPassword(email, pass);
    closeAuth();
    showToast('👋', 'Welcome back!', 'You are now logged in.');
    if (pendingAction === 'report') scrollToForm();
  } catch(e) {
    showError('li-error', friendlyError(e.code));
  }
  setLoading('li-btn', false);
}

async function handleLogout() {
  await auth.signOut();
  showToast('👋', 'Logged out', 'See you next time!');
}

function friendlyError(code) {
  const map = {
    'auth/email-already-in-use': 'This email is already registered.',
    'auth/invalid-email': 'Please enter a valid email address.',
    'auth/weak-password': 'Password must be at least 6 characters.',
    'auth/user-not-found': 'No account found with this email.',
    'auth/wrong-password': 'Incorrect password. Please try again.',
    'auth/too-many-requests': 'Too many attempts. Please try again later.',
    'auth/network-request-failed': 'Network error. Check your connection.'
  };
  return map[code] || 'Something went wrong. Please try again.';
}

// ── Gate helper ──────────────────────────────────────────────────────────────
function requireAuth(action, event, id) {
  if (!currentUser) {
    if (event) event.stopPropagation();
    openAuth('signup', action);
    return false;
  }
  if (action === 'report') scrollToForm();
  if (action === 'vote' && id !== undefined) vote(event, id);
  return true;
}

// ── Firestore: load issues ───────────────────────────────────────────────────
async function loadIssuesFromFirestore() {
  if (!db) return;
  try {
    const snap = await db.collection('issues').orderBy('createdAt','desc').limit(20).get();
    if (!snap.empty) {
      snap.forEach(doc => {
        const d = doc.data();
        if (!issues.find(i => i.id === doc.id)) {
          issues.unshift({
            id: doc.id, title: d.title, desc: d.description,
            category: d.category, catColor: '#00e5a0', catBg: 'rgba(0,229,160,0.1)',
            status: d.status || 'open', statusLabel: d.status === 'open' ? 'Open' : d.status === 'progress' ? 'In Progress' : 'Resolved',
            location: d.location, votes: d.votes || 0, comments: 0,
            priority: 'medium', priorityLabel: 'MED', time: 'just now', cardAccent: '#00e5a0'
          });
        }
      });
      renderIssues();
    }
  } catch(e) { console.warn('Firestore load:', e.message); }
}

// ── Firestore: save issue ─────────────────────────────────────────────────────
async function saveIssueToFirestore(issueData) {
  if (!db || !currentUser) return null;
  try {
    const ref = await db.collection('issues').add({
      ...issueData,
      uid: currentUser.uid,
      authorName: currentUser.displayName || 'Anonymous',
      votes: 0, status: 'open',
      createdAt: firebase.firestore.FieldValue.serverTimestamp()
    });
    return ref.id;
  } catch(e) { console.warn('Firestore save:', e.message); return null; }
}

// ── Override submitIssue to use Firestore + Storage ──────────────────────────
const _origSubmit = submitIssue;
submitIssue = async function() {
  if (!currentUser) { openAuth('signup', 'report'); return; }
  const title    = document.getElementById('issueTitle').value.trim();
  const desc     = document.getElementById('issueDesc').value.trim();
  const loc      = document.getElementById('issueLocation').value.trim();
  const cat      = document.getElementById('catSelect').value;
  const fileInput = document.querySelector('.upload-zone input[type=file]');
  const file      = fileInput && fileInput.files[0];

  if (!title || !loc || !cat) {
    showToast('⚠️', 'Missing Fields', 'Please fill in category, title, and location');
    return;
  }

  const btn = document.querySelector('.submit-btn');
  btn.disabled = true; btn.textContent = 'Submitting…';

  let photoURL = null;
  if (file && storage) {
    try {
      const ref = storage.ref('issues/' + Date.now() + '_' + file.name);
      await ref.put(file);
      photoURL = await ref.getDownloadURL();
    } catch(e) { console.warn('Storage upload:', e.message); }
  }

  const docId = await saveIssueToFirestore({ title, description: desc, location: loc, category: cat, photoURL });
  const refNum = docId ? docId.slice(0,8).toUpperCase() : 'CP-' + Math.floor(Math.random()*9000+1000);

  showToast('✅', 'Issue Submitted!', 'Ref #' + refNum + ' · Authorities notified');

  document.getElementById('issueTitle').value = '';
  document.getElementById('issueDesc').value  = '';
  document.getElementById('issueLocation').value = '';
  document.getElementById('catSelect').value  = '';
  if (fileInput) fileInput.value = '';

  btn.disabled = false; btn.textContent = 'Submit Report →';
};

</script>

<!-- AUTH MODAL -->
<div class="auth-overlay" id="authOverlay" onclick="closeAuthOnBg(event)">
  <div class="auth-box">
    <button class="auth-close" onclick="closeAuth()">&#x2715;</button>
    <div class="auth-top">
      <div class="auth-icon">🏙️</div>
      <div class="auth-title">Join CivicPulse</div>
      <div class="auth-sub">Create an account to report issues,<br>vote, and make your city better.</div>
    </div>
    <div class="auth-body">
      <div class="auth-tabs">
        <button class="auth-tab active" onclick="switchTab('signup')">Sign Up</button>
        <button class="auth-tab" onclick="switchTab('login')">Log In</button>
      </div>

      <!-- SIGN UP -->
      <div class="auth-form active" id="formSignup">
        <div class="auth-row">
          <div class="auth-input-wrap">
            <span class="auth-input-icon">👤</span>
            <input class="auth-input" id="su-name" type="text" placeholder="Full name">
          </div>
          <div class="auth-input-wrap">
            <span class="auth-input-icon">📍</span>
            <select class="auth-input ward-select" id="su-ward">
              <option value="">Select ward…</option>
              <option>Indiranagar</option><option>Koramangala</option>
              <option>Malleswaram</option><option>Rajajinagar</option>
              <option>JP Nagar</option><option>Jayanagar</option>
              <option>Whitefield</option><option>Electronic City</option>
              <option>Hebbal</option><option>Yelahanka</option>
              <option>BTM Layout</option><option>Marathahalli</option>
            </select>
          </div>
        </div>
        <div class="auth-input-wrap">
          <span class="auth-input-icon">✉️</span>
          <input class="auth-input" id="su-email" type="email" placeholder="Email address">
        </div>
        <div class="auth-input-wrap">
          <span class="auth-input-icon">🔒</span>
          <input class="auth-input" id="su-pass" type="password" placeholder="Password (min 6 chars)">
        </div>
        <div class="auth-error" id="su-error"></div>
        <button class="auth-btn" id="su-btn" onclick="handleSignup()">
          <span>Create Account</span>
        </button>
      </div>

      <!-- LOG IN -->
      <div class="auth-form" id="formLogin">
        <div class="auth-input-wrap">
          <span class="auth-input-icon">✉️</span>
          <input class="auth-input" id="li-email" type="email" placeholder="Email address">
        </div>
        <div class="auth-input-wrap">
          <span class="auth-input-icon">🔒</span>
          <input class="auth-input" id="li-pass" type="password" placeholder="Password">
        </div>
        <div class="auth-error" id="li-error"></div>
        <button class="auth-btn" id="li-btn" onclick="handleLogin()">
          <span>Log In</span>
        </button>
      </div>
    </div>
  </div>
</div>

</body>
</html>
