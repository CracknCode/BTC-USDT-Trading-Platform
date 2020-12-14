



## Binance Part 1 - Websockets ana realtime Lightweight charts 

* What is binance and how does it compare to other exchanges?
  Binance is one of the leading cryptocurrency exchanges with a 
  large list of very volatile small cap coins, as well as 
  high volume pairs like BTCUSD.
  Not only can you trade sopt markets you can trade with margin, 
  or the futures market using up to 120X on the BTCUSDT pair. 
* Why crypto? Markets open 24/7 (nights and weekends) New asset
  class with lots of room for growth, currently still under a 
  trillion dollar market cap.
  *High risk High Reward*
________________________________________________________________
* wscat - connect to websocket from the command line

* wss://stream.binance.com:9443/ws/btcusdt@trade

The Kline/Candlestick Stream push updates to the current klines/candlestick every second.

Kline/Candlestick chart intervals:

m -> minutes; h -> hours; d -> days; w -> weeks; M -> months

1m
3m
5m
15m
30m
1h
2h
4h
6h
8h
12h
1d
3d
1w
1M
Stream Name: <symbol>@kline_<interval>


_________________Example of unparsed 5min BTCUSDT websocket____________________

command line prompt =
$  wscat -c wss://stream.binance.com:9443/ws/btcusdt@kline_5m

{"e": "kline", 
"E": 1607919090903,
"s": "BTCUSDT",
"k":{
    "t": 1607919000000,
    "T": 1607919299999,
    "s": "BTCUSDT",
    "i": "5m",
    "f": 506578301,
    "L": 506578608,
    "o": "19278.17000000",
    "c": "19275.12000000",
    "h": "19278.17000000",
    "l": "19275.11000000",
    "v": "10.21395200",
    "n": 308,
    "x": false,
    "q": "196892.83140665",
    "V": "4.35188900",
    "Q": "83889.44860309",
    "B": "0"}}

Payload..........................
{
  "e": // Event type
  "E": // Event time
  "s": // Symbol
  "k": {
    "t": // Kline start time
    "T": // Kline close time
    "s": // Symbol
    "i": // Interval
    "f": // First trade ID
    "L": // Last trade ID
    "o": // Open price
    "c": // Close price
    "h": // High price
    "l": // Low price
    "v": // Base asset volume
    "n": // Number of trades
    "x": // Is this kline closed?
    "q": // Quote asset volume
    "V": // Taker buy base asset volume
    "Q": // Taker buy quote asset volume
    "B": // Ignore
  }
}


* capture output to a file 

$  wscat -c wss://stream.binance.com:9443/ws/btcusdt@kline_5m | tee dataset_5m.txt


* connect to a websocket from the web / Javascript

https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications

* lightweight charts - create real-time candlestick chart similar to tradingView
* UI to check indicators (eg.RSI), configure values, configure alerts/ 
  notifications

  ## Binance Part 2 - Technical Analysis with Python and TALib

  * connect to websockets from python, write candlestick data to CSV
  * download some historical data using a REST API
  * install TALib, try some indicators on a datatest 

  ## Binance Part 3 - Backtesting with Backtrader and TALib indicators

  * teat some indicators against some historical dataset
  * plot some pretty charts with buy and sell points 
  
 