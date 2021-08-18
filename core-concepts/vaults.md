# Vaults

### What are vaults?

Vaults are yield-bearing transferrable ERC20 tokens. The tokens are named with the prefix "wd-", followed by the name of the asset - e.g. wdETH, wdDAI, etc.

### Shared rebalancing costs

Vaults decrease the gas costs of LPs in several ways. First, it's roughly ~4x cheaper to enter a vault when compared to entering a lending pair.

Second, the cost of the following actions is shared by all LPs of the vault and paid from the earned interest:

* Rebalancing between two pairs which are 2 actions: withdraw, then deposit.
* Claim interest & compound

Note that in the very early stages of vaults with extremely low deposit limits, these actions are sponsored by the protocol. Later on, once the vaults have much higher deposit limits, these actions will be from a part of the earned interest.

### Rebalancing

Vaults try to rebalance funds between individual lending pairs to get the highest long-term overall yield.

For example, if the total vault balance is 100 ETH, it may hold deposits in:

* 10 ETH in ETH-LINK pair at 51% APR
* 40 ETH in ETH-MKR pair at 36% APR
* 50 ETH in ETH-COMP pair at 48% APR

Vaults are still in a very early stage and the rebalancing process is currently not yet fully automated.

The funds may not be at the most optimal highest yielding pair 100% of the time. This is because the gas cost of rebalancing may be much higher than the potential short-lived increase in the supplying interest rate of any given pair.

As people deposit and borrow funds into each pair, the interest rate on the pair may increase or decrease dramatically from minute to minute. Rebalancing into such short-lived highest yielding pairs every few minutes would generate unreasonable gas costs. Instead, rebalancing tries to predict which pairs may have the best stable yield long-term.

### Yield earning

The yield from individual lending pairs is not funneled into the vault in real time. Earned interest must be harvested from time to time by the rebalancer and costs gas. Therefore, the accumulated yield from a given pair must outweigh the cost of the harvesting.

### Yield distribution

Depositors of the vaults earn an interest accrued by the block. Once the yield is harvested, it's added to the pending undistributed income and distributed evenly over 7 days.

### New deposits / Buffer area / Withdrawals

New deposits made into the vault are waiting in the buffer area and do yet earn any yield. Once there is a large enough balance in the buffer area, it will get deployed to a lending pair.

The buffer area also serves as a cheap way for LPs to withdraw their funds. Since these funds are not yet deployed to any lending pair, the vault doesn't need to withdraw them and can just send them directly to the LP.

If the LP tries to withdraw an amount larger than what's in the buffer area, the vault will first need to withdraw deployed funds and then send them to the LP. This will have a much higher gas cost.

The buffer area is currently targeting to hold about 10% of the balance deposited into the vault.  Meaning that 90% of the balance will be earning fees and 10% will be idle and available for a cheap withdrawal.

