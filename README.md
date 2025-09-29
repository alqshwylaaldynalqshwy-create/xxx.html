<!DOCTYPE html>a
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>متجر علاء الدين القشوي للأجهزة</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      direction: rtl;
      background: #f4f7f6;
      padding: 20px;
      text-align: center;
      color: #333;
    }
    .container {
      max-width: 600px;
      margin: 0 auto;
      background: #fff;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
    h1 {
      color: #3498db;
      font-size: 2em;
      margin-bottom: 25px;
      border-bottom: 2px solid #ecf0f1;
      padding-bottom: 10px;
    }
    h2, h3 {
      color: #2c3e50;
      margin-top: 25px;
      font-size: 1.3em;
    }
    select, input[type="text"], input[type="number"], button {
      margin: 10px 0;
      padding: 12px;
      width: 100%;
      border: 1px solid #ccc;
      border-radius: 6px;
      box-sizing: border-box; 
      font-size: 1em;
    }
    button {
      background-color: #2ecc71;
      color: white;
      cursor: pointer;
      border: none;
      transition: background-color 0.3s ease;
      margin-top: 20px;
    }
    button:hover {
      background-color: #27ae60;
    }
    .price-section {
      margin-top: 25px;
      padding: 15px;
      border-radius: 8px;
    }
    #price-result {
      font-weight: bold;
      font-size: 1.5em;
      color: #e74c3c;
    }
    #purchase-details {
      border-top: 1px dashed #ccc;
      padding-top: 20px;
      margin-top: 20px;
      display: none;
    }
    .available {
      background-color: #d4edda;
      color: #155724;
    }
    .not-available {
      background-color: #f8d7da;
      color: #721c24;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>مرحباً بك في متجر الأجهزة، علاء الدين القشوي 🌟</h1>

    <h2>اختر مواصفات جهازك</h2>

    <label for="device">أنواع الجهازات:</label>
    <select id="device">
      <option value="1">Thincpad</option>
      <option value="2">HP</option>
      <option value="3">Del</option>
      <option value="4">Lenvo</option>
      <option value="5">Samsung</option>
      <option value="6">Apple</option>
      <option value="7">Toshiba</option>
    </select>

    <label for="ram">الرام:</label>
    <select id="ram">
      <option value="8">RAM16</option>
      <option value="9">RAM8</option>
      <option value="10">RAM4</option>
      <option value="11">RAM32</option>
      <option value="12">RAM12</option>
    </select>

    <label for="core">المعالج:</label>
    <select id="core">
      <option value="13">CORE i7</option>
      <option value="14">CORE i5</option>
      <option value="15">CORE i2</option>
    </select>

    <label for="memory">الذاكرة:</label>
    <select id="memory">
      <option value="16">124G</option>
      <option value="17">256G</option>
      <option value="18">512G</option>
      <option value="19">1024G</option>
    </select>

    <button onclick="calculatePrice()">تحقق من التوفر واحسب السعر</button>

    <div class="price-section" id="price-section">
      <p id="price-result"></p>
      <button id="buy-button" style="display: none; background-color: #f39c12;" onclick="showPurchaseForm()">أريد الشراء!</button>
    </div>

    <form id="purchase-details" action="https://formsubmit.co/alqshwylaaldynalqshwy@gmail.com" method="POST">
      <h3>معلومات الطلب والتوصيل</h3>
      <p style="color: red; font-size: 0.9em;">(يرجى ملاحظة: هذا النموذج بسيط ويناسب طلبات الاستفسار، وليس لعمليات دفع آمنة.)</p>

      <input type="text" name="نوع الجهاز و مواصفاته" id="specs-summary" hidden>
      
      <input type="text" name="رمز الدولة" placeholder="رمز الدولة (+967 لليمن)" required>
      <input type="number" name="رقم الهاتف" placeholder="رقم الهاتف" required>
      <input type="text" name="العنوان التفصيلي" placeholder="العنوان التفصيلي" required>

      <button type="submit">تأكيد وإرسال الطلب</button>
    </form>
  </div>

  <script>
    let finalPrice = 0; 

    function getSpecsText() {
        const deviceText = document.getElementById("device").options[document.getElementById("device").selectedIndex].text;
        const ramText = document.getElementById("ram").options[document.getElementById("ram").selectedIndex].text;
        const coreText = document.getElementById("core").options[document.getElementById("core").selectedIndex].text;
        const memoryText = document.getElementById("memory").options[document.getElementById("memory").selectedIndex].text;
        return `${deviceText} / ${ramText} / ${coreText} / ${memoryText}`;
    }

    function calculatePrice() {
      const device = parseInt(document.getElementById("device").value);
      const ram = parseInt(document.getElementById("ram").value);
      const core = parseInt(document.getElementById("core").value);
      const memory = parseInt(document.getElementById("memory").value);
      
      const resultDiv = document.getElementById("price-result");
      const priceSection = document.getElementById("price-section");
      const buyButton = document.getElementById("buy-button");
      const purchaseForm = document.getElementById("purchase-details");

      buyButton.style.display = 'none';
      purchaseForm.style.display = 'none';
      
      // منطق التحقق من التوفر
      if ((device === 1 || device === 2) &&
          (ram === 8 || ram === 9) &&
          (core === 13 || core === 15) &&
          (memory === 16 || memory === 17)) {
        
        finalPrice = Math.floor(Math.random() * (500 - 200 + 1)) + 200;
        
        resultDiv.innerText = `السعر التقديري: $${finalPrice}`;
        priceSection.className = 'price-section available';
        
        // إظهار زر الشراء
        buyButton.style.display = 'block';
        
        // ملء حقل ملخص المواصفات المخفي لإرساله مع الطلب
        document.getElementById("specs-summary").value = `${getSpecsText()} - السعر: $${finalPrice}`;

      } else {
        resultDiv.innerText = "طلبك غير متوفر حالياً بالمواصفات المحددة";
        priceSection.className = 'price-section not-available';
        buyButton.style.display = 'none';
      }
    }

    function showPurchaseForm() {
        document.getElementById("purchase-details").style.display = 'block';
        document.getElementById("buy-button").style.display = 'none';
    }
  </script>
</body>
</html><!DOCTYPE html>a
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>متجر علاء الدين القشوي للأجهزة</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      direction: rtl;
      background: #f4f7f6;
      padding: 20px;
      text-align: center;
      color: #333;
    }
    .container {
      max-width: 600px;
      margin: 0 auto;
      background: #fff;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
    h1 {
      color: #3498db;
      font-size: 2em;
      margin-bottom: 25px;
      border-bottom: 2px solid #ecf0f1;
      padding-bottom: 10px;
    }
    h2, h3 {
      color: #2c3e50;
      margin-top: 25px;
      font-size: 1.3em;
    }
    select, input[type="text"], input[type="number"], button {
      margin: 10px 0;
      padding: 12px;
      width: 100%;
      border: 1px solid #ccc;
      border-radius: 6px;
      box-sizing: border-box; 
      font-size: 1em;
    }
    button {
      background-color: #2ecc71;
      color: white;
      cursor: pointer;
      border: none;
      transition: background-color 0.3s ease;
      margin-top: 20px;
    }
    button:hover {
      background-color: #27ae60;
    }
    .price-section {
      margin-top: 25px;
      padding: 15px;
      border-radius: 8px;
    }
    #price-result {
      font-weight: bold;
      font-size: 1.5em;
      color: #e74c3c;
    }
    #purchase-details {
      border-top: 1px dashed #ccc;
      padding-top: 20px;
      margin-top: 20px;
      display: none;
    }
    .available {
      background-color: #d4edda;
      color: #155724;
    }
    .not-available {
      background-color: #f8d7da;
      color: #721c24;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>مرحباً بك في متجر الأجهزة، علاء الدين القشوي 🌟</h1>

    <h2>اختر مواصفات جهازك</h2>

    <label for="device">أنواع الجهازات:</label>
    <select id="device">
      <option value="1">Thincpad</option>
      <option value="2">HP</option>
      <option value="3">Del</option>
      <option value="4">Lenvo</option>
      <option value="5">Samsung</option>
      <option value="6">Apple</option>
      <option value="7">Toshiba</option>
    </select>

    <label for="ram">الرام:</label>
    <select id="ram">
      <option value="8">RAM16</option>
      <option value="9">RAM8</option>
      <option value="10">RAM4</option>
      <option value="11">RAM32</option>
      <option value="12">RAM12</option>
    </select>

    <label for="core">المعالج:</label>
    <select id="core">
      <option value="13">CORE i7</option>
      <option value="14">CORE i5</option>
      <option value="15">CORE i2</option>
    </select>

    <label for="memory">الذاكرة:</label>
    <select id="memory">
      <option value="16">124G</option>
      <option value="17">256G</option>
      <option value="18">512G</option>
      <option value="19">1024G</option>
    </select>

    <button onclick="calculatePrice()">تحقق من التوفر واحسب السعر</button>

    <div class="price-section" id="price-section">
      <p id="price-result"></p>
      <button id="buy-button" style="display: none; background-color: #f39c12;" onclick="showPurchaseForm()">أريد الشراء!</button>
    </div>

    <form id="purchase-details" action="https://formsubmit.co/alqshwylaaldynalqshwy@gmail.com" method="POST">
      <h3>معلومات الطلب والتوصيل</h3>
      <p style="color: red; font-size: 0.9em;">(يرجى ملاحظة: هذا النموذج بسيط ويناسب طلبات الاستفسار، وليس لعمليات دفع آمنة.)</p>

      <input type="text" name="نوع الجهاز و مواصفاته" id="specs-summary" hidden>
      
      <input type="text" name="رمز الدولة" placeholder="رمز الدولة (+967 لليمن)" required>
      <input type="number" name="رقم الهاتف" placeholder="رقم الهاتف" required>
      <input type="text" name="العنوان التفصيلي" placeholder="العنوان التفصيلي" required>

      <button type="submit">تأكيد وإرسال الطلب</button>
    </form>
  </div>

  <script>
    let finalPrice = 0; 

    function getSpecsText() {
        const deviceText = document.getElementById("device").options[document.getElementById("device").selectedIndex].text;
        const ramText = document.getElementById("ram").options[document.getElementById("ram").selectedIndex].text;
        const coreText = document.getElementById("core").options[document.getElementById("core").selectedIndex].text;
        const memoryText = document.getElementById("memory").options[document.getElementById("memory").selectedIndex].text;
        return `${deviceText} / ${ramText} / ${coreText} / ${memoryText}`;
    }

    function calculatePrice() {
      const device = parseInt(document.getElementById("device").value);
      const ram = parseInt(document.getElementById("ram").value);
      const core = parseInt(document.getElementById("core").value);
      const memory = parseInt(document.getElementById("memory").value);
      
      const resultDiv = document.getElementById("price-result");
      const priceSection = document.getElementById("price-section");
      const buyButton = document.getElementById("buy-button");
      const purchaseForm = document.getElementById("purchase-details");

      buyButton.style.display = 'none';
      purchaseForm.style.display = 'none';
      
      // منطق التحقق من التوفر
      if ((device === 1 || device === 2) &&
          (ram === 8 || ram === 9) &&
          (core === 13 || core === 15) &&
          (memory === 16 || memory === 17)) {
        
        finalPrice = Math.floor(Math.random() * (500 - 200 + 1)) + 200;
        
        resultDiv.innerText = `السعر التقديري: $${finalPrice}`;
        priceSection.className = 'price-section available';
        
        // إظهار زر الشراء
        buyButton.style.display = 'block';
        
        // ملء حقل ملخص المواصفات المخفي لإرساله مع الطلب
        document.getElementById("specs-summary").value = `${getSpecsText()} - السعر: $${finalPrice}`;

      } else {
        resultDiv.innerText = "طلبك غير متوفر حالياً بالمواصفات المحددة";
        priceSection.className = 'price-section not-available';
        buyButton.style.display = 'none';
      }
    }

    function showPurchaseForm() {
        document.getElementById("purchase-details").style.display = 'block';
        document.getElementById("buy-button").style.display = 'none';
    }
  </script>
</body>
</html>
