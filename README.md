# Auctus
Software for structured accumulation.

## Requirements
* extensible, few assumptions, minimize boilerplate
* Assets
  * stocks
  * crypto
  * options
  * FOREX
* easily convert backtesting strategies to live trading
* scheduling logic (market open/close, specific time). like quantopian's zipline
    * part of framework (asyncio?) or left to algo implementer?
    * schedule strategy functions and schedule strategies
    * strategies control when they are run, ex. always on OR daily, etc.
* collect, organize, and present holdings from multiple portfolios. you might trade stocks with alpaca,
and options with IB. This data is more useful if collated.
* design s.t. strategies CAN (not have to) be api-agnostic
* should be tolerant to computer shutting down mid-run
  * leave this to implementer, or include something on the framework side?
## Components
* Data API
```
data_api = Datasource.get_api('polygon')
```
OR
```
from data import polygon_api as data_api
```
* Brokerage API
* Backtesting framework
* Live trading framework
* Analysis
    * return, risk-adjusted return
    * by-strategy analysis
* Output
    * email
    * text
    * csv
* Strategy (implemented by user)
    * def run(): runs algo
    * def get_state(): returns state info. all strategies should have the same state info. 
    potentially allow for custom state. What should be in state?
```
strat = Strategy()
strat.run()
...
analyzer = Analyzer()
analysis = analyzer.analyze(strategy.get_state())
``` 
* utils: common calculations

## Development Guide
* How to contribute
* Required tests
