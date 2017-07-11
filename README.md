# marconi  
![marconi](images/marconi.jpeg)  
Poloniex Trading Bot

### Requirements:
__system__:
```
Python 3
Mongodb (running local)
```
__pip__:
```
requests
numpy
bokeh
cherrypy
beautifulsoup4
pymongo
pandas
websocket-client
```

### Mongo database layout:
```
 ( )  = database
(( )) = collection/table
+{ }+ = document

( poloniex )
  |
  | # Built by ticker.py ============================
 (( ticker ))------------+{'_id': str(currencyPair),
  |                        'id': float(),
  |                        'last': float(),
  |                        'lowestAsk': float(),
  |                        'highestBid': float(),
  |                        'percentChange': float(),
  |                        'baseVolume': float(),
  |                        'quoteVolume': float(),
  |                        'isFrozen': float(),
  |                        'high24hr': float(),
  |                        'low24hr': float()}+,
  |                      +{ }+,
  |                      +{ }+,
  |                      +{ }+
  |
  |
  |
  | # Built by loaner.py ============================
 (( lendingHistory ))----+{'_id': loan['id'],
  |                         }+,
  |                      +{ }+,
  |                      +{ }+,
  |                      +{ }+
  |
  |
  |
  | # Built by bookie.py ============================
 (( 'market'tradeHistory ))
  |          -----------+{'_id': trade['globalTradeID'],
  |                         }+
  |                      +{ }+,
  |                      +{ }+,
  |                      +{ }+
  |
  |
  |
  | # Built by charter.py ============================
 (( 'market'chart ))
  |          -----------+{'_id': candle['date'],
  |                         }+
  |                      +{ }+,
  |                      +{ }+,
  |                      +{ }+
  |
  |
  |

```
