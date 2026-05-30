[index.html](https://github.com/user-attachments/files/28415093/index.html)

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Watchlist — Live Prices · Short Interest · Social</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:system-ui,-apple-system,sans-serif;background:#fff;color:#111;font-size:12px;padding:.6rem}

/* ── Status bar ── */
#sbar{display:flex;gap:10px;align-items:center;flex-wrap:wrap;padding:6px 10px;background:#f0f8f4;border:1px solid #cce8d8;border-radius:6px;margin-bottom:7px;font-size:11px}
.dot{width:8px;height:8px;border-radius:50%;background:#ccc;display:inline-block;margin-right:3px;flex-shrink:0}
.dot.live{background:#22c55e;animation:blink 2s infinite}
.dot.loading{background:#f59e0b;animation:blink .8s infinite}
.dot.error{background:#ef4444}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
.rbtn{font-size:11px;padding:3px 10px;background:#e8f0fe;border:1px solid #c5d5f8;border-radius:4px;color:#1a56db;cursor:pointer}
.rbtn:hover{background:#d1e0fc}

/* ── Controls ── */
#ctrl{display:flex;gap:6px;align-items:center;flex-wrap:wrap;margin-bottom:7px}
#srch{font-size:12px;padding:4px 8px;border:1px solid #ddd;border-radius:4px;width:190px;outline:none}
#srch:focus{border-color:#1a56db}
#rcnt{font-size:11px;color:#888;white-space:nowrap}
#fbars{display:flex;gap:4px;flex-wrap:wrap}
.fbtn{font-size:10px;padding:3px 9px;border:1px solid #ddd;border-radius:12px;background:#fff;cursor:pointer;white-space:nowrap;transition:background .15s}
.fbtn:hover{background:#f0f0ee}
.fbtn.active{background:#111;color:#fff;border-color:#111}

/* ── Table ── */
/* ── Table: auto layout, fills available width, no horizontal scroll ── */
#wt{width:100%;border-collapse:collapse;table-layout:auto}
th{background:#f5f5f3;color:#444;font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.05em;padding:6px 8px;text-align:left;border-bottom:2px solid #ddd;white-space:nowrap;cursor:pointer;user-select:none;position:sticky;top:0;z-index:10}
th:hover{background:#eae9e7}
th.asc::after{content:" ▲";font-size:8px;opacity:.6}
th.desc::after{content:" ▼";font-size:8px;opacity:.6}
th.nosort{cursor:default}
th.nosort:hover{background:#f5f5f3}
td{padding:6px 8px;border-bottom:1px solid #f0f0ee;vertical-align:top;line-height:1.45;word-break:break-word}
tr:hover td{background:#fafaf9}
tr.hide{display:none}

/* ── Column behaviour: let browser size naturally, constrain only where needed ── */
.c-sec  {font-size:10px;color:#777;white-space:nowrap}
.c-tick {white-space:nowrap}
.c-name {white-space:nowrap}
.c-price{text-align:right;white-space:nowrap}
.c-mc   {text-align:right;white-space:nowrap}
.c-si   {text-align:right;white-space:nowrap;font-weight:600}
.c-chg  {text-align:right;white-space:nowrap;font-weight:600}
.c-hl   {text-align:right;white-space:nowrap}
.c-spark{text-align:center;padding:4px 8px;white-space:nowrap}
/* Social and Thesis get the remaining space and wrap naturally */
.c-soc  {min-width:180px}
.c-thesis{min-width:200px}

/* ── Badges ── */
.badge{display:inline-block;font-size:10px;font-weight:700;padding:2px 7px;border-radius:3px;white-space:nowrap}
.eq{background:#E1F5EE;color:#085041}
.hk{background:#E6F1FB;color:#0C447C}
.new{background:#FAEEDA;color:#633806}

/* ── Numeric ── */
.pos{color:#0a7f4f;font-weight:700}
.neg{color:#c0392b;font-weight:700}
.flat{color:#888}
.si-hot{color:#c0392b;font-weight:700}
.si-med{color:#d35400;font-weight:700}
.si-low{color:#0a7f4f;font-weight:600}
.si-cell{text-align:right}
.live-p{font-weight:700;font-size:12px}
.live-mc{font-size:10px;color:#888;display:block}
.mc-val{font-size:11px}
.dim{color:#bbb;font-style:italic}

/* ── H/L bar ── */
.hl-hi{font-size:11px}
.hl-lo{font-size:10px;color:#aaa}
.hl-pbar{margin-top:3px;background:#eee;border-radius:2px;height:4px;width:76px}
.hl-pfill{background:#1a56db;height:4px;border-radius:2px}

/* ── Sparkline ── */
.spark{display:block;cursor:default}

/* ── Social ── */
.wsb-live{display:inline-block;font-size:10px;border-radius:3px;padding:1px 5px;margin-bottom:2px;color:#fff;background:#ff4500}
.wsb-live.none{background:#ddd;color:#666}
.wsb{display:inline-block;font-size:10px;background:#ff4500;color:#fff;border-radius:3px;padding:1px 5px}
.cam{display:inline-block;font-size:10px;background:#2d5fa8;color:#fff;border-radius:3px;padding:1px 5px}

/* ── Note ── */
.note{font-size:10px;color:#999;margin-top:10px;line-height:1.6}
</style>
</head>
<body>

<!-- STATUS BAR -->
<div id="sbar">
  <span><span class="dot loading" id="sdot"></span><span id="stxt">Connecting…</span></span>
  <span>📈 Yahoo Finance (15min delay)</span>
  <span>💬 Tradestie WSB live</span>
  <span>⏱ Updated: <strong id="lupd">—</strong></span>
  <button class="rbtn" onclick="refresh()">↻ Refresh</button>
</div>

<!-- CONTROLS -->
<div id="ctrl">
  <input id="srch" type="text" placeholder="🔍 Search ticker, name, keyword…" oninput="applyFilters()">
  <span id="rcnt"></span>
  <div id="fbars">
    <button class="fbtn active" data-f="all" onclick="filt(this)">All</button>
<button class="fbtn" data-f="AI & Semiconductors — Core" onclick="filt(this)">AI & Semiconductor</button>
<button class="fbtn" data-f="Quantum Computing" onclick="filt(this)">Quantum Computing</button>
<button class="fbtn" data-f="Memory & Storage" onclick="filt(this)">Memory & Storage</button>
<button class="fbtn" data-f="Space & Defence" onclick="filt(this)">Space & Defence</button>
<button class="fbtn" data-f="Uranium & Nuclear" onclick="filt(this)">Uranium & Nuclear</button>
<button class="fbtn" data-f="Bitcoin / Crypto Treasury — Equities" onclick="filt(this)">Bitcoin</button>
<button class="fbtn" data-f="China / Hong Kong Equities" onclick="filt(this)">China</button>
<button class="fbtn" data-f="Biotech & Healthcare" onclick="filt(this)">Biotech & Healthca</button>
<button class="fbtn" data-f="Specialist — Superconductors / SaaS / Semis" onclick="filt(this)">Specialist</button>
<button class="fbtn" data-f="Robotics Value Chain" onclick="filt(this)">Robotics Value Cha</button>

  </div>
</div>

<!-- TABLE -->
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
  <th class="nosort">Social</th>
  <th class="nosort">Thesis</th>
</tr></thead>
<tbody id="wtb">
<tr data-sector="AI & Semiconductors — Core" data-ticker="NVDA" data-i="0">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">NVDA</span></td>
  <td class="c-name" style="font-size:12px">NVIDIA</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$5.71 T</span>
  </td>
  <td class="si-cell si-low" data-si="">1.17%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High</span> <span class="cam">Camillo: Core AI infra — fits perfectly</span><br>Most mentioned AI stock on Reddit; perennial WSB top 3; Camillo's stated 2026 AI infra focus</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI GPU monopoly; CUDA ecosystem; NVQLink quantum; Q1 FY27 earnings May 20 — next major catalyst</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="MU" data-i="1">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">MU</span></td>
  <td class="c-name" style="font-size:12px">Micron Technology</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$913 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4% ↑rising</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — #7 in 2026 index</span> <span class="cam">Camillo: Fits — AI memory supercycle visible in social data</span><br>WSB 2026 community index top 10; retail cult following; SI rising (Schwab noted +16% SI in early May)</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#3 ranked; HBM/DRAM supercycle; Q2 revenue +196% YoY; approaching $1T market cap</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="AMD" data-i="2">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">AMD</span></td>
  <td class="c-name" style="font-size:12px">Advanced Micro Devices</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$733 B</span>
  </td>
  <td class="si-cell si-low" data-si="">2.22%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High</span> <span class="cam">Camillo: Indirect — AI infra adjacent</span><br>Active WSB & options flow; huge week on earnings beat and China optimism</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">MI300X AI GPU; NVDA challenger; +260% in 52 weeks; $37.5B revenue FY26</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="INTC" data-i="3">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">INTC</span></td>
  <td class="c-name" style="font-size:12px">Intel</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$534 B</span>
  </td>
  <td class="si-cell si-low" data-si="">2.87%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — trending on Apple foundry deal</span> <span class="cam">Camillo: Turnaround narrative fits his consumer-info edge</span><br>Tiger Global initiated Q1 2026; Apple foundry rumours driving retail momentum; top options flow May 11</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Foundry turnaround; Gaudi AI chips; +492% in 52 weeks; Apple foundry partnership in negotiation</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="PLTR" data-i="4">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">PLTR</span></td>
  <td class="c-name" style="font-size:12px">Palantir Technologies</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$320 B</span>
  </td>
  <td class="si-cell si-low" data-si="">2.47%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — #10 in 2026 index; cult stock</span> <span class="cam">Camillo: Fits — military AI social narrative massive</span><br>WSB 2026 index top 10; constant top-5 mentions; Trump personal position disclosed</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#5 ranked; military AI; AIP platform; US commercial revenue +133% YoY; 11 consecutive quarters accelerating</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="CBRS" data-i="5">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">CBRS</span></td>
  <td class="c-name" style="font-size:12px">Cerebras Systems</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$43 B</span>
  </td>
  <td class="si-cell" data-si="">N/A — IPO'd May 14</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Exploding — massive IPO buzz</span> <span class="cam">Camillo: Strong fit — AI chip alternative social trend massive on TikTok/X</span><br>"Monster debut" coverage everywhere; trending Stocktwits May 15; CNBC/Cramer coverage; social AI chip narrative perfectly aligned with Camillo's social arb method</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Wafer-scale AI chip — "dinner plate" GPU; IPO'd May 14 at $185; raised $5.55B; NVDA alternative narrative; Vicor power infra link</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="CRWV" data-i="6">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">CRWV</span></td>
  <td class="c-name" style="font-size:12px">CoreWeave</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$62 B</span>
  </td>
  <td class="si-cell si-med" data-si="">11.85%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Fits — AI cloud infra narrative dominant in social</span><br>Top options flow list consistently; NVDA doubled its CRWV stake this week; institutional flow heavy</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI GPU cloud infra; Q1 revenue +112% YoY; OpenAI anchor tenant; $35B debt load is key risk</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="NBIS" data-i="7">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">NBIS</span></td>
  <td class="c-name" style="font-size:12px">Nebius Group</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$45 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">17.04%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — #5 in WSB 2026 index</span> <span class="cam">Camillo: Moderate fit — European AI infra, less social visibility</span><br>WSB 2026 community voted it into top 5; AltIndex AI score 75 (highest on WSB list); Q1 beat +21%</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">European AI GPU cloud (ex-Yandex); NVDA partnership; +545% in 52 weeks; 17% short interest = squeeze risk</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="BIDU" data-i="8">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">BIDU</span></td>
  <td class="c-name" style="font-size:12px">Baidu</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$30 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Weak — China narrative less accessible via US social</span><br>Moves with China-US trade developments; limited retail chatter outside China-tech-basket plays</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China AI leader; Ernie Bot; Apollo Go self-driving; trades at deep discount vs US AI peers</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="ORCL" data-i="9">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">ORCL</span></td>
  <td class="c-name" style="font-size:12px">Oracle</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$566 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~1.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate fit — enterprise AI infra, less consumer-visible</span><br>Institutional favourite; retail less engaged but growing as AI cloud narrative broadens</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI cloud GPU clusters; LLM hosting; cloud infra hyperscaler play for enterprise AI</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="NOW" data-i="10">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">NOW</span></td>
  <td class="c-name" style="font-size:12px">ServiceNow</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$200 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~1.8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Weak — B2B SaaS less visible in consumer social</span><br>"Free money" per Hans; less retail-driven but consistent institutional accumulation</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI fat-data moat; enterprise workflow lock-in; SaaS rotation target alongside NET, CRM</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="APP" data-i="11">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">APP</span></td>
  <td class="c-name" style="font-size:12px">Applovin</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$80 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3.2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Strong fit — consumer app + AI ad revenue visible in social data</span><br>Q1 beat confirmed; mobile gaming + AI ad revenue very trackable via social signals (Camillo's core method)</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-powered ad tech; AXON AI model; confirmed great earnings; +260% in 52 weeks</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="DDOG" data-i="12">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">DDOG</span></td>
  <td class="c-name" style="font-size:12px">Datadog</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$40 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate — developer tooling, visible in tech Twitter/X</span><br>Confirmed great earnings; dev community buzz strong on X; SaaS rotation candidate</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI observability; monitoring AI workloads; confirmed great earnings alongside PLTR and APP</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="NET" data-i="13">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">NET</span></td>
  <td class="c-name" style="font-size:12px">Cloudflare</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$65 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~2.8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — AI inference/security narrative building on social</span><br>SaaS rotation candidate; less retail hype but fundamentals debated actively in tech communities</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI inference edge network; CDN + security + AI gateway; SaaS rotation candidate</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="RDDT" data-i="14">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">RDDT</span></td>
  <td class="c-name" style="font-size:12px">Reddit</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$27 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — #6 in WSB 2026 index (Reddit voting itself in)</span> <span class="cam">Camillo: Perfect fit — social media platform, data licensing visible in social</span><br>WSB voted RDDT into their own 2026 index; Camillo explicitly tracks social data for AI licensing trends</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI data licensing moat; LLM training data demand; unique human-generated corpus</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="QCOM" data-i="15">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">QCOM</span></td>
  <td class="c-name" style="font-size:12px">Qualcomm</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$160 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~1.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate — on-device AI visible via consumer device chatter</span><br>Top options volume May 8 & 11; Snapdragon X retail buzz on TikTok/YouTube — fits Camillo's consumer-visible AI theme</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">On-device AI chips; Snapdragon X; PC + mobile AI inference; buylisted in Hans' watchlist</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="VICR" data-i="16">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">VICR</span></td>
  <td class="c-name" style="font-size:12px">Vicor</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$4 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Weak — industrial power, not consumer-visible</span><br>Power delivery infra narrative; Cerebras IPO brings new attention; less retail-driven</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Vertical power delivery for Cerebras wafer-scale engines; ran 50→250 in 9 months; CBRS IPO adds fresh catalyst</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="GDYN" data-i="17">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">GDYN</span></td>
  <td class="c-name" style="font-size:12px">Grid Dynamics</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$1 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low — niche but gaining</span> <span class="cam">Camillo: Low — B2B enterprise AI consulting</span><br>Called out by @stocktalkweekly (Elon follows); breakout volume May 8; Rosenblatt coverage May 12</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Enterprise AI implementation consultancy; breakout volume signal; analyst coverage initiating</td>
</tr>
<tr data-sector="Quantum Computing" data-ticker="IONQ" data-i="18">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Quantum Computing</td>
  <td class="c-tick"><span class="badge eq">IONQ</span></td>
  <td class="c-name" style="font-size:12px">IonQ</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$20 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">22.51%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High — quantum hype narrative</span> <span class="cam">Camillo: Moderate — quantum social trend growing on TikTok/X</span><br>Q1 revenue +755% YoY; only positive-YTD quantum name; Jefferies prefers IONQ over RGTI after earnings; very high SI = squeeze risk</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Leading pure-play quantum; trapped-ion; Q1 revenue $64.7M; 22.5% short float = potential squeeze fuel</td>
</tr>
<tr data-sector="Quantum Computing" data-ticker="RGTI" data-i="19">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Quantum Computing</td>
  <td class="c-tick"><span class="badge eq">RGTI</span></td>
  <td class="c-name" style="font-size:12px">Rigetti Computing</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$6 B</span>
  </td>
  <td class="si-cell si-med" data-si="">12.50%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — quantum speculation play</span> <span class="cam">Camillo: Low-Moderate — hardware story less social-visible</span><br>108-qubit Cepheus-1 announced; Mizuho PT cut $33→$27; "Quantum Hype Meets Reality" headline May 15; Rosenblatt still >100% upside</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Superconducting qubit; 108-qubit Cepheus-1; Q1 revenue +199% YoY; 12.5% short = elevated; caution warranted near-term</td>
</tr>
<tr data-sector="Quantum Computing" data-ticker="QBTS" data-i="20">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Quantum Computing</td>
  <td class="c-tick"><span class="badge eq">QBTS</span></td>
  <td class="c-name" style="font-size:12px">D-Wave Quantum</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$8.9 B</span>
  </td>
  <td class="si-cell si-med" data-si="">14.04%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Low</span><br>Bookings +1,994% YoY; 76.5% analyst PT upside; "dual-platform" narrative gaining traction; 14% SI elevated</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Annealing + gate-model dual platform; bookings +1,994% YoY; 83% gross margin; 14% short = meaningful</td>
</tr>
<tr data-sector="Quantum Computing" data-ticker="CCCX / INFQ" data-i="21">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Quantum Computing</td>
  <td class="c-tick"><span class="badge eq">CCCX / INFQ</span></td>
  <td class="c-name" style="font-size:12px">Infleqtion</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">small cap</span>
  </td>
  <td class="si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low — niche quantum</span> <span class="cam">Camillo: Low</span><br>"Best tech IMO and most undervalued" per Hans; NVDA CUDA-Q integration; contract visibility as signal</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Neutral-atom hybrid quantum-AI; NVQLink + CUDA-Q; Royal Navy / Illinois gov contracts; undervalued vs peers</td>
</tr>
<tr data-sector="Memory & Storage" data-ticker="DRAM" data-i="22">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Memory & Storage</td>
  <td class="c-tick"><span class="badge eq">DRAM</span></td>
  <td class="c-name" style="font-size:12px">Roundhill Memory ETF</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$6 B AUM</span>
  </td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — options flow notable (3.1 calls : 1 put May 8)</span> <span class="cam">Camillo: Moderate — consumer AI device memory demand trackable</span><br>IV at 78; call-heavy; one of fastest-growing ETF launches ever; Stocktwits trending</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">First memory ETF; +107% since Apr 2 launch; $6B AUM; SK Hynix 26%, MU 23%, Samsung 20%</td>
</tr>
<tr data-sector="Memory & Storage" data-ticker="SNDK" data-i="23">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Memory & Storage</td>
  <td class="c-tick"><span class="badge eq">SNDK</span></td>
  <td class="c-name" style="font-size:12px">SanDisk</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$70 B</span>
  </td>
  <td class="si-cell si-low" data-si="">6.58% ↑rising</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — trending as memory supercycle pick</span> <span class="cam">Camillo: Moderate — SSD/storage consumer demand trackable</span><br>Schwab Short Monitor flagged SI +21% in early May; +3,930% in 52 weeks; IV at 106 (near 52-wk high); Stocktwits trending May 15</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">NAND flash; WDC spinoff; +3,930% in 52 weeks; AI SSD demand supercycle; 6.6% SI rising = watch</td>
</tr>
<tr data-sector="Memory & Storage" data-ticker="WDC" data-i="24">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Memory & Storage</td>
  <td class="c-tick"><span class="badge eq">WDC</span></td>
  <td class="c-name" style="font-size:12px">Western Digital</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$30 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — HDD/cloud storage visible in consumer data</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">HDD + NAND; AI data centre capacity build; DRAM ETF top holding</td>
</tr>
<tr data-sector="Memory & Storage" data-ticker="STX" data-i="25">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Memory & Storage</td>
  <td class="c-tick"><span class="badge eq">STX</span></td>
  <td class="c-name" style="font-size:12px">Seagate</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$25 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low-Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">HDD storage; AI data centre demand; pairs with MU/SNDK/WDC in storage basket</td>
</tr>
<tr data-sector="Space & Defence" data-ticker="RKLB" data-i="26">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq">RKLB</span></td>
  <td class="c-name" style="font-size:12px">Rocket Lab USA</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$72 B</span>
  </td>
  <td class="si-cell si-low" data-si="">5.45%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — #2 in WSB 2026 index</span> <span class="cam">Camillo: Strong fit — space narrative massive on social; humanoid/space themes he explicitly bullish on</span><br>WSB voted RKLB #2 in 2026 index; AltIndex AI score 72; Neutron + Golden Dome / Space Force contracts driving meme-level hype; Trump position in ASTS/RKLB revealed by filings</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#1 ranked; record Q1 $200.3M revenue; $2.2B backlog; Neutron + Raytheon SBIRS + Anduril HASTE; transferring to Nasdaq Global Market May 15</td>
</tr>
<tr data-sector="Space & Defence" data-ticker="ASTS" data-i="27">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq">ASTS</span></td>
  <td class="c-name" style="font-size:12px">AST SpaceMobile</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$18 B</span>
  </td>
  <td class="si-cell si-med" data-si="">12.7% ↑↑ rising fast</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — #1 in WSB 2026 index</span> <span class="cam">Camillo: Strong — direct-to-device satellite social trend huge on TikTok/X</span><br>WSB voted ASTS #1 for 2026; call:put 4.4:1 on May 11 before earnings; BlueBird satellite failure April = short interest surged +11% to 12.7%; Q1 miss ($14.7M revenue); retail holding firm vs short pressure</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#2 ranked; 12.7% SI rising fast post-BlueBird failure + Q1 miss — short squeeze potential vs fundamental risk; Trump personal position disclosed; FCC auth for 248 satellites</td>
</tr>
<tr data-sector="Space & Defence" data-ticker="LUNR" data-i="28">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space & Defence</td>
  <td class="c-tick"><span class="badge eq">LUNR</span></td>
  <td class="c-name" style="font-size:12px">Intuitive Machines</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$1 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~6%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Low — lunar logistics less consumer-visible</span><br>SpaceX IPO narrative lifting all space stocks; IM-3 mission watch in H2 2026</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">NASA/DoD lunar lander contracts; binary on IM-3 mission; SpaceX IPO tailwind</td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="CCJ" data-i="29">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq">CCJ</span></td>
  <td class="c-name" style="font-size:12px">Cameco</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$18 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — nuclear energy narrative</span> <span class="cam">Camillo: Moderate — AI power demand nuclear narrative growing on social</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">World's largest publicly traded uranium miner; nuclear renaissance on AI data centre power demand</td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="UEC" data-i="30">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq">UEC</span></td>
  <td class="c-name" style="font-size:12px">Uranium Energy Corp</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$3 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">US-domestic uranium supply; energy security narrative; pinned basket play by Eren Coup</td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="URA" data-i="31">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq">URA</span></td>
  <td class="c-name" style="font-size:12px">Global X Uranium ETF</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$3 B AUM</span>
  </td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — nuclear energy theme</span> <span class="cam">Camillo: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Diversified uranium basket ETF; cleanest single-ticker nuclear exposure</td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="NXE" data-i="32">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium & Nuclear</td>
  <td class="c-tick"><span class="badge eq">NXE</span></td>
  <td class="c-name" style="font-size:12px">NexGen Energy</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$5 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Tier-1 Arrow deposit; highest-grade undeveloped uranium in Athabasca Basin</td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="MSTR" data-i="33">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq">MSTR</span></td>
  <td class="c-name" style="font-size:12px">Strategy Inc</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$100 B</span>
  </td>
  <td class="si-cell si-med" data-si="">10.60%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — Bitcoin proxy cult stock</span> <span class="cam">Camillo: Strong fit — BTC narrative the dominant financial social trend</span><br>Constant top-5 WSB mentions; Saylor posts drive social spikes; 10.6% SI means shorts fighting the BTC bull</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">818K BTC; leveraged BTC proxy; -53% in 52 weeks (BTC underperformance); 10.6% SI = meaningful squeeze risk if BTC rallies</td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="COIN" data-i="34">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq">COIN</span></td>
  <td class="c-name" style="font-size:12px">Coinbase</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$60 B</span>
  </td>
  <td class="si-cell si-med" data-si="">9.57%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — crypto bull narrative</span> <span class="cam">Camillo: Strong fit — crypto adoption very visible in consumer social data</span><br>Clarity Act Senate vote = direct catalyst; JPMorgan partnership; 9.6% SI with BTC at highs = shorts squeezable</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Crypto exchange; Clarity Act beneficiary; 9.6% short interest; BTC hit $82K catalyst window</td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="HOOD" data-i="35">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq">HOOD</span></td>
  <td class="c-name" style="font-size:12px">Robinhood Markets</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$25 B</span>
  </td>
  <td class="si-cell si-low" data-si="">3.53%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — retail trading platform of WSB itself</span> <span class="cam">Camillo: Strong fit — retail investing app visible in every social context</span><br>Tiger Global initiated Q1 2026; IV at 64 (near 52-wk range high); WSB trades via HOOD — native social signal</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Retail brokerage; crypto + prediction markets; Q1 revenue strong; Tiger Global new buyer</td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="CRCL" data-i="36">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq">CRCL</span></td>
  <td class="c-name" style="font-size:12px">Circle Internet Group</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$8–12 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High — stablecoin regulatory play</span> <span class="cam">Camillo: Moderate — USDC/stablecoin narrative visible in crypto social</span><br>IV 130% (May) / 93% (June) — highest range in 52wks; call:put 2.2:1; Clarity Act direct beneficiary</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">USDC stablecoin issuer; IPO 2026; Clarity Act direct beneficiary; elevated options flow signals uncertainty + opportunity</td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="GLXY" data-i="37">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq">GLXY</span></td>
  <td class="c-name" style="font-size:12px">Galaxy Digital</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$8 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Crypto merchant bank; BTC/ETH treasury + trading; direct crypto market exposure</td>
</tr>
<tr data-sector="Bitcoin / Crypto Treasury — Equities" data-ticker="DFDV" data-i="38">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Bitcoin / Crypto Treasury — Equities</td>
  <td class="c-tick"><span class="badge eq">DFDV</span></td>
  <td class="c-name" style="font-size:12px">DeFi Dev Corp</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">small cap</span>
  </td>
  <td class="si-cell si-med" data-si="">~8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate — SOL treasury play</span> <span class="cam">Camillo: Moderate — Solana social narrative growing</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">SOL treasury company; MSTR model applied to Solana; small cap with high beta to SOL price</td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 700" data-i="39">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk">HK: 700</span></td>
  <td class="c-name" style="font-size:12px">Tencent</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$550 B</span>
  </td>
  <td class="si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — WeChat / gaming social data globally trackable</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China internet; gaming; AI moat; WeChat ecosystem; US-China thaw tailwind May 2026</td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 1810" data-i="40">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk">HK: 1810</span></td>
  <td class="c-name" style="font-size:12px">Xiaomi</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$80 B</span>
  </td>
  <td class="si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Strong fit — SU7 EV consumer buzz massive in Asian social, growing in US</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">EV + smartphone ecosystem; SU7 car momentum; China tech re-rating; Camillo's social-visible consumer play</td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 9992" data-i="41">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk">HK: 9992</span></td>
  <td class="c-name" style="font-size:12px">Pop Mart</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$30 B</span>
  </td>
  <td class="si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Very Strong fit — collectibles trend MASSIVE on TikTok globally, exactly his method</span><br>Labubu blind-box craze viral on TikTok/Instagram globally — precisely the social-before-analysts pattern Camillo built his career on</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Collectibles/IP; Labubu TikTok viral; China consumer re-rating; international expansion; Camillo-type social-arb setup</td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="HK: 0100" data-i="42">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge hk">HK: 0100</span></td>
  <td class="c-name" style="font-size:12px">MiniMax Group</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$34 B</span>
  </td>
  <td class="si-cell" data-si="">n/a (HK)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Moderate — China AI social trend building on X/TikTok</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China AI LLM; Hailuo AI video viral; 212M users; 70%+ overseas revenue; doubled on Jan 2026 IPO</td>
</tr>
<tr data-sector="China / Hong Kong Equities" data-ticker="BABA" data-i="43">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">China / Hong Kong Equities</td>
  <td class="c-tick"><span class="badge eq">BABA</span></td>
  <td class="c-name" style="font-size:12px">Alibaba</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$270 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate — ecommerce + AI cloud, less consumer-visible in US</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China ecommerce + AI cloud (Qwen LLM); US-China trade thaw = direct catalyst; deep discount vs US AI peers</td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="HIMS" data-i="44">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq">HIMS</span></td>
  <td class="c-name" style="font-size:12px">Hims &amp; Hers Health</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$4 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">30–43% ↑↑</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very High — extremely active GLP-1 meme</span> <span class="cam">Camillo: Very Strong fit — GLP-1/weight loss viral on every social platform; telehealth consumer-visible</span><br>SI 30.6% (StockAnalysis) to 42.8% (Ihor Dusaniwsky via X) — shorts added $443M YTD; Q1 revenue miss -14.3% drop; call:put 3.4:1 pre-earnings; Camillo's social arb method perfectly tracks GLP-1 cultural shift</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Telehealth; GLP-1 branded pivot; 30–43% short interest = massive squeeze potential; Q1 revenue miss -14.3%; FY guide raised; RoW +969% YoY</td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="RXRX" data-i="45">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq">RXRX</span></td>
  <td class="c-name" style="font-size:12px">Recursion Pharma</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$3 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — AI drug discovery narrative building on X/TikTok</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI drug discovery; ML pipeline; largest proprietary biology dataset in industry</td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="CMPS" data-i="46">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq">CMPS</span></td>
  <td class="c-name" style="font-size:12px">COMPASS Pathways</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$0.5 B</span>
  </td>
  <td class="si-cell si-med" data-si="">~8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate — psychedelic narrative</span> <span class="cam">Camillo: Strong fit — psychedelic / mental health social trend very visible</span><br>Mental health + psychedelics heavily discussed on Reddit/TikTok — exactly Camillo's social-before-analysts pattern</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Psilocybin mental health; COMP360 Phase 3; psychedelic therapy social narrative building</td>
</tr>
<tr data-sector="Biotech & Healthcare" data-ticker="GHRS" data-i="47">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Biotech & Healthcare</td>
  <td class="c-tick"><span class="badge eq">GHRS</span></td>
  <td class="c-name" style="font-size:12px">GH Research</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$0.4 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~6%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Moderate — ibogaine addiction narrative growing in social</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Ibogaine-based depression/addiction therapy; novel mechanism of action</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="AMSC" data-i="48">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq">AMSC</span></td>
  <td class="c-name" style="font-size:12px">American Superconductor</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$1.5 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~7%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Weak — industrial, not consumer-visible</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">#1 in Hans' 21-report superconductor deep dive; monthly base breakout; wind energy + DoD power</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="HIMX" data-i="49">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq">HIMX</span></td>
  <td class="c-name" style="font-size:12px">Himax Technologies</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$2 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low</span><br>IV increasing per Market Rebellion May 11; gregory_FTA 4th largest position</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Display driver ICs; monthly base breakout; AR/VR adoption play</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="APLD" data-i="50">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq">APLD</span></td>
  <td class="c-name" style="font-size:12px">Applied Digital</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$2 B</span>
  </td>
  <td class="si-cell si-med" data-si="">~9%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — AI data centre narrative visible</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI data centres; Hans buy-at-open call; data centre narrative riding AI infra supercycle</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="IGV" data-i="51">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq">IGV</span></td>
  <td class="c-name" style="font-size:12px">iShares Tech-Software ETF</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim"></span>
  </td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — SaaS rotation narrative</span> <span class="cam">Camillo: Moderate</span><br>"IGV only up because SMH is down" — watching for both to rally together as net new capital signal</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Diversified AI software basket; Salesforce, NOW, Oracle, Adobe, Workday; rotation signal watch</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="EWY" data-i="52">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq">EWY</span></td>
  <td class="c-name" style="font-size:12px">iShares MSCI S. Korea ETF</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim"></span>
  </td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low</span><br>10–14% of all global equity ETF volume — institutional signal, not retail-driven</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Korea semi/tech (Samsung, SK Hynix); massive EM inflow tailwind; $35B YTD EM ETF flows</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="BOT" data-i="53">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis</td>
  <td class="c-tick"><span class="badge eq">BOT</span></td>
  <td class="c-name" style="font-size:12px">RoboStrategy Inc</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">small cap</span>
  </td>
  <td class="si-cell" data-si="">n/a — new IPO</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low — niche IPO</span> <span class="cam">Camillo: Strong fit — robotics/physical AI = his stated 2026 focus area</span><br>Robotics/AI Camillo stated explicitly in late 2025 interviews as his multi-trillion-dollar 2026 focus; BOT is direct pure-play vehicle</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Dedicated robotics/physical AI fund; NASDAQ IPO May 11 2026; institutional-style concentrated exposure</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="TSLA" data-i="54">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Consumer / Humanoid</span></td>
  <td class="c-tick"><span class="badge eq">TSLA</span></td>
  <td class="c-name" style="font-size:12px">Tesla</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$1.61 T</span>
  </td>
  <td class="si-cell si-low" data-si="">~2.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Extreme</span> <span class="cam">Camillo: Very Strong — Optimus humanoid viral across every platform</span><br>Optimus robot mass production target 1M units 2026; FSD social narrative dominant</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">EV + Optimus humanoid + FSD AI; #1 consumer-visible robotics stock; Optimus = Camillo's stated robotics megatrend</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="AMZN" data-i="55">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Consumer / Humanoid</span></td>
  <td class="c-tick"><span class="badge eq">AMZN</span></td>
  <td class="c-name" style="font-size:12px">Amazon</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">$2.58 T</span>
  </td>
  <td class="si-cell si-low" data-si="">~0.8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High</span> <span class="cam">Camillo: Strong — warehouse robotics + Alexa AI + drone delivery visible in consumer social</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Proteus/Sequoia warehouse robots; Zoox robotaxi; Kuiper satellite; $200B capex 2026; robotics consumer-visible via Prime delivery</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ISRG" data-i="56">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Surgical Robotics</span></td>
  <td class="c-tick"><span class="badge eq">ISRG</span></td>
  <td class="c-name" style="font-size:12px">Intuitive Surgical</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$195 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~1.2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Strong — surgical robot social narrative growing on TikTok/medical</span><br>Da Vinci 5 launch; 2.2M procedures/yr; 85% recurring revenue; near-monopoly</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">World leader in robotic surgery; da Vinci 5 system; 85% recurring revenue; AI-guided surgical assist next catalyst; compounding installed base</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="PRCT" data-i="57">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Surgical Robotics</span></td>
  <td class="c-tick"><span class="badge eq">PRCT</span></td>
  <td class="c-name" style="font-size:12px">Procept BioRobotics</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$6 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">~18%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — prostate treatment social narrative building</span><br>Aquabeam robotic system for BPH; 18% SI elevated; +45% YoY revenue</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Aquabeam robotic hydrodissection for BPH; fastest-growing surgical robot; 18% short float = squeeze potential; +45% YoY revenue</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="NOVT" data-i="58">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Surgical Robotics</span></td>
  <td class="c-tick"><span class="badge eq">NOVT</span></td>
  <td class="c-name" style="font-size:12px">Novanta</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$4.5 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low</span><br>Precision motion + laser scanning for surgical robots; ISRG supply chain play</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Precision motion + laser components for surgical robots (ISRG supply chain) + industrial automation; high-margin; medical robotics enabler</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ROK" data-i="59">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Industrial Automation</span></td>
  <td class="c-tick"><span class="badge eq">ROK</span></td>
  <td class="c-name" style="font-size:12px">Rockwell Automation</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$25 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low — industrial automation not consumer-visible</span><br>Re-shoring of US manufacturing = direct tailwind; AI-driven factory automation supercycle</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Industrial automation leader; AI-integrated factory control; US re-shoring direct beneficiary; PLC + SCADA + robotics integration</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="SYM" data-i="60">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Industrial Automation</span></td>
  <td class="c-tick"><span class="badge eq">SYM</span></td>
  <td class="c-name" style="font-size:12px">Symbotic</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$18 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">~15%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High</span> <span class="cam">Camillo: Strong — Walmart warehouse robot narrative very visible on social</span><br>Walmart + SoftBank backing; +88% YoY revenue; 15% SI elevated</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-powered warehouse robotics; Walmart anchor; SoftBank-backed; 15% short float; revenue +88% YoY post-restatement; real-world AI automation compounding</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ZBRA" data-i="61">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Industrial Automation</span></td>
  <td class="c-tick"><span class="badge eq">ZBRA</span></td>
  <td class="c-name" style="font-size:12px">Zebra Technologies</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$15 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — warehouse/retail scanning visible via supply chain social</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Barcode + RFID + warehouse automation; supply chain AI integration; re-shoring beneficiary; enterprise mobility platform; cyclical recovery 2026</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="CGNX" data-i="62">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Industrial Automation</span></td>
  <td class="c-tick"><span class="badge eq">CGNX</span></td>
  <td class="c-name" style="font-size:12px">Cognex</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$7 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low-Moderate</span><br>JPMorgan upgraded May 26 to Overweight PT $75; EV battery inspection + semi machine vision</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Machine vision leader; EV battery + semi fab inspection; JPMorgan upgrade May 26 OW / PT $75; recovery from down-cycle; AI-powered QC systems</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="MOD" data-i="63">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Industrial Automation</span></td>
  <td class="c-tick"><span class="badge eq">MOD</span></td>
  <td class="c-name" style="font-size:12px">Modine Manufacturing</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$4.5 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low</span><br>Thermal management for AI data centres and EVs; pivoting to data centre cooling</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Thermal management systems; AI data centre cooling (direct AI infra play) + EV thermal; pivoting to high-growth data centre segment; margin expansion</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="TER" data-i="64">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Industrial Automation</span></td>
  <td class="c-tick"><span class="badge eq">TER</span></td>
  <td class="c-name" style="font-size:12px">Teradyne</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$18 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~2.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Low</span><br>Universal Robots cobot market leader; semiconductor ATE for AI chips; dual robotics + AI semi exposure</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Semi ATE (tests NVDA/TSMC output) + Universal Robots cobots; dual exposure to AI chip test + industrial robotics; UR cobot business accelerating with factory automation</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ALNT" data-i="65">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Industrial Automation</span></td>
  <td class="c-tick"><span class="badge eq">ALNT</span></td>
  <td class="c-name" style="font-size:12px">Allient</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$0.6 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very Low</span> <span class="cam">Camillo: Low</span><br>JPMorgan upgraded May 26 OW PT $80; motion control for surgical robots + defence drones</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Motion control for surgical robots (ISRG supply chain) + defence UAVs + EVs; JPMorgan upgrade May 26 OW / PT $80 (from $65); re-rating catalyst</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="OUST" data-i="66">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">LiDAR / Perception</span></td>
  <td class="c-tick"><span class="badge eq">OUST</span></td>
  <td class="c-name" style="font-size:12px">Ouster</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$1.5 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">~22%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — AV/LiDAR speculation</span> <span class="cam">Camillo: Moderate — AV social narrative large on every platform</span><br>Digital LiDAR for AV + robotics + smart infrastructure; 22% SI = extreme squeeze potential</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Digital LiDAR for AV + robotics + smart cities; 22% short float = one of highest in robotics space; GM/Ford AV integration; revenue growing</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="AEVA" data-i="67">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">LiDAR / Perception</span></td>
  <td class="c-tick"><span class="badge eq">AEVA</span></td>
  <td class="c-name" style="font-size:12px">Aeva Technologies</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$0.8 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">~25%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate</span> <span class="cam">Camillo: Moderate — FMCW LiDAR social narrative</span><br>FMCW LiDAR (sees velocity + distance); VW + Continental partnerships; 25% SI extreme; Daimler Trucks SOP contract</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">FMCW 4D LiDAR — sees velocity in addition to distance; VW + Continental + Daimler Trucks validation; 25% short float = extreme squeeze risk; unique tech moat</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="AMBA" data-i="68">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Edge AI / Vision Chips</span></td>
  <td class="c-tick"><span class="badge eq">AMBA</span></td>
  <td class="c-name" style="font-size:12px">Ambarella</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$2.5 B</span>
  </td>
  <td class="si-cell si-med" data-si="">~9%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — edge AI chip for cameras/drones visible in consumer tech social</span><br>CV3 AI domain controller for ADAS; edge AI inference for drones + security + robotics vision</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI vision SoC for ADAS, drones, security cameras, robotics; CV3 domain controller; edge AI inference at low power; automotive design-win cycle building 2026–27</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="AMBQ" data-i="69">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Edge AI / Vision Chips</span></td>
  <td class="c-tick"><span class="badge eq">AMBQ</span></td>
  <td class="c-name" style="font-size:12px">Ambarella (class Q / warrants)</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">small cap</span>
  </td>
  <td class="si-cell" data-si="">—</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low</span><br>Likely AMBA warrants or alternative listing; same AMBA thesis — verify ticker before trading</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Same underlying thesis as AMBA — CV3 edge AI robotics chips; confirm share class / warrant status before sizing</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="SYNA" data-i="70">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Edge AI / Vision Chips</span></td>
  <td class="c-tick"><span class="badge eq">SYNA</span></td>
  <td class="c-name" style="font-size:12px">Synaptics</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$1.8 B</span>
  </td>
  <td class="si-cell si-med" data-si="">~11%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low-Moderate — touchscreen/IoT chips consumer-visible</span><br>Edge AI inference for smart home + IoT; recovering from post-PC downcycle; 11% SI elevated</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Human interface SoCs + IoT wireless + edge AI; recovery play; 11% SI; IoT volume leverage as robotics proliferates into consumer products</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="MBLY" data-i="71">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">AV / Autonomy</span></td>
  <td class="c-tick"><span class="badge eq">MBLY</span></td>
  <td class="c-name" style="font-size:12px">Mobileye</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$14 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — AV race narrative</span> <span class="cam">Camillo: Strong — self-driving car social narrative massive on every platform</span><br>EyeQ chips in 100M+ vehicles; SuperVision ADAS; Robotaxi program; Q1 beat May 2026</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">ADAS + AV chip leader; EyeQ in 100M+ vehicles; SuperVision full-surround ADAS; Robotaxi pilot; Intel majority owner; key autonomy value chain play</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="XPEV" data-i="72">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">AV / Autonomy</span></td>
  <td class="c-tick"><span class="badge eq">XPEV</span></td>
  <td class="c-name" style="font-size:12px">XPeng</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$16 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — China EV AV narrative</span> <span class="cam">Camillo: Strong — XNGP full-scenario driving demo viral on Chinese social, growing on X/TikTok</span><br>XNGP city-driving AI; Turing AI chip (in-house); VW co-development validates tech</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">China EV + in-house AI/AV chips (Turing); XNGP city-level autonomous driving; VW co-development; Mona M03 volume ramp; recovering unit economics</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="VPG" data-i="73">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Sensing / Force</span></td>
  <td class="c-tick"><span class="badge eq">VPG</span></td>
  <td class="c-name" style="font-size:12px">Vishay Precision Group</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$0.4 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very Low</span> <span class="cam">Camillo: Very Low</span><br>Foil strain gauges + force sensors for precision robotics; niche micro-cap enabler</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Force measurement sensors for robotics + industrial weighing; enables robot haptic feedback; micro-cap deep value in robotics supply chain</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="CTS" data-i="74">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Sensing / Force</span></td>
  <td class="c-tick"><span class="badge eq">CTS</span></td>
  <td class="c-name" style="font-size:12px">CTS Corporation</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$0.8 B</span>
  </td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Very Low</span> <span class="cam">Camillo: Very Low</span></td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Sensors + actuators + connectivity for industrial robots, EVs, medical; small-cap enabler; EV + reshoring dual tailwind</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="PDYN" data-i="75">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">AI Robotics Software</span></td>
  <td class="c-tick"><span class="badge eq">PDYN</span></td>
  <td class="c-name" style="font-size:12px">Palladyne AI</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$0.3 B</span>
  </td>
  <td class="si-cell si-hot" data-si="">~20%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low — speculative micro-cap</span> <span class="cam">Camillo: Moderate — AI + robotics software narrative; name change catalyst visible</span><br>Rebranded to Palladyne AI 2025; autonomous robot software + geospatial AI; DoD contracts; 20% SI = squeeze risk on any positive news</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-powered autonomous robot software; DoD/defence contracts; renamed from Orbital Insight to signal AI pivot; 20% SI micro-cap = high risk/high reward on robotics AI narrative</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="RR" data-i="76">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Aerospace / Defence Robotics</span></td>
  <td class="c-tick"><span class="badge eq">RR</span></td>
  <td class="c-name" style="font-size:12px">Rolls-Royce Holdings (LSE)</td>
  <td class="c-price" data-p="" data-mc="">
    <span class="live-p dim">—</span>
    <span class="live-mc"></span>
  </td>
  <td class="c-mc" data-mc2="">
    <span class="mc-val dim">~$45 B</span>
  </td>
  <td class="si-cell" data-si="">n/a (LSE)</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes="">
    <canvas class="spark" width="90" height="36" title=""></canvas>
  </td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate — UK defence narrative</span> <span class="cam">Camillo: Moderate — UK defence/aerospace re-rating visible on financial social</span><br>UK defence budget at 2.5% GDP = direct tailwind; AI-integrated manufacturing + robotic component inspection</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Jet engines (Trent XWB) + SMR nuclear + defence; UK defence budget surge; AI-integrated manufacturing + robotic inspection of precision components; SMR = long-duration option</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="AVGO" data-i="99">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">AVGO</span></td>
  <td class="c-name" style="font-size:12px">Broadcom Inc</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">$2.0 T</span></td>
  <td class="si-cell si-low" data-si="">~1.2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — AI chip alternative narrative</span> <span class="cam">Camillo: Strong — custom AI chip social narrative massive; Google 2031 deal viral on X</span><br>Google 10yr custom AI chip deal Apr 6 2026; $125M semiconductor research hub UCLA May 21 2026; Samsung collaboration announced May 27 2026; CNBC Club taking profits May 26</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">World's #2 AI chip company ($2T mkt cap); custom AI ASICs for Google, Meta, Apple; VMware software ($6.8B/qtr); 50G PON gateway chip with built-in AI launched May 26; Google 2031 supply agreement = multi-year revenue lock-in; trades at 80x PE; SI ~1.2% = low squeeze risk but high conviction institutional holding</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="ALAB" data-i="100">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core</td>
  <td class="c-tick"><span class="badge eq">ALAB</span></td>
  <td class="c-name" style="font-size:12px">Astera Labs</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$34 B</span></td>
  <td class="si-cell si-med" data-si="">8.43%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High — AI connectivity chip play</span> <span class="cam">Camillo: Moderate — PCIe/CXL data centre narrative building on tech social</span><br>+182% in 52 weeks; 8.43% SI elevated for size; beta 3.36 = high vol; consensus Buy avg PT $192; EV/EBITDA 184x = priced for hypergrowth</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">PCIe / CXL / ethernet connectivity chips enabling AI data centre scale-out; Aries PCIe retimers and Taurus ethernet controllers are mandatory infrastructure for every AI server rack; direct NVDA ecosystem play — Astera chips sit between GPU and memory/network fabric; +182% 52W; 8.43% SI; 171M shares outstanding; Q1 2026 earnings May 5</td>
</tr>
<tr data-sector="AI & Semiconductors — Core" data-ticker="VRT" data-i="101">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI & Semiconductors — Core<br><span style="color:#aaa;font-size:10px">Data Centre Infra</span></td>
  <td class="c-tick"><span class="badge eq">VRT</span></td>
  <td class="c-name" style="font-size:12px">Vertiv Holdings</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$100 B</span></td>
  <td class="si-cell si-low" data-si="">~2.5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High — AI data centre power/cooling play</span> <span class="cam">Camillo: Strong — data centre cooling narrative visible across every tech platform; hyperscaler capex spending viral on social</span><br>+61% 52W mkt cap growth; $100B mkt cap as of May 2026; hyperscaler capex boom ($200B+ each from MSFT/AMZN/GOOGL) = direct VRT revenue; liquid cooling becoming standard</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Critical power and thermal management for AI data centres; PDUs, UPS systems, precision cooling for GPU clusters; every AI data centre build needs Vertiv; liquid cooling supercycle as dense GPU racks hit 100kW+; direct beneficiary of $800B+ hyperscaler capex 2026; +61% mkt cap YoY; 2025 revenue $8B → 2026E ~$10B; operating leverage as mix shifts to higher-margin liquid cooling</td>
</tr>
<tr data-sector="Uranium & Nuclear" data-ticker="VST" data-i="102">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Uranium &amp; Nuclear<br><span style="color:#aaa;font-size:10px">Power / AI Energy</span></td>
  <td class="c-tick"><span class="badge eq">VST</span></td>
  <td class="c-name" style="font-size:12px">Vistra Corp</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$54 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — AI power demand narrative</span> <span class="cam">Camillo: Moderate — electricity/AI power social narrative growing; tech firms signing power deals visible in social</span><br>$54B mkt cap May 27 2026; avg analyst PT $221 vs ~$150 current = 47% upside per consensus; signed significant power agreements with major tech firms; 4.3M retail customers</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Largest competitive power generator in the US; 4.3M retail electricity + gas customers; signed long-term power purchase agreements with hyperscalers for AI data centre power; nuclear + natural gas + solar generation mix; direct AI power demand play without semi valuation risk; avg PT $221 vs ~$150 = 47% analyst upside; CAGR 23.4% mkt cap since 2016; 6 analyst warning signs flagged by GF</td>
</tr>

<tr data-sector="AI &amp; Semiconductors — Core" data-ticker="CRDO" data-i="200">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core<br><span style="color:#aaa;font-size:10px">AI Connectivity</span></td>
  <td class="c-tick"><span class="badge eq">CRDO</span></td>
  <td class="c-name" style="font-size:12px">Credo Technology</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$22 B</span></td>
  <td class="si-cell si-low" data-si="">~5%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — AI connectivity narrative</span> <span class="cam">Camillo: Moderate — AI rack-scale chip demand</span><br>Hans added CRDO 6/18 calls May 29 "building a launchpad"; same analyst (Feroce Research) who called ALAB recommends CRDO for similar move; call volume above normal and directionally bullish (TipRanks May 5); Rothschild Buy initiated Apr 28; earnings Jun 1</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Active electrical cables and SerDes chips for AI data centre interconnect; sits alongside ALAB in the AI rack connectivity theme; $222 price May 28; earnings Jun 1 catalyst; "lots of downside wicks, buyers eating up anything offered at previous ATHs" per Hans; Feroce Research conviction Buy — same analyst whose ALAB call played out</td>
</tr>
<tr data-sector="AI &amp; Semiconductors — Core" data-ticker="DELL" data-i="201">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core<br><span style="color:#aaa;font-size:10px">AI Servers</span></td>
  <td class="c-tick"><span class="badge eq">DELL</span></td>
  <td class="c-name" style="font-size:12px">Dell Technologies</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$90 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — Trump endorsement + massive earnings beat</span> <span class="cam">Camillo: Strong — AI server consumer narrative viral; Trump "buy DELL" + Cramer coverage</span><br>+30% after-hours May 28 on earnings beat; Trump publicly told people to buy DELL; group member: "Trump literally said to buy DELL recently and the stock just keeps going"</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI server infrastructure; PowerEdge GPU servers for AI workloads; NVDA H100/H200/B200 systems integrator; +30% AH May 28 earnings catalyst; Trump publicly endorsed; AI PC transition with Copilot+ devices; direct beneficiary of hyperscaler AI build-out as the OEM layer; ~$90B mkt cap</td>
</tr>
<tr data-sector="AI &amp; Semiconductors — Core" data-ticker="SNOW" data-i="202">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core<br><span style="color:#aaa;font-size:10px">Data Cloud / AI</span></td>
  <td class="c-tick"><span class="badge eq">SNOW</span></td>
  <td class="c-name" style="font-size:12px">Snowflake</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$70 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High — SaaS recovery narrative</span> <span class="cam">Camillo: Moderate — AI data cloud visible in enterprise social</span><br>JC longed SNOW on May 16 and May 28; "See why we longed $SNOW?" referencing agent swarms using software tools; group confirmed RES flipping to Support; SaaS-to-agents transition narrative — SaaS platforms re-pricing by token count not seat count</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI data cloud platform; Cortex AI for LLM-on-Snowflake; SaaS pricing shift from per-seat to per-token = revenue tailwind; agent swarms need data layer = Snowflake direct beneficiary; JC conviction long from $16 area; resistance flipping to support; SaaS rotation candidate alongside NOW, ZS, CRWD</td>
</tr>
<tr data-sector="AI &amp; Semiconductors — Core" data-ticker="CRWD" data-i="203">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core<br><span style="color:#aaa;font-size:10px">Cybersecurity AI</span></td>
  <td class="c-tick"><span class="badge eq">CRWD</span></td>
  <td class="c-name" style="font-size:12px">CrowdStrike</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$110 B</span></td>
  <td class="si-cell si-low" data-si="">2.93%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate-High — cyber narrative + SaaS rotation</span> <span class="cam">Camillo: Strong — cyber breach social narrative constantly viral</span><br>Integrating Claude Compliance API (Anthropic partnership); +47% 52W; 2.93% SI low; $5.25B ARR growing 24%; $5.9B FY27 guide; "already back up" per CryptoEva group; SaaS rotation basket alongside NOW, SNOW, ZS, FTNT</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI-native cybersecurity platform; Falcon platform rebuilt with Claude Compliance API; $5.25B ARR +24% YoY; 2.93% SI; $4.41B net cash; FY27 guide $5.9B; recovering from Jul 2024 outage — trust rebuilt; earnings Jun 3; SaaS rotation candidate + AI security narrative</td>
</tr>
<tr data-sector="AI &amp; Semiconductors — Core" data-ticker="ZS" data-i="204">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core<br><span style="color:#aaa;font-size:10px">Cybersecurity AI</span></td>
  <td class="c-tick"><span class="badge eq">ZS</span></td>
  <td class="c-name" style="font-size:12px">Zscaler</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$50 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — cybersecurity rotation</span> <span class="cam">Camillo: Moderate — zero-trust AI security narrative</span><br>CryptoEva: "RES flipping to Support... $SNOW and $ZS finally follow $CRWD, $FTNT"; 50%+ drawdown from 2025 highs = contrarian setup; Q2 FY26 revenue +26% YoY; ARR $3.36B</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Cloud-native zero-trust security (SASE); best contrarian entry in cybersecurity per analysis — 50%+ drawdown + 26% revenue growth + 25% ARR growth; ARR $3.36B; resistance flipping to support per CryptoEva; SaaS rotation candidate</td>
</tr>
<tr data-sector="AI &amp; Semiconductors — Core" data-ticker="FTNT" data-i="205">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core<br><span style="color:#aaa;font-size:10px">Cybersecurity AI</span></td>
  <td class="c-tick"><span class="badge eq">FTNT</span></td>
  <td class="c-name" style="font-size:12px">Fortinet</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$80 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate</span><br>CryptoEva noted already "back up" alongside CRWD; cheapest quality name in cyber at ~30x forward earnings; 80% gross margins; 41% product revenue growth</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Network security + SASE; cheapest quality cybersecurity stock at ~30x forward earnings, 80% gross margins; 41% product revenue growth; firewall leader with AI-enhanced threat detection; SaaS rotation basket with NOW, SNOW, ZS, CRWD</td>
</tr>
<tr data-sector="Space &amp; Defence" data-ticker="SPCX" data-i="206">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space &amp; Defence<br><span style="color:#aaa;font-size:10px">SpaceX IPO</span></td>
  <td class="c-tick"><span class="badge new">SPCX</span></td>
  <td class="c-name" style="font-size:12px">SpaceX (IPO)</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">Pre-IPO</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$1.75-2 T</span></td>
  <td class="si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Extreme — #1 most anticipated IPO in history</span> <span class="cam">Camillo: Very Strong — SpaceX social narrative dominant across every platform globally</span><br>Target June 12 Nasdaq debut; S-1 filed May 2026; $1.75T valuation target; group says "SpaceX IPO is the top / then dump into midterms"; halo lifting ASTS, RKLB, SPCE, LUNR</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Starlink ($11B+ 2025 revenue) + Starship + xAI merger ($1.25T); $1.75-2T target valuation; Nasdaq June 12 under SPCX; largest IPO in history if priced at target; own the picks-and-shovels (RKLB, ASTS) as liquid proxies pre-IPO; group debate: "SpaceX IPO = tradfi top signal for July rotation"</td>
</tr>
<tr data-sector="Space &amp; Defence" data-ticker="SPCE" data-i="207">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space &amp; Defence<br><span style="color:#aaa;font-size:10px">Space Tourism</span></td>
  <td class="c-tick"><span class="badge eq">SPCE</span></td>
  <td class="c-name" style="font-size:12px">Virgin Galactic</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$165-210 M</span></td>
  <td class="si-cell si-low" data-si="">~8%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: High — SpaceX IPO halo trade</span> <span class="cam">Camillo: Strong — space tourism social narrative massively viral pre-SPCX IPO</span><br>+74% AH on Q1 earnings May 14; Delta spaceplane moved to Phoenix testing facility; Q3 flight test target; Q4 commercial launch; net loss narrowed $84M → $65M; pure SpaceX IPO sympathy trade</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">SpaceX IPO halo trade — retail buying all space names; Delta class spaceplane targeting Q3 flight test + Q4 commercial launch; micro-cap $165M mkt cap = high beta to SpaceX narrative; narrowing losses; Jefferies backing; 52W high $6.64 vs current ~$2-3; speculative momentum play only</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="TXN" data-i="208">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Robotics Semis</span></td>
  <td class="c-tick"><span class="badge eq">TXN</span></td>
  <td class="c-name" style="font-size:12px">Texas Instruments</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$180 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Low — industrial analog chips, not consumer-visible</span><br>Highlighted as Optimus-like robot semiconductor supplier (sensors, power management, motor drive); analogue + embedded = dominant in industrial + EV + robotics power management</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Analog + embedded chips for humanoid robots (power management, motor drive, sensors); flagged specifically as Optimus/humanoid robot semiconductor supplier; dominant market share in industrial analog; re-shoring + EV + robotics triple tailwind; very high FCF generation; ~$180B mkt cap</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="MCHP" data-i="209">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Robotics Semis</span></td>
  <td class="c-tick"><span class="badge eq">MCHP</span></td>
  <td class="c-name" style="font-size:12px">Microchip Technology</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$25 B</span></td>
  <td class="si-cell si-low" data-si="">~3%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low</span><br>Highlighted as Optimus-like robot semiconductor supplier; MCUs for actuators and motor control in humanoid robots; deep robotics design-in pipeline</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Microcontrollers + analog for robot actuators/motor control; flagged as Optimus-like humanoid robot chip supplier; cyclical recovery from 2024-25 inventory correction; design-in pipeline for next-gen robots; ~$25B mkt cap; recovery candidate</td>
</tr>
<tr data-sector="Robotics Value Chain" data-ticker="ON" data-i="210">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Robotics Value Chain<br><span style="color:#aaa;font-size:10px">Robotics Semis</span></td>
  <td class="c-tick"><span class="badge eq">ON</span></td>
  <td class="c-name" style="font-size:12px">ON Semiconductor</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$20 B</span></td>
  <td class="si-cell si-low" data-si="">~4%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Low-Moderate — EV + robot power chips</span><br>Highlighted as Optimus-like robot semiconductor supplier; SiC power chips for EV + robot motor drive; image sensors for robot vision</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">SiC power semiconductors + image sensors for humanoid robots and EVs; flagged as Optimus-like robot chip supplier; SiC automotive design-wins compounding; image sensors for robot perception; ~$20B mkt cap; EV + robotics dual tailwind</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="HACK" data-i="211">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis<br><span style="color:#aaa;font-size:10px">Cybersecurity ETF</span></td>
  <td class="c-tick"><span class="badge eq">HACK</span></td>
  <td class="c-name" style="font-size:12px">Amplify Cybersecurity ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">ETF</span></td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate</span> <span class="cam">Camillo: Moderate — cybersecurity narrative massive in social</span><br>JC: "10 year Livermore Accumulation Cylinder is breaking out" on HACK chart — highest conviction ETF call of May 29 session; holds CRWD, ZS, FTNT, PANW, NET, S</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Cybersecurity basket ETF (CRWD, ZS, FTNT, PANW, NET, S); JC posted chart May 29 calling out 10-year Livermore Accumulation Cylinder breakout — one of his highest-conviction chart reads of the week; diversified cyber exposure as AI expands attack surface and cyber budget</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="QTUM" data-i="212">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis<br><span style="color:#aaa;font-size:10px">Quantum ETF</span></td>
  <td class="c-tick"><span class="badge eq">QTUM</span></td>
  <td class="c-name" style="font-size:12px">Defiance Quantum ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">ETF</span></td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Moderate — quantum hype narrative</span> <span class="cam">Camillo: Moderate — quantum social trend growing</span><br>JC 90-120 day theme ETF list: "Quantum: QTUM (Defiance Quantum ETF)" — clean basket exposure to IONQ, RGTI, QBTS, CCCX alongside quantum computing re-rating</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Defiance Quantum ETF — holds IONQ, RGTI, QBTS, CCCX and broader quantum ecosystem; JC's preferred quantum basket for next 90-120 days; captures entire quantum computing re-rating without single-stock risk; diversified exposure to the NVDA NVQLink quantum integration theme</td>
</tr>
<tr data-sector="Space &amp; Defence" data-ticker="JEDI" data-i="213">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Space &amp; Defence<br><span style="color:#aaa;font-size:10px">Drone ETF</span></td>
  <td class="c-tick"><span class="badge eq">JEDI</span></td>
  <td class="c-name" style="font-size:12px">Defiance Drone &amp; Warfare ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">ETF</span></td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low-Moderate — defence ETF</span> <span class="cam">Camillo: Moderate — drone warfare social narrative massive on every platform</span><br>JC 90-120 day theme ETF list: "Drones: JEDI (Defiance Drone and Modern Warfare)"; "long weapons, short peace" thesis; JC also shared drone tek chart May 29 "Drone tek is gud tek 🚀"</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Drone + modern warfare ETF; JC top ETF pick for next 90-120 days; "long weapons short peace" thesis — NATO re-arming, Ukraine, Middle East, Taiwan; drone tech replacing manpower; holds DPRO, AeroVironment, Shield AI proxies; direct play on JC's stated defence tech theme</td>
</tr>
<tr data-sector="Specialist — Superconductors / SaaS / Semis" data-ticker="NOWL" data-i="214">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Specialist — Superconductors / SaaS / Semis<br><span style="color:#aaa;font-size:10px">Leveraged ETF</span></td>
  <td class="c-tick"><span class="badge new">NOWL</span></td>
  <td class="c-name" style="font-size:12px">ServiceNow 2x Bull ETF</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">small</span></td>
  <td class="si-cell" data-si="">ETF</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low — leveraged ETF niche</span> <span class="cam">Camillo: Moderate — 2x NOW for his ServiceNow conviction</span><br>JC: "$NOWL full send 🚀 as promised" May 18; then "full ported $NOWL at the open today" May 29 — highest-conviction single position declaration of the week; 2x leveraged ServiceNow for JC's "bottom for $NOW" thesis</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">2x leveraged ServiceNow ETF; JC's highest-conviction trade — "full ported NOWL at open" May 29 after "bottom for $NOW" call May 16; leveraged play on NOW SaaS rotation + AI platform re-rating; agent swarms = SaaS-priced-per-token = NOW direct beneficiary; 2x amplifies every NOW move</td>
</tr>
<tr data-sector="AI &amp; Semiconductors — Core" data-ticker="SKM" data-i="215">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">AI &amp; Semiconductors — Core<br><span style="color:#aaa;font-size:10px">Korea Telecom</span></td>
  <td class="c-tick"><span class="badge eq">SKM</span></td>
  <td class="c-name" style="font-size:12px">SK Telecom</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$12 B</span></td>
  <td class="si-cell si-low" data-si="">~2%</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: Low</span> <span class="cam">Camillo: Low — Korean telecom less visible on US social</span><br>Hans: "pump my $SKM plz thx" May 29 — flagged as a late-add alongside CRDO and ALAB; Korean telecom with AI and semiconductor ecosystem exposure; EWY-adjacent Korea tech basket play</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">South Korea's largest telecom; AI platform + semiconductor ecosystem exposure (SK Hynix parent group); ASTS investor; 6G development; Korea tech re-rating play alongside EWY; Hans flagged May 29; ~$12B mkt cap; dividend-paying; EWY basket constituent</td>
</tr>
<tr data-sector="Crypto — AI &amp; DePin" data-ticker="PHA" data-i="300">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI &amp; DePin<br><span style="color:#aaa;font-size:10px">Private AI Inference</span></td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">PHA</span></td>
  <td class="c-name" style="font-size:12px">Phala Network</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$30 M</span></td>
  <td class="si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span> <span class="cam">Camillo: n/a</span><br>JC highest-conviction crypto AI inference play; "sub 30M in trending tokens on CoinGecko — doesn't have the liquidity for what comes next"; flagged 4+ times May 18-26; TEE (Trusted Execution Environment) compute for private AI; "Web3 AI inference szn" thesis leader</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">TEE-based private AI inference on-chain; fixed 1B supply; ~70% mining rewards for compute providers; JC's #1 crypto AI inference pick May 2026; "trending on socials, PHA doesn't have the liquidity for what comes next" = thin float + growing social narrative; Phala = TEE compute network that makes AI inference verifiable and private</td>
</tr>
<tr data-sector="Crypto — AI &amp; DePin" data-ticker="VVV" data-i="301">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI &amp; DePin<br><span style="color:#aaa;font-size:10px">Private AI Inference</span></td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">VVV</span></td>
  <td class="c-name" style="font-size:12px">Venice AI</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">small</span></td>
  <td class="si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span> <span class="cam">Camillo: n/a</span><br>JC: "$VVV 2.0" May 22 alongside $PHA; also flagged in "Phill the wick" post — deflationary tokenomics (~100M initial, burns via revenue buybacks); staking yields ~15% + DIEM credits for AI usage; AskVenice decentralised private AI inference platform</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Decentralised private AI inference platform; deflationary (~100M initial supply, burns via revenue buybacks); staking 15% APY + mints DIEM credits for AI usage; JC Web3 AI inference szn list; pairs with PHA in private inference narrative; revenue buybacks = real yield; competing with centralised AI API providers</td>
</tr>
<tr data-sector="Crypto — AI &amp; DePin" data-ticker="NEAR" data-i="302">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI &amp; DePin<br><span style="color:#aaa;font-size:10px">AI Agent L1</span></td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">NEAR</span></td>
  <td class="c-name" style="font-size:12px">NEAR Protocol</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$5 B</span></td>
  <td class="si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span> <span class="cam">Camillo: n/a</span><br>JC Web3 AI inference list; "S-tier: one of the strongest architectures for AI Agents right now, agentic payments, low fees, chain abstraction" per arndxt_xo; Grayscale onboarded; AI agent payments native to chain</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">AI agent L1 with native chain abstraction + low fees; S-tier for AI agent infrastructure per privacy/AI thesis analysts; NEAR AI agents pay for compute, settlement in TEE setups; Grayscale product = institutional onramp; usage-driven tokenomics for AI inference; agent swarms narrative = NEAR demand driver</td>
</tr>
<tr data-sector="Crypto — AI &amp; DePin" data-ticker="OLAS" data-i="303">
  <td class="c-sec" style="font-size:10px;color:#777;line-height:1.3">Crypto — AI &amp; DePin<br><span style="color:#aaa;font-size:10px">AI Agent Protocol</span></td>
  <td class="c-tick"><span class="badge new" style="background:#EEEDFE;color:#3C3489">OLAS</span></td>
  <td class="c-name" style="font-size:12px">Autonolas</td>
  <td class="c-price" data-p="" data-mc=""><span class="live-p dim">—</span><span class="live-mc"></span></td>
  <td class="c-mc" data-mc2=""><span class="mc-val dim">~$0.5 B</span></td>
  <td class="si-cell" data-si="">n/a</td>
  <td class="c-chg" data-chg="">—</td>
  <td class="c-hl" data-hi="" data-lo="">—</td>
  <td class="c-spark" data-closes=""><canvas class="spark" width="90" height="36" title=""></canvas></td>
  <td class="c-soc" style="font-size:11px;line-height:1.4"><span class="wsb">WSB: n/a — crypto</span> <span class="cam">Camillo: n/a</span><br>JC Web3 AI inference list; Autonolas = decentralised autonomous AI agent network; agent swarms infrastructure; composable multi-agent coordination on-chain</td>
  <td class="c-thesis" style="font-size:11px;line-height:1.45">Decentralised autonomous AI agent network; enables multi-agent coordination and composable agent swarms on-chain; JC's agent swarm thesis = "next meta after inference"; OLAS is the protocol layer for AI agents to interact, coordinate and transact; ~$0.5B mkt cap = small relative to narrative</td>
</tr>
</tbody>
</table>

<p class="note">
  <strong>Price &amp; charts</strong> — Yahoo Finance, ~15min delayed for US equities, ~20min HK/LSE. Auto-refreshes every 90s.
  <strong>Short interest</strong> — FINRA official data via StockAnalysis; published twice monthly. Figures from May 2026.
  <strong>WSB</strong> — live from Tradestie Reddit API. <strong>4W H/L</strong> — rolling 30 calendar days.
  <strong>7D Trend</strong> — 7 most recent daily closes; green = net up, red = net down over period.
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
  'AVGO':'AVGO',
  'ALAB':'ALAB',
  'VRT':'VRT',
  'VST':'VST',
  'CRDO':'CRDO',
  'DELL':'DELL',
  'SNOW':'SNOW',
  'CRWD':'CRWD',
  'ZS':'ZS',
  'FTNT':'FTNT',
  'SPCE':'SPCE',
  'TXN':'TXN',
  'MCHP':'MCHP',
  'ON':'ON',
  'HACK':'HACK',
  'QTUM':'QTUM',
  'JEDI':'JEDI',
  'NOWL':'NOWL',
  'SKM':'SKM'
};

const WSB_URL = 'https://tradestie.com/api/v1/apps/reddit';
let wsbData = {};
let sortCol = -1, sortAsc = true, activeF = 'all';

// ══════════════════════════════════════════════════════════════
// FETCH
// ══════════════════════════════════════════════════════════════
// ── CORS proxies tried in order until one works ──────────────────
const PROXIES = [
  sym => `https://query1.finance.yahoo.com/v8/finance/chart/${sym}?interval=1d&range=30d`,
  sym => `https://query2.finance.yahoo.com/v8/finance/chart/${sym}?interval=1d&range=30d`,
  sym => `https://corsproxy.io/?url=${encodeURIComponent('https://query1.finance.yahoo.com/v8/finance/chart/'+sym+'?interval=1d&range=30d')}`,
  sym => `https://api.allorigins.win/raw?url=${encodeURIComponent('https://query1.finance.yahoo.com/v8/finance/chart/'+sym+'?interval=1d&range=30d')}`,
];

async function fetchTicker(sym) {
  for (const proxyFn of PROXIES) {
    try {
      const url = proxyFn(sym);
      const r = await fetch(url, {
        headers: {
          'Accept': 'application/json',
          'User-Agent': 'Mozilla/5.0'
        },
        signal: AbortSignal.timeout(8000)
      });
      if (!r.ok) continue;
      const j = await r.json();
      const res = j?.chart?.result?.[0];
      if (!res) continue;
      const m = res.meta;
      if (!m?.regularMarketPrice) continue;
      const closes = (res.indicators?.quote?.[0]?.close || []).filter(v => v != null);
      const hi4w = closes.length ? Math.max(...closes) : null;
      const lo4w = closes.length ? Math.min(...closes) : null;
      const last7 = closes.slice(-7);
      const prev = m.chartPreviousClose || m.previousClose;
      return {
        price:  m.regularMarketPrice,
        prev,
        shares: m.sharesOutstanding,
        ccy:    m.currency || 'USD',
        hi4w, lo4w, last7,
        chgPct: prev ? (m.regularMarketPrice - prev) / prev * 100 : null
      };
    } catch(e) { continue; }
  }
  return null; // all proxies failed
}

async function fetchWSB() {
  try {
    const r = await fetch(WSB_URL);
    if (!r.ok) return {};
    const arr = await r.json();
    const out = {};
    arr.forEach((x,i) => { out[x.ticker] = {rank:i+1, mentions:x.no_of_comments, sentiment:x.sentiment}; });
    return out;
  } catch(e) { return {}; }
}

// ══════════════════════════════════════════════════════════════
// FORMAT
// ══════════════════════════════════════════════════════════════
function fPrice(v, ccy) {
  if (v == null) return '—';
  if (ccy === 'GBp') return v.toFixed(0) + 'p';
  const s = ccy === 'HKD' ? 'HK$' : '$';
  return s + (v < 10 ? v.toFixed(3) : v.toFixed(2));
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
  if (p == null) return '<span class="flat">—</span>';
  const c = p>0.05?'pos':p<-0.05?'neg':'flat';
  return `<span class="${c}">${p>0?'+':''}${p.toFixed(2)}%</span>`;
}

// ══════════════════════════════════════════════════════════════
// SPARKLINE — draws 7-day trendline on canvas
// ══════════════════════════════════════════════════════════════
function drawSpark(canvas, closes) {
  if (!closes || closes.length < 2) {
    const ctx = canvas.getContext('2d');
    ctx.clearRect(0,0,canvas.width,canvas.height);
    ctx.fillStyle = '#ddd';
    ctx.font = '9px system-ui';
    ctx.fillText('no data', 4, 20);
    return;
  }
  const W = canvas.width, H = canvas.height;
  const pad = 4;
  const ctx = canvas.getContext('2d');
  ctx.clearRect(0,0,W,H);

  const mn = Math.min(...closes), mx = Math.max(...closes);
  const range = mx - mn || mx * 0.02 || 1;
  const up = closes[closes.length-1] >= closes[0];
  const colour = up ? '#16a34a' : '#dc2626';
  const fillColour = up ? 'rgba(22,163,74,0.12)' : 'rgba(220,38,38,0.10)';

  const xs = closes.map((_,i) => pad + i * (W - pad*2) / (closes.length-1));
  const ys = closes.map(v => H - pad - (v - mn) / range * (H - pad*2));

  // Fill area under line
  ctx.beginPath();
  ctx.moveTo(xs[0], H - pad);
  xs.forEach((x,i) => ctx.lineTo(x, ys[i]));
  ctx.lineTo(xs[xs.length-1], H - pad);
  ctx.closePath();
  ctx.fillStyle = fillColour;
  ctx.fill();

  // Line
  ctx.beginPath();
  ctx.moveTo(xs[0], ys[0]);
  for (let i=1; i<xs.length; i++) ctx.lineTo(xs[i], ys[i]);
  ctx.strokeStyle = colour;
  ctx.lineWidth = 2;
  ctx.lineJoin = 'round';
  ctx.stroke();

  // End dot
  ctx.beginPath();
  ctx.arc(xs[xs.length-1], ys[ys.length-1], 3, 0, Math.PI*2);
  ctx.fillStyle = colour;
  ctx.fill();

  // Pct change label
  const pct = ((closes[closes.length-1] - closes[0]) / closes[0] * 100);
  ctx.fillStyle = colour;
  ctx.font = `bold 9px system-ui`;
  ctx.textAlign = 'right';
  ctx.fillText((pct>0?'+':'')+pct.toFixed(1)+'%', W-2, 10);
  ctx.textAlign = 'left';

  // Tooltip data
  canvas.title = closes.map((v,i) => `Day ${i+1}: ${v.toFixed(2)}`).join(' | ');
}

// ══════════════════════════════════════════════════════════════
// UPDATE ROW
// ══════════════════════════════════════════════════════════════
function updateRow(badge, sym, d) {
  const rows = document.querySelectorAll('#wtb tr');
  for (const row of rows) {
    const b = row.querySelector('.badge');
    if (!b || b.textContent.trim() !== badge) continue;

    const ccy = d.ccy;
    const mcap = d.shares ? d.price * d.shares : null;

    // Price cell
    const pc = row.cells[3];
    pc.dataset.p = d.price || 0;
    pc.innerHTML = `<span class="live-p">${fPrice(d.price,ccy)}</span>`;

    // Mkt Cap cell
    const mc = row.cells[4];
    mc.dataset.mc2 = mcap || 0;
    mc.innerHTML = `<span class="mc-val">${fMcap(mcap,ccy) || '—'}</span>`;

    // Day change
    const cc = row.cells[6];
    cc.dataset.chg = d.chgPct ?? '';
    cc.innerHTML = fChg(d.chgPct);

    // 4W H/L
    const hlc = row.cells[7];
    if (d.hi4w && d.lo4w) {
      const barPct = d.hi4w !== d.lo4w
        ? Math.round((d.price - d.lo4w)/(d.hi4w - d.lo4w)*100) : 50;
      const fill = Math.max(0,Math.min(100,barPct));
      hlc.dataset.hi = d.hi4w;
      hlc.dataset.lo = d.lo4w;
      hlc.innerHTML = `
        <span class="hl-hi">${fPrice(d.hi4w,ccy)}</span>
        <span class="hl-lo"> / ${fPrice(d.lo4w,ccy)}</span>
        <div class="hl-pbar"><div class="hl-pfill" style="width:${fill}%"></div></div>`;
    }

    // Sparkline
    const sc = row.cells[8];
    const canvas = sc.querySelector('canvas.spark');
    if (canvas && d.last7 && d.last7.length) {
      sc.dataset.closes = JSON.stringify(d.last7);
      drawSpark(canvas, d.last7);
    }

    // WSB live badge
    const cleanSym = sym.replace('.HK','').replace('.L','');
    const wd = wsbData[cleanSym];
    const socialCell = row.cells[9];
    if (socialCell) {
      const wsbHtml = wd
        ? `<span class="wsb-live" style="background:${wd.sentiment==='Bullish'?'#16a34a':'#dc2626'}">#${wd.rank} · ${wd.mentions} mentions · ${wd.sentiment}</span>`
        : `<span class="wsb-live none">not in WSB top 50</span>`;
      const existing = socialCell.querySelector('.wsb-live');
      if (existing) existing.outerHTML = wsbHtml;
      else socialCell.innerHTML = wsbHtml + '<br>' + socialCell.innerHTML;
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
  const entries = Object.entries(TM);
  for (let i=0; i<entries.length; i+=6) {
    const batch = entries.slice(i, i+6);
    await Promise.all(batch.map(async ([badge, sym]) => {
      const d = await fetchTicker(sym);
      if (d) updateRow(badge, sym, d);
    }));
    if (i+6 < entries.length) await new Promise(r=>setTimeout(r,220));
  }
  const t = new Date().toLocaleTimeString();
  document.getElementById('lupd').textContent = t;
  setDot('live', 'Live · ' + t);
}

function setDot(state, msg) {
  const d = document.getElementById('sdot');
  const t = document.getElementById('stxt');
  if(d) d.className = 'dot ' + state;
  if(t) t.textContent = msg;
}

// Debug helper — call debugFetch('NVDA') in console to test
window.debugFetch = async function(sym) {
  console.log('Testing fetch for', sym);
  for (const [i, fn] of PROXIES.entries()) {
    const url = fn(sym);
    console.log(`Proxy ${i}:`, url);
    try {
      const r = await fetch(url, {signal: AbortSignal.timeout(8000)});
      console.log(`  Status: ${r.status}`);
      if (r.ok) {
        const j = await r.json();
        console.log(`  Price: ${j?.chart?.result?.[0]?.meta?.regularMarketPrice}`);
      }
    } catch(e) { console.log(`  Error: ${e.message}`); }
  }
};

// ══════════════════════════════════════════════════════════════
// SORT — numeric-aware, all columns
// ══════════════════════════════════════════════════════════════
function srt(col) {
  const tbody = document.getElementById('wtb');
  const rows = Array.from(tbody.querySelectorAll('tr'));
  const ths = document.querySelectorAll('#wt thead th');
  ths.forEach(h=>h.classList.remove('asc','desc'));

  const asc = sortCol===col ? !sortAsc : true;
  sortCol=col; sortAsc=asc;
  ths[col].classList.add(asc?'asc':'desc');

  rows.sort((a,b) => {
    let av = getVal(a,col), bv = getVal(b,col);
    const an = parseFloat(av), bn = parseFloat(bv);
    if (!isNaN(an) && !isNaN(bn)) {av=an; bv=bn;}
    return av<bv ? (asc?-1:1) : av>bv ? (asc?1:-1) : 0;
  });
  tbody.append(...rows);
  updateCount();
}

function getVal(row, col) {
  const c = row.cells[col];
  if (!c) return '';
  switch(col) {
    case 3: return c.dataset.p || '0';
    case 4: return c.dataset.mc2 || '0';
    case 5: {
      const t = c.innerText.replace(/[^0-9.]/g,'');
      return t || '0';
    }
    case 6: return c.dataset.chg || '0';
    case 7: return c.dataset.hi  || '0';
    default: return c.innerText.trim().toLowerCase();
  }
}

// ══════════════════════════════════════════════════════════════
// FILTER + SEARCH
// ══════════════════════════════════════════════════════════════
function filt(btn) {
  document.querySelectorAll('.fbtn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  activeF = btn.dataset.f;
  applyFilters();
}

function applyFilters() {
  const q = (document.getElementById('srch').value||'').toLowerCase().trim();
  document.querySelectorAll('#wtb tr').forEach(row => {
    const sec = row.dataset.sector || '';
    const txt = row.innerText.toLowerCase();
    const sm = activeF==='all' || sec===activeF;
    const qm = !q || txt.includes(q);
    row.classList.toggle('hide', !(sm && qm));
  });
  updateCount();
}

function updateCount() {
  const total   = document.querySelectorAll('#wtb tr').length;
  const visible = document.querySelectorAll('#wtb tr:not(.hide)').length;
  const el = document.getElementById('rcnt');
  if (el) el.textContent = visible===total ? total+' stocks' : visible+' / '+total+' stocks';
}

// ══════════════════════════════════════════════════════════════
// INIT
// ══════════════════════════════════════════════════════════════
document.addEventListener('DOMContentLoaded', () => {
  updateCount();
  refresh();
  setInterval(refresh, 90000);
});
</script>
</body>
</html>
