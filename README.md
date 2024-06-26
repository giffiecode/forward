# forward
simple implementation of on-chain btc forward contract      

txn: 
- T0 
    - buyer: -spotBTC -rt | cBTC 
    - seller: -BTC +rt +spotBTC 
    - vault: +BTC | BTC 
- Redemption? 
    - cBTC = +BTC; 
- T1 
    - buyer: +BTC -cBTC 
    - seller: 
    - vault: -BTC 

position: 
- -F = short; +F = long  

There are two core components:   
- cBTC (forward buyer receipt): cBTC will become BTC at its maturity date. cBTC should be traded slightly higher than BTC. 
- vault (btc): one btc is deposited into the vault per forward txn  

capital-efficient variant: 
- cBTC (forward buyer receipt): cBTC will become BTC at its maturity date. cBTC should be traded slightly higher than BTC.  
- vault (margin acccount): can hold any assets that's worth more than the obligation. If margin account is below the obligation + cushion, liquidate and buy BTC 

fund-rate version: 
- perp = mark; spot = index  
- daily funding rate (longs pay to short) = ( mark - index ) * 1/365 
- paid by hourly, or even less time 
- long / short perp are positions  
- fully funded -> 0 margin  
- liquidation = sell and transfer before long / short become insolvant  
- long perp = buy forward contract 
- short perp = synthetic short  
- what if long / short don't match perfectly? 
 
Maturity: 
- At maturity, cBTC is burned. BTC is transferred from vault to cBTC holder. 

- if holders think BTC will go down and thus want to sell BTC now  
        - cBTC holder: 1/ sell cBTC for slightly more than BTC spot; 2/ burn cBTC to redeem BTC and sell BTC 
- if holders think BTC will go up and thus want to buy BTC now 
        - cBTC holder: keep holding cBTC till maturity.   
        
Market: 
- r and s are determined by the market, impacted by risk-free rate, related slippage, and BTC price   

margin and liquidatin: 
- stake money 

Downside: 
- less capital efficient because money has to be locked in the vault before the forward contract reaches maturity. 
- in tradfi, seller of forward contract can sell and buy the assets before maturity, creating a short position. 
- trafi needs KYC and some credit to the seller; broker wouldn't not margin call the user as long as the user has sufficient assets in the account for paying back 