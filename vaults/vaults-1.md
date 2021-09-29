# Overview

### Qu'est-ce qu'un vault ?

Les vaults sont des tokens ERC20 transférables produisant un rendement. Ces tokens sont nommés avec le préfixe "wd-", suivi du nom de l'actif - ex: wdETH, wdDAI, etc.

### Des coûts de rééquilibrage partagés

Les vaults réduisent le coût en gas de l'apport de liquidités de plusieurs façons. Premièrement, c'est à peu près 4x moins cher de rentrer dans un vault plutôt que de rentrer dans une paire de prêt.

Deuxièmement, le coût des actions suivantes est partagé par tous les fournisseurs de liquidité du vault et payé par l'intérêt gagné:
* Rééquilibrage entre deux paires ce qui implique deux actions: retirer puis déposer.
* Claim l'intérêt et le réinvestir.

Veuillez noter que durant les débuts des vaults avec des limites de dépôts très basses, ces actions seront prises en charge par le protcole. Plus tard, une fois que les vaults auront des limites de dépôts plus élevés, ces actions seront financées par une partie de l'intérêt gagné.

### Rééquilibrage

Les vaults tentent de rééquilibrer les fonds entre les différentes paires d'emprunt afin d'obtenir le meilleur rendement à long terme.

Par exemple, si le total du vault est de 100 ETH, il pourrait contenir des dépôts tel que:

* 10 ETH dans la paire ETH-LINK à 51% d'APR
* 40 ETH dans la paire ETH-MKR à 36% APR
* 50 ETH dans la paire ETH-COMP à 48% APR

Les vaults sont encore à un stade précoce et le processus de rééquilibrage n'est pas encore totalement automatisé.

Il se peut que les fonds ne soient pas optimisés à 100% afin d'obtenir le meilleur rendement tout le temps. En effet, le coût du gas nécessaire pour rééquilibrer les paires peut être bien plus élevé que le potentiel de courte durée de l'amélioration du rendement global.

Au fur et à mesure que les utilisateurs déposent et empruntent des fonds dans chaque pair, le taux d'intérêt de la paire peut augmenter ou diminuer drastiquement de minute ne minute. Procéder à un rééquilibrage sur de si courtes durées engendrerait des coûts de gas bien trop élevés. Au lieu de cela, le rééquilibrage tente de prédire quelles paires peuvent avoir le meilleur rendement le plus stable à long terme.

### Gain du rendement

Le rendement des paires de prêt n'est pas versé dans le vault en temps réel. L'intérêt gagné doit être récolté ponctuellement par le rééquilibrage et a un coût en gas. Par conséquence, le rendement cumulé d'une paire donnée doit être supérieure au coût de la récolte.

### Distribution du rendement

Les dépositants des vaults gagnent un intérêt augmentant à chaque bloc. Une fois le rendement récolté, il est ajouté aux revenus en attente d'être distribués sur une période de 7 jours.

### Nouveaux dépôts / Zone tampon / Retraits

Les nouveaux dépôts effectués dans le vault sont en attente dans la zone tampon et ne rapporte aucun rendement. Une fois qu'il y a assez de liquidités dans la zone tampon, elle est alors déployée dans une paire de prêt.

La zone tampon sert aussi de moyen à bas coût pour les fournisseurs de liquidité de retirer leurs fonds. Etant donné que les fonds ne sont pas déployés dans une paire de prêt, le vault n'a pas besoin de les retirer et peut les envoyer directement au fournisseur de liquidité.

Si le fournisseur de liquidté essaye de retirer un montant supérieur au montant présent dans la zone tampon, le vault doit d'abord retirer les fonds néecessaires avant de les renvoyer au fournisseur de liquidité. Cela a un coût en gas bien plus élevé.

La zone tampon a actuellement un objectif de 10% du montant total déposé dans le vault. Ce qui implique que 90% du montant déposé gagnera des frais, et 10% sera inactif et disponible pour un retrait peu coûteux.
