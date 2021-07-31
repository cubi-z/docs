# Providing Liquidity

Liquidity providers \(LPs\) of Wild Credit have single-sided asset exposure and don't suffer from impermanent loss.

### Interest rate fees

The interest rate fees are split between LPs and WILD token stakers.

#### Single-sided LP tokens

To allow better composability, Wild introduces single-sided LP tokens. Instead of giving you a single combined LP token, each lending pair has two LP tokens, representing a claim over their respective underlying assets. These are standard ERC20 tokens that can be used, transferred, or sold anywhere else.

For example, if you deposit 10 DAI in DAI-ETH pair, you’ll get 10 **DAI** LP tokens ****in ****DAI-ETH pair. If you deposit another 5 DAI in DAI-YFI pair and you’ll get 5 **DAI** LP tokens ****in ****DAI-YFI pair. Both LP tokens are unique and can only be used in their respective pairs.

Fees are distributed to the LPs each time they interact with the protocol \(transfer LP tokens, deposit, withdraw\) by increasing the balance of their LP tokens.

