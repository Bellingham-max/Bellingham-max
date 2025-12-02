<style>
  /* --- 蒸汽朋克核心样式容器 --- */
  .sp-container {
    font-family: 'Courier New', Courier, monospace; /* 复古打字机字体 */
    background-color: #1a1510; /* 深煤炭色背景 */
    background-image: radial-gradient(#2b221a 15%, transparent 16%),
                      radial-gradient(#2b221a 15%, transparent 16%);
    background-size: 20px 20px;
    background-position: 0 0, 10px 10px;
    color: #d4c5a3; /* 羊皮纸文字色 */
    padding: 40px;
    border: 8px solid #8b5a2b; /* 铜框 */
    border-radius: 10px;
    box-shadow: 
      inset 0 0 40px #000, 
      0 0 15px rgba(139, 90, 43, 0.6); /* 外部辉光 */
    position: relative;
    overflow: hidden;
    max-width: 700px;
    margin: 20px auto;
  }

  /* --- 装饰性铆钉 --- */
  .sp-container::before {
    content: '';
    position: absolute;
    top: 5px; left: 5px; right: 5px; bottom: 5px;
    border: 2px dashed #5a4632;
    pointer-events: none;
    z-index: 1;
  }

  /* --- 标题样式 --- */
  .sp-header {
    text-align: center;
    border-bottom: 3px double #c0965c;
    padding-bottom: 15px;
    margin-bottom: 25px;
    position: relative;
    z-index: 2;
  }

  .sp-title {
    font-size: 2.2em;
    font-weight: bold;
    color: #e6b876;
    text-transform: uppercase;
    text-shadow: 2px 2px 0px #3e2714;
    letter-spacing: 4px;
    margin: 0;
  }

  .sp-subtitle {
    font-size: 0.9em;
    color: #8f7458;
    margin-top: 5px;
    font-style: italic;
  }

  /* --- 内容区域 --- */
  .sp-content {
    background: rgba(0, 0, 0, 0.3);
    padding: 20px;
    border: 1px solid #5a4632;
    box-shadow: inset 0 0 10px #000;
    position: relative;
    z-index: 2;
    line-height: 1.6;
  }

  .sp-highlight {
    color: #ff7f50; /* 炽热橙色 */
    font-weight: bold;
    text-shadow: 0 0 5px rgba(255, 127, 80, 0.4);
  }

  /* --- 动态齿轮 (SVG) --- */
  .sp-gear {
    position: absolute;
    fill: #5e4b35;
    opacity: 0.6;
    z-index: 0;
  }
  
  .sp-gear-1 {
    top: -30px;
    right: -30px;
    width: 120px;
    height: 120px;
    animation: sp-spin 10s linear infinite;
  }

  .sp-gear-2 {
    bottom: -20px;
    left: -20px;
    width: 80px;
    height: 80px;
    fill: #3e2e22;
    animation: sp-spin-reverse 7s linear infinite;
  }

  /* --- 交互按钮 --- */
  .sp-btn {
    display: block;
    width: fit-content;
    margin: 20px auto 0;
    background: linear-gradient(180deg, #c0965c, #8b5a2b);
    border: 2px solid #3e2714;
    padding: 10px 30px;
    color: #1a1510;
    font-weight: bold;
    text-transform: uppercase;
    cursor: pointer;
    box-shadow: 0 4px 0 #3e2714;
    transition: all 0.1s;
    text-decoration: none;
    font-family: inherit;
  }

  .sp-btn:hover {
    background: linear-gradient(180deg, #d4aa6e, #9e6935);
    transform: translateY(2px);
    box-shadow: 0 2px 0 #3e2714;
  }

  .sp-btn:active {
    transform: translateY(4px);
    box-shadow: 0 0 0 #3e2714;
  }

  /* --- 动画定义 --- */
  @keyframes sp-spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  @keyframes sp-spin-reverse {
    from { transform: rotate(360deg); }
    to { transform: rotate(0deg); }
  }

  /* --- 蒸汽烟雾效果 --- */
  .sp-steam {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100px;
    background: linear-gradient(to top, rgba(200, 200, 200, 0.1), transparent);
    pointer-events: none;
    z-index: 1;
    animation: sp-flicker 4s infinite alternate;
  }
  
  @keyframes sp-flicker {
    0% { opacity: 0.3; }
    100% { opacity: 0.6; }
  }

</style>

<div class="sp-container">
  <svg class="sp-gear sp-gear-1" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm0-14c-3.31 0-6 2.69-6 6s2.69 6 6 6 6-2.69 6-6-2.69-6-6-6zm0 10c-2.21 0-4-1.79-4-4s1.79-4 4-4 4 1.79 4 4-1.79 4-4 4z"/></svg>
  <svg class="sp-gear sp-gear-2" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M19.43 12.98c.04-.32.07-.64.07-.98s-.03-.66-.07-.98l2.11-1.65c.19-.15.24-.42.12-.64l-2-3.46c-.12-.22-.39-.3-.61-.22l-2.49 1c-.52-.4-1.08-.73-1.69-.98l-.38-2.65C14.46 2.18 14.25 2 14 2h-4c-.25 0-.46.18-.49.42l-.38 2.65c-.61.25-1.17.59-1.69.98l-2.49-1c-.23-.09-.49 0-.61.22l-2 3.46c-.13.22-.07.49.12.64l2.11 1.65c-.04.32-.07.65-.07.98s.03.66.07.98l-2.11 1.65c-.19.15-.24.42-.12.64l2 3.46c.12.22.39.3.61.22l2.49-1c.52.4 1.08.73 1.69.98l.38 2.65c.03.24.24.42.49.42h4c.25 0 .46-.18.49-.42l.38-2.65c.61-.25 1.17-.59 1.69-.98l2.49 1c.23.09.49 0 .61-.22l2-3.46c.12-.22.07-.49-.12-.64l-2.11-1.65zM12 15.5c-1.93 0-3.5-1.57-3.5-3.5s1.57-3.5 3.5-3.5 3.5 1.57 3.5 3.5-1.57 3.5-3.5 3.5z"/></svg>
  
  <div class="sp-steam"></div>

  <div class="sp-header">
    <h1 class="sp-title">Aether & Iron</h1>
    <div class="sp-subtitle">Est. 1889 • Victorian Engineering Division</div>
  </div>

  <div class="sp-content">
    <p>
      欢迎来到 <span class="sp-highlight">档案馆 07 号</span>。这里的机械由黄铜打造，动力源自纯净的蒸汽。
    </p>
    <p>
      当前锅炉压力读数正常。请检查您的护目镜，确保齿轮咬合紧密。在这个模拟与数字交织的时代，我们将重铸<b>复古未来主义</b>的荣光。
    </p>
    <ul>
      <li>⚙️ 纯铜机械结构</li>
      <li>🔥 蒸汽动力驱动</li>
      <li>🕰️ 模拟信号传输</li>
    </ul>

    <a href="#" class="sp-btn">启动引擎</a>
  </div>
</div>
