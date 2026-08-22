<style>
  @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap');

  html, body {
    overflow: hidden;
    height: 100%;
  }
  .md-header, .md-tabs, .md-sidebar {
    display: none !important;
  }
  .md-main {
    margin-top: 0 !important;
    flex: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }
  .md-main::before {
    content: '';
    position: absolute;
    top: -5px; left: -5px; right: -5px; bottom: -5px;
    background: url('assets/images/background.jpg') center/cover no-repeat;
    filter: blur(3px);
    z-index: 0;
  }
  .md-main::after {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0, 0, 0, 0.2);
    z-index: 0;
  }
  .md-main__inner {
    max-width: none !important;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding-top: 7vh;
    box-sizing: border-box;
  }
  .md-content {
    position: relative;
    z-index: 1;
    text-align: center;
    flex: none !important;
    max-width: none !important;
  }
  .md-content__inner {
    margin: 0 !important;
    padding: 0 !important;
  }
  .md-content h1 {
    color: #ffffff !important;
    font-weight: 700 !important;
    font-size: 9rem !important;
    font-family: 'Great Vibes', 'Dancing Script', cursive !important;
    text-shadow: 2px 4px 12px rgba(0, 0, 0, 0.4);
    margin: 0 0 1rem 0 !important;
  }

  /* ========== 星空与流星雨动效（两层画布：星星在下，流星在上） ========== */
  #starCanvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    pointer-events: none;
  }
  #meteorCanvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
    pointer-events: none;
  }
  /* ========== 四颗小星星图标（保持原位置横排） ========== */
  .star-shape {
    width: 36px;
    height: 36px;
    background: linear-gradient(135deg, #fffdf0, #ffe27a 60%, #ffb84d);
    clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
    filter: drop-shadow(0 0 6px rgba(255, 226, 122, 0.95)) drop-shadow(0 0 18px rgba(255, 200, 90, 0.55));
    animation: starTwinkle 2.8s ease-in-out infinite;
  }
  @keyframes starTwinkle {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.7; transform: scale(0.92); }
  }
  /* 四颗星星图标错落有致且整体平衡：上下左右对称的钻石型布局 */
  .home-icon-row .home-icon-item:nth-child(1) { transform: translate(-90px, -10px); }
  .home-icon-row .home-icon-item:nth-child(1):hover { transform: translate(-90px, -10px) scale(1.15); }
  .home-icon-row .home-icon-item:nth-child(2) { transform: translate(-30px, 120px); }
  .home-icon-row .home-icon-item:nth-child(2):hover { transform: translate(-30px, 120px) scale(1.15); }
  .home-icon-row .home-icon-item:nth-child(3) { transform: translate(30px, -90px); }
  .home-icon-row .home-icon-item:nth-child(3):hover { transform: translate(30px, -90px) scale(1.15); }
  .home-icon-row .home-icon-item:nth-child(4) { transform: translate(90px, 90px); }
  .home-icon-row .home-icon-item:nth-child(4):hover { transform: translate(90px, 90px) scale(1.15); }
  /* 图标依次淡入浮现，更有层次感 */
  .home-icon-item {
    animation: iconFadeIn 0.8s ease both;
  }
  .home-icon-item:nth-child(1) { animation-delay: 0.15s; }
  .home-icon-item:nth-child(2) { animation-delay: 0.3s; }
  .home-icon-item:nth-child(3) { animation-delay: 0.45s; }
  .home-icon-item:nth-child(4) { animation-delay: 0.6s; }
  @keyframes iconFadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  /* 让标题、欢迎语、图标盖在星空流星之上 */
  .md-content h1,
  .home-welcome,
  .home-icon-row {
    position: relative;
    z-index: 3;
  }

  /* 手机端适配 */
  @media (max-width: 768px) {
    html, body {
      overflow: auto;
    }
    .md-main {
      overflow-y: auto;
    }
    .md-main__inner {
      height: auto;
      min-height: 100vh;
      min-height: 100dvh;
      align-items: center;
      padding-top: 1vh;
    }
    .md-content h1 {
      font-size: 3rem !important;
    }
    .home-welcome {
      font-size: 0.9rem;
    }
    .home-icon-row {
      gap: 1.5rem;
      margin-top: 2.5rem;
      max-width: 90%;
      flex-wrap: wrap;
    }
    .home-icon-row .home-icon-item {
      transform: none !important;
    }
    .star-shape {
      width: 26px;
      height: 26px;
    }
    .home-icon-label {
      font-size: 0.85rem;
    }
  }

  /* 更小屏幕（如 iPhone SE / 小屏安卓）：进一步压缩 */
  @media (max-width: 420px) {
    .md-content h1 {
      font-size: 2.4rem !important;
    }
    .home-icon-row {
      gap: 1rem;
      margin-top: 2rem;
    }
    .star-shape {
      width: 24px;
      height: 24px;
    }
  }
</style>

# zhizhi·lovethislife

<p class="home-welcome">「<span id="welcome-text"></span><span class="welcome-cursor"></span>」</p>

<div class="home-icon-row">
  <a class="home-icon-item" href="course/">
    <span class="star-shape"></span>
    <span class="home-icon-label">Notes</span>
  </a>
  <a class="home-icon-item" href="life/">
    <span class="star-shape"></span>
    <span class="home-icon-label">Life</span>
  </a>
  <a class="home-icon-item" href="friends/">
    <span class="star-shape"></span>
    <span class="home-icon-label">Friends</span>
  </a>
  <a class="home-icon-item" href="about/">
    <span class="star-shape"></span>
    <span class="home-icon-label">About</span>
  </a>
</div>

<script>
(function() {
  var el = document.getElementById('welcome-text');
  if (!el) return;
  var word = 'Welcome!';
  var i = 0;
  function type() {
    if (i < word.length) {
      el.textContent = word.slice(0, i + 1);
      i++;
      setTimeout(type, 120);
    }
  }
  setTimeout(type, 600);
})();
</script>

<div class="meteor-wrap">
<canvas id="starCanvas" aria-hidden="true"></canvas>
<script>
(function () {
  var canvas = document.getElementById('starCanvas');
  if (!canvas) return;
  var ctx = canvas.getContext('2d');
  var W, H, DPR;
  var stars = [];
  function initStars() {
    stars = [];
    var count = Math.max(40, Math.min(160, Math.floor(W * H / 9000)));
    for (var i = 0; i < count; i++) {
      var roll = Math.random();
      var xl = roll < 0.08;
      var big = roll < 0.24;
      stars.push({
        x: Math.random() * W,
        y: Math.random() * H * 0.95,
        r: xl ? 3.2 + Math.random() * 1.6
           : big ? 2.0 + Math.random() * 1.2
           : 0.5 + Math.random() * 0.9,
        base: 0.25 + Math.random() * 0.55,
        phase: Math.random() * Math.PI * 2,
        speed: 0.4 + Math.random() * 1.4,
        rot: Math.random() * Math.PI * 2,
        blue: Math.random() < 0.3
      });
    }
  }
  function resize() {
    DPR = window.devicePixelRatio || 1;
    W = window.innerWidth;
    H = window.innerHeight;
    canvas.width = W * DPR;
    canvas.height = H * DPR;
    canvas.style.width = W + 'px';
    canvas.style.height = H + 'px';
    ctx.setTransform(DPR, 0, 0, DPR, 0, 0);
    initStars();
  }
  resize();
  window.addEventListener('resize', resize);
  function draw(t) {
    ctx.clearRect(0, 0, W, H);
    for (var i = 0; i < stars.length; i++) {
      var s = stars[i];
      var tw = 0.55 + 0.45 * Math.sin(t * 0.001 * s.speed * 3 + s.phase);
      var a = s.base * tw;
      if (s.r > 1.5) {
        var g = ctx.createRadialGradient(s.x, s.y, 0, s.x, s.y, s.r * 4);
        var gc = s.blue ? 'rgba(190,220,255,' + (a * 0.7).toFixed(3) + ')' : 'rgba(255,255,255,' + (a * 0.7).toFixed(3) + ')';
        g.addColorStop(0, gc);
        g.addColorStop(1, 'rgba(255,255,255,0)');
        ctx.fillStyle = g;
        ctx.beginPath();
        ctx.arc(s.x, s.y, s.r * 4, 0, Math.PI * 2);
        ctx.fill();
      }
      ctx.globalAlpha = Math.min(1, a);
      ctx.fillStyle = s.blue ? '#dcecff' : '#ffffff';
      ctx.save();
      ctx.translate(s.x, s.y);
      ctx.rotate(s.rot);
      var rr = s.r;
      ctx.beginPath();
      ctx.moveTo(0, -rr * 2.6);
      ctx.quadraticCurveTo(rr * 0.25, -rr * 0.25, rr * 2.6, 0);
      ctx.quadraticCurveTo(rr * 0.25, rr * 0.25, 0, rr * 2.6);
      ctx.quadraticCurveTo(-rr * 0.25, rr * 0.25, -rr * 2.6, 0);
      ctx.quadraticCurveTo(-rr * 0.25, -rr * 0.25, 0, -rr * 2.6);
      ctx.fill();
      ctx.restore();
      ctx.globalAlpha = 1;
    }
    requestAnimationFrame(draw);
  }
  requestAnimationFrame(draw);
})();
</script>
<canvas id="meteorCanvas" aria-hidden="true"></canvas>
<script>
(function () {
  var canvas = document.getElementById('meteorCanvas');
  if (!canvas) return;
  var ctx = canvas.getContext('2d');
  var W, H, DPR;
  function resize() {
    DPR = window.devicePixelRatio || 1;
    W = window.innerWidth;
    H = window.innerHeight;
    canvas.width = W * DPR;
    canvas.height = H * DPR;
    canvas.style.width = W + 'px';
    canvas.style.height = H + 'px';
    ctx.setTransform(DPR, 0, 0, DPR, 0, 0);
  }
  resize();
  window.addEventListener('resize', resize);
  var colors = ['#ffffff', '#ffffff', '#ffffff', '#fff3d6', '#fff3d6', '#ffebba', '#eaf2ff', '#d9f2e4'];
  var meteors = [];
  var sparks = [];
  function spawn() {
    if (meteors.length >= 10) return;
    var roll = Math.random();
    var sc;
    if (roll < 0.08) sc = 2.4 + Math.random() * 0.6;
    else if (roll < 0.4) sc = 1.5 + Math.random() * 0.4;
    else sc = 0.75 + Math.random() * 0.55;
    var r = Math.random();
    var x, y;
    if (r < 0.55) {
      x = W * (0.5 + Math.random() * 0.45);
      y = H * (Math.random() * 0.3);
    } else if (r < 0.85) {
      x = W * (Math.random() * 0.45);
      y = H * (Math.random() * 0.3);
    } else {
      x = W * (0.55 + Math.random() * 0.4);
      y = H * (0.45 + Math.random() * 0.3);
    }
    var speed = (1.8 + Math.random() * 2.2) * (W / 900) * (sc > 2 ? 0.85 : 1);
    var angle = (20 + Math.random() * 34) * Math.PI / 180;
    var sx = -speed * Math.sin(angle);
    var sy = speed * Math.cos(angle);
    meteors.push({
      x: x, y: y,
      vx: sx, vy: sy,
      tvx: sx * 2.4, tvy: sy * 2.4,
      twPhase: Math.random() * Math.PI * 2,
      color: colors[(Math.random() * colors.length) | 0],
      sc: sc,
      len: (90 + Math.random() * 150) * sc,
      life: 0,
      sparkTimer: 0,
      maxLife: (55 + Math.random() * 45) * (sc > 2 ? 1.5 : 1)
    });
  }
  function emitSparks(m) {
    if (m.life < 4) return;
    m.sparkTimer--;
    if (m.sparkTimer > 0) return;
    m.sparkTimer = 1 + ((Math.random() * 3) | 0);
    var n = m.sc > 1.5 ? 2 : 1;
    for (var k = 0; k < n; k++) {
      sparks.push({
        x: m.x, y: m.y,
        vx: m.vx * (0.2 + Math.random() * 0.3) + (Math.random() - 0.5) * 0.8,
        vy: m.vy * (0.2 + Math.random() * 0.3) + (Math.random() - 0.5) * 0.8,
        r: (1.1 * m.sc) + Math.random() * 0.7,
        life: 0,
        maxLife: (20 + ((Math.random() * 25) | 0)),
        color: m.color
      });
    }
  }
  function stepSparks() {
    for (var i = sparks.length - 1; i >= 0; i--) {
      var sp = sparks[i];
      sp.life++;
      if (sp.life > sp.maxLife) { sparks.splice(i, 1); continue; }
      sp.vx *= 0.94;
      sp.vy *= 0.94;
      sp.x += sp.vx;
      sp.y += sp.vy;
      var a = 1 - sp.life / sp.maxLife;
      ctx.globalAlpha = a * 0.85;
      ctx.fillStyle = sp.color;
      ctx.beginPath();
      ctx.arc(sp.x, sp.y, sp.r * (0.4 + 0.6 * a), 0, Math.PI * 2);
      ctx.fill();
      ctx.globalAlpha = 1;
    }
  }
  function step() {
    ctx.globalCompositeOperation = 'destination-out';
    ctx.globalAlpha = 0.15;
    ctx.fillStyle = '#000';
    ctx.fillRect(0, 0, W, H);
    ctx.globalAlpha = 1;
    ctx.globalCompositeOperation = 'source-over';
    for (var i = meteors.length - 1; i >= 0; i--) {
      var m = meteors[i];
      m.life++;
      if (m.life > m.maxLife) { meteors.splice(i, 1); continue; }
      m.vx += (m.tvx - m.vx) * 0.05;
      m.vy += (m.tvy - m.vy) * 0.05;
      m.x += m.vx;
      m.y += m.vy;
      emitSparks(m);
      var appear = Math.min(1, m.life / 6);
      var fade = 1 - Math.max(0, (m.life - (m.maxLife - 10)) / 10);
      var tw = 0.85 + 0.15 * Math.sin(m.life * 0.45 + m.twPhase);
      var bright = Math.max(0, Math.min(appear, fade)) * tw;
      var mag = Math.hypot(m.vx, m.vy) || 1;
      var ux = m.vx / mag, uy = m.vy / mag;
      var ox = -uy, oy = ux;
      var segs = 18;
      ctx.lineCap = 'round';
      for (var s = 0; s < segs; s++) {
        var t = s / segs;
        var px = m.x - ux * m.len * t;
        var py = m.y - uy * m.len * t;
        var w = (5.5 * m.sc) * (1 - t) + 0.5;
        var a = bright * (1 - t * t) * 0.9;
        ctx.globalAlpha = a;
        ctx.strokeStyle = t < 0.25 ? '#ffffff' : m.color;
        ctx.lineWidth = w;
        ctx.beginPath();
        ctx.moveTo(px + ox * (w / 2), py + oy * (w / 2));
        ctx.lineTo(px - ox * (w / 2), py - oy * (w / 2));
        ctx.stroke();
      }
      var hr = 8 * m.sc;
      var hg = ctx.createRadialGradient(m.x, m.y, 0, m.x, m.y, hr);
      hg.addColorStop(0, 'rgba(255,255,255,1)');
      hg.addColorStop(0.4, 'rgba(255,255,255,0.9)');
      hg.addColorStop(0.75, m.color);
      hg.addColorStop(1, 'rgba(255,255,255,0)');
      ctx.globalAlpha = bright;
      ctx.fillStyle = hg;
      ctx.beginPath();
      ctx.arc(m.x, m.y, hr, 0, Math.PI * 2);
      ctx.fill();
    }
    stepSparks();
    requestAnimationFrame(step);
  }
  var timer = 0;
  function schedule() {
    timer--;
    if (timer <= 0) {
      spawn();
      timer = 10 + ((Math.random() * 20) | 0);
    }
    setTimeout(schedule, 60);
  }
  setTimeout(schedule, 300);
  requestAnimationFrame(step);
})();
</script>
</div>
