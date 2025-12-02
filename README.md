<div class="cyber-container">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');

    .cyber-container {
      /* 全局容器设置 */
      font-family: 'VT323', 'Courier New', monospace;
      background-color: #050505;
      color: #e0e0e0;
      padding: 40px;
      position: relative;
      overflow: hidden;
      border: 2px solid #333;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.8);
      max-width: 800px;
      margin: 20px auto;
      --neon-cyan: #00f3ff;
      --neon-pink: #ff00ff;
      --bg-dark: #0a0a0a;
    }

    /* 背景网格 - 复古80s风格 */
    .cyber-container::before {
      content: "";
      position: absolute;
      top: 0; left: 0; right: 0; bottom: 0;
      background: 
        linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), 
        linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
      background-size: 100% 2px, 3px 100%;
      z-index: 1;
      pointer-events: none;
    }

    /* 装饰性网格地板 */
    .cyber-grid-bg {
      position: absolute;
      width: 200%;
      height: 100%;
      top: -50%;
      left: -50%;
      background-image: 
        linear-gradient(rgba(0, 243, 255, 0.1) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0, 243, 255, 0.1) 1px, transparent 1px);
      background-size: 40px 40px;
      transform: perspective(500px) rotateX(60deg);
      opacity: 0.3;
      z-index: 0;
      animation: grid-move 20s linear infinite;
    }

    @keyframes grid-move {
      0% { transform: perspective(500px) rotateX(60deg) translateY(0); }
      100% { transform: perspective(500px) rotateX(60deg) translateY(40px); }
    }

    /* 标题 Glitch 效果 */
    .cyber-header {
      position: relative;
      z-index: 2;
      text-align: center;
      margin-bottom: 50px;
    }

    .glitch-title {
      font-size: 3.5rem;
      font-weight: bold;
      text-transform: uppercase;
      position: relative;
      text-shadow: 2px 2px 0px var(--neon-pink), -2px -2px 0px var(--neon-cyan);
      letter-spacing: 5px;
      animation: text-flicker 3s infinite alternate;
    }

    .glitch-title::before, .glitch-title::after {
      content: attr(data-text);
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #050505;
    }

    .glitch-title::before {
      left: 2px;
      text-shadow: -1px 0 var(--neon-pink);
      clip-path: inset(20% 0 30% 0);
      animation: glitch-anim-1 2s infinite linear alternate-reverse;
    }

    .glitch-title::after {
      left: -2px;
      text-shadow: -1px 0 var(--neon-cyan);
      clip-path: inset(40% 0 43% 0);
      animation: glitch-anim-2 2s infinite linear alternate-reverse;
    }

    /* 内容卡片 - 赛博风格切角 */
    .cyber-card {
      position: relative;
      z-index: 2;
      background: rgba(10, 10, 10, 0.85);
      border: 1px solid var(--neon-cyan);
      padding: 25px;
      margin-bottom: 20px;
      clip-path: polygon(
        10% 0, 100% 0, 100% 90%, 90% 100%, 0 100%, 0 10%
      );
      transition: all 0.3s ease;
    }

    .cyber-card:hover {
      box-shadow: 0 0 15px var(--neon-cyan);
      background: rgba(10, 10, 10, 0.95);
      transform: translateY(-2px);
    }

    .card-title {
      color: var(--neon-pink);
      border-bottom: 2px solid var(--neon-pink);
      display: inline-block;
      padding-bottom: 5px;
      margin-bottom: 15px;
      font-size: 1.5rem;
      text-transform: uppercase;
    }

    /* 装饰性细节 */
    .deco-corner {
      position: absolute;
      width: 10px;
      height: 10px;
      border: 2px solid var(--neon-cyan);
      z-index: 3;
    }
    .top-left { top: 10px; left: 10px; border-right: none; border-bottom: none; }
    .top-right { top: 10px; right: 10px; border-left: none; border-bottom: none; }
    .bottom-left { bottom: 10px; left: 10px; border-right: none; border-top: none; }
    .bottom-right { bottom: 10px; right: 10px; border-left: none; border-top: none; }

    /* 按钮样式 */
    .cyber-btn {
      background: transparent;
      color: var(--neon-cyan);
      font-family: 'VT323', monospace;
      font-size: 1.2rem;
      padding: 10px 30px;
      border: 2px solid var(--neon-cyan);
      cursor: pointer;
      text-transform: uppercase;
      position: relative;
      overflow: hidden;
      transition: 0.3s;
      margin-top: 10px;
      display: inline-block;
      text-decoration: none;
    }

    .cyber-btn:hover {
      background: var(--neon-cyan);
      color: #000;
      box-shadow: 0 0 20px var(--neon-cyan);
    }

    /* 状态栏 */
    .status-bar {
      display: flex;
      justify-content: space-between;
      border-top: 1px dashed #333;
      padding-top: 10px;
      margin-top: 30px;
      font-size: 0.9rem;
      color: #666;
      z-index: 2;
      position: relative;
    }

    .blink { animation: blink 1s step-end infinite; }

    /* 动画定义 */
    @keyframes blink { 50% { opacity: 0; } }
    @keyframes text-flicker {
      0% { opacity: 1; } 3% { opacity: 0.4; } 6% { opacity: 1; } 
      7% { opacity: 0.4; } 8% { opacity: 1; } 9% { opacity: 1; } 
      10% { opacity: 0.1; } 11% { opacity: 1; } 100% { opacity: 1; }
    }
    @keyframes glitch-anim-1 {
      0% { clip-path: inset(20% 0 80% 0); } 20% { clip-path: inset(60% 0 10% 0); }
      40% { clip-path: inset(40% 0 50% 0); } 60% { clip-path: inset(80% 0 5% 0); }
      80% { clip-path: inset(10% 0 60% 0); } 100% { clip-path: inset(30% 0 20% 0); }
    }
    @keyframes glitch-anim-2 {
      0% { clip-path: inset(10% 0 60% 0); } 20% { clip-path: inset(30% 0 20% 0); }
      40% { clip-path: inset(10% 0 80% 0); } 60% { clip-path: inset(40% 0 10% 0); }
      80% { clip-path: inset(50% 0 30% 0); } 100% { clip-path: inset(20% 0 70% 0); }
    }

  </style>

  <div class="cyber-grid-bg"></div>
  
  <div class="deco-corner top-left"></div>
  <div class="deco-corner top-right"></div>
  <div class="deco-corner bottom-left"></div>
  <div class="deco-corner bottom-right"></div>

  <header class="cyber-header">
    <div style="font-size: 0.8rem; color: var(--neon-pink); letter-spacing: 2px; margin-bottom: 5px;">SYSTEM STATUS: ONLINE</div>
    <h1 class="glitch-title" data-text="CYBER_NEXUS">CYBER_NEXUS</h1>
    <div style="font-size: 0.9rem; color: #555;">v.2077.01.a [BETA]</div>
  </header>

  <div class="cyber-card">
    <h2 class="card-title">01_Identity_Core</h2>
    <p>正在连接神经漫游网络... <span class="blink">_</span></p>
    <p>欢迎访问终端。此处收录了遗落的数据碎片与记忆备份。所有访问行为已被记录。</p>
    
    <ul style="list-style: none; padding: 0; margin-top: 15px;">
      <li style="margin-bottom: 8px;">> <strong>职业:</strong> 赏金黑客 / 前端架构师</li>
      <li style="margin-bottom: 8px;">> <strong>位置:</strong> 新九龙城寨, 扇区 7</li>
      <li style="margin-bottom: 8px;">> <strong>状态:</strong> <span style="color:#0f0">■ 活跃</span></li>
    </ul>
  </div>

  <div class="cyber-card" style="border-color: var(--neon-pink);">
    <h2 class="card-title" style="color: var(--neon-cyan); border-color: var(--neon-cyan);">02_Protocol</h2>
    <p>检测到未经授权的访问协议。是否启动防御矩阵？</p>
    <br>
    <a href="#" class="cyber-btn">启动协议</a>
    <a href="#" class="cyber-btn" style="border-color: var(--neon-pink); color: var(--neon-pink); margin-left: 10px;">拒绝访问</a>
  </div>

  <div class="status-bar">
    <span>MEM: 64TB / 128TB</span>
    <span>NET: ENCRYPTED</span>
    <span>PWR: 87%</span>
  </div>

</div>
