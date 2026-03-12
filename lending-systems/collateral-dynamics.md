# Collateral Dynamics in Decentralized Lending

This note examines the mechanics of collateralized lending protocols.

In decentralized lending systems, borrowers lock collateral in order to
obtain loans. The protocol must ensure that the value of collateral
remains sufficient to cover the outstanding debt.

---

## Basic Lending Model

Let:

C = collateral value  
D = borrowed debt  

A lending system requires:

C ≥ D

In practice, protocols enforce an overcollateralization ratio.

Define:

r = collateralization ratio

Then the constraint becomes:

C ≥ rD

Typical values:

r = 1.5 → 150% collateralization  
r = 2.0 → 200% collateralization

This protects lenders from price volatility.

---

## Collateral Ratio

The collateral ratio is defined as:

CR = C / D

A position is considered healthy if:

CR ≥ r

If CR falls below the threshold, the position becomes eligible
for liquidation.

---

## Liquidation Mechanism

When the collateral ratio drops below the required level,
liquidators are allowed to repay debt in exchange for collateral.

Liquidation typically involves:

1. repaying a portion of debt
2. receiving discounted collateral

This creates incentives for external participants to maintain
protocol solvency.

---

## Price Oracle Dependency

Collateral valuation depends on price feeds.

Let:

P = price of collateral asset

Then:

C = P × collateral_amount

If price feeds are incorrect or delayed, the protocol may allow
undercollateralized borrowing.

Oracle design therefore becomes a critical component of lending
protocol security.

---

## Systemic Risk

Several risks emerge in decentralized credit markets:

- rapid collateral price drops
- oracle manipulation
- liquidation cascades
- liquidity shortages during market stress

These dynamics can create feedback loops where falling prices
trigger further liquidations.

---

## Interest Rate Dynamics

Interest rates regulate borrowing demand.

Common models include:

- fixed rates
- utilization-based rates
- dynamic market-driven rates

Utilization-based models adjust interest depending on the
ratio of borrowed assets to available liquidity.

---

## Comparison with Traditional Credit

Traditional lending systems rely on:

- identity
- credit scores
- legal enforcement

Decentralized lending relies instead on:

- overcollateralization
- automated liquidation
- transparent smart contracts

This removes counterparty risk but reduces capital efficiency.

---

## Open Questions

Several questions remain important for protocol design:

- how to reduce overcollateralization requirements
- how to prevent liquidation cascades
- how to design more resilient oracle systems
- how credit markets interact with automated market makers
