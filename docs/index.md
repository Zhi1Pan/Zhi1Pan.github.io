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

  /* ========== 真实流星雨动效（画布实现：尾巴留在原地慢慢消失） ========== */
  #meteorCanvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
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
  /* 让标题、欢迎语、图标盖在流星之上 */
  .md-content h1,
  .home-welcome,
  .home-icon-row {
    position: relative;
    z-index: 2;
  }

  /* 手机端适配 */
  @media (max-width: 768px) {
    .md-content h1 {
      font-size: 3.2rem !important;
    }
    .home-welcome {
      font-size: 0.9rem;
    }
    .home-icon-row {
      gap: 1.5rem;
      margin-top: 3rem;
      max-width: 90%;
      flex-wrap: wrap;
    }
    .home-icon-row .home-icon-item {
      transform: none !important;
    }
    .star-shape {
      width: 28px;
      height: 28px;
    }
    .home-icon-label {
      font-size: 0.85rem;
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
  var colors = ['#5c8bc2', '#4a75ab', '#7bc8e8', '#64b5f6', '#3d6a9e', '#8db4da', '#42a5f5', '#1e88e5'];
  var meteors = [];
  function spawn() {
    if (meteors.length >= 8) return;
    var r = Math.random();
    var x, y;
    if (r < 0.6) {
      x = W * (0.5 + Math.random() * 0.45);
      y = H * (Math.random() * 0.3);
    } else if (r < 0.85) {
      x = W * (Math.random() * 0.45);
      y = H * (Math.random() * 0.3);
    } else {
      x = W * (0.55 + Math.random() * 0.4);
      y = H * (0.45 + Math.random() * 0.3);
    }
    var big = Math.random() < 0.18;
    var speed = (2.0 + Math.random() * 1.8) * (W / 900);
    var angle = (22 + Math.random() * 32) * Math.PI / 180;
    var sx = -speed * Math.sin(angle);
    var sy = speed * Math.cos(angle);
    meteors.push({
      x: x, y: y,
      vx: sx, vy: sy,
      tvx: sx * 2.4, tvy: sy * 2.4,
      twPhase: Math.random() * Math.PI * 2,
      color: colors[(Math.random() * colors.length) | 0],
      big: big,
      len: (110 + Math.random() * 110) * (big ? 1.5 : 1),
      life: 0,
      maxLife: (60 + Math.random() * 45) * (big ? 1.3 : 1)
    });
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
        var w = (m.big ? 8.5 : 5.5) * (1 - t) + 0.5;
        var a = bright * (1 - t * t) * 0.9;
        ctx.globalAlpha = a;
        ctx.strokeStyle = t < 0.25 ? '#ffffff' : m.color;
        ctx.lineWidth = w;
        ctx.beginPath();
        ctx.moveTo(px + ox * (w / 2), py + oy * (w / 2));
        ctx.lineTo(px - ox * (w / 2), py - oy * (w / 2));
        ctx.stroke();
      }
      var hr = m.big ? 11 : 8;
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
    requestAnimationFrame(step);
  }
  var timer = 0;
  function schedule() {
    timer--;
    if (timer <= 0) {
      spawn();
      timer = 12 + ((Math.random() * 24) | 0);
    }
    setTimeout(schedule, 60);
  }
  setTimeout(schedule, 400);
  requestAnimationFrame(step);
})();
</script>
</div>
