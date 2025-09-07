<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Mission Vruksh</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #dff5e1, #b2e6c9);
      margin: 0;
      padding: 0;
      color: #114b18;
      overflow-x: hidden;
    }
    #container {
      max-width: 750px;
      margin: 40px auto;
      background: #fff;
      border-radius: 16px;
      box-shadow: 0 4px 25px rgba(0,0,0,0.1);
      padding: 40px 32px;
      text-align: center;
      animation: fadeIn 0.8s ease-in-out;
    }
    h1, h2 {
      color: #1a6029;
    }
    p {
      line-height: 1.6;
    }
    .btns {
      display: flex;
      justify-content: center;
      gap: 12px;
      margin-top: 28px;
      flex-wrap: wrap;
    }
    .next-btn, .back-btn {
      background: linear-gradient(135deg, #2f8c47, #1c6230);
      color: white;
      border: none;
      padding: 12px 28px;
      border-radius: 30px;
      font-size: 1em;
      cursor: pointer;
      transition: transform 0.2s, background 0.3s;
    }
    .next-btn:hover, .back-btn:hover {
      transform: scale(1.05);
      background: linear-gradient(135deg, #1c6230, #145020);
    }
    .login-form input {
      display: block;
      width: 95%;
      margin: 14px auto;
      padding: 12px;
      font-size: 1em;
      border-radius: 8px;
      border: 1px solid #9fc8a7;
    }
    .login-form label {
      display: block;
      margin-top: 12px;
      font-weight: 600;
      color: #114b18;
      text-align: left;
    }
    .instructions, .details {
      text-align: left;
      margin: 0 auto;
      max-width: 600px;
    }
    ul {
      padding-left: 20px;
    }
    .progress-bar {
      width: 100%;
      background: #e5f4e8;
      height: 12px;
      border-radius: 10px;
      overflow: hidden;
      margin-top: 8px;
      margin-bottom: 24px;
    }
    .progress {
      height: 100%;
      width: 0%;
      background: #2f8c47;
      transition: width 0.5s ease;
    }
    footer {
      margin-top: 20px;
      font-size: 0.9em;
      color: #4b7c57;
      text-align: center;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(15px); }
      to { opacity: 1; transform: translateY(0); }
    }
    @media (max-width: 600px) {
      #container {
        padding: 20px;
        margin: 20px;
      }
      .next-btn, .back-btn {
        width: 100%;
      }
    }
    /* Falling leaves */
    .leaf {
      position: fixed;
      top: -50px;
      font-size: 24px;
      animation: fall linear forwards;
      z-index: 9999;
    }
    @keyframes fall {
      to {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <div id="container"></div>
  
  <footer>
    🌱 Mission Vruksh © 2025 | Together for a Greener Tomorrow
  </footer>

  <script>
    const pages = [
      {
        html: `
          <h1>🌳 Mission Vruksh</h1>
          <h2>Welcome Participants!</h2>
          <p>Thank you for joining us in our mission to make the world greener and healthier. 
          <b>Mission Vruksh</b> is a collective effort of students, teachers, and the community 
          to plant and nurture trees for a sustainable tomorrow.</p>
          <p>🌱 Together we can create cleaner air, better soil, and a healthier environment 
          for generations to come.</p>
        `
      },
      {
        html: `
          <h2>About Tree Plantation</h2>
          <div class="details">
            <p>Tree plantation is not just about planting saplings—it is about creating harmony 
            between humans and nature. Each tree planted helps reduce carbon dioxide, 
            improve biodiversity, and regulate the climate.</p>
            <p>🌿 Our mission is to plant trees in schools, colleges, villages, and cities 
            where greenery is needed the most. With your help, we aim to make every space 
            more eco-friendly.</p>
          </div>
        `
      },
      {
        html: `
          <h2>Benefits of Tree Plantation</h2>
          <div class="details">
            <ul>
              <li>🌿 Purifies the air and increases oxygen levels</li>
              <li>🌍 Helps in fighting climate change by absorbing CO₂</li>
              <li>💧 Conserves water and prevents soil erosion</li>
              <li>🏞 Provides shade and cools down cities</li>
              <li>🐦 Supports wildlife and biodiversity</li>
              <li>💚 Enhances beauty and peace in surroundings</li>
            </ul>
          </div>
        `
      },
      {
        html: `
          <h2>Login</h2>
          <p>Please log in to record your participation in Mission Vruksh.</p>
          <form class="login-form">
            <label for="username">Username:</label>
            <input type="text" id="username" placeholder="Enter your username" required>
            <label for="password">Password:</label>
            <input type="password" id="password" placeholder="Enter your password" required>
            <button type="submit" class="next-btn">Login</button>
          </form>
        `
      },
      {
        html: `
          <h2>Tree Care Instructions</h2>
          <div class="instructions">
            <p>🌱 Planting is only the beginning—nurturing trees is equally important. 
            Here are some care tips:</p>
            <ul>
              <li>💦 Water regularly, especially in the first year</li>
              <li>🌱 Keep the area weed-free so the tree gets enough nutrients</li>
              <li>🛡 Protect young plants with fencing if animals are nearby</li>
              <li>🐛 Monitor for pests and diseases, and act promptly</li>
              <li>🌳 Add mulch around the base to keep moisture in the soil</li>
            </ul>
          </div>
        `
      },
      {
        html: `
          <h2>🌿 Thank You!</h2>
          <p id="thankUser"></p>
          <p><b>Mission Vruksh</b> appreciates your contribution. Every small effort counts, 
          and your support inspires others to join this green revolution.</p>
          <p>💚 Let’s promise to care for nature and create a greener, healthier tomorrow together.</p>
        `
      }
    ];

    let currentPage = 0;
    let loggedInUser = "";
    const container = document.getElementById('container');

    function renderPage() {
      let header = `
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:10px;">
          <span style="font-weight:600; color:#2f8c47;">
            ${loggedInUser ? "Hello, " + loggedInUser + " 🌿" : "Mission Vruksh"}
          </span>
          <span style="font-size:0.9em; color:#256e39;">
            Progress: ${Math.round(((currentPage+1)/pages.length)*100)}%
          </span>
        </div>
        <div class="progress-bar"><div class="progress" style="width:${((currentPage+1)/pages.length * 100)}%"></div></div>
      `;

      container.innerHTML = header + pages[currentPage].html;

      // Navigation buttons
      let navBtns = "";
      if (currentPage > 0 && currentPage < pages.length - 1) {
        navBtns += `<button class="back-btn">Back</button>`;
      }
      if (currentPage < pages.length - 1 && currentPage !== 3) {
        navBtns += `<button class="next-btn">Next</button>`;
      }
      container.innerHTML += `<div class="btns">${navBtns}</div>`;

      // Handle login page
      if (currentPage === 3) {
        const form = container.querySelector('.login-form');
        form.onsubmit = (e) => {
          e.preventDefault();
          const username = form.querySelector('#username').value.trim();
          const password = form.querySelector('#password').value.trim();
          if (username && password.length >= 4) {
            loggedInUser = username;
            currentPage++;
            renderPage();
          } else {
            alert('⚠️ Enter a valid username and password (min 4 chars).');
          }
        };
      }

      // Back button logic
      const backBtn = container.querySelector('.back-btn');
      if (backBtn) {
        backBtn.onclick = () => {
          currentPage--;
          renderPage();
        };
      }

      // Next button logic
      const nextBtn = container.querySelector('.next-btn');
      if (nextBtn) {
        nextBtn.onclick = () => {
          currentPage++;
          renderPage();
        };
      }

      // Final page effects
      if (currentPage === pages.length - 1) {
        const thankUser = container.querySelector('#thankUser');
        if (thankUser && loggedInUser) {
          thankUser.innerHTML = `🌟 Thank you, <b>${loggedInUser}</b>, for being part of this green journey!`;
        }
        launchLeaves();
      }
    }

    // Falling leaves effect
    function launchLeaves() {
      for (let i = 0; i < 20; i++) {
        let leaf = document.createElement("div");
        leaf.className = "leaf";
        leaf.innerHTML = "🍃";
        leaf.style.left = Math.random() * window.innerWidth + "px";
        leaf.style.animationDuration = (2 + Math.random() * 3) + "s";
        document.body.appendChild(leaf);
        setTimeout(() => leaf.remove(), 5000);
      }
    }

    renderPage();
  </script>
</body>
</html>
