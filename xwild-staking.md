# xWILD Staking

WILD can be staked to earn the protocol fees. Staked WILD is called xWILD.

### Lifecycle of protocol fees

Protocol fees earned from the interest rate spread are collected in a native token of each lending pair. Before they can be distributed to xWILD stakers, they must first be accrued & converted to WILD.

#### 1. Supply & borrow - fee generation

Suppliers add a native token to each lending pair. Borrowers pay interest which is partly earned by suppliers and partly by the protocol. This interest, however, is not distributed in real-time and must be accrued for each supplier separately.

#### 2. Accruing - fee collection

Accrued supply interest is sent to the Fee Recipent contract on each interaction of the suppliers with the given lending pair \(claiming, depositing, withdrawing\).

Bot developers may watch large accounts and accrue them when the accumulated fees grow large enough to become profitable for the bot to distribute them to xWILD stakers.

#### 3. Fee Recipent contract - fee conversion

The interest earned from step 2 is sent to the Fee Recipient contract. This can happen either by suppliers interacting with lending pairs naturally or by their accounts being accrued by anyone else. This interest is waiting in the Fee Recipient in the respective native tokens and must be converted to WILD \(buyback\).

To incentivize automated fee distributions, this conversion action has a caller incentive set to a percentage of the converted funds.

In practice, this conversion can happen anytime from several times per day to one every few days.

#### 4. xWILD - fee distribution

Fees from step 3 are used to buyback WILD and distribute it to xWILD stakers.

