# Fabrication de paires

## Adresse

en attente d'ajout

## Evènements

### PairCreated

Emis à chaque appel de la fonction `createPair`.

```text
event PairCreated(
  address indexed pair,
  address indexed tokenA,
  address indexed tokenB
)
```

## Fonctions

### createPair

Creer & initialise une nouvelle paire de prêt sans y ajouter de liquidité.

```text
createPair(
  address tokenA,
  address tokenB
)
```

