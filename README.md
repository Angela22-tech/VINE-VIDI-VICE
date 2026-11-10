# VINE-VIDI-VICE
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>My Market News</title>
  <style>
    body { font-family: sans-serif; background: #111; color: #eee; max-width: 600px; margin: auto; padding: 16px; }
    a { color: #6cf; display: block; padding: 8px 0; }
    .row { display: flex; justify-content: space-between; padding: 6px 0; border-bottom: 1px solid #333; }
  </style>
</head>
<body>
  <h1>My Market News</h1>

  <h2>Live crypto prices</h2>
  <div id="prices">Loading...</div>

  <h2>Stock news</h2>
  <a href="https://finance.yahoo.com">Yahoo Finance</a>
  <a href="https://www.cnbc.com/markets/">CNBC Markets</a>

  <h2>Crypto news</h2>
  <a href="https://www.coindesk.com">CoinDesk</a>
  <a href="https://cointelegraph.com">Cointelegraph</a>

  <script>
    fetch("https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana&vs_currencies=usd")
      .then(r => r.json())
      .then(d => {
        document.getElementById("prices").innerHTML = Object.keys(d)
          .map(k => `<div class="row"><span>${k}</span><span>$${d[k].usd}</span></div>`)
          .join("");
      })
      .catch(() => { document.getElementById("prices").textContent = "Could not load prices."; });
  </script>
</body>
</html>
