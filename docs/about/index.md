# 关于

你好，我是 zhizhi

ZJU25心理在读

欢迎来到我的小世界！

---

2026.7.28正在收被试的zhizhi闲着无聊跟着大狗老师的教程搭建了这个网站

起初也只是想建着玩玩儿，或是只上传一些笔记。

> 那天晚上的晚霞特别好看，刚想拍照记录下来，有位被试就进来了，于是放下手机去开程序。
>
> 再次回来，短短几分钟的时间，晚霞就已经变了样子，暗淡了下来。
>
> 在这一瞬间萌发了一些想法：
>
>**这个世界上有好多像晚霞一样美好的事物，我不想每次都来不及记录，或是让记录散落在备忘录上。**

于是除了笔记之外，我也想要在这里记录一些可以和大家分享的美好。

> 哪天老了躺在病床上，打开网站也能笑着说"我真真切切地活过"。

另外，网站名称也来自于我很喜欢的一首歌 **《I love this life》**。

**热爱很重要，所以我们都要热爱生活！！**

---


## 留言板

欢迎留下你的意见！！~

<script src="https://utteranc.es/client.js"
        repo="Zhi1Pan/Zhi1Pan.github.io"
        issue-term="pathname"
        theme="preferred-color-scheme"
        crossorigin="anonymous"
        async>
</script>

<script>
(function () {
  function currentTheme() {
    return document.body.getAttribute('data-md-color-scheme') || '';
  }
  function sync() {
    var iframe = document.querySelector('iframe.utterances-frame');
    if (!iframe) return;
    var theme = currentTheme() === 'slate' ? 'github-dark' : 'github-light';
    try {
      iframe.contentWindow.postMessage({ type: 'set-theme', theme: theme }, 'https://utteranc.es');
    } catch (e) {}
  }
  var tries = 0;
  var timer = setInterval(function () {
    var iframe = document.querySelector('iframe.utterances-frame');
    if (iframe) {
      clearInterval(timer);
      iframe.addEventListener('load', function () { setTimeout(sync, 500); });
    }
    if (++tries > 60) clearInterval(timer);
  }, 200);
  var observer = new MutationObserver(function () { setTimeout(sync, 200); });
  observer.observe(document.documentElement, { attributes: true, attributeFilter: ['data-md-color-scheme'] });
})();
</script>

---

<div class="pv-counter-wrap">
  <div class="pv-card" id="busuanzi_container_site_pv" style="display:none;">
    <span class="pv-number" id="busuanzi_value_site_pv"></span>
    <span class="pv-label">次浏览</span>
  </div>
  <span class="pv-loading-text" id="pv-loading">📊 数据加载中...</span>
</div>

<script>
(function() {
  var check = setInterval(function() {
    var card = document.getElementById('busuanzi_container_site_pv');
    var loading = document.getElementById('pv-loading');
    if (card && card.style.display !== 'none') {
      if (loading) loading.style.display = 'none';
      clearInterval(check);
    }
  }, 200);
  setTimeout(function() {
    var loading = document.getElementById('pv-loading');
    if (loading) loading.style.display = 'none';
    clearInterval(check);
  }, 6000);
})();
</script>
