<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Joanne's Gift Baskets</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #e6f7ff;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #66b2ff;
            color: white;
            padding: 20px;
            text-align: center;
            border-bottom: 5px solid #4d94cc;
        }
        h1 {
            margin: 0;
            font-size: 2.5em;
            font-family: "Georgia", serif;
            color: white;
        }
        p {
            font-size: 1em;
            color: #dce7f8;
            margin: 10px 0;
        }
        .container {
            padding: 20px;
            max-width: 95%;
            margin: 0 auto;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border: 1px solid #66b2ff;
        }
        .form-section {
            margin: 20px 0;
        }
        label {
            font-weight: bold;
            margin-top: 10px;
            display: block;
            color: #4da6ff;
        }
        select, input, textarea, button {
            width: 100%;
            margin-top: 8px;
            padding: 8px;
            font-size: 0.9em;
            border: 1px solid #66b2ff;
            border-radius: 8px;
            background-color: #f9faff;
        }
        button {
            background-color: #4da6ff;
            color: white;
            font-weight: bold;
            cursor: pointer;
            border-radius: 20px;
            border: none;
            padding: 15px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
            transition: transform 0.2s, background-color 0.3s ease;
        }
        button:hover {
            background-color: #357ab8;
            transform: scale(1.1);
        }
        textarea {
            height: 100px;
        }
        .checkbox-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }
        .checkbox-group label {
            font-size: 0.9em;
            color: #333;
        }
        footer {
            text-align: center;
            padding: 10px;
            background-color: #66b2ff;
            color: white;
        }
    </style>
</head>
<body>

<header>
    <h1>Joanne's Gift Baskets</h1>
    <p>Beautiful baskets for all occasions. Pickup in Plainville, CT.</p>
</header>

<div class="container">
    <form id="basketForm">
        <div class="form-section">
            <h2>Basket Details</h2>

            <label for="theme">Choose a Theme</label>
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

            <label for="products">Select Products</label>
            <div class="checkbox-group" id="products">
                <label><input type="checkbox" value="Candles"> Candles</label>
                <label><input type="checkbox" value="Fruit"> Fresh Fruit</label>
                <label><input type="checkbox" value="Mixed Nuts"> Mixed Nuts</label>
                <label><input type="checkbox" value="Crackers"> Gourmet Crackers</label>
                <label><input type="checkbox" value="Chips"> Artisan Chips</label>
                <label><input type="checkbox" value="Cheese"> Premium Cheeses</label>
                <label><input type="checkbox" value="Wine"> Wine</label>
                <label><input type="checkbox" value="Chocolate"> Assorted Chocolates</label>
                <label><input type="checkbox" value="Coffee"> Gourmet Coffee</label>
                <label><input type="checkbox" value="Tea"> Specialty Teas</label>
            </div>

            <label for="message">Special Message</label>
            <textarea id="message" name="message" placeholder="Write your personalized message here"></textarea>
        </div>

        <div class="form-section">
            <h2>Contact Information</h2>
            <p class="info-note">Submit your quote request. Joanne will contact you to finalize payment and pickup details.</p>

            <label for="name">Your Name</label>
            <input type="text" id="name" name="name" required>

            <label for="phone">Your Phone Number</label>
            <input type="tel" id="phone" name="phone" required>

            <label for="email">Your Email</label>
            <input type="email" id="email" name="email" required>
        </div>

        <button type="submit">Submit</button>
    </form>
</div>

<footer>
    <p>Joanne's Gift Baskets © 2024 | Crafted with love in Hartford County.</p>
</footer>

<script>
    document.getElementById('basketForm').addEventListener('submit', function(event) {
        event.preventDefault();

        const name = document.getElementById('name').value;
        const phone = document.getElementById('phone').value;
        const email = document.getElementById('email').value;
        const theme = document.getElementById('theme').value;
        const products = Array.from(document.querySelectorAll('#products input:checked'))
                            .map(checkbox => checkbox.value)
                            .join(', ');
        const message = document.getElementById('message').value || 'No special message.';

        const subject = encodeURIComponent('New Basket Request');
        const body = encodeURIComponent(
            `=== Customer Details ===\n` +
            `Name: ${name}\n` +
            `Phone: ${phone}\n` +
            `Email: ${email}\n\n` +
            `=== Basket Details ===\n` +
            `Theme: ${theme}\n` +
            `Products: ${products}\n` +
            `Special Message: ${message}`
        );

        // Open email client
        window.location.href = `mailto:jbtr9@comcast.net?subject=${subject}&body=${body}`;
    });
</script>

</body>
</html>
