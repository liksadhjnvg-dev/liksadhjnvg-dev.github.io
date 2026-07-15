# liksadhjnvg-dev.github.io

<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Trainingslog</title>
<style>body{margin:0;background:#15171b;padding:12px 0;}</style>
</head>
<body>
<!-- Trainingslog: Push/Pull/Beine -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Oswald:wght@500;600;700&family=IBM+Plex+Mono:wght@400;500;600&family=Inter:wght@400;500&display=swap" rel="stylesheet">
<style>
  #tl-root {
    --bg: #15171b;
    --surface: #1e2127;
    --surface-2: #272b32;
    --text: #edeef0;
    --text-muted: #8b8f96;
    --accent: #e8862e;
    --accent-dim: #3a2c1c;
    --border: #303540;
    --ok: #6fae6f;
    font-family: 'Inter', sans-serif;
    color: var(--text);
    background: var(--bg);
    padding: 24px 16px 32px;
    border-radius: 16px;
    max-width: 720px;
    margin: 0 auto;
  }
  #tl-root * { box-sizing: border-box; }
  .tl-h1 {
    font-family: 'Oswald', sans-serif;
    font-weight: 700;
    font-size: 26px;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    margin: 0 0 4px;
  }
  .tl-sub { color: var(--text-muted); font-size: 13px; margin: 0 0 20px; }
  .tl-tabs { display: flex; gap: 8px; margin-bottom: 20px; border-bottom: 1px solid var(--border); }
  .tl-tab {
    font-family: 'Oswald', sans-serif;
    font-weight: 600;
    font-size: 14px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    background: none;
    border: none;
    color: var(--text-muted);
    padding: 10px 4px 12px;
    cursor: pointer;
    position: relative;
    flex: 1;
  }
  .tl-tab.active { color: var(--accent); }
  .tl-tab.active::after {
    content: ''; position: absolute; left: 0; right: 0; bottom: -1px; height: 2px; background: var(--accent);
  }
  .tl-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px;
    margin-bottom: 12px;
  }
  .tl-card-head { display: flex; justify-content: space-between; align-items: baseline; gap: 12px; margin-bottom: 10px; }
  .tl-ex-name { font-weight: 500; font-size: 15px; }
  .tl-ex-equip { color: var(--text-muted); font-size: 12px; }
  .tl-volume {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12px;
    color: var(--accent);
    white-space: nowrap;
  }
  .tl-set-row { display: grid; grid-template-columns: 28px 1fr 1fr 28px; gap: 8px; align-items: center; margin-bottom: 6px; }
  .tl-set-num { font-family: 'IBM Plex Mono', monospace; font-size: 12px; color: var(--text-muted); text-align: center; }
  .tl-input {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 14px;
    background: var(--surface-2);
    border: 1px solid var(--border);
    color: var(--text);
    border-radius: 8px;
    padding: 8px 10px;
    width: 100%;
  }
  .tl-input:focus { outline: none; border-color: var(--accent); }
  .tl-input::placeholder { color: var(--text-muted); }
  .tl-del {
    background: none; border: none; color: var(--text-muted); cursor: pointer; font-size: 16px; line-height: 1;
    padding: 4px;
  }
  .tl-del:hover { color: #d9534f; }
  .tl-labels { display: grid; grid-template-columns: 28px 1fr 1fr 28px; gap: 8px; margin-bottom: 6px; }
  .tl-labels span { font-size: 11px; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.3px; }
  .tl-add {
    font-family: 'Inter', sans-serif;
    font-size: 13px;
    font-weight: 500;
    background: var(--accent-dim);
    color: var(--accent);
    border: none;
    border-radius: 8px;
    padding: 8px 12px;
    cursor: pointer;
    margin-top: 4px;
  }
  .tl-add:hover { filter: brightness(1.15); }
  .tl-status {
    font-size: 12px; color: var(--text-muted); text-align: right; margin-top: 4px; min-height: 16px;
  }
  .tl-status.saved { color: var(--ok); }
  .tl-loading { color: var(--text-muted); font-size: 13px; padding: 20px 0; text-align: center; }
  .tl-card-actions { display: flex; gap: 8px; margin-top: 8px; flex-wrap: wrap; }
  .tl-finish {
    font-family: 'Inter', sans-serif; font-size: 13px; font-weight: 500;
    background: none; color: var(--ok); border: 1px solid var(--ok); border-radius: 8px;
    padding: 8px 12px; cursor: pointer;
  }
  .tl-finish:hover { background: rgba(111,174,111,0.12); }
  .tl-history-toggle {
    font-family: 'Inter', sans-serif; font-size: 13px; font-weight: 500;
    background: none; color: var(--text-muted); border: 1px solid var(--border); border-radius: 8px;
    padding: 8px 12px; cursor: pointer;
  }
  .tl-history-toggle:hover { color: var(--text); }
  .tl-history { margin-top: 12px; border-top: 1px solid var(--border); padding-top: 12px; display: none; }
  .tl-history.open { display: block; }
  .tl-history-empty { color: var(--text-muted); font-size: 12px; }
  .tl-hrow { display: grid; grid-template-columns: 78px 1fr 60px; gap: 8px; align-items: center; margin-bottom: 8px; }
  .tl-hdate { font-family: 'IBM Plex Mono', monospace; font-size: 12px; color: var(--text-muted); }
  .tl-hbar-track { background: var(--surface-2); border-radius: 4px; height: 8px; overflow: hidden; }
  .tl-hbar-fill { background: var(--accent); height: 100%; border-radius: 4px; }
  .tl-hval { font-family: 'IBM Plex Mono', monospace; font-size: 12px; text-align: right; color: var(--text); }
  .tl-card-head { justify-content: space-between; }
  .tl-head-main { display: flex; justify-content: space-between; align-items: baseline; flex: 1; gap: 12px; }
  .tl-equip-icon {
    width: 36px; height: 36px; border-radius: 50%; flex-shrink: 0;
    display: flex; align-items: center; justify-content: center;
    background: var(--surface-2); border: 1.5px solid var(--icon-color, var(--border));
    margin-left: 12px;
  }
  .tl-guide-toggle {
    font-family: 'Inter', sans-serif; font-size: 13px; font-weight: 500;
    background: none; color: var(--accent); border: 1px solid var(--accent); border-radius: 8px;
    padding: 8px 12px; cursor: pointer;
  }
  .tl-guide-toggle:hover { background: var(--accent-dim); }
  .tl-guide { margin-top: 12px; border-top: 1px solid var(--border); padding-top: 12px; display: none; }
  .tl-guide.open { display: block; }
  .tl-guide ol { margin: 0; padding-left: 20px; }
  .tl-guide li { font-size: 13px; line-height: 1.6; color: var(--text); margin-bottom: 6px; }
  .tl-guide li::marker { color: var(--accent); font-family: 'IBM Plex Mono', monospace; font-weight: 600; }
</style>

<div id="tl-root">
  <div class="tl-h1">Trainingslog</div>
  <p class="tl-sub">Sätze, Wiederholungen und Gewicht pro Übung eintragen — wird automatisch gespeichert.</p>
  <div class="tl-tabs" id="tl-tabs"></div>
  <div id="tl-content"><div class="tl-loading">Lade...</div></div>
  <div class="tl-status" id="tl-status"></div>
</div>

<script>
window.storage = {
  async get(key, shared) {
    const raw = localStorage.getItem('tl_' + key);
    if (raw === null) throw new Error('key not found');
    return { key: key, value: raw, shared: !!shared };
  },
  async set(key, value, shared) {
    localStorage.setItem('tl_' + key, value);
    return { key: key, value: value, shared: !!shared };
  },
  async delete(key, shared) {
    localStorage.removeItem('tl_' + key);
    return { key: key, deleted: true, shared: !!shared };
  },
  async list(prefix, shared) {
    const p = 'tl_' + (prefix || '');
    const keys = Object.keys(localStorage).filter(k => k.startsWith(p)).map(k => k.slice(3));
    return { keys: keys, prefix: prefix, shared: !!shared };
  }
};
(function() {
  const DAYS = {
    push: {
      label: 'Push',
      exercises: [
        { name: 'Kurzhantel-Bankdrücken', equip: 'Kurzhantel + Bank', pose: 'horizontal_press', steps: [
          'Auf der Bank liegen, Füße fest am Boden, Kurzhanteln über der Brust halten.',
          'Hanteln kontrolliert bis auf Brusthöhe absenken, Ellbogen ca. 45° zum Körper.',
          'Kurz unten pausieren, dann explosiv nach oben drücken bis die Arme fast gestreckt sind.',
          '3-4 Sätze x 6-8 Wiederholungen.'
        ]},
        { name: 'Schrägbankdrücken', equip: 'Kurzhantel + Bank', pose: 'horizontal_press', steps: [
          'Bank auf 30-45° einstellen, Kurzhanteln auf Schulterhöhe starten.',
          'Hanteln langsam absenken bis eine leichte Dehnung in der oberen Brust spürbar ist.',
          'Nach oben drücken, Hanteln am Ende leicht zueinander führen.',
          '3 Sätze x 8-10 Wiederholungen.'
        ]},
        { name: 'Schulterdrücken', equip: 'Kurzhantel', pose: 'overhead_press', steps: [
          'Aufrecht sitzen oder stehen, Kurzhanteln auf Schulterhöhe, Handflächen nach vorne.',
          'Hanteln über den Kopf drücken bis die Arme fast gestreckt sind, Rumpf stabil halten.',
          'Kontrolliert zurück auf Schulterhöhe absenken.',
          '3 Sätze x 8-10 Wiederholungen.'
        ]},
        { name: 'Seitheben', equip: 'Kurzhantel', pose: 'lateral_raise', steps: [
          'Aufrecht stehen, Kurzhanteln seitlich am Körper, leichte Ellbogenbeugung.',
          'Arme seitlich bis Schulterhöhe anheben, keinen Schwung aus dem Rücken nutzen.',
          'Kurz oben halten, dann langsam absenken.',
          '3 Sätze x 12-15 Wiederholungen.'
        ]},
        { name: 'Trizepsdrücken', equip: 'Widerstandsband', pose: 'triceps_overhead', steps: [
          'Widerstandsband über Kopf oder an einer Tür befestigen, Ellbogen nah am Kopf.',
          'Unterarm nach oben strecken, bis der Arm fast gerade ist.',
          'Kontrolliert zurück in die Ausgangsposition führen.',
          '3 Sätze x 10-12 Wiederholungen.'
        ]},
        { name: 'French Press', equip: 'SZ-Stange', pose: 'triceps_overhead', steps: [
          'SZ-Stange mit engem Griff über dem Kopf halten, Oberarme senkrecht.',
          'Stange hinter den Kopf absenken, nur im Ellbogengelenk bewegen.',
          'Zurück nach oben strecken.',
          '2-3 Sätze x 12-15 Wiederholungen.'
        ]},
      ]
    },
    pull: {
      label: 'Pull',
      exercises: [
        { name: 'Kurzhantel-Rudern', equip: 'Kurzhantel', pose: 'bent_row', steps: [
          'Leicht nach vorne gebeugt, Rücken gerade, Kurzhanteln unter den Schultern.',
          'Hanteln zur Hüfte ziehen, Ellbogen nah am Körper führen.',
          'Schulterblätter am Ende zusammenziehen, dann kontrolliert absenken.',
          '3 Sätze x 8-10 Wiederholungen.'
        ]},
        { name: 'Einarmiges Rudern', equip: 'Widerstandsband', pose: 'bent_row', steps: [
          'Band unter dem Fuß fixieren oder an einem Punkt befestigen, leicht vorgebeugt.',
          'Mit einem Arm zur Hüfte ziehen, Ellbogen eng am Körper.',
          'Langsam wieder strecken, dann die Seite wechseln.',
          '3 Sätze x 10-12 Wiederholungen pro Seite.'
        ]},
        { name: 'Kurzhantel-Kreuzheben', equip: 'Kurzhantel', pose: 'hinge_deadlift', steps: [
          'Kurzhanteln vor den Oberschenkeln halten, Füße hüftbreit.',
          'Hüfte nach hinten schieben, Rücken gerade, Hanteln nah am Bein entlang absenken.',
          'Über die Fersen aufrichten, Hüfte am Ende nach vorne strecken.',
          '3-4 Sätze x 6-8 Wiederholungen.'
        ]},
        { name: 'Face Pulls', equip: 'Widerstandsband', pose: 'face_pull', steps: [
          'Band auf Gesichtshöhe befestigen, leicht nach hinten lehnen.',
          'Band zum Gesicht ziehen, Ellbogen hoch und nach außen führen.',
          'Schulterblätter zusammenziehen, dann kontrolliert zurückführen.',
          '3 Sätze x 15 Wiederholungen.'
        ]},
        { name: 'Bizepscurls', equip: 'SZ-Stange', pose: 'curl', steps: [
          'SZ-Stange mit schulterbreitem Griff halten, Ellbogen am Körper fixiert.',
          'Stange nach oben curlen, ohne den Oberkörper zu schwingen.',
          'Kontrolliert wieder absenken bis die Arme fast gestreckt sind.',
          '3 Sätze x 10-12 Wiederholungen.'
        ]},
        { name: 'Hammercurls', equip: 'Kurzhantel', pose: 'curl', steps: [
          'Kurzhanteln seitlich halten, Handflächen zeigen zueinander.',
          'Hanteln curlen, die Handstellung bleibt während der ganzen Bewegung neutral.',
          'Langsam wieder absenken.',
          '2-3 Sätze x 12-15 Wiederholungen.'
        ]},
      ]
    },
    beine: {
      label: 'Beine',
      exercises: [
        { name: 'Goblet Squats', equip: 'Kurzhantel', pose: 'squat', steps: [
          'Kurzhantel senkrecht vor der Brust halten, Füße schulterbreit.',
          'In die Hocke gehen, Knie folgen den Zehen, Rücken bleibt gerade.',
          'Über die Fersen wieder nach oben drücken.',
          '3-4 Sätze x 8-10 Wiederholungen.'
        ]},
        { name: 'Rumänisches Kreuzheben', equip: 'Kurzhantel', pose: 'hinge_deadlift', steps: [
          'Kurzhanteln vor den Oberschenkeln, Knie nur leicht gebeugt.',
          'Hüfte nach hinten schieben, Hanteln eng am Bein entlang absenken bis Dehnung im Hamstring.',
          'Über die Hüfte wieder aufrichten.',
          '3 Sätze x 8-10 Wiederholungen.'
        ]},
        { name: 'Bulgarian Split Squats', equip: 'Kurzhantel + Bank', pose: 'lunge', steps: [
          'Hinteren Fuß erhöht auf der Bank ablegen, das vordere Bein trägt das Gewicht.',
          'Knie beugen bis der Oberschenkel etwa parallel zum Boden ist, Rumpf aufrecht.',
          'Über die vordere Ferse wieder hochdrücken.',
          '2-3 Sätze x 10 Wiederholungen pro Bein.'
        ]},
        { name: 'Band-Beinbeuger', equip: 'Widerstandsband', pose: 'leg_curl', steps: [
          'Band an Knöchel und festem Punkt befestigen, Bauchlage oder stehend.',
          'Ferse Richtung Gesäß ziehen, der Oberschenkel bleibt ruhig.',
          'Kontrolliert zurückführen.',
          '3 Sätze x 10-12 Wiederholungen.'
        ]},
        { name: 'Wadenheben', equip: 'Kurzhantel + Korkblock', pose: 'calf_raise', steps: [
          'Fußballen auf den Korkblock stellen, Fersen ragen frei nach hinten.',
          'Fersen langsam unter Blockhöhe absenken für maximale Dehnung.',
          'Explosiv nach oben drücken, bis auf die Zehenspitzen.',
          '4 Sätze x 12-15 Wiederholungen.'
        ]},
        { name: 'Ausfallschritte', equip: 'Kurzhantel', pose: 'lunge', steps: [
          'Aufrecht stehen, Kurzhanteln seitlich halten.',
          'Großen Schritt nach vorne, beide Knie auf ca. 90° beugen.',
          'Über die vordere Ferse zurück in die Ausgangsposition drücken.',
          '2-3 Sätze x 10 Wiederholungen pro Bein.'
        ]},
      ]
    }
  };

  let currentDay = 'push';
  let dataCache = {}; // dayKey -> array of arrays of {reps, weight}
  const tabsEl = document.getElementById('tl-tabs');
  const contentEl = document.getElementById('tl-content');
  const statusEl = document.getElementById('tl-status');

  Object.keys(DAYS).forEach(key => {
    const btn = document.createElement('button');
    btn.className = 'tl-tab' + (key === currentDay ? ' active' : '');
    btn.textContent = DAYS[key].label;
    btn.dataset.day = key;
    btn.onclick = () => switchDay(key);
    tabsEl.appendChild(btn);
  });

  let historyCache = {}; // dayKey -> array of history arrays per exercise

  function storageKey(day, exIndex) {
    return 'sets:' + day + ':' + exIndex;
  }

  function historyKey(day, exIndex) {
    return 'history:' + day + ':' + exIndex;
  }

  function todayStr() {
    const d = new Date();
    return d.toISOString().slice(0, 10);
  }

  async function loadDay(day) {
    const exercises = DAYS[day].exercises;
    const sets = [];
    const histories = [];
    for (let i = 0; i < exercises.length; i++) {
      try {
        const res = await window.storage.get(storageKey(day, i), false);
        sets.push(res && res.value ? JSON.parse(res.value) : [{ reps: '', weight: '' }]);
      } catch (e) {
        sets.push([{ reps: '', weight: '' }]);
      }
      try {
        const hres = await window.storage.get(historyKey(day, i), false);
        histories.push(hres && hres.value ? JSON.parse(hres.value) : []);
      } catch (e) {
        histories.push([]);
      }
    }
    dataCache[day] = sets;
    historyCache[day] = histories;
  }

  async function saveHistory(day, exIndex) {
    try {
      await window.storage.set(historyKey(day, exIndex), JSON.stringify(historyCache[day][exIndex]), false);
    } catch (e) {
      // silent fail, history is a bonus feature
    }
  }

  async function saveExercise(day, exIndex) {
    statusEl.textContent = 'Speichere...';
    statusEl.classList.remove('saved');
    try {
      const value = JSON.stringify(dataCache[day][exIndex]);
      const result = await window.storage.set(storageKey(day, exIndex), value, false);
      if (result) {
        statusEl.textContent = 'Gespeichert';
        statusEl.classList.add('saved');
      } else {
        statusEl.textContent = 'Speichern fehlgeschlagen';
      }
    } catch (e) {
      statusEl.textContent = 'Speichern fehlgeschlagen';
    }
  }

  function computeVolume(sets) {
    let total = 0;
    sets.forEach(s => {
      const r = parseFloat(s.reps) || 0;
      const w = parseFloat(s.weight) || 0;
      total += r * w;
    });
    return total;
  }

  function equipColor(equip) {
    if (equip.indexOf('Korkblock') !== -1) return '#c9822f';
    if (equip.indexOf('Widerstandsband') !== -1) return '#c96a4a';
    if (equip.indexOf('SZ-Stange') !== -1) return '#3fa88a';
    return '#4a90d9';
  }

  function poseSvg(pose, color) {
    const head = '<circle cx="12" cy="4" r="2"/>';
    const legsStd = '<path d="M12 14L9 21M12 14L15 21"/>';
    let body = '';
    switch (pose) {
      case 'horizontal_press':
        body = `<circle cx="5" cy="14" r="2"/><path d="M7 14H16M16 14L20 12L22 16M10 14V7M14 14V7"/><circle cx="10" cy="6" r="1"/><circle cx="14" cy="6" r="1"/>`;
        return svgWrap(body, color);
      case 'overhead_press':
        body = `${head}<path d="M12 6V14M12 8L7 3M12 8L17 3"/>${legsStd}`;
        return svgWrap(body, color);
      case 'lateral_raise':
        body = `${head}<path d="M12 6V14M12 9H5M12 9H19"/>${legsStd}`;
        return svgWrap(body, color);
      case 'triceps_overhead':
        body = `${head}<path d="M12 6V14M12 8L12 3L15 5M12 8L9 13"/>${legsStd}`;
        return svgWrap(body, color);
      case 'bent_row':
        body = `<circle cx="8" cy="6" r="2"/><path d="M8 8L14 16M11 12L9 17M12 13L16 10M14 16L13 21M14 16L17 20"/>`;
        return svgWrap(body, color);
      case 'hinge_deadlift':
        body = `<circle cx="8" cy="6" r="2"/><path d="M8 8L15 15M11 10L9 17M13 12L11 18M15 15L14 21M15 15L17 21"/>`;
        return svgWrap(body, color);
      case 'face_pull':
        body = `${head}<path d="M12 6V14M6 9L9 7L12 9M18 9L15 7L12 9"/>${legsStd}`;
        return svgWrap(body, color);
      case 'curl':
        body = `${head}<path d="M12 6V14M12 9L15 12L13 8M12 9L9 14"/>${legsStd}`;
        return svgWrap(body, color);
      case 'squat':
        body = `${head}<path d="M12 6V11M12 8L9 9M12 8L15 9M12 11L9 15L9 21M12 11L15 15L15 21"/>`;
        return svgWrap(body, color);
      case 'lunge':
        body = `${head}<path d="M12 6V13M12 8L10 12M12 8L14 12M12 13L10 17L10 21M12 13L16 16L19 19"/>`;
        return svgWrap(body, color);
      case 'calf_raise':
        body = `${head}<path d="M12 6V14M12 8L10 13M12 8L14 13M12 14L11 21M12 14L13 21"/><path d="M9 21H15" stroke-dasharray="1 1.5"/>`;
        return svgWrap(body, color);
      case 'leg_curl':
        body = `<circle cx="5" cy="10" r="2"/><path d="M7 10H15M9 10L7 13M15 10L15 14L18 12"/>`;
        return svgWrap(body, color);
      default:
        body = `${head}<path d="M12 6V14"/>${legsStd}`;
        return svgWrap(body, color);
    }
  }

  function svgWrap(inner, color) {
    return `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="${color}" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">${inner}</svg>`;
  }

  function render(day) {
    contentEl.innerHTML = '';
    const exercises = DAYS[day].exercises;
    exercises.forEach((ex, exIndex) => {
      const sets = dataCache[day][exIndex];
      const card = document.createElement('div');
      card.className = 'tl-card';

      const head = document.createElement('div');
      head.className = 'tl-card-head';
      head.innerHTML = `
        <div class="tl-head-main">
          <div>
            <div class="tl-ex-name">${ex.name}</div>
            <div class="tl-ex-equip">${ex.equip}</div>
          </div>
          <div class="tl-volume" data-vol="${exIndex}">Volumen: ${computeVolume(sets)} kg</div>
        </div>
        <div class="tl-equip-icon" style="--icon-color:${equipColor(ex.equip)}">${poseSvg(ex.pose, equipColor(ex.equip))}</div>
      `;
      card.appendChild(head);

      const labels = document.createElement('div');
      labels.className = 'tl-labels';
      labels.innerHTML = '<span></span><span>Wdh.</span><span>Gewicht (kg)</span><span></span>';
      card.appendChild(labels);

      const rowsWrap = document.createElement('div');
      rowsWrap.dataset.rows = exIndex;

      function renderRows() {
        rowsWrap.innerHTML = '';
        sets.forEach((set, setIndex) => {
          const row = document.createElement('div');
          row.className = 'tl-set-row';

          const num = document.createElement('div');
          num.className = 'tl-set-num';
          num.textContent = setIndex + 1;
          row.appendChild(num);

          const repsInput = document.createElement('input');
          repsInput.className = 'tl-input';
          repsInput.type = 'number';
          repsInput.min = '0';
          repsInput.placeholder = 'z.B. 10';
          repsInput.value = set.reps;
          repsInput.oninput = () => {
            set.reps = repsInput.value;
            head.querySelector('.tl-volume').textContent = 'Volumen: ' + computeVolume(sets) + ' kg';
          };
          repsInput.onblur = () => saveExercise(day, exIndex);
          row.appendChild(repsInput);

          const weightInput = document.createElement('input');
          weightInput.className = 'tl-input';
          weightInput.type = 'number';
          weightInput.min = '0';
          weightInput.step = '0.5';
          weightInput.placeholder = 'z.B. 12.5';
          weightInput.value = set.weight;
          weightInput.oninput = () => {
            set.weight = weightInput.value;
            head.querySelector('.tl-volume').textContent = 'Volumen: ' + computeVolume(sets) + ' kg';
          };
          weightInput.onblur = () => saveExercise(day, exIndex);
          row.appendChild(weightInput);

          const del = document.createElement('button');
          del.className = 'tl-del';
          del.textContent = '\u00d7';
          del.setAttribute('aria-label', 'Satz entfernen');
          del.onclick = () => {
            if (sets.length > 1) {
              sets.splice(setIndex, 1);
              renderRows();
              head.querySelector('.tl-volume').textContent = 'Volumen: ' + computeVolume(sets) + ' kg';
              saveExercise(day, exIndex);
            }
          };
          row.appendChild(del);

          rowsWrap.appendChild(row);
        });
      }
      renderRows();
      card.appendChild(rowsWrap);

      const addBtn = document.createElement('button');
      addBtn.className = 'tl-add';
      addBtn.textContent = '+ Satz hinzufügen';
      addBtn.onclick = () => {
        sets.push({ reps: '', weight: '' });
        renderRows();
        saveExercise(day, exIndex);
      };
      card.appendChild(addBtn);

      const actions = document.createElement('div');
      actions.className = 'tl-card-actions';

      const finishBtn = document.createElement('button');
      finishBtn.className = 'tl-finish';
      finishBtn.textContent = 'Einheit abschließen';
      finishBtn.onclick = async () => {
        const validSets = sets.filter(s => s.reps !== '' && s.weight !== '');
        if (validSets.length === 0) return;
        const volume = computeVolume(validSets);
        const topWeight = Math.max(...validSets.map(s => parseFloat(s.weight) || 0));
        const history = historyCache[day][exIndex];
        const today = todayStr();
        const existingIdx = history.findIndex(h => h.date === today);
        const entry = { date: today, volume, topWeight, setsCount: validSets.length };
        if (existingIdx >= 0) history[existingIdx] = entry; else history.push(entry);
        history.sort((a, b) => a.date.localeCompare(b.date));
        await saveHistory(day, exIndex);
        renderHistory();
        statusEl.textContent = 'Einheit gespeichert';
        statusEl.classList.add('saved');
      };
      actions.appendChild(finishBtn);

      const historyToggle = document.createElement('button');
      historyToggle.className = 'tl-history-toggle';
      historyToggle.textContent = 'Verlauf';
      const historyEl = document.createElement('div');
      historyEl.className = 'tl-history';
      historyToggle.onclick = () => historyEl.classList.toggle('open');
      actions.appendChild(historyToggle);

      const guideToggle = document.createElement('button');
      guideToggle.className = 'tl-guide-toggle';
      guideToggle.textContent = 'Anleitung';
      const guideEl = document.createElement('div');
      guideEl.className = 'tl-guide';
      const stepsList = document.createElement('ol');
      (ex.steps || []).forEach(step => {
        const li = document.createElement('li');
        li.textContent = step;
        stepsList.appendChild(li);
      });
      guideEl.appendChild(stepsList);
      guideToggle.onclick = () => guideEl.classList.toggle('open');
      actions.appendChild(guideToggle);

      card.appendChild(actions);
      card.appendChild(guideEl);

      function renderHistory() {
        const history = historyCache[day][exIndex];
        historyEl.innerHTML = '';
        if (history.length === 0) {
          historyEl.innerHTML = '<div class="tl-history-empty">Noch keine abgeschlossenen Einheiten.</div>';
          return;
        }
        const recent = history.slice(-8).reverse();
        const maxVolume = Math.max(...recent.map(h => h.volume), 1);
        recent.forEach(h => {
          const row = document.createElement('div');
          row.className = 'tl-hrow';
          const pct = Math.round((h.volume / maxVolume) * 100);
          row.innerHTML = `
            <span class="tl-hdate">${h.date}</span>
            <span class="tl-hbar-track"><span class="tl-hbar-fill" style="width:${pct}%"></span></span>
            <span class="tl-hval">${h.topWeight}kg</span>
          `;
          historyEl.appendChild(row);
        });
      }
      renderHistory();
      card.appendChild(historyEl);

      contentEl.appendChild(card);
    });
  }

  async function switchDay(day) {
    currentDay = day;
    document.querySelectorAll('.tl-tab').forEach(t => {
      t.classList.toggle('active', t.dataset.day === day);
    });
    if (!dataCache[day]) {
      contentEl.innerHTML = '<div class="tl-loading">Lade...</div>';
      await loadDay(day);
    }
    render(day);
  }

  switchDay(currentDay);
})();
</script>
</body>
</html>
