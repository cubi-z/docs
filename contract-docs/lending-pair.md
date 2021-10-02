# Paires de prêt

## Evènements

### Liquidation

Emis à chaque appel de la fonction `liquidateAccount`.

```text
event Liquidation(
  address indexed account,
  address indexed repayToken,
  address indexed supplyToken,
  uint repayAmount,
  uint supplyAmount
)
```

### Dépôt

Emis sur n'importe quel appel de la fonction `deposit`.

```text
event Deposit(address indexed account, address indexed token, uint amount)
```

### Retrait

Emis sur n'importe quel appel de la fonction `withdraw`.

```text
event Withdraw(address indexed token, uint amount)
```

### Emprunt

Emis sur chaque appel de la fonction `borrow`.

```text
event Borrow(address indexed token, uint amount)
```

### Remboursement

Emis sur chaque appel de la fonction `repay`.

```text
event Repay(address indexed account, address indexed token, uint amount)
```

## Fonctions en lecture seule

### debtOf

Montant du token emprunté intérêt compris pour une position. Peut ne pas inclure les intérêts en attente.

```text
debtOf(address token, address account)
```

### totalDebt

Dette totale intérêt compris pour un token donné. Peut ne pas inclure les intérêts en attente.

```text
totalDebt(address token)
```

### borrowBalance

Montant emprunté `borrowToken` intérêts compris pour une `position` donnée, convertie en token `returnToken` sur la base du [prix de liquidation]() actuel. N'inclut pas le slippage. Peut ne pas inclure les intérêts en attente.


```text
borrowBalance(address account, address borrowToken, address returnToken)
```

### supplyBalance

Montant emprunté `suppliedToken` intérêts compris pour une `position` donnée, convertie en token `returnToken` sur la base du [prix de liquidation]() actuel. N'inclut pas le slippage. Peut ne pas inclure les intérêts en attente.

```text
supplyBalance(address account, address borrowToken, address returnToken)
```

### accountHealth

Correspond au ratio `supplyBalance` / `borrowBalance` des deux tokens. Quand celui ci passe en dessous de `controller.liqMinHealth()`, la position peut être liquidée.


```text
accountHealth(address account)
```

### convertTokenValues

Convertit le montant `fromToken` en montant `toToken` basé sur les prix de l'oracle.

```text
convertTokenValues(address fromToken, address toToken, uint inputAmount)
```

### pendingSupplyInterest

Montant des intérêts en attente pas encore inclus dans `supplyBalance`.

```text
pendingSupplyInterest(address token, address account)
```

### pendingBorrowInterest

Montant des intérêts en attente pas encore inclus dans `borrowBalance`.


```text
pendingBorrowInterest(address token, address account)
```

## Fonctions de modification de l'état

### deposit

Déposer un `token` afin de gagner de l'intérêt ou de fournir un collatéral afin d'emprunter un autre token.

```text
deposit(address account, address token, uint amount)
```

### withdraw

Retirer le token déposé. Si il y a une `borrowBalance` positive, la position doit rester au dessus du `accountHealth` requis après l'appel de cette fonction.

```text
withdraw(address token, uint amount)
```

### withdrawAll

Retire le solde total + les intérêts en attente.

```text
withdrawAll(address token)
```

### repayAll

Rembourse l'intégralité de la dette + les intérêts en attente.

```text
repayAll(address account, address token)
```

### borrow

Emprunte un `token`. La position doit rester au dessus du `accountHealth` requis après l'appel de cette fonction. Il est impossible d'emprunter le même token que celui qui est déposé.

```text
borrow(address token, uint amount)
```

### repay

Rembourse l'emprunt du `token`.

```text
repay(address account, address token, uint amount)
```

### depositRepay

Pour un `token` donné, la fonction `deposit` peut seulement être appelée après avoir rembourser la dette. Cette fonction d'aide combine les deux actions en une, en remboursant d'abord la dette avant d'utiliser le montant restant comme dépôt.

```text
depositRepay(address account, address token, uint amount)
```

### depositRepayETH

Même fonction que `depositRepay` mais en utilisant de l'ETH comme entrée.

```text
depositRepayETH(address account) payable
```

### withdrawBorrow

Pour un `token` donné, la fonction `borrow` peut seulement être appelée après avoir retirer le montant déposé. Cette fonction d'aide combine les deux actions en une, en retirant d'abord le montant déposé et en utilisant le montant restant pour emprunter.

```text
withdrawBorrow(address token, uint amount)
```

### withdrawBorrowETH

Même fonction que `withdrawBorrow` mais en utilisant de l'ETH comme entrée.

```text
withdrawBorrowETH(uint amount)
```

