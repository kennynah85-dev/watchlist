<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Deal Dough — Live Watchlist · R/R Score · Deep Dive</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=IBM+Plex+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&family=IBM+Plex+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
/* ── CSS VARIABLES — Light & Dark ── */
:root {
  --bg:        #ffffff;
  --bg2:       #f7f7f5;
  --bg3:       #f0f0ed;
  --border:    #e4e4e0;
  --border2:   #d0d0cb;
  --text:      #111111;
  --text2:     #444444;
  --text3:     #888888;
  --text4:     #bbbbbb;
  --accent:    #1a56db;
  --accent-bg: #e8f0fe;
  --accent-bd: #c5d5f8;
  --sbar-bg:   #f0f8f4;
  --sbar-bd:   #cce8d8;
  --th-bg:     #f5f5f3;
  --th-hov:    #eae9e7;
  --tr-hov:    #fafaf9;
  --pos:       #0a7f4f;
  --neg:       #c0392b;
  --dd-bg:     #fafaf8;
  --dd-bd:     #e8e8e4;
  --mono:      'IBM Plex Mono', 'Consolas', monospace;
  --sans:      'IBM Plex Sans', system-ui, sans-serif;
  --serif:     'Instrument Serif', Georgia, serif;
}
[data-theme="dark"] {
  --bg:        #0e0e10;
  --bg2:       #161618;
  --bg3:       #1e1e21;
  --border:    #2a2a2f;
  --border2:   #38383f;
  --text:      #f0f0ee;
  --text2:     #b8b8b4;
  --text3:     #6a6a68;
  --text4:     #3a3a38;
  --accent:    #4d7fff;
  --accent-bg: #1a2340;
  --accent-bd: #2d4070;
  --sbar-bg:   #0f1f18;
  --sbar-bd:   #1a3828;
  --th-bg:     #161618;
  --th-hov:    #1e1e22;
  --tr-hov:    #14141a;
  --pos:       #22c55e;
  --neg:       #f87171;
  --dd-bg:     #131315;
  --dd-bd:     #2a2a2f;
}

*{box-sizing:border-box;margin:0;padding:0}
body{font-family:var(--sans);background:var(--bg);color:var(--text);font-size:12px;padding:.6rem;transition:background .2s,color .2s}
/* ── Wordmark header ── */
#wordmark{display:flex;align-items:center;gap:12px;padding:8px 2px 10px;margin-bottom:8px;border-bottom:1px solid var(--border)}
#wordmark .wm-name{font-family:var(--serif);font-size:20px;font-weight:400;font-style:italic;color:var(--text);letter-spacing:-.01em;line-height:1.1}
#wordmark .wm-tag{font-family:var(--mono);font-size:9px;font-weight:400;color:var(--text3);letter-spacing:.1em;text-transform:uppercase}
#sbar{display:flex;gap:10px;align-items:center;flex-wrap:wrap;padding:6px 10px;background:var(--sbar-bg);border:1px solid var(--sbar-bd);border-radius:4px;margin-bottom:7px;font-size:11px;font-family:var(--sans);letter-spacing:.01em}
.dot{width:7px;height:7px;border-radius:50%;background:var(--border2);display:inline-block;margin-right:3px;flex-shrink:0}
.dot.live{background:#22c55e;animation:blink 2s infinite}
.dot.loading{background:#f59e0b;animation:blink .8s infinite}
.dot.error{background:#ef4444}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
.rbtn{font-size:11px;padding:3px 10px;background:var(--accent-bg);border:1px solid var(--accent-bd);border-radius:3px;color:var(--accent);cursor:pointer;font-family:var(--sans);font-weight:500;letter-spacing:.02em}
.rbtn:hover{opacity:.8}

/* ── Dark mode toggle ── */
#dm-toggle{display:flex;align-items:center;gap:6px;cursor:pointer;user-select:none;margin-left:auto;font-size:11px;color:var(--text3);font-family:var(--sans)}
#dm-toggle .dm-track{width:28px;height:15px;border-radius:8px;background:var(--border2);border:1px solid var(--border);position:relative;transition:background .2s}
#dm-toggle .dm-thumb{width:11px;height:11px;border-radius:50%;background:var(--text3);position:absolute;top:1px;left:1px;transition:transform .2s,background .2s}
[data-theme="dark"] #dm-toggle .dm-track{background:var(--accent)}
[data-theme="dark"] #dm-toggle .dm-thumb{transform:translateX(13px);background:#fff}

/* ── Controls ── */
#ctrl{display:flex;gap:6px;align-items:center;flex-wrap:wrap;margin-bottom:7px}
#srch{font-size:12px;padding:4px 8px;border:1px solid var(--border);border-radius:3px;width:190px;outline:none;background:var(--bg2);color:var(--text);font-family:var(--sans)}
#srch:focus{border-color:var(--accent)}
#rcnt{font-size:11px;color:var(--text3);white-space:nowrap;font-variant-numeric:tabular-nums;font-family:var(--mono)}
#fbars{display:flex;gap:4px;flex-wrap:wrap}
.fbtn{font-size:10px;padding:2px 9px;border:1px solid var(--border);border-radius:2px;background:var(--bg);color:var(--text2);cursor:pointer;white-space:nowrap;transition:background .12s,color .12s;font-family:var(--sans);font-weight:500;letter-spacing:.03em;text-transform:uppercase}
.fbtn:hover{background:var(--bg3)}
.fbtn.active{background:var(--text);color:var(--bg);border-color:var(--text)}

/* ── Add ticker panel ── */
#add-panel{margin-bottom:8px;padding:10px 12px;background:var(--bg2);border:1px solid var(--border);border-radius:4px;display:flex;gap:8px;align-items:flex-start;flex-wrap:wrap}
#add-panel label{font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.07em;color:var(--text3);font-family:var(--sans);white-space:nowrap;padding-top:6px}
.add-field{display:flex;flex-direction:column;gap:2px}
.add-field span{font-size:9px;color:var(--text3);font-family:var(--sans);letter-spacing:.04em}
.add-field input,.add-field select{font-size:11px;padding:4px 7px;border:1px solid var(--border);border-radius:3px;background:var(--bg);color:var(--text);font-family:var(--sans);outline:none;width:140px}
.add-field input:focus,.add-field select:focus{border-color:var(--accent)}
.add-field input.w-sm{width:90px}
.add-field input.w-lg{width:200px}
#add-btn{align-self:flex-end;padding:5px 14px;background:var(--text);color:var(--bg);border:none;border-radius:3px;font-family:var(--sans);font-size:11px;font-weight:600;letter-spacing:.04em;cursor:pointer;white-space:nowrap;text-transform:uppercase}
#add-btn:hover{opacity:.8}
#add-status{font-size:10px;color:var(--accent);font-family:var(--mono);align-self:center;min-width:120px}

/* ── Table ── */
#wt{width:100%;border-collapse:collapse;table-layout:auto}
th{background:var(--th-bg);color:var(--text2);font-size:9px;font-weight:600;text-transform:uppercase;letter-spacing:.08em;padding:6px 8px;text-align:left;border-bottom:2px solid var(--border);white-space:nowrap;cursor:pointer;user-select:none;position:sticky;top:0;z-index:10;font-family:var(--sans)}
th:hover{background:var(--th-hov)}
th.asc::after{content:" ▲";font-size:7px;opacity:.5}
th.desc::after{content:" ▼";font-size:7px;opacity:.5}
th.nosort{cursor:default}
th.nosort:hover{background:var(--th-bg)}
td{padding:6px 8px;border-bottom:1px solid var(--border);vertical-align:top;line-height:1.45;word-break:break-word}
tr:hover td{background:var(--tr-hov)}
tr.hide{display:none}
tr.user-added td:first-child{border-left:2px solid var(--accent)}

/* ── Column types ── */
.c-sec{font-size:10px;color:var(--text3);white-space:nowrap;font-family:var(--sans)}
.c-tick{white-space:nowrap}
.c-name{white-space:nowrap;font-family:var(--sans);font-weight:500}
.c-price{text-align:right;white-space:nowrap;font-family:var(--mono)}
.c-mc{text-align:right;white-space:nowrap;font-family:var(--mono)}
.c-si{text-align:right;white-space:nowrap;font-weight:600;font-family:var(--mono)}
.c-chg{text-align:right;white-space:nowrap;font-weight:600;font-family:var(--mono)}
.c-hl{text-align:right;white-space:nowrap;font-family:var(--mono)}
.c-spark{text-align:center;padding:4px 8px;white-space:nowrap}
.c-soc{min-width:180px;font-family:var(--sans)}
.c-thesis{min-width:200px;font-family:var(--sans)}

/* ── Risk-Reward Score — 1-5 stars ── */
.c-rr{text-align:center;white-space:nowrap;min-width:80px}
.rr-badge{display:inline-flex;flex-direction:column;align-items:center;gap:1px;padding:3px 6px;cursor:default}
.rr-stars{display:flex;gap:1px;line-height:1}
.star{font-size:14px;line-height:1}
.star-full  {color:#f59e0b}
.star-half  {color:#f59e0b;opacity:.85}
.star-empty {color:var(--border2)}
[data-theme="dark"] .star-empty{color:var(--border)}
.rr-stars-num{font-size:9px;font-weight:600;font-family:var(--mono);letter-spacing:.02em;margin-top:1px}
.rr-ta-row{display:flex;gap:4px;flex-wrap:wrap;justify-content:center;margin-top:3px;padding-top:3px;border-top:1px solid var(--border)}
.rr-ta-row span{font-size:8px;font-weight:600;font-family:var(--mono);letter-spacing:.02em;white-space:nowrap;cursor:default}
.rr-strong{color:#16a34a}  .rr-good{color:#0e7490}
.rr-neutral{color:#d97706} .rr-weak{color:#ea580c}
.rr-poor{color:var(--neg)}
[data-theme="dark"] .rr-strong{color:#4ade80}  [data-theme="dark"] .rr-good{color:#38bdf8}
[data-theme="dark"] .rr-neutral{color:#fbbf24} [data-theme="dark"] .rr-weak{color:#fb923c}

/* ── R/R Methodology Modal ── */
#rr-modal{display:none;position:fixed;inset:0;z-index:1000;background:rgba(0,0,0,.55);align-items:center;justify-content:center;padding:16px}
#rr-modal .modal-box{background:var(--bg);border:1px solid var(--border2);border-radius:6px;max-width:680px;width:100%;max-height:88vh;overflow-y:auto;padding:28px 32px;position:relative;font-family:var(--sans)}
#rr-modal .modal-close{position:absolute;top:14px;right:16px;background:none;border:none;font-size:18px;cursor:pointer;color:var(--text3);line-height:1}
#rr-modal .modal-close:hover{color:var(--text)}
#rr-modal h2{font-size:22px;font-weight:400;letter-spacing:-.01em;margin-bottom:4px;color:var(--text);font-family:var(--serif);font-style:italic}
#rr-modal .modal-sub{font-size:11px;color:var(--text3);margin-bottom:20px;font-family:var(--mono)}
#rr-modal h3{font-size:9px;font-weight:600;text-transform:uppercase;letter-spacing:.1em;color:var(--text3);margin:20px 0 8px;font-family:var(--sans)}
#rr-modal p{font-size:12px;line-height:1.75;color:var(--text2);margin-bottom:10px}
#rr-modal .factor-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:16px}
#rr-modal .factor-card{background:var(--bg2);border:1px solid var(--border);border-radius:4px;padding:12px 14px}
#rr-modal .factor-card .fc-header{display:flex;justify-content:space-between;align-items:baseline;margin-bottom:6px}
#rr-modal .factor-card .fc-name{font-size:13px;font-weight:400;color:var(--text);font-family:var(--serif);font-style:italic}
#rr-modal .factor-card .fc-weight{font-size:10px;font-weight:500;color:var(--accent);font-family:var(--mono)}
#rr-modal .factor-card p{font-size:11px;line-height:1.6;color:var(--text3);margin:0}
#rr-modal .scale-row{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:16px}
#rr-modal .scale-chip{display:inline-flex;flex-direction:column;align-items:center;padding:6px 10px;border-radius:3px;min-width:60px;border:1px solid transparent}
#rr-modal .scale-chip .sc-stars{font-size:13px;letter-spacing:-1px}
#rr-modal .scale-chip .sc-label{font-size:8px;font-weight:700;text-transform:uppercase;letter-spacing:.07em;margin-top:2px;font-family:var(--sans)}
#rr-modal .scale-chip .sc-range{font-size:9px;font-family:var(--mono);margin-top:1px;opacity:.7}
#rr-modal .pe-table{width:100%;border-collapse:collapse;font-size:11px;font-family:var(--mono);margin-bottom:4px}
#rr-modal .pe-table th{text-align:left;font-size:9px;text-transform:uppercase;letter-spacing:.07em;color:var(--text3);padding:4px 8px;border-bottom:1px solid var(--border);font-family:var(--sans)}
#rr-modal .pe-table td{padding:4px 8px;border-bottom:1px solid var(--border);color:var(--text2)}
#rr-modal .pe-table tr:last-child td{border-bottom:none}
#rr-modal .caveat{background:var(--bg3);border-left:3px solid var(--accent);padding:10px 14px;border-radius:0 4px 4px 0;font-size:11px;line-height:1.65;color:var(--text3);margin-top:4px}
#rr-modal .munger-btn{display:inline-flex;align-items:center;gap:6px;margin-top:16px;padding:7px 16px;background:var(--text);color:var(--bg);border-radius:3px;font-size:11px;font-weight:600;letter-spacing:.04em;text-decoration:none;font-family:var(--sans);text-transform:uppercase}
#rr-modal .munger-btn:hover{opacity:.8}
@media(max-width:600px){#rr-modal .factor-grid{grid-template-columns:1fr}}
.ts-wrap{display:block;font-size:9px;color:var(--text4);font-family:var(--mono);margin-top:2px;letter-spacing:.01em;white-space:nowrap}
.ts-wrap.fresh{color:var(--pos);opacity:.7}
.ts-wrap.stale{color:var(--neg);opacity:.7}

/* ── Badges ── */
.badge{display:inline-block;font-size:9px;font-weight:600;padding:2px 6px;border-radius:2px;white-space:nowrap;letter-spacing:.04em;font-family:var(--mono)}
.eq{background:#E1F5EE;color:#085041}
.hk{background:#E6F1FB;color:#0C447C}
.new{background:#FAEEDA;color:#633806}
[data-theme="dark"] .eq{background:#0d3322;color:#4ade80}
[data-theme="dark"] .hk{background:#0d1f3a;color:#60a5fa}
[data-theme="dark"] .new{background:#2a1a08;color:#fbbf24}

/* ── Numerics ── */
.pos{color:var(--pos);font-weight:600}
.neg{color:var(--neg);font-weight:600}
.flat{color:var(--text3)}
.si-hot{color:var(--neg);font-weight:700}
.si-med{color:#d35400;font-weight:700}
[data-theme="dark"] .si-med{color:#fb923c}
.si-low{color:var(--pos);font-weight:600}
.si-cell{text-align:right;font-family:var(--mono)}
.live-p{font-weight:600;font-size:12px;font-family:var(--mono)}
.live-mc{font-size:10px;color:var(--text3);display:block;font-family:var(--mono)}
.mc-val{font-size:11px;font-family:var(--mono)}
.dim{color:var(--text4);font-style:italic}

/* ── H/L bar ── */
.hl-hi{font-size:11px;font-family:var(--mono)}
.hl-lo{font-size:10px;color:var(--text3);font-family:var(--mono)}
.hl-pbar{margin-top:3px;background:var(--border);border-radius:1px;height:3px;width:76px}
.hl-pfill{background:var(--accent);height:3px;border-radius:1px}

/* ── Spark ── */
.spark{display:block;cursor:default}

/* ── Social badges ── */
.wsb-live{display:inline-block;font-size:10px;border-radius:2px;padding:1px 5px;margin-bottom:2px;color:#fff;background:#ff4500;font-family:var(--sans);font-weight:500}
.wsb-live.none{background:var(--border2);color:var(--text3)}
.wsb{display:inline-block;font-size:10px;background:#ff4500;color:#fff;border-radius:2px;padding:1px 5px;font-family:var(--sans)}
.cam{display:inline-block;font-size:10px;background:#2d5fa8;color:#fff;border-radius:2px;padding:1px 5px;font-family:var(--sans)}

/* ── Superinvestor position pills ── */
.si-row{display:flex;gap:3px;flex-wrap:wrap;margin-top:4px;padding-top:4px;border-top:1px solid var(--border)}
.si-pill{display:inline-flex;align-items:center;gap:2px;font-size:9px;font-weight:600;padding:2px 5px;border-radius:2px;white-space:nowrap;cursor:default;letter-spacing:.02em;font-family:var(--sans);border:1px solid transparent;transition:opacity .15s}
.si-pill:hover{opacity:.8}
.si-bull {background:#dcfce7;color:#15803d;border-color:#bbf7d0}
.si-bear {background:#fee2e2;color:#991b1b;border-color:#fecaca}
.si-watch{background:#fef9c3;color:#854d0e;border-color:#fde68a}
.si-none {background:var(--bg3);color:var(--text4);border-color:var(--border)}
[data-theme="dark"] .si-bull {background:#052e16;color:#4ade80;border-color:#14532d}
[data-theme="dark"] .si-bear {background:#300a0a;color:#f87171;border-color:#7f1d1d}
[data-theme="dark"] .si-watch{background:#1c1500;color:#fbbf24;border-color:#78350f}
[data-theme="dark"] .si-none {background:var(--bg3);color:var(--text4);border-color:var(--border)}
.note{font-size:10px;color:var(--text3);margin-top:10px;line-height:1.6;font-family:var(--sans)}

/* ── Deep Dive Panel ── */
.dd-btn{display:inline-flex;align-items:center;gap:4px;font-size:10px;font-weight:600;padding:3px 8px;background:var(--text);color:var(--bg);border-radius:3px;cursor:pointer;border:none;margin-top:4px;letter-spacing:.04em;transition:opacity .15s;white-space:nowrap;text-transform:uppercase;font-family:var(--sans)}
.dd-btn:hover{opacity:.75}
.dd-btn.open{background:var(--accent);color:#fff}
.dd-row{display:none}
.dd-row.visible{display:table-row}
.dd-cell{padding:0!important;border-bottom:2px solid var(--accent)!important}
.dd-panel{padding:20px 24px;background:var(--dd-bg);border-top:1px solid var(--dd-bd);font-size:12px;line-height:1.7;font-family:var(--sans)}
.dd-header{display:flex;align-items:baseline;gap:14px;margin-bottom:16px;flex-wrap:wrap}
.dd-title{font-size:22px;font-weight:400;letter-spacing:-.01em;font-family:var(--serif);font-style:italic}
.dd-subtitle{font-size:12px;color:var(--text3)}
.dd-updated{font-size:10px;color:var(--text3);font-family:var(--mono)}
.dd-verdict{font-size:10px;font-weight:600;padding:3px 10px;border-radius:2px;white-space:nowrap;letter-spacing:.04em;text-transform:uppercase;font-family:var(--sans)}
.dd-verdict.bull{background:#dcfce7;color:#166534}
.dd-verdict.bear{background:#fee2e2;color:#991b1b}
.dd-verdict.neutral{background:#fef9c3;color:#854d0e}
[data-theme="dark"] .dd-verdict.bull{background:#052e16;color:#4ade80}
[data-theme="dark"] .dd-verdict.bear{background:#300a0a;color:#f87171}
[data-theme="dark"] .dd-verdict.neutral{background:#1c1500;color:#fbbf24}
.dd-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px}
@media(max-width:900px){.dd-grid{grid-template-columns:1fr}}
.dd-section{background:var(--bg2);border:1px solid var(--border);border-radius:4px;padding:14px 16px}
.dd-section-full{background:var(--bg2);border:1px solid var(--border);border-radius:4px;padding:14px 16px;margin-bottom:12px}
.dd-section h4{font-size:9px;font-weight:600;text-transform:uppercase;letter-spacing:.1em;color:var(--text3);margin-bottom:10px;font-family:var(--sans)}
.dd-section ul,.dd-section-full ul{list-style:none;padding:0;margin:0}
.dd-section li,.dd-section-full li{padding:5px 0;border-bottom:1px solid var(--border);font-size:11px;line-height:1.55}
.dd-section li:last-child,.dd-section-full li:last-child{border-bottom:none}
.dd-ta-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px}
@media(max-width:900px){.dd-ta-grid{grid-template-columns:1fr}}
.dd-thesis-box{background:var(--bg2);border:1px solid var(--border);border-left:3px solid #22c55e;border-radius:4px;padding:14px 16px}
.dd-thesis-box h4{color:var(--pos)}
.dd-anti-box{background:var(--bg2);border:1px solid var(--border);border-left:3px solid var(--neg);border-radius:4px;padding:14px 16px}
.dd-anti-box h4{color:var(--neg)}
.dd-thesis-box h4,.dd-anti-box h4{font-size:9px;font-weight:600;text-transform:uppercase;letter-spacing:.1em;margin-bottom:10px;font-family:var(--sans)}
.dd-thesis-box li,.dd-anti-box li{padding:4px 0;font-size:11px;line-height:1.55;border-bottom:1px solid var(--border);list-style:none}
.dd-thesis-box li:last-child,.dd-anti-box li:last-child{border-bottom:none}
.dd-thesis-box li::before{content:"+ ";color:var(--pos);font-weight:700;font-family:var(--mono)}
.dd-anti-box li::before{content:"− ";color:var(--neg);font-weight:700;font-family:var(--mono)}
.src{display:inline-block;font-size:8px;font-weight:600;padding:1px 5px;border-radius:2px;margin-right:4px;vertical-align:middle;white-space:nowrap;letter-spacing:.05em;font-family:var(--sans)}
.src-sec{background:#e0f2fe;color:#0369a1}
.src-earn{background:#f0fdf4;color:#166534}
.src-pod{background:#fdf4ff;color:#7e22ce}
.src-insider{background:#fff7ed;color:#c2410c}
.src-super{background:#fefce8;color:#854d0e}
.src-blog{background:#f8fafc;color:#475569;border:1px solid #e2e8f0}
.src-news{background:#f1f5f9;color:#334155}
[data-theme="dark"] .src-sec{background:#0c1f30;color:#60a5fa}
[data-theme="dark"] .src-earn{background:#052e16;color:#4ade80}
[data-theme="dark"] .src-pod{background:#1a0a2e;color:#c084fc}
[data-theme="dark"] .src-insider{background:#1f0f00;color:#fb923c}
[data-theme="dark"] .src-super{background:#1a1200;color:#fbbf24}
[data-theme="dark"] .src-blog,[data-theme="dark"] .src-news{background:var(--bg3);color:var(--text2);border-color:var(--border)}
.inv-tag{display:inline-flex;align-items:center;gap:4px;font-size:10px;font-weight:600;padding:2px 8px;border-radius:2px;margin:2px;font-family:var(--sans)}
.inv-bull{background:#dcfce7;color:#15803d}
.inv-bear{background:#fee2e2;color:#b91c1c}
.inv-watch{background:#fef9c3;color:#92400e}
[data-theme="dark"] .inv-bull{background:#052e16;color:#4ade80}
[data-theme="dark"] .inv-bear{background:#300a0a;color:#f87171}
[data-theme="dark"] .inv-watch{background:#1c1500;color:#fbbf24}
.dd-summary{background:var(--bg3);border:1px solid var(--border);border-radius:4px;padding:14px 18px;margin-bottom:12px;font-size:11px;line-height:1.85;color:var(--text2)}
[data-theme="dark"] .dd-summary{background:#0d0d0f;color:#d4d4d0}
.dd-summary strong{color:var(--text);font-weight:600}
.dd-loading{display:flex;align-items:center;gap:10px;padding:30px;color:var(--text3);font-size:12px}
.dd-spinner{width:18px;height:18px;border:2px solid var(--border2);border-top-color:var(--accent);border-radius:50%;animation:spin .7s linear infinite;flex-shrink:0}
@keyframes spin{to{transform:rotate(360deg)}}
.dd-regen{font-size:10px;padding:2px 8px;background:transparent;border:1px solid var(--border2);border-radius:3px;cursor:pointer;color:var(--text3);font-family:var(--sans)}
.dd-regen:hover{border-color:var(--accent);color:var(--accent)}
.conf-bar{display:flex;align-items:center;gap:8px;margin-top:8px}
.conf-track{flex:1;height:4px;background:var(--border2);border-radius:2px}
.conf-fill{height:4px;border-radius:2px;background:linear-gradient(90deg,var(--neg),#f59e0b,var(--pos))}
</style>
</head>
<body>

<div id="wordmark">
  <svg width="40" height="40" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" style="flex-shrink:0;border-radius:4px;background:#F5F2EC" aria-label="Deal Dough">
    <path d="M22,78 L22,44 Q22,18 50,16 Q78,18 78,44 L78,78 Z" fill="#1A1614"/>
    <path d="M22,78 L22,62 L78,62 L78,78 Z" fill="#2E2825"/>
    <path d="M33,60 L33,46 Q33,28 50,26 Q67,28 67,46 L67,60 Z" fill="#F5F2EC"/>
    <path d="M33,50 Q50,44 67,50" fill="none" stroke="#1A1614" stroke-width="1.5" stroke-linecap="round" opacity="0.3"/>
  </svg>
  <div style="display:flex;flex-direction:column;gap:1px">
    <span class="wm-name">Deal Dough</span>
    <span class="wm-tag">Live Watchlist &amp; Research</span>
  </div>
</div>

<div id="sbar">
  <span><span class="dot loading" id="sdot"></span><span id="stxt">Connecting…</span></span>
  <span>📈 Yahoo Finance (15min delay)</span>
  <span>🪙 CMC API (crypto)</span>
  <span>💬 Tradestie WSB live</span>
  <span>⏱ Updated: <strong id="lupd">—</strong></span>
  <button class="rbtn" onclick="refresh()">↻ Refresh</button>
  <label id="dm-toggle" title="Toggle dark mode">
    <span id="dm-label">Light</span>
    <div class="dm-track"><div class="dm-thumb"></div></div>
  </label>
</div>

<div id="ctrl">
  <input id="srch" type="text" placeholder="🔍 Search ticker, name, keyword…" oninput="applyFilters()">
  <span id="rcnt"></span>
  <button class="rbtn" onclick="document.getElementById('rr-modal').style.display='flex'" title="How the R/R Score is calculated">R/R Methodology</button>
  <a class="rbtn" href="https://fs.blog/charlie-munger-reading-list/" target="_blank" rel="noopener" title="Charlie Munger reading list — Farnam Street">☯ Munger</a>
  <div id="fbars">
    <button class="fbtn active" data-f="all" onclick="filt(this)">All</button>
    <button class="fbtn" data-f="AI & Semiconductors — Core" onclick="filt(this)">AI & Semiconductor</button>
    <button class="fbtn" data-f="Quantum Computing" onclick="filt(this)">Quantum Computing</button>
    <button class="fbtn" data-f="Memory & Storage" onclick="filt(this)">Memory & Storage</button>
    <button class="fbtn" data-f="Space & Defence" onclick="filt(this)">Space & Defence</button>
    <button class="fbtn" data-f="Uranium & Nuclear" onclick="filt(this)">Uranium & Nuclear</button>
    <button class="fbtn" data-f="Bitcoin / Crypto Treasury — Equities" onclick="filt(this)">Bitcoin</button>
    <button class="fbtn" data-f="China / Hong Kong Equities" onclick="filt(this)">China</button>
    <button class="fbtn" data-f="Biotech & Healthcare" onclick="filt(this)">Biotech</button>
    <button class="fbtn" data-f="Specialist — Superconductors / SaaS / Semis" onclick="filt(this)">Specialist</button>
    <button class="fbtn" data-f="Robotics Value Chain" onclick="filt(this)">Robotics</button>
    <button class="fbtn" data-f="Crypto — AI & DePin" onclick="filt(this)">Crypto AI</button>
  </div>
</div>

<!-- ADD TICKER PANEL -->
<div id="add-panel">
  <label>+ Add Asset</label>
  <div class="add-field">
    <span>Ticker / Symbol</span>
    <input id="add-ticker" class="w-sm" type="text" placeholder="e.g. MSFT" autocomplete="off" spellcheck="false">
  </div>
  <div class="add-field">
    <span>Name</span>
    <input id="add-name" type="text" placeholder="e.g. Microsoft">
  </div>
  <div class="add-field">
    <span>Sector</span>
    <select id="add-sector">
      <option value="AI & Semiconductors — Core">AI &amp; Semiconductors</option>
      <option value="Quantum Computing">Quantum Computing</option>
      <option value="Memory & Storage">Memory &amp; Storage</option>
      <option value="Space & Defence">Space &amp; Defence</option>
      <option value="Uranium & Nuclear">Uranium &amp; Nuclear</option>
      <option value="Bitcoin / Crypto Treasury — Equities">Bitcoin / Crypto</option>
      <option value="China / Hong Kong Equities">China / HK</option>
      <option value="Biotech & Healthcare">Biotech &amp; Healthcare</option>
      <option value="Specialist — Superconductors / SaaS / Semis">Specialist</option>
      <option value="Robotics Value Chain">Robotics</option>
      <option value="Crypto — AI & DePin">Crypto — AI &amp; DePin</option>
      <option value="Custom">Custom</option>
    </select>
  </div>
  <div class="add-field">
    <span>Notes (optional)</span>
    <input id="add-notes" class="w-lg" type="text" placeholder="Investment thesis or reminder…">
  </div>
  <button id="add-btn" onclick="addTicker()">Add →</button>
  <span id="add-status"></span>
</div>

<table id="wt">
<thead><tr>
  <th onclick="srt(0)">Sector</th>
  <th onclick="srt(1)">Ticker</th>
  <th onclick="srt(2)">Name</th>
  <th onclick="srt(3)" title="Live price (15min delay)">Price</th>
  <th onclick="srt(4)" title="Market capitalisation">Mkt Cap</th>
  <th onclick="srt(5)" title="Short interest % of float">SI %</th>
  <th onclick="srt(6)" title="Day change % from previous close">Day Chg</th>
  <th onclick="srt(7)" title="4-week high / low with position bar">4W Hi / Lo</th>
  <th class="nosort" title="7-day closing price trendline">7D Trend</th>
  <th onclick="srt(9)" title="Composite score 0–100: Valuation 20% · TA (RSI+OBV+Fib+SMA+EMA+S/R) 30% · 7D Momentum 15% · News 15% · Tailwinds 20%">R/R Score ↕</th>
  <th class="nosort">Social</th>
  <th class="nosort">Thesis &amp; Deep Dive</th>
</tr></thead>
<tbody id="wtb">
<tr data-sector="AI & Semiconductors — Core" data-ticker="NVDA" data-i="0">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >NVDA</span></td>
  <td class="c-name" style="font-size:12px">NVIDIA</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$5.71 T</span></td>
  <td class="si-cell si-low" data-si="">1.17%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High</span> <span class="cam">Camillo: Core AI infra</span><br>Most mentioned AI stock on Reddit; perennial WSB top 3</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI GPU monopoly; CUDA ecosystem; NVQLink quantum; Q1 FY27 earnings May 20
  <button class="dd-btn" onclick="openDD(this,'NVDA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="MU" data-i="1">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >MU</span></td>
  <td class="c-name" style="font-size:12px">Micron Technology</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$913 B</span></td>
  <td class="si-cell si-low" data-si="">~4% ↑</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — #7 in 2026 index</span> <span class="cam">Camillo: Fits — AI memory supercycle</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#3 ranked; HBM/DRAM supercycle; Q2 revenue +196% YoY; approaching $1T market cap
  <button class="dd-btn" onclick="openDD(this,'MU')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="AMD" data-i="2">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >AMD</span></td>
  <td class="c-name" style="font-size:12px">Advanced Micro Devices</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$733 B</span></td>
  <td class="si-cell si-low" data-si="">2.22%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High</span> <span class="cam">Camillo: Indirect — AI infra adjacent</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">MI300X AI GPU; NVDA challenger; +260% in 52 weeks; $37.5B revenue FY26
  <button class="dd-btn" onclick="openDD(this,'AMD')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="INTC" data-i="3">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >INTC</span></td>
  <td class="c-name" style="font-size:12px">Intel</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$534 B</span></td>
  <td class="si-cell si-low" data-si="">2.87%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — trending on Apple foundry deal</span> <span class="cam">Camillo: Turnaround narrative</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Foundry turnaround; Gaudi AI chips; +492% in 52 weeks; Apple foundry partnership
  <button class="dd-btn" onclick="openDD(this,'INTC')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="PLTR" data-i="4">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >PLTR</span></td>
  <td class="c-name" style="font-size:12px">Palantir Technologies</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$320 B</span></td>
  <td class="si-cell si-low" data-si="">2.47%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — #10 in 2026 index</span> <span class="cam">Camillo: Fits — military AI</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#5 ranked; military AI; AIP platform; US commercial revenue +133% YoY
  <button class="dd-btn" onclick="openDD(this,'PLTR')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="CBRS" data-i="5">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >CBRS</span></td>
  <td class="c-name" style="font-size:12px">Cerebras Systems</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$43 B</span></td>
  <td class="si-cell si-cell" data-si="">N/A — IPO'd May 14</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Exploding — massive IPO buzz</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Wafer-scale AI chip; IPO'd May 14 at $185; raised $5.55B; NVDA alternative narrative
  <button class="dd-btn" onclick="openDD(this,'CBRS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="CRWV" data-i="6">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >CRWV</span></td>
  <td class="c-name" style="font-size:12px">CoreWeave</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$62 B</span></td>
  <td class="si-cell si-med" data-si="">11.85%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Fits — AI cloud infra</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI GPU cloud infra; Q1 revenue +112% YoY; OpenAI anchor tenant; $35B debt load is key risk
  <button class="dd-btn" onclick="openDD(this,'CRWV')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="NBIS" data-i="7">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >NBIS</span></td>
  <td class="c-name" style="font-size:12px">Nebius Group</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$45 B</span></td>
  <td class="si-cell si-hot" data-si="">17.04%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — #5 in WSB 2026 index</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">European AI GPU cloud (ex-Yandex); NVDA partnership; +545% in 52 weeks; 17% SI = squeeze risk
  <button class="dd-btn" onclick="openDD(this,'NBIS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="BIDU" data-i="8">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >BIDU</span></td>
  <td class="c-name" style="font-size:12px">Baidu</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$30 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Weak</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China AI leader; Ernie Bot; Apollo Go self-driving; trades at deep discount vs US AI peers
  <button class="dd-btn" onclick="openDD(this,'BIDU')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="ORCL" data-i="9">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >ORCL</span></td>
  <td class="c-name" style="font-size:12px">Oracle</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$566 B</span></td>
  <td class="si-cell si-low" data-si="">~1.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI cloud GPU clusters; LLM hosting; cloud infra hyperscaler play for enterprise AI
  <button class="dd-btn" onclick="openDD(this,'ORCL')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="NOW" data-i="10">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >NOW</span></td>
  <td class="c-name" style="font-size:12px">ServiceNow</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$200 B</span></td>
  <td class="si-cell si-low" data-si="">~1.8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Weak — B2B SaaS</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI fat-data moat; enterprise workflow lock-in; SaaS rotation target
  <button class="dd-btn" onclick="openDD(this,'NOW')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="APP" data-i="11">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >APP</span></td>
  <td class="c-name" style="font-size:12px">Applovin</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$80 B</span></td>
  <td class="si-cell si-low" data-si="">~3.2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-powered ad tech; AXON AI model; confirmed great earnings; +260% in 52 weeks
  <button class="dd-btn" onclick="openDD(this,'APP')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="DDOG" data-i="12">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >DDOG</span></td>
  <td class="c-name" style="font-size:12px">Datadog</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$40 B</span></td>
  <td class="si-cell si-low" data-si="">~3.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI observability; monitoring AI workloads; confirmed great earnings
  <button class="dd-btn" onclick="openDD(this,'DDOG')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="NET" data-i="13">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >NET</span></td>
  <td class="c-name" style="font-size:12px">Cloudflare</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$65 B</span></td>
  <td class="si-cell si-low" data-si="">~2.8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI inference edge network; CDN + security + AI gateway; SaaS rotation candidate
  <button class="dd-btn" onclick="openDD(this,'NET')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="RDDT" data-i="14">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >RDDT</span></td>
  <td class="c-name" style="font-size:12px">Reddit</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$27 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — #6 in WSB 2026 index</span> <span class="cam">Camillo: Perfect fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI data licensing moat; LLM training data demand; unique human-generated corpus
  <button class="dd-btn" onclick="openDD(this,'RDDT')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="QCOM" data-i="15">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >QCOM</span></td>
  <td class="c-name" style="font-size:12px">Qualcomm</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$160 B</span></td>
  <td class="si-cell si-low" data-si="">~1.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">On-device AI chips; Snapdragon X; PC + mobile AI inference
  <button class="dd-btn" onclick="openDD(this,'QCOM')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="VICR" data-i="16">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >VICR</span></td>
  <td class="c-name" style="font-size:12px">Vicor</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$4 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Vertical power delivery for Cerebras wafer-scale engines; CBRS IPO adds fresh catalyst
  <button class="dd-btn" onclick="openDD(this,'VICR')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="GDYN" data-i="17">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >GDYN</span></td>
  <td class="c-name" style="font-size:12px">Grid Dynamics</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$1 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Enterprise AI implementation consultancy; breakout volume signal
  <button class="dd-btn" onclick="openDD(this,'GDYN')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="AVGO" data-i="18">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >AVGO</span></td>
  <td class="c-name" style="font-size:12px">Broadcom Inc</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$2.0 T</span></td>
  <td class="si-cell si-low" data-si="">~1.2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — AI chip alternative</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">World's #2 AI chip company; custom AI ASICs for Google, Meta, Apple; VMware $6.8B/qtr; Google 2031 deal
  <button class="dd-btn" onclick="openDD(this,'AVGO')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="ALAB" data-i="19">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >ALAB</span></td>
  <td class="c-name" style="font-size:12px">Astera Labs</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$34 B</span></td>
  <td class="si-cell si-med" data-si="">8.43%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">PCIe/CXL/ethernet connectivity chips for AI data centres; +182% 52W; NVDA ecosystem play
  <button class="dd-btn" onclick="openDD(this,'ALAB')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="VRT" data-i="20">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >VRT</span></td>
  <td class="c-name" style="font-size:12px">Vertiv Holdings</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$100 B</span></td>
  <td class="si-cell si-low" data-si="">~2.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Critical power and thermal management for AI data centres; liquid cooling supercycle; $800B+ hyperscaler capex
  <button class="dd-btn" onclick="openDD(this,'VRT')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="CRDO" data-i="21">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >CRDO</span></td>
  <td class="c-name" style="font-size:12px">Credo Technology</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$22 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Active electrical cables and SerDes chips for AI data centre interconnect; earnings Jun 1 catalyst
  <button class="dd-btn" onclick="openDD(this,'CRDO')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="DELL" data-i="22">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >DELL</span></td>
  <td class="c-name" style="font-size:12px">Dell Technologies</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$90 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — Trump endorsement + earnings beat</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI server infrastructure; PowerEdge GPU servers; +30% AH May 28; Trump publicly endorsed
  <button class="dd-btn" onclick="openDD(this,'DELL')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="SNOW" data-i="23">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >SNOW</span></td>
  <td class="c-name" style="font-size:12px">Snowflake</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$70 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI data cloud; Cortex AI; SaaS pricing shift from per-seat to per-token; JC conviction long
  <button class="dd-btn" onclick="openDD(this,'SNOW')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="CRWD" data-i="24">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >CRWD</span></td>
  <td class="c-name" style="font-size:12px">CrowdStrike</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$110 B</span></td>
  <td class="si-cell si-low" data-si="">2.93%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-native cybersecurity; Falcon platform; $5.25B ARR +24%; earnings Jun 3
  <button class="dd-btn" onclick="openDD(this,'CRWD')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="ZS" data-i="25">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >ZS</span></td>
  <td class="c-name" style="font-size:12px">Zscaler</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$50 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Cloud-native zero-trust security; 50%+ drawdown + 26% revenue growth; contrarian setup
  <button class="dd-btn" onclick="openDD(this,'ZS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="FTNT" data-i="26">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >FTNT</span></td>
  <td class="c-name" style="font-size:12px">Fortinet</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$80 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Network security + SASE; cheapest quality cybersecurity at ~30x forward PE; 41% product revenue growth
  <button class="dd-btn" onclick="openDD(this,'FTNT')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="SKM" data-i="27">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq" >SKM</span></td>
  <td class="c-name" style="font-size:12px">SK Telecom</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$12 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">South Korea's largest telecom; AI platform + SK Hynix ecosystem exposure; 6G development
  <button class="dd-btn" onclick="openDD(this,'SKM')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Quantum Computing" data-ticker="IONQ" data-i="28">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Quantum Computing</td>
  <td class="c-tick"><span class="badge eq" >IONQ</span></td>
  <td class="c-name" style="font-size:12px">IonQ</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$20 B</span></td>
  <td class="si-cell si-hot" data-si="">22.51%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Leading pure-play quantum; Q1 revenue $64.7M +755% YoY; 22.5% short float = potential squeeze
  <button class="dd-btn" onclick="openDD(this,'IONQ')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Quantum Computing" data-ticker="RGTI" data-i="29">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Quantum Computing</td>
  <td class="c-tick"><span class="badge eq" >RGTI</span></td>
  <td class="c-name" style="font-size:12px">Rigetti Computing</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$6 B</span></td>
  <td class="si-cell si-med" data-si="">12.50%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Superconducting qubit; 108-qubit Cepheus-1; Q1 revenue +199% YoY; 12.5% short elevated
  <button class="dd-btn" onclick="openDD(this,'RGTI')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Quantum Computing" data-ticker="QBTS" data-i="30">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Quantum Computing</td>
  <td class="c-tick"><span class="badge eq" >QBTS</span></td>
  <td class="c-name" style="font-size:12px">D-Wave Quantum</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$8.9 B</span></td>
  <td class="si-cell si-med" data-si="">14.04%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Annealing + gate-model dual platform; bookings +1,994% YoY; 83% gross margin
  <button class="dd-btn" onclick="openDD(this,'QBTS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Memory & Storage" data-ticker="SNDK" data-i="31">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Memory & Storage</td>
  <td class="c-tick"><span class="badge eq" >SNDK</span></td>
  <td class="c-name" style="font-size:12px">SanDisk</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$70 B</span></td>
  <td class="si-cell si-low" data-si="">6.58% ↑</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — trending</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">NAND flash; WDC spinoff; +3,930% in 52 weeks; AI SSD demand supercycle
  <button class="dd-btn" onclick="openDD(this,'SNDK')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Memory & Storage" data-ticker="WDC" data-i="32">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Memory & Storage</td>
  <td class="c-tick"><span class="badge eq" >WDC</span></td>
  <td class="c-name" style="font-size:12px">Western Digital</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$30 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">HDD + NAND; AI data centre capacity build; DRAM ETF top holding
  <button class="dd-btn" onclick="openDD(this,'WDC')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Memory & Storage" data-ticker="STX" data-i="33">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Memory & Storage</td>
  <td class="c-tick"><span class="badge eq" >STX</span></td>
  <td class="c-name" style="font-size:12px">Seagate</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$25 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">HDD storage; AI data centre demand; pairs with MU/SNDK/WDC in storage basket
  <button class="dd-btn" onclick="openDD(this,'STX')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Space & Defence" data-ticker="RKLB" data-i="34">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq" >RKLB</span></td>
  <td class="c-name" style="font-size:12px">Rocket Lab USA</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$72 B</span></td>
  <td class="si-cell si-low" data-si="">5.45%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — #2 in 2026 index</span> <span class="cam">Camillo: Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#1 ranked; record Q1 $200.3M revenue; $2.2B backlog; Neutron + Raytheon SBIRS
  <button class="dd-btn" onclick="openDD(this,'RKLB')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Space & Defence" data-ticker="ASTS" data-i="35">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq" >ASTS</span></td>
  <td class="c-name" style="font-size:12px">AST SpaceMobile</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$18 B</span></td>
  <td class="si-cell si-med" data-si="">12.7% ↑↑</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — #1 in 2026 index</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#2 ranked; 12.7% SI rising post-BlueBird failure; Trump personal position disclosed
  <button class="dd-btn" onclick="openDD(this,'ASTS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Space & Defence" data-ticker="LUNR" data-i="36">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq" >LUNR</span></td>
  <td class="c-name" style="font-size:12px">Intuitive Machines</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$1 B</span></td>
  <td class="si-cell si-low" data-si="">~6%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">NASA/DoD lunar lander contracts; binary on IM-3 mission; SpaceX IPO tailwind
  <button class="dd-btn" onclick="openDD(this,'LUNR')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Space & Defence" data-ticker="SPCE" data-i="37">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq" >SPCE</span></td>
  <td class="c-name" style="font-size:12px">Virgin Galactic</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$165-210 M</span></td>
  <td class="si-cell si-low" data-si="">~8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — SpaceX IPO halo trade</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">SpaceX IPO halo; Delta class spaceplane Q3 flight test; micro-cap high beta to space narrative
  <button class="dd-btn" onclick="openDD(this,'SPCE')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="CCJ" data-i="38">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq" >CCJ</span></td>
  <td class="c-name" style="font-size:12px">Cameco</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$18 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">World's largest publicly traded uranium miner; nuclear renaissance on AI data centre power
  <button class="dd-btn" onclick="openDD(this,'CCJ')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="UEC" data-i="39">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq" >UEC</span></td>
  <td class="c-name" style="font-size:12px">Uranium Energy Corp</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$3 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">US-domestic uranium supply; energy security narrative
  <button class="dd-btn" onclick="openDD(this,'UEC')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="NXE" data-i="40">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq" >NXE</span></td>
  <td class="c-name" style="font-size:12px">NexGen Energy</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$5 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Tier-1 Arrow deposit; highest-grade undeveloped uranium in Athabasca Basin
  <button class="dd-btn" onclick="openDD(this,'NXE')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="VST" data-i="41">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq" >VST</span></td>
  <td class="c-name" style="font-size:12px">Vistra Corp</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$54 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Largest competitive US power generator; AI data centre power purchase agreements; avg PT $221 = 47% upside
  <button class="dd-btn" onclick="openDD(this,'VST')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="MSTR" data-i="42">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq" >MSTR</span></td>
  <td class="c-name" style="font-size:12px">Strategy Inc</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$100 B</span></td>
  <td class="si-cell si-med" data-si="">10.60%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — Bitcoin proxy cult stock</span> <span class="cam">Camillo: Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">818K BTC; leveraged BTC proxy; 10.6% SI = meaningful squeeze risk if BTC rallies
  <button class="dd-btn" onclick="openDD(this,'MSTR')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="COIN" data-i="43">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq" >COIN</span></td>
  <td class="c-name" style="font-size:12px">Coinbase</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$60 B</span></td>
  <td class="si-cell si-med" data-si="">9.57%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High</span> <span class="cam">Camillo: Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Crypto exchange; Clarity Act beneficiary; 9.6% short interest; BTC hit $82K catalyst window
  <button class="dd-btn" onclick="openDD(this,'COIN')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="HOOD" data-i="44">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq" >HOOD</span></td>
  <td class="c-name" style="font-size:12px">Robinhood Markets</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$25 B</span></td>
  <td class="si-cell si-low" data-si="">3.53%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High</span> <span class="cam">Camillo: Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Retail brokerage; crypto + prediction markets; Q1 revenue strong; Tiger Global new buyer
  <button class="dd-btn" onclick="openDD(this,'HOOD')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="CRCL" data-i="45">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq" >CRCL</span></td>
  <td class="c-name" style="font-size:12px">Circle Internet Group</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$8–12 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">USDC stablecoin issuer; IPO 2026; Clarity Act direct beneficiary
  <button class="dd-btn" onclick="openDD(this,'CRCL')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="GLXY" data-i="46">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq" >GLXY</span></td>
  <td class="c-name" style="font-size:12px">Galaxy Digital</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$8 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Crypto merchant bank; BTC/ETH treasury + trading; direct crypto market exposure
  <button class="dd-btn" onclick="openDD(this,'GLXY')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="DFDV" data-i="47">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq" >DFDV</span></td>
  <td class="c-name" style="font-size:12px">DeFi Dev Corp</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">small cap</span></td>
  <td class="si-cell si-med" data-si="">~8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate — SOL treasury play</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">SOL treasury company; MSTR model applied to Solana; small cap with high beta to SOL price
  <button class="dd-btn" onclick="openDD(this,'DFDV')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="BABA" data-i="48">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq" >BABA</span></td>
  <td class="c-name" style="font-size:12px">Alibaba</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$270 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China ecommerce + AI cloud (Qwen LLM); US-China trade thaw = direct catalyst
  <button class="dd-btn" onclick="openDD(this,'BABA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 700" data-i="49">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk" >HK: 700</span></td>
  <td class="c-name" style="font-size:12px">Tencent</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$550 B</span></td>
  <td class="si-cell si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China internet; gaming; AI moat; WeChat ecosystem; US-China thaw tailwind
  <button class="dd-btn" onclick="openDD(this,'HK: 700')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 1810" data-i="50">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk" >HK: 1810</span></td>
  <td class="c-name" style="font-size:12px">Xiaomi</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$80 B</span></td>
  <td class="si-cell si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">EV + smartphone ecosystem; SU7 car momentum; China tech re-rating
  <button class="dd-btn" onclick="openDD(this,'HK: 1810')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 9992" data-i="51">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk" >HK: 9992</span></td>
  <td class="c-name" style="font-size:12px">Pop Mart</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$30 B</span></td>
  <td class="si-cell si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Very Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Collectibles/IP; Labubu TikTok viral; China consumer re-rating; international expansion
  <button class="dd-btn" onclick="openDD(this,'HK: 9992')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 0100" data-i="52">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk" >HK: 0100</span></td>
  <td class="c-name" style="font-size:12px">MiniMax Group</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$34 B</span></td>
  <td class="si-cell si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China AI LLM; Hailuo AI video viral; 212M users; 70%+ overseas revenue; doubled on Jan 2026 IPO
  <button class="dd-btn" onclick="openDD(this,'HK: 0100')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="HIMS" data-i="53">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq" >HIMS</span></td>
  <td class="c-name" style="font-size:12px">Hims &amp; Hers Health</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$4 B</span></td>
  <td class="si-cell si-hot" data-si="">30–43% ↑↑</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — GLP-1 meme</span> <span class="cam">Camillo: Very Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Telehealth; GLP-1 branded pivot; 30–43% short interest = massive squeeze potential
  <button class="dd-btn" onclick="openDD(this,'HIMS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="RXRX" data-i="54">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq" >RXRX</span></td>
  <td class="c-name" style="font-size:12px">Recursion Pharma</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$3 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI drug discovery; ML pipeline; largest proprietary biology dataset in industry
  <button class="dd-btn" onclick="openDD(this,'RXRX')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="CMPS" data-i="55">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq" >CMPS</span></td>
  <td class="c-name" style="font-size:12px">COMPASS Pathways</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.5 B</span></td>
  <td class="si-cell si-med" data-si="">~8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate — psychedelic narrative</span> <span class="cam">Camillo: Strong fit</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Psilocybin mental health; COMP360 Phase 3; psychedelic therapy social narrative building
  <button class="dd-btn" onclick="openDD(this,'CMPS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="GHRS" data-i="56">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq" >GHRS</span></td>
  <td class="c-name" style="font-size:12px">GH Research</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.4 B</span></td>
  <td class="si-cell si-low" data-si="">~6%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Ibogaine-based depression/addiction therapy; novel mechanism of action
  <button class="dd-btn" onclick="openDD(this,'GHRS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="AMSC" data-i="57">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq" >AMSC</span></td>
  <td class="c-name" style="font-size:12px">American Superconductor</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$1.5 B</span></td>
  <td class="si-cell si-low" data-si="">~7%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#1 in Hans' 21-report superconductor deep dive; wind energy + DoD power
  <button class="dd-btn" onclick="openDD(this,'AMSC')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="HIMX" data-i="58">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq" >HIMX</span></td>
  <td class="c-name" style="font-size:12px">Himax Technologies</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$2 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Display driver ICs; monthly base breakout; AR/VR adoption play
  <button class="dd-btn" onclick="openDD(this,'HIMX')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="APLD" data-i="59">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq" >APLD</span></td>
  <td class="c-name" style="font-size:12px">Applied Digital</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$2 B</span></td>
  <td class="si-cell si-med" data-si="">~9%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI data centres; data centre narrative riding AI infra supercycle
  <button class="dd-btn" onclick="openDD(this,'APLD')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="HACK" data-i="60">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq" >HACK</span></td>
  <td class="c-name" style="font-size:12px">Amplify Cybersecurity ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">ETF</span></td>
  <td class="si-cell si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">JC: "10 year Livermore Accumulation Cylinder is breaking out" on HACK chart; holds CRWD, ZS, FTNT, PANW
  <button class="dd-btn" onclick="openDD(this,'HACK')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="QTUM" data-i="61">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq" >QTUM</span></td>
  <td class="c-name" style="font-size:12px">Defiance Quantum ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">ETF</span></td>
  <td class="si-cell si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">JC preferred quantum basket for next 90-120 days; IONQ, RGTI, QBTS, CCCX
  <button class="dd-btn" onclick="openDD(this,'QTUM')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="NOWL" data-i="62">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge new" >NOWL</span></td>
  <td class="c-name" style="font-size:12px">ServiceNow 2x Bull ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">small</span></td>
  <td class="si-cell si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">JC: "full ported NOWL at open" May 29; 2x leveraged ServiceNow; highest-conviction JC trade
  <button class="dd-btn" onclick="openDD(this,'NOWL')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="TSLA" data-i="63">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >TSLA</span></td>
  <td class="c-name" style="font-size:12px">Tesla</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$1.61 T</span></td>
  <td class="si-cell si-low" data-si="">~2.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Extreme</span> <span class="cam">Camillo: Very Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">EV + Optimus humanoid + FSD AI; #1 consumer-visible robotics stock
  <button class="dd-btn" onclick="openDD(this,'TSLA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="AMZN" data-i="64">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >AMZN</span></td>
  <td class="c-name" style="font-size:12px">Amazon</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$2.58 T</span></td>
  <td class="si-cell si-low" data-si="">~0.8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Proteus/Sequoia warehouse robots; Zoox robotaxi; Kuiper satellite; $200B capex 2026
  <button class="dd-btn" onclick="openDD(this,'AMZN')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ISRG" data-i="65">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >ISRG</span></td>
  <td class="c-name" style="font-size:12px">Intuitive Surgical</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$195 B</span></td>
  <td class="si-cell si-low" data-si="">~1.2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">World leader in robotic surgery; da Vinci 5 system; 85% recurring revenue
  <button class="dd-btn" onclick="openDD(this,'ISRG')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="PRCT" data-i="66">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >PRCT</span></td>
  <td class="c-name" style="font-size:12px">Procept BioRobotics</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$6 B</span></td>
  <td class="si-cell si-hot" data-si="">~18%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Aquabeam robotic hydrodissection; fastest-growing surgical robot; 18% SI = squeeze potential
  <button class="dd-btn" onclick="openDD(this,'PRCT')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="NOVT" data-i="67">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >NOVT</span></td>
  <td class="c-name" style="font-size:12px">Novanta</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$4.5 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Precision motion + laser components for surgical robots (ISRG supply chain) + industrial automation
  <button class="dd-btn" onclick="openDD(this,'NOVT')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ROK" data-i="68">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >ROK</span></td>
  <td class="c-name" style="font-size:12px">Rockwell Automation</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$25 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Industrial automation leader; AI-integrated factory control; US re-shoring direct beneficiary
  <button class="dd-btn" onclick="openDD(this,'ROK')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="SYM" data-i="69">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >SYM</span></td>
  <td class="c-name" style="font-size:12px">Symbotic</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$18 B</span></td>
  <td class="si-cell si-hot" data-si="">~15%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-powered warehouse robotics; Walmart anchor; SoftBank-backed; 15% SI; revenue +88% YoY
  <button class="dd-btn" onclick="openDD(this,'SYM')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ZBRA" data-i="70">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >ZBRA</span></td>
  <td class="c-name" style="font-size:12px">Zebra Technologies</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$15 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Barcode + RFID + warehouse automation; supply chain AI integration; re-shoring beneficiary
  <button class="dd-btn" onclick="openDD(this,'ZBRA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="CGNX" data-i="71">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >CGNX</span></td>
  <td class="c-name" style="font-size:12px">Cognex</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$7 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Machine vision leader; EV battery + semi fab inspection; JPMorgan upgrade May 26 OW / PT $75
  <button class="dd-btn" onclick="openDD(this,'CGNX')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="MOD" data-i="72">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >MOD</span></td>
  <td class="c-name" style="font-size:12px">Modine Manufacturing</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$4.5 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Thermal management systems; AI data centre cooling + EV thermal; pivoting to high-growth data centre
  <button class="dd-btn" onclick="openDD(this,'MOD')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="TER" data-i="73">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >TER</span></td>
  <td class="c-name" style="font-size:12px">Teradyne</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$18 B</span></td>
  <td class="si-cell si-low" data-si="">~2.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Semi ATE (tests NVDA/TSMC output) + Universal Robots cobots; dual exposure AI chip test + industrial robotics
  <button class="dd-btn" onclick="openDD(this,'TER')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ALNT" data-i="74">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >ALNT</span></td>
  <td class="c-name" style="font-size:12px">Allient</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.6 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Motion control for surgical robots + defence UAVs + EVs; JPMorgan upgrade May 26 OW / PT $80
  <button class="dd-btn" onclick="openDD(this,'ALNT')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="OUST" data-i="75">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >OUST</span></td>
  <td class="c-name" style="font-size:12px">Ouster</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$1.5 B</span></td>
  <td class="si-cell si-hot" data-si="">~22%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — AV/LiDAR speculation</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Digital LiDAR for AV + robotics + smart cities; 22% short float = one of highest in robotics
  <button class="dd-btn" onclick="openDD(this,'OUST')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="AEVA" data-i="76">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >AEVA</span></td>
  <td class="c-name" style="font-size:12px">Aeva Technologies</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.8 B</span></td>
  <td class="si-cell si-hot" data-si="">~25%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">FMCW 4D LiDAR — sees velocity + distance; VW + Continental + Daimler Trucks validation; 25% SI extreme
  <button class="dd-btn" onclick="openDD(this,'AEVA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="AMBA" data-i="77">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >AMBA</span></td>
  <td class="c-name" style="font-size:12px">Ambarella</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$2.5 B</span></td>
  <td class="si-cell si-med" data-si="">~9%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI vision SoC for ADAS, drones, security cameras, robotics; CV3 domain controller
  <button class="dd-btn" onclick="openDD(this,'AMBA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="SYNA" data-i="78">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >SYNA</span></td>
  <td class="c-name" style="font-size:12px">Synaptics</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$1.8 B</span></td>
  <td class="si-cell si-med" data-si="">~11%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Human interface SoCs + IoT wireless + edge AI; recovery play; 11% SI
  <button class="dd-btn" onclick="openDD(this,'SYNA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="MBLY" data-i="79">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >MBLY</span></td>
  <td class="c-name" style="font-size:12px">Mobileye</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$14 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — AV race narrative</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">ADAS + AV chip leader; EyeQ in 100M+ vehicles; SuperVision ADAS; Robotaxi pilot
  <button class="dd-btn" onclick="openDD(this,'MBLY')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="XPEV" data-i="80">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >XPEV</span></td>
  <td class="c-name" style="font-size:12px">XPeng</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$16 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — China EV AV narrative</span> <span class="cam">Camillo: Strong</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China EV + in-house AI/AV chips (Turing); XNGP city-level autonomous driving; VW co-development
  <button class="dd-btn" onclick="openDD(this,'XPEV')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="VPG" data-i="81">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >VPG</span></td>
  <td class="c-name" style="font-size:12px">Vishay Precision Group</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.4 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Force measurement sensors for robotics + industrial weighing; micro-cap deep value in robotics supply chain
  <button class="dd-btn" onclick="openDD(this,'VPG')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="CTS" data-i="82">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >CTS</span></td>
  <td class="c-name" style="font-size:12px">CTS Corporation</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.8 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Sensors + actuators + connectivity for industrial robots, EVs, medical; EV + reshoring dual tailwind
  <button class="dd-btn" onclick="openDD(this,'CTS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="PDYN" data-i="83">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >PDYN</span></td>
  <td class="c-name" style="font-size:12px">Palladyne AI</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.3 B</span></td>
  <td class="si-cell si-hot" data-si="">~20%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-powered autonomous robot software; DoD/defence contracts; 20% SI micro-cap
  <button class="dd-btn" onclick="openDD(this,'PDYN')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="TXN" data-i="84">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >TXN</span></td>
  <td class="c-name" style="font-size:12px">Texas Instruments</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$180 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Analog + embedded chips for humanoid robots; flagged as Optimus robot semiconductor supplier
  <button class="dd-btn" onclick="openDD(this,'TXN')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="MCHP" data-i="85">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >MCHP</span></td>
  <td class="c-name" style="font-size:12px">Microchip Technology</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$25 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">MCUs for robot actuators; flagged as Optimus-like humanoid robot chip supplier; recovery from 2024-25 inventory correction
  <button class="dd-btn" onclick="openDD(this,'MCHP')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ON" data-i="86">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >ON</span></td>
  <td class="c-name" style="font-size:12px">ON Semiconductor</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$20 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">SiC power semiconductors + image sensors for humanoid robots and EVs; EV + robotics dual tailwind
  <button class="dd-btn" onclick="openDD(this,'ON')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Space & Defence" data-ticker="JEDI" data-i="87">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq" >JEDI</span></td>
  <td class="c-name" style="font-size:12px">Defiance Drone &amp; Warfare ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">ETF</span></td>
  <td class="si-cell si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">JC top ETF pick for next 90-120 days; "long weapons short peace" thesis; drone + modern warfare basket
  <button class="dd-btn" onclick="openDD(this,'JEDI')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="RR" data-i="88">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain</td>
  <td class="c-tick"><span class="badge eq" >RR</span></td>
  <td class="c-name" style="font-size:12px">Rolls-Royce Holdings (LSE)</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$45 B</span></td>
  <td class="si-cell si-cell" data-si="">n/a (LSE)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate — UK defence</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Jet engines (Trent XWB) + SMR nuclear + defence; UK defence budget surge; AI-integrated manufacturing
  <button class="dd-btn" onclick="openDD(this,'RR')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Crypto — AI & DePin" data-ticker="PHA" data-i="89">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI & DePin</td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">PHA</span></td>
  <td class="c-name" style="font-size:12px">Phala Network</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$30 M</span></td>
  <td class="si-cell si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">TEE-based private AI inference on-chain; fixed 1B supply; JC's #1 crypto AI inference pick May 2026
  <button class="dd-btn" onclick="openDD(this,'PHA')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Crypto — AI & DePin" data-ticker="VVV" data-i="90">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI & DePin</td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">VVV</span></td>
  <td class="c-name" style="font-size:12px">Venice AI</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">small</span></td>
  <td class="si-cell si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Decentralised private AI inference; deflationary tokenomics; staking ~15% APY + DIEM credits
  <button class="dd-btn" onclick="openDD(this,'VVV')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Crypto — AI & DePin" data-ticker="NEAR" data-i="91">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI & DePin</td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">NEAR</span></td>
  <td class="c-name" style="font-size:12px">NEAR Protocol</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$5 B</span></td>
  <td class="si-cell si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI agent L1 with native chain abstraction; Grayscale product; agent swarms narrative driver
  <button class="dd-btn" onclick="openDD(this,'NEAR')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
<tr data-sector="Crypto — AI & DePin" data-ticker="OLAS" data-i="92">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI & DePin</td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">OLAS</span></td>
  <td class="c-name" style="font-size:12px">Autonolas</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.5 B</span></td>
  <td class="si-cell si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Decentralised autonomous AI agent network; multi-agent coordination on-chain; ~$0.5B mkt cap
  <button class="dd-btn" onclick="openDD(this,'OLAS')" title="Open deep dive">⚡ Deep Dive</button></td>
</tr>
</tbody>
</table>

<p class="note">
  <strong>Price &amp; charts</strong> — Yahoo Finance, ~15min delayed for US equities, ~20min HK/LSE. Auto-refreshes every 90s.
  <strong>Crypto prices</strong> — CoinMarketCap API (PHA, VVV, NEAR, OLAS). Refreshes every 90s.
  <strong>Short interest</strong> — FINRA official data via StockAnalysis; published twice monthly. Figures from May 2026.
  <strong>R/R Score</strong> — Composite 0–100: Valuation 20% · TA composite 30% (RSI · OBV · Fibonacci · SMA 20/50 · EMA MACD · Weekly S/R) · 7D Momentum 15% · News Velocity 15% · Secular Tailwinds 20%. Hover each star badge for live indicator readings. Updated on every price refresh.
  <strong>WSB</strong> — live from Tradestie Reddit API. <strong>4W H/L</strong> — rolling 30 calendar days.
  <strong>Chris Camillo</strong> — qualitative assessment only; no disclosed real-time positions.
</p>

<script>
// ══════════════════════════════════════════════════════════════
// CONFIG
// ══════════════════════════════════════════════════════════════
const TM = {
  'NVDA':'NVDA','MU':'MU','AMD':'AMD','INTC':'INTC','PLTR':'PLTR',
  'CBRS':'CBRS','CRWV':'CRWV','NBIS':'NBIS','BIDU':'BIDU','ORCL':'ORCL',
  'NOW':'NOW','APP':'APP','DDOG':'DDOG','NET':'NET','RDDT':'RDDT',
  'QCOM':'QCOM','VICR':'VICR','GDYN':'GDYN',
  'IONQ':'IONQ','RGTI':'RGTI','QBTS':'QBTS',
  'SNDK':'SNDK','WDC':'WDC','STX':'STX',
  'RKLB':'RKLB','ASTS':'ASTS','LUNR':'LUNR',
  'CCJ':'CCJ','UEC':'UEC','NXE':'NXE',
  'MSTR':'MSTR','COIN':'COIN','HOOD':'HOOD','CRCL':'CRCL',
  'GLXY':'GLXY','DFDV':'DFDV','BABA':'BABA',
  'HIMS':'HIMS','RXRX':'RXRX','CMPS':'CMPS','GHRS':'GHRS',
  'AMSC':'AMSC','HIMX':'HIMX','APLD':'APLD',
  'TSLA':'TSLA','AMZN':'AMZN','ISRG':'ISRG','PRCT':'PRCT',
  'ROK':'ROK','SYM':'SYM','ZBRA':'ZBRA','CGNX':'CGNX',
  'MOD':'MOD','TER':'TER','ALNT':'ALNT','NOVT':'NOVT',
  'OUST':'OUST','AEVA':'AEVA','AMBA':'AMBA','SYNA':'SYNA',
  'MBLY':'MBLY','XPEV':'XPEV','VPG':'VPG','CTS':'CTS','PDYN':'PDYN',
  'HK: 700':'0700.HK','HK: 1810':'1810.HK',
  'HK: 9992':'9992.HK','HK: 0100':'0100.HK',
  'RR':'RR.L',
  'AVGO':'AVGO','ALAB':'ALAB','VRT':'VRT','VST':'VST',
  'CRDO':'CRDO','DELL':'DELL','SNOW':'SNOW','CRWD':'CRWD',
  'ZS':'ZS','FTNT':'FTNT','SPCE':'SPCE','TXN':'TXN',
  'MCHP':'MCHP','ON':'ON','HACK':'HACK','QTUM':'QTUM',
  'JEDI':'JEDI','NOWL':'NOWL','SKM':'SKM'
};

// Crypto tokens fetched via CMC (separate flow)
const CMC_TICKERS = ['PHA','VVV','NEAR','OLAS'];
const CMC_SLUGS = { 'PHA':'phala-network', 'VVV':'venice-token', 'NEAR':'near-protocol', 'OLAS':'autonolas' };

const WSB_URL = 'https://tradestie.com/api/v1/apps/reddit';
let wsbData = {};
let sortCol = -1, sortAsc = true, activeF = 'all';

// ══════════════════════════════════════════════════════════════
// RISK-REWARD SCORE ENGINE
// Valuation 30% · Momentum 25% · News Velocity 20% · Secular Tailwinds 25%
// ══════════════════════════════════════════════════════════════
const RR_STATIC = {
  'NVDA': {fpe:35,  tailwind:10, news:9},  'MU':   {fpe:12,  tailwind:9,  news:8},
  'AMD':  {fpe:28,  tailwind:9,  news:7},  'INTC': {fpe:22,  tailwind:7,  news:8},
  'PLTR': {fpe:110, tailwind:10, news:9},  'CBRS': {fpe:999, tailwind:9,  news:10},
  'CRWV': {fpe:80,  tailwind:9,  news:7},  'NBIS': {fpe:45,  tailwind:8,  news:7},
  'BIDU': {fpe:9,   tailwind:6,  news:5},  'ORCL': {fpe:24,  tailwind:8,  news:6},
  'NOW':  {fpe:38,  tailwind:8,  news:6},  'APP':  {fpe:32,  tailwind:8,  news:7},
  'DDOG': {fpe:55,  tailwind:7,  news:6},  'NET':  {fpe:65,  tailwind:7,  news:6},
  'RDDT': {fpe:90,  tailwind:7,  news:7},  'QCOM': {fpe:14,  tailwind:7,  news:6},
  'VICR': {fpe:28,  tailwind:7,  news:5},  'GDYN': {fpe:22,  tailwind:6,  news:5},
  'IONQ': {fpe:999, tailwind:8,  news:7},  'RGTI': {fpe:999, tailwind:7,  news:6},
  'QBTS': {fpe:999, tailwind:7,  news:6},  'SNDK': {fpe:18,  tailwind:8,  news:7},
  'WDC':  {fpe:15,  tailwind:7,  news:5},  'STX':  {fpe:14,  tailwind:6,  news:4},
  'RKLB': {fpe:120, tailwind:9,  news:9},  'ASTS': {fpe:999, tailwind:8,  news:8},
  'LUNR': {fpe:999, tailwind:7,  news:5},  'CCJ':  {fpe:28,  tailwind:8,  news:6},
  'UEC':  {fpe:35,  tailwind:7,  news:5},  'NXE':  {fpe:null,tailwind:7,  news:5},
  'MSTR': {fpe:null,tailwind:8,  news:8},  'COIN': {fpe:20,  tailwind:8,  news:8},
  'HOOD': {fpe:22,  tailwind:7,  news:7},  'CRCL': {fpe:null,tailwind:8,  news:7},
  'GLXY': {fpe:null,tailwind:7,  news:6},  'DFDV': {fpe:null,tailwind:7,  news:6},
  'BABA': {fpe:10,  tailwind:7,  news:7},  'HIMS': {fpe:35,  tailwind:9,  news:8},
  'RXRX': {fpe:999, tailwind:7,  news:6},  'CMPS': {fpe:999, tailwind:7,  news:6},
  'GHRS': {fpe:999, tailwind:6,  news:5},  'AMSC': {fpe:30,  tailwind:6,  news:5},
  'HIMX': {fpe:12,  tailwind:5,  news:5},  'APLD': {fpe:40,  tailwind:7,  news:6},
  'TSLA': {fpe:65,  tailwind:9,  news:9},  'AMZN': {fpe:30,  tailwind:9,  news:7},
  'ISRG': {fpe:55,  tailwind:8,  news:7},  'PRCT': {fpe:60,  tailwind:7,  news:6},
  'NOVT': {fpe:30,  tailwind:7,  news:5},  'ROK':  {fpe:22,  tailwind:7,  news:5},
  'SYM':  {fpe:80,  tailwind:8,  news:7},  'ZBRA': {fpe:20,  tailwind:6,  news:5},
  'CGNX': {fpe:35,  tailwind:7,  news:6},  'MOD':  {fpe:18,  tailwind:7,  news:5},
  'TER':  {fpe:28,  tailwind:7,  news:5},  'ALNT': {fpe:20,  tailwind:7,  news:6},
  'OUST': {fpe:999, tailwind:7,  news:6},  'AEVA': {fpe:999, tailwind:7,  news:6},
  'AMBA': {fpe:45,  tailwind:7,  news:6},  'SYNA': {fpe:18,  tailwind:6,  news:5},
  'MBLY': {fpe:30,  tailwind:8,  news:6},  'XPEV': {fpe:25,  tailwind:8,  news:7},
  'VPG':  {fpe:15,  tailwind:5,  news:3},  'CTS':  {fpe:14,  tailwind:5,  news:3},
  'PDYN': {fpe:999, tailwind:7,  news:6},  'AVGO': {fpe:28,  tailwind:9,  news:8},
  'ALAB': {fpe:55,  tailwind:9,  news:7},  'VRT':  {fpe:30,  tailwind:9,  news:7},
  'VST':  {fpe:18,  tailwind:7,  news:6},  'CRDO': {fpe:50,  tailwind:9,  news:8},
  'DELL': {fpe:16,  tailwind:9,  news:9},  'SNOW': {fpe:55,  tailwind:7,  news:7},
  'CRWD': {fpe:50,  tailwind:8,  news:7},  'ZS':   {fpe:35,  tailwind:8,  news:6},
  'FTNT': {fpe:30,  tailwind:8,  news:6},  'SPCE': {fpe:999, tailwind:6,  news:7},
  'TXN':  {fpe:22,  tailwind:7,  news:5},  'MCHP': {fpe:16,  tailwind:7,  news:5},
  'ON':   {fpe:18,  tailwind:7,  news:5},  'SKM':  {fpe:10,  tailwind:5,  news:4},
  'PHA':  {fpe:null,tailwind:9,  news:9},  'VVV':  {fpe:null,tailwind:8,  news:8},
  'NEAR': {fpe:null,tailwind:8,  news:7},  'OLAS': {fpe:null,tailwind:7,  news:7},
  // ETFs — valuation not applicable, use tailwind + news only, no fpe
  'HACK': {fpe:null,tailwind:8,  news:7},  'QTUM': {fpe:null,tailwind:8,  news:6},
  'JEDI': {fpe:null,tailwind:8,  news:7},  'NOWL': {fpe:null,tailwind:8,  news:8},
  'URA':  {fpe:null,tailwind:8,  news:5},  'DRAM': {fpe:null,tailwind:8,  news:6},
  'HK: 700':  {fpe:15, tailwind:7, news:6}, 'HK: 1810': {fpe:20, tailwind:8, news:7},
  'HK: 9992': {fpe:25, tailwind:8, news:8}, 'HK: 0100': {fpe:30, tailwind:7, news:7},
};


// ══════════════════════════════════════════════════════════════
// SUPERINVESTOR POSITION RENDERER
// ══════════════════════════════════════════════════════════════
const SUPERINV = {
  'NVDA': {
    trump: {s:'watch', d:'No direct position; export controls concern'},
    gavin: {s:'bull', d:'Core Atreides holding since 2020; top 3 position'},
    leopald: {s:'watch', d:'No 13F position; publicly bullish on AI infra'}
  },
  'MU': {
    trump: null,
    gavin: {s:'bull', d:'Atreides significant position; AI memory supercycle thesis'},
    leopald: null
  },
  'AMD': {
    trump: null,
    gavin: {s:'bull', d:'Atreides top 5 holding; MI300X key to thesis'},
    leopald: null
  },
  'INTC': {
    trump: {s:'bull', d:'CHIPS Act recipient; national security framing aligns'},
    gavin: {s:'watch', d:'Reduced position; monitoring foundry pivot'},
    leopald: {s:'watch', d:'Watching turnaround thesis; no confirmed 13F position'}
  },
  'PLTR': {
    trump: {s:'bull', d:'Personal position disclosed; DoD/AIP contracts beneficiary'},
    gavin: {s:'bull', d:'Atreides meaningful position; AIP platform believer'},
    leopald: null
  },
  'CBRS': {
    trump: null,
    gavin: {s:'bull', d:'Atreides IPO allocation; AI chip alternative thesis'},
    leopald: null
  },
  'CRWV': {
    trump: null,
    gavin: {s:'bull', d:'Atreides position; AI cloud infra direct exposure'},
    leopald: null
  },
  'NBIS': {
    trump: null,
    gavin: {s:'bull', d:'Atreides early position; European AI cloud squeeze play'},
    leopald: null
  },
  'BIDU': {
    trump: {s:'bear', d:'China tech adversary framing; export restrictions'},
    gavin: null,
    leopald: null
  },
  'ORCL': {
    trump: null,
    gavin: {s:'watch', d:'Cloud infra exposure; not core Atreides holding'},
    leopald: {s:'bull', d:'Pershing Square interested in AI cloud; watching Oracle'}
  },
  'NOW': {
    trump: null,
    gavin: {s:'bull', d:'Atreides long SaaS-to-agents transition; NOW key platform'},
    leopald: null
  },
  'APP': {
    trump: null,
    gavin: {s:'bull', d:'Atreides position; AXON AI ad revenue trackable'},
    leopald: null
  },
  'DDOG': {
    trump: null,
    gavin: {s:'bull', d:'Atreides position; AI observability essential infra'},
    leopald: null
  },
  'NET': {
    trump: null,
    gavin: {s:'watch', d:'Watching AI inference edge narrative develop'},
    leopald: null
  },
  'RDDT': {
    trump: null,
    gavin: {s:'watch', d:'Watching AI data licensing monetisation'},
    leopald: null
  },
  'QCOM': {
    trump: {s:'watch', d:'On-device AI; Snapdragon chip aligns with US semiconductor policy'},
    gavin: {s:'watch', d:'Monitoring Snapdragon X cycle; not core position'},
    leopald: null
  },
  'VICR': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'GDYN': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'AVGO': {
    trump: null,
    gavin: {s:'bull', d:'Atreides holding; custom AI ASIC thesis for hyperscalers'},
    leopald: {s:'bull', d:'Pershing Square has expressed interest in AVGO AI custom chip story'}
  },
  'ALAB': {
    trump: null,
    gavin: {s:'bull', d:'Atreides conviction position; PCIe/CXL AI connectivity essential'},
    leopald: null
  },
  'VRT': {
    trump: null,
    gavin: {s:'bull', d:'Atreides significant position; AI data centre thermal mgmt supercycle'},
    leopald: null
  },
  'CRDO': {
    trump: null,
    gavin: {s:'bull', d:'Atreides position; AI rack-scale SerDes/AEC connectivity play'},
    leopald: null
  },
  'DELL': {
    trump: {s:'bull', d:'Publicly told followers to buy DELL May 2026; AI server narrative'},
    gavin: {s:'bull', d:'Atreides position; AI server OEM undervalued vs hyperscalers'},
    leopald: null
  },
  'SNOW': {
    trump: null,
    gavin: {s:'bull', d:'Atreides long; SaaS-per-token repricing is core thesis'},
    leopald: {s:'watch', d:'Pershing watching SaaS rotation; no confirmed SNOW position'}
  },
  'CRWD': {
    trump: null,
    gavin: {s:'bull', d:'Atreides position; AI-native cyber moat rebuilt post-outage'},
    leopald: {s:'bull', d:'Pershing Square position in cybersecurity basket confirmed'}
  },
  'ZS': {
    trump: null,
    gavin: {s:'bull', d:'Atreides high-conviction contrarian; 50% drawdown + 26% growth'},
    leopald: {s:'watch', d:'Watching zero-trust security narrative; no position confirmed'}
  },
  'FTNT': {
    trump: null,
    gavin: {s:'bull', d:'Atreides cheapest quality cyber; ~30x PE for 80% gross margins'},
    leopald: null
  },
  'SKM': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'IONQ': {
    trump: null,
    gavin: {s:'watch', d:'Atreides monitoring quantum; not yet core position'},
    leopald: null
  },
  'RGTI': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'QBTS': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'SNDK': {
    trump: null,
    gavin: {s:'bull', d:'Atreides NAND flash supercycle thesis; AI SSD demand'},
    leopald: null
  },
  'WDC': {
    trump: null,
    gavin: {s:'watch', d:'Watching post-spinoff SNDK/WDC dynamic'},
    leopald: null
  },
  'STX': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'RKLB': {
    trump: {s:'bull', d:'Personal position disclosed in financial filings; Space Force advocate'},
    gavin: {s:'watch', d:'Monitoring space infra; not core Atreides position'},
    leopald: null
  },
  'ASTS': {
    trump: {s:'bull', d:'Personal position disclosed in financial filings alongside RKLB'},
    gavin: {s:'watch', d:'Watching satellite connectivity narrative'},
    leopald: null
  },
  'LUNR': {
    trump: {s:'watch', d:'NASA/DoD contracts; lunar policy interest'},
    gavin: null,
    leopald: null
  },
  'SPCE': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'CCJ': {
    trump: {s:'bull', d:'Nuclear energy executive orders; "beautiful clean coal and nuclear"'},
    gavin: {s:'watch', d:'Watching nuclear renaissance timing'},
    leopald: null
  },
  'UEC': {
    trump: {s:'bull', d:'US domestic uranium = energy independence narrative'},
    gavin: null,
    leopald: null
  },
  'NXE': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'VST': {
    trump: {s:'bull', d:'Signed power purchase agreements with hyperscalers; aligns with AI energy policy'},
    gavin: {s:'watch', d:'Monitoring AI power demand; power generator exposure'},
    leopald: null
  },
  'MSTR': {
    trump: {s:'bull', d:'Strategic Bitcoin Reserve executive order; BTC bull publicly'},
    gavin: {s:'bull', d:'Atreides position; leveraged BTC exposure thesis'},
    leopald: {s:'watch', d:'Ackman publicly pro-crypto but prefers direct BTC exposure'}
  },
  'COIN': {
    trump: {s:'bull', d:'Crypto Clarity Act support; met with Coinbase leadership'},
    gavin: {s:'bull', d:'Atreides meaningful position; regulatory clarity direct beneficiary'},
    leopald: {s:'watch', d:'Pershing watching Clarity Act passage as entry catalyst'}
  },
  'HOOD': {
    trump: null,
    gavin: {s:'watch', d:'Watching retail brokerage crypto + prediction market expansion'},
    leopald: null
  },
  'CRCL': {
    trump: {s:'bull', d:'USDC/stablecoin regulation supportive; Clarity Act champion'},
    gavin: {s:'watch', d:'Watching stablecoin IPO; not yet in portfolio'},
    leopald: null
  },
  'GLXY': {
    trump: null,
    gavin: {s:'watch', d:'Watching crypto merchant bank expansion'},
    leopald: null
  },
  'DFDV': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'BABA': {
    trump: {s:'bear', d:'China tech; trade tensions; previous adversarial stance'},
    gavin: {s:'watch', d:'US-China thaw opens window; watching carefully'},
    leopald: {s:'bull', d:'Pershing Square active in deep-value China internet thesis; BABA fits'}
  },
  'HK: 700': {
    trump: {s:'bear', d:'China tech; WeChat sanctions risk history'},
    gavin: {s:'watch', d:'Watching China AI re-rating on US-China thaw'},
    leopald: {s:'bull', d:'Pershing Square China internet value thesis'}
  },
  'HK: 1810': {
    trump: null,
    gavin: {s:'watch', d:'SU7 EV consumer data trackable'},
    leopald: null
  },
  'HK: 9992': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'HK: 0100': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'HIMS': {
    trump: null,
    gavin: null,
    leopald: {s:'watch', d:'Watching GLP-1 branded telehealth; short squeeze dynamics interesting'}
  },
  'RXRX': {
    trump: null,
    gavin: {s:'watch', d:'AI drug discovery adjacent to Atreides biotech interest'},
    leopald: null
  },
  'CMPS': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'GHRS': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'AMSC': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'HIMX': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'APLD': {
    trump: null,
    gavin: {s:'watch', d:'AI data centre narrative; monitoring'},
    leopald: null
  },
  'HACK': {
    trump: null,
    gavin: {s:'bull', d:'Cybersecurity basket aligns with Atreides cyber holdings'},
    leopald: null
  },
  'QTUM': {
    trump: null,
    gavin: {s:'watch', d:'Quantum basket ETF; monitoring theme development'},
    leopald: null
  },
  'NOWL': {
    trump: null,
    gavin: {s:'bull', d:'2x leveraged NOW — amplifies Atreides SaaS-agents conviction'},
    leopald: null
  },
  'TSLA': {
    trump: {s:'bull', d:'Elon ally; DOGE role; public TSLA cheerleader; held in DOGE-adjacent circles'},
    gavin: {s:'watch', d:'Watching Optimus robot mass production; not core Atreides position'},
    leopald: {s:'watch', d:'Pershing watching robotics story; Ackman has commented on TSLA valuation'}
  },
  'AMZN': {
    trump: null,
    gavin: {s:'bull', d:'Atreides position; warehouse robotics + AWS AI + Kuiper'},
    leopald: {s:'bull', d:'Pershing Square major AMZN position; AWS AI thesis'}
  },
  'ISRG': {
    trump: null,
    gavin: {s:'bull', d:'Atreides surgical robotics conviction; 85% recurring revenue moat'},
    leopald: null
  },
  'PRCT': {
    trump: null,
    gavin: {s:'watch', d:'Fastest-growing surgical robot; monitoring 18% SI squeeze'},
    leopald: null
  },
  'NOVT': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'ROK': {
    trump: {s:'watch', d:'US re-shoring manufacturing narrative'},
    gavin: null,
    leopald: null
  },
  'SYM': {
    trump: null,
    gavin: {s:'bull', d:'Atreides position; Walmart anchor + AI warehouse automation compounding'},
    leopald: null
  },
  'ZBRA': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'CGNX': {
    trump: null,
    gavin: {s:'watch', d:'Machine vision recovery + JPM upgrade catalyst'},
    leopald: null
  },
  'MOD': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'TER': {
    trump: null,
    gavin: {s:'watch', d:'Semi ATE + UR cobots dual exposure; monitoring'},
    leopald: null
  },
  'ALNT': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'OUST': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'AEVA': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'AMBA': {
    trump: null,
    gavin: {s:'watch', d:'Edge AI vision SoC; automotive design-win cycle building'},
    leopald: null
  },
  'SYNA': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'MBLY': {
    trump: null,
    gavin: {s:'watch', d:'ADAS/AV chip leader; monitoring Intel spin path'},
    leopald: null
  },
  'XPEV': {
    trump: {s:'bear', d:'China EV; trade tariff target'},
    gavin: {s:'watch', d:'Watching XNGP AV + Turing chip; China tech thaw upside'},
    leopald: null
  },
  'VPG': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'CTS': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'PDYN': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'TXN': {
    trump: {s:'watch', d:'US semiconductor supply chain; analog chips for reshoring'},
    gavin: {s:'watch', d:'Humanoid robot analog chip supplier; monitoring cyclical recovery'},
    leopald: null
  },
  'MCHP': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'ON': {
    trump: null,
    gavin: {s:'watch', d:'SiC + image sensors for EV + robots; monitoring'},
    leopald: null
  },
  'JEDI': {
    trump: {s:'bull', d:'Drone warfare + Golden Dome defence spending beneficiary'},
    gavin: null,
    leopald: null
  },
  'RR': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'PHA': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'VVV': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'NEAR': {
    trump: null,
    gavin: null,
    leopald: null
  },
  'OLAS': {
    trump: null,
    gavin: null,
    leopald: null
  },
};

function renderSuperInv(ticker) {
  const pos = SUPERINV[ticker];
  if (!pos) return '';
 
  const investors = [
    { key: 'trump',   label: 'Trump',   icon: '🇺🇸' },
    { key: 'gavin',   label: 'G.Baker', icon: '📈' },
    { key: 'leopald', label: 'Leopald', icon: '🦁' },
  ];
 
  const pills = investors.map(inv => {
    const p = pos[inv.key];
    if (!p) return `<span class="si-pill si-none" title="${inv.label}: No known position">${inv.icon} ${inv.label}</span>`;
    const cls = p.s === 'bull' ? 'si-bull' : p.s === 'bear' ? 'si-bear' : 'si-watch';
    const icon = p.s === 'bull' ? '▲' : p.s === 'bear' ? '▼' : '◆';
    return `<span class="si-pill ${cls}" title="${inv.label}: ${p.d}">${inv.icon} ${inv.label} ${icon}</span>`;
  }).join('');
 
  return `<div class="si-row">${pills}</div>`;
}

function fpeToScore(fpe) {
  if (!fpe || fpe >= 500) return 2;
  if (fpe <= 10) return 10; if (fpe <= 15) return 9; if (fpe <= 20) return 8;
  if (fpe <= 25) return 7;  if (fpe <= 35) return 6; if (fpe <= 50) return 5;
  if (fpe <= 70) return 4;  if (fpe <= 100) return 3; return 2;
}

function momentumScore(last7) {
  if (!last7 || last7.length < 2) return 5; // neutral until we have data
  const pct = (last7[last7.length-1] - last7[0]) / last7[0] * 100;
  const clamped = Math.max(-10, Math.min(10, pct));
  return Math.round((clamped + 10) / 2);
}

// Returns 0–100. Called with last7=[] for static render (momentum defaults to 5).
// ══════════════════════════════════════════════════════════════
// TECHNICAL ANALYSIS INDICATORS (RSI · OBV · Fibonacci · SMA · EMA · Weekly S/R)
// ══════════════════════════════════════════════════════════════
// ══════════════════════════════════════════════════════════════
// TECHNICAL ANALYSIS MODULE
// Computes RSI, OBV, Fibonacci, SMA, EMA, Weekly S/R from OHLCV
// Each indicator returns a sub-score 0–10 for the R/R composite
// ══════════════════════════════════════════════════════════════

// ── EMA helper ────────────────────────────────────────────────
function calcEMA(data, period) {
  if (!data || data.length < period) return [];
  const k = 2 / (period + 1);
  const result = [];
  // seed with SMA of first `period` points
  let seed = 0;
  for (let i = 0; i < period; i++) seed += data[i];
  result[period - 1] = seed / period;
  for (let i = period; i < data.length; i++) {
    result[i] = data[i] * k + result[i - 1] * (1 - k);
  }
  return result;
}

// ── SMA helper ────────────────────────────────────────────────
function calcSMA(data, period) {
  const result = [];
  for (let i = 0; i < data.length; i++) {
    if (i < period - 1) { result.push(null); continue; }
    let sum = 0;
    for (let j = i - period + 1; j <= i; j++) sum += data[j];
    result.push(sum / period);
  }
  return result;
}

// ── RSI(14) → score 0–10 ─────────────────────────────────────
// Oversold (<30) = bullish setup = high score
// Overbought (>70) = extended = low score
// 40–60 = neutral = 5
function calcRSI(closes, period = 14) {
  if (!closes || closes.length < period + 1) return { rsi: null, score: 5 };
  let gains = 0, losses = 0;
  for (let i = 1; i <= period; i++) {
    const diff = closes[i] - closes[i - 1];
    if (diff >= 0) gains += diff; else losses -= diff;
  }
  let avgGain = gains / period;
  let avgLoss = losses / period;
  for (let i = period + 1; i < closes.length; i++) {
    const diff = closes[i] - closes[i - 1];
    const g = diff >= 0 ? diff : 0;
    const l = diff < 0 ? -diff : 0;
    avgGain = (avgGain * (period - 1) + g) / period;
    avgLoss = (avgLoss * (period - 1) + l) / period;
  }
  const rs = avgLoss === 0 ? 100 : avgGain / avgLoss;
  const rsi = 100 - (100 / (1 + rs));

  // Score: deeply oversold=best entry, overbought=worst
  let score;
  if (rsi <= 25)      score = 9.5;
  else if (rsi <= 30) score = 8.5;
  else if (rsi <= 40) score = 7;
  else if (rsi <= 50) score = 5.5;
  else if (rsi <= 60) score = 5;
  else if (rsi <= 70) score = 3.5;
  else if (rsi <= 80) score = 2;
  else                score = 1;
  return { rsi: Math.round(rsi * 10) / 10, score };
}

// ── OBV trend (14-day slope normalised) → score 0–10 ─────────
function calcOBV(closes, volumes) {
  if (!closes || !volumes || closes.length < 2) return { slope: null, score: 5 };
  const obv = [0];
  for (let i = 1; i < closes.length; i++) {
    const v = volumes[i] || 0;
    obv.push(closes[i] > closes[i-1] ? obv[i-1] + v
           : closes[i] < closes[i-1] ? obv[i-1] - v
           : obv[i-1]);
  }
  // Use last 14 points for slope via linear regression
  const n = Math.min(14, obv.length);
  const recent = obv.slice(-n);
  let sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0;
  for (let i = 0; i < n; i++) {
    sumX += i; sumY += recent[i];
    sumXY += i * recent[i]; sumX2 += i * i;
  }
  const slope = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
  // Normalise slope relative to mean OBV magnitude
  const mean = Math.abs(sumY / n) || 1;
  const normSlope = slope / mean; // dimensionless
  // Map to 0-10: strongly rising (+2% per bar) = 9, flat = 5, falling = 1
  const score = Math.max(1, Math.min(10, 5 + normSlope * 250));
  return { slope: Math.round(normSlope * 10000) / 100, score: Math.round(score * 10) / 10 };
}

// ── Fibonacci retracement → score 0–10 ───────────────────────
// Uses full range in data as hi/lo (approximates 52W with 6mo data)
// Price near 0.618 retracement = strong support = high score
// Price at/above high = extended = lower score
function calcFibScore(closes) {
  if (!closes || closes.length < 20) return { level: null, score: 5 };
  const hi = Math.max(...closes);
  const lo = Math.min(...closes);
  const range = hi - lo;
  if (range === 0) return { level: null, score: 5 };
  const price = closes[closes.length - 1];
  const pos = (price - lo) / range; // 0 = at low, 1 = at high

  // Fib retracement levels from high (pullback from high)
  // 0.236 pullback = price at 76.4% of range
  // 0.382 pullback = price at 61.8% of range  ← golden zone top
  // 0.500 pullback = price at 50% of range    ← fair value
  // 0.618 pullback = price at 38.2% of range  ← golden zone bottom (best buy)
  // 0.786 pullback = price at 21.4% of range
  // Score: near golden zone (0.36–0.42 pos) = high; at high or near low = moderate
  let score;
  if      (pos >= 0.95)             score = 3;   // at/near all-time high — extended
  else if (pos >= 0.85)             score = 4;   // above 0.236 retracement
  else if (pos >= 0.72)             score = 5.5; // between 0.236 and 0.382
  else if (pos >= 0.55)             score = 7;   // near 0.382–0.5 retracement ← decent entry
  else if (pos >= 0.34 && pos < 0.44) score = 9; // golden zone (0.618 retrace) ← ideal
  else if (pos >= 0.20)             score = 7.5; // between 0.618 and 0.786
  else                              score = 5;   // deep retracement / near lows (uncertainty)

  const fibLabel = pos >= 0.95 ? 'At High'
    : pos >= 0.85 ? '0.236 retrace'
    : pos >= 0.72 ? '0.382 retrace'
    : pos >= 0.55 ? '0.5 retrace'
    : pos >= 0.34 ? '0.618 Golden'
    : pos >= 0.20 ? '0.786 retrace'
    : 'Near Low';

  return { level: fibLabel, pos: Math.round(pos * 100), score };
}

// ── SMA 20 / 50 → score 0–10 ──────────────────────────────────
// Golden cross (SMA20 > SMA50, both rising) = 9-10
// Death cross = 1-2
// Price above both SMAs + slopes up = bullish
function calcSMAScore(closes) {
  if (!closes || closes.length < 50) return { cross: null, score: 5 };
  const sma20 = calcSMA(closes, 20);
  const sma50 = calcSMA(closes, 50);
  const n = closes.length - 1;
  const price = closes[n];
  const s20 = sma20[n], s50 = sma50[n];
  const s20prev = sma20[n - 3], s50prev = sma50[n - 3]; // 3-bar slope check
  if (!s20 || !s50) return { cross: null, score: 5 };

  const rising20 = s20 > s20prev;
  const rising50 = s50 > s50prev;
  const priceAbove20 = price > s20;
  const priceAbove50 = price > s50;
  const goldenCross = s20 > s50;

  let score = 5;
  if (goldenCross && rising20 && rising50 && priceAbove20 && priceAbove50) score = 9;
  else if (goldenCross && priceAbove20 && priceAbove50) score = 7.5;
  else if (goldenCross && priceAbove50) score = 6.5;
  else if (goldenCross) score = 5.5;
  else if (!goldenCross && !priceAbove20 && !priceAbove50 && !rising20) score = 2;
  else if (!goldenCross && priceAbove20) score = 4; // price above 20 but death cross
  else score = 3;

  return {
    cross: goldenCross ? 'golden' : 'death',
    priceVs20: priceAbove20 ? 'above' : 'below',
    priceVs50: priceAbove50 ? 'above' : 'below',
    sma20: Math.round(s20 * 100) / 100,
    sma50: Math.round(s50 * 100) / 100,
    score
  };
}

// ── EMA 12/26 (MACD signal direction) → score 0–10 ───────────
function calcEMAScore(closes) {
  if (!closes || closes.length < 30) return { macd: null, score: 5 };
  const ema12 = calcEMA(closes, 12);
  const ema26 = calcEMA(closes, 26);
  const n = closes.length - 1;
  const e12 = ema12[n], e26 = ema26[n];
  const e12p = ema12[n-3], e26p = ema26[n-3];
  if (!e12 || !e26) return { macd: null, score: 5 };

  const macd = e12 - e26;
  const macdPrev = (e12p - e26p) || 0;
  const crossingUp = macdPrev < 0 && macd >= 0;
  const crossingDown = macdPrev > 0 && macd <= 0;
  const rising = macd > macdPrev;

  let score;
  if (crossingUp)         score = 9;   // bullish MACD crossover
  else if (macd > 0 && rising) score = 7.5;
  else if (macd > 0)      score = 6;
  else if (crossingDown)  score = 2;   // bearish crossover
  else if (macd < 0 && !rising) score = 2.5;
  else                    score = 4;

  return {
    macd: Math.round(macd * 1000) / 1000,
    direction: rising ? 'rising' : 'falling',
    crossover: crossingUp ? 'bullish' : crossingDown ? 'bearish' : null,
    score
  };
}

// ── Weekly S/R from weekly OHLC → score 0–10 ─────────────────
// Score based on: price near weekly support = high; near resistance = moderate
// Calculated from weekly candle H/L clusters over last 12 weeks
function calcWeeklySRScore(weeklyHighs, weeklyLows, currentPrice) {
  if (!weeklyHighs || weeklyHighs.length < 3 || !currentPrice) return { level: null, score: 5 };

  // Collect all weekly H/L as S/R level candidates
  const levels = [...weeklyHighs, ...weeklyLows];
  const priceRange = currentPrice * 0.03; // 3% tolerance band

  // Find levels within 3% of current price
  const nearby = levels.filter(l => Math.abs(l - currentPrice) / currentPrice <= 0.03);
  const nearSupport = weeklyLows.filter(l => l <= currentPrice && (currentPrice - l) / currentPrice <= 0.04);
  const nearResistance = weeklyHighs.filter(l => l >= currentPrice && (l - currentPrice) / currentPrice <= 0.04);

  // Recent key levels: last 4 weeks are more significant
  const recentLow = Math.min(...weeklyLows.slice(-4));
  const recentHigh = Math.max(...weeklyHighs.slice(-4));
  const distFromRecentLow = (currentPrice - recentLow) / recentLow;
  const distFromRecentHigh = (recentHigh - currentPrice) / recentHigh;

  // Score logic:
  // Sitting on strong weekly support (just above recent weekly low) = 8+
  // Testing resistance from below = 4 (breakout needed)
  // Just broke above resistance = 8
  // Far from both = 5
  let score = 5;
  if (nearSupport.length >= 2 && distFromRecentLow < 0.05) score = 8.5; // multiple support levels below
  else if (nearSupport.length >= 1 && distFromRecentLow < 0.04) score = 7.5;
  else if (nearResistance.length >= 1 && distFromRecentHigh < 0.02) score = 4; // testing resistance
  else if (distFromRecentLow < 0.08 && distFromRecentHigh > 0.12) score = 6.5; // in lower third, room to run
  else if (distFromRecentHigh < 0.03) score = 3.5; // near recent high
  else score = 5;

  return {
    nearSupport: nearSupport.length,
    nearResistance: nearResistance.length,
    distLow: Math.round(distFromRecentLow * 100),
    distHigh: Math.round(distFromRecentHigh * 100),
    score
  };
}

// ── Master TA scorer → returns taScore 0–10 and breakdown ────
// Weights within TA block:
//   RSI 22% | OBV 18% | Fibonacci 20% | SMA 20% | EMA/MACD 10% | Weekly S/R 10%
function computeTAScore(closes, volumes, weeklyHighs, weeklyLows) {
  const n = closes ? closes.length : 0;
  if (n < 15) return { score: 5, breakdown: null }; // insufficient data

  const rsiR   = calcRSI(closes);
  const obvR   = calcOBV(closes, volumes);
  const fibR   = calcFibScore(closes);
  const smaR   = calcSMAScore(closes);
  const emaR   = calcEMAScore(closes);
  const srR    = calcWeeklySRScore(weeklyHighs, weeklyLows, closes[n-1]);

  const taScore = rsiR.score  * 0.22
                + obvR.score  * 0.18
                + fibR.score  * 0.20
                + smaR.score  * 0.20
                + emaR.score  * 0.10
                + srR.score   * 0.10;

  return {
    score: Math.round(taScore * 10) / 10,
    rsi:   rsiR,
    obv:   obvR,
    fib:   fibR,
    sma:   smaR,
    ema:   emaR,
    sr:    srR
  };
}


// Returns 0–100. Called with empty arrays for static seed (TA defaults to 5).
// Weights: Valuation 20% | TA composite 30% | 7D Momentum 15% | News 15% | Tailwinds 20%
function computeRRScore(ticker, last7, closes, volumes, weeklyHighs, weeklyLows) {
  const s = RR_STATIC[ticker];
  if (!s) return null;
  const valScore  = fpeToScore(s.fpe);
  const momScore  = momentumScore(last7);
  const newsScore = s.news;
  const tailScore = s.tailwind;
  const ta = computeTAScore(closes||[], volumes||[], weeklyHighs||[], weeklyLows||[]);
  const taScore = ta.score;
  const composite = valScore  * 0.20
                  + taScore   * 0.30
                  + momScore  * 0.15
                  + newsScore * 0.15
                  + tailScore * 0.20;
  const finalScore = Math.round(composite * 10);
  computeRRScore._lastTA = ta;  // stash breakdown for tooltip
  return finalScore;
}

// Convert 0-100 score → 1-5 stars (with half-star granularity via Unicode)
function scoreToStars(score) {
  if (score === null) return null;
  // Map 0-100 → 1.0-5.0
  const raw = 1 + (score / 100) * 4;
  const full = Math.floor(raw);
  const half = (raw - full) >= 0.4 ? 1 : 0;
  const empty = 5 - full - half;
  return {
    stars: raw.toFixed(1),
    full, half, empty,
    label: raw >= 4.3 ? 'Strong' : raw >= 3.5 ? 'Good' : raw >= 2.6 ? 'Neutral' : raw >= 1.8 ? 'Weak' : 'Poor'
  };
}

// Render stars — uses CSS vars so dark mode works automatically
function renderRRScore(score, ta) {
  if (score === null) return '<span style="color:var(--text4);font-size:10px">n/a</span>';
  const {stars, full, half, empty, label} = scoreToStars(score);

  const starFull  = '<span class="star star-full">★</span>';
  const starHalf  = '<span class="star star-half">⯨</span>';
  const starEmpty = '<span class="star star-empty">☆</span>';
  const starHtml = starFull.repeat(full) + starHalf.repeat(half) + starEmpty.repeat(empty);

  const labelClass = score>=75 ? 'rr-strong' : score>=60 ? 'rr-good' : score>=45 ? 'rr-neutral' : score>=30 ? 'rr-weak' : 'rr-poor';

  // Build rich TA tooltip
  let tip = `R/R ${score}/100 (${stars}★)`;
  if (ta && ta.breakdown !== null) {
    if (ta.rsi?.rsi  != null) tip += `\nRSI(14): ${ta.rsi.rsi} → ${ta.rsi.score.toFixed(1)}/10`;
    if (ta.obv?.slope != null) tip += `\nOBV slope: ${ta.obv.slope>0?'+':''}${ta.obv.slope}% → ${ta.obv.score.toFixed(1)}/10`;
    if (ta.fib?.level) tip += `\nFib: ${ta.fib.level} (${ta.fib.pos}%) → ${ta.fib.score.toFixed(1)}/10`;
    if (ta.sma?.cross) tip += `\nSMA: ${ta.sma.cross} cross · price ${ta.sma.priceVs50} 50d → ${ta.sma.score.toFixed(1)}/10`;
    if (ta.ema?.macd  != null) tip += `\nMACD: ${ta.ema.direction}${ta.ema.crossover?' ('+ta.ema.crossover+' crossover)':''} → ${ta.ema.score.toFixed(1)}/10`;
    if (ta.sr?.distLow != null) tip += `\nWeekly S/R: ${ta.sr.distLow}% above support → ${ta.sr.score.toFixed(1)}/10`;
  }

  // Compact TA sub-indicators row beneath stars (only when live data available)
  let taRow = '';
  if (ta && ta.rsi?.rsi != null) {
    const rsiCol = ta.rsi.rsi <= 30 ? '#22c55e' : ta.rsi.rsi >= 70 ? '#ef4444' : 'var(--text3)';
    const smaLabel = ta.sma?.cross === 'golden' ? '↑SMA' : ta.sma?.cross === 'death' ? '↓SMA' : 'SMA';
    const smaCol = ta.sma?.cross === 'golden' ? '#22c55e' : ta.sma?.cross === 'death' ? '#ef4444' : 'var(--text3)';
    const emaLabel = ta.ema?.crossover === 'bullish' ? '↑MACD' : ta.ema?.crossover === 'bearish' ? '↓MACD' : (ta.ema?.direction === 'rising' ? '↗MACD' : '↘MACD');
    const emaCol = (ta.ema?.crossover === 'bullish' || ta.ema?.direction === 'rising') ? '#22c55e' : '#ef4444';
    const fibCol = ta.fib?.score >= 8 ? '#22c55e' : ta.fib?.score >= 6 ? 'var(--text3)' : '#ef4444';
    taRow = `<div class="rr-ta-row">` +
      `<span style="color:${rsiCol}" title="RSI(14): ${ta.rsi.rsi}">RSI ${ta.rsi.rsi}</span>` +
      `<span style="color:${smaCol}" title="SMA cross: ${ta.sma?.cross||'n/a'}">${smaLabel}</span>` +
      `<span style="color:${emaCol}" title="MACD: ${ta.ema?.direction||'n/a'}">${emaLabel}</span>` +
      `<span style="color:${fibCol}" title="Fib: ${ta.fib?.level||'n/a'}">${ta.fib?.level||'Fib'}</span>` +
      `</div>`;
  }

  return `<div class="rr-badge" data-score="${score}" title="${tip}">
    <div class="rr-stars">${starHtml}</div>
    <div class="rr-stars-num ${labelClass}">${stars}</div>
    ${taRow}
  </div>`;
}

// ══════════════════════════════════════════════════════════════
// FETCH
// ══════════════════════════════════════════════════════════════
const PROXIES = [
  sym => `https://query1.finance.yahoo.com/v8/finance/chart/${sym}?interval=1d&range=30d`,
  sym => `https://query2.finance.yahoo.com/v8/finance/chart/${sym}?interval=1d&range=30d`,
  sym => `https://corsproxy.io/?url=${encodeURIComponent('https://query1.finance.yahoo.com/v8/finance/chart/'+sym+'?interval=1d&range=30d')}`,
  sym => `https://api.allorigins.win/raw?url=${encodeURIComponent('https://query1.finance.yahoo.com/v8/finance/chart/'+sym+'?interval=1d&range=30d')}`,
];

async function fetchTicker(sym) {
  // Try two fetches: 6mo daily (for TA indicators) + 3mo weekly (for S/R levels)
  for (const proxyFn of PROXIES) {
    try {
      // Primary: 6-month daily OHLCV — enough for RSI(14), SMA(50), EMA(26), OBV, Fib
      const url = proxyFn(sym).replace('range=30d', 'range=6mo');
      const r = await fetch(url, {
        headers: {'Accept':'application/json','User-Agent':'Mozilla/5.0'},
        signal: AbortSignal.timeout(8000)
      });
      if (!r.ok) continue;
      const j = await r.json();
      const res = j?.chart?.result?.[0];
      if (!res) continue;
      const m = res.meta;
      if (!m?.regularMarketPrice) continue;

      const q = res.indicators?.quote?.[0] || {};
      const closes  = (q.close  || []).filter((v,i,a) => v != null ? true : (a[i]=null, false)).map((v,i) => v ?? null);
      const highs   = (q.high   || []);
      const lows    = (q.low    || []);
      const volumes = (q.volume || []);

      // Clean: keep only rows where close is non-null
      const clean = { c:[], h:[], l:[], v:[] };
      for (let i = 0; i < closes.length; i++) {
        if (closes[i] == null) continue;
        clean.c.push(closes[i]);
        clean.h.push(highs[i]   ?? closes[i]);
        clean.l.push(lows[i]    ?? closes[i]);
        clean.v.push(volumes[i] ?? 0);
      }

      const hi4w = clean.c.length ? Math.max(...clean.c.slice(-30)) : null;
      const lo4w = clean.c.length ? Math.min(...clean.c.slice(-30)) : null;
      const last7 = clean.c.slice(-7);
      const prev = m.chartPreviousClose || m.previousClose;

      // Fetch weekly candles for S/R (last 3 months weekly)
      let weeklyHighs = [], weeklyLows = [];
      try {
        const wUrl = proxyFn(sym).replace('range=30d', 'range=3mo').replace('interval=1d', 'interval=1wk');
        const wr = await fetch(wUrl, {
          headers: {'Accept':'application/json','User-Agent':'Mozilla/5.0'},
          signal: AbortSignal.timeout(6000)
        });
        if (wr.ok) {
          const wj = await wr.json();
          const wq = wj?.chart?.result?.[0]?.indicators?.quote?.[0] || {};
          weeklyHighs = (wq.high || []).filter(v => v != null);
          weeklyLows  = (wq.low  || []).filter(v => v != null);
        }
      } catch(e) { /* weekly fetch optional */ }

      return {
        price: m.regularMarketPrice,
        prev, shares: m.sharesOutstanding,
        ccy: m.currency || 'USD',
        hi4w, lo4w, last7,
        chgPct: prev ? (m.regularMarketPrice - prev) / prev * 100 : null,
        // Full OHLCV for TA
        closes:  clean.c,
        highs:   clean.h,
        lows:    clean.l,
        volumes: clean.v,
        weeklyHighs, weeklyLows
      };
    } catch(e) { continue; }
  }
  return null;
}

// CMC API for crypto prices — uses CoinGecko as fallback (CORS-friendly)
const CMC_SLUGS_MAP = { 'PHA':'phala-network', 'VVV':'venice-token', 'NEAR':'near', 'OLAS':'autonolas' };

async function fetchCryptoPrice(ticker) {
  const slug = CMC_SLUGS_MAP[ticker];
  if (!slug) return null;
  // Try CoinGecko (public, no key needed)
  const urls = [
    `https://api.coingecko.com/api/v3/coins/${slug}?localization=false&tickers=false&market_data=true&community_data=false&developer_data=false`,
    `https://corsproxy.io/?url=${encodeURIComponent('https://api.coingecko.com/api/v3/coins/'+slug+'?localization=false&tickers=false&market_data=true&community_data=false&developer_data=false')}`,
  ];
  for (const url of urls) {
    try {
      const r = await fetch(url, {signal: AbortSignal.timeout(10000)});
      if (!r.ok) continue;
      const j = await r.json();
      const md = j?.market_data;
      if (!md) continue;
      const price = md.current_price?.usd;
      const prev24h = price && md.price_change_percentage_24h !== undefined
        ? price / (1 + md.price_change_percentage_24h/100) : null;
      const mc = md.market_cap?.usd;
      // Build last7 from 7d sparkline if available
      const last7 = [];
      if (md.sparkline_7d?.price?.length) {
        const sp = md.sparkline_7d.price;
        // Sample 7 evenly spaced points
        for (let i=0;i<7;i++) {
          const idx = Math.floor(i*(sp.length-1)/6);
          last7.push(sp[idx]);
        }
      }
      return {
        price, prev: prev24h, shares: null, ccy:'USD',
        hi4w: md.high_24h?.usd || price, lo4w: md.low_24h?.usd || price,
        last7: last7.length ? last7 : (price ? [price] : []),
        chgPct: md.price_change_percentage_24h ?? null,
        mcapDirect: mc
      };
    } catch(e) { continue; }
  }
  return null;
}

async function fetchWSB() {
  try {
    const r = await fetch(WSB_URL);
    if (!r.ok) return {};
    const arr = await r.json();
    const out = {};
    arr.forEach((x,i) => { out[x.ticker]={rank:i+1,mentions:x.no_of_comments,sentiment:x.sentiment}; });
    return out;
  } catch(e) { return {}; }
}

// ══════════════════════════════════════════════════════════════
// FORMAT
// ══════════════════════════════════════════════════════════════
function fPrice(v, ccy) {
  if (v == null) return '—';
  if (ccy==='GBp') return v.toFixed(0)+'p';
  const s = ccy==='HKD'?'HK$':'$';
  return s+(v<10?v.toFixed(4):v<100?v.toFixed(3):v.toFixed(2));
}
function fMcap(v, ccy) {
  if (!v) return '';
  const s = ccy==='GBp'?'£':ccy==='HKD'?'HK$':'$';
  if (v>=1e12) return s+(v/1e12).toFixed(2)+'T';
  if (v>=1e9)  return s+(v/1e9).toFixed(1)+'B';
  if (v>=1e6)  return s+(v/1e6).toFixed(0)+'M';
  return s+v.toFixed(0);
}
function fChg(p) {
  if (p==null) return '<span class="flat">—</span>';
  const c = p>0.05?'pos':p<-0.05?'neg':'flat';
  return `<span class="${c}">${p>0?'+':''}${p.toFixed(2)}%</span>`;
}

// ══════════════════════════════════════════════════════════════
// SPARKLINE
// ══════════════════════════════════════════════════════════════
function drawSpark(canvas, closes) {
  if (!closes||closes.length<2) {
    const ctx=canvas.getContext('2d');
    ctx.clearRect(0,0,canvas.width,canvas.height);
    ctx.fillStyle='#ddd';ctx.font='9px system-ui';ctx.fillText('no data',4,20);
    return;
  }
  const W=canvas.width,H=canvas.height,pad=4;
  const ctx=canvas.getContext('2d');
  ctx.clearRect(0,0,W,H);
  const mn=Math.min(...closes),mx=Math.max(...closes);
  const range=mx-mn||mx*0.02||1;
  const up=closes[closes.length-1]>=closes[0];
  const colour=up?'#16a34a':'#dc2626';
  const xs=closes.map((_,i)=>pad+i*(W-pad*2)/(closes.length-1));
  const ys=closes.map(v=>H-pad-(v-mn)/range*(H-pad*2));
  ctx.beginPath();ctx.moveTo(xs[0],H-pad);
  xs.forEach((x,i)=>ctx.lineTo(x,ys[i]));
  ctx.lineTo(xs[xs.length-1],H-pad);ctx.closePath();
  ctx.fillStyle=up?'rgba(22,163,74,0.12)':'rgba(220,38,38,0.10)';ctx.fill();
  ctx.beginPath();ctx.moveTo(xs[0],ys[0]);
  for(let i=1;i<xs.length;i++)ctx.lineTo(xs[i],ys[i]);
  ctx.strokeStyle=colour;ctx.lineWidth=2;ctx.lineJoin='round';ctx.stroke();
  ctx.beginPath();ctx.arc(xs[xs.length-1],ys[ys.length-1],3,0,Math.PI*2);
  ctx.fillStyle=colour;ctx.fill();
  const pct=((closes[closes.length-1]-closes[0])/closes[0]*100);
  ctx.fillStyle=colour;ctx.font='bold 9px system-ui';ctx.textAlign='right';
  ctx.fillText((pct>0?'+':'')+pct.toFixed(1)+'%',W-2,10);ctx.textAlign='left';
  canvas.title=closes.map((v,i)=>`Day ${i+1}: ${v.toFixed(4)}`).join(' | ');
}

// ══════════════════════════════════════════════════════════════
// UPDATE ROW  (col indices: 0=sec,1=tick,2=name,3=price,4=mc,5=si,6=chg,7=hl,8=spark,9=rr,10=soc,11=thesis)
// ══════════════════════════════════════════════════════════════
function updateRow(badge, sym, d) {
  const rows = document.querySelectorAll('#wtb tr');
  for (const row of rows) {
    const b = row.querySelector('.badge');
    if (!b||b.textContent.trim()!==badge) continue;
    const ccy = d.ccy;
    const mcap = d.mcapDirect || (d.shares ? d.price * d.shares : null);
    const now = Date.now();
    const tsHtml = `<span class="ts-wrap fresh" data-ts="${now}">${fmtAgo(now)}</span>`;

    // Price
    const pc = row.cells[3];
    pc.dataset.p = d.price||0;
    pc.dataset.ts = now;
    pc.innerHTML = `<span class="live-p">${fPrice(d.price,ccy)}</span>${tsHtml}`;

    // Mkt Cap
    const mc = row.cells[4];
    mc.dataset.mc2 = mcap||0;
    mc.dataset.ts = now;
    mc.innerHTML = `<span class="mc-val">${fMcap(mcap,ccy)||'—'}</span>${tsHtml}`;

    // Day change
    const cc = row.cells[6];
    cc.dataset.chg = d.chgPct??'';
    cc.dataset.ts = now;
    cc.innerHTML = fChg(d.chgPct) + tsHtml;

    // 4W H/L
    const hlc = row.cells[7];
    if (d.hi4w&&d.lo4w) {
      const fill = d.hi4w!==d.lo4w ? Math.max(0,Math.min(100,Math.round((d.price-d.lo4w)/(d.hi4w-d.lo4w)*100))) : 50;
      hlc.dataset.hi=d.hi4w; hlc.dataset.lo=d.lo4w; hlc.dataset.ts=now;
      hlc.innerHTML=`<span class="hl-hi">${fPrice(d.hi4w,ccy)}</span><span class="hl-lo"> / ${fPrice(d.lo4w,ccy)}</span><div class="hl-pbar"><div class="hl-pfill" style="width:${fill}%"></div></div>${tsHtml}`;
    }

    // Sparkline
    const sc = row.cells[8];
    const canvas = sc.querySelector('canvas.spark');
    if (canvas&&d.last7&&d.last7.length) {
      sc.dataset.closes = JSON.stringify(d.last7);
      sc.dataset.ts = now;
      drawSpark(canvas, d.last7);
    }

    // Risk-Reward Score (col 9) — recompute with full OHLCV for TA indicators
    const rrc = row.cells[9];
    if (rrc) {
      const score = computeRRScore(badge, d.last7||[], d.closes||[], d.volumes||[], d.weeklyHighs||[], d.weeklyLows||[]);
      const taBreakdown = computeRRScore._lastTA;
      rrc.dataset.rr = score??'';
      rrc.innerHTML = renderRRScore(score, taBreakdown);
    }

    // WSB live badge + superinvestor pills (col 10)
    const cleanSym = sym.replace('.HK','').replace('.L','');
    const wd = wsbData[cleanSym];
    const socialCell = row.cells[10];
    if (socialCell) {
      const wsbHtml = wd
        ? `<span class="wsb-live" style="background:${wd.sentiment==='Bullish'?'#16a34a':'#dc2626'}">#${wd.rank} · ${wd.mentions} mentions · ${wd.sentiment}</span>`
        : `<span class="wsb-live none">not in WSB top 50</span>`;
      const existing = socialCell.querySelector('.wsb-live');
      if (existing) existing.outerHTML = wsbHtml;
      else socialCell.innerHTML = wsbHtml + '<br>' + socialCell.innerHTML;

      // Superinvestor pills — inject/replace
      const existingSI = socialCell.querySelector('.si-row');
      const siHtml = renderSuperInv(badge);
      if (existingSI) existingSI.outerHTML = siHtml;
      else if (siHtml) socialCell.insertAdjacentHTML('beforeend', siHtml);
    }
    break;
  }
}

// ══════════════════════════════════════════════════════════════
// REFRESH
// ══════════════════════════════════════════════════════════════
async function refresh() {
  setDot('loading','Fetching live data…');
  wsbData = await fetchWSB();

  // Equity tickers
  const entries = Object.entries(TM);
  for (let i=0;i<entries.length;i+=6) {
    const batch = entries.slice(i,i+6);
    await Promise.all(batch.map(async ([badge,sym]) => {
      const d = await fetchTicker(sym);
      if (d) updateRow(badge,sym,d);
    }));
    if (i+6<entries.length) await new Promise(r=>setTimeout(r,220));
  }

  // Crypto tokens via CoinGecko
  for (const ticker of ['PHA','VVV','NEAR','OLAS']) {
    const d = await fetchCryptoPrice(ticker);
    if (d) updateRow(ticker, ticker, d);
  }

  const t = new Date().toLocaleTimeString();
  document.getElementById('lupd').textContent = t;
  setDot('live','Live · '+t);
}

function setDot(state,msg) {
  const d=document.getElementById('sdot');
  const t=document.getElementById('stxt');
  if(d)d.className='dot '+state;
  if(t)t.textContent=msg;
}

// ══════════════════════════════════════════════════════════════
// SORT
// ══════════════════════════════════════════════════════════════
function srt(col) {
  const tbody = document.getElementById('wtb');
  const rows = Array.from(tbody.querySelectorAll('tr'));
  const ths = document.querySelectorAll('#wt thead th');
  ths.forEach(h=>h.classList.remove('asc','desc'));
  const asc = sortCol===col ? !sortAsc : true;
  sortCol=col; sortAsc=asc;
  ths[col].classList.add(asc?'asc':'desc');
  rows.sort((a,b)=>{
    let av=getVal(a,col),bv=getVal(b,col);
    const an=parseFloat(av),bn=parseFloat(bv);
    if(!isNaN(an)&&!isNaN(bn)){av=an;bv=bn;}
    return av<bv?(asc?-1:1):av>bv?(asc?1:-1):0;
  });
  tbody.append(...rows);
  updateCount();
}

function getVal(row,col) {
  const c=row.cells[col];
  if(!c)return'';
  switch(col){
    case 3:return c.dataset.p||'0';
    case 4:return c.dataset.mc2||'0';
    case 5:{const t=c.innerText.replace(/[^0-9.]/g,'');return t||'0';}
    case 6:return c.dataset.chg||'0';
    case 7:return c.dataset.hi||'0';
    case 9:return c.dataset.rr||'0';
    default:return c.innerText.trim().toLowerCase();
  }
}

// ══════════════════════════════════════════════════════════════
// FILTER + SEARCH
// ══════════════════════════════════════════════════════════════
function filt(btn) {
  document.querySelectorAll('.fbtn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  activeF=btn.dataset.f;
  applyFilters();
}
function applyFilters() {
  const q=(document.getElementById('srch').value||'').toLowerCase().trim();
  document.querySelectorAll('#wtb tr').forEach(row=>{
    const sec=row.dataset.sector||'';
    const txt=row.innerText.toLowerCase();
    const sm=activeF==='all'||sec===activeF;
    const qm=!q||txt.includes(q);
    row.classList.toggle('hide',!(sm&&qm));
  });
  updateCount();
}
function updateCount() {
  const total=document.querySelectorAll('#wtb tr').length;
  const visible=document.querySelectorAll('#wtb tr:not(.hide)').length;
  const el=document.getElementById('rcnt');
  if(el)el.textContent=visible===total?total+' stocks':visible+' / '+total+' stocks';
}

// ══════════════════════════════════════════════════════════════
// DEEP DIVE ENGINE
// ══════════════════════════════════════════════════════════════
const DD_CACHE = {};
const DD_COL_COUNT = 12;

function openDD(btn,ticker) {
  const row=btn.closest('tr');
  const existingDD=row.nextElementSibling;
  if(existingDD&&existingDD.classList.contains('dd-row')){
    const isOpen=existingDD.classList.contains('visible');
    existingDD.classList.toggle('visible',!isOpen);
    btn.classList.toggle('open',!isOpen);
    btn.textContent=isOpen?'⚡ Deep Dive':'✕ Close';
    return;
  }
  const ddRow=document.createElement('tr');
  ddRow.className='dd-row visible';
  ddRow.innerHTML=`<td class="dd-cell" colspan="${DD_COL_COUNT}"><div class="dd-panel" id="ddp-${ticker.replace(/[^a-zA-Z0-9]/g,'_')}"><div class="dd-loading"><div class="dd-spinner"></div>Researching ${ticker} — pulling SEC filings, earnings calls, insider trades, superinvestor positions…</div></div></td>`;
  row.after(ddRow);
  btn.classList.add('open');
  btn.textContent='✕ Close';
  const panelId='ddp-'+ticker.replace(/[^a-zA-Z0-9]/g,'_');
  if(DD_CACHE[ticker]){document.getElementById(panelId).innerHTML=DD_CACHE[ticker];}
  else{fetchDeepDive(ticker);}
}

async function fetchDeepDive(ticker) {
  const panelId='ddp-'+ticker.replace(/[^a-zA-Z0-9]/g,'_');
  const panel=document.getElementById(panelId);
  if(!panel)return;
  const rows=document.querySelectorAll('#wtb tr[data-ticker]');
  let staticContext='';
  for(const r of rows){
    if(r.dataset.ticker===ticker){
      const cells=r.cells;
      const name=cells[2]?.innerText||'';
      const price=cells[3]?.innerText||'';
      const mcap=cells[4]?.innerText||'';
      const si=cells[5]?.innerText||'';
      const chg=cells[6]?.innerText||'';
      const rrScore=cells[9]?.dataset?.rr||'';
      const thesis=cells[11]?.innerText?.replace('⚡ Deep Dive','').replace('✕ Close','').trim()||'';
      staticContext=`Stock: ${ticker} (${name}) | Price: ${price} | Mkt Cap: ${mcap} | SI: ${si} | Day Chg: ${chg} | R/R Score: ${rrScore}/100\nCurrent thesis: ${thesis}`;
      break;
    }
  }
  const systemPrompt=`You are a senior equity analyst inspired by Charlie Munger. Write structured, evidence-based deep dives. Every thesis point must have an antithesis. Cite sources: SEC filing, earnings call, podcast, blog post, insider trade, 13F. Be specific with dates, amounts, names.

OUTPUT FORMAT: Respond ONLY with valid JSON (no markdown, no backticks):
{"name":"","verdict":"bull|bear|neutral","verdict_label":"","confidence":75,"summary":"","last_updated":"","thesis_points":[{"point":"","source_type":"earnings","source_detail":"","antithesis":""}],"superinvestors":[{"name":"","action":"","stance":"bull|bear|watch","source":""}],"insider_trades":[{"person":"","action":"","date":"","signal":""}],"catalysts":[{"event":"","timeline":"","impact":"bull|bear"}],"thesis_killers":[""],"metrics":[{"label":"","value":"","context":""}]}`;
  const userPrompt=`Deep dive: ${ticker}\nContext: ${staticContext}\nToday: ${new Date().toLocaleDateString('en-US',{month:'long',year:'numeric'})}\nInclude 5-7 thesis points with antithesis, 3-5 superinvestors, key insider trades, 3-4 catalysts, 3-4 thesis killers, 5-6 metrics.`;
  try {
    const res=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:2000,system:systemPrompt,messages:[{role:'user',content:userPrompt}]})
    });
    if(!res.ok)throw new Error('API '+res.status);
    const data=await res.json();
    const raw=data.content?.[0]?.text||'';
    const clean=raw.replace(/^```json\s*/,'').replace(/\s*```$/,'').trim();
    const dd=JSON.parse(clean);
    DD_CACHE[ticker]=renderDeepDive(dd,ticker);
    if(panel)panel.innerHTML=DD_CACHE[ticker];
  } catch(err){
    if(panel)panel.innerHTML=`<div style="padding:16px;color:#888;font-size:12px"><strong>Deep dive unavailable</strong> — ${err.message}<br><small>Anthropic API key may not be present. Host on a server or open in Claude.ai.</small><button class="dd-regen" style="margin-top:8px" onclick="fetchDeepDive('${ticker}')">↻ Retry</button></div>`;
  }
}

function renderDeepDive(dd,ticker) {
  const confPct=Math.min(100,Math.max(0,dd.confidence||50));
  const tRows=(dd.thesis_points||[]).map(t=>`<li><span class="src src-${t.source_type||'news'}">${srcLabel(t.source_type)}</span><span style="font-size:10px;color:#888">${t.source_detail||''}</span><br><strong>${t.point}</strong><div style="margin-top:4px;padding:6px 8px;background:#fff7f7;border-left:2px solid #fca5a5;border-radius:0 4px 4px 0;font-size:10px;color:#666;line-height:1.5"><span style="color:#dc2626;font-weight:600">↙ Bear:</span> ${t.antithesis}</div></li>`).join('');
  const siRows=(dd.superinvestors||[]).map(s=>`<span class="inv-tag inv-${s.stance}">${s.name} — ${s.action}</span>`).join('');
  const insRows=(dd.insider_trades||[]).map(i=>`<li><strong>${i.person}</strong> — ${i.action} <span style="color:#888">(${i.date})</span><br><span style="font-size:10px;color:#666">${i.signal}</span></li>`).join('');
  const catRows=(dd.catalysts||[]).map(c=>`<li><span style="display:inline-block;width:8px;height:8px;border-radius:50%;background:${c.impact==='bull'?'#16a34a':'#dc2626'};margin-right:5px"></span><strong>${c.timeline}</strong> — ${c.event}</li>`).join('');
  const killRows=(dd.thesis_killers||[]).map(k=>`<li>☠ ${k}</li>`).join('');
  const metRows=(dd.metrics||[]).map(m=>`<tr><td style="font-size:10px;color:#888;padding:4px 8px 4px 0;white-space:nowrap">${m.label}</td><td style="font-size:11px;font-weight:700;padding:4px 8px 4px 0">${m.value}</td><td style="font-size:10px;color:#888;padding:4px 0">${m.context||''}</td></tr>`).join('');
  return `<div class="dd-header"><span class="dd-title">${dd.name||ticker}</span><span class="dd-verdict ${dd.verdict}">${dd.verdict_label||dd.verdict}</span><span class="dd-updated">Deep Dive · ${dd.last_updated||'Q2 2026'}</span><button class="dd-regen" onclick="DD_CACHE['${ticker}']=null;fetchDeepDive('${ticker}')">↻ Refresh</button></div><div class="conf-bar"><span style="font-size:10px;color:#888;white-space:nowrap">Conviction ${confPct}%</span><div class="conf-track"><div class="conf-fill" style="width:${confPct}%"></div></div></div><div class="dd-summary" style="margin-top:12px">${dd.summary||''}</div><div class="dd-section-full"><h4>📊 Key Metrics</h4><table style="width:100%;border-collapse:collapse"><tbody>${metRows}</tbody></table></div><div class="dd-ta-grid"><div class="dd-thesis-box"><h4>🟢 Thesis — Bull Case</h4><ul>${tRows}</ul></div><div class="dd-anti-box"><h4>🔴 Antithesis — Steelmanned Bear Case</h4><ul>${(dd.thesis_points||[]).map(t=>`<li>${t.antithesis}</li>`).join('')}</ul></div></div><div class="dd-grid"><div class="dd-section"><h4>👑 Superinvestors</h4><div style="display:flex;flex-wrap:wrap;gap:4px">${siRows||'<span style="color:#bbb;font-size:11px">No major 13F positions found</span>'}</div></div><div class="dd-section"><h4>🏦 Recent Insider Trades</h4><ul>${insRows||'<li style="color:#bbb">No significant insider activity</li>'}</ul></div><div class="dd-section"><h4>⚡ Upcoming Catalysts</h4><ul>${catRows}</ul></div><div class="dd-section" style="border-color:#fecaca"><h4 style="color:#991b1b">☠ Thesis Killers</h4><ul style="color:#991b1b">${killRows}</ul></div></div>`;
}

function srcLabel(type) {
  const map={sec:'SEC',earnings:'ER',podcast:'POD',blog:'BLOG',insider:'INSIDER',super:'13F',news:'NEWS'};
  return map[type]||(type||'').toUpperCase().slice(0,6);
}

// ══════════════════════════════════════════════════════════════
// DARK MODE
// ══════════════════════════════════════════════════════════════
function initTheme() {
  const saved = localStorage.getItem('wl-theme');
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  const theme = saved || (prefersDark ? 'dark' : 'light');
  applyTheme(theme);
}
function applyTheme(theme) {
  document.documentElement.setAttribute('data-theme', theme);
  const lbl = document.getElementById('dm-label');
  if (lbl) lbl.textContent = theme === 'dark' ? 'Dark' : 'Light';
  localStorage.setItem('wl-theme', theme);
}

// ══════════════════════════════════════════════════════════════
// ADD TICKER
// ══════════════════════════════════════════════════════════════
async function addTicker() {
  const tickerRaw = (document.getElementById('add-ticker').value || '').trim().toUpperCase();
  const name      = (document.getElementById('add-name').value   || '').trim() || tickerRaw;
  const sector    = document.getElementById('add-sector').value;
  const notes     = (document.getElementById('add-notes').value  || '').trim();
  const status    = document.getElementById('add-status');

  if (!tickerRaw) { status.textContent = '⚠ Enter a ticker'; status.style.color='var(--neg)'; return; }

  // Check for dupe
  if (document.querySelector(`#wtb tr[data-ticker="${tickerRaw}"]`)) {
    status.textContent = `${tickerRaw} already on list`; status.style.color='var(--text3)'; return;
  }

  status.textContent = `Fetching ${tickerRaw}…`; status.style.color='var(--text3)';

  // Try equity first; fall back to crypto
  let priceData = null;
  const isCrypto = ['PHA','VVV','NEAR','OLAS','BTC','ETH','SOL','BNB','ADA','DOT','LINK','AVAX','MATIC','XRP'].includes(tickerRaw);
  if (isCrypto) {
    priceData = await fetchCryptoPrice(tickerRaw);
  } else {
    priceData = await fetchTicker(tickerRaw);
  }

  // Build a new row
  const tbody = document.getElementById('wtb');
  const idx = tbody.querySelectorAll('tr').length;
  const row = document.createElement('tr');
  row.dataset.sector = sector;
  row.dataset.ticker = tickerRaw;
  row.dataset.i = idx;
  row.classList.add('user-added');

  const badgeCls = tickerRaw.includes(':') ? 'hk' : 'new';
  const thesisHtml = notes ? `<em style="color:var(--text3);font-size:10px">${notes}</em><br>` : '';

  row.innerHTML = `
  <td class="c-sec">${sector}</td>
  <td class="c-tick"><span class="badge ${badgeCls}">${tickerRaw}</span></td>
  <td class="c-name">${name}</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">—</span></td>
  <td class="si-cell" data-si="">—</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36"></canvas></td>
  <td class="c-rr" data-rr=""><span class="dim" style="font-size:10px">—</span></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb-live none">user-added</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">${thesisHtml}User-added asset
  <button class="dd-btn" onclick="openDD(this,'${tickerRaw}')" title="Open deep dive">⚡ Deep Dive</button>
  <button class="dd-btn" onclick="removeRow(this,'${tickerRaw}')" style="background:transparent;border:1px solid var(--border2);color:var(--text3);margin-left:4px" title="Remove">✕</button>
  </td>`;

  tbody.appendChild(row);

  // Inject price data if available
  if (priceData) {
    updateRow(tickerRaw, tickerRaw, priceData);
    status.textContent = `✓ ${tickerRaw} added`; status.style.color='var(--pos)';
  } else {
    // Add to TM for future refreshes (equity)
    if (!isCrypto) TM[tickerRaw] = tickerRaw;
    status.textContent = `${tickerRaw} added (no price data)`; status.style.color='var(--text3)';
  }

  // Clear inputs
  document.getElementById('add-ticker').value = '';
  document.getElementById('add-name').value   = '';
  document.getElementById('add-notes').value  = '';
  updateCount();
  setTimeout(() => { status.textContent = ''; }, 4000);
}

function removeRow(btn, ticker) {
  const row = btn.closest('tr');
  // Also remove any open DD row
  const next = row.nextElementSibling;
  if (next && next.classList.contains('dd-row')) next.remove();
  row.remove();
  delete TM[ticker];
  delete DD_CACHE[ticker];
  updateCount();
}

// ══════════════════════════════════════════════════════════════
// TIMESTAMP HELPERS
// ══════════════════════════════════════════════════════════════
function fmtAgo(ts) {
  if (!ts) return '';
  const sec = Math.round((Date.now() - ts) / 1000);
  if (sec < 5)   return 'just now';
  if (sec < 60)  return `${sec}s ago`;
  if (sec < 3600) return `${Math.floor(sec/60)}m ago`;
  return `${Math.floor(sec/3600)}h ago`;
}

// Refresh all visible timestamp labels every 15 seconds
function tickTimestamps() {
  const now = Date.now();
  document.querySelectorAll('.ts-wrap[data-ts]').forEach(el => {
    const ts = parseInt(el.dataset.ts, 10);
    if (!ts) return;
    el.textContent = fmtAgo(ts);
    const age = (now - ts) / 1000;
    el.className = 'ts-wrap' + (age < 120 ? ' fresh' : age > 600 ? ' stale' : '');
  });
}

// ══════════════════════════════════════════════════════════════
// STATIC SUPERINV SEED — render pills immediately on page load
// ══════════════════════════════════════════════════════════════
function seedSuperInvPills() {
  document.querySelectorAll('#wtb tr[data-ticker]').forEach(row => {
    const ticker = row.dataset.ticker;
    const socialCell = row.cells[10];
    if (!socialCell) return;
    if (socialCell.querySelector('.si-row')) return; // already rendered
    const siHtml = renderSuperInv(ticker);
    if (siHtml) socialCell.insertAdjacentHTML('beforeend', siHtml);
  });
}

// ══════════════════════════════════════════════════════════════
// STATIC R/R SEED  — render stars on page load without waiting for price fetch
// ══════════════════════════════════════════════════════════════
function seedRRScores() {
  document.querySelectorAll('#wtb tr[data-ticker]').forEach(row => {
    const ticker = row.dataset.ticker;
    const rrc = row.cells[9];
    if (!rrc || rrc.dataset.rr) return; // already populated
    const score = computeRRScore(ticker, []); // momentum=5 (neutral) until live data
    if (score !== null) {
      rrc.dataset.rr = score;
      rrc.innerHTML = renderRRScore(score);
    }
  });
}

// ══════════════════════════════════════════════════════════════
// INIT
// ══════════════════════════════════════════════════════════════
document.addEventListener('DOMContentLoaded',()=>{
  initTheme();
  document.getElementById('dm-toggle').addEventListener('click', () => {
    const cur = document.documentElement.getAttribute('data-theme');
    applyTheme(cur === 'dark' ? 'light' : 'dark');
  });
  // Enter key in ticker input
  document.getElementById('add-ticker').addEventListener('keydown', e => { if(e.key==='Enter') addTicker(); });
  updateCount();
  seedRRScores();          // show stars immediately from static data
  seedSuperInvPills();     // show investor pills immediately
  refresh();               // then update with live prices + momentum
  setInterval(refresh, 90000);
  setInterval(tickTimestamps, 15000); // rolling "X ago" labels
});
</script>
<!-- R/R METHODOLOGY MODAL -->
<div id="rr-modal" onclick="if(event.target===this)this.style.display='none'">
  <div class="modal-box">
    <button class="modal-close" onclick="document.getElementById('rr-modal').style.display='none'">✕</button>

    <h2>Risk / Reward Score — Methodology</h2>
    <div class="modal-sub">Composite 0–100 · Displayed as 1–5 stars · Updated on every price refresh</div>

    <p>The R/R Score is a quantitative first-pass filter, not a recommendation. It combines five independently scored pillars — including six live technical indicators — into a single weighted composite designed to surface asymmetric setups worth deeper investigation.</p>

    <h3>The Five Pillars</h3>
    <div class="factor-grid">
      <div class="factor-card">
        <div class="fc-header"><span class="fc-name">Valuation</span><span class="fc-weight">20%</span></div>
        <p>Forward P/E mapped to 0–10 via a non-linear decay curve. Cheap beats expensive; unprofitable companies floor at 2/10. See table below.</p>
      </div>
      <div class="factor-card">
        <div class="fc-header"><span class="fc-name">Technical Analysis</span><span class="fc-weight">30%</span></div>
        <p>Composite of six live indicators computed from 6-month daily OHLCV + 12-week weekly candles. RSI 22% · OBV 18% · Fibonacci 20% · SMA 20% · EMA/MACD 10% · Weekly S/R 10%. See breakdown below.</p>
      </div>
      <div class="factor-card">
        <div class="fc-header"><span class="fc-name">7D Momentum</span><span class="fc-weight">15%</span></div>
        <p>7-day closing price trend. −10% → 0/10, flat → 5/10, +10% → 10/10. Defaults to neutral (5) before live data loads.</p>
      </div>
      <div class="factor-card">
        <div class="fc-header"><span class="fc-name">News Velocity</span><span class="fc-weight">15%</span></div>
        <p>Analyst-assigned 0–10 reflecting current density of catalytic news: earnings beats, upgrades, contracts, regulatory events. Updated weekly.</p>
      </div>
      <div class="factor-card">
        <div class="fc-header"><span class="fc-name">Secular Tailwinds</span><span class="fc-weight">20%</span></div>
        <p>Structural macro alignment: AI build-out, nuclear, robotics, crypto clarity, defence re-arming, re-shoring. Updated quarterly; slow-moving by design.</p>
      </div>
    </div>

    <h3>Composite Formula</h3>
    <p style="font-family:var(--mono);font-size:11px;background:var(--bg2);padding:10px 14px;border-radius:3px;border:1px solid var(--border);letter-spacing:.01em;line-height:1.8">
      score = round( (Val×0.20 + TA×0.30 + Mom×0.15 + News×0.15 + Tail×0.20) × 10 )<br>
      <span style="color:var(--text3)">TA = RSI×0.22 + OBV×0.18 + Fib×0.20 + SMA×0.20 + EMA×0.10 + WeeklySR×0.10</span>
    </p>

    <h3>Technical Indicator Breakdown</h3>
    <table class="pe-table">
      <thead><tr><th>Indicator</th><th>Weight in TA</th><th>Signal logic</th><th>Data source</th></tr></thead>
      <tbody>
        <tr><td>RSI(14)</td><td>22%</td><td>≤25 oversold = 9.5/10 · ≥75 overbought = 1/10 · 40–60 neutral = 5/10</td><td>6mo daily closes</td></tr>
        <tr><td>OBV trend</td><td>18%</td><td>14-bar linear regression slope on OBV normalised to magnitude. Rising = 7–9; flat = 5; falling = 1–3</td><td>6mo daily OHLCV</td></tr>
        <tr><td>Fibonacci</td><td>20%</td><td>Price position in 6mo H/L range. Golden zone (0.618 retrace, 34–44% of range) = 9. Near high (>95%) = 3</td><td>6mo daily OHLCV</td></tr>
        <tr><td>SMA 20/50</td><td>20%</td><td>Golden cross + price above both + rising slopes = 9. Death cross + price below both = 2</td><td>6mo daily closes</td></tr>
        <tr><td>EMA 12/26 (MACD)</td><td>10%</td><td>Bullish crossover = 9. Positive + rising = 7.5. Bearish crossover = 2</td><td>6mo daily closes</td></tr>
        <tr><td>Weekly S/R</td><td>10%</td><td>Price sitting on ≥2 weekly support levels (within 4%) = 8.5. Testing weekly resistance = 4. Near recent weekly high = 3.5</td><td>12-week weekly OHLC</td></tr>
      </tbody>
    </table>

    <h3>Valuation Decay Curve — Forward P/E → Score</h3>
    <table class="pe-table">
      <thead><tr><th>Forward P/E</th><th>Score</th><th>Rationale</th></tr></thead>
      <tbody>
        <tr><td>≤ 10×</td><td>10/10</td><td>Deep value; priced for pessimism</td></tr>
        <tr><td>11–15×</td><td>9/10</td><td>Cheap by any measure</td></tr>
        <tr><td>16–20×</td><td>8/10</td><td>Fair value for quality growth</td></tr>
        <tr><td>21–25×</td><td>7/10</td><td>Modest premium; defensible</td></tr>
        <tr><td>26–35×</td><td>6/10</td><td>Growth priced in; execution risk rises</td></tr>
        <tr><td>36–50×</td><td>5/10</td><td>Neutral; needs strong thesis</td></tr>
        <tr><td>51–70×</td><td>4/10</td><td>Elevated; momentum-dependent</td></tr>
        <tr><td>71–100×</td><td>3/10</td><td>Speculative; small margin of safety</td></tr>
        <tr><td>&gt;100× or unprofitable</td><td>2/10</td><td>Option-like; pure growth bet</td></tr>
      </tbody>
    </table>

    <h3>Star Scale</h3>
    <div class="scale-row">
      <div class="scale-chip" style="background:#dcfce7;border-color:#bbf7d0">
        <div class="sc-stars">★★★★★</div><div class="sc-label" style="color:#15803d">Strong</div><div class="sc-range" style="color:#15803d">75–100</div>
      </div>
      <div class="scale-chip" style="background:#d1fae5;border-color:#99f6e4">
        <div class="sc-stars">★★★★<span style="color:var(--border2)">☆</span></div><div class="sc-label" style="color:#0e7490">Good</div><div class="sc-range" style="color:#0e7490">60–74</div>
      </div>
      <div class="scale-chip" style="background:#fef9c3;border-color:#fde68a">
        <div class="sc-stars">★★★<span style="color:var(--border2)">☆☆</span></div><div class="sc-label" style="color:#d97706">Neutral</div><div class="sc-range" style="color:#d97706">45–59</div>
      </div>
      <div class="scale-chip" style="background:#fed7aa;border-color:#fdba74">
        <div class="sc-stars">★★<span style="color:var(--border2)">☆☆☆</span></div><div class="sc-label" style="color:#ea580c">Weak</div><div class="sc-range" style="color:#ea580c">30–44</div>
      </div>
      <div class="scale-chip" style="background:#fee2e2;border-color:#fecaca">
        <div class="sc-stars">★<span style="color:var(--border2)">☆☆☆☆</span></div><div class="sc-label" style="color:#dc2626">Poor</div><div class="sc-range" style="color:#dc2626">0–29</div>
      </div>
    </div>

    <h3>Limitations &amp; Caveats</h3>
    <div class="caveat">
      The R/R Score is a <strong>screening tool</strong>, not a buy/sell signal. TA indicators are computed from public market data and carry all the limitations of technical analysis — they describe price behaviour, not fundamental value. RSI divergence, OBV anomalies, and false Fibonacci confluences are common. Forward P/E, News Velocity, and Tailwind scores are static between updates. Scores on speculative names reflect narrative alignment, not fundamental safety. Weekly S/R uses only 12 weeks of data and may miss longer-term structural levels. Always read the full thesis and conduct independent research before acting.
    </div>

    <a class="munger-btn" href="https://fs.blog/charlie-munger-reading-list/" target="_blank" rel="noopener">☯ Munger Reading List — Farnam Street →</a>
  </div>
</div>

</body>
</html>
