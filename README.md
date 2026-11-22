Market-Making Simulation
A Python simulation of a market maker quoting a bid and an ask against random and informed traders. I built it to understand how a trading firm earns money from the spread, and how adverse selection and inventory risk eat into that.
The question
How does the size of the bid-ask spread trade off against adverse selection? A tight spread attracts more trades but loses money to traders who know where the price is heading. A wide spread protects against those traders but scares off the harmless ones.
How it works
• True price: a hidden value that moves as a random walk.
• Quotes: the market maker posts a bid below and an ask above its estimate of fair value. The gap is the spread.
• Order flow: each step, a buyer, a seller or nobody arrives at random. A fraction of traders are informed and only trade when they know the price is about to move past our quote.
• Inventory: buying and selling changes the position held. Quotes are shifted slightly to push inventory back toward zero.
• Profit: cash plus inventory valued at the current true price.
All data is simulated, so there is no market data to download.
Results
Chart: !profit against spread (file: spread_vs_profit.png)
Finding 1: Profit peaked at a spread of about 0.50. Below that, informed traders caused losses. Above it, trading volume dried up
Finding 2: When buyers arrived more often than sellers (P_buyer 0.50, P_seller 0.30), the market maker kept selling and ended with a short inventory of -505 units. Profit was 316.17, compared with [X] when both probabilities were 0.30. One-sided order flow leaves the market maker exposed to price moves, which is the inventory risk the quote-shifting rule is meant to reduce
• Real order flow is not random. Trades cluster and react to news.
• Real markets have many competing market makers, not one.
• The price model is a simple random walk with constant volatility.
• Informed traders are modelled crudely.
Run it yourself
1.  Open market_making.ipynb in Google Colab, or run it locally with Python 3.
2.  Install the libraries if needed: numpy, pandas and matplotlib.
3.  Run all cells. Change the settings at the top to try different spreads and trader mixes.
Possible next steps
• Let volatility change over time.
• Make informed traders smarter or rarer and see how the best spread moves.
• Compare strategies on profit divided by risk.
