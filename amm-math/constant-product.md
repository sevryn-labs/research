# Constant Product AMM

This note derives the core pricing mechanics of constant-product automated market makers.

The invariant used by systems such as Uniswap v2 maintains:

x · y = k

where:

x = reserve of token X  
y = reserve of token Y  
k = invariant constant

---

## Price Function

The instantaneous price of token X in terms of Y is given by the marginal rate:

p = dy/dx

From the invariant:

x y = k

Solving for y:

y = k / x

Differentiating:

dy/dx = -k / x²

Thus the marginal price magnitude is:

p = k / x²

Since y = k / x:

p = y / x

So the AMM price equals the ratio of reserves.

---

## Trade Mechanics

Suppose a trader adds Δx of token X.

New reserves:

x' = x + Δx

From the invariant:

(x + Δx)(y - Δy) = k

Expanding:

xy - xΔy + yΔx - ΔxΔy = xy

Simplifying:

yΔx = Δy (x + Δx)

Thus:

Δy = (y Δx) / (x + Δx)

This determines the output amount of token Y.

---

## Slippage

The effective trade price is:

Δy / Δx

Substituting:

price_trade = y / (x + Δx)

Compared to the spot price:

price_spot = y / x

Thus price impact increases with trade size relative to liquidity.

---

## Observations

Constant-product markets exhibit several important properties:

1. Liquidity depth increases with reserves.
2. Price impact grows nonlinearly with trade size.
3. Arbitrage maintains external price alignment.
4. Liquidity providers are exposed to impermanent loss.

---

## Open Questions

Some directions worth exploring:

- Alternative invariants for improved capital efficiency
- Dynamic fee mechanisms
- Multi-asset constant-function markets
- Interaction between AMMs and encrypted orderbooks
