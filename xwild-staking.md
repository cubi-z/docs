# xWILD Staking

WILD peut être staké afin de gagner les frais générés par le protocole. Le WILD staké se nomme xWILD.

### Le cycle de vie des frais générés par le protocole

Les frais générés par le protocole à travers l'écart des taux d'intérêts prêteur/emprunteur sont collectés dans le token natif de chaque paire d'emprunt. Avant d'être pouvoir distribué aux stakers de xWILD, ils doivent d'abord être accumulés et convertis en WILD.

#### 1. Fournir de la liquidité & emprunter - la génération des frais

Les fournisseurs de liquidité ajoutent un token natif à chaque paire d'emprunt. Les emprunteurs paient un intérêt qui est partiellement gagnée par les fournisseurs de liquidité, et partiellement par le protocole. Cet intérêt, cependant, n'est pas distribué en temps réel et doit être accumulé pour chaque fournisseur séparemment.

#### 2. Accruing - fee collection

Accrued supply interest is sent to the Fee Recipent contract on each interaction of the suppliers with the given lending pair \(claiming, depositing, withdrawing\).

Bot developers may watch large accounts and accrue them when the accumulated fees grow large enough to become profitable for the bot to distribute them to xWILD stakers. This external accrual doesn't cost anything to suppliers and is actually beneficial to them since it auto-compounds their position.

#### 3. Fee Recipent contract - fee conversion

The interest earned from step 2 is sent to the Fee Recipient contract. This can happen either by suppliers interacting with lending pairs naturally or by their accounts being accrued by anyone else. This interest is waiting in the Fee Recipient in the respective native tokens and must be converted to WILD \(buyback\).

To incentivize automated fee distributions, this conversion action has a caller incentive set to a percentage of the converted funds.

In practice, this conversion can happen anytime from several times per day to one every few days.

#### 4. xWILD - fee distribution

Fees from step 3 are used to buyback WILD and distribute it to xWILD stakers.

If you're a bot developer and want to earn incentives for fee distributions, follow [these guidelines](https://github.com/WildCredit/mev-job-board/blob/main/specs/wild-credit.md).

