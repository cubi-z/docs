# Liquidations

Afin de comprendre comment les oracles de prix fonctionnent, voir [Price Oracles](price-oracles.md).

Pour chaque paire de prêt, Wild Credit vous permet de déposer un token et d'emprunter l'autre. Votre ratio de sécurité doit rester au dessus de 1.0, autrement votre position peut se faire liquider.

Chaque paire de prêt est isolé. Ce qui signifique que vos soldes, ratio de sécurité et liquidations pour une paire n'affectera pas votre ratio ou soldes dans d'autres paires.

Quand une position est liquidité, le collatéral est vendu au prix indiqué par l'oracle afin de rembourser la dette.

La pénalité de liquidation est une somme de [controller.liqFeeSystem](../contract-docs/controller.md#liqfeesystem) et de [controller.liqFeeCaller](../contract-docs/controller.md#liqfeecaller).

Au moment de la rédaction de ce document, la pénalité de liquidation s'élève à 10%.


