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
    background: url('assets/images/bg.jpg') center/cover no-repeat;
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

  /* 手机端适配 */
  @media (max-width: 768px) {
    .md-content h1 {
      font-size: 3.8rem !important;
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
    .home-icon-emoji {
      font-size: 3rem;
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
    <span class="home-icon-emoji">📚</span>
    <span class="home-icon-label">Notes</span>
  </a>
  <a class="home-icon-item" href="life/">
    <span class="home-icon-emoji">🍸</span>
    <span class="home-icon-label">Life</span>
  </a>
  <a class="home-icon-item" href="friends/">
    <span class="home-icon-emoji">🤝</span>
    <span class="home-icon-label">Friends</span>
  </a>
  <a class="home-icon-item" href="about/">
    <span class="home-icon-emoji">🔗</span>
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
