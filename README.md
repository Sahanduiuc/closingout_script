# closingout_script
This scripts demonstrates how to close out of a position at the end of the day based on market allocations the strategy holds.

Previously, I had shown several scripts that closed out positions based on an internal variable, however I noticed the script did
not always completely close out positions at the end of the day, even though there was no bug in the code. Closing based on open
market positions is a more robust way to ensure positions are properly terminated at the end of the day.

```
if account[self.symbol].position.shares>0:
    order_id = order.algo_sell(self.symbol, "market", intent="exit")   
    print('sold ' + self.symbol + ' at end of day.')    
    if len(bar_close)>0:    
        print('Approximate price: ' + str(bar_close[0]))        
elif account[self.symbol].position.shares<0:
    order_id = order.algo_buy(self.symbol, "market", intent="exit")
    print('bought ' + self.symbol + ' at end of day.')
    if len(bar_close)>0:
        print('Approximate price: ' + str(bar_close[0]))     
```
Attached is a revised breakout script that correctly ends the position.
