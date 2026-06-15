[index (2).html](https://github.com/user-attachments/files/28978543/index.2.html)
<!DOCTYPE html>
<html lang="pt-BR" style="background:#0F1729">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>US Stock Screener — Preço Justo & Indicadores</title>
  <meta name="description" content="Análise fundamentalista das maiores ações americanas com preço justo por DCF, P/L, ROE, margem líquida e mais.">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg:        #0F1729;
      --bg2:       #151E35;
      --bg3:       #1A2340;
      --border:    #222C4A;
      --border2:   #2A3555;
      --txt:       #E2E8F5;
      --txt2:      #7E8DB0;
      --txt3:      #4A5578;
      --accent:    #4F8EF7;
      --green:     #1DB87A;
      --red:       #E05252;
      --yellow:    #D4952A;
      --green-bg:  #0E2E20;
      --red-bg:    #2E1414;
      --yellow-bg: #2B2010;
      --font:      'Inter', system-ui, sans-serif;
      --mono:      'DM Mono', monospace;
      --radius:    6px;
      --radius-lg: 10px;
    }
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { font-size: 14px; scroll-behavior: smooth; background: #0F1729; }
    table, tbody, tbody tr { background: #0F1729; }
    tbody tr:nth-child(even) { background: #0e1220; }
    tbody tr:hover { background: #151E35 !important; }
    .table-wrap { background: #0F1729; }
    input, select { background-color: #1A2340 !important; color: #E2E8F5 !important; }
    body { font-family: var(--font); background: var(--bg); color: var(--txt); min-height: 100vh; }

    /* ═══════════════════════════════════════
       AD BANNERS
    ═══════════════════════════════════════ */
    .ad-banner {
      width: 100%;
      background: var(--bg2);
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 12px 16px;
      min-height: 90px;
      position: relative;
    }
    .ad-banner.ad-bottom {
      border-bottom: none;
      border-top: 1px solid var(--border);
      margin-top: 0;
    }
    .ad-placeholder {
      width: 100%;
      max-width: 728px;
      min-height: 60px;
      border: 1px dashed var(--border2);
      border-radius: var(--radius);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      color: var(--txt3);
      font-size: 11px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }
    .ad-placeholder::before { content: ''; width: 14px; height: 14px; border: 1.5px dashed var(--txt3); border-radius: 3px; flex-shrink: 0; }

    /* ═══════════════════════════════════════
       LAYOUT
    ═══════════════════════════════════════ */
    .site-header {
      padding: 20px 20px 14px;
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 10px;
    }
    .site-header h1 { font-size: 18px; font-weight: 600; color: var(--txt); letter-spacing: -0.02em; }
    .site-header h1 span { color: var(--accent); }
    .site-header p { font-size: 12px; color: var(--txt2); margin-top: 3px; max-width: 500px; line-height: 1.5; }
    .badge { display: inline-flex; align-items: center; background: #1C2545; border: 1px solid #2D3A68; color: var(--accent); font-size: 11px; padding: 2px 10px; border-radius: 20px; font-weight: 500; margin-left: 8px; }

    .controls {
      display: flex; gap: 8px; padding: 12px 20px;
      flex-wrap: wrap; align-items: center;
      border-bottom: 1px solid var(--border);
      background: var(--bg2);
    }
    .controls input[type=text] {
      flex: 1; min-width: 160px; height: 32px; font-size: 12px;
      padding: 0 12px; border-radius: var(--radius);
      border: 1px solid var(--border2); background: var(--bg3);
      color: var(--txt); font-family: var(--font);
    }
    .controls input[type=text]:focus { outline: none; border-color: var(--accent); }
    .controls input::placeholder { color: var(--txt3); }
    .controls select {
      height: 32px; font-size: 12px; padding: 0 8px;
      border-radius: var(--radius); border: 1px solid var(--border2);
      background: var(--bg3); color: var(--txt); cursor: pointer;
      font-family: var(--font);
    }
    .btn {
      height: 32px; padding: 0 14px; font-size: 12px; font-weight: 500;
      border-radius: var(--radius); cursor: pointer; border: 1px solid;
      font-family: var(--font); white-space: nowrap; transition: opacity 0.15s;
    }
    .btn:hover { opacity: 0.82; }
    .btn-primary { background: var(--accent); border-color: var(--accent); color: #fff; }
    .btn-ghost { background: transparent; border-color: var(--border2); color: var(--txt2); }

    .stats-bar {
      display: flex; gap: 6px; padding: 8px 20px;
      flex-wrap: wrap; align-items: center;
      background: var(--bg); border-bottom: 1px solid var(--border);
    }
    .chip {
      font-size: 11px; color: var(--txt2); padding: 3px 10px;
      border-radius: 20px; border: 1px solid var(--border2);
      background: var(--bg2); white-space: nowrap;
    }
    .chip b { font-weight: 500; }
    .chip.c-green { border-color: #1C4433; background: var(--green-bg); }
    .chip.c-green b { color: var(--green); }
    .chip.c-red { border-color: #401C1C; background: var(--red-bg); }
    .chip.c-red b { color: var(--red); }

    .legend {
      display: flex; gap: 14px; padding: 7px 20px;
      border-bottom: 1px solid var(--border);
      background: var(--bg2); flex-wrap: wrap; align-items: center;
    }
    .legend-lbl { font-size: 11px; color: var(--txt3); font-weight: 500; text-transform: uppercase; letter-spacing: 0.05em; }
    .legend-item { display: flex; align-items: center; gap: 5px; font-size: 11px; color: var(--txt2); }
    .legend-dot { width: 9px; height: 9px; border-radius: 2px; }

    /* ═══════════════════════════════════════
       TABLE
    ═══════════════════════════════════════ */
    .table-wrap { overflow-x: auto; }
    table { width: 100%; border-collapse: collapse; font-size: 12px; }
    thead th {
      text-align: left; padding: 9px 10px;
      font-size: 10px; font-weight: 500; color: var(--txt3);
      border-bottom: 1px solid var(--border2);
      white-space: nowrap; cursor: pointer; user-select: none;
      background: var(--bg2); letter-spacing: 0.04em; text-transform: uppercase;
      position: sticky; top: 0; z-index: 10;
    }
    thead th:hover { color: var(--txt); }
    thead th.sorted-asc::after  { content: ' ↑'; color: var(--accent); }
    thead th.sorted-desc::after { content: ' ↓'; color: var(--accent); }
    tbody tr { border-bottom: 1px solid var(--border); cursor: pointer; transition: background 0.1s; }
    tbody tr:hover { background: var(--bg2); }
    tbody td { padding: 9px 10px; vertical-align: middle; white-space: nowrap; }

    .sym { font-family: var(--mono); font-weight: 500; font-size: 13px; color: var(--accent); }
    .name-cell { font-size: 11px; color: var(--txt2); max-width: 140px; overflow: hidden; text-overflow: ellipsis; }
    .sec-badge {
      display: inline-block; font-size: 10px; padding: 2px 6px;
      border-radius: 3px; background: var(--bg3);
      color: var(--txt3); border: 1px solid var(--border);
      max-width: 110px; overflow: hidden; text-overflow: ellipsis;
    }
    .up  { color: var(--green); font-weight: 500; }
    .dn  { color: var(--red);   font-weight: 500; }
    .neu { color: var(--txt2); }

    /* termômetro na linha */
    .therm-cell { display: flex; flex-direction: column; gap: 3px; min-width: 120px; }
    .therm-prices { display: flex; gap: 6px; align-items: baseline; }
    .therm-track {
      height: 7px; border-radius: 4px;
      background: var(--bg3); border: 1px solid var(--border);
      position: relative; overflow: visible;
    }
    .therm-gradient { position: absolute; inset: 0; border-radius: 4px; background: linear-gradient(to right, #1DB87A44, #D4952A44, #E0525244); }
    .therm-needle {
      position: absolute; top: 50%; transform: translate(-50%,-50%);
      width: 13px; height: 13px; border-radius: 50%;
      border: 2px solid var(--bg); z-index: 2;
    }
    .therm-pct { font-size: 10px; font-weight: 500; font-family: var(--mono); }

    /* barra margem liq */
    .mbar { display: flex; align-items: center; gap: 5px; min-width: 85px; }
    .mbar-track { flex: 1; height: 5px; border-radius: 3px; background: var(--bg3); border: 1px solid var(--border); overflow: hidden; }
    .mbar-fill { height: 100%; border-radius: 3px; }
    .mbar-val { font-size: 11px; font-family: var(--mono); min-width: 40px; text-align: right; }

    .loading { text-align: center; padding: 3rem; color: var(--txt2); font-size: 13px; }
    .spinner { display: inline-block; width: 16px; height: 16px; border: 2px solid var(--border2); border-top-color: var(--accent); border-radius: 50%; animation: spin 0.8s linear infinite; margin-right: 8px; vertical-align: middle; }
    @keyframes spin { to { transform: rotate(360deg); } }

    /* ═══════════════════════════════════════
       MODAL
    ═══════════════════════════════════════ */
    .modal-bg {
      position: fixed; inset: 0; background: rgba(0,0,0,0.65);
      display: flex; align-items: center; justify-content: center;
      z-index: 999; padding: 1rem;
    }
    .modal {
      background: var(--bg2); border-radius: var(--radius-lg);
      border: 1px solid var(--border2); width: 100%; max-width: 540px;
      max-height: 88vh; overflow-y: auto;
    }
    .modal-header {
      padding: 1.1rem 1.25rem 0.9rem;
      border-bottom: 1px solid var(--border);
      display: flex; justify-content: space-between; align-items: flex-start;
      position: sticky; top: 0; background: var(--bg2); z-index: 2;
    }
    .modal-body { padding: 1rem 1.25rem 1.5rem; }
    .btn-close { background: none; border: none; font-size: 20px; cursor: pointer; color: var(--txt3); padding: 2px; line-height: 1; }
    .btn-close:hover { color: var(--txt); }
    .mgrid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 1rem; }
    .mc { background: var(--bg3); border-radius: var(--radius); padding: 0.7rem 0.9rem; border: 1px solid var(--border); }
    .mc .lbl { font-size: 10px; color: var(--txt3); margin-bottom: 3px; text-transform: uppercase; letter-spacing: 0.04em; }
    .mc .val { font-size: 18px; font-weight: 600; color: var(--txt); font-family: var(--mono); }
    .mc .val.sm { font-size: 13px; }
    .sec-title { font-size: 10px; font-weight: 500; color: var(--txt3); text-transform: uppercase; letter-spacing: 0.05em; margin: 1rem 0 0.4rem; }
    .irow { display: flex; justify-content: space-between; align-items: center; padding: 6px 0; border-bottom: 1px solid var(--border); font-size: 12px; }
    .irow:last-child { border-bottom: none; }
    .irow .il { color: var(--txt2); }

    .dcf-box { border-radius: var(--radius); padding: 1rem; margin-top: 0.75rem; border: 1px solid var(--border2); background: var(--bg3); }
    .dcf-therm-track { height: 18px; border-radius: 9px; position: relative; overflow: hidden; margin-top: 10px; }
    .dcf-therm-bg { position: absolute; inset: 0; background: linear-gradient(to right, #1DB87A 0%, #D4952A 50%, #E05252 100%); opacity: 0.22; }
    .dcf-needle {
      position: absolute; top: 50%; transform: translate(-50%,-50%);
      width: 22px; height: 22px; border-radius: 50%;
      border: 3px solid var(--bg2); z-index: 2;
      transition: left 0.6s cubic-bezier(.4,0,.2,1);
    }
    .dcf-labels { display: flex; justify-content: space-between; font-size: 10px; color: var(--txt3); margin-top: 5px; }
    .verdict-pill { display: inline-flex; align-items: center; gap: 5px; margin-top: 8px; padding: 4px 12px; border-radius: 20px; font-size: 12px; font-weight: 500; }
    .vp-buy  { background: var(--green-bg); color: var(--green); border: 1px solid #1C4433; }
    .vp-sell { background: var(--red-bg);   color: var(--red);   border: 1px solid #401C1C; }
    .vp-fair { background: #112040;          color: var(--accent); border: 1px solid #1A2E56; }
    .modal-btn {
      margin-top: 0.9rem; width: 100%; height: 36px; font-size: 12px;
      border-radius: var(--radius); border: 1px solid var(--border2);
      background: var(--bg); color: var(--txt2); cursor: pointer;
      font-family: var(--font); transition: all 0.15s;
    }
    .modal-btn:hover { background: var(--bg3); color: var(--txt); border-color: var(--accent); }

    footer {
      padding: 16px 20px; border-top: 1px solid var(--border);
      text-align: center; font-size: 11px; color: var(--txt3);
      background: var(--bg2); line-height: 1.7;
    }
    footer a { color: var(--txt2); text-decoration: none; }
    footer a:hover { color: var(--txt); }

    @media (max-width: 640px) {
      .site-header { padding: 14px; }
      .controls, .stats-bar, .legend { padding: 8px 12px; }
      .mgrid { grid-template-columns: 1fr; }
    }
    .pagination { display:flex; align-items:center; justify-content:space-between; padding:10px 20px; border-top:1px solid #222C4A; background:#151E35; flex-wrap:wrap; gap:8px; }
    .pagination-info { font-size:11px; color:#4A5578; }
    .pagination-info b { color:#7E8DB0; }
    .page-btns { display:flex; gap:4px; }
    .page-btn { height:28px; min-width:28px; padding:0 8px; font-size:11px; border-radius:5px; border:1px solid #2A3555; background:#0F1729; color:#7E8DB0; cursor:pointer; font-family:'Inter',sans-serif; transition:all 0.15s; }
    .page-btn:hover:not(:disabled) { background:#1A2340; color:#E2E8F5; }
    .page-btn.active { background:#1C2545; border-color:#4F8EF7; color:#4F8EF7; font-weight:500; }
    .page-btn:disabled { opacity:0.3; cursor:not-allowed; }
    .load-progress { font-size:11px; color:#4F8EF7; padding:6px 20px 8px; background:#0F1729; border-bottom:1px solid #222C4A; display:none; }
    .load-progress-bar { height:3px; background:#222C4A; margin-top:5px; border-radius:2px; overflow:hidden; }
    .load-progress-fill { height:100%; background:#4F8EF7; border-radius:2px; transition:width 0.3s; width:0%; }
    .table-topnav { display:flex; align-items:center; justify-content:space-between; padding:7px 12px; background:#151E35; border-bottom:1px solid #222C4A; flex-wrap:wrap; gap:6px; }
    .table-topnav .pagination-info { font-size:11px; color:#4A5578; }
    .table-topnav .pagination-info b { color:#7E8DB0; }
    .table-topnav .page-btns { display:flex; gap:4px; }
  </style>
</head>
<body style="background:#0F1729;color:#E2E8F5;min-height:100vh">
<style>
html,body,div,main,section,table,tbody,tr,td,th,thead { background-color: #0F1729 !important; color: #E2E8F5; }
thead th { background-color: #151E35 !important; color: #7E8DB0 !important; }
tbody tr:hover td { background-color: #151E35 !important; }
.table-wrap, .controls, .stats-bar, .legend, .site-header, .ad-banner, footer { background-color: #151E35 !important; }
.controls { background-color: #151E35 !important; }
.stats-bar { background-color: #0F1729 !important; }
input[type=text], select { background-color: #1A2340 !important; color: #E2E8F5 !important; border-color: #2A3555 !important; }
</style>

  <!-- ██████████  AD BANNER TOPO  ██████████ -->
  <div class="ad-banner" id="ad-top" aria-label="Espaço publicitário">
    <!--
      CARBON ADS — cole aqui o código do Carbon Ads depois de aprovado:
      <script async type="text/javascript" src="//cdn.carbonads.com/carbon.js?serve=SEU_CÓDIGO_AQUI&placement=seusite" id="_carbonads_js"></script>

      GOOGLE ADSENSE — ou cole aqui o tag do AdSense:
      <ins class="adsbygoogle" style="display:inline-block;width:728px;height:90px" data-ad-client="ca-pub-XXXXXXXX" data-ad-slot="XXXXXXXX"></ins>
    -->
    <div class="ad-placeholder">Espaço publicitário — 728×90 (Leaderboard)</div>
  </div>

  <!-- ██████████  CABEÇALHO  ██████████ -->
  <header class="site-header">
    <div>
      <h1>US Stock <span>Screener</span> <span class="badge" id="count-badge">0 ações</span></h1>
      <p>Indicadores fundamentalistas + preço justo por Fluxo de Caixa Descontado (DCF) para as maiores empresas americanas.</p>
    </div>
    <div style="display:flex;gap:8px;align-items:center;flex-wrap:wrap">
      <button class="btn btn-ghost" onclick="exportCSV()">⬇ Exportar CSV</button>
      <button class="btn btn-primary" onclick="loadData()">⟳ Atualizar dados</button>
    </div>
  </header>

  <!-- ██████████  CONTROLES  ██████████ -->
  <div class="controls">
    <input type="text" id="search" placeholder="🔍  Buscar por ticker ou nome..." oninput="renderTable()">
    <select id="filter-sector" onchange="renderTable()">
      <option value="">Todos os setores</option>
    </select>
    <select id="filter-verdict" onchange="renderTable()">
      <option value="">Todos os veredictos</option>
      <option value="sub">Subvalorizada</option>
      <option value="fair">Preço Justo</option>
      <option value="over">Sobrevalorizada</option>
    </select>
    <select id="filter-pe" onchange="renderTable()">
      <option value="">P/L — todos</option>
      <option value="low">P/L abaixo de 15</option>
      <option value="mid">P/L 15–40</option>
      <option value="high">P/L acima de 40</option>
    </select>
    <select id="per-page" onchange="changePerPage()">
      <option value="1">1 empresa</option>
      <option value="5">5 empresas</option>
      <option value="10">10 empresas</option>
      <option value="20" selected>20 empresas</option>
      <option value="30">30 empresas</option>
      <option value="40">40 empresas</option>
      <option value="50">50 empresas</option>
    </select>
  </div>

  <!-- ██████████  STATS + LEGENDA  ██████████ -->
  <div class="stats-bar">
    <span class="chip c-green">Subvalorizadas: <b id="s-under">—</b></span>
    <span class="chip">Preço Justo: <b id="s-fair">—</b></span>
    <span class="chip c-red">Sobrevalorizadas: <b id="s-over">—</b></span>
    <span class="chip">Atualizado: <b id="s-updated">demo</b></span>
  </div>

  <div class="legend">
    <span class="legend-lbl">Termômetro DCF:</span>
    <span class="legend-item"><span class="legend-dot" style="background:var(--green)"></span> Subvalorizada (&gt;15% abaixo do justo)</span>
    <span class="legend-item"><span class="legend-dot" style="background:var(--yellow)"></span> Preço Justo (±15%)</span>
    <span class="legend-item"><span class="legend-dot" style="background:var(--red)"></span> Sobrevalorizada (&gt;15% acima)</span>
  </div>

  <!-- ██████████  LOADING  ██████████ -->
  <div id="loading-msg" class="loading" style="display:none">
    <span class="spinner"></span>Buscando dados do Yahoo Finance...
  </div>
  <div class="load-progress" id="load-progress">
    <span id="load-progress-text">Carregando...</span>
    <div class="load-progress-bar"><div class="load-progress-fill" id="load-progress-fill"></div></div>
  </div>

  <!-- ██████████  TABELA  ██████████ -->
  <div class="table-wrap">
    <!-- Navegação topo -->
    <div class="table-topnav" id="table-topnav-top">
      <div class="pagination-info" id="pagination-info-top">—</div>
      <div class="page-btns" id="page-btns-top"></div>
      <select id="per-page-top" onchange="syncPerPage('top')" style="height:26px;font-size:11px;padding:0 6px;border-radius:5px;border:1px solid #2A3555;background:#1A2340;color:#7E8DB0;cursor:pointer;font-family:'Inter',sans-serif;">
        <option value="1">1</option>
        <option value="5">5</option>
        <option value="10">10</option>
        <option value="20" selected>20</option>
        <option value="30">30</option>
        <option value="40">40</option>
        <option value="50">50</option>
      </select>
    </div>
    <table id="stock-table">
      <thead>
        <tr>
          <th data-col="symbol">Ticker</th>
          <th data-col="name">Empresa</th>
          <th data-col="sector">Setor</th>
          <th data-col="price">Preço</th>
          <th data-col="fairPrice">Preço Justo (DCF) ↔ Termômetro</th>
          <th data-col="change1d">1D %</th>
          <th data-col="marketCap">M. Cap</th>
          <th data-col="pe">P/L</th>
          <th data-col="pb">P/VP</th>
          <th data-col="ps" title="Price-to-Sales: preço ÷ receita por ação. Quanto o mercado paga por cada $1 de receita.">P/S ⓘ</th>
          <th data-col="evEbitda">EV/EBITDA</th>
          <th data-col="roe">ROE</th>
          <th data-col="netMargin">Margem Liq.</th>
          <th data-col="divYield">Yield</th>
        </tr>
      </thead>
      <tbody id="tbody"></tbody>
    </table>
  </div>

  <!-- ██████████  PAGINAÇÃO  ██████████ -->
  <div class="pagination" id="pagination">
    <div class="pagination-info" id="pagination-info">—</div>
    <div class="page-btns" id="page-btns"></div>
    <select id="per-page-bottom" onchange="syncPerPage('bottom')" style="height:28px;font-size:11px;padding:0 6px;border-radius:5px;border:1px solid #2A3555;background:#1A2340;color:#7E8DB0;cursor:pointer;font-family:'Inter',sans-serif;">
      <option value="1">1 empresa</option>
      <option value="5">5 empresas</option>
      <option value="10">10 empresas</option>
      <option value="20" selected>20 empresas</option>
      <option value="30">30 empresas</option>
      <option value="40">40 empresas</option>
      <option value="50">50 empresas</option>
    </select>
  </div>

  <!-- ██████████  AD BANNER RODAPÉ  ██████████ -->
  <div class="ad-banner ad-bottom" id="ad-bottom" aria-label="Espaço publicitário">
    <!--
      Cole aqui o segundo bloco de anúncio (Carbon Ads ou AdSense)
    -->
    <div class="ad-placeholder">Espaço publicitário — 728×90 (Leaderboard)</div>
  </div>

  <!-- ██████████  FOOTER  ██████████ -->
  <footer>
    <p><strong>US Stock Screener</strong> — dados via Yahoo Finance (atraso ~15 min). Atualizado a cada visita.</p>
    <p style="margin-top:4px">O preço justo é calculado por DCF simplificado (taxa de desconto 10%, múltiplo terminal 15×). <strong>Não constitui recomendação de investimento.</strong></p>
    <p style="margin-top:8px">
      <a href="#">Sobre</a> &nbsp;·&nbsp;
      <a href="#">Metodologia DCF</a> &nbsp;·&nbsp;
      <a href="#">Aviso Legal</a>
    </p>
  </footer>

  <!-- ██████████  MODAL  ██████████ -->
  <div id="modal-container"></div>

  <!-- ██████████  JAVASCRIPT  ██████████ -->
  <script>
  // ─── TICKERS (100 maiores S&P500) ───────────────────────────────────────────
  const TICKERS = [
    // Mega caps
    'AAPL','MSFT','NVDA','GOOGL','AMZN','META','TSLA','BRK-B','AVGO','JPM',
    'LLY','V','UNH','XOM','MA','JNJ','PG','COST','HD','ABBV',
    'MRK','BAC','NFLX','CRM','CVX','ORCL','AMD','ADBE','KO','WMT',
    'PEP','CSCO','TMO','ACN','MCD','ABT','LIN','TXN','DHR','NKE',
    'WFC','PM','NEE','INTC','AMGN','IBM','QCOM','INTU','RTX','CAT',
    // Large caps
    'HON','SPGI','GS','BKNG','AXP','LOW','UPS','ELV','PLD','MS',
    'VRTX','GILD','MDT','T','DE','AMAT','SCHW','ADI','REGN','CI',
    'ISRG','MU','LRCX','SYK','BX','CB','ETN','KLAC','ZTS','C',
    'PGR','MO','MMC','BSX','HCA','TJX','SO','DUK','BDX','NOW',
    'AON','SLB','GE','CME','MDLZ','PANW','SNPS','CDNS','EOG','F',
    // Mid-large caps
    'GM','MAR','PCAR','ODFL','CTAS','AFL','STZ','AZO','TDG','IDXX',
    'ROST','EW','CTVA','TEL','VRSK','MNST','CARR','OTIS','PWR','BIIB',
    'MSI','DXCM','GEHC','LHX','KEYS','EXC','PAYX','GIS','SRE','D',
    'IQV','ON','EA','HAL','FAST','ACGL','HES','KR','CPRT','EBAY',
    'TROW','DLTR','IR','VMC','MLM','GWW','CHD','ZBRA','IRM','TER',
    // Finance & Insurance
    'VLO','MPC','PSX','XEL','WAT','TFC','MTD','FTV','BR','ROK',
    'ICE','COF','USB','PNC','TRV','ALL','MET','PRU','AFL','GL',
    'AIZ','LNC','RGA','UNM','FNF','FAF','CINF','PFG','ERIE','HIG',
    // Healthcare
    'BMY','AMGN','BIIB','ILMN','IDXX','ALGN','HOLX','TECH','RMD','COO',
    'BAX','BIO','HSIC','DVA','UHS','HUM','MOH','CNC','CVS','WBA',
    'MCK','CAH','ABC','PDCO','PRGO','ENDP','MNK','BHC','JAZZ','HZNP',
    // Tech & Semis
    'ENPH','SEDG','MPWR','GNRC','TDY','PODD','QRVO','SWKS','MCHP','XLNX',
    'FTNT','CTSH','INFY','WIT','EPAM','GLOB','PEGA','MANH','VEEV','ANSS',
    'CDNS','SNPS','PTC','DASN','ALTR','TTWO','EA','ATVI','NTDOY','GLUU',
    // Energy
    'COP','OXY','DVN','FANG','APA','MRO','HES','PXD','EOG','SLB',
    'HAL','BKR','NOV','HP','RIG','VAL','DO','NE','PTEN','PUMP',
    // Consumer & Retail
    'SBUX','CMG','YUM','QSR','DPZ','JACK','DRI','EAT','TXRH','WING',
    'TGT','DG','DLTR','FIVE','OLLI','KR','ACI','SFM','WMT','COST',
    // Industrials & Materials
    'BA','LMT','NOC','GD','RTX','TXT','HII','KTOS','AJRD','LDOS',
    'EMR','ROK','PH','ITW','AME','XYL','DOV','EXPD','CHRW','JBHT',
    'NUE','STLD','RS','CMC','WOR','ATI','ALB','EMN','CE','LYB',
    // Real Estate
    'AMT','PLD','CCI','EQIX','WELL','PSA','DLR','O','SPG','VTR',
    'EXR','AVB','EQR','MAA','UDR','CPT','ESS','BXP','KIM','REG',
  ];

  let allData = [];
  let sortCol = 'marketCap';
  let sortDir = -1;

  // ─── HELPERS ────────────────────────────────────────────────────────────────
  const fmt  = (n,d=2) => (n==null||isNaN(n)) ? '—' : Number(n).toFixed(d);
  const fmtP = (n)     => (n==null||isNaN(n)) ? '—' : (n*100).toFixed(1)+'%';
  function fmtB(n) {
    if (!n||isNaN(n)) return '—';
    if (n>=1e12) return '$'+(n/1e12).toFixed(2)+'T';
    if (n>=1e9)  return '$'+(n/1e9).toFixed(1)+'B';
    if (n>=1e6)  return '$'+(n/1e6).toFixed(1)+'M';
    return '$'+n.toFixed(0);
  }

  // ─── DCF SIMPLIFICADO ───────────────────────────────────────────────────────
  function calcFair(s) {
    const base = (s.fcfPerShare > 0) ? s.fcfPerShare : (s.eps > 0 ? s.eps : null);
    if (!base || !s.price) return null;
    const g  = Math.min(s.growthRate || 0.08, 0.30);
    const dr = 0.10, tm = 15, yr = 10;
    let pv = 0, cf = base;
    for (let i = 1; i <= yr; i++) {
      cf *= (1 + g * (1 - (i/yr)*0.45));
      pv += cf / Math.pow(1+dr, i);
    }
    pv += (cf * tm) / Math.pow(1+dr, yr);
    return pv > 0 ? pv : null;
  }

  function getVerdict(price, fair) {
    if (!fair || !price) return { code:'none', pct:null };
    const pct = (fair - price) / price * 100;
    return pct > 15 ? { code:'sub', pct } : pct < -15 ? { code:'over', pct } : { code:'fair', pct };
  }

  // ─── TERMÔMETRO NA LINHA ────────────────────────────────────────────────────
  function thermCell(price, fair) {
    if (!price) return '<span style="color:var(--txt3)">—</span>';
    const fp = '$' + price.toFixed(2);
    if (!fair) return `<div class="therm-cell"><span style="font-weight:500;font-family:var(--mono)">${fp}</span><span style="font-size:10px;color:var(--txt3)">DCF indisponível</span></div>`;
    const pct = (fair - price) / price * 100;
    const color = pct > 15 ? 'var(--green)' : pct < -15 ? 'var(--red)' : 'var(--yellow)';
    const sign  = pct >= 0 ? '+' : '';
    const left  = Math.min(Math.max(50 - pct * 0.8, 4), 96);
    return `<div class="therm-cell">
      <div class="therm-prices">
        <span style="font-weight:500;font-family:var(--mono);font-size:12px">${fp}</span>
        <span style="color:${color};font-size:11px;font-family:var(--mono)">→ $${fair.toFixed(0)}</span>
      </div>
      <div class="therm-track">
        <div class="therm-gradient"></div>
        <div class="therm-needle" style="left:${left}%;background:${color}"></div>
      </div>
      <span class="therm-pct" style="color:${color}">${sign}${pct.toFixed(1)}% margem</span>
    </div>`;
  }

  // ─── BARRA MARGEM LÍQ ───────────────────────────────────────────────────────
  function mbarCell(val) {
    if (val==null||isNaN(val)) return '—';
    const pct = val * 100;
    const bar = Math.min(Math.abs(pct), 50) * 2;
    const color = pct > 15 ? 'var(--green)' : pct > 0 ? 'var(--yellow)' : 'var(--red)';
    const cls   = pct > 5 ? 'up' : pct > 0 ? 'neu' : 'dn';
    return `<div class="mbar"><div class="mbar-track"><div class="mbar-fill" style="width:${bar}%;background:${color}"></div></div><span class="mbar-val ${cls}">${pct.toFixed(1)}%</span></div>`;
  }

  // ─── RENDER TABELA COM PAGINAÇÃO ────────────────────────────────────────────
  let currentPage = 1;
  let perPage = 20;

  function getPerPage() { return parseInt(document.getElementById('per-page').value) || 20; }

  function changePerPage() {
    perPage = getPerPage();
    currentPage = 1;
    // sync all selects
    ['per-page','per-page-top','per-page-bottom'].forEach(id => {
      const el = document.getElementById(id);
      if (el) el.value = perPage;
    });
    if (allData.length > 0) { renderTable(); return; }
    loadData();
  }

  function renderTable() {
    const q   = document.getElementById('search').value.toLowerCase();
    const sec = document.getElementById('filter-sector').value;
    const vf  = document.getElementById('filter-verdict').value;
    const pef = document.getElementById('filter-pe').value;
    perPage   = getPerPage();

    let filtered = allData.filter(s => {
      if (q && !s.symbol.toLowerCase().includes(q) && !(s.name||'').toLowerCase().includes(q)) return false;
      if (sec && s.sector !== sec) return false;
      if (vf && getVerdict(s.price, s.fairPrice).code !== vf) return false;
      if (pef === 'low'  && !(s.pe > 0 && s.pe < 15))    return false;
      if (pef === 'mid'  && !(s.pe >= 15 && s.pe <= 40)) return false;
      if (pef === 'high' && !(s.pe > 40))                 return false;
      return true;
    });

    filtered.sort((a,b) => {
      let av=a[sortCol], bv=b[sortCol];
      if (av==null) return 1; if (bv==null) return -1;
      if (typeof av==='string') return sortDir*av.localeCompare(bv);
      return sortDir*(av-bv);
    });

    const totalPages = Math.max(1, Math.ceil(filtered.length / perPage));
    if (currentPage > totalPages) currentPage = 1;
    const start = (currentPage - 1) * perPage;
    const pageData = filtered.slice(start, start + perPage);

    document.getElementById('tbody').innerHTML = pageData.map(s => {
      const cc  = (s.change1d||0)>=0 ? 'up':'dn';
      const cs  = (s.change1d||0)>=0 ? '+':'';
      const pec = s.pe>0&&s.pe<15 ? 'up' : s.pe>40 ? 'dn' : 'neu';
      const rec = s.roe>0.15 ? 'up' : s.roe<0 ? 'dn' : 'neu';
      return `<tr onclick="openModal('${s.symbol}')">
        <td class="sym">${s.symbol}</td>
        <td><div class="name-cell">${s.name||'—'}</div></td>
        <td><span class="sec-badge">${s.sector||'—'}</span></td>
        <td style="font-family:'DM Mono',monospace;font-weight:500">$${(s.price||0).toFixed(2)}</td>
        <td>${thermCell(s.price, s.fairPrice)}</td>
        <td class="${cc}">${cs}${fmt(s.change1d)}%</td>
        <td style="font-family:'DM Mono',monospace">${fmtB(s.marketCap)}</td>
        <td class="${pec}" style="font-family:'DM Mono',monospace">${s.pe?fmt(s.pe,1):'—'}</td>
        <td style="font-family:'DM Mono',monospace">${s.pb?fmt(s.pb,1):'—'}</td>
        <td style="font-family:'DM Mono',monospace">${s.ps?fmt(s.ps,1):'—'}</td>
        <td style="font-family:'DM Mono',monospace">${s.evEbitda?fmt(s.evEbitda,1):'—'}</td>
        <td class="${rec}" style="font-family:'DM Mono',monospace">${s.roe?fmtP(s.roe):'—'}</td>
        <td>${mbarCell(s.netMargin)}</td>
        <td class="${(s.divYield||0)>0.03?'up':'neu'}" style="font-family:'DM Mono',monospace">${s.divYield?fmtP(s.divYield):'—'}</td>
      </tr>`;
    }).join('');

    // Stats
    document.getElementById('count-badge').textContent = TICKERS.length + ' empresas';
    document.getElementById('s-under').textContent = allData.filter(s=>getVerdict(s.price,s.fairPrice).code==='sub').length;
    document.getElementById('s-fair').textContent  = allData.filter(s=>getVerdict(s.price,s.fairPrice).code==='fair').length;
    document.getElementById('s-over').textContent  = allData.filter(s=>getVerdict(s.price,s.fairPrice).code==='over').length;

    // Info paginação
    const from = filtered.length ? start+1 : 0;
    const to   = Math.min(start+perPage, filtered.length);
    const infoHtml = `Mostrando <b>${from}–${to}</b> de <b>${filtered.length}</b> carregadas`;
    document.getElementById('pagination-info').innerHTML = infoHtml;
    const elTop = document.getElementById('pagination-info-top');
    if (elTop) elTop.innerHTML = infoHtml;

    // Sync selects
    ['per-page','per-page-top','per-page-bottom'].forEach(id => {
      const el = document.getElementById(id);
      if (el) el.value = perPage;
    });

    // Gera botões para topo e rodapé
    function buildPageBtns(containerId, scrollTop) {
      const btns = document.getElementById(containerId);
      if (!btns) return;
      btns.innerHTML = '';
      const addBtn = (label, page, disabled, active) => {
        const b = document.createElement('button');
        b.className = 'page-btn' + (active?' active':'');
        b.textContent = label;
        b.disabled = disabled;
        b.onclick = () => {
          currentPage = page;
          renderTable();
          if (scrollTop) window.scrollTo({top:0,behavior:'smooth'});
        };
        btns.appendChild(b);
      };
      addBtn('←', currentPage-1, currentPage===1, false);
      const range = [];
      for (let i=1; i<=totalPages; i++) {
        if (i===1||i===totalPages||Math.abs(i-currentPage)<=2) range.push(i);
        else if (range[range.length-1]!=='…') range.push('…');
      }
      range.forEach(p => {
        if (p==='…') {
          const sp = document.createElement('span');
          sp.textContent='…'; sp.style.cssText='color:#4A5578;padding:0 4px;font-size:11px;line-height:28px';
          btns.appendChild(sp);
        } else addBtn(p, p, false, p===currentPage);
      });
      addBtn('→', currentPage+1, currentPage===totalPages, false);
    }
    buildPageBtns('page-btns-top', true);
    buildPageBtns('page-btns', false);
  }

  function syncPerPage(source) {
    const val = document.getElementById('per-page-'+(source==='top'?'top':source==='bottom'?'bottom':'top')).value
              || document.getElementById('per-page').value;
    // sync all selects
    ['per-page','per-page-top','per-page-bottom'].forEach(id => {
      const el = document.getElementById(id);
      if (el) el.value = val;
    });
    perPage = parseInt(val);
    currentPage = 1;
    if (allData.length > 0) { renderTable(); return; }
    loadData();
  }

  // ─── MODAL ──────────────────────────────────────────────────────────────────
  function openModal(sym) {
    const s = allData.find(x=>x.symbol===sym);
    if (!s) return;
    const fair = s.fairPrice;
    const v    = getVerdict(s.price, fair);
    const pct  = v.pct;
    const left = pct!=null ? Math.min(Math.max(50 - pct*0.8, 4), 96) : 50;
    const color= pct!=null ? (pct>15?'var(--green)':pct<-15?'var(--red)':'var(--yellow)') : 'var(--txt3)';
    const pill = !pct ? '' : pct>15
      ? `<span class="verdict-pill vp-buy">✓ Subvalorizada — margem de +${pct.toFixed(0)}%</span>`
      : pct<-15
      ? `<span class="verdict-pill vp-sell">✗ Sobrevalorizada — ${Math.abs(pct).toFixed(0)}% acima do justo</span>`
      : `<span class="verdict-pill vp-fair">≈ Preço Justo (${(pct>=0?'+':'')+pct.toFixed(0)}%)</span>`;

    document.getElementById('modal-container').innerHTML = `
    <div class="modal-bg" onclick="if(event.target===this)closeModal()">
      <div class="modal" role="dialog" aria-modal="true" aria-label="${s.symbol} — detalhes">
        <div class="modal-header">
          <div>
            <div style="font-size:20px;font-weight:600;font-family:var(--mono)">${s.symbol}</div>
            <div style="font-size:12px;color:var(--txt2)">${s.name||''} · ${s.sector||'—'}</div>
          </div>
          <button class="btn-close" onclick="closeModal()" aria-label="Fechar">×</button>
        </div>
        <div class="modal-body">
          <div class="mgrid">
            <div class="mc"><div class="lbl">Preço atual</div><div class="val">$${(s.price||0).toFixed(2)}</div></div>
            <div class="mc"><div class="lbl">Variação 1D</div><div class="val ${(s.change1d||0)>=0?'up':'dn'}">${((s.change1d||0)>=0?'+':'')+fmt(s.change1d)}%</div></div>
            <div class="mc"><div class="lbl">Market Cap</div><div class="val sm">${fmtB(s.marketCap)}</div></div>
            <div class="mc"><div class="lbl">Dividend Yield</div><div class="val sm">${s.divYield?fmtP(s.divYield):'—'}</div></div>
          </div>

          <div class="sec-title">Valuation</div>
          <div class="irow"><span class="il">P/L (P/E Ratio)</span><span class="${s.pe>0&&s.pe<15?'up':s.pe>40?'dn':'neu'}" style="font-family:var(--mono)">${s.pe?fmt(s.pe,1):'—'}</span></div>
          <div class="irow"><span class="il">P/VP (P/Book)</span><span style="font-family:var(--mono)">${s.pb?fmt(s.pb,1):'—'}</span></div>
          <div class="irow"><span class="il">P/S (P/Sales)</span><span style="font-family:var(--mono)">${s.ps?fmt(s.ps,1):'—'}</span></div>
          <div class="irow"><span class="il">EV/EBITDA</span><span style="font-family:var(--mono)">${s.evEbitda?fmt(s.evEbitda,1):'—'}</span></div>
          <div class="irow"><span class="il">PEG Ratio</span><span style="font-family:var(--mono)">${s.peg?fmt(s.peg,2):'—'}</span></div>

          <div class="sec-title">Rentabilidade</div>
          <div class="irow"><span class="il">ROE</span><span class="${s.roe>0.15?'up':s.roe<0?'dn':'neu'}" style="font-family:var(--mono)">${fmtP(s.roe)}</span></div>
          <div class="irow"><span class="il">ROA</span><span style="font-family:var(--mono)">${fmtP(s.roa)}</span></div>
          <div class="irow"><span class="il">Margem Bruta</span><span style="font-family:var(--mono)">${fmtP(s.grossMargin)}</span></div>
          <div class="irow"><span class="il">Margem Líquida</span><span class="${(s.netMargin||0)>0.1?'up':(s.netMargin||0)<0?'dn':'neu'}" style="font-family:var(--mono)">${fmtP(s.netMargin)}</span></div>
          <div class="irow"><span class="il">Margem Operacional</span><span style="font-family:var(--mono)">${fmtP(s.opMargin)}</span></div>

          <div class="sec-title">Saúde Financeira</div>
          <div class="irow"><span class="il">EPS (lucro/ação)</span><span style="font-family:var(--mono)">${s.eps?'$'+fmt(s.eps,2):'—'}</span></div>
          <div class="irow"><span class="il">FCF por ação</span><span style="font-family:var(--mono)">${s.fcfPerShare?'$'+fmt(s.fcfPerShare,2):'—'}</span></div>
          <div class="irow"><span class="il">Dívida / Patrimônio</span><span style="font-family:var(--mono)">${s.debtEq?fmt(s.debtEq,2):'—'}</span></div>
          <div class="irow"><span class="il">Current Ratio</span><span style="font-family:var(--mono)">${s.currentRatio?fmt(s.currentRatio,2):'—'}</span></div>
          <div class="irow"><span class="il">Volume médio</span><span style="font-family:var(--mono)">${fmtB(s.avgVol)}</span></div>

          <div class="dcf-box">
            <div style="font-size:11px;color:var(--txt3);margin-bottom:8px">⚙ Preço Justo — Fluxo de Caixa Descontado (DCF)</div>
            <div style="display:flex;gap:20px;align-items:baseline;flex-wrap:wrap">
              <span style="font-size:12px;color:var(--txt2)">Atual: <strong style="color:var(--txt);font-family:var(--mono)">$${(s.price||0).toFixed(2)}</strong></span>
              ${fair
                ? `<span style="font-size:12px;color:var(--txt2)">Justo: <strong style="color:${color};font-size:17px;font-family:var(--mono)">$${fair.toFixed(2)}</strong></span>`
                : `<span style="font-size:12px;color:var(--txt3)">Dados insuficientes para calcular</span>`}
            </div>
            ${fair ? `
            <div class="dcf-therm-track" aria-label="Termômetro de margem de segurança">
              <div class="dcf-therm-bg"></div>
              <div class="dcf-needle" style="left:${left}%;background:${color}"></div>
            </div>
            <div class="dcf-labels"><span>Muito barata</span><span>Preço justo</span><span>Muito cara</span></div>
            ${pill}
            <div style="font-size:10px;color:var(--txt3);margin-top:8px;line-height:1.6">
              Parâmetros: taxa de desconto 10% · crescimento estimado ${((s.growthRate||0.08)*100).toFixed(0)}%/ano (10 anos) · múltiplo terminal 15×.<br>
              <strong>Não constitui recomendação de investimento.</strong>
            </div>` : ''}
          </div>
        </div>
      </div>
    </div>`;
  }

  function closeModal() { document.getElementById('modal-container').innerHTML=''; }
  document.addEventListener('keydown', e => { if(e.key==='Escape') closeModal(); });

  // ─── SORT ───────────────────────────────────────────────────────────────────
  document.querySelectorAll('thead th[data-col]').forEach(th => {
    th.addEventListener('click', () => {
      const col = th.dataset.col;
      sortDir = sortCol===col ? sortDir*-1 : -1;
      sortCol = col;
      document.querySelectorAll('thead th').forEach(t=>t.classList.remove('sorted-asc','sorted-desc'));
      th.classList.add(sortDir===1?'sorted-asc':'sorted-desc');
      renderTable();
    });
  });

  // ─── EXPORTAR CSV ───────────────────────────────────────────────────────────
  function exportCSV() {
    const headers = ['Ticker','Empresa','Setor','Preço','Preço Justo DCF','Margem %','P/L','P/VP','P/S','EV/EBITDA','ROE','Margem Liq.','Yield'];
    const rows = allData.map(s => {
      const v = getVerdict(s.price, s.fairPrice);
      return [s.symbol, s.name, s.sector, s.price, s.fairPrice?s.fairPrice.toFixed(2):'', v.pct?v.pct.toFixed(1):'', s.pe, s.pb, s.ps, s.evEbitda, s.roe?(s.roe*100).toFixed(1):'', s.netMargin?(s.netMargin*100).toFixed(1):'', s.divYield?(s.divYield*100).toFixed(2):''].join(',');
    });
    const csv = [headers.join(','), ...rows].join('\n');
    const a = document.createElement('a');
    a.href = URL.createObjectURL(new Blob([csv], {type:'text/csv'}));
    a.download = 'us-stocks-screener.csv';
    a.click();
  }

  // ─── CARREGAR DADOS REAIS (YAHOO FINANCE) ───────────────────────────────────
  async function loadData() {
    perPage = getPerPage();
    // Busca TODOS os tickers (até 300) para que filtros de setor funcionem corretamente.
    // A paginação controla quantos são EXIBIDOS, não quantos são buscados.
    const tickersToFetch = TICKERS;
    const total = tickersToFetch.length;

    allData = [];
    currentPage = 1;
    document.getElementById('tbody').innerHTML = '';
    document.getElementById('loading-msg').style.display = 'none';
    const prog = document.getElementById('load-progress');
    const progText = document.getElementById('load-progress-text');
    const progFill = document.getElementById('load-progress-fill');
    prog.style.display = 'block';

    for (let i = 0; i < tickersToFetch.length; i++) {
      const sym = tickersToFetch[i];
      progText.textContent = `Buscando ${i+1} de ${total}: ${sym} — dados aparecerão conforme carregam`;
      progFill.style.width = ((i+1)/total*100) + '%';
      try {
        // Try multiple proxies/endpoints for CORS bypass
        const FIELDS = 'shortName,regularMarketPrice,regularMarketChangePercent,marketCap,trailingPE,priceToBook,priceToSalesTrailing12Months,enterpriseToEbitda,returnOnEquity,returnOnAssets,grossMargins,netMargins,operatingMargins,debtToEquity,currentRatio,trailingEps,freeCashflow,sharesOutstanding,dividendYield,averageVolume,pegRatio,revenueGrowth,sector';
        const YAHOO_URL = `https://query1.finance.yahoo.com/v7/finance/quote?symbols=${sym}&fields=${FIELDS}&crumb=`;
        const PROXY1 = `https://corsproxy.io/?${encodeURIComponent(YAHOO_URL)}`;
        const PROXY2 = `https://api.allorigins.win/raw?url=${encodeURIComponent(YAHOO_URL)}`;
        let r, lastErr;
        for (const url of [PROXY1, PROXY2]) {
          try { r = await fetch(url, {headers:{'User-Agent':'Mozilla/5.0'}}); if(r.ok) break; } catch(e){ lastErr=e; r=null; }
        }
        if (!r || !r.ok) throw lastErr || new Error('All proxies failed');
        const j = await r.json();
        const q = j?.quoteResponse?.result?.[0];
        if (q) {
          const fcfPerShare = q.freeCashflow && q.sharesOutstanding ? q.freeCashflow/q.sharesOutstanding : null;
          const s = {
            symbol:sym, name:q.shortName||sym, sector:q.sector||'Unknown',
            price:q.regularMarketPrice, change1d:q.regularMarketChangePercent,
            marketCap:q.marketCap, pe:q.trailingPE, pb:q.priceToBook,
            ps:q.priceToSalesTrailing12Months, evEbitda:q.enterpriseToEbitda,
            roe:q.returnOnEquity, roa:q.returnOnAssets,
            grossMargin:q.grossMargins, netMargin:q.netMargins, opMargin:q.operatingMargins,
            debtEq:q.debtToEquity, currentRatio:q.currentRatio,
            eps:q.trailingEps, fcfPerShare, divYield:q.dividendYield,
            avgVol:q.averageVolume, peg:q.pegRatio,
            growthRate:q.revenueGrowth||0.08
          };
          s.fairPrice = calcFair(s);
          allData.push(s);
          // Render progressively every 5 tickers
          if (allData.length % 5 === 0) renderTable();
        }
      } catch(e){}
      await new Promise(r=>setTimeout(r,110));
    }

    prog.style.display = 'none';
    const secs = [...new Set(allData.map(s=>s.sector).filter(Boolean))].sort();
    const sel = document.getElementById('filter-sector');
    sel.innerHTML = '<option value="">Todos os setores</option>'+secs.map(s=>`<option value="${s}">${s}</option>`).join('');
    document.getElementById('s-updated').textContent = new Date().toLocaleTimeString('pt-BR');
    renderTable();
  }

  // ─── DADOS DEMO (carrega imediatamente) ─────────────────────────────────────
  const DEMO = [
    {symbol:'AAPL',name:'Apple Inc.',sector:'Technology',price:213.49,change1d:0.85,marketCap:3.27e12,pe:34.2,pb:48.1,ps:8.1,evEbitda:24.3,roe:1.72,roa:0.28,grossMargin:0.461,netMargin:0.257,opMargin:0.311,debtEq:1.51,currentRatio:0.98,eps:6.23,fcfPerShare:6.97,divYield:0.0051,avgVol:57e6,peg:2.8,growthRate:0.09},
    {symbol:'MSFT',name:'Microsoft Corp.',sector:'Technology',price:447.83,change1d:1.21,marketCap:3.33e12,pe:37.8,pb:13.4,ps:14.2,evEbitda:28.1,roe:0.35,roa:0.17,grossMargin:0.697,netMargin:0.355,opMargin:0.451,debtEq:0.29,currentRatio:1.27,eps:11.85,fcfPerShare:13.20,divYield:0.0065,avgVol:19e6,peg:2.4,growthRate:0.15},
    {symbol:'NVDA',name:'NVIDIA Corporation',sector:'Technology',price:131.38,change1d:2.43,marketCap:3.21e12,pe:52.3,pb:42.8,ps:22.1,evEbitda:39.4,roe:0.85,roa:0.48,grossMargin:0.748,netMargin:0.553,opMargin:0.619,debtEq:0.42,currentRatio:4.17,eps:2.51,fcfPerShare:2.38,divYield:0.0003,avgVol:190e6,peg:1.1,growthRate:0.80},
    {symbol:'GOOGL',name:'Alphabet Inc.',sector:'Technology',price:178.74,change1d:-0.32,marketCap:2.19e12,pe:22.4,pb:6.8,ps:5.9,evEbitda:16.2,roe:0.30,roa:0.19,grossMargin:0.566,netMargin:0.261,opMargin:0.318,debtEq:0.07,currentRatio:1.84,eps:7.97,fcfPerShare:6.42,divYield:0,avgVol:22e6,peg:1.4,growthRate:0.14},
    {symbol:'AMZN',name:'Amazon.com Inc.',sector:'Consumer Cyclical',price:205.61,change1d:0.67,marketCap:2.19e12,pe:45.1,pb:10.3,ps:3.2,evEbitda:24.7,roe:0.23,roa:0.09,grossMargin:0.476,netMargin:0.072,opMargin:0.108,debtEq:0.59,currentRatio:1.05,eps:4.56,fcfPerShare:5.11,divYield:0,avgVol:32e6,peg:1.9,growthRate:0.12},
    {symbol:'META',name:'Meta Platforms',sector:'Technology',price:577.90,change1d:1.44,marketCap:1.47e12,pe:27.3,pb:8.9,ps:9.2,evEbitda:19.8,roe:0.33,roa:0.22,grossMargin:0.815,netMargin:0.337,opMargin:0.418,debtEq:0.28,currentRatio:2.73,eps:21.16,fcfPerShare:19.30,divYield:0.0032,avgVol:13e6,peg:1.2,growthRate:0.22},
    {symbol:'TSLA',name:'Tesla Inc.',sector:'Consumer Cyclical',price:248.50,change1d:-1.20,marketCap:7.95e11,pe:68.1,pb:12.4,ps:7.8,evEbitda:46.3,roe:0.18,roa:0.07,grossMargin:0.176,netMargin:0.051,opMargin:0.075,debtEq:0.18,currentRatio:1.84,eps:3.65,fcfPerShare:1.50,divYield:0,avgVol:98e6,peg:4.2,growthRate:0.19},
    {symbol:'JPM',name:'JPMorgan Chase',sector:'Financial Services',price:258.41,change1d:0.23,marketCap:7.40e11,pe:13.2,pb:2.18,ps:3.8,evEbitda:null,roe:0.161,roa:0.013,grossMargin:null,netMargin:0.291,opMargin:null,debtEq:null,currentRatio:null,eps:19.60,fcfPerShare:null,divYield:0.023,avgVol:8.5e6,peg:1.4,growthRate:0.07},
    {symbol:'LLY',name:'Eli Lilly & Co.',sector:'Healthcare',price:896.30,change1d:-0.78,marketCap:8.53e11,pe:112.4,pb:51.2,ps:18.4,evEbitda:54.8,roe:0.521,roa:0.124,grossMargin:0.832,netMargin:0.167,opMargin:0.269,debtEq:2.71,currentRatio:1.04,eps:7.98,fcfPerShare:6.21,divYield:0.0062,avgVol:3e6,peg:1.8,growthRate:0.28},
    {symbol:'V',name:'Visa Inc.',sector:'Financial Services',price:297.48,change1d:0.44,marketCap:6.17e11,pe:31.4,pb:14.9,ps:16.2,evEbitda:23.7,roe:0.441,roa:0.167,grossMargin:0.812,netMargin:0.515,opMargin:0.668,debtEq:1.72,currentRatio:1.38,eps:9.47,fcfPerShare:9.00,divYield:0.0082,avgVol:5.4e6,peg:2.1,growthRate:0.11},
    {symbol:'XOM',name:'Exxon Mobil',sector:'Energy',price:111.23,change1d:-0.54,marketCap:4.42e11,pe:14.8,pb:2.1,ps:1.3,evEbitda:9.8,roe:0.143,roa:0.073,grossMargin:0.432,netMargin:0.091,opMargin:0.118,debtEq:0.21,currentRatio:1.44,eps:7.52,fcfPerShare:6.11,divYield:0.035,avgVol:14e6,peg:1.6,growthRate:0.05},
    {symbol:'WMT',name:'Walmart Inc.',sector:'Consumer Defensive',price:97.84,change1d:0.31,marketCap:7.87e11,pe:41.2,pb:8.4,ps:1.0,evEbitda:19.3,roe:0.204,roa:0.068,grossMargin:0.243,netMargin:0.024,opMargin:0.044,debtEq:0.72,currentRatio:0.84,eps:2.37,fcfPerShare:2.10,divYield:0.012,avgVol:13e6,peg:3.1,growthRate:0.06},
    {symbol:'JNJ',name:'Johnson & Johnson',sector:'Healthcare',price:157.82,change1d:-0.19,marketCap:3.80e11,pe:22.7,pb:4.8,ps:4.5,evEbitda:14.9,roe:0.213,roa:0.102,grossMargin:0.682,netMargin:0.198,opMargin:0.249,debtEq:0.56,currentRatio:1.12,eps:6.96,fcfPerShare:7.44,divYield:0.034,avgVol:7.2e6,peg:2.3,growthRate:0.06},
    {symbol:'NFLX',name:'Netflix Inc.',sector:'Technology',price:1090.00,change1d:1.82,marketCap:4.65e11,pe:52.1,pb:18.3,ps:9.8,evEbitda:38.2,roe:0.352,roa:0.105,grossMargin:0.461,netMargin:0.187,opMargin:0.268,debtEq:0.73,currentRatio:1.22,eps:20.93,fcfPerShare:18.50,divYield:0,avgVol:2.4e6,peg:1.9,growthRate:0.15},
    {symbol:'BAC',name:'Bank of America',sector:'Financial Services',price:44.21,change1d:-0.18,marketCap:3.44e11,pe:14.1,pb:1.4,ps:3.1,evEbitda:null,roe:0.094,roa:0.009,grossMargin:null,netMargin:0.219,opMargin:null,debtEq:null,currentRatio:null,eps:3.14,fcfPerShare:null,divYield:0.024,avgVol:34e6,peg:1.6,growthRate:0.08},
    {symbol:'KO',name:'Coca-Cola Co.',sector:'Consumer Defensive',price:71.20,change1d:0.12,marketCap:3.07e11,pe:27.8,pb:10.2,ps:5.8,evEbitda:21.3,roe:0.384,roa:0.091,grossMargin:0.608,netMargin:0.209,opMargin:0.280,debtEq:1.83,currentRatio:1.05,eps:2.56,fcfPerShare:2.30,divYield:0.030,avgVol:12e6,peg:3.2,growthRate:0.05},
    {symbol:'PEP',name:'PepsiCo Inc.',sector:'Consumer Defensive',price:131.50,change1d:-0.22,marketCap:1.81e11,pe:21.4,pb:8.7,ps:2.3,evEbitda:16.4,roe:0.502,roa:0.104,grossMargin:0.538,netMargin:0.108,opMargin:0.155,debtEq:2.43,currentRatio:0.79,eps:6.14,fcfPerShare:5.80,divYield:0.037,avgVol:5.9e6,peg:2.8,growthRate:0.04},
    {symbol:'MCD',name:"McDonald's Corp.",sector:'Consumer Cyclical',price:294.10,change1d:0.55,marketCap:2.11e11,pe:24.3,pb:null,ps:9.4,evEbitda:19.7,roe:null,roa:0.126,grossMargin:0.568,netMargin:0.386,opMargin:0.487,debtEq:null,currentRatio:0.48,eps:12.10,fcfPerShare:11.40,divYield:0.025,avgVol:2.8e6,peg:2.5,growthRate:0.06},
    {symbol:'GS',name:'Goldman Sachs',sector:'Financial Services',price:582.30,change1d:0.88,marketCap:1.89e11,pe:16.2,pb:1.72,ps:2.9,evEbitda:null,roe:0.106,roa:0.009,grossMargin:null,netMargin:0.179,opMargin:null,debtEq:null,currentRatio:null,eps:35.97,fcfPerShare:null,divYield:0.022,avgVol:1.6e6,peg:1.3,growthRate:0.09},
    {symbol:'COST',name:'Costco Wholesale',sector:'Consumer Defensive',price:918.40,change1d:0.67,marketCap:4.08e11,pe:56.8,pb:16.4,ps:1.6,evEbitda:34.2,roe:0.289,roa:0.085,grossMargin:0.126,netMargin:0.028,opMargin:0.036,debtEq:0.43,currentRatio:0.94,eps:16.18,fcfPerShare:15.10,divYield:0.005,avgVol:1.8e6,peg:3.8,growthRate:0.08},
  ].map(s=>({...s, fairPrice:calcFair(s)}));

  allData = DEMO;
  (() => {
    const secs = [...new Set(allData.map(s=>s.sector).filter(Boolean))].sort();
    const sel = document.getElementById('filter-sector');
    sel.innerHTML = '<option value="">Todos os setores</option>'+secs.map(s=>`<option value="${s}">${s}</option>`).join('');
    renderTable();
  })();
  </script>
</body>
</html>
