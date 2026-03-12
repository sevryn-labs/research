# Linear Bonding Curve

This note examines the mechanics of a linear bonding curve used for token issuance and pricing.

Bonding curves define a deterministic pricing function where the token price depends on the total supply.

---

## Price Function

For a linear curve:

p(s) = a s + b

where:

p(s) = token price at supply s  
a = slope parameter  
b = base price

As supply increases, price increases linearly.

---

## Total Cost of Purchase

When minting tokens, the buyer pays the integral of the price function.

Cost(s₀ → s₁) = ∫ₛ₀^ₛ₁ p(s) ds

Substituting the linear function:

∫ (a s + b) ds

This evaluates to:

(a/2)(s₁² - s₀²) + b(s₁ - s₀)

This represents the total amount paid to mint tokens between supply levels.

---

## Marginal Price

The marginal price is simply:

p(s) = a s + b

Each new token becomes slightly more expensive.

This creates a continuous price discovery mechanism.

---

## Redemption Mechanics

If the bonding curve allows burning, the seller receives the reverse integral:

Refund(s₁ → s₀) = ∫ₛ₀^ₛ₁ p(s) ds

Thus the system preserves symmetry between minting and burning.

---

## Liquidity Characteristics

Bonding curves differ from AMMs in several ways:

- Liquidity is always available
- Price depends only on supply
- No external liquidity providers are required

However:

- Price can become extremely volatile at low supply
- Early participants obtain large pricing advantages

---

## Parameter Sensitivity

The slope parameter **a** determines how aggressively the price increases.

Small a:

- slower price increase
- smoother early participation

Large a:

- rapid price growth
- stronger incentive for early buyers

---

## Comparison with AMMs

AMMs price assets based on reserve ratios:

p = y / x

Bonding curves price assets based on supply:

p = f(s)

This makes bonding curves useful for:

- continuous token issuance
- protocol funding
- participation markets

---

## Open Questions

Some areas worth further investigation:

- nonlinear bonding curves (exponential, sigmoid)
- dynamic slope adjustment
- volatility stabilization mechanisms
- integration with AMM liquidity pools
