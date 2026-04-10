<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Informe Financiero — Secretaría Control Ecológico 2012</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: Georgia, serif; background: #071a07; color: #d4ead4; min-height: 100vh; }
 
    /* HEADER */
    .header { background: linear-gradient(135deg, #0d2110 0%, #1a3a1a 100%); border-bottom: 3px solid #c8a84b; padding: 24px 32px; }
    .header-top { display: flex; align-items: center; gap: 16px; margin-bottom: 8px; }
    .header-logo { width: 52px; height: 52px; background: #c8a84b; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 22px; flex-shrink: 0; }
    .header-sub { font-size: 10px; letter-spacing: 3px; color: #c8a84b; text-transform: uppercase; margin-bottom: 2px; }
    .header h1 { font-size: 20px; color: #fff; letter-spacing: 1px; }
    .header-divider { margin-top: 16px; border-top: 1px solid #2e4a2e; padding-top: 12px; }
    .header h2 { font-size: 15px; color: #a8d4a8; font-weight: normal; letter-spacing: 1px; }
    .header-meta { display: flex; gap: 24px; margin-top: 8px; font-size: 11px; color: #7aab7a; }
 
    /* KPIS */
    .kpis { display: grid; grid-template-columns: repeat(4, 1fr); background: #0d2110; border-bottom: 2px solid #1a3a1a; }
    .kpi { padding: 20px 24px; border-right: 1px solid #1a3a1a; }
    .kpi-icon { font-size: 18px; margin-bottom: 4px; }
    .kpi-value { font-size: 22px; font-weight: bold; color: #c8a84b; }
    .kpi-value.green { color: #5bc85b; }
    .kpi-value.red { color: #e74c3c; }
    .kpi-label { font-size: 11px; color: #7aab7a; margin-top: 4px; letter-spacing: 0.5px; }
 
    /* TABS */
    .tabs { display: flex; background: #0d2110; border-bottom: 2px solid #1a3a1a; padding: 0 16px; overflow-x: auto; }
    .tab-btn { padding: 12px 18px; border: none; background: none; cursor: pointer; font-size: 12px; letter-spacing: 0.5px; font-family: Georgia, serif; color: #7aab7a; border-bottom: 2px solid transparent; margin-bottom: -2px; transition: color 0.2s; white-space: nowrap; }
    .tab-btn.active { color: #c8a84b; border-bottom-color: #c8a84b; }
    .tab-btn:hover { color: #a8d4a8; }
 
    /* CONTENT */
    .content { padding: 28px 32px; max-width: 1100px; margin: 0 auto; }
    .tab-panel { display: none; }
    .tab-panel.active { display: block; }
 
    /* SECTION TITLE */
    .section-title { font-size: 11px; letter-spacing: 2px; color: #c8a84b; text-transform: uppercase; border-bottom: 1px solid #1a3a1a; padding-bottom: 8px; margin-bottom: 16px; margin-top: 0; }
 
    /* TEXT */
    .body-text { font-size: 13px; line-height: 1.8; color: #b0d4b0; margin-bottom: 24px; }
    .highlight { color: #c8a84b; font-weight: bold; }
    .highlight-green { color: #5bc85b; font-weight: bold; }
    .highlight-red { color: #e74c3c; font-weight: bold; }
 
    /* CHART GRID */
    .chart-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; margin-bottom: 32px; }
    .chart-box { background: #0d2110; border: 1px solid #1e3d1e; border-radius: 6px; padding: 20px; }
    .chart-title { color: #c8a84b; font-size: 12px; letter-spacing: 1px; margin-bottom: 16px; text-transform: uppercase; }
    .chart-container { position: relative; }
 
    /* CONCLUSION GRID */
    .conclusion-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    .conclusion-item { display: flex; gap: 10px; padding: 12px 16px; background: #0d2110; border-radius: 4px; font-size: 12px; color: #b0d4b0; line-height: 1.6; }
    .conclusion-item.ok { border: 1px solid #1a4a1a; }
    .conclusion-item.warn { border: 1px solid #4a1a1a; }
    .conclusion-item .icon { font-size: 16px; flex-shrink: 0; }
 
    /* TABLE */
    .table-wrap { overflow-x: auto; margin-bottom: 32px; }
    table { width: 100%; border-collapse: collapse; font-size: 12px; }
    thead tr { background: #1a3a1a; }
    th { padding: 10px 14px; text-align: right; font-weight: normal; font-size: 10px; letter-spacing: 0.5px; color: #c8a84b; border-bottom: 2px solid #c8a84b; }
    th:first-child { text-align: left; }
    td { padding: 11px 14px; text-align: right; border-bottom: 1px solid #1a3a1a; color: #a8d4a8; }
    td:first-child { text-align: left; color: #d4ead4; }
    tr:hover td { background: #0f2a0f; }
    .total-row td { background: #1a3a1a; color: #fff; font-weight: bold; }
    .total-row td:nth-child(2), .total-row td:nth-child(5) { color: #c8a84b; }
    .total-row td:nth-child(6) { color: #5bc85b; }
 
    /* PROGRESS BAR */
    .progress-wrap { display: flex; align-items: center; justify-content: flex-end; gap: 8px; }
    .progress-bar { width: 60px; height: 6px; background: #1a3a1a; border-radius: 3px; overflow: hidden; }
    .progress-fill { height: 100%; border-radius: 3px; }
    .progress-fill.green { background: #2e6d3a; }
    .progress-fill.red { background: #c0392b; }
 
    /* BADGE */
    .badge { padding: 3px 8px; border-radius: 3px; font-size: 10px; }
    .badge.ok { background: #1a3a1a; color: #5bc85b; border: 1px solid #2a6a2a; }
    .badge.warn { background: #3a1a1a; color: #e74c3c; border: 1px solid #6a2a2a; }
 
    /* STATS GRID */
    .stats-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 16px; margin-top: 28px; }
    .stat-card { background: #0d2110; border: 1px solid #1e3d1e; border-radius: 6px; padding: 16px; }
    .stat-value { font-size: 20px; font-weight: bold; color: #c8a84b; }
    .stat-label { font-size: 11px; color: #d4ead4; margin: 6px 0 4px; }
    .stat-delta { font-size: 10px; color: #7aab7a; }
 
    /* HALLAZGOS */
    .hallazgos-list { display: flex; flex-direction: column; gap: 16px; margin-bottom: 32px; }
    .hallazgo { background: #0d2110; border-radius: 4px; padding: 16px 20px; }
    .hallazgo.obs { border: 1px solid #e74c3c44; border-left: 4px solid #e74c3c; }
    .hallazgo.rec { border: 1px solid #2e6d3a44; border-left: 4px solid #2e6d3a; }
    .hallazgo-header { display: flex; align-items: center; gap: 12px; margin-bottom: 8px; }
    .hallazgo-tipo { padding: 2px 8px; font-size: 10px; border-radius: 2px; color: #fff; letter-spacing: 1px; font-family: monospace; }
    .hallazgo-tipo.obs { background: #e74c3c; }
    .hallazgo-tipo.rec { background: #2e6d3a; }
    .hallazgo-id { font-size: 11px; color: #7aab7a; font-family: monospace; }
    .hallazgo h4 { margin: 0 0 8px 0; font-size: 13px; color: #d4ead4; }
    .hallazgo p { margin: 0; font-size: 12px; color: #a0c4a0; line-height: 1.7; }
 
    /* RESPUESTA BOX */
    .respuesta-box { background: #0d2110; border: 1px solid #1e3d1e; border-radius: 6px; padding: 20px; }
    .respuesta-box h4 { color: #c8a84b; font-size: 12px; letter-spacing: 1px; margin: 0 0 16px 0; text-transform: uppercase; }
    .respuesta-box p { font-size: 12px; color: #b0d4b0; line-height: 1.8; margin: 0; }
    .respuesta-estado { display: flex; gap: 12px; margin-top: 12px; align-items: center; }
    .respuesta-label { font-size: 11px; color: #7aab7a; }
    .respuesta-badge { font-size: 11px; color: #5bc85b; background: #1a3a1a; padding: 2px 10px; border-radius: 3px; border: 1px solid #2a6a2a; }
 
    /* FOOTER */
    .footer { margin-top: 40px; padding-top: 16px; border-top: 1px solid #1a3a1a; display: flex; justify-content: space-between; font-size: 10px; color: #3a5a3a; }
 
    @media (max-width: 700px) {
      .kpis { grid-template-columns: repeat(2,1fr); }
      .chart-grid { grid-template-columns: 1fr; }
      .conclusion-grid { grid-template-columns: 1fr; }
      .stats-grid { grid-template-columns: 1fr; }
      .header-meta { flex-direction: column; gap: 4px; }
      .footer { flex-direction: column; gap: 4px; }
      .content { padding: 16px; }
    }
  </style>
</head>
<body>
 
<!-- HEADER -->
<div class="header">
  <div class="header-top">
    <div class="header-logo">⚖</div>
    <div>
      <div class="header-sub">Organismo de Control</div>
      <h1>SECRETARÍA CONTROL ECOLÓGICO</h1>
    </div>
  </div>
  <div class="header-divider">
    <h2>INFORME DE AUDITORÍA PRESUPUESTARIA — EJERCICIO 2012</h2>
    <div class="header-meta">
      <span>Actuación N° 2012/0187</span>
      <span>Entidad: Organismo Descentralizado — Control Ecológico</span>
      <span>Aprobado: Resolución SCE 42/2013</span>
    </div>
  </div>
</div>
 
<!-- KPIS -->
<div class="kpis">
  <div class="kpi"><div class="kpi-icon">📋</div><div class="kpi-value">$2.974M</div><div class="kpi-label">Crédito Vigente Total</div></div>
  <div class="kpi"><div class="kpi-icon">💳</div><div class="kpi-value">$2.568M</div><div class="kpi-label">Total Devengado</div></div>
  <div class="kpi"><div class="kpi-icon">📊</div><div class="kpi-value green">86.3%</div><div class="kpi-label">Ejecución Presupuestaria</div></div>
  <div class="kpi"><div class="kpi-icon">🏛</div><div class="kpi-value">4</div><div class="kpi-label">Fuentes de Financiamiento</div></div>
</div>
 
<!-- TABS -->
<div class="tabs">
  <button class="tab-btn active" onclick="showTab('resumen', this)">RESUMEN EJECUTIVO</button>
  <button class="tab-btn" onclick="showTab('fuentes', this)">FUENTES DE FINANCIAMIENTO</button>
  <button class="tab-btn" onclick="showTab('conceptos', this)">ESTRUCTURA DEL GASTO</button>
  <button class="tab-btn" onclick="showTab('evolucion', this)">EVOLUCIÓN MENSUAL</button>
  <button class="tab-btn" onclick="showTab('hallazgos', this)">HALLAZGOS</button>
</div>
 
<!-- CONTENT -->
<div class="content">
 
  <!-- RESUMEN -->
  <div id="tab-resumen" class="tab-panel active">
    <h3 class="section-title">I. OBJETO DE LA AUDITORÍA</h3>
    <p class="body-text">
      La presente actuación tuvo por objeto verificar la legalidad, regularidad y eficiencia en la ejecución presupuestaria del Organismo durante el ejercicio fiscal 2012, con especial énfasis en la utilización de los créditos asignados por fuente de financiamiento y objeto del gasto, conforme lo establecido en la Ley N° 25.675 General del Ambiente y los Sistemas de Control del Sector Público Nacional.
    </p>
    <h3 class="section-title">II. ALCANCE</h3>
    <p class="body-text">
      Se auditaron el 100% de las fuentes de financiamiento y conceptos de gasto, abarcando un crédito vigente total de <span class="highlight">$2.974,0 millones</span> y devengado consumido de <span class="highlight">$2.567,7 millones</span>, lo que representa una ejecución presupuestaria global del <span class="highlight-green">86,3%</span>.
    </p>
    <div class="chart-grid">
      <div class="chart-box">
        <div class="chart-title">Distribución del Gasto Devengado</div>
        <div class="chart-container"><canvas id="pieChart" height="200"></canvas></div>
      </div>
      <div class="chart-box">
        <div class="chart-title">Ejecución por Fuente (%)</div>
        <div class="chart-container"><canvas id="ejecChart" height="200"></canvas></div>
      </div>
    </div>
    <h3 class="section-title">III. CONCLUSIONES GENERALES</h3>
    <div class="conclusion-grid">
      <div class="conclusion-item ok"><span class="icon">✅</span><span>La ejecución global del 86,3% se encuentra dentro de parámetros aceptables para organismos del sector ambiental.</span></div>
      <div class="conclusion-item warn"><span class="icon">⚠️</span><span>Se detectaron 2 observaciones formales que requieren atención por parte de las autoridades del Organismo.</span></div>
      <div class="conclusion-item ok"><span class="icon">✅</span><span>Los Gastos en Personal representan el 61,7% del presupuesto devengado, coherente con la naturaleza del Organismo de control ambiental.</span></div>
      <div class="conclusion-item warn"><span class="icon">⚠️</span><span>La subejecución en Bienes de Uso (36,7%) podría comprometer la capacidad operativa del Organismo en el mediano plazo.</span></div>
    </div>
  </div>
 
  <!-- FUENTES -->
  <div id="tab-fuentes" class="tab-panel">
    <h3 class="section-title">ANÁLISIS POR FUENTE DE FINANCIAMIENTO</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th style="text-align:left">Fuente</th>
            <th>Crédito Vigente</th>
            <th>Compromiso</th>
            <th>Devengado</th>
            <th>Ejec. %</th>
            <th>Estado</th>
          </tr>
        </thead>
        <tbody id="fuentes-tbody"></tbody>
      </table>
    </div>
    <div class="chart-container"><canvas id="fuentesBar" height="120"></canvas></div>
  </div>
 
  <!-- CONCEPTOS -->
  <div id="tab-conceptos" class="tab-panel">
    <h3 class="section-title">ESTRUCTURA DEL GASTO POR CONCEPTO</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th style="text-align:left">Concepto</th>
            <th>Crédito Vigente</th>
            <th>Devengado</th>
            <th>Diferencia</th>
            <th>Ejecución</th>
            <th>% del Total</th>
          </tr>
        </thead>
        <tbody id="conceptos-tbody"></tbody>
      </table>
    </div>
    <div class="chart-container"><canvas id="conceptosBar" height="120"></canvas></div>
  </div>
 
  <!-- EVOLUCION -->
  <div id="tab-evolucion" class="tab-panel">
    <h3 class="section-title">EVOLUCIÓN MENSUAL DEL GASTO (en $M)</h3>
    <p style="font-size:12px;color:#7aab7a;margin-bottom:24px;font-style:italic">* Datos proyectados sobre base de la ejecución anual — Ejercicio 2012. Cifras en millones de pesos ($M).</p>
    <div class="chart-container"><canvas id="lineChart" height="120"></canvas></div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-value">$2.222,8M</div><div class="stat-label">Devengado Acumulado</div><div class="stat-delta">+4,2% vs ejercicio 2011</div></div>
      <div class="stat-card"><div class="stat-value">$44M</div><div class="stat-label">Brecha Comprometido/Pagado</div><div class="stat-delta">Dentro de parámetros normales</div></div>
      <div class="stat-card"><div class="stat-value">7,2%/mes</div><div class="stat-label">Ritmo de Ejecución</div><div class="stat-delta">Promedio mensual</div></div>
    </div>
  </div>
 
  <!-- HALLAZGOS -->
  <div id="tab-hallazgos" class="tab-panel">
    <h3 class="section-title">OBSERVACIONES Y RECOMENDACIONES</h3>
    <div class="hallazgos-list">
      <div class="hallazgo obs">
        <div class="hallazgo-header"><span class="hallazgo-tipo obs">OBSERVACIÓN</span><span class="hallazgo-id">OBS-001</span></div>
        <h4>Subejecución en Bienes de Uso</h4>
        <p>El crédito destinado a Bienes de Uso presenta una ejecución del 36,7%, significativamente por debajo de la media del organismo (86,3%). Se recomienda rever la planificación de adquisiciones.</p>
      </div>
      <div class="hallazgo obs">
        <div class="hallazgo-header"><span class="hallazgo-tipo obs">OBSERVACIÓN</span><span class="hallazgo-id">OBS-002</span></div>
        <h4>Incremento de Activos Financieros sin ejecución</h4>
        <p>El crédito de $248,2M asignado a Incremento de Activos Financieros no registra pagos en el período auditado. Se requiere documentación justificatoria.</p>
      </div>
      <div class="hallazgo rec">
        <div class="hallazgo-header"><span class="hallazgo-tipo rec">RECOMENDACIÓN</span><span class="hallazgo-id">REC-001</span></div>
        <h4>Mejora en planificación presupuestaria</h4>
        <p>Se sugiere implementar un sistema de seguimiento trimestral del gasto por fuente de financiamiento, con alertas tempranas ante desviaciones superiores al 15% respecto a lo programado.</p>
      </div>
      <div class="hallazgo rec">
        <div class="hallazgo-header"><span class="hallazgo-tipo rec">RECOMENDACIÓN</span><span class="hallazgo-id">REC-002</span></div>
        <h4>Fortalecimiento del control interno</h4>
        <p>Reforzar los procedimientos de control previo para Transferencias Externas, cuya ejecución del 61,9% es la más baja entre las fuentes de financiamiento.</p>
      </div>
    </div>
    <div class="respuesta-box">
      <h4>RESPUESTA DEL ORGANISMO AUDITADO</h4>
      <p>La autoridad auditada tomó conocimiento de las observaciones formuladas mediante Nota DGPLA N° 2013/0054 de fecha 15/03/2013. Comprometió la implementación de las recomendaciones en un plazo de 90 días corridos, con presentación de un plan de acción detallado ante esta Auditoría General.</p>
      <div class="respuesta-estado">
        <span class="respuesta-label">Estado de respuesta:</span>
        <span class="respuesta-badge">RECIBIDA Y EN SEGUIMIENTO</span>
      </div>
    </div>
  </div>
 
  <div class="footer">
    <span>SECRETARÍA CONTROL ECOLÓGICO — Uso Interno</span>
    <span>Actuación N° 2012/0187 · Página 1 de 1</span>
    <span>Generado: Abril 2013</span>
  </div>
</div>
 
<script>
  // ---- DATA ----
  const fuentes = [
    { name: "Tesoro Nacional",    credito: 1685.1, devengado: 1625.8, ejecucion: 0.9648 },
    { name: "Recursos Propios",   credito: 1254.5, devengado: 920.5,  ejecucion: 0.7337 },
    { name: "Transf. Externas",   credito: 33.9,   devengado: 21.0,   ejecucion: 0.6190 },
    { name: "Crédito Interno",    credito: 0.4,    devengado: 0.4,    ejecucion: 0.9998 },
  ];
  const conceptos = [
    { name: "Gastos en Personal",       credito: 1596.7, devengado: 1583.4 },
    { name: "Servicios No Pers.",       credito: 499.2,  devengado: 404.6  },
    { name: "Transferencias",           credito: 330.3,  devengado: 318.0  },
    { name: "Inc. Act. Financieros",    credito: 248.2,  devengado: 0.0    },
    { name: "Gastos Figurativos",       credito: 216.1,  devengado: 216.1  },
    { name: "Bienes de Uso",            credito: 45.8,   devengado: 16.8   },
    { name: "Bienes de Consumo",        credito: 37.8,   devengado: 28.8   },
  ];
  const meses = ["Ene","Feb","Mar","Abr","May","Jun","Jul","Ago","Sep","Oct","Nov","Dic"];
  const comprometido = [142,168,195,221,248,267,289,312,334,358,381,406];
  const devengadoMes = [138,155,189,208,231,254,272,296,315,339,362,387];
  const pagadoMes    = [121,143,172,191,215,238,253,274,298,318,341,362];
 
  const totalDevengado = fuentes.reduce((a,b) => a+b.devengado, 0);
  const fmtM = v => `$${(v).toFixed(1)}M`;
  const fmtPct = v => `${(v*100).toFixed(1)}%`;
 
  // ---- TABS ----
  function showTab(id, btn) {
    document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    document.getElementById('tab-'+id).classList.add('active');
    btn.classList.add('active');
  }
 
  // ---- TABLES ----
  // Fuentes
  const ftbody = document.getElementById('fuentes-tbody');
  fuentes.forEach(f => {
    const ok = f.ejecucion >= 0.75;
    const pctW = Math.round(f.ejecucion*100);
    ftbody.innerHTML += `
      <tr>
        <td><b>${f.name}</b></td>
        <td>${fmtM(f.credito)}</td>
        <td>${fmtM(f.credito*f.ejecucion*1.02)}</td>
        <td style="color:#c8a84b;font-weight:bold">${fmtM(f.devengado)}</td>
        <td>
          <div class="progress-wrap">
            <div class="progress-bar"><div class="progress-fill ${ok?'green':'red'}" style="width:${pctW}%"></div></div>
            <span style="color:${ok?'#5bc85b':'#e74c3c'}">${fmtPct(f.ejecucion)}</span>
          </div>
        </td>
        <td><span class="badge ${ok?'ok':'warn'}">${ok?'REGULAR':'OBSERVADO'}</span></td>
      </tr>`;
  });
  const totalCredF = fuentes.reduce((a,b)=>a+b.credito,0);
  ftbody.innerHTML += `<tr class="total-row"><td>TOTAL</td><td>${fmtM(totalCredF)}</td><td>—</td><td>${fmtM(totalDevengado)}</td><td style="color:#5bc85b">${fmtPct(totalDevengado/totalCredF)}</td><td></td></tr>`;
 
  // Conceptos
  const ctbody = document.getElementById('conceptos-tbody');
  conceptos.forEach(c => {
    const ejec = c.credito > 0 ? c.devengado/c.credito : 0;
    const pct  = totalDevengado > 0 ? c.devengado/totalDevengado : 0;
    const eColor = ejec >= 0.75 ? '#5bc85b' : ejec === 0 ? '#e74c3c' : '#f39c12';
    const devVal = c.devengado > 0 ? `<span style="color:#c8a84b;font-weight:bold">${fmtM(c.devengado)}</span>` : `<span style="color:#e74c3c">$0</span>`;
    ctbody.innerHTML += `
      <tr>
        <td>${c.name}</td>
        <td>${fmtM(c.credito)}</td>
        <td>${devVal}</td>
        <td style="color:#e74c3c">${fmtM(c.credito-c.devengado)}</td>
        <td style="color:${eColor}">${fmtPct(ejec)}</td>
        <td>
          <div class="progress-wrap">
            <div class="progress-bar" style="width:80px"><div class="progress-fill green" style="width:${Math.round(pct*100)}%"></div></div>
            <span style="color:#a8d4a8">${fmtPct(pct)}</span>
          </div>
        </td>
      </tr>`;
  });
 
  // ---- CHARTS ----
  const GRID = '#1a3a1a';
  const TEXT = '#a8d4a8';
  Chart.defaults.color = TEXT;
 
  // Pie
  new Chart(document.getElementById('pieChart'), {
    type: 'doughnut',
    data: {
      labels: conceptos.filter(c=>c.devengado>0).map(c=>c.name),
      datasets: [{ data: conceptos.filter(c=>c.devengado>0).map(c=>c.devengado),
        backgroundColor: ['#1a3a1a','#2e6d3a','#4a9b5b','#a8d4a8','#d4ead4'],
        borderColor: '#071a07', borderWidth: 2 }]
    },
    options: { plugins: { legend: { position:'bottom', labels:{ font:{size:10}, boxWidth:10 }}}, responsive:true }
  });
 
  // Ejecución horizontal bar
  new Chart(document.getElementById('ejecChart'), {
    type: 'bar',
    data: {
      labels: fuentes.map(f=>f.name),
      datasets: [{ label:'Ejecución', data: fuentes.map(f=>+(f.ejecucion*100).toFixed(1)),
        backgroundColor: fuentes.map(f=>f.ejecucion>=0.75?'#2e6d3a':'#c0392b'),
        borderRadius: 3 }]
    },
    options: {
      indexAxis: 'y',
      plugins: { legend:{display:false} },
      scales: { x:{ max:100, ticks:{callback:v=>v+'%'}, grid:{color:GRID} }, y:{ grid:{color:GRID} } },
      responsive:true
    }
  });
 
  // Fuentes bar
  new Chart(document.getElementById('fuentesBar'), {
    type: 'bar',
    data: {
      labels: fuentes.map(f=>f.name),
      datasets: [
        { label:'Crédito Vigente', data: fuentes.map(f=>f.credito), backgroundColor:'#1a3a1a', borderRadius:3 },
        { label:'Devengado',       data: fuentes.map(f=>f.devengado), backgroundColor:'#2e6d3a', borderRadius:3 }
      ]
    },
    options: {
      plugins: { legend:{ labels:{ color:TEXT } } },
      scales: { x:{ grid:{color:GRID} }, y:{ ticks:{callback:v=>'$'+v+'M'}, grid:{color:GRID} } },
      responsive:true
    }
  });
 
  // Conceptos bar
  new Chart(document.getElementById('conceptosBar'), {
    type: 'bar',
    data: {
      labels: conceptos.map(c=>c.name),
      datasets: [
        { label:'Crédito Vigente', data: conceptos.map(c=>c.credito), backgroundColor:'#1a3a1a', borderRadius:3 },
        { label:'Devengado',       data: conceptos.map(c=>c.devengado), backgroundColor:'#c8a84b', borderRadius:3 }
      ]
    },
    options: {
      plugins: { legend:{ labels:{ color:TEXT } } },
      scales: { x:{ ticks:{ maxRotation:25, font:{size:9} }, grid:{color:GRID} }, y:{ ticks:{callback:v=>'$'+v+'M'}, grid:{color:GRID} } },
      responsive:true
    }
  });
 
  // Line chart
  new Chart(document.getElementById('lineChart'), {
    type: 'line',
    data: {
      labels: meses,
      datasets: [
        { label:'Comprometido', data: comprometido, borderColor:'#4a9b5b', tension:0.3, pointRadius:0, borderWidth:2 },
        { label:'Devengado',    data: devengadoMes, borderColor:'#c8a84b', tension:0.3, pointRadius:0, borderWidth:2 },
        { label:'Pagado',       data: pagadoMes,    borderColor:'#5bc85b', tension:0.3, pointRadius:0, borderWidth:2 }
      ]
    },
    options: {
      plugins: { legend:{ labels:{ color:TEXT } } },
      scales: { x:{ grid:{color:GRID} }, y:{ ticks:{callback:v=>'$'+v+'M'}, grid:{color:GRID} } },
      responsive:true
    }
  });
</script>
</body>
</html>
