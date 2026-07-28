<style>
  body {
    overflow: hidden;
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
    background: url('assets/images/bg.jpg') center/cover no-repeat;
    position: relative;
  }
  .md-main::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0, 0, 0, 0.25);
    z-index: 0;
  }
  .md-main__inner {
    max-width: none !important;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding-top: 15vh;
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
    font-size: 6rem !important;
    text-shadow: 2px 4px 12px rgba(0, 0, 0, 0.4);
    margin: 0 0 1rem 0 !important;
  }
</style>

# zhizhi·lovethislife

<p class="home-welcome">「Welcome!」</p>

<div class="home-icon-row">
  <a class="home-icon-item" href="course/">
    <span class="home-icon-emoji">📚</span>
    <span class="home-icon-label">Notes</span>
  </a>
  <a class="home-icon-item" href="life/">
    <span class="home-icon-emoji">💃</span>
    <span class="home-icon-label">Life</span>
  </a>
  <a class="home-icon-item" href="friends/">
    <span class="home-icon-emoji">🤝</span>
    <span class="home-icon-label">Friends</span>
  </a>
</div>
