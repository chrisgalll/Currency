# Currency
Creating a fully functional code for controlling the exchange rate of national currencies on the market and the price sale and purchase on a crypto exchange like Binance would be a complex task involving real-time data retrieval and analysis. 
import requests

# API endpoints for retrieving exchange rates and cryptocurrency prices
exchange_rates_api = "https://api.exchangerate-api.com/v4/latest/USD"
cryptocurrency_prices_api = "https://api.binance.com/api/v3/ticker/price"

# Fetch exchange rates
response = requests.get(exchange_rates_api)
exchange_rates = response.json()["rates"]

# Fetch cryptocurrency prices
response = requests.get(cryptocurrency_prices_api)
cryptocurrency_prices = response.json()

# Compare and calculate differences
table_data = []
for currency, rate in exchange_rates.items():
    if currency in cryptocurrency_prices:
        crypto_price = cryptocurrency_prices[currency]
        difference = float(rate) - float(crypto_price)
        table_data.append((currency, rate, crypto_price, difference))

# Display data in a tabular format
print("Currency Pair\tExchange Rate\tCrypto Price\tDifference")
for data in table_data:
    print("\t".join(str(item) for item in data))
