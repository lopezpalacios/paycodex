# FX Swap

Two-leg transaction: spot + opposite-direction forward at agreed rates.

## Mechanics

- Leg 1: buy CCY1 / sell CCY2 spot
- Leg 2: sell CCY1 / buy CCY2 forward
- Net effect: temporary swap of currencies, no FX exposure
- Used for funding, not directional bet

## Use cases

- Treasury funds nostro temporarily without FX exposure
- Roll forward existing forward (extend hedge)
- Money market alternative — borrow CCY1 by lending CCY2

## Pricing

- Net swap points = forward points
- Drives spot vs forward implied funding rate

## Related

[[fx-spot]] · [[fx-forward]]
