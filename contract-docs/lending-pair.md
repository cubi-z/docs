# Lending Pair

## Events

### Liquidation

Emitted on each `liquidateAccount` function call.

```text
event Liquidation(
  address indexed account,
  address indexed repayToken,
  address indexed supplyToken,
  uint repayAmount,
  uint supplyAmount
)
```

### Deposit

Emitted on any of the `deposit` function calls.

```text
event Deposit(address indexed account, address indexed token, uint amount)
```

### Withdraw

Emitted on any of the `withdraw` function calls.

```text
event Withdraw(address indexed token, uint amount)
```

### Borrow

Emitted on each `borrow` function call.

```text
event Borrow(address indexed token, uint amount)
```

### Repay

Emitted on each `repay` function call.

```text
event Repay(address indexed account, address indexed token, uint amount)
```

## Read-only functions

### debtOf

Borrowed token amount with interest for a given account. May not include currently pending interest.

```text
debtOf(address token, address account)
```

### totalDebt

Total debt with interest for a given token. May not include currently pending interest.

```text
totalDebt(address token)
```

### borrowBalance

Borrowed `borrowToken` amount with interest for a given `account`, converted into `returnToken` token based on the liquidation current [liquidation price](). Does not include slippage. May not include pending interest.

```text
borrowBalance(address account, address borrowToken, address returnToken)
```

### supplyBalance

Borrowed `suppliedToken` amount with interest for a given `account`, converted into `returnToken` token based on the current [liquidation price](). Does not include slippage. May not include pending interest.

```text
supplyBalance(address account, address borrowToken, address returnToken)
```

### accountHealth

Calculated as combined `supplyBalance` / `borrowBalance`of both tokens. When below `controller.liqMinHealth()`, the account may be liquidated.

```text
accountHealth(address account)
```

### convertTokenValues

Convert`fromToken` amount into `toToken` amount based on the oracle prices.

```text
convertTokenValues(address fromToken, address toToken, uint inputAmount)
```

### pendingSupplyInterest

Pending interest amount not yet included in `supplyBalance`.

```text
pendingSupplyInterest(address token, address account)
```

### pendingBorrowInterest

Pending interest amount not yet included in `borrowBalance`.

```text
pendingBorrowInterest(address token, address account)
```

## State-modifying functions

### deposit

Deposit `token` to earn interest or to provide collateral for borrowing another token.

```text
deposit(address account, address token, uint amount)
```

### withdraw

Withdraw deposited token. If there is a positive `borrowBalance`, the account must stay above required  `accountHealth` after calling this function.

```text
withdraw(address token, uint amount)
```

### withdrawAll

Withdraw the full supply balance + pending interest.

```text
withdrawAll(address token)
```

### repayAll

Repay the full borrow balance + pending interest.

```text
repayAll(address account, address token)
```

### borrow

Borrow `token`. The account must stay above required  `accountHealth` after calling this function. The account cannot borrow the same token it's currently supplying.

```text
borrow(address token, uint amount)
```

### repay

Repay borrowed `token`.

```text
repay(address account, address token, uint amount)
```

### depositRepay

For a given `token`, the `deposit` function can only be called after repaying the debt first. This helper function combines both actions into one by repaying the debt first and using the remaining amount as a deposit.

```text
depositRepay(address account, address token, uint amount)
```

### depositRepayETH

Same as `depositRepay` but using ETH as input.

```text
depositRepayETH(address account) payable
```

### withdrawBorrow

For a given `token`, the `borrow` function can only be called after withdrawing the supplied amount first. This helper function combines both actions into one by withdrawing the supplied amount first and using the remaining amount to borrow.

```text
withdrawBorrow(address token, uint amount)
```

### withdrawBorrowETH

Same as `withdrawBorrow` but using ETH as output.

```text
withdrawBorrowETH(uint amount)
```

