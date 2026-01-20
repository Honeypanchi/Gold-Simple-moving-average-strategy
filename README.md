# Gold-Simple-moving-average-strategy

## Project overview 
This project uses a quantitative trading strategy for GOLD prices using dual moving average crossover logic. The goal is to maximise wealth by investing only during confirmed uptrends, while transitioning to a cash or hold position, or selling in times of downtrends, thereby exiting the market.

## Strategy logic
The strategy is built on trend following using two simple moving averages to determine entry and exit points.

* **Fast SMA (10-day):** acts as the short-term, faster-paced average, captures short-term price momentum. 
* **Slow SMA (30 Day):** acts as a longer-term, slower average, showing broader market direction lagging behind the faster one.
*Rules* 
* **Buy signal:** Triggered when the 10-Day SMA crosses above the 30-day SMA
* **Sell Signal:** Triggered when the 10-Day SMA crosses below the 30-Day SMA  
* **Position:** When a sell signal is active, the strategy exits the market and hold 100% cash(wealth stays flat until the next buy signal)

 ## Technical Implementation
The backtesting is developed by using the following libraries
* yfinance: For downloading historical Gold price data.
*  pandas: For data manipulation and vector-based signal calculations.
*  matplotlib: For visualising the logic and performance results.

## Key code features
* **Signal shifting:** The strategy accounts for the "Look ahead bias" by shifting signals by one day(.shift(1))
* **Wealth compounding:** Uses the cumulative product of daily returns (.cumprod()) to simulate the growth of 1$ invested at the start of the period.
* **Event marking:** Automatically stamps "Buy" (green up-triangle) and "Sell" (Red Down-Triangle) markers on the price chart exactly at the crossover points.
  ## Backtest Visualisation
  The project creates a dual plot visualisation.
  * **Top chart (Logic):** Displays the Gold closing price alongside the Fast and Slow SMAs. This allows for immediate verification of the crossover logic.
  * **Bottom Chart (Performance):** Compares the Strategy Wealth against a standard Buy & Hold benchmark. This highlights the strategy's ability to avoid "drawdowns" (market crashes).
    ## Key findings
 * **Flat wealth periods:** One of the most critical features is the "Flat line" in the wealth curve, which proves the strategy performs well in times of crashes and market decline and creates a hedge against the market.
 * **Following the trend:** model follows the trend, the market is presumed to be heading, creating a significant reason for buying or selling to match the trend.
      
Disclaimer
This project is for **educational and research purposes only**. 
Trading gold and other financial instruments involves significant risk. 
Past performance is not indicative of future results. 
Always perform your own due diligence before making investment decisions
