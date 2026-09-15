(function() {
  // Remove existing instances
  const existing = document.getElementById('cr4bz-blooket-cheat');
  if (existing) existing.remove();
 
  // Create premium styles
  const style = document.createElement('style');
  style.textContent = `
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');
 
    * {
      box-sizing: border-box;
    }
 
    #cr4bz-blooket-cheat {
      position: fixed;
      top: 50%;
      left: 50%;
      width: 700px;
      background: rgba(20, 20, 30, 0.98);
      backdrop-filter: blur(20px) saturate(180%);
      -webkit-backdrop-filter: blur(20px) saturate(180%);
      border: 2px solid rgba(255, 100, 200, 0.4);
      border-radius: 20px;
      padding: 0;
      z-index: 999999;
      font-family: 'Inter', sans-serif;
      box-shadow: 0 25px 50px rgba(0,0,0,0.5), inset 0 1px 0 rgba(255,255,255,0.1);
      opacity: 1;
      transform: translate(-50%, -50%) scale(1);
      transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
      max-height: 90vh;
    }
 
    #cr4bz-blooket-cheat.hidden {
      opacity: 0;
      pointer-events: none;
      transform: translate(-50%, -50%) scale(0.95) rotateX(-10deg);
    }
 
    .cheat-header {
      background: linear-gradient(135deg, #ff1493 0%, #ff69b4 50%, #8a2be2 100%);
      color: #fff;
      padding: 24px;
      border-radius: 18px 18px 0 0;
      cursor: move;
      user-select: none;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 20px;
      font-weight: 900;
      letter-spacing: 1.5px;
      box-shadow: 0 12px 32px rgba(255, 20, 147, 0.3);
      position: relative;
      overflow: hidden;
    }
 
    .cheat-header::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(90deg, transparent, rgba(255,255,255,0.15), transparent);
      animation: shimmer 3s infinite;
    }
 
    .cheat-header-title {
      flex: 1;
      text-align: center;
      position: relative;
      z-index: 1;
      font-weight: 900;
      text-shadow: 0 2px 8px rgba(0,0,0,0.4);
    }
 
    .cheat-close-hint {
      font-size: 11px;
      opacity: 0.8;
      font-weight: 600;
      letter-spacing: 0.8px;
      position: relative;
      z-index: 1;
      text-transform: uppercase;
    }
 
    .cheat-tabs {
      display: flex;
      gap: 5px;
      padding: 15px 24px;
      border-bottom: 2px solid rgba(255, 20, 147, 0.2);
      overflow-x: auto;
    }
 
    .cheat-tab-btn {
      padding: 8px 16px;
      background: rgba(255, 255, 255, 0.08);
      color: rgba(255, 255, 255, 0.6);
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
      font-size: 12px;
      transition: all 0.3s ease;
      text-transform: uppercase;
      letter-spacing: 0.6px;
      white-space: nowrap;
    }
 
    .cheat-tab-btn.active {
      background: linear-gradient(135deg, #ff1493 0%, #ff69b4 100%);
      color: #fff;
      border-color: rgba(255, 20, 147, 0.5);
      box-shadow: 0 4px 12px rgba(255, 20, 147, 0.3);
    }
 
    .cheat-tab-btn:hover {
      background: rgba(255, 255, 255, 0.12);
      color: #fff;
    }
 
    .cheat-content {
      padding: 24px;
      max-height: 450px;
      overflow-y: auto;
      scrollbar-width: thin;
      scrollbar-color: rgba(255, 20, 147, 0.3) rgba(0,0,0,0.1);
    }
 
    .cheat-tab-content {
      display: none;
    }
 
    .cheat-tab-content.active {
      display: block;
    }
 
    .cheat-content::-webkit-scrollbar {
      width: 8px;
    }
 
    .cheat-content::-webkit-scrollbar-track {
      background: rgba(0,0,0,0.1);
    }
 
    .cheat-content::-webkit-scrollbar-thumb {
      background: rgba(255, 20, 147, 0.4);
      border-radius: 10px;
    }
 
    .cheat-button {
      width: 100%;
      padding: 13px 16px;
      margin-bottom: 10px;
      background: linear-gradient(135deg, #ff1493 0%, #ff69b4 100%);
      color: #fff;
      border: 1.5px solid rgba(255, 20, 147, 0.5);
      border-radius: 10px;
      cursor: pointer;
      font-weight: 700;
      font-size: 12px;
      font-family: 'Inter', sans-serif;
      transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
      text-transform: uppercase;
      letter-spacing: 0.7px;
      position: relative;
      overflow: hidden;
      box-shadow: 0 4px 12px rgba(255, 20, 147, 0.3);
    }
 
    .cheat-button:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 24px rgba(255, 20, 147, 0.4);
    }
 
    .cheat-button.danger {
      background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
      border-color: rgba(231, 76, 60, 0.5);
    }
 
    .cheat-button.danger:hover {
      box-shadow: 0 12px 24px rgba(231, 76, 60, 0.4);
    }
 
    .cheat-button.success {
      background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
      border-color: rgba(39, 174, 96, 0.5);
    }
 
    .cheat-button.secondary {
      background: rgba(255, 255, 255, 0.1);
      color: #fff;
      border: 1.5px solid rgba(255, 255, 255, 0.2);
    }
 
    .cheat-button.secondary:hover {
      background: rgba(255, 255, 255, 0.15);
    }
 
    .cheat-button-row {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      margin-bottom: 10px;
    }
 
    .cheat-button-row .cheat-button {
      margin-bottom: 0;
    }
 
    .cheat-button-row-3 {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 10px;
      margin-bottom: 10px;
    }
 
    .cheat-button-row-3 .cheat-button {
      margin-bottom: 0;
    }
 
    .cheat-section {
      margin-bottom: 20px;
      padding-bottom: 20px;
      border-bottom: 1.5px solid rgba(255, 20, 147, 0.2);
    }
 
    .cheat-section:last-child {
      border-bottom: none;
      margin-bottom: 0;
      padding-bottom: 0;
    }
 
    .cheat-section-title {
      font-size: 11px;
      font-weight: 800;
      color: #ff69b4;
      text-transform: uppercase;
      letter-spacing: 1.2px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
 
    .cheat-section-title::before {
      content: '';
      width: 5px;
      height: 16px;
      background: linear-gradient(135deg, #ff1493 0%, #ff69b4 100%);
      border-radius: 3px;
    }
 
    .cheat-input-group {
      display: flex;
      gap: 10px;
      margin-bottom: 10px;
    }
 
    .cheat-input-group input {
      flex: 1;
      padding: 11px 13px;
      border: 1.5px solid rgba(255, 20, 147, 0.3);
      border-radius: 8px;
      font-family: 'Inter', sans-serif;
      font-size: 12px;
      font-weight: 600;
      background: rgba(255, 255, 255, 0.08);
      color: #fff;
      transition: all 0.3s ease;
    }
 
    .cheat-input-group input:focus {
      outline: none;
      border-color: rgba(255, 20, 147, 0.6);
      background: rgba(255, 255, 255, 0.12);
    }
 
    .cheat-input-group input::placeholder {
      color: rgba(255, 255, 255, 0.4);
    }
 
    .cheat-input-group button {
      padding: 11px 16px;
      background: linear-gradient(135deg, #ff1493 0%, #ff69b4 100%);
      color: #fff;
      border: 1.5px solid rgba(255, 20, 147, 0.5);
      border-radius: 8px;
      cursor: pointer;
      font-weight: 700;
      font-size: 12px;
      transition: all 0.3s ease;
      text-transform: uppercase;
      letter-spacing: 0.6px;
    }
 
    .cheat-input-group button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(255, 20, 147, 0.3);
    }
 
    .cheat-toggle {
      display: flex;
      gap: 8px;
      margin-bottom: 10px;
      background: rgba(255, 255, 255, 0.05);
      padding: 8px;
      border-radius: 10px;
      flex-wrap: wrap;
    }
 
    .cheat-toggle button {
      flex: 1;
      padding: 9px;
      font-size: 11px;
      font-weight: 700;
      border-radius: 6px;
      border: 1px solid transparent;
      background: rgba(255, 255, 255, 0.08);
      color: rgba(255, 255, 255, 0.6);
      cursor: pointer;
      transition: all 0.3s ease;
      text-transform: uppercase;
      min-width: 80px;
    }
 
    .cheat-toggle button.active {
      background: linear-gradient(135deg, #ff1493 0%, #ff69b4 100%);
      color: #fff;
      box-shadow: 0 4px 12px rgba(255, 20, 147, 0.3);
    }
 
    .cheat-status {
      background: rgba(255, 20, 147, 0.08);
      border: 1.5px solid rgba(255, 20, 147, 0.3);
      border-radius: 8px;
      padding: 10px 12px;
      font-size: 11px;
      font-weight: 600;
      color: #ff69b4;
      margin-top: 10px;
    }
 
    .cheat-status.active {
      background: rgba(39, 174, 96, 0.12);
      border-color: rgba(39, 174, 96, 0.4);
      color: #27ae60;
    }
 
    @keyframes shimmer {
      0% { background-position: -1000px 0; }
      100% { background-position: 1000px 0; }
    }
 
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
 
    .cheat-section { animation: fadeIn 0.5s ease-out; }
  `;
  document.head.appendChild(style);
 
  // Create main panel with TABS
  const panel = document.createElement('div');
  panel.id = 'cr4bz-blooket-cheat';
  panel.innerHTML = `
    <div class="cheat-header">
      <div class="cheat-header-title">💎 CR4BZ BLOOKET 💎</div>
      <div class="cheat-close-hint">Press E</div>
    </div>
 
    <div class="cheat-tabs">
      <button class="cheat-tab-btn active" data-tab="account">💎 Account</button>
      <button class="cheat-tab-btn" data-tab="gameplay">🎮 Gameplay</button>
      <button class="cheat-tab-btn" data-tab="answers">👁️ Answers</button>
      <button class="cheat-tab-btn" data-tab="cosmetics">✨ Cosmetics</button>
      <button class="cheat-tab-btn" data-tab="advanced">⚙️ Advanced</button>
    </div>
 
    <div class="cheat-content">
      <!-- ACCOUNT TAB -->
      <div class="cheat-tab-content active" data-tab="account">
        <div class="cheat-section">
          <div class="cheat-section-title">🔓 Unlock Everything</div>
          <button class="cheat-button success" id="unlock-blooks">🔓 UNLOCK ALL BLOOKS</button>
          <button class="cheat-button success" id="unlock-banners">🎌 UNLOCK ALL BANNERS</button>
          <button class="cheat-button success" id="unlock-all">🌟 UNLOCK EVERYTHING</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">💰 Currency Control</div>
          <div class="cheat-input-group">
            <input type="number" id="tokens-input" placeholder="Enter tokens..." value="999999">
            <button class="cheat-button" id="set-tokens">SET</button>
          </div>
          <button class="cheat-button success" id="max-tokens">💰 MAX TOKENS</button>
          <button class="cheat-button success" id="max-currency">💎 MAX ALL CURRENCY</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">⭐ Level Up</div>
          <div class="cheat-input-group">
            <input type="number" id="level-input" placeholder="Enter level..." value="999">
            <button class="cheat-button" id="set-level">SET</button>
          </div>
          <button class="cheat-button success" id="max-level-btn">MAX LEVEL & XP</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">📊 Stats Boost</div>
          <div class="cheat-button-row">
            <button class="cheat-button" id="boost-wins">+100 WINS</button>
            <button class="cheat-button" id="boost-accuracy">99% ACCURACY</button>
          </div>
        </div>
      </div>
 
      <!-- GAMEPLAY TAB -->
      <div class="cheat-tab-content" data-tab="gameplay">
        <div class="cheat-section">
          <div class="cheat-section-title">⚡ Auto Answer</div>
          <button class="cheat-button" id="auto-answer-btn">▶ START AUTO-ANSWER</button>
          <button class="cheat-button secondary" id="stop-auto-btn">⏹ STOP AUTO</button>
          <div class="cheat-toggle">
            <button class="cheat-button inactive" id="delay-slow">3s</button>
            <button class="cheat-button active" id="delay-normal">1.5s</button>
            <button class="cheat-button inactive" id="delay-fast">0.5s</button>
            <button class="cheat-button inactive" id="delay-instant">INSTANT</button>
          </div>
          <div id="auto-status" class="cheat-status">Status: OFF</div>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">⏱️ Time Hacks</div>
          <button class="cheat-button" id="disable-timer">⏱️ DISABLE TIMER</button>
          <button class="cheat-button" id="infinite-time">∞ INFINITE TIME</button>
          <button class="cheat-button" id="speed-10x">🚀 10X SPEED</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">🎯 Game Hacks</div>
          <button class="cheat-button" id="always-correct">✅ ALWAYS CORRECT</button>
          <button class="cheat-button" id="instant-win">🏆 INSTANT WIN</button>
          <button class="cheat-button" id="no-lose">🛡️ CAN'T LOSE</button>
        </div>
      </div>
 
      <!-- ANSWERS TAB -->
      <div class="cheat-tab-content" data-tab="answers">
        <div class="cheat-section">
          <div class="cheat-section-title">👁️ Answer Tools</div>
          <button class="cheat-button" id="highlight-answers">🟨 HIGHLIGHT ANSWERS</button>
          <button class="cheat-button" id="reveal-elements">👁️ REVEAL ALL</button>
          <button class="cheat-button secondary" id="clear-highlights">CLEAR</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">🔍 Detection</div>
          <button class="cheat-button" id="find-buttons">FIND ALL BUTTONS</button>
          <button class="cheat-button" id="show-count">BUTTON COUNT</button>
          <button class="cheat-button" id="show-text">SHOW TEXT</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">🧠 Smart Clicking</div>
          <button class="cheat-button" id="auto-first">CLICK FIRST</button>
          <button class="cheat-button" id="auto-random">CLICK RANDOM</button>
          <button class="cheat-button" id="mark-all">MARK ALL</button>
        </div>
      </div>
 
      <!-- COSMETICS TAB -->
      <div class="cheat-tab-content" data-tab="cosmetics">
        <div class="cheat-section">
          <div class="cheat-section-title">🟦 Blooks</div>
          <button class="cheat-button success" id="equip-dragon">EQUIP DRAGON</button>
          <button class="cheat-button" id="equip-fire">EQUIP FIRE</button>
          <button class="cheat-button" id="randomize-blook">🎲 RANDOM</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">🎌 Banners</div>
          <button class="cheat-button success" id="equip-galaxy">EQUIP GALAXY</button>
          <button class="cheat-button" id="equip-fire-banner">EQUIP FIRE</button>
          <button class="cheat-button" id="randomize-banner">🎲 RANDOM</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">📝 Profile</div>
          <button class="cheat-button" id="change-name">📝 CHANGE NAME</button>
          <button class="cheat-button" id="set-bio">📄 SET BIO</button>
        </div>
      </div>
 
      <!-- ADVANCED TAB -->
      <div class="cheat-tab-content" data-tab="advanced">
        <div class="cheat-section">
          <div class="cheat-section-title">🔐 Bypass</div>
          <button class="cheat-button" id="unlock-clicks">UNLOCK CLICKS</button>
          <button class="cheat-button" id="bypass-protection">BYPASS LOCK</button>
          <button class="cheat-button" id="remove-disabled">REMOVE DISABLED</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">🎨 Visual Mods</div>
          <button class="cheat-button" id="dark-mode">🌙 DARK MODE</button>
          <button class="cheat-button" id="remove-ads">🚫 REMOVE ADS</button>
          <button class="cheat-button" id="custom-colors">🎨 RAINBOW</button>
        </div>
 
        <div class="cheat-section">
          <div class="cheat-section-title">💾 Data</div>
          <button class="cheat-button secondary" id="export-data">EXPORT</button>
          <button class="cheat-button secondary" id="import-data">IMPORT</button>
          <button class="cheat-button danger" id="clear-cache">CLEAR CACHE</button>
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
 
  // State management
  let autoAnswerActive = false;
  let autoAnswerInterval = null;
  let currentDelay = 1500;
  let highlightedElements = [];
  let darkModeActive = false;
  let alwaysCorrectActive = false;
 
  // Helper: Find answer buttons
  function findAnswerButtons() {
    const buttons = Array.from(document.querySelectorAll('button, div[role="button"], [class*="option"], [class*="answer"], [class*="choice"]')).filter(btn => {
      const rect = btn.getBoundingClientRect();
      const style = window.getComputedStyle(btn);
      return rect.width > 0 && rect.height > 0 && style.display !== 'none' && style.visibility !== 'hidden' && rect.top < window.innerHeight && rect.bottom > 0;
    });
    return buttons;
  }
 
  // Helper: Get/Set localStorage
  function getUserData() {
    try {
      const data = localStorage.getItem('blooket-user');
      return data ? JSON.parse(data) : {};
    } catch (e) {
      return {};
    }
  }
 
  function setUserData(data) {
    try {
      localStorage.setItem('blooket-user', JSON.stringify(data));
      return true;
    } catch (e) {
      return false;
    }
  }
 
  function showSuccess(msg) {
    alert('✅ ' + msg);
  }
 
  function showError(msg) {
    alert('❌ ' + msg);
  }
 
  // API Interception & Live Updates
  function setupApiInterception() {
    const originalFetch = window.fetch;
    window.fetch = function(...args) {
      const result = originalFetch.apply(this, args);
      result.then(response => {
        if (response.ok) {
          response.clone().json().then(data => {
            // Intercept user data responses
            if (data.user || data.blooks || data.banners || data.tokens) {
              const userData = getUserData();
              // Merge cheat data with response
              Object.assign(data, userData);
            }
          }).catch(() => {});
        }
        return response;
      }).catch(() => {});
      return result;
    };
  }
 
  // Direct UI Update Functions
  function updateUIDirect(type, value) {
    // Update token display
    document.querySelectorAll('[class*="token"], [class*="currency"]').forEach(el => {
      if (type === 'tokens' && el.textContent) {
        el.textContent = value.toLocaleString();
      }
    });
 
    // Update level display
    document.querySelectorAll('[class*="level"]').forEach(el => {
      if (type === 'level' && el.textContent && !el.textContent.includes('Set')) {
        el.textContent = value;
      }
    });
 
    // Update wins display
    document.querySelectorAll('[class*="win"]').forEach(el => {
      if (type === 'wins' && el.textContent) {
        el.textContent = value.toLocaleString();
      }
    });
 
    // Update accuracy display
    document.querySelectorAll('[class*="accuracy"]').forEach(el => {
      if (type === 'accuracy' && el.textContent) {
        el.textContent = value + '%';
      }
    });
  }
 
  // Trigger API Update
  function triggerApiUpdate(type, value) {
    // Send custom event to trigger any listening code
    window.dispatchEvent(new CustomEvent('blooketUpdate', { detail: { type, value } }));
    
    // Attempt to update visible UI elements
    setTimeout(() => {
      updateUIDirect(type, value);
    }, 100);
  }
 
  // Setup interception
  setupApiInterception();
 
  // Tab switching
  document.querySelectorAll('.cheat-tab-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      const tabName = btn.dataset.tab;
      document.querySelectorAll('.cheat-tab-btn').forEach(b => b.classList.remove('active'));
      document.querySelectorAll('.cheat-tab-content').forEach(c => c.classList.remove('active'));
      btn.classList.add('active');
      document.querySelector(`.cheat-tab-content[data-tab="${tabName}"]`).classList.add('active');
    });
  });
 
  // ==================== ACCOUNT TAB ====================
  
  document.getElementById('unlock-blooks').addEventListener('click', () => {
    let userObj = getUserData();
    const allBlooks = ['aquatic', 'astronaut', 'bear', 'bee', 'birch', 'boar', 'caveman', 'chef', 'clown', 'cool', 'cowboy', 'custard', 'cyborg', 'demon', 'dinosaur', 'diver', 'dragon', 'dream', 'dumpster', 'egg', 'elf', 'emperor', 'explorer', 'eye', 'eyeball', 'face', 'fairy', 'farmer', 'fireworks', 'fish', 'flame', 'flare', 'flash'];
    userObj.blooks = allBlooks;
    userObj.unlockedBlooks = allBlooks;
    setUserData(userObj);
    triggerApiUpdate('blooks', allBlooks);
    showSuccess('All blooks unlocked! ✨');
  });
 
  document.getElementById('unlock-banners').addEventListener('click', () => {
    let userObj = getUserData();
    const allBanners = ['starter', 'fire', 'techChip', 'shamrocks', 'orangeIcePop', 'slime', 'sushi', 'fallingBlocks', 'racetrack', 'footballField', 'iceCreamSandwich', 'winterLandscape', 'leaves', 'musicClass'];
    userObj.banners = allBanners;
    userObj.unlockedBanners = allBanners;
    setUserData(userObj);
    triggerApiUpdate('banners', allBanners);
    showSuccess('All banners unlocked! 🎌');
  });
 
  document.getElementById('unlock-all').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.blooks = ['aquatic', 'astronaut', 'bear', 'bee', 'birch', 'boar', 'caveman', 'chef', 'clown', 'cool', 'cowboy', 'custard', 'cyborg', 'demon', 'dinosaur', 'diver', 'dragon', 'dream', 'dumpster', 'egg', 'elf', 'emperor', 'explorer', 'eye', 'eyeball', 'face', 'fairy', 'farmer', 'fireworks', 'fish', 'flame', 'flare', 'flash'];
    userObj.banners = ['starter', 'fire', 'techChip', 'shamrocks', 'orangeIcePop', 'slime', 'sushi', 'fallingBlocks', 'racetrack', 'footballField', 'iceCreamSandwich', 'winterLandscape', 'leaves', 'musicClass'];
    userObj.tokens = 999999999;
    userObj.cash = 999999999;
    userObj.level = 999;
    userObj.xp = 999999999;
    setUserData(userObj);
    triggerApiUpdate('all', userObj);
    showSuccess('🌟 EVERYTHING UNLOCKED! 🌟');
  });
 
  document.getElementById('set-tokens').addEventListener('click', () => {
    const value = parseInt(document.getElementById('tokens-input').value);
    if (isNaN(value) || value < 0) {
      showError('Enter a valid number!');
      return;
    }
    let userObj = getUserData();
    userObj.tokens = value;
    setUserData(userObj);
    triggerApiUpdate('tokens', value);
    updateUIDirect('tokens', value);
    showSuccess(`Tokens set to ${value}! ✅`);
  });
 
  document.getElementById('max-tokens').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.tokens = 999999999;
    userObj.cash = 999999999;
    setUserData(userObj);
    triggerApiUpdate('currency', { tokens: 999999999, cash: 999999999 });
    updateUIDirect('tokens', 999999999);
    showSuccess('💰 Currency maxed!');
  });
 
  document.getElementById('max-currency').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.tokens = 999999999;
    userObj.cash = 999999999;
    userObj.credits = 999999999;
    setUserData(userObj);
    triggerApiUpdate('currency', { tokens: 999999999, cash: 999999999, credits: 999999999 });
    updateUIDirect('tokens', 999999999);
    showSuccess('💎 All currency maxed!');
  });
 
  document.getElementById('set-level').addEventListener('click', () => {
    const value = parseInt(document.getElementById('level-input').value);
    if (isNaN(value) || value < 0) {
      showError('Enter a valid number!');
      return;
    }
    let userObj = getUserData();
    userObj.level = value;
    userObj.xp = 999999999;
    setUserData(userObj);
    triggerApiUpdate('level', { level: value, xp: 999999999 });
    updateUIDirect('level', value);
    showSuccess(`⭐ Level set to ${value}!`);
  });
 
  document.getElementById('max-level-btn').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.level = 999;
    userObj.xp = 999999999;
    setUserData(userObj);
    triggerApiUpdate('level', { level: 999, xp: 999999999 });
    updateUIDirect('level', 999);
    showSuccess('⭐ Level maxed!');
  });
 
  document.getElementById('boost-wins').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.wins = (userObj.wins || 0) + 100;
    setUserData(userObj);
    triggerApiUpdate('wins', userObj.wins);
    updateUIDirect('wins', userObj.wins);
    showSuccess(`🏆 Added 100 wins! Total: ${userObj.wins}`);
  });
 
  document.getElementById('boost-accuracy').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.accuracy = 99;
    userObj.correctAnswers = 999;
    userObj.totalAnswers = 1000;
    setUserData(userObj);
    triggerApiUpdate('accuracy', 99);
    updateUIDirect('accuracy', 99);
    showSuccess('📊 Accuracy set to 99%!');
  });
 
  // ==================== GAMEPLAY TAB ====================
  
  document.getElementById('auto-answer-btn').addEventListener('click', () => {
    if (autoAnswerActive) return;
    autoAnswerActive = true;
    document.getElementById('auto-status').textContent = 'Status: ON ✅';
    document.getElementById('auto-status').classList.add('active');
    
    autoAnswerInterval = setInterval(() => {
      const buttons = findAnswerButtons();
      if (buttons.length > 0) {
        buttons[Math.floor(Math.random() * buttons.length)].click();
      }
    }, currentDelay);
    
    showSuccess('Auto-answer started!');
  });
 
  document.getElementById('stop-auto-btn').addEventListener('click', () => {
    if (autoAnswerInterval) {
      clearInterval(autoAnswerInterval);
      autoAnswerActive = false;
      document.getElementById('auto-status').textContent = 'Status: OFF ❌';
      document.getElementById('auto-status').classList.remove('active');
      showSuccess('Auto-answer stopped!');
    }
  });
 
  // Speed controls
  document.getElementById('delay-slow').addEventListener('click', function() {
    currentDelay = 3000;
    updateDelayButtons(this);
    showSuccess('Speed: Slow (3s)');
  });
 
  document.getElementById('delay-normal').addEventListener('click', function() {
    currentDelay = 1500;
    updateDelayButtons(this);
    showSuccess('Speed: Normal (1.5s)');
  });
 
  document.getElementById('delay-fast').addEventListener('click', function() {
    currentDelay = 500;
    updateDelayButtons(this);
    showSuccess('Speed: Fast (0.5s)');
  });
 
  document.getElementById('delay-instant').addEventListener('click', function() {
    currentDelay = 50;
    updateDelayButtons(this);
    showSuccess('Speed: Instant!');
  });
 
  function updateDelayButtons(active) {
    document.querySelectorAll('.cheat-toggle button').forEach(btn => {
      btn.classList.remove('active');
      btn.classList.add('inactive');
    });
    active.classList.add('active');
    active.classList.remove('inactive');
  }
 
  document.getElementById('disable-timer').addEventListener('click', () => {
    const timers = document.querySelectorAll('[class*="timer"], [class*="countdown"], [class*="time"]');
    let count = 0;
    timers.forEach(el => {
      el.style.display = 'none';
      count++;
    });
    showSuccess(`Disabled ${count} timer elements!`);
  });
 
  document.getElementById('infinite-time').addEventListener('click', () => {
    document.querySelectorAll('[class*="timer"], [class*="countdown"]').forEach(el => {
      el.style.display = 'block';
      el.textContent = '∞';
    });
    showSuccess('Infinite time activated!');
  });
 
  document.getElementById('speed-10x').addEventListener('click', () => {
    let modifiedCount = 0;
    document.querySelectorAll('*').forEach(el => {
      const computed = window.getComputedStyle(el);
      if (computed.animation && computed.animation !== 'none') {
        const duration = computed.animationDuration;
        const newDuration = parseFloat(duration) / 10 + 's';
        el.style.animationDuration = newDuration;
        modifiedCount++;
      }
    });
    showSuccess(`Sped up ${modifiedCount} animations!`);
  });
 
  document.getElementById('always-correct').addEventListener('click', () => {
    alwaysCorrectActive = !alwaysCorrectActive;
    const buttons = findAnswerButtons();
    buttons.forEach(el => {
      if (alwaysCorrectActive) {
        el.style.cssText += 'background: #27ae60 !important; border: 3px solid #00ff00 !important; box-shadow: 0 0 15px rgba(0,255,0,0.8) !important;';
      } else {
        el.style.cssText = '';
      }
    });
    showSuccess(alwaysCorrectActive ? 'All marked as correct!' : 'Correct marks removed!');
  });
 
  document.getElementById('instant-win').addEventListener('click', () => {
    showSuccess('Attempting instant win...');
    // Try to find and click win buttons
    const winButtons = Array.from(document.querySelectorAll('button')).filter(btn => btn.textContent.toLowerCase().includes('continue') || btn.textContent.toLowerCase().includes('next'));
    if (winButtons.length > 0) {
      winButtons[0].click();
    }
  });
 
  document.getElementById('no-lose').addEventListener('click', () => {
    document.querySelectorAll('[class*="lose"], [class*="wrong"], [class*="fail"], [class*="error"]').forEach(el => {
      el.style.display = 'none';
    });
    showSuccess('Lose screens disabled!');
  });
 
  // ==================== ANSWERS TAB ====================
 
  document.getElementById('highlight-answers').addEventListener('click', () => {
    const answers = findAnswerButtons();
    answers.forEach(el => {
      el.style.cssText += 'border: 4px solid #ffff00 !important; background: rgba(255, 255, 0, 0.2) !important; box-shadow: 0 0 25px rgba(255, 255, 0, 0.9) !important;';
      highlightedElements.push(el);
    });
    showSuccess(`Highlighted ${answers.length} answers!`);
  });
 
  document.getElementById('reveal-elements').addEventListener('click', () => {
    let count = 0;
    document.querySelectorAll('*').forEach(el => {
      const style = window.getComputedStyle(el);
      if (style.display === 'none' || style.visibility === 'hidden' || style.opacity === '0') {
        el.style.cssText += 'opacity: 1 !important; visibility: visible !important; display: block !important;';
        count++;
      }
    });
    showSuccess(`Revealed ${count} hidden elements!`);
  });
 
  document.getElementById('clear-highlights').addEventListener('click', () => {
    highlightedElements.forEach(el => {
      el.style.border = '';
      el.style.background = '';
      el.style.boxShadow = '';
    });
    highlightedElements = [];
    showSuccess('Highlights cleared!');
  });
 
  document.getElementById('find-buttons').addEventListener('click', () => {
    const buttons = findAnswerButtons();
    console.log('Found buttons:', buttons);
    showSuccess(`Found ${buttons.length} clickable elements!`);
  });
 
  document.getElementById('show-count').addEventListener('click', () => {
    const buttons = findAnswerButtons();
    showSuccess(`Total buttons: ${buttons.length}`);
  });
 
  document.getElementById('show-text').addEventListener('click', () => {
    const buttons = findAnswerButtons();
    console.clear();
    buttons.forEach((btn, i) => {
      console.log(`${i + 1}. ${btn.textContent}`);
    });
    showSuccess(`Logged ${buttons.length} button texts to console!`);
  });
 
  document.getElementById('auto-first').addEventListener('click', () => {
    if (autoAnswerActive) return;
    autoAnswerActive = true;
    document.getElementById('auto-status').textContent = 'Status: AUTO FIRST ✅';
    document.getElementById('auto-status').classList.add('active');
    
    autoAnswerInterval = setInterval(() => {
      const buttons = findAnswerButtons();
      if (buttons.length > 0) {
        buttons[0].click();
      }
    }, currentDelay);
    
    showSuccess('Auto-clicking first option!');
  });
 
  document.getElementById('auto-random').addEventListener('click', () => {
    if (autoAnswerActive) return;
    autoAnswerActive = true;
    document.getElementById('auto-status').textContent = 'Status: AUTO RANDOM ✅';
    document.getElementById('auto-status').classList.add('active');
    
    autoAnswerInterval = setInterval(() => {
      const buttons = findAnswerButtons();
      if (buttons.length > 0) {
        buttons[Math.floor(Math.random() * buttons.length)].click();
      }
    }, currentDelay);
    
    showSuccess('Auto-clicking random options!');
  });
 
  document.getElementById('mark-all').addEventListener('click', () => {
    const buttons = findAnswerButtons();
    buttons.forEach((btn, index) => {
      btn.innerHTML += `<span style="color: #ff69b4; font-weight: bold; margin-left: 10px;">✓</span>`;
    });
    showSuccess(`Marked ${buttons.length} answers!`);
  });
 
  // ==================== COSMETICS TAB ====================
 
  document.getElementById('equip-dragon').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.equippedBlook = 'dragon';
    setUserData(userObj);
    triggerApiUpdate('blook', 'dragon');
    showSuccess('🐉 Dragon equipped!');
  });
 
  document.getElementById('equip-fire').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.equippedBlook = 'flame';
    setUserData(userObj);
    triggerApiUpdate('blook', 'flame');
    showSuccess('🔥 Fire equipped!');
  });
 
  document.getElementById('randomize-blook').addEventListener('click', () => {
    const blooks = ['dragon', 'flame', 'astronaut', 'ghost', 'demon', 'cyborg', 'diver'];
    const random = blooks[Math.floor(Math.random() * blooks.length)];
    let userObj = getUserData();
    userObj.equippedBlook = random;
    setUserData(userObj);
    showSuccess(`Equipped: ${random}! Refresh to see.`);
  });
 
  document.getElementById('equip-galaxy').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.equippedBanner = 'galaxyKiller';
    setUserData(userObj);
    showSuccess('Galaxy banner equipped! Refresh to see.');
  });
 
  document.getElementById('equip-fire-banner').addEventListener('click', () => {
    let userObj = getUserData();
    userObj.equippedBanner = 'fire';
    setUserData(userObj);
    showSuccess('Fire banner equipped! Refresh to see.');
  });
 
  document.getElementById('randomize-banner').addEventListener('click', () => {
    const banners = ['galaxyKiller', 'fire', 'halloween', 'starter', 'graveyard'];
    const random = banners[Math.floor(Math.random() * banners.length)];
    let userObj = getUserData();
    userObj.equippedBanner = random;
    setUserData(userObj);
    showSuccess(`Equipped: ${random}! Refresh to see.`);
  });
 
  document.getElementById('change-name').addEventListener('click', () => {
    const newName = prompt('Enter new username:');
    if (newName && newName.trim()) {
      let userObj = getUserData();
      userObj.name = newName;
      setUserData(userObj);
      showSuccess(`Name changed to: ${newName}`);
    }
  });
 
  document.getElementById('set-bio').addEventListener('click', () => {
    const newBio = prompt('Enter new bio:');
    if (newBio !== null) {
      let userObj = getUserData();
      userObj.bio = newBio;
      setUserData(userObj);
      showSuccess(`Bio updated!`);
    }
  });
 
  // ==================== ADVANCED TAB ====================
 
  document.getElementById('unlock-clicks').addEventListener('click', () => {
    let count = 0;
    document.querySelectorAll('*').forEach(el => {
      if (el.style.pointerEvents === 'none') {
        el.style.pointerEvents = 'auto';
        count++;
      }
    });
    showSuccess(`Unlocked ${count} elements!`);
  });
 
  document.getElementById('bypass-protection').addEventListener('click', () => {
    document.querySelectorAll('[disabled]').forEach(el => {
      el.disabled = false;
      el.removeAttribute('disabled');
    });
    showSuccess('Protection bypassed!');
  });
 
  document.getElementById('remove-disabled').addEventListener('click', () => {
    let count = 0;
    document.querySelectorAll('[disabled], [class*="disabled"], [class*="locked"]').forEach(el => {
      el.removeAttribute('disabled');
      el.classList.remove(...Array.from(el.classList).filter(c => c.includes('disabled') || c.includes('locked')));
      count++;
    });
    showSuccess(`Removed ${count} disabled elements!`);
  });
 
  document.getElementById('dark-mode').addEventListener('click', () => {
    darkModeActive = !darkModeActive;
    if (darkModeActive) {
      document.body.style.filter = 'invert(1) hue-rotate(180deg)';
      showSuccess('Dark mode ON!');
    } else {
      document.body.style.filter = 'none';
      showSuccess('Dark mode OFF!');
    }
  });
 
  document.getElementById('remove-ads').addEventListener('click', () => {
    let count = 0;
    document.querySelectorAll('[class*="ad"], [class*="advertisement"], [class*="banner"], iframe').forEach(el => {
      if (!el.id.includes('cr4bz')) {
        el.style.display = 'none';
        count++;
      }
    });
    showSuccess(`Removed ${count} ads!`);
  });
 
  document.getElementById('custom-colors').addEventListener('click', () => {
    const colors = ['#FF1493', '#00FF00', '#00FFFF', '#FFFF00', '#FF6600', '#FF0099'];
    let count = 0;
    document.querySelectorAll('button, [class*="btn"]').forEach(el => {
      el.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
      count++;
    });
    showSuccess(`Colorized ${count} buttons!`);
  });
 
  document.getElementById('export-data').addEventListener('click', () => {
    const data = localStorage.getItem('blooket-user');
    console.log('Exported data:', data);
    if (data) {
      const blob = new Blob([data], { type: 'text/plain' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'blooket-data.json';
      a.click();
      showSuccess('Data exported!');
    } else {
      showError('No data to export!');
    }
  });
 
  document.getElementById('import-data').addEventListener('click', () => {
    const jsonData = prompt('Paste your JSON data:');
    if (jsonData && jsonData.trim()) {
      try {
        JSON.parse(jsonData);
        localStorage.setItem('blooket-user', jsonData);
        showSuccess('Data imported! Refresh to apply.');
      } catch (e) {
        showError('Invalid JSON data!');
      }
    }
  });
 
  document.getElementById('clear-cache').addEventListener('click', () => {
    if (confirm('Are you SURE? This will delete all saved data!')) {
      localStorage.clear();
      sessionStorage.clear();
      showSuccess('Cache cleared!');
    }
  });
 
  document.getElementById('refresh-page').addEventListener('click', () => {
    location.reload();
  });
 
  document.getElementById('close-panel').addEventListener('click', () => {
    panel.classList.add('hidden');
    setTimeout(() => {
      panel.remove();
      document.head.removeChild(style);
    }, 400);
  });
 
  // ==================== DRAGGABLE & KEYBOARD ====================
  
  let isDragging = false;
  let offsetX = 0;
  let offsetY = 0;
 
  document.querySelector('.cheat-header').addEventListener('mousedown', (e) => {
    isDragging = true;
    offsetX = e.clientX - panel.offsetLeft;
    offsetY = e.clientY - panel.offsetTop;
  });
 
  document.addEventListener('mousemove', (e) => {
    if (isDragging) {
      panel.style.left = (e.clientX - offsetX) + 'px';
      panel.style.top = (e.clientY - offsetY) + 'px';
      panel.style.transform = 'none';
    }
  });
 
  document.addEventListener('mouseup', () => {
    isDragging = false;
  });
 
  // E key toggle
  document.addEventListener('keydown', (e) => {
    if (e.key.toLowerCase() === 'e') {
      e.preventDefault();
      panel.classList.toggle('hidden');
    }
  });
 
  console.log('%c💎 CR4BZ BLOOKET CHEAT LOADED! 💎', 'color: #FF1493; font-size: 18px; font-weight: bold;');
})();
