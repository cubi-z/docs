# Oracles de prix

Wild Credit utilise une combinaison d'oracles Chainlink pour les tokens blue-chip et d'oracle Uniswap V3 pour les tokens à faible et moyenne capitalisation.

En cas d'interruption de communication du prix par l'oracle pour une quelconque raison, les actions suivantes seront désactivées: déposer, emprunter, liquider.

Les actions qui ne requiert pas le prix des tokens resteront activées: rembourser, retirer.

Soyez conscient que fournir de la liquidité sur une paire contenant un token à faible capitalisation est hautement risqué. Si le coût d'achat au marché d'un token à faible capitalisation afin d'augmenter son prix pour une période donnée \(ex 10 minutes\) est inférieur à la récompense potentielle de l'utiliser en collatéral afin d'emprunter, il est possible qu'une personne fasse exactement ça.

A l'inverse, si le prix d'un token baisse significativement sur une période TWAP, cela pourrait engendrer de nombreuses liquidations.

Veuillez noter que ce genre de manipulation du prix n'est pas un problème technique. Le prix donné par l'oracle serait, dans ces cas là, correct. Ce n'est pas non plus une attaque flash loan qui se produit dans une seule et même transaction, ce qui n'est pas possible ici.  L'emprunteur devrait en effet maintenir le prix du token ciblé pour une certaine période de temps afin d'éxécuter l'ensemble du scénario.


