### DIVIDEND DISTRIBUTION CONTRACT FOR TOKENS
<div style="text-align: justify">A contract receiving as value, an ERC20 "token A", and being able to distribute dividends proportionally to holders of another ERC20 "token B", has to address three principal parameters:</div>

1. A uint256 variable, let's say, Total_A: The total amount of "token A" rightfully received and present, inside the "Dividend Contract".

2. Another uint256 variable, let's say, Total_tB: Is the total amount of "token B" __times__ the lapse of time passed in hands of each owner that collected dividends; is a summatory proportional to collected payments throught time. The specification for this variable is described below.

3. And a third uint256 variable, say, dividend_Burnable: Will be the total amount of token B __times__ the period of time which that asset has been possessed by a token holder.

#### SPECIFICATIONS
<div style="text-align: justify">Tokens "A" can only be received by the Dividend Contract through a "Payment" function.</div><br>
<div style="text-align: justify">Tokens "B" must have a managment history, in which the today owners owns the total valid amount of these tokens. Tokens B cannot be either burned or minted by this moment. The Dividend Contract must be initialized by a constructor, in which the last block number is registered in a uint256 "sTart" variable.</div><br>
<div style="text-align: justify">Any time a dividend payment is done, certain amount of "dividend_Burnable" is burnt in the Dividend Contract and this amount is deducted from the total amount of token B times the number of blocks between the last observable one and "sTart", this value is added to Total_tB.</div><br>
<div style="text-align: justify">To estimate any payment, a token B holder will execute a "ConsultDividend(address)" function. But to collect a dividend, a map inside the Dividend Contract must associate the message.sender address to a struct storing both, a block number, which is the last time the owner moved or redeem any dividend, and the last token B balance the owner had at that moment. It allow to calculate the value for a third value in the struct pointed by the map(address => struct) which will be the total amount of dividend_Burnable.</div><br>
<div style="text-align: justify">This reveals an intimate relationship between the token B contract and the Dividend Contract.</div><br>
