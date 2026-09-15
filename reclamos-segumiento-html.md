<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Seguimiento de reclamos — Prototipo de experimento</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #F1F3EE;
    --panel: #FFFFFF;
    --ink: #1C2A22;
    --ink-soft: #55645A;
    --accent: #B68A1E;
    --accent-soft: #EFE3C2;
    --line: #D7DBD2;
    --line-strong: #1C2A22;
    --error: #A8482E;
    --ok: #3D6B4C;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    background: var(--bg);
    color: var(--ink);
    font-family: 'Inter', -apple-system, sans-serif;
    line-height: 1.5;
    min-height: 100vh;
  }
  .wrap {
    max-width: 640px;
    margin: 0 auto;
    padding: 40px 20px 80px;
  }
  .masthead {
    border-bottom: 2px solid var(--line-strong);
    padding-bottom: 20px;
    margin-bottom: 28px;
  }
  .masthead .tag {
    font-size: 13px;
    color: var(--ink-soft);
    letter-spacing: 0.02em;
  }
  h1 {
    font-family: 'Fraunces', serif;
    font-weight: 500;
    font-size: 30px;
    margin: 6px 0 8px;
    letter-spacing: -0.01em;
  }
  .masthead p {
    color: var(--ink-soft);
    font-size: 14.5px;
    margin: 0;
    max-width: 50ch;
  }
  nav.tabs {
    display: flex;
    gap: 4px;
    margin-bottom: 28px;
    border-bottom: 1px solid var(--line);
  }
  nav.tabs button {
    background: none;
    border: none;
    font-family: 'Inter', sans-serif;
    font-size: 14.5px;
    font-weight: 500;
    color: var(--ink-soft);
    padding: 10px 4px;
    margin-right: 22px;
    cursor: pointer;
    border-bottom: 2px solid transparent;
    transform: translateY(1px);
  }
  nav.tabs button.active {
    color: var(--ink);
    border-bottom-color: var(--accent);
  }
  .view { display: none; }
  .view.active { display: block; }

  .card {
    background: var(--panel);
    border: 1px solid var(--line);
    border-radius: 3px;
    padding: 28px;
  }

  label {
    display: block;
    font-size: 13.5px;
    font-weight: 500;
    margin: 18px 0 6px;
  }
  label:first-of-type { margin-top: 0; }
  input[type=text], input[type=email], textarea, select {
    width: 100%;
    padding: 10px 12px;
    border: 1px solid var(--line);
    border-radius: 2px;
    font-family: 'Inter', sans-serif;
    font-size: 14.5px;
    background: var(--bg);
    color: var(--ink);
  }
  textarea { min-height: 90px; resize: vertical; }
  input:focus, textarea:focus, select:focus, button:focus-visible {
    outline: 2px solid var(--accent);
    outline-offset: 1px;
  }
  .hint { font-size: 12.5px; color: var(--ink-soft); margin-top: 4px; }

  .btn {
    display: inline-block;
    margin-top: 22px;
    background: var(--ink);
    color: #fff;
    border: none;
    padding: 11px 22px;
    font-size: 14.5px;
    font-weight: 500;
    border-radius: 2px;
    cursor: pointer;
    font-family: 'Inter', sans-serif;
  }
  .btn:hover { background: var(--accent); }
  .btn.secondary {
    background: none;
    color: var(--ink);
    border: 1px solid var(--line-strong);
  }
  .btn.secondary:hover { background: var(--accent-soft); border-color: var(--accent); }
  .btn:disabled { opacity: 0.45; cursor: not-allowed; }

  .confirm {
    text-align: center;
    padding: 10px 0 4px;
  }
  .code-box {
    display: inline-block;
    font-family: 'Fraunces', serif;
    font-size: 26px;
    letter-spacing: 0.06em;
    border: 1px dashed var(--accent);
    background: var(--accent-soft);
    padding: 10px 22px;
    margin: 14px 0;
    border-radius: 2px;
  }

  /* Timeline */
  .timeline {
    margin: 26px 0 8px;
    padding-left: 4px;
  }
  .stop {
    position: relative;
    padding: 0 0 26px 30px;
    border-left: 2px solid var(--line);
  }
  .stop:last-child { border-left-color: transparent; padding-bottom: 0; }
  .stop::before {
    content: '';
    position: absolute;
    left: -7px;
    top: 0;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: var(--panel);
    border: 2px solid var(--line);
  }
  .stop.done::before { background: var(--ok); border-color: var(--ok); }
  .stop.current::before { background: var(--accent); border-color: var(--accent); }
  .stop .label { font-weight: 600; font-size: 15px; }
  .stop .when { font-size: 12.5px; color: var(--ink-soft); margin-top: 2px; }
  .stop .note { font-size: 13.5px; color: var(--ink-soft); margin-top: 4px; }
  .stop.pending .label { color: var(--ink-soft); font-weight: 500; }

  .banner {
    font-size: 13.5px;
    padding: 10px 14px;
    border-radius: 2px;
    margin-bottom: 18px;
  }
  .banner.error { background: #F6E4DD; color: var(--error); }
  .banner.ok { background: #E4EEE6; color: var(--ok); }

  .admin-row {
    border: 1px solid var(--line);
    border-radius: 2px;
    padding: 14px 16px;
    margin-bottom: 12px;
    background: var(--panel);
  }
  .admin-row .top { display: flex; justify-content: space-between; align-items: baseline; }
  .admin-row .code { font-family: 'Fraunces', serif; font-size: 16px; }
  .admin-row .estado-pill {
    font-size: 11.5px;
    text-transform: none;
    padding: 3px 9px;
    border-radius: 12px;
    background: var(--accent-soft);
    color: var(--ink);
  }
  .admin-row .desc { font-size: 13.5px; color: var(--ink-soft); margin: 8px 0; }
  .admin-row .meta { font-size: 12px; color: var(--ink-soft); }
  .admin-actions { display: flex; gap: 8px; margin-top: 10px; }
  .admin-actions button { font-size: 13px; padding: 7px 12px; }

  .stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-bottom: 22px;
  }
  .stat {
    border: 1px solid var(--line);
    background: var(--panel);
    padding: 14px 12px;
    border-radius: 2px;
  }
  .stat .n { font-family: 'Fraunces', serif; font-size: 26px; }
  .stat .l { font-size: 12px; color: var(--ink-soft); }

  .radio-group { display: flex; flex-direction: column; gap: 8px; margin-top: 8px; }
  .radio-group label {
    display: flex; align-items: center; gap: 8px;
    font-weight: 400; font-size: 14px; margin: 0;
    cursor: pointer;
  }
  .radio-group input { width: auto; }

  .check-row {
    display: flex; align-items: flex-start; gap: 10px;
    margin-top: 20px; padding: 14px; background: var(--accent-soft); border-radius: 2px;
  }
  .check-row input { width: auto; margin-top: 3px; }
  .check-row label { margin: 0; font-weight: 500; font-size: 14px; }

  footer {
    margin-top: 40px;
    font-size: 12px;
    color: var(--ink-soft);
    border-top: 1px solid var(--line);
    padding-top: 14px;
  }
  footer a { color: var(--ink-soft); }
</style>
</head>
<body>
<div class="wrap">

  <div class="masthead">
    <div class="tag">Prototipo de experimento — no es un sistema de una marca real</div>
    <h1>Seguí tu reclamo</h1>
    <p>Esto es parte de una investigación de un equipo de Negocios Digitales sobre cómo el seguimiento de un reclamo afecta la confianza en una marca. Tus datos se usan solo para esta prueba.</p>
  </div>

  <nav class="tabs">
    <button data-view="reportar" class="active">Reportar un reclamo</button>
    <button data-view="seguir">Seguir mi reclamo</button>
    <button data-view="admin">Equipo (uso interno)</button>
  </nav>

  <!-- REPORTAR -->
  <section class="view active" id="view-reportar">
    <div class="card">
      <div id="reportar-banner"></div>
      <form id="form-reportar">
        <label for="nombre">Nombre</label>
        <input type="text" id="nombre" required />

        <label for="contacto">Mail o WhatsApp de contacto</label>
        <input type="text" id="contacto" required placeholder="para avisarte cuando cambie el estado" />

        <label for="descripcion">Contanos qué pasó con tu compra</label>
        <textarea id="descripcion" required placeholder="Ej: el talle no coincidía con la tabla de medidas, la prenda llegó con una falla, etc."></textarea>

        <label for="experiencia-previa">¿Tuviste antes algún reclamo con una compra de ropa online (con esta u otra marca)?</label>
        <select id="experiencia-previa">
          <option value="si">Sí</option>
          <option value="no">No</option>
        </select>

        <button type="submit" class="btn">Enviar reclamo</button>
      </form>
    </div>
  </section>

  <!-- SEGUIR -->
  <section class="view" id="view-seguir">
    <div class="card" id="seguir-lookup">
      <div id="seguir-banner"></div>
      <label for="codigo">Código de tu reclamo</label>
      <input type="text" id="codigo" placeholder="Ej: RC-4F9K" />
      <button class="btn" id="btn-buscar">Ver estado</button>
    </div>
    <div class="card" id="seguir-resultado" style="display:none; margin-top:16px;"></div>
  </section>

  <!-- ADMIN -->
  <section class="view" id="view-admin">
    <div class="stats" id="admin-stats"></div>
    <div id="admin-lista"></div>
  </section>

  <footer>
    Instrumento construido para el experimento de la Clase 5 (Hipótesis de Valor). Datos guardados en almacenamiento compartido del artifact — visibles para cualquiera con este link. No cargar datos personales reales sensibles.
  </footer>
</div>

<script>
const STORAGE_KEY = 'reclamos-casos-clase5';
const ESTADOS = ['recibido', 'revision', 'resuelto'];
const ESTADO_LABEL = { recibido: 'Recibido', revision: 'En revisión', resuelto: 'Resuelto' };

async function loadCases() {
  try {
    const res = await window.storage.get(STORAGE_KEY, true);
    return res && res.value ? JSON.parse(res.value) : [];
  } catch (e) {
    return [];
  }
}
async function saveCases(cases) {
  try {
    await window.storage.set(STORAGE_KEY, JSON.stringify(cases), true);
    return true;
  } catch (e) {
    console.error('Error guardando', e);
    return false;
  }
}
function genCode() {
  const chars = 'ABCDEFGHJKMNPQRSTUVWXYZ23456789';
  let s = '';
  for (let i = 0; i < 4; i++) s += chars[Math.floor(Math.random() * chars.length)];
  return 'RC-' + s;
}
function fmtDate(iso) {
  const d = new Date(iso);
  return d.toLocaleDateString('es-AR', { day: '2-digit', month: 'short' }) + ' ' +
         d.toLocaleTimeString('es-AR', { hour: '2-digit', minute: '2-digit' });
}

// ---- Tabs ----
document.querySelectorAll('nav.tabs button').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('nav.tabs button').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('view-' + btn.dataset.view).classList.add('active');
    if (btn.dataset.view === 'admin') renderAdmin();
  });
});

// ---- Reportar ----
document.getElementById('form-reportar').addEventListener('submit', async (e) => {
  e.preventDefault();
  const banner = document.getElementById('reportar-banner');
  banner.innerHTML = '';
  const btn = e.target.querySelector('button');
  btn.disabled = true;
  btn.textContent = 'Enviando…';

  const nuevo = {
    id: genCode(),
    nombre: document.getElementById('nombre').value.trim(),
    contacto: document.getElementById('contacto').value.trim(),
    descripcion: document.getElementById('descripcion').value.trim(),
    experienciaPrevia: document.getElementById('experiencia-previa').value,
    estado: 'recibido',
    createdAt: new Date().toISOString(),
    historial: [{ estado: 'recibido', ts: new Date().toISOString(), nota: '' }],
    encuestaCierre: null
  };

  const cases = await loadCases();
  cases.push(nuevo);
  const ok = await saveCases(cases);
  btn.disabled = false;
  btn.textContent = 'Enviar reclamo';

  if (!ok) {
    banner.innerHTML = '<div class="banner error">No pudimos guardar tu reclamo. Probá de nuevo en un momento.</div>';
    return;
  }
  e.target.reset();
  banner.innerHTML = `
    <div class="confirm">
      <div class="banner ok">Reclamo recibido</div>
      <p>Guardá este código para consultar el estado más adelante:</p>
      <div class="code-box">${nuevo.id}</div>
      <p class="hint">Te vamos a avisar por ${nuevo.contacto.includes('@') ? 'mail' : 'WhatsApp'} cuando cambie el estado.</p>
    </div>`;
});

// ---- Seguir ----
document.getElementById('btn-buscar').addEventListener('click', buscarCaso);
document.getElementById('codigo').addEventListener('keydown', (e) => { if (e.key === 'Enter') buscarCaso(); });

async function buscarCaso() {
  const banner = document.getElementById('seguir-banner');
  const resultado = document.getElementById('seguir-resultado');
  const codigo = document.getElementById('codigo').value.trim().toUpperCase();
  banner.innerHTML = '';
  resultado.style.display = 'none';
  if (!codigo) return;

  const cases = await loadCases();
  const caso = cases.find(c => c.id === codigo);
  if (!caso) {
    banner.innerHTML = '<div class="banner error">No encontramos ese código. Revisá que esté bien escrito.</div>';
    return;
  }
  renderTimeline(caso, cases);
}

function renderTimeline(caso, allCases) {
  const resultado = document.getElementById('seguir-resultado');
  resultado.style.display = 'block';

  const idxActual = ESTADOS.indexOf(caso.estado);
  let html = `<div class="code-box" style="font-size:18px; padding:6px 16px; margin-bottom:18px;">${caso.id}</div>
  <div class="timeline">`;

  ESTADOS.forEach((estado, idx) => {
    const hist = caso.historial.find(h => h.estado === estado);
    let cls = 'pending';
    if (idx < idxActual) cls = 'done';
    else if (idx === idxActual) cls = 'current';
    html += `<div class="stop ${cls}">
      <div class="label">${ESTADO_LABEL[estado]}</div>
      ${hist ? `<div class="when">${fmtDate(hist.ts)}</div>` : ''}
      ${hist && hist.nota ? `<div class="note">${hist.nota}</div>` : ''}
    </div>`;
  });
  html += `</div>`;

  resultado.innerHTML = html;

  if (caso.estado === 'resuelto') {
    if (!caso.encuestaCierre) {
      resultado.innerHTML += renderEncuestaForm(caso.id);
      attachEncuestaHandler(caso.id, allCases);
    } else {
      resultado.innerHTML += `<div class="banner ok" style="margin-top:18px;">Ya nos contaste tu experiencia. ¡Gracias por participar de la prueba!</div>`;
    }
  }
}

function renderEncuestaForm(caseId) {
  return `
  <div style="margin-top:22px; padding-top:20px; border-top:1px solid var(--line);">
    <p style="font-weight:500; margin-bottom:4px;">Tu reclamo quedó resuelto. Tres preguntas cortas:</p>
    <form id="form-encuesta" data-caseid="${caseId}">
      <label>Comparado con reclamos anteriores (WhatsApp, mail, sin seguimiento), ¿cómo te resultó este proceso?</label>
      <div class="radio-group">
        <label><input type="radio" name="comparacion" value="mejor" required /> Mejor que antes</label>
        <label><input type="radio" name="comparacion" value="igual" /> Igual que antes</label>
        <label><input type="radio" name="comparacion" value="peor" /> Peor que antes</label>
        <label><input type="radio" name="comparacion" value="na" /> No tuve otro reclamo antes para comparar</label>
      </div>

      <label>Después de esta experiencia, ¿qué tan dispuesto/a estás a volver a comprarle a esta marca?</label>
      <div class="radio-group">
        <label><input type="radio" name="disposicion" value="mas" required /> Más dispuesto/a que antes</label>
        <label><input type="radio" name="disposicion" value="igual" /> Igual que antes</label>
        <label><input type="radio" name="disposicion" value="menos" /> Menos dispuesto/a que antes</label>
      </div>

      <label for="comentario">¿Algo más que quieras contarnos? (opcional)</label>
      <textarea id="comentario" placeholder="Opcional"></textarea>

      <div class="check-row">
        <input type="checkbox" id="recontacto" />
        <label for="recontacto">Acepto que la marca me vuelva a contactar cuando tenga novedades o promociones.</label>
      </div>

      <button type="submit" class="btn">Enviar respuestas</button>
    </form>
  </div>`;
}

function attachEncuestaHandler(caseId, allCases) {
  const form = document.getElementById('form-encuesta');
  form.addEventListener('submit', async (e) => {
    e.preventDefault();
    const comparacion = form.querySelector('input[name=comparacion]:checked')?.value;
    const disposicion = form.querySelector('input[name=disposicion]:checked')?.value;
    const comentario = document.getElementById('comentario').value.trim();
    const aceptaRecontacto = document.getElementById('recontacto').checked;

    const cases = await loadCases();
    const caso = cases.find(c => c.id === caseId);
    caso.encuestaCierre = { comparacion, disposicion, comentario, aceptaRecontacto, ts: new Date().toISOString() };
    await saveCases(cases);

    document.getElementById('seguir-resultado').innerHTML += `<div class="banner ok" style="margin-top:18px;">¡Gracias! Registramos tu respuesta.</div>`;
    form.remove();
  });
}

// ---- Admin ----
async function renderAdmin() {
  const cases = await loadCases();
  const lista = document.getElementById('admin-lista');
  const stats = document.getElementById('admin-stats');

  const total = cases.length;
  const completaron = cases.filter(c => c.encuestaCierre).length;
  const masDisposicion = cases.filter(c => c.encuestaCierre?.disposicion === 'mas').length;
  const aceptaRecontacto = cases.filter(c => c.encuestaCierre?.aceptaRecontacto).length;
  const cumpleCriterio = cases.filter(c => c.encuestaCierre?.disposicion === 'mas' && c.encuestaCierre?.aceptaRecontacto).length;

  stats.innerHTML = `
    <div class="stat"><div class="n">${total}</div><div class="l">Reclamos reportados</div></div>
    <div class="stat"><div class="n">${completaron}</div><div class="l">Completaron el cierre</div></div>
    <div class="stat"><div class="n">${cumpleCriterio}</div><div class="l">Cumplen criterio completo (+ disposición y + recontacto)</div></div>
  `;

  if (total === 0) {
    lista.innerHTML = '<p class="hint">Todavía no hay reclamos cargados.</p>';
    return;
  }

  lista.innerHTML = cases
    .slice()
    .reverse()
    .map(c => {
      const idx = ESTADOS.indexOf(c.estado);
      const puedeAvanzar = idx < ESTADOS.length - 1;
      return `
      <div class="admin-row">
        <div class="top">
          <span class="code">${c.id}</span>
          <span class="estado-pill">${ESTADO_LABEL[c.estado]}</span>
        </div>
        <div class="meta">${c.nombre} · ${c.contacto} · reportado ${fmtDate(c.createdAt)}</div>
        <div class="desc">${c.descripcion}</div>
        ${c.encuestaCierre ? `<div class="meta">Cierre: comparación=${c.encuestaCierre.comparacion}, disposición=${c.encuestaCierre.disposicion}, recontacto=${c.encuestaCierre.aceptaRecontacto ? 'sí' : 'no'}</div>` : ''}
        <div class="admin-actions">
          ${puedeAvanzar ? `<button class="btn secondary" onclick="avanzarEstado('${c.id}')">Avanzar a "${ESTADO_LABEL[ESTADOS[idx + 1]]}"</button>` : ''}
        </div>
      </div>`;
    })
    .join('');
}

async function avanzarEstado(caseId) {
  const nota = prompt('Nota opcional para esta actualización (se muestra al participante, ej. "Confirmamos el cambio, te enviamos la prenda nueva"):') || '';
  const cases = await loadCases();
  const caso = cases.find(c => c.id === caseId);
  const idx = ESTADOS.indexOf(caso.estado);
  if (idx >= ESTADOS.length - 1) return;
  const nuevoEstado = ESTADOS[idx + 1];
  caso.estado = nuevoEstado;
  caso.historial.push({ estado: nuevoEstado, ts: new Date().toISOString(), nota });
  await saveCases(cases);
  alert('Estado actualizado. Recordá avisarle manualmente al participante por ' + (caso.contacto.includes('@') ? 'mail' : 'WhatsApp') + ' que puede volver a consultar su código.');
  renderAdmin();
}
</script>
</body>
</html>
