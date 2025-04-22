<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Claybie Mug Customizer</title>
  <style>
    body {
      font-family: 'Arial Rounded MT Bold', sans-serif;
      background-color: #fdf6ee;
      color: #800020;
      margin: 0;
      padding: 0;
    }
    header, footer {
      background-color: #800020;
      color: #fff;
      text-align: center;
      padding: 1rem;
    }
    main {
      padding: 2rem;
    }
    section {
      margin-bottom: 2rem;
    }
    .question {
      margin-bottom: 1.5rem;
    }
    label, select, input, textarea {
      display: block;
      margin: 0.5rem 0;
      font-size: 1rem;
    }
    input[type="file"], input[type="text"], input[type="number"], input[type="email"], textarea {
      padding: 0.5rem;
      width: 100%;
      box-sizing: border-box;
    }
    .price {
      font-weight: bold;
      font-size: 1.2rem;
      margin-top: 1rem;
    }
    .button {
      background-color: #800020;
      color: #fff;
      padding: 0.75rem 1.5rem;
      border: none;
      cursor: pointer;
      font-size: 1rem;
    }
    .button:hover {
      background-color: #a52a2a;
    }
    .hidden {
      display: none;
    }
  </style>
  <script>
    const priceMap = {
      '1-portrait': 11.63,
      '2-portrait': 21.01,
      'small-bow': 5.83,
      '3-bows': 9.34,
      'heart': 3.50,
      'cherry': 8.17,
      'strawberry': 7.01,
      'cat-footprint': 11.68,
      'dog-footprint': 11.68,
      'teddy-bear': 9.34,
      'butterfly': 7.01,
      'giant-bow': 17.51,
      'inside-bow': 3.50,
      'inside-heart': 2.34,
      'inside-cherry': 5.84,
      'inside-strawberry': 5.84,
      'inside-cat-footprint': 3.50,
      'inside-dog-footprint': 3.50,
      'inside-cat': 11.68,
      'inside-dog': 11.68,
      'inside-butterfly': 7.01,
      'handle-bow': 7.01,
      'handle-cat': 9.34,
      'handle-dog': 9.34,
      'text-inside': 5.84,
      'text-outside': 8.17,
      'text-both': 11.68
    };function updatePrice() {
  let totalPrice = 46.69;
  const checkboxes = document.querySelectorAll('input[type="radio"]:checked, input[type="checkbox"]:checked');
  checkboxes.forEach(cb => {
    const id = cb.value;
    if (priceMap[id]) totalPrice += priceMap[id];
  });
  document.getElementById('priceDisplay').textContent = `Total Price: $${totalPrice.toFixed(2)}`;

  const portrait = document.querySelector('input[name="portrait"]:checked')?.value;
  document.getElementById('portraitUpload').classList.toggle('hidden', !portrait);
  document.getElementById('portraitFile').required = !!portrait;

  const textChoice = document.querySelector('input[name="text"]:checked')?.value;
  document.getElementById('textEntry').classList.toggle('hidden', !textChoice);
  document.getElementById('textInput').required = !!textChoice;
}

document.addEventListener('DOMContentLoaded', () => {
  document.querySelectorAll('input[type="radio"], input[type="checkbox"]').forEach(input => {
    input.addEventListener('change', updatePrice);
  });
  updatePrice();
});

  </script>
</head>
<body>
  <header>
    <h1>Welcome to Claybie</h1>
  </header>
  <main>
    <section>
      <p>At Claybie, your mug becomes your world ✨<br>
      We turn cozy cups into magical moments—with Ghibli-style portraits 🌸, anime character vibes 🎌, and even designs inspired by your fave K-pop idol 🎤.<br>
      Everything’s handmade, personalized, and totally aesthetic ☁️.<br>
      So if you’ve ever dreamed of sipping from a cup that looks like it walked out of a Studio Ghibli scene or your favourite idols' MV—welcome home.</p>
    </section>
    <section>
      <div class="question">
        <label><strong>Portrait:</strong></label>
        <label><input type="radio" name="portrait" value="1-portrait" /> 1 Portrait</label>
        <label><input type="radio" name="portrait" value="2-portrait" /> 2 Portraits</label>
        <div id="portraitUpload" class="hidden">
          <label>Upload Photo(s): <input type="file" id="portraitFile" accept="image/*" /></label>
        </div>
      </div>
      <div class="question">
        <label><strong>Extras:</strong></label>
        <label><input type="checkbox" value="small-bow" /> Small Bow</label>
        <label><input type="checkbox" value="3-bows" /> 3 Bows</label>
        <label><input type="checkbox" value="heart" /> Heart</label>
        <label><input type="checkbox" value="cherry" /> Cherry</label>
        <label><input type="checkbox" value="strawberry" /> Strawberry</label>
        <label><input type="checkbox" value="cat-footprint" /> Cat Footprint</label>
        <label><input type="checkbox" value="dog-footprint" /> Dog Footprint</label>
        <label><input type="checkbox" value="teddy-bear" /> Teddy Bear</label>
        <label><input type="checkbox" value="butterfly" /> Butterfly</label>
      </div>
      <div class="question">
        <label><strong>Text Options:</strong></label>
        <label><input type="radio" name="text" value="text-inside" /> Text Inside</label>
        <label><input type="radio" name="text" value="text-outside" /> Text Outside</label>
        <label><input type="radio" name="text" value="text-both" /> Text Both</label>
        <div id="textEntry" class="hidden">
          <label>Enter Text: <input type="text" id="textInput" /></label>
        </div>
      </div>
      <div class="price" id="priceDisplay">Total Price: $46.69</div>
      <button class="button" onclick="alert('Your mug has been customized!')">Submit</button>
    </section>
  </main>
  <footer>
    <p>© 2025 Claybie. All rights reserved.</p>
  </footer>
</body>
</html>
