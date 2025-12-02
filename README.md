<style>
  /* --- 基础容器：重型装甲板 --- */
  .ind-container {
    font-family: 'Courier New', monospace;
    /* 模拟深色金属网格背景 */
    background-color: #0d0d0d;
    background-image: 
      linear-gradient(rgba(18, 16, 16, 0.9) 2px, transparent 2px),
      linear-gradient(90deg, rgba(18, 16, 16, 0.9) 2px, transparent 2px),
      linear-gradient(rgba(255, 255, 255, 0.05) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255, 255, 255, 0.05) 1px, transparent 1px);
    background-size: 50px 50px, 50px 50px, 10px 10px, 10px 10px;
    
    color: #a8a8a8; /* 灰尘色文字 */
    padding: 0;
    border: 6px solid #2e2620; /* 深褐锈色边框 */
    box-shadow: 
      0 0 0 4px #000,
      0 0 30px rgba(0, 0, 0, 0.8);
    position: relative;
    max-width: 680px;
    margin: 30px auto;
    overflow: hidden;
  }

  /* --- 顶部警示条纹 --- */
  .ind-hazard-stripe {
    height: 15px;
    width: 100%;
    background: repeating-linear-gradient(
      45deg,
      #2b2b2b,
      #2b2b2b 10px,
      #dfa000 10px,
      #dfa000 20px
    );
    border-bottom: 2px solid #000;
  }

  /* --- 内部内容区 --- */
  .ind-content-box {
    padding: 30px;
    position: relative;
    z-index: 2;
  }

  /* --- 标题：辉光管风格 --- */
  .ind-title {
    font-size: 2.5em;
    font-weight: 900;
    text-transform: uppercase;
    color: #1a1a1a;
    /* 文字镂空效果 + 橙色发光背景 */
    -webkit-text-stroke: 1px #ff6600;
    text-shadow: 
      0 0 10px rgba(255, 102, 0, 0.5),
      0 0 20px rgba(255, 102, 0, 0.3);
    margin: 0;
    letter-spacing: -2px;
    border-left: 5px solid #ff6600;
    padding-left: 15px;
  }

  .ind-subtitle {
    color: #ff6600;
    font-size: 0.8em;
    letter-spacing: 3px;
    margin-bottom: 20px;
    opacity: 0.8;
    text-transform: uppercase;
  }

  /* --- 装饰性螺丝钉 --- */
  .ind-screw {
    position: absolute;
    width: 12px;
    height: 12px;
    background: radial-gradient(circle, #555 30%, #222 90%);
    border-radius: 50%;
    box-shadow: inset 1px 1px 2px rgba(255,255,255,0.2);
    z-index: 5;
  }
  .ind-screw::after { /* 螺丝槽 */
    content: '';
    position: absolute;
    top: 50%; left: 50%;
    width: 80%; height: 2px;
    background: #111;
    transform: translate(-50%, -50%) rotate(45deg);
  }
  /* 螺丝位置 */
  .tl { top: 25px; left: 10px; }
  .tr { top: 25px; right: 10px; }
  .bl { bottom: 10px; left: 10px; }
  .br { bottom: 10px; right: 10px; }

  /* --- 动态仪表盘条 --- */
  .ind-meter-container {
    background: #111;
    height: 8px;
    width: 100%;
    margin: 20px 0;
    border: 1px solid #333;
    position: relative;
    overflow: hidden;
  }

  .ind-meter-fill {
    height: 100%;
    background: linear-gradient(90deg, #333, #ff6600);
    width: 75%;
    box-shadow: 0 0 10px #ff6600;
    animation: ind-pressure 3s ease-in-out infinite alternate;
  }

  /* --- 工业齿轮 (SVG) --- */
  .ind-gear {
    position: absolute;
    fill: #1f1a17; /* 非常深的生锈色 */
    z-index: 1;
  }

  .ind-gear-big {
    right: -40px;
    bottom: -40px;
    width: 180px;
    height: 180px;
    opacity: 0.5;
    animation: ind-rotate 15s linear infinite;
  }

  /* --- 交互按钮：紧急开关 --- */
  .ind-btn {
    display: inline-block;
    background: #222;
    color: #ff6600;
    border: 2px solid #ff6600;
    padding: 12px 25px;
    font-weight: bold;
    text-transform: uppercase;
    text-decoration: none;
    margin-top: 15px;
    transition: all 0.2s;
    box-shadow: 0 0 5px rgba(255, 102, 0, 0.2);
  }

  .ind-btn:hover {
    background: #ff6600;
    color: #000;
    box-shadow: 0 0 20px rgba(255, 102, 0, 0.8);
  }

  /* --- 动画 --- */
  @keyframes ind-rotate {
    100% { transform: rotate(360deg); }
  }
  @keyframes ind-pressure {
    0% { width: 60%; opacity: 0.7; }
    20% { width: 62%; }
    40% { width: 58%; }
    100% { width: 85%; opacity: 1; }
  }
  
  /* 烟雾层 */
  .ind-smoke {
    position: absolute;
    top: 0; left: 0; width: 100%; height: 100%;
    background: radial-gradient(circle at 50% 50%, transparent 60%, rgba(0,0,0,0.8) 100%);
    pointer-events: none;
    z-index: 3;
  }

</style>

<div class="ind-container">
  <div class="ind-hazard-stripe"></div>
  
  <div class="ind-screw tl"></div>
  <div class="ind-screw tr"></div>
  <div class="ind-screw bl"></div>
  <div class="ind-screw br"></div>

  <svg class="ind-gear ind-gear-big" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm0-14c-3.31 0-6 2.69-6 6s2.69 6 6 6 6-2.69 6-6-2.69-6-6-6zm0 10c-2.21 0-4-1.79-4-4s1.79-4 4-4 4 1.79 4 4-1.79 4-4 4z"/></svg>

  <div class="ind-content-box">
    <h1 class="ind-title">PROJECT: IRONCLAD</h1>
    <div class="ind-subtitle">System Status: Critical // Level 4</div>
    
    <div style="font-size: 0.9em; margin-bottom: 5px;">BOILER PRESSURE</div>
    <div class="ind-meter-container">
      <div class="ind-meter-fill"></div>
    </div>

    <p>
      检测到以太能量波动。核心温度已达到临界值。
      <br><br>
      在这个被煤灰覆盖的世界里，只有最坚硬的齿轮才能转动。所有非必要的装饰已被剥离，剩下的只有<b>纯粹的功能</b>与<b>工业的轰鸣</b>。
    </p>

    <ul style="list-style: square; color: #777;">
      <li>[x] 启动重型液压泵</li>
      <li>[ ] 释放紧急蒸汽阀</li>
      <li>[ ] 接入差分机网络</li>
    </ul>

    <a href="#" class="ind-btn">执行协议 OMEGA</a>
  </div>
  
  <div class="ind-smoke"></div>
</div>
