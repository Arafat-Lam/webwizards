<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Web Wizards Studio Website</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
  <style>
    /* Basic Reset */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    .video-container {
        position: fixed;
        top: 50%;
        left: 50%;
        width: 100vw;
        height: 100vh;
        transform: translate(-50%, -50%);
        z-index: -1;
        pointer-events: none;
    }
    .video-background {
        width: 100vw;
        height: 56.25vw; /* 16:9 Aspect Ratio */
        min-height: 100vh;
        min-width: 177.78vh;
    }
    body {
      font-family: 'Roboto', sans-serif;
      background-color: #000;
      color: #333;
      line-height: 1.6;
    }

    h1, h2 {
      color: #333;
    }

    a {
      text-decoration: none;
      color: inherit;
    }

    /* Navigation */
    nav {
      background-color: #000;
      padding: 1rem;
    }
  
    nav ul {
      list-style: none;
      display: flex;
      justify-content: center;
    }
  
    nav ul li {
      margin: 0 20px;
    }
  
    nav ul li a {
      color: #fff;
      font-weight: bold;
      font-size: 1.2rem;
      text-transform: uppercase;
    }
  
    nav ul li a:hover {
      color: #3498db;
    }
  
    /* Hide navigation on mobile */
    @media (max-width: 768px) {
      nav ul {
        display: none; /* Hide navigation items on mobile */
      }
    }
  
    /* Show navigation on larger screens (desktop/tablet) */
    @media (min-width: 769px) {
      nav ul {
        display: flex; /* Display navigation items on larger screens */
      }
    }
     /* Hero Section */
    .hero {
      background: url('https://via.placeholder.com/1920x1080') center/cover no-repeat;
      color: white;
      text-align: center;
      padding: 120px 20px;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      height: 50vh; /* Full viewport height */
      text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.6);
    }
  
    .hero h1 {
      font-size: 4rem;
      color: white;
      margin-bottom: 20px;
      animation: typing 5s steps(40) forwards, blink 0.75s step-end infinite;
      white-space: nowrap;
      overflow: hidden;
      display: inline-block;
      border-right: 2px solid #000;
    }

    .hero p {
      font-size: 1.5rem;
      font-weight: 300;
    }

    @keyframes typing {
      from { width: 0; }
      to { width: 100%; }
    }

    @keyframes blink {
      50% { border-color: transparent; }
    }
    /* About Section */
    .about-us {
      display: flex;
      align-items: center;
      padding: 60px 20px;
    }

    .about-us img {
      max-width: 425px;
      margin-right: 30px;
    }

    .about-us .description {
      flex: 1;
    }

    .about-us h2 {
      font-size: 2rem;
      margin-bottom: 20px;
      color: white;
    }

    .about-us p {
      font-size: 1rem;
      color:white;
    }

    /* Additional Styles for the Services Section Animation */
    .services {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      padding: 60px 20px;
      opacity: 0; /* Make it invisible initially */
      animation: fadeIn 2s forwards; /* Add fade-in animation */
    }
  
    .service-item {
      background-color: #fff;
      width: 250px;
      padding: 20px;
      margin: 10px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      text-align: center;
      cursor: pointer;
      transform: translateY(-50px); /* Start from above */
      animation: slideInFromTop 1s ease forwards; /* Add slide-in effect */
    }

    .service-item img {
      width: 100px; /* Fixed width */
      height: 100px; /* Fixed height */
      object-fit: cover; /* Ensures the image covers the area without distortion */
      border-radius: 8px; /* Optional, for rounded corners */
      margin-bottom: 10px; /* Optional, adds some spacing between the image and text */
    }

    @keyframes fadeIn {
      0% { opacity: 0; }
      100% { opacity: 1; }
    }
  
    @keyframes slideInFromTop {
      0% {
        transform: translateY(-50px); /* Start above the section */
        opacity: 0;
      }
      100% {
        transform: translateY(0); /* End at the normal position */
        opacity: 1;
      }
    }
  
    /* Animation delay to stagger the items */
    .service-item:nth-child(1) {
      animation-delay: 0.2s;
    }
  
    .service-item:nth-child(2) {
      animation-delay: 0.4s;
    }
  
    .service-item:nth-child(3) {
      animation-delay: 0.6s;
    }

    /* Loader */
    .loader-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.8);
      display: none;
      justify-content: center;
      align-items: center;
    }

    .loader-ring {
      position: absolute;
      border: 5px solid transparent;
      border-top: 5px solid #fff;
      border-radius: 50%;
      width: 100px;
      height: 100px;
      animation: rotate 1.5s linear infinite;
    }

    .loader-ring:nth-child(2) {
      border-top: 5px solid gray;
      border-right: 5px solid gray;
      width: 140px;
      height: 140px;
      animation-duration: 2s;
    }

    .logo {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 80px;
      height: 80px;
      border-radius: 50%;
      filter: grayscale(100%);
    }

    @keyframes rotate {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* Logo and Title Section (Circle with Text) */
    .logo-container {
      position: absolute;
      top: 10px;
      left: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
    }

    .logo-circle {
      background-color: #000;
      border-radius: 50%;
      padding: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 10px;
    }

    .logo-circle img {
      width: 40px;
      height: 40px;
    }

    .logo-text {
      font-size: 1.6rem;
      font-weight: bold;
      color:white;
      white-space: nowrap;
      overflow: hidden;
      border-right: 2px solid #000;
      width: 0;
      animation: typing1 7.2s steps(1000) infinite;
    }

    @keyframes typing1 {
      0% { width: 0; }
      100% { width: 9.3em; }
    }

    /* Iframe Section */
    iframe {
      width: 100%;
      height: 500px;
      border: none;
      display: block;
      margin-top: 20px;
    }

    /* Footer */
    footer {
      background-color: #333;
      color: #fff;
      text-align: center;
      padding: 20px;
    }

    footer a {
      color: #3498db;
    }

    /* Responsive Design */
    @media (max-width: 768px) {
      nav ul {
        flex-direction: column;
      }

      .hero h1 {
        font-size: 2rem;
      }

      .about-us {
        flex-direction: column;
        text-align: center;
      }

      .about-us img {
        margin-bottom: 150px;
      }

      .services {
        flex-direction: column;
        align-items: center;
      }

      .logo-container {
        left: 10px;
        top: 10px;
        flex-direction: column;
        align-items: center;
      }

      .logo-text {
        font-size: 1.4rem;
        text-align: center;
      }
    }
    .chat-container {
      position: fixed;
      bottom: 80px;
      right: 20px;
      width: 350px;
      max-width: 90%;
      background: #111;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(255, 255, 255, 0.2);
      display: none;
      flex-direction: column;
    }
    
    .chat-header {
      background: white;
      padding: 12px;
      text-align: center;
      font-weight: bold;
      border-top-left-radius: 12px;
      border-top-right-radius: 12px;
    }
    
    .chat-body {
      height: 300px;
      overflow-y: auto;
      padding: 10px;
      background: #0a0a0a;
      display: flex;
      flex-direction: column;
    }
    
    .chat-footer {
      display: flex;
      background: #222;
      padding: 10px;
      border-bottom-left-radius: 12px;
      border-bottom-right-radius: 12px;
    }
    
    .chat-footer input {
      flex: 1;
      padding: 8px;
      border: none;
      border-radius: 8px;
      outline: none;
    }
    
    .chat-footer button {
      background: #fff;
      color: #000;
      border: none;
      padding: 8px 12px;
      margin-left: 8px;
      border-radius: 8px;
      cursor: pointer;
    }
    
    .chat-toggle {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: black;
      color: #000;
      padding: 15px;
      border-radius: 50%;
      font-size: 24px;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(255, 255, 255, 0.2);
    }
    
    .message {
      max-width: 75%;
      padding: 8px 12px;
      margin: 5px;
      border-radius: 10px;
      word-wrap: break-word;
    }
    .user { background: #fff; align-self: flex-end; }
    .bot { background:#fff; align-self: flex-start; }
    .search-container {
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 20px 0;
        width: 100%;
    }
    
    .search-input {
        width: 80%; /* মোবাইল ডিভাইসের জন্য বড় */
        max-width: 500px; /* বড় স্ক্রিনে সীমিত প্রস্থ */
        padding: 12px;
        font-size: 16px;
        border-radius: 25px;
        border: 1px solid #ccc;
        outline: none;
        transition: all 0.3s;
        text-align: center; /* টেক্সট মাঝখানে রাখবে */
    }
    
    .search-input:focus {
        border-color: #007bff;
        box-shadow: 0 0 8px rgba(0, 123, 255, 0.5);
    }
    
    /* ছোট স্ক্রিনের জন্য */
    @media (max-width: 600px) {
        .search-input {
            width: 90%; /* মোবাইলে বড় করে দেখাবে */
        }
    }
  </style>
</head>
<body>
  <div class="video-container">
      <iframe class="video-background" 
              src="https://www.youtube.com/embed/Z90rTdVoomY?autoplay=1&mute=1&loop=1&playlist=Z90rTdVoomY&controls=0&modestbranding=1&showinfo=0&disablekb=1&rel=0&fs=0&vq=hd1080" 
              frameborder="0" 
              allowfullscreen>
      </iframe>
      <!-- Fallback Image -->
      <img src="https://via.placeholder.com/1920x1080" alt="Fallback Background" class="video-background">
  </div>
    <!-- Navigation -->
  <nav>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#services">GAMES</a></li>
    </ul>
  </nav>
  
  <!-- Logo and Text Section (Typing Effect) -->
  <div class="logo-container" onclick="refreshIframe('https://sites.google.com/view/webwizardsstudio/the-studio')">
    <div class="logo-circle">
      <img src="https://assets.onecompiler.app/438cc35sk/43byh7sar/cloud%20gaming%20hub%20logo%20for%20gen%20z%20with%20black%20background%20and%20every%20meaning%20of%20game.png" alt="Logo">
    </div>
    <div class="logo-text">Clould Gaming Hub</div>
  </div>

  <!-- Hero Section -->
  <section class="hero" id="home">
    <h1>Welcome to Clould Gaming Hub</h1>
    <p>A Cloud Gaming Hub is an online platform</p>
  </section>

  <!-- About Us Section -->
  <section class="about-us" id="about">
    <img src="https://assets.onecompiler.app/438cc35sk/43byn64c3/Screenshot%202025-03-16%20191028.png" alt="Web Wizards Studio Logo">
    <div class="description">
      <h2>About Cloud Gaming Hub </h2>
      <p>Cloud Gaming Hub is the ultimate platform for gamers who want to experience high-performance gaming without the need for expensive hardware. By leveraging the power of cloud computing, it allows users to play resource-intensive games on any device with an internet connection. Whether you’re using a PC, smartphone, or tablet, the Cloud Gaming Hub ensures seamless gameplay, stunning visuals, and minimal lag, all while eliminating the need for downloads or installations.

The platform supports a wide range of popular games, from AAA titles to indie gems, providing gamers with access to an extensive library. Users can jump into games instantly and enjoy multiplayer features, social integration, and more, all without worrying about storage space or hardware limitations.

With cutting-edge technology, Cloud Gaming Hub transforms the way games are played, making gaming more accessible and flexible than ever before. Whether you're a casual player or a competitive gamer, Cloud Gaming Hub opens up a world of possibilities, offering a hassle-free, high-quality gaming experience anytime, anywhere. Join the revolution and elevate your gaming experience to the cloud!</p>
    </div>
  </section>
  
  <!-- Services Section -->
  <section class="hero" id="services">
    <h1>GAMES</h1>
  </section>
  <div class="search-container">
      <input type="text" id="searchBar" class="search-input" placeholder="Search For Games..." onkeyup="searchGames()">
  </div>
  <section class="services" id="services">
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/minecraft')">
      <img src="https://assets.onecompiler.app/438cc35sk/43bydtfrq/m1.jpeg" alt="Service Logo">
      <h3>MINECRAFT</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/krunker')">
      <img src="https://i.redd.it/17xsk8x20qs51.png" alt="Service Logo">
      <h3>krunker</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/mr-mine')">
      <img src="https://pbs.twimg.com/profile_images/1344417953115119619/Jpf355Ce_400x400.jpg" alt="Service Logo">
      <h3>Mr. Mine</h3>
    </div>   
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/war-brokers')">
      <img src="https://static.tvtropes.org/pmwiki/pub/images/war_brokers.png" alt="Service Logo">
      <h3>War Brokers</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/dead-frontier')">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRewA-ScvSHD-9wFSA1ebzPZzH4Picq4jQkCQ&s" alt="Service Logo">
      <h3>Dead Frontier</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/among-us')">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRhB42QBXN3M3heY3e9oMJGMWRWMgG1VmEz9Q&s" alt="Service Logo">
      <h3>Among us</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/nightpoint')">
      <img src="https://img.poki-cdn.com/cdn-cgi/image/quality=78,width=314,height=314,fit=cover,f=auto/ef026214-7374-450a-98dd-a60f74de4617.png" alt="Service Logo">
      <h3>Nightpoint</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/splix-io')">
      <img src="https://iogames.games/data/image/game/splix-io.jpg" alt="Service Logo">
      <h3>Splix.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/mope-io')">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTl9p-w1qnkGUw9P0Uvv73PVqvyRw7HoZxF4RCpyoDDl_y91Yr7nFDe7LflQoxw95RKgh8&usqp=CAU" alt="Service Logo">
      <h3>Mope.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/superhex-io')">
      <img src="https://a.silvergames.com/screenshots/superhexio/superhex.jpg" alt="Service Logo">
      <h3>Superhex.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/deeeep-io')">
      <img src="https://img.itch.zone/aW1nLzE5NDE2OTgxLnBuZw==/original/IEeyyl.png" alt="Service Logo">
      <h3>Deeeep.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/wormszone-io')">
      <img src="https://assets.apk.live/com.wildspike.wormszone--5383-icon.png" alt="Service Logo">
      <h3>WormsZone.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/littlebigsnake')">
      <img src="https://pbs.twimg.com/profile_images/1572280657023479808/Jv_TUZUf_400x400.jpg" alt="Service Logo">
      <h3>LittleBigSnake </h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/yorg-io')">
      <img src="https://www.gamekarma.com/images/games/76.png" alt="Service Logo">
      <h3>Yorg.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/tankwars-io)">
      <img src="https://www.gamekarma.com/images/games/59.png" alt="Service Logo">
      <h3>TankWars.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/flyordie-io')">
      <img src="https://is4-ssl.mzstatic.com/image/thumb/Purple115/v4/3a/04/05/3a0405e1-32ac-6a48-d971-a0fb1ac343b4/AppIcon-1x_U007emarketing-0-85-220-0-8.png/1024x1024bb.png" alt="Service Logo">
      <h3>FlyOrDie.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/brutal-io')">
      <img src="https://play-lh.googleusercontent.com/tELDr42pXgKm7bppm9u7Lxi1wsIondePelVzvflo6rbStOLlIS41nEb01ssUYVqFnpo=w526-h296-rw" alt="Service Logo">
      <h3>Brutal.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/starve-io')">
      <img src="https://www.gamekarma.com/images/games/19.png" alt="Service Logo">
      <h3>Starve.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/limax-io')">
      <img src="https://images.forfun.com/v2/fetch/67/67a6481c9611268608b0c38ecda9c26a.png" alt="Service Logo">
      <h3>Limax.io</h3>
    </div>
    <div class="service-item" onclick="loadService('https://sites.google.com/view/webwizardsstudio/slithercraft-io')">
      <img src="https://img.gamepix.com/games/slithercraft-io/icon/slithercraft-io.png?w=105" alt="Service Logo">
      <h3>SlitherCraft.io</h3>
    </div>
    <!-- Repeat the above block 47 times as required -->
  </section>
<script>
  function loadService(url) {
    // Show the loader
    document.getElementById('loader').style.display = 'flex';

    // Delay opening the link slightly so the loader is visible
    setTimeout(function() {
      window.open(url, "_blank");
      // Hide loader after opening
      document.getElementById('loader').style.display = 'none';
    }, 4000); // 800ms delay to allow loader visibility
  }
</script>
  <!-- Iframe to load content -->
  <iframe id="iframe" src="https://example.com" title="ads"></iframe>

  <!-- Loader -->
  <div id="loader" class="loader-container">
    <div class="loader-ring"></div>
    <div class="loader-ring"></div>
    <img class="logo" src="https://assets.onecompiler.app/438cc35sk/43byh7sar/cloud%20gaming%20hub%20logo%20for%20gen%20z%20with%20black%20background%20and%20every%20meaning%20of%20game.png" alt="Logo">
  </div>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025  Website. Web Wizards Studio.</p>
  </footer>
  <div class="chat-container" id="chatContainer">
    <div class="chat-header">Chatbot</div>
    <div class="chat-body" id="messages">
      <p class="message bot">Hello! How can I help you? I can answer questions that start with "what" or "who".</p>
    </div>
    <div class="chat-footer">
      <input type="text" id="userInput" placeholder="Type here..." onkeypress="handleKeyPress(event)">
      <button onclick="sendMessage()">Send</button>
    </div>
  </div>
  <div class="chat-toggle" id="chatToggle">💬</div>

  <script>
    function addMessage(text, sender = "bot") {
      const message = document.createElement("p");
      message.className = `message ${sender}`;
      message.textContent = text;
      document.getElementById("messages").appendChild(message);
      document.getElementById("messages").scrollTop = document.getElementById("messages").scrollHeight;
    }

    function sendMessage() {
      const userInput = document.getElementById("userInput");
      const userText = userInput.value.trim();
      if (!userText) return;

      addMessage(userText, "user");
      userInput.value = "";

      fetch(`https://en.wikipedia.org/api/rest_v1/page/summary/${encodeURIComponent(userText)}`)
        .then(response => response.json())
        .then(data => {
          if (data.extract) {
            addMessage(data.extract, "bot");
          } else {
            addMessage("Sorry, I couldn't find an answer. Try another question! I can answer questions that start with 'what' or 'who'.Like : Minecraft,snowball .etc", "bot");
          }
        })
        .catch(() => addMessage("Error retrieving data. Try again!", "bot"));
    }

    function handleKeyPress(event) {
      if (event.key === "Enter") {
        sendMessage();
      }
    }

    const chatContainer = document.getElementById("chatContainer");
    const chatToggle = document.getElementById("chatToggle");
    
    chatToggle.addEventListener("click", () => {
      const isVisible = chatContainer.style.display === "flex";
      chatContainer.style.display = isVisible ? "none" : "flex";
    });
    function searchGames() {
        let input = document.getElementById('searchBar').value.toLowerCase();
        let items = document.querySelectorAll('.service-item');
        
        items.forEach(item => {
            let gameName = item.querySelector('h3').textContent.toLowerCase();
            if (gameName.includes(input)) {
                item.style.display = 'block';
            } else {
                item.style.display = 'none';
            }
        });
    }
  </script>
</body>
</html>
