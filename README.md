# kkumi-s-cookie-shop
꾸미가 쿠키를 파는 게임
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>굿쿠키, 베이크마스터</title>
  <style>
    body {
      font-family: sans-serif;
      text-align: center;
      background-color: #fff7f0;
      padding: 20px;
    }
    h1 {
      color: #a0522d;
    }
    .order-box, .bake-box, .result-box {
      margin: 20px auto;
      padding: 20px;
      background: #fff;
      border: 2px solid #d2b48c;
      border-radius: 12px;
      max-width: 500px;
    }
    button {
      padding: 10px 20px;
      margin: 5px;
      border: none;
      border-radius: 8px;
      background-color: #deb887;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    button:hover {
      background-color: #c08040;
    }
  </style>
</head>
<body>
  <h1>굿쿠키, 베이크마스터 🍪</h1>  <div class="order-box">
    <h2>손님 주문</h2>
    <p id="order-text">바닐라 반죽 + 초코칩 + 바삭하게 구워줘요!</p>
  </div>  <div class="bake-box">
    <h2>쿠키 만들기</h2>
    <p><strong>반죽 선택:</strong></p>
    <button onclick="selectOption('dough', '바닐라')">바닐라</button>
    <button onclick="selectOption('dough', '초콜릿')">초콜릿</button><p><strong>토핑 선택:</strong></p>
<button onclick="selectOption('topping', '초코칩')">초코칩</button>
<button onclick="selectOption('topping', '딸기잼')">딸기잼</button>

<p><strong>굽기 정도:</strong></p>
<button onclick="selectOption('bake', '살짝')">살짝</button>
<button onclick="selectOption('bake', '보통')">보통</button>
<button onclick="selectOption('bake', '바삭하게')">바삭하게</button>

<br><br>
<button onclick="submitCookie()">손님에게 제공하기</button>

  </div>  <div class="result-box">
    <h2>손님 평가</h2>
    <p id="result-text">아직 쿠키를 제공하지 않았어요.</p>
  </div>  <script>
    const order = {
      dough: "바닐라",
      topping: "초코칩",
      bake: "바삭하게"
    };

    const player = {
      dough: null,
      topping: null,
      bake: null
    };

    function selectOption(type, value) {
      player[type] = value;
      console.log(`선택됨: ${type} = ${value}`);
    }

    function submitCookie() {
      if (!player.dough || !player.topping || !player.bake) {
        document.getElementById("result-text").innerText = "모든 항목을 선택해주세요!";
        return;
      }

      let score = 0;
      if (player.dough === order.dough) score++;
      if (player.topping === order.topping) score++;
      if (player.bake === order.bake) score++;

      let msg = "";
      if (score === 3) msg = "완벽해요! ⭐⭐⭐";
      else if (score === 2) msg = "거의 맞췄네요! ⭐⭐";
      else if (score === 1) msg = "음... 한 가지만 맞췄네요. ⭐";
      else msg = "다 틀렸어요... 다시 도전해봐요.";

      document.getElementById("result-text").innerText = msg;
    }
  </script></body>
</html>
