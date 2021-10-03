# Fournir de la liquidité

Les fournisseurs de liquidités \(LPs\) de Wild Credit ont une exposition à un seul actif et ne risque donc pas d'impermanent loss.

## Frais de taux d'intérêt

Les frais de taux d'intérêt est réparti entre les fournisseurs de liquidité et les stakers du token WILD.

### Tokens LP uniques

Afin de permettre une meilleure composabilité, Wild a mis en place des LP tokens représentant un seul actif. Au lieu de vous donner un LP token représentant la combinaison de la pool, chaque paire de prêt a deux tokens, représentant leur actif sous-jacent respectif. Ce sont des tokens ERC20 qui peuvent être utilisés, transférés ou vendus n'importe où.

Par exemple, si vous déposez 10 DAI dans la paire DAI-ETH, vous obtiendrez 10 **DAI** tokens LP dans la paire DAI-ETH. Si vous déposez 5 autres DAI dans la paire DAI-YFI, vous obtiendrez 5 **DAI** tokens LP dans la paire DAI-YFI. Ces deux tokens LP sont uniques et ne peuvent être utilisés que dans leur paire respective.

Les frais sont distribués aux fournisseurs de liquidité à chaque fois qu'ils intéragissent avec le protocole \(transfert des tokens LP, dépôt, retrait\) en augmantant le solde de leur tokens LP.

