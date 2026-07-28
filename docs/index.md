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
  }
  .md-main__inner {
    max-width: none !important;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
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
    font-size: 3.5rem !important;
    text-shadow: 2px 4px 12px rgba(0, 0, 0, 0.4);
    margin: 0 !important;
  }
</style>

# zhizhi·lovethislife
