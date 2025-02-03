<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ethereum Canlı Fiyatı</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
    }
    h1 {
      color: #333;
    }
    #eth-price {
      font-size: 24px;
      font-weight: bold;
      color: #008000;
    }
  </style>
</head>
<body>
  <h1>Ethereum Canlı Fiyatı</h1>
  <div id="eth-price">Yükleniyor...</div>
  <script>
    async function getEthPrice() {
      try {
        const response = await fetch('https://api.coingecko.com/api/v3/simple/price?ids=ethereum&vs_currencies=usd');
        const data = await response.json();
        document.getElementById('eth-price').textContent = '$' + data.ethereum.usd;
      } catch (error) {
        document.getElementById('eth-price').textContent = "Veri alınamadı!";
        console.error("Hata oluştu:", error);
      }
    }
    
    getEthPrice(); // Sayfa açıldığında çalıştır
    setInterval(getEthPrice, 1000); // Her saniye güncelle
  </script>
</body>
</html>
