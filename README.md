# forward
simple implementation of on-chain btc forward contract      

txn: 
- T0 
    - buyer: - spot BTC - rt | cBTC 
    - seller: - BTC | fBTC 
    - vault: + BTC | BTC 
- Redemption 
    - cBTC = BTC + rt   
    - fBTC = BTC - rt 
- T1 
    - buyer: 
    - seller: 
    - vault: 

There are three core components:   
- fBTC (forward seller receipt): (fBTC + rt ) can be used to redeem BTC before its maturity date. fBTC should be traded slightly lower than BTC.  
- cBTC (forward buyer receipt): cBTC will become BTC at its maturity date. cBTC should be traded slightly higher than BTC. 
- vault (btc): one btc is deposited into the vault per forward txn 


Maturity: 
- At maturity, fBTC and cBTC are burned. BTC is transferred from vault to cBTC holder. 

Redeem: 
- Before maturity, fBTC holders can use (fBTC + rt ) to redeem BTC from the vault.  
- if BTC drop from 10k to 1k,  
- if BTC appreciate from 10k to 100k 


- if holders think BTC will go down and thus want to sell BTC now  
        - fBTC holder: 1/ sell fBTC for slightly less than BTC spot; 2/ (fBTC + rt + s) redeem btc and sell BTC
        - cBTC holder: 1/ sell cBTC for slightly more than BTC spot; 2/ burn cBTC to redeem (BTC + rt) and sell BTC 
- if holders think BTC will go up and thus want to buy BTC now 
        - fBTC holder: 1/ (fBTC + rt + s) redeem BTC and hold 
        - cBTC holder: keep holding. 
        
Market: 
- r and s are determined by the market, impacted by risk-free rate, related slippage, and BTC price  
- index  
- mark

BTC 

Seller (-F) 

Buyer  (+F)

risk-free rate (r) 

slippage premium (s)



