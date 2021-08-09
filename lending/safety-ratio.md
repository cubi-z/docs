# Safety Ratio

In order to maintain the solvency of the protocol, borrowers are required to overcollateralize their borrowing positions.

A safety ratio is calculated as USD values of \(yourDeposit amount \* collateralFactor\) / \(yourBorrow amount\).

Collateral factors of all tokens are currently set to 0.6.

When the value of their collateral becomes insufficient in relation to the amount borrowed, their account may get liquidated to pay off their debt. When this happens, a liquidation penalty is charged which is earned by the protocol & the liquidators.

