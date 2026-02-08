<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>MCFA.GEN – Redeem</title>
  <style>
    body {
      background:#0f172a;
      color:white;
      font-family:Arial;
      display:flex;
      justify-content:center;
      align-items:center;
      height:100vh;
    }
    .box {
      background:#1e293b;
      padding:25px;
      border-radius:10px;
      width:360px;
      text-align:center;
    }
    input, button {
      width:100%;
      padding:10px;
      margin-top:10px;
    }
    .msg {
      margin-top:15px;
      font-weight:bold;
    }
    .reward {
      margin-top:15px;
      background:#020617;
      padding:12px;
      border-radius:6px;
      text-align:left;
      display:none;
    }
    .label {
      color:#94a3b8;
      font-size:13px;
    }
  </style>
</head>
<body>

<div class="box">
  <h2>MCFA.GEN</h2>

  <input id="code" placeholder="Enter redeem code">
  <button onclick="redeem()">Redeem</button>

  <div id="msg" class="msg"></div>

  <!-- REWARD BOX -->
  <div id="rewardBox" class="reward">
    <div class="label">✉️ Email</div>
    <div>paveromao@hotmail.com
</div>

    <div class="label" style="margin-top:8px;">🔑 Password</div>
    <div>Dani7rui#</div>

    <div class="label" style="margin-top:10px;">
      
    </div>
  </div>
</div>

<script>
  function redeem() {
    const code = document.getElementById("code").value.trim();
    const msg = document.getElementById("msg");
    const reward = document.getElementById("rewardBox");

    let codes = JSON.parse(localStorage.getItem("MCFA_CODES")) || {};

    reward.style.display = "none";

    if (!(code in codes)) {
      msg.style.color = "red";
      msg.innerText = "❌ Invalid or out of stock code";
      return;
    }

    if (codes[code] === "used") {
      msg.style.color = "red";
      msg.innerText = "❌ This code has already been redeemed";
      return;
    }

    codes[code] = "used";
    localStorage.setItem("MCFA_CODES", JSON.stringify(codes));

    msg.style.color = "lightgreen";
    msg.innerText = "✅ Code redeemed successfully!";

    // SHOW DEMO REWARD
    reward.style.display = "block";
  }
</script>

</body>
</html>
