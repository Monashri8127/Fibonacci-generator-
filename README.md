# Fibonacci-generator-import yfinance as yf
import matplotlib.pyplot as plt

data = yf.download('AAPL', start='2023-01-01', end='2024-01-01')
high, low = data['Close'].max(), data['Close'].min()
diff = high - low

levels = [high - diff * r for r in [0, 0.236, 0.382, 0.5, 0.618, 0.786, 1.0]]

plt.figure(figsize=(12,6))
plt.plot(data['Close'], label='AAPL Close', color='blue')
for lvl in levels:
    plt.axhline(lvl, linestyle='--', alpha=0.6)
plt.title('AAPL Fibonacci Retracement')
plt.legend()
plt.grid()
plt.tight_layout()
plt.show()
