# closingout_script
This scripts demonstrates how to close out of a position at the end of the day based on market allocations the strategy holds.

Previously, I had shown several scripts that did this by using either an internal variable, but some scripts didn't seem to close out
properly. Though there were no errors, the best way to end scripts is with closing all market positions:

```
if account[self.symbol].position.shares>0:
    order_id = order.algo_sell(self.symbol, "market", intent="exit")   
    print('sold ' + self.symbol + ' at end of day.')    
    if len(bar_close)>0:    
        print('Approximate price: ' + str(bar_close[0]))        
elif account[self.symbol].position.shares<0:

```

    order_id = order.algo_buy(self.symbol, "market", intent="exit")
    
    print('bought ' + self.symbol + ' at end of day.')
    
    if len(bar_close)>0:
    
        print('Approximate price: ' + str(bar_close[0]))
        
        
        
        
        
Attached is a revised breakout script that correctly ends the position.
