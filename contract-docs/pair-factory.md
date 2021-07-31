# Pair Factory

## Address

to-be-added

## Events

### PairCreated

Emitted on each `createPair` function call.

```text
event PairCreated(
  address indexed pair,
  address indexed tokenA,
  address indexed tokenB
)
```

## Functions

### createPair

Creates & initializes a new lending pair without adding any liquidity to it.

```text
createPair(
  address tokenA,
  address tokenB
)
```

