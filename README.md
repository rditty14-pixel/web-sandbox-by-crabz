(function () {
  'use strict';

  // Remove existing instances
  const existing = document.getElementById('cr4bz-blooket-cheat');
  if (existing) existing.remove();

  // ==================== STYLES ====================
  const style = document.createElement('style');
  style.textContent = `
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800;900&display=swap');
    * { box-sizing: border-box; }
    #cr4bz-blooket-cheat {
      position: fixed; top: 50%; left: 50%; width: 700px;
      background: rgba(20,20,30,.98); backdrop-filter: blur(20px);
      border: 2px solid rgba(255,100,200,.4); border-radius: 20px;
      padding: 0; z-index: 999999; font-family: 'Inter', sans-serif;
      box-shadow: 0 25px 50px rgba(0,0,0,.5); transform: translate(-50%,-50%);
      transition: opacity .3s, transform .3s; max-height: 90vh;
    }
    #cr4bz-blooket-cheat.hidden { opacity: 0; pointer-events: none; transform: translate(-50%,-50%) scale(.95); }
    .cheat-header {
      background: linear-gradient(135deg,#ff1493,#ff69b4,#8a2be2); color: #fff;
      padding: 24px; border-radius: 18px 18px 0 0; cursor: move; user-select: none;
      display: flex; justify-content: space-between; align-items: center;
      font-size: 20px; font-weight: 900; letter-spacing: 1.5px;
    }
    .cheat-header-title { flex: 1; text-align: center; }
    .cheat-close-hint { font-size: 11px; opacity: .8; font-weight: 600; }
    .cheat-tabs { display: flex; gap: 5px; padding: 15px 24px; border-bottom: 2px solid rgba(255,20,147,.2); overflow-x: auto; }
    .cheat-tab-btn {
      padding: 8px 16px; background: rgba(255,255,255,.08); color: rgba(255,255,255,.6);
      border: 1px solid rgba(255,255,255,.1); border-radius: 8px; cursor: pointer;
      font-weight: 600; font-size: 12px; transition: .3s; text-transform: uppercase; white-space: nowrap;
    }
    .cheat-tab-btn.active { background: linear-gradient(135deg,#ff1493,#ff69b4); color: #fff; border-color: rgba(255,20,147,.5); }
    .cheat-content { padding: 24px; max-height: 450px; overflow-y: auto; }
    .cheat-tab-content { display: none; }
    .cheat-tab-content.active { display: block; }
    .cheat-button {
      width: 100%; padding: 13px 16px; margin-bottom: 10px;
      background: linear-gradient(135deg,#ff1493,#ff69b4); color: #fff;
      border: 1.5px solid rgba(255,20,147,.5); border-radius: 10px; cursor: pointer;
      font-weight: 700; font-size: 12px; font-family: 'Inter', sans-serif;
      transition: .3s; text-transform: uppercase;
    }
    .cheat-button:hover { transform: translateY(-3px); filter: brightness(1.1); }
    .cheat-button.danger { background: linear-gradient(135deg,#e74c3c,#c0392b); border-color: rgba(231,76,60,.5); }
    .cheat-button.success { background: linear-gradient(135deg,#27ae60,#229954); border-color: rgba(39,174,96,.5); }
    .cheat-button.secondary { background: rgba(255,255,255,.1); border-color: rgba(255,255,255,.2); }
    .cheat-button-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
    .cheat-button-row .cheat-button { margin-bottom: 0; }
    .cheat-section { margin-bottom: 20px; padding-bottom: 20px; border-bottom: 1.5px solid rgba(255,20,147,.2); }
    .cheat-section:last-child { border-bottom: none; margin-bottom: 0; padding-bottom: 0; }
    .cheat-section-title {
      font-size: 11px; font-weight: 800; color: #ff69b4; text-transform: uppercase;
      letter-spacing: 1.2px; margin-bottom: 12px; display: flex; align-items: center; gap: 8px;
    }
    .cheat-section-title::before { content: ''; width: 5px; height: 16px; background: linear-gradient(135deg,#ff1493,#ff69b4); border-radius: 3px; }
    .cheat-input-group { display: flex; gap: 10px; margin-bottom: 10px; }
    .cheat-input-group input {
      flex: 1; padding: 11px 13px; border: 1.5px solid rgba(255,20,147,.3); border-radius: 8px;
      font-family: 'Inter', sans-serif; font-size: 12px; font-weight: 600;
      background: rgba(255,255,255,.08); color: #fff;
    }
    .cheat-input-group input:focus { outline: none; border-color: rgba(255,20,147,.6); }
    .cheat-input-group button {
      padding: 11px 16px; background: linear-gradient(135deg,#ff1493,#ff69b4); color: #fff;
      border: none; border-radius: 8px; cursor: pointer; font-weight: 700; font-size: 12px; text-transform: uppercase;
    }
    .cheat-toggle { display: flex; gap: 8px; margin-bottom: 10px; background: rgba(255,255,255,.05); padding: 8px; border-radius: 10px; flex-wrap: wrap; }
    .cheat-toggle button {
      flex: 1; padding: 9px; font-size: 11px; font-weight: 700; border-radius: 6px;
      border: none; background: rgba(255,255,255,.08); color: rgba(255,255,255,.6);
      cursor: pointer; text-transform: uppercase; min-width: 80px;
    }
    .cheat-toggle button.active { background: linear-gradient(135deg,#ff1493,#ff69b4); color: #fff; }
    .cheat-status {
      background: rgba(255,20,147,.08); border: 1.5px solid rgba(255,20,147,.3);
      border-radius: 8px; padding: 10px 12px; font-size: 11px; font-weight: 600; color: #ff69b4; margin-top: 10px;
    }
    .cheat-status.active { background: rgba(39,174,96,.12); border-color: rgba(39,174,96,.4); color: #27ae60; }
  `;
  document.head.appendChild(style);

  // ==================== PANEL ====================
  const panel = document.createElement('div');
  panel.id = 'cr4bz-blooket-cheat';
  panel.innerHTML = `
    <div class="cheat-header">
      <div class="cheat-header-title">💎 CR4BZ BLOOKET 💎</div>
      <div class="cheat-close-hint">Press E</div>
    </div>
    <div class="cheat-tabs">
      <button class="cheat-tab-btn active" data-tab="gameplay">🎮 Gameplay</button>
      <button class="cheat-tab-btn" data-tab="answers">👁️ Answers</button>
      <button class="cheat-tab-btn" data-tab="cosmetics">✨ Cosmetics</button>
      <button class="cheat-tab-btn" data-tab="advanced">⚙️ Advanced</button>
    </div>
    <div class="cheat-content">
      <!-- GAMEPLAY -->
      <div class="cheat-tab-content active" data-tab="gameplay">
        <div class="cheat-section">
          <div class="cheat-section-title">⚡ Auto Answer (React Hook)</div>
          <button class="cheat-button" id="auto-answer-btn">▶ START AUTO-ANSWER</button>
          <button class="cheat-button secondary" id="stop-auto-btn">⏹ STOP AUTO</button>
          <div class="cheat-toggle">
            <button id="delay-slow">3s</button>
            <button class="active" id="delay-normal">1.5s</button>
            <button id="delay-fast">0.5s</button>
            <button id="delay-instant">INSTANT</button>
          </div>
          <div id="auto-status" class="cheat-status">Status: OFF</div>
        </div>
        <div class="cheat-section">
          <div class="cheat-section-title">🎯 Game Hacks</div>
          <button class="cheat-button" id="instant-win">🏆 INSTANT WIN (spams continue)</button>
          <button class="cheat-button" id="no-lose">🛡️ HIDE LOSE SCREENS</button>
        </div>
      </div>

      <!-- ANSWERS -->
      <div class="cheat-tab-content" data-tab="answers">
        <div class="cheat-section">
          <div class="cheat-section-title">👁️ Answer Tools (React Hook)</div>
          <button class="cheat-button" id="highlight-answers">🟨 HIGHLIGHT CORRECT ANSWERS</button>
          <button class="cheat-button secondary" id="clear-highlights">CLEAR HIGHLIGHTS</button>
        </div>
        <div class="cheat-section">
          <div class="cheat-section-title">🔍 Detection</div>
          <button class="cheat-button" id="show-count">COUNT ANSWER BOXES</button>
          <button class="cheat-button" id="show-text">SHOW QUESTION DATA (console)</button>
        </div>
      </div>

      <!-- COSMETICS -->
      <div class="cheat-tab-content" data-tab="cosmetics">
        <div class="cheat-section">
          <div class="cheat-section-title">🟦 Use Any Blook (in-game only)</div>
          <button class="cheat-button success" id="equip-dragon">EQUIP DRAGON</button>
          <button class="cheat-button" id="equip-fire">EQUIP FLAME</button>
          <button class="cheat-button" id="randomize-blook">🎲 RANDOM BLOOK</button>
        </div>
        <div class="cheat-section">
          <div class="cheat-section-title">📝 Custom (console)</div>
          <div class="cheat-status" style="margin-top:0;">
            Type <b>useBlook("Any Blook Name")</b> in console while in a live game.<br>
            Note: permanent blook/token/level unlocks are server-side and impossible.
          </div>
        </div>
      </div>

      <!-- ADVANCED -->
      <div class="cheat-tab-content" data-tab="advanced">
        <div class="cheat-section">
          <div class="cheat-section-title">🎨 Visual Mods</div>
          <button class="cheat-button" id="dark-mode">🌙 DARK MODE</button>
          <button class="cheat-button" id="custom-colors">🎨 RAINBOW PANEL</button>
        </div>
        <div class="cheat-section">
          <div class="cheat-section-title">⚙️ Settings</div>
          <button class="cheat-button secondary" id="refresh-page">REFRESH PAGE</button>
          <button class="cheat-button danger" id="close-panel">CLOSE</button>
        </div>
      </div>
    </div>
  `;
  document.body.appendChild(panel);

  // ==================== HELPERS ====================
  const $ = (id) => document.getElementById(id);
  function on(id, fn) {
    const el = $(id);
    if (el) el.addEventListener('click', fn);
    else console.warn('[CR4BZ] Missing element:', id);
  }
  function setStatus(text, active) {
    const st = $('auto-status');
    st.textContent = 'Status: ' + text;
    st.classList.toggle('active', !!active);
  }

  // ==================== REACT STATE HOOK ====================
  function getStateNode() {
    for (const el of document.querySelectorAll('body *')) {
      const key = Object.keys(el).find(k => k.startsWith('__reactFiber$'));
      if (!key) continue;
      let fiber = el[key];
      while (fiber) {
        const sn = fiber.stateNode;
        if (sn && sn.state && sn.props && (sn.props.client || sn.state.question)) return sn;
        fiber = fiber.return;
      }
    }
    return null;
  }

  function getCurrentQuestion() {
    const sn = getStateNode();
    return sn && sn.state && sn.state.question ? sn.state.question : null;
  }

  // ==================== AUTO ANSWER (WORKING) ====================
  let autoTimer = null;
  let currentDelay = 1500;

  function autoAnswerTick() {
    const q = getCurrentQuestion();
    if (!q) return;
    const boxes = [...document.querySelectorAll('[class*="answerContainer"]')];
    if (boxes.length > 0 && q.correctAnswers) {
      const idx = boxes.findIndex((el, i) => q.correctAnswers.includes(q.answers[i]));
      if (idx !== -1) boxes[idx].click();
    } else {
      const sn = getStateNode();
      if (sn && typeof sn.sendAnswer === 'function' && q.answers && q.answers[0]) {
        sn.sendAnswer(q.answers[0]);
      }
    }
  }

  function startAuto(label) {
    if (autoTimer) return;
    autoTimer = setInterval(autoAnswerTick, currentDelay);
    setStatus(label + ' ✅ (React hook)', true);
  }
  function stopAuto() {
    if (autoTimer) { clearInterval(autoTimer); autoTimer = null; }
    setStatus('OFF ❌', false);
  }
  function setDelay(ms, btn) {
    currentDelay = ms;
    panel.querySelectorAll('.cheat-toggle button').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    if (autoTimer) { clearInterval(autoTimer); autoTimer = setInterval(autoAnswerTick, currentDelay); }
  }

  on('auto-answer-btn', () => startAuto('ON'));
  on('stop-auto-btn', stopAuto);
  on('delay-slow', function () { setDelay(3000, this); });
  on('delay-normal', function () { setDelay(1500, this); });
  on('delay-fast', function () { setDelay(500, this); });
  on('delay-instant', function () { setDelay(50, this); });

  on('instant-win', () => {
    // Spam the continue/next button via the game state
    let clicks = 0;
    const iv = setInterval(() => {
      const btns = [...document.querySelectorAll('button')].filter(b =>
        !panel.contains(b) && /continue|next|ok/i.test(b.textContent));
      if (btns.length > 0) { btns[0].click(); clicks++; }
      if (clicks >= 10) clearInterval(iv);
    }, 300);
  });

  on('no-lose', () => {
    document.querySelectorAll('[class*="lose"], [class*="wrong"], [class*="fail"]').forEach(el => {
      el.style.display = 'none';
    });
  });

  // ==================== HIGHLIGHT ANSWERS (WORKING) ====================
  let highlightTimer = null;

  on('highlight-answers', () => {
    if (highlightTimer) return;
    highlightTimer = setInterval(() => {
      const q = getCurrentQuestion();
      if (!q || !q.correctAnswers) return;
      document.querySelectorAll('[class*="answerContainer"]').forEach((el, i) => {
        if (q.correctAnswers.includes(q.answers[i])) {
          el.style.setProperty('background-color', '#00c853', 'important');
          el.style.setProperty('border', '3px solid #00ff00', 'important');
        }
      });
    }, 100);
    setStatus('Highlighting ✅', true);
  });

  on('clear-highlights', () => {
    if (highlightTimer) { clearInterval(highlightTimer); highlightTimer = null; }
    document.querySelectorAll('[class*="answerContainer"]').forEach(el => {
      el.style.removeProperty('background-color');
      el.style.removeProperty('border');
    });
    setStatus('OFF ❌', false);
  });

  on('show-count', () => {
    const c = document.querySelectorAll('[class*="answerContainer"]').length;
    alert(c > 0 ? `✅ Found ${c} answer boxes (in game).` : '❌ 0 answer boxes — join a game question screen first.');
  });

  on('show-text', () => {
    const q = getCurrentQuestion();
    if (!q) return alert('❌ No question in state — join a game first!');
    console.clear();
    console.log('[CR4BZ] Question:', q.question);
    console.log('[CR4BZ] Answers:', q.answers);
    console.log('%c[CR4BZ] Correct: ' + q.correctAnswers.join(', '), 'color:#27ae60;font-weight:bold');
    alert('✅ Question data logged to console (F12).');
  });

  // ==================== USE ANY BLOOK (WORKING, IN-GAME) ====================
  window.useBlook = function (blookName) {
    const sn = getStateNode();
    if (!sn || !sn.props || !sn.props.liveGameController) {
      return alert('❌ Must be used inside a live game!');
    }
    sn.props.liveGameController.setVal({
      path: 'c/' + sn.props.client.name + '/b',
      val: blookName
    });
    alert('✅ Now showing as: ' + blookName);
  };

  on('equip-dragon', () => window.useBlook('Dragon'));
  on('equip-fire', () => window.useBlook('Flame'));
  on('randomize-blook', () => {
    const blooks = ['Dragon', 'Flame', 'Ghost', 'Demon', 'Cyborg', 'Diver', 'Astronaut', 'Unicorn', 'Tiger', 'Wolf'];
    window.useBlook(blooks[Math.floor(Math.random() * blooks.length)]);
  });

  // ==================== VISUAL / SETTINGS ====================
  let darkModeActive = false;
  on('dark-mode', () => {
    darkModeActive = !darkModeActive;
    document.body.style.filter = darkModeActive ? 'invert(1) hue-rotate(180deg)' : 'none';
  });

  on('custom-colors', () => {
    const cols = ['#FF1493', '#00FF00', '#00FFFF', '#FFFF00', '#FF6600', '#FF0099'];
    panel.querySelectorAll('button').forEach(el => {
      el.style.backgroundColor = cols[Math.floor(Math.random() * cols.length)];
    });
  });

  on('refresh-page', () => location.reload());

  on('close-panel', () => {
    if (autoTimer) clearInterval(autoTimer);
    if (highlightTimer) clearInterval(highlightTimer);
    panel.classList.add('hidden');
    setTimeout(() => {
      panel.remove();
      if (style.parentNode) style.parentNode.removeChild(style);
    }, 300);
  });

  // ==================== DRAG ====================
  let isDragging = false, offX = 0, offY = 0;
  panel.querySelector('.cheat-header').addEventListener('mousedown', (e) => {
    isDragging = true;
    offX = e.clientX - panel.offsetLeft;
    offY = e.clientY - panel.offsetTop;
    e.preventDefault();
  });
  document.addEventListener('mousemove', (e) => {
    if (!isDragging) return;
    panel.style.left = (e.clientX - offX) + 'px';
    panel.style.top = (e.clientY - offY) + 'px';
    panel.style.transform = 'none';
  });
  document.addEventListener('mouseup', () => { isDragging = false; });

  // ==================== KEYBOARD ====================
  document.addEventListener('keydown', (e) => {
    if (e.key !== 'e' && e.key !== 'E') return;
    const t = e.target;
    if (t && (t.tagName === 'INPUT' || t.tagName === 'TEXTAREA' || t.isContentEditable)) return;
    e.preventDefault();
    panel.classList.toggle('hidden');
  });

  console.log('%c💎 CR4BZ BLOOKET CHEAT (ALL-IN-ONE) LOADED 💎', 'color:#FF1493;font-size:18px;font-weight:bold');
  console.log('%c✅ Working: Auto Answer, Highlight Answers, Use Any Blook (in-game)', 'color:#27ae60;font-weight:bold');
  console.log('%c⚠️ Join an actual game and reach a question screen — features need game state.', 'color:#ffc107');
  console.log('%c❌ Impossible (server-side): tokens, level, blook inventory, stats.', 'color:#e74c3c');
})();
