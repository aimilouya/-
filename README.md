# -
ӨЗБАС-high-school-site
<!DOCTYPE html>
<html lang="mn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>UZBAS 50th Anniversary</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #393939;
      color: white;
      transition: all 0.3s ease;
    }
    .light-mode {
      background-color: #f5f5f5;
      color: black;
    }

    .top-section {
      position: relative;
      height: 100vh;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      text-align: center;
      padding: 2rem;
      animation: fadeIn 1.5s ease-in;
    }
    .top-section video {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      object-fit: cover;
      z-index: 0;
      filter: brightness(0.4);
    }
    .top-section .overlay {
      position: relative;
      z-index: 1;
      animation: zoomIn 1.5s ease forwards;
    }
    .animated-title {
      font-size: 3rem;
      font-weight: bold;
      line-height: 1.2;
      overflow: hidden;
      display: inline-block;
    }
    .animated-title .line {
      display: block;
      transform: translateY(100%);
      opacity: 0;
      animation: slideIn 1s ease-out forwards;
    }
    .line1 { animation-delay: 0.2s; }
    .line2 { animation-delay: 0.6s; }
    @keyframes slideIn {
      to {
        transform: translateY(0);
        opacity: 1;
      }
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes zoomIn {
      from { transform: scale(0.8); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    .scroll-down {
      position: absolute;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      z-index: 2;
      font-size: 1.5rem;
      color: white;
      cursor: pointer;
      animation: bounce 1.5s infinite;
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    .scroll-down.show {
      opacity: 1;
    }
    .scroll-down::before {
      content: '\25BC'; /* Downward arrow */
    }
    @keyframes bounce {
      0%, 100% {
        transform: translateX(-50%) translateY(0);
      }
      50% {
        transform: translateX(-50%) translateY(-10px);
      }
    }
    .scroll-down:hover {
      opacity: 0.7;
    }

    .top-controls {
      position: fixed;
      top: 20px;
      right: 20px;
      z-index: 1000;
      display: flex;
      align-items: center;
      gap: 15px;
    }
    .logo {
      position: fixed;
      top: 20px;
      left: 20px;
      z-index: 1000;
    }
    .logo img {
      height: 40px;
    }

    .menu-toggle {
      display: flex;
      flex-direction: column;
      cursor: pointer;
    }
    .menu-toggle span {
      height: 3px;
      width: 25px;
      background: white;
      margin: 4px 0;
      border-radius: 2px;
      transition: all 0.3s ease;
    }
    .theme-toggle button {
      font-size: 1.5rem;
      background: transparent;
      border: none;
      cursor: pointer;
      color: inherit;
    }
    nav {
      position: fixed;
      top: 70px;
      right: 20px;
      background: rgba(0, 0, 0, 0.8);
      padding: 15px 20px;
      border-radius: 10px;
      display: none;
      flex-direction: column;
      z-index: 1000;
      animation: fadeIn 0.5s ease;
    }
    .light-mode nav {
      background: rgba(255, 255, 255, 0.95);
    }
    nav a {
      color: white;
      text-decoration: none;
      font-size: 1.2rem;
      margin: 10px 0;
      transition: color 0.3s ease;
    }
    .light-mode nav a {
      color: black;
    }
    nav.show {
      display: flex;
    }

    .body-section {
      display: flex;
      justify-content: space-between;
      padding: 60px 10%;
      background-color: #5b5b5b;
      border: 2px solid #ff7400;
      border-radius: 8px;
      flex-wrap: wrap;
      transition: all 0.3s ease;
      animation: slideUp 1.2s ease-in;
    }
    .light-mode .body-section {
      background-color: #d6e4f0;
      border: 2px solid #66b3ff;
    }
    .body-section .text {
      flex: 1;
      font-size: 1rem;
      color: white;
      line-height: 1.6;
      margin-right: 20px;
      animation: fadeInText 1.5s ease-in;
    }
    .light-mode .body-section .text {
      color: black;
    }
    .body-section .image {
      flex: 1;
      background-image: url('mdku-image.jpg');
      background-size: cover;
      background-position: center;
      height: 300px;
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      border: 2px solid #ff7400;
      min-width: 250px;
      animation: zoomIn 1.2s ease;
    }
    .light-mode .body-section .image {
      border: 2px solid #66b3ff;
    }

    @keyframes slideUp {
      from { transform: translateY(50px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
    @keyframes fadeInText {
      from { opacity: 0; transform: translateX(-20px); }
      to { opacity: 1; transform: translateX(0); }
    }

    footer {
      background-color: #1c1c1c;
      color: white;
      text-align: center;
      padding: 20px;
      border-top: 2px solid #ff7400;
      animation: fadeIn 1s ease;
    }
    .light-mode footer {
      background-color: #f0f0f0;
      color: black;
      border-top: 2px solid #66b3ff;
    }

    @media (max-width: 768px) {
      .body-section {
        flex-direction: column;
        text-align: center;
        padding: 40px 5%;
      }
      .body-section .text {
        margin-right: 0;
        margin-bottom: 20px;
      }
      .body-section .image {
        width: 100%;
        height: 200px;
      }
    }
  </style>
</head>
<body>
  <div class="logo">
    <a href="home.html"><img src="logo.png" alt="UZBAS Logo"></a>
  </div>
  <div class="top-section">
    <video autoplay muted loop id="bgVideo">
      <source src="dark-video.mp4" type="video/mp4">
    </video>
    <div class="overlay">
      <h1 class="animated-title">
        <span class="line line1">Өсвөрийн зохион бүтээгчдийн</span>
        <span class="line line2">ахлах сургууль</span>
      </h1>
    </div>
    <div class="scroll-down" onclick="scrollToSection()"></div>
  </div>

  <div class="top-controls">
    <div class="menu-toggle" onclick="toggleMenu()">
      <span></span>
      <span></span>
      <span></span>
    </div>
    <div class="theme-toggle">
      <button onclick="toggleTheme()" id="theme-toggle-btn" aria-label="Toggle Theme">🌙</button>
    </div>
  </div>

  <nav id="mainNav">
    <a href="about.html">Тухай</a>
    <a href="history.html">Түүх</a>
    <a href="programs.html">Үйл ажиллагаа</a>
    <a href="contact.html">Холбоо</a>
    <a href="anniversary.html">50 жилийн ой</a>
  </nav>

  <section class="body-section">
    <div class="text">
      <h2 class="about-title">Өсвөрийн зохион бүтээгчдийн ахлах сургууль...
    }
  ]
}
