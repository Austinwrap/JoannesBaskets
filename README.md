<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Joanne's Baskets - Groovy Vibes</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
  <style>
    /* Cheerful, Balanced Styling */
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      padding: 0;
      background: #fff8e1; /* Warm, light yellow */
      color: #333;
    }

    /* Header with Flair */
    header {
      background: #26a69a; /* Bright teal */
      color: #fff;
      padding: 25px;
      text-align: center;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      border-bottom: 4px solid #ff7043; /* Coral accent */
    }
    header h1 {
      margin: 0;
      font-size: 2.8em;
      text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
      animation: bounceIn 1s ease;
    }
    header p {
      font-size: 1.2em;
      margin: 5px 0 0;
    }
    @keyframes bounceIn {
      0% { transform: scale(0.8); opacity: 0; }
      60% { transform: scale(1.1); opacity: 1; }
      100% { transform: scale(1); }
    }

    /* Main Content */
    .container {
      max-width: 800px;
      margin: 20px auto;
      background: #fff;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
      border: 2px solid #26a69a;
    }
    h2 {
      color: #26a69a;
      margin: 20px 0 10px;
      font-size: 1.5em;
      border-bottom: 2px solid #ffca28;
      padding-bottom: 5px;
    }

    /* Form Styling */
    .form-section {
      margin-bottom: 30px;
    }
    label {
      display: block;
      font-weight: bold;
      margin: 10px 0 5px;
      color: #26a69a;
    }
    select, input, textarea {
      width: 100%;
      padding: 12px;
      border: 2px solid #ffca28;
      border-radius: 8px;
      font-size: 1em;
      background: #fffde7;
      transition: border-color 0.3s;
    }
    select:focus, input:focus, textarea:focus {
      border-color: #ff7043;
      outline: none;
    }
    textarea {
      height: 90px;
      resize: vertical;
    }

    /* Product Grid */
    #products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
      gap: 15px;
    }
    .product-btn {
      padding: 12px;
      background: #fff;
      border: 2px solid #26a69a;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
      text-align: center;
      font-weight: bold;
      color: #333;
    }
    .product-btn:hover {
      background: #ff7043;
      color: #fff;
      transform: scale(1.05);
    }
    .product-btn.selected {
      background: #26a69a;
      color: #fff;
      border-color: #ffca28;
    }

    /* Preview */
    #basketPreview {
      margin-top: 20px;
      padding: 15px;
      background: #fffde7;
      border: 2px dashed #ff7043;
      border-radius: 8px;
      text-align: center;
    }

    /* Buttons */
    button {
      background: #26a69a;
      color: #fff;
      padding: 12px 25px;
      border: none;
      border-radius: 25px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    }
    button:hover {
      background: #ff7043;
      transform: translateY(-2px);
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    }

    /* Footer */
    footer {
      background: #26a69a;
      color: #fff;
      text-align: center;
      padding: 20px;
      margin-top: 20px;
      border-top: 4px solid #ffca28;
    }

    /* Slot Machine Modal */
    #slotMachineModal {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 600px;
      background: #fff;
      border: 3px solid #ff7043;
      border-radius: 15px;
      padding: 20px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
      z-index: 1000;
      display: none;
      animation: popIn 0.3s ease;
    }
    @keyframes popIn {
      0% { transform: translate(-50%, -50%) scale(0.8); opacity: 0; }
      100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
    }
    #slotMachineHeader {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;
      font-weight: bold;
      color: #26a69a;
    }
    #reels {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-bottom: 15px;
    }
    .reel {
      width: 80px;
      height: 80px;
      line-height: 80px;
      text-align: center;
      font-size: 2.5em;
      border: 2px solid #ffca28;
      border-radius: 10px;
      background: #fffde7;
      transition: transform 0.2s;
    }
    .reel.spinning {
      transform: rotateX(360deg);
    }
    #slotMachineModal button {
      width: 100%;
    }

    /* Responsive */
    @media (max-width: 600px) {
      .container {
        padding: 20px;
        margin: 10px;
      }
      #products {
        grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
      }
      #slotMachineModal {
        width: 90%;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Joanne's Baskets</h1>
    <p>Build a Basket with a Splash of Fun!</p>
  </header>

  <div class="container">
    <form id="basketForm">
      <!-- Basket Details -->
      <div class="form-section">
        <h2>Basket Details</h2>
        <label for="theme">Theme <span style="color: #ff7043">*</span></label>
        <select id="theme" name="theme" required>
          <option value="" disabled selected>Select a theme</option>
          <option value="Christmas">Christmas</option>
          <option value="Birthday">Birthday</option>
          <option value="Wedding">Wedding</option>
          <option value="Custom">Custom</option>
        </select>

        <label for="tier">Basket Size <span style="color: #ff7043">*</span></label>
        <select id="tier" name="tier" required>
          <option value="" disabled selected>Choose a size</option>
          <option value="standard">Standard</option>
          <option value="deluxe">Deluxe</option>
          <option value="premium">Premium</option>
        </select>

        <label>Products</label>
        <div id="products">
          <button type="button" class="product-btn" data-product="Candles">🕯️ Candles</button>
          <button type="button" class="product-btn" data-product="Fruit">🍎 Fruit</button>
          <button type="button" class="product-btn" data-product="Nuts">🥜 Nuts</button>
          <button type="button" class="product-btn" data-product="Chocolates">🍫 Chocolates</button>
          <button type="button" class="product-btn" data-product="Wine">🍷 Wine</button>
          <button type="button" class="product-btn" data-product="Flowers">🌸 Flowers</button>
        </div>

        <div id="basketPreview">
          <h3>Your Basket</h3>
          <p id="previewText">Start adding some goodies!</p>
        </div>

        <label for="message">Message</label>
        <textarea id="message" name="message" placeholder="Add a special touch (optional)"></textarea>
      </div>

      <!-- Delivery/Pickup -->
      <div class="form-section">
        <h2>Delivery/Pickup</h2>
        <label for="delivery">Delivery or Pickup <span style="color: #ff7043">*</span></label>
        <select id="delivery" name="delivery" required>
          <option value="" disabled selected>Choose an option</option>
          <option value="pickup">Pickup</option>
          <option value="delivery">Delivery</option>
        </select>

        <label for="date">Preferred Date <span style="color: #ff7043">*</span></label>
        <input type="date" id="date" name="date" required />
      </div>

      <!-- Contact Info -->
      <div class="form-section">
        <h2>Contact Info</h2>
        <label for="name">Name <span style="color: #ff7043">*</span></label>
        <input type="text" id="name" name="name" required />
        <label for="phone">Phone <span style="color: #ff7043">*</span></label>
        <input type="tel" id="phone" name="phone" required />
        <label for="email">Email <span style="color: #ff7043">*</span></label>
        <input type="email" id="email" name="email" required />
        <label for="venmo">Venmo <span style="color: #ff7043">*</span></label>
        <input type="text" id="venmo" name="venmo" required />
      </div>

      <button type="button" id="generateQuote">Get a Quote</button>
      <p id="quoteDisplay"></p>
      <button type="submit">Send It Off!</button>
    </form>
    <button id="openSlotLink" style="margin-top: 20px;">Spin the Slots!</button>
  </div>

  <footer>
    <p>Joanne's Baskets © 2024 | Gifts with a Groovy Twist!</p>
  </footer>

  <!-- Slot Machine Modal -->
  <div id="slotMachineModal">
    <div id="slotMachineHeader">
      <span>Balance: <span id="slotMachineBalance">$1,000</span></span>
      <button id="closeSlot">X</button>
    </div>
    <div id="reels">
      <div class="reel" id="reel1">🧺</div>
      <div class="reel" id="reel2">🍎</div>
      <div class="reel" id="reel3">🍫</div>
    </div>
    <button id="spinButton">Spin ($5)</button>
  </div>

  <script>
    /* Product Selection */
    const productButtons = document.querySelectorAll('.product-btn');
    const previewText = document.getElementById('previewText');
    productButtons.forEach(btn => {
      btn.addEventListener('click', () => {
        btn.classList.toggle('selected');
        updatePreview();
      });
    });

    function updatePreview() {
      const selected = Array.from(productButtons)
        .filter(btn => btn.classList.contains('selected'))
        .map(btn => btn.getAttribute('data-product'));
      const theme = document.getElementById('theme').value;
      previewText.textContent = selected.length
        ? `A ${theme} basket with: ${selected.join(', ')}`
        : 'Start adding some goodies!';
    }

    /* Smart Quote Generator */
    const tierBaseCosts = { standard: 10, deluxe: 20, premium: 30 }; // Hidden base costs
    const productPrices = { Candles: 5, Fruit: 7, Nuts: 8, Chocolates: 8, Wine: 15, Flowers: 8 };
    document.getElementById('generateQuote').addEventListener('click', () => {
      const selected = Array.from(productButtons)
        .filter(btn => btn.classList.contains('selected'))
        .map(btn => btn.getAttribute('data-product'));
      const tier = document.getElementById('tier').value;
      const delivery = document.getElementById('delivery').value === 'delivery' ? 10 : 0;
      const baseCost = tierBaseCosts[tier] || 0;
      const productCost = selected.reduce((sum, p) => sum + (productPrices[p] || 0), 0);
      const total = baseCost + productCost + delivery;
      document.getElementById('quoteDisplay').textContent = `Estimated Total: $${total.toFixed(2)}`;
    });

    /* Form Submission */
    document.getElementById('basketForm').addEventListener('submit', e => {
      e.preventDefault();
      const form = e.target;
      if (!form.checkValidity()) {
        form.reportValidity(); // Show validation errors if any
        return;
      }
      const formData = new FormData(form);
      const selected = Array.from(productButtons)
        .filter(btn => btn.classList.contains('selected'))
        .map(btn => btn.getAttribute('data-product'))
        .join(', ');
      const body = encodeURIComponent(
        `=== Customer Details ===\n` +
        `Name: ${formData.get('name')}\n` +
        `Phone: ${formData.get('phone')}\n` +
        `Email: ${formData.get('email')}\n` +
        `Venmo: ${formData.get('venmo')}\n\n` +
        `=== Basket Details ===\n` +
        `Theme: ${formData.get('theme')}\n` +
        `Size: ${document.getElementById('tier').options[document.getElementById('tier').selectedIndex].text}\n` +
        `Products: ${selected || 'None'}\n` +
        `Message: ${formData.get('message') || 'None'}\n\n` +
        `=== Delivery/Pickup ===\n` +
        `Option: ${formData.get('delivery')}\n` +
        `Date: ${formData.get('date')}\n\n` +
        `${document.getElementById('quoteDisplay').textContent || 'Quote not generated'}`
      );
      window.location.href = `mailto:jbtr9@comcast.net?subject=New%20Basket%20Order&body=${body}`;
    });

    /* Slot Machine */
    const slotModal = document.getElementById('slotMachineModal');
    const reels = [document.getElementById('reel1'), document.getElementById('reel2'), document.getElementById('reel3')];
    const spinButton = document.getElementById('spinButton');
    const balanceDisplay = document.getElementById('slotMachineBalance');
    let balance = 1000;
    const slotIcons = ['🧺', '🍎', '🍫', '💰', '🎁'];

    function updateBalance() {
      balanceDisplay.textContent = `$${balance}`;
    }

    spinButton.addEventListener('click', () => {
      if (balance < 5) return alert('Not enough funds!');
      balance -= 5;
      updateBalance();
      spinButton.disabled = true;
      reels.forEach(reel => reel.classList.add('spinning'));
      let spins = 20;
      const interval = setInterval(() => {
        reels.forEach(reel => reel.textContent = slotIcons[Math.floor(Math.random() * slotIcons.length)]);
        if (--spins <= 0) {
          clearInterval(interval);
          spinButton.disabled = false;
          reels.forEach(reel => reel.classList.remove('spinning'));
          const results = reels.map(reel => reel.textContent);
          if (results[0] === results[1] && results[1] === results[2]) {
            balance += 50;
            alert('Jackpot! +$50');
          } else if (results[0] === results[1] || results[1] === results[2] || results[0] === results[2]) {
            balance += 10;
            alert('Win! +$10');
          }
          updateBalance();
        }
      }, 100);
    });

    document.getElementById('openSlotLink').addEventListener('click', () => {
      slotModal.style.display = 'block';
    });
    document.getElementById('closeSlot').addEventListener('click', () => {
      slotModal.style.display = 'none';
    });
  </script>
</body>
</html>
