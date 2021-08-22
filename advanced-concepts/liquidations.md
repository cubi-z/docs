# Liquidations

To understand how the price oracles work, see [Price Oracles](price-oracles.md).

For each lending pair, Wild Credit allows you to deposit one token and borrow the other. Your safety ratio must stay above 1.0, else your account may be liquidated.

The safety ratio is calculated as:

`(deposit in USD * collateral factor) / (borrowed amount in USD).`

The collateral factor is currently set to 0.6 for all assets.

Each lending pair is isolated. Meaning your balances, safety ratio and liquidations for one pair will not affect your ratio or balances in other lending pairs.

When an account is liquidated, your collateral is sold based on the current oracle price to repay all your debt.

The liquidation penalty is a sum of [controller.liqFeeSystem](../contract-docs/controller.md#liqfeesystem) and [controller.liqFeeCaller](../contract-docs/controller.md#liqfeecaller) values.

At the time of writing, the total liquidation fee is 10%.

