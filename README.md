# 🪙 Cryptocurrency Performance Analyzer

This project is a real-time cryptocurrency monitoring dashboard built in **Power BI** using data from the [CoinGecko API](https://www.coingecko.com/en/api). The dashboard provides insights into market trends, top-performing and underperforming coins, market capitalization, and trading volume across 250 cryptocurrencies.

---

## 📊 Features

- **Live API Integration** using CoinGecko API
- **Top 4 KPIs**:
  - 🥇 Top Coin by Market Cap
  - 🚀 Top Gainer (24h % increase)
  - 📉 Top Loser (24h % decrease)
  - 💰 Total Market Volume (USD)
 
- **Interactive Visualizations**:
  - Line chart for price % change (24h)
  - Combo chart for current price & price change %
  - Donut chart for total trading volume
  - Bar chart for top 5 coins by market cap
- **Slicer** to filter dashboard by coin names
- Professional dark theme with clear data labels

---

## 🔗 API Used

**Endpoint**:  
```
https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd
```

**Returned JSON Includes**:
- `id`, `symbol`, `name`
- `current_price`, `market_cap`, `market_cap_rank`
- `total_volume`, `high_24h`, `low_24h`
- `price_change_percentage_24h`

---

## ⚙️ Technologies Used

- **Power BI Desktop**
- **DAX** (for KPI calculations)
- **Power Query M** (for API data transformation)

---

## 🧮 Key DAX Measures

```dax
-- Top Coin by Market Cap
Top Coin = 
VAR TopCoin =
    TOPN(1, ALL(CryptoData), CryptoData[market_cap], DESC)
RETURN
    MAXX(TopCoin, CryptoData[name])

-- Top Gainer Coin
Top Gainer Coin = 
VAR Gainer =
    TOPN(1, ALL(CryptoData), CryptoData[price_change_percentage_24h], DESC)
RETURN
    MAXX(Gainer, CryptoData[name])

-- Top Loser Coin
Top Loser Coin = 
VAR Loser =
    TOPN(1, ALL(CryptoData), CryptoData[price_change_percentage_24h], ASC)
RETURN
    MAXX(Loser, CryptoData[name])

-- Total Market Volume
Total Volume = 
SUM(CryptoData[total_volume])
```

---

## 🔄 Refresh Instructions

To refresh the dashboard with the latest API data:
1. Open the Power BI file
2. Click **Home → Refresh**
3. Optionally set up **scheduled refresh** via Power BI Service

---

## 📷 Screenshot

![Dashboard Screenshot](./assets/crypto_dashboard.png)

---

## 📁 Project Structure

```
📦 Cryptocurrency Performance Analyzer
├── README.md
├── Crypto_Performance_Analyzer.pbix
├── assets
│   └── crypto_dashboard.png
```

---

## ✍️ Author

**D Charan Teja**  
Aspiring Data Analyst | Power BI Enthusiast | API Integration Projects

---

## 📜 License

This project is open-source and free to use for educational and personal purposes.
