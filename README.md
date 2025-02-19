<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Joannes Baskets</title>
  <!-- Google Font for bubbly neon header -->
  <link href="https://fonts.googleapis.com/css2?family=Bubblegum+Sans&display=swap" rel="stylesheet">
  <style>
    /* Neon colorful gradient background */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(45deg, #ff007f, #00ffee, #ffee00, #ff007f);
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
    }
    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    /* Header with neon glowing, bubbly font – more legible */
    header {
      background-color: #000;
      padding: 20px;
      text-align: center;
      border-bottom: 5px solid #00ccff;
    }
    header h1 {
      margin: 0;
      font-family: 'Bubblegum Sans', cursive;
      font-size: 3em;
      color: #00ccff;
      text-shadow: 0 0 5px #00ccff, 0 0 10px #00ccff;
    }
    header p {
      font-size: 1.2em;
      margin-top: 10px;
      color: #fff;
    }

    /* Container with smooth fade-in */
    .container {
      background: #fff;
      border-radius: 10px;
      max-width: 95%;
      margin: 30px auto;
      padding: 20px;
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
      border: 3px solid #00ccff;
      animation: fadeIn 1s ease-out;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* Form styling */
    .form-section { margin-bottom: 25px; }
    label { font-weight: bold; margin-top: 10px; display: block; color: #333; }
    select, input, textarea, button {
      width: 100%;
      padding: 10px;
      font-size: 1em;
      border: 2px solid #00ccff;
      border-radius: 8px;
      background-color: #f9faff;
      margin-top: 8px;
    }
    textarea { height: 100px; resize: vertical; }

    /* Product Buttons Container (cute & extra buttons) */
    #products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      gap: 10px;
      margin-top: 10px;
    }
    .product-btn {
      padding: 10px;
      background-color: #fff;
      border: 2px solid #00ccff;
      border-radius: 10px;
      cursor: pointer;
      transition: transform 0.2s ease, background-color 0.3s ease, box-shadow 0.3s ease;
      font-size: 0.9em;
      color: #333;
    }
    .product-btn:hover {
      transform: scale(1.1) rotate(3deg);
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    }
    .product-btn.selected {
      background-color: #00ccff;
      color: #fff;
      transform: scale(1.1) rotate(-3deg);
    }
    @keyframes pop {
      0% { transform: scale(1); }
      50% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }
    .pop { animation: pop 0.3s ease; }

    /* "Your Basket" List Styling */
    #selectedProductsContainer {
      margin-top: 15px;
      background: #f0faff;
      padding: 10px;
      border: 2px dashed #00ccff;
      border-radius: 8px;
    }
    #selectedProductsContainer h3 { margin-top: 0; color: #00ccff; text-align: center; }
    #selectedProducts { list-style-type: none; padding-left: 0; text-align: center; color: #333; }

    /* Generic Button Styling (updated colors) */
    button {
      background-color: #00ccff;
      color: #fff;
      font-weight: bold;
      cursor: pointer;
      border: none;
      border-radius: 20px;
      padding: 15px;
      box-shadow: 0 4px 6px rgba(0,0,0,0.2);
      transition: transform 0.2s, background-color 0.3s;
      margin-top: 15px;
    }
    button:hover {
      background-color: #0099cc;
      transform: scale(1.1);
    }
    #quoteDisplay { margin-top: 10px; font-weight: bold; color: #0099cc; text-align: center; }

    footer {
      text-align: center;
      padding: 10px;
      background-color: #000;
      color: #fff;
      margin-top: 20px;
    }

    /* Slot Machine Modal (smaller and less in the way) */
    #slotMachineModal {
      position: fixed;
      top: 10%;
      right: 10px;
      width: 300px;
      background: rgba(0,0,0,0.95);
      border: 2px solid #00ff00;
      border-radius: 10px;
      z-index: 1000;
      color: #fff;
      box-shadow: 0 0 15px #00ff00;
      padding: 10px;
      display: none;
    }
    #slotMachineModal.minimized {
      height: 40px;
      overflow: hidden;
      cursor: pointer;
    }
    #slotMachineHeader {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    #slotMachineHeader button {
      background: transparent;
      border: none;
      color: #00ff00;
      font-size: 1.2em;
      cursor: pointer;
      margin-left: 5px;
    }
    #slotMachineContent {
      text-align: center;
      margin-top: 10px;
    }
    #reels {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-bottom: 10px;
    }
    .reel {
      font-size: 2em;
      width: 50px;
      height: 50px;
      line-height: 50px;
      background: #222;
      border: 2px solid #00ff00;
      border-radius: 5px;
    }
    #spinButton {
      background-color: #00ff00;
      color: #000;
      padding: 10px 20px;
      border-radius: 10px;
      border: none;
      cursor: pointer;
      font-weight: bold;
    }
    #spinButton:hover {
      background-color: #00cc00;
    }

    /* Win Popup Modal */
    #winPopup {
      position: fixed;
      top: 30%;
      left: 50%;
      transform: translate(-50%, -30%);
      width: 80%;
      max-width: 300px;
      background: rgba(0, 0, 0, 0.95);
      border: 3px solid #ffdd00;
      border-radius: 10px;
      z-index: 1100;
      color: #ffdd00;
      text-align: center;
      padding: 20px;
      display: none;
      box-shadow: 0 0 20px #ffdd00;
    }
    #winPopup button {
      background-color: #ffdd00;
      color: #000;
      margin-top: 15px;
      border: none;
      border-radius: 10px;
      padding: 10px 20px;
      font-weight: bold;
    }
    #winPopup button:hover {
      background-color: #ffcc00;
    }

    /* Open Slot Machine Button (fixed in bottom-right) */
    #openSlotButton {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #00ff00;
      color: #000;
      border: none;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      font-size: 2em;
      box-shadow: 0 4px 6px rgba(0,0,0,0.3);
      cursor: pointer;
      z-index: 1200;
    }
    #openSlotButton:hover {
      background-color: #00cc00;
      transform: scale(1.1);
    }

    /* Responsive optimization for iPhone */
    @media only screen and (max-width: 600px) {
      header h1 { font-size: 2.5em; }
      .container { padding: 15px; }
      .reel { font-size: 1.5em; width: 40px; height: 40px; line-height: 40px; }
      #slotMachineModal { width: 250px; }
      #openSlotButton { width: 50px; height: 50px; font-size: 1.5em; }
    }
  </style>
</head>
<body>
  <header>
    <h1>Joannes Baskets</h1>
    <p>Your destination for extraordinary baskets!</p>
  </header>

  <div class="container">
    <form id="basketForm">
      <div class="form-section">
        <h2>Basket Details</h2>
        <label for="theme">Select a Theme</label>
        <select id="theme" name="theme" required>
          <option value="Christmas">Christmas</option>
          <option value="Halloween">Halloween</option>
          <option value="Birthday">Birthday</option>
          <option value="Wedding">Wedding</option>
          <option value="Easter">Easter</option>
          <option value="Thanksgiving">Thanksgiving</option>
          <option value="Hanukkah">Hanukkah</option>
          <option value="Valentine's Day">Valentine's Day</option>
          <option value="Mother's Day">Mother's Day</option>
          <option value="Father's Day">Father's Day</option>
        </select>

        <label for="tier">Select Basket Tier</label>
        <select id="tier" name="tier" required>
          <option value="standard">Tier 1: Standard</option>
          <option value="deluxe">Tier 2: Deluxe</option>
          <option value="premium">Tier 3: Premium</option>
        </select>

        <label for="products">Choose Your Products</label>
        <!-- Product Buttons Container with extra cute buttons -->
        <div id="products">
          <button type="button" class="product-btn" data-product="Candles">🕯️ Elegant Candles</button>
          <button type="button" class="product-btn" data-product="Fresh Fruit">🍎 Seasonal Fresh Fruit</button>
          <button type="button" class="product-btn" data-product="Mixed Nuts">🥜 Premium Mixed Nuts</button>
          <button type="button" class="product-btn" data-product="Gourmet Crackers">🥨 Artisan Crackers</button>
          <button type="button" class="product-btn" data-product="Artisan Chips">🍟 Handcrafted Chips</button>
          <button type="button" class="product-btn" data-product="Premium Cheeses">🧀 Fine Cheeses</button>
          <button type="button" class="product-btn" data-product="Wine">🍷 Select Wine</button>
          <button type="button" class="product-btn" data-product="Assorted Chocolates">🍫 Decadent Chocolates</button>
          <button type="button" class="product-btn" data-product="Gourmet Coffee">☕ Exquisite Coffee</button>
          <button type="button" class="product-btn" data-product="Specialty Teas">🍵 Exotic Teas</button>
          <!-- Extra Cute Buttons -->
          <button type="button" class="product-btn" data-product="Fresh Flowers">🌸 Fresh Flowers</button>
          <button type="button" class="product-btn" data-product="Gourmet Cookies">🍪 Gourmet Cookies</button>
          <button type="button" class="product-btn" data-product="Sweet Cupcakes">🧁 Sweet Cupcakes</button>
          <button type="button" class="product-btn" data-product="Organic Honey">🍯 Organic Honey</button>
          <button type="button" class="product-btn" data-product="Artisan Bread">🥖 Artisan Bread</button>
        </div>

        <!-- Live "Your Basket" List -->
        <div id="selectedProductsContainer">
          <h3>Your Basket</h3>
          <ul id="selectedProducts"></ul>
        </div>

        <label for="message">Personalized Message</label>
        <textarea id="message" name="message" placeholder="Enter your message here"></textarea>
      </div>

      <div class="form-section">
        <h2>Quote Generator</h2>
        <p class="info-note">Click below to view your estimated quote based on your selections.</p>
        <button type="button" id="generateQuote">Generate Quote</button>
        <p id="quoteDisplay"></p>
      </div>

      <div class="form-section">
        <h2>Contact Information</h2>
        <p class="info-note">Please provide your contact details so we can confirm your order and arrange pickup.</p>
        <label for="name">Your Name</label>
        <input type="text" id="name" name="name" required />

        <label for="phone">Phone Number</label>
        <input type="tel" id="phone" name="phone" required />

        <label for="email">Email Address</label>
        <input type="email" id="email" name="email" required />

        <label for="venmo">Venmo Username</label>
        <input type="text" id="venmo" name="venmo" required />
      </div>

      <button type="submit">Submit Order Request</button>
    </form>
  </div>

  <footer>
    <p>Joannes Baskets © 2024 | Curated excellence in every basket.</p>
  </footer>

  <!-- Slot Machine Modal (initially hidden) -->
  <div id="slotMachineModal">
    <div id="slotMachineHeader">
      <span id="slotMachineTitle">Slot Machine</span>
      <span id="slotMachineBalance">Balance: $1,000,000</span>
      <div>
        <button id="minimizeSlot">_</button>
        <button id="closeSlot">X</button>
      </div>
    </div>
    <div id="slotMachineContent">
      <div id="reels">
        <div class="reel" id="reel1">🧺</div>
        <div class="reel" id="reel2">🍎</div>
        <div class="reel" id="reel3">🍫</div>
      </div>
      <button id="spinButton">Spin</button>
    </div>
  </div>

  <!-- Win Popup Modal -->
  <div id="winPopup">
    <h2></h2>
    <button id="closeWinPopup">Close</button>
  </div>

  <!-- Open Slot Machine Button (fixed in bottom-right) -->
  <button id="openSlotButton">🎰</button>

  <script>
    /* --- Product Button Functionality --- */
    const selectedProductsList = document.getElementById('selectedProducts');
    const productButtons = document.querySelectorAll('.product-btn');
    productButtons.forEach(btn => {
      btn.addEventListener('click', function() {
        btn.classList.toggle('selected');
        btn.classList.add('pop');
        btn.addEventListener('animationend', () => {
          btn.classList.remove('pop');
        }, {once: true});
        updateSelectedList();
      });
    });
    function updateSelectedList() {
      selectedProductsList.innerHTML = "";
      productButtons.forEach(btn => {
        if (btn.classList.contains('selected')) {
          const li = document.createElement('li');
          li.textContent = btn.getAttribute('data-product');
          selectedProductsList.appendChild(li);
        }
      });
    }

    /* --- Quote Generator --- */
    const productPrices = {
      "Candles": 5,
      "Fresh Fruit": 7,
      "Mixed Nuts": 8,
      "Gourmet Crackers": 6,
      "Artisan Chips": 5,
      "Premium Cheeses": 10,
      "Wine": 15,
      "Assorted Chocolates": 8,
      "Gourmet Coffee": 9,
      "Specialty Teas": 7,
      "Fresh Flowers": 8,
      "Gourmet Cookies": 7,
      "Sweet Cupcakes": 9,
      "Organic Honey": 6,
      "Artisan Bread": 5
    };
    document.getElementById('generateQuote').addEventListener('click', function() {
      let total = 0;
      productButtons.forEach(btn => {
        if (btn.classList.contains('selected')) {
          const product = btn.getAttribute('data-product');
          total += productPrices[product] || 0;
        }
      });
      const tier = document.getElementById('tier').value;
      const multiplier = tier === "standard" ? 1 : tier === "deluxe" ? 1.5 : 2;
      const finalQuote = total * multiplier;
      document.getElementById('quoteDisplay').innerText = "Estimated Quote: $" + finalQuote.toFixed(2);
    });

    /* --- Form Submission via Email --- */
    document.getElementById('basketForm').addEventListener('submit', function(event) {
      event.preventDefault();
      const name = document.getElementById('name').value;
      const phone = document.getElementById('phone').value;
      const email = document.getElementById('email').value;
      const venmo = document.getElementById('venmo').value;
      const theme = document.getElementById('theme').value;
      const tierText = document.getElementById('tier').options[document.getElementById('tier').selectedIndex].text;
      let selectedProducts = [];
      productButtons.forEach(btn => {
        if (btn.classList.contains('selected')) {
          selectedProducts.push(btn.getAttribute('data-product'));
        }
      });
      const productsStr = selectedProducts.join(', ') || 'None selected';
      const message = document.getElementById('message').value || 'No special message.';
      const quoteText = document.getElementById('quoteDisplay').innerText || "Quote not generated.";
      const subject = encodeURIComponent('New Basket Request');
      const body = encodeURIComponent(
        `=== Customer Details ===\n` +
        `Name: ${name}\n` +
        `Phone: ${phone}\n` +
        `Email: ${email}\n` +
        `Venmo Username: ${venmo}\n\n` +
        `=== Basket Details ===\n` +
        `Theme: ${theme}\n` +
        `Tier: ${tierText}\n` +
        `Products: ${productsStr}\n` +
        `Special Message: ${message}\n` +
        `${quoteText}`
      );
      window.location.href = `mailto:jbtr9@comcast.net?subject=${subject}&body=${body}`;
    });

    /* --- Slot Machine Functionality --- */
    const slotEmojis = ["🧺", "🕯️", "🍎", "🥜", "🧀", "🍫", "🍷", "☕", "🍵", "💰", "🎰"];
    const reel1 = document.getElementById('reel1');
    const reel2 = document.getElementById('reel2');
    const reel3 = document.getElementById('reel3');
    const spinButton = document.getElementById('spinButton');
    const balanceDisplay = document.getElementById('slotMachineBalance');
    let balance = 1000000; // resets on refresh
    const spinCost = 50; // cost per spin

    function updateBalanceDisplay() {
      balanceDisplay.textContent = "Balance: $" + balance.toLocaleString();
    }
    updateBalanceDisplay();

    spinButton.addEventListener('click', function() {
      if (balance < spinCost) {
        alert("Insufficient funds for a spin!");
        return;
      }
      // Deduct spin cost and update display
      balance -= spinCost;
      updateBalanceDisplay();
      spinButton.disabled = true;
      const spinTime = 1500; // spin for 1.5 seconds for realism
      const interval = setInterval(() => {
        reel1.textContent = slotEmojis[Math.floor(Math.random() * slotEmojis.length)];
        reel2.textContent = slotEmojis[Math.floor(Math.random() * slotEmojis.length)];
        reel3.textContent = slotEmojis[Math.floor(Math.random() * slotEmojis.length)];
      }, 75);
      setTimeout(() => {
        clearInterval(interval);
        // Determine final values
        const final1 = slotEmojis[Math.floor(Math.random() * slotEmojis.length)];
        const final2 = slotEmojis[Math.floor(Math.random() * slotEmojis.length)];
        const final3 = slotEmojis[Math.floor(Math.random() * slotEmojis.length)];
        reel1.textContent = final1;
        reel2.textContent = final2;
        reel3.textContent = final3;
        spinButton.disabled = false;
        // Determine win conditions: if at least two reels match, win bonus.
        let bonus = 0;
        if (final1 === final2 && final2 === final3) {
          bonus = 1000; // jackpot for triple match
        } else if (final1 === final2 || final2 === final3 || final1 === final3) {
          bonus = 200; // win for double match
        }
        if (bonus > 0) {
          // Add bonus to account balance and show win popup
          balance += bonus;
          updateBalanceDisplay();
          showWinPopup(`Congratulations! You won $${bonus.toLocaleString()}!`);
        }
      }, spinTime);
    });

    /* --- Slot Machine Modal Controls --- */
    const slotMachineModal = document.getElementById('slotMachineModal');
    const minimizeSlot = document.getElementById('minimizeSlot');
    const closeSlot = document.getElementById('closeSlot');
    minimizeSlot.addEventListener('click', function(e) {
      e.stopPropagation();
      slotMachineModal.classList.toggle('minimized');
    });
    closeSlot.addEventListener('click', function(e) {
      e.stopPropagation();
      slotMachineModal.style.display = 'none';
    });
    // Clicking the modal restores it if minimized
    slotMachineModal.addEventListener('click', function() {
      if (slotMachineModal.classList.contains('minimized')) {
        slotMachineModal.classList.remove('minimized');
      }
    });

    /* --- Win Popup Functionality --- */
    const winPopup = document.getElementById('winPopup');
    const closeWinPopup = document.getElementById('closeWinPopup');
    function showWinPopup(message) {
      winPopup.querySelector("h2").textContent = message;
      winPopup.style.display = 'block';
    }
    closeWinPopup.addEventListener('click', function() {
      winPopup.style.display = 'none';
    });

    /* --- Open Slot Machine Button Functionality --- */
    const openSlotButton = document.getElementById('openSlotButton');
    openSlotButton.addEventListener('click', function() {
      // Toggle display of the slot machine modal
      if (slotMachineModal.style.display === 'none' || slotMachineModal.style.display === '') {
        slotMachineModal.style.display = 'block';
      } else {
        slotMachineModal.style.display = 'none';
      }
    });
  </script>
</body>
</html>
`
