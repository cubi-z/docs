# Ratio de sécurité

Afin de maintenir la solvabilité du protocole, les emprunteurs doivent sur-collatéraliser leurs positions d'emprunt.

Un ratio de sécurité est calculé en USD:

`(montant votreDépôt * Facteurcollatéral) / (montant votreEmprunt)`

Le facteur de collatéral de tous les tokens sont actuellement fixés à 0.6.

Quand la valeur du collatéral devient insuffisante par rapport au montant emprunté, la position peut être liquidé afin de rembourser la dette. Si cela arrive, une pénalité de liquidation est prélevée par le protocol et les liquidateurs.

