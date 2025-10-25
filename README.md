# <!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>我讨厌你 (-`ェ´-)</title>
  <style>
    body {
      font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial;
      text-align: center;
      background: linear-gradient(135deg,#f8fafc,#e0f7fa);
      min-height: 100vh;
      padding: 40px 20px;
    }
    .card {
      background: #fff;
      margin: 60px auto;
      padding: 40px 20px;
      max-width: 420px;
      border-radius: 20px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.1);
    }
    h1 {
      color: #333;
      font-size: 22px;
      margin-bottom: 8px;
    }
    p {
      color: #666;
      font-size: 15px;
      margin-bottom: 24px;
    }
    button {
      background: #07c160;
      color: white;
      border: none;
      border-radius: 10px;
      padding: 14px 30px;
      font-size: 16px;
      cursor: pointer;
      transition: all .25s;
    }
    button:hover {
      background: #06ad55;
    }
    #result {
      margin-top: 24px;
      font-size: 18px;
      color: #e91e63;
      font-weight: bold;
      min-height: 24px;
    }
    .hint {
      margin-top: 12px;
      font-size: 13px;
      color: #999;
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>我讨厌你 (-`ェ´-)</h1>
    <p>点一下下面的按钮看看会发生什么～</p>
    <button id="loveBtn">点我</button>
    <div id="result"></div>
    <div class="hint">（点完会自动复制“我喜欢你”，长按群聊输入框粘贴发送）</div>
  </div>

  <script>
    const btn = document.getElementById('loveBtn');
    const result = document.getElementById('result');
    const text = '我喜欢你 ❤️';

    btn.addEventListener('click', async () => {
      result.textContent = text;
      try {
        await navigator.clipboard.writeText(text);
        result.textContent = text + '（已复制到剪贴板）';
      } catch (e) {
        result.textContent = text + '（复制失败，请长按手动复制）';
      }
      btn.textContent = '嘿嘿 😳';
      btn.disabled = true;
      setTimeout(() => {
        btn.textContent = '再点一次';
        btn.disabled = false;
      }, 1500);
    });
  </script>
</body>
</html>
