# Price Oracles

Wild Credit uses a combination of Chainlink oracles for large blue-chip tokens and Uniswap V3 oracle for mid and small cap tokens.

If the oracle stops reporting the price for any reason, the following actions will be auto-disabled: deposit, borrow, liquidate.

The actions which don't require token prices will remain enabled: repay, withdraw.

Be aware that providing liquidity on a pair with a low-cap token is highly risky. If the cost of market buying a small-cap token to increase its price for a period of time \(e.g. 10 minutes\) is lower than the potential reward of borrowing against, it's possible that someone may do exactly that.

On the opposite side, if the token price drops significantly for a TWAP period of time, this could result in a lot of liquidations.

Note that this kind of price manipulation is not a technical issue. The price reported by the oracle would in this case be correct. It's also not a flash loan attack which all happens in the same transaction and is not possible here. The borrower would need to maintain the price of the target token for a certain period of time in order to execute this scenario.

