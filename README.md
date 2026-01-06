# ideal-barnacle
BTC Dealer Gamma Exposure (GEX) Model
This model computes and visualises dealer Net Gamma Exposure (GEX) in BTC options using live data from Deribit.
Its purpose is to identify price regimes, volatility behavior, and forced hedging flows driven by options dealers.

The framework is designed to answer:
-When will BTC trend vs mean-revert?
-Where are acceleration / trap levels?
-Why do certain strikes magnetise price into expiry?

Gamma Exposure (GEX) measures how much dealers must buy or sell BTC futures as spot moves.

From a dealer perspective:

Dealers typically sell options to clients

This leaves them short gamma

They must delta-hedge dynamically

This hedging behavior directly impacts spot price action.

Dealer Behaviour by Gamma Regime
Regime	Dealer Action              	            Market Effect
Net Positive Gamma	Sell rips, buy dips	       Mean reversion, suppressed volatility
Net Negative Gamma	Buy rips, sell dumps	      Momentum, trend acceleration

Data Ingestion (Deribit API)

Fetches:

BTC spot price (perpetual)

All live BTC option instruments

Open Interest

Implied Volatility

Expiry dates

Output:
options_df — full options universe
spot_price — current BTC price


The Gamma Flip is the strike where:
Net GEX crosses from negative → positive
Interpretation:
Above flip → mean reversion regime
Below flip → momentum regime

This level defines market structure, not direction.

Trap Levels (High |GEX|)
Trap levels are strikes with:
Extremely large absolute GEX
Heavy open interest concentration
These levels often act as:
Pinning zones into expiry
Acceleration triggers if broken
Liquidity magnets
