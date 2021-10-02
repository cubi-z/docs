# Staking xWILD

WILD peut être staké afin de gagner les frais générés par le protocole. Le WILD staké se nomme xWILD.

## Le cycle de vie des frais générés par le protocole

Les frais générés par le protocole à travers l'écart des taux d'intérêts prêteur/emprunteur sont collectés dans le token natif de chaque paire prêtée. Avant d'être pouvoir distribué aux stakers de xWILD, ils doivent d'abord être accumulés et convertis en WILD.

### 1. Fournir de la liquidité & emprunter - la génération des frais

Les fournisseurs de liquidité ajoutent un token natif à chaque paire d'emprunt. Les emprunteurs paient un intérêt qui est partiellement gagnée par les fournisseurs de liquidité, et partiellement par le protocole. Cet intérêt, cependant, n'est pas distribué en temps réel et doit être accumulé pour chaque fournisseur séparemment.

### 2. Accumuler - la collecte des frais

Les intérêts accumulés sont envoyés au Fee Recipient Contract à chaque intéraction des fournisseurs de liquidité avec la paire prêtée en question \(claiming, déposer, retirer\).

Les développeurs de bot peuvent surveiller les grosses positions et les accumuler lorsque que les frais accumulés sont suffisamment élevés pour être rentable pour le bot qui les distribue alors aux stakers de xWILD. Cette accumulation externe ne coûte rien aux fournisseurs de liquidité et est même bénéfique pour eux car elle permet d'auto-compound leur position.

### 3. Fee Recipient contract - conversion des frais

Les intérêts générés lors de l'étape 2 sont envoyés au Fee Recipient contract. Cela peut se produire soit lorsque les fournisseurs intéragissent avec leurs paires prêtées naturellement, ou par l'accumulation de leur compte par quelqu'un d'autre. Cet intérêt reste alors en attente dans le Fee Recipient dans les tokens natifs avant d'être convertis en WILD \(buyback\).

Pour inciter à l'automatisation de la distribution des frais, cette action de conversion est assortie d'une incitation correspondant à un pourcentage des fonds convertis.

En pratique, cette conversion peut se produire à tout moment, entre plusieurs fois par jour à une fois tous les quelques jours.

### 4. xWILD - Distribution des frais

Les frais de l'étape 3 sont utilisés pour racheter du WILD et le distribuer aux stakers de xWILD.

Si vous êtes un développeur de bot et voulez obtenir une partie de la distribution des frais, suivez [ces instructions](https://github.com/WildCredit/mev-job-board/blob/main/specs/wild-credit.md).

