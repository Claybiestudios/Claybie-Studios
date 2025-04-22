<!DOCTYPE html><html lang="en"><head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f9f5f0;
      color: #4a1c1c;
      margin: 0;
      padding: 20px;
    }
    h1, h2, h3 {
      color: #8b0000;
    }
    .page {
      display: none;
    }
    .active {
      display: block;
    }
    .question {
      margin-bottom: 20px;
    }
    input[type="text"], input[type="email"], input[type="number"], textarea, select {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
    }
    button {
      padding: 10px 20px;
      background-color: #8b0000;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }
    .price {
      font-size: 20px;
      font-weight: bold;
    }
  </style>
</head><body>
  <div id="page1" class="page active">
    <h1>Welcome to Claybie!</h1>
    <p>
      At Claybie, your mug becomes your world ✨ We turn cozy cups into magical moments—with Ghibli-style portraits 🌸,
      anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤. Everything’s handmade,
      personalized, and totally aesthetic ☁️. So if you’ve ever dreamed of sipping from a cup that looks like it
      walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.
    </p>
    <button onclick="nextPage(2)">Customize Your Mug</button>
  </div>  <form id="customizerForm">
    <div id="page2" class="page">
      <h2>Customize Your Mug</h2>
      <div class="question">
        <label>Want portrait on your mug?</label><br>
        <select id="portraitOption" name="portraitOption" required onchange="togglePortraitUpload()">
          <option value="">Select an option</option>
          <option value="1" data-price="11.63">1 portrait (+$11.63)</option>
          <option value="2" data-price="21.01">2 portraits (+$21.01)</option>
        </select>
      </div>
      <div id="portraitUploadDiv" class="question" style="display: none;">
        <label>Upload your portrait:</label><br>
        <input type="file" id="portraitUpload" name="portraitUpload" accept="image/*" required>
      </div><!-- Additional questions go here with similar structure, each having price impacts -->
  <!-- For brevity, not repeating all here, but it would be similar selects and toggleable inputs -->

  <div class="question">
    <label>Total Price:</label>
    <p class="price" id="totalPrice">$46.69</p>
  </div>
  <button type="button" onclick="nextPage(3)">Proceed to Buyer Info</button>
</div>

<div id="page3" class="page">
  <h2>Your Info</h2>
  <div class="question">
    <label>Full Name</label>
    <input type="text" name="fullName" required>
  </div>
  <div class="question">
    <label>Contact Number</label>
    <input type="text" name="contactNumber" required>
  </div>
  <div class="question">
    <label>Email</label>
    <input type="email" name="email" required>
  </div>
  <div class="question">
    <label>Shipping Address</label>
    <textarea name="address" required></textarea>
  </div>
  <button type="button" onclick="nextPage(4)">Proceed to Payment</button>
</div>

<div id="page4" class="page">
  <h2>Payment</h2>
  <p>Use the following payment methods:</p>
  <ul>
    <li><strong>Google Pay:</strong> 6352177416@ptaxis</li>
    <li><strong>PayPal:</strong> <a href="https://www.paypal.me/KavitaVarma883" target="_blank">Click to Pay</a></li>
  </ul>
  <p>After completing payment, click below:</p>
  <button type="submit">I’ve Paid – Confirm Order</button>
</div>

  </form>  <div id="page5" class="page">
    <h2>Thanks for Ordering!</h2>
    <p>Your order is confirmed. You’re the best!</p>
  </div>  <script>
    let basePrice = 46.69;

    function nextPage(pageNum) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById(`page${pageNum}`).classList.add('active');
      calculateTotal();
    }

    function togglePortraitUpload() {
      const option = document.getElementById('portraitOption').value;
      const uploadDiv = document.getElementById('portraitUploadDiv');
      const uploadInput = document.getElementById('portraitUpload');
      if (option === "1" || option === "2") {
        uploadDiv.style.display = 'block';
        uploadInput.required = true;
      } else {
        uploadDiv.style.display = 'none';
        uploadInput.required = false;
      }
      calculateTotal();
    }

    function calculateTotal() {
      let total = basePrice;
      const selects = document.querySelectorAll('#customizerForm select');
      selects.forEach(select => {
        const option = select.selectedOptions[0];
        if (option && option.dataset.price) {
          total += parseFloat(option.dataset.price);
        }
      });
      document.getElementById('totalPrice').textContent = `$${total.toFixed(2)}`;
    }

    document.getElementById('customizerForm').addEventListener('submit', function (e) {
      e.preventDefault();
      nextPage(5);
    });
  </script></body></html>
