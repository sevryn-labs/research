# Encrypted Orderbook Markets

This note explores the design of orderbook-based markets where orders are encrypted
before being submitted to the network.

The goal is to reduce information leakage and front-running while preserving
market functionality.

---

## Traditional Orderbooks

In a standard orderbook exchange, participants submit:

- limit orders
- market orders
- cancellations

Orders are publicly visible and sorted by price and time priority.

This transparency enables price discovery but introduces several problems:

- front-running
- sandwich attacks
- information leakage

Participants can observe incoming orders and adjust strategies accordingly.

---

## Encrypted Orderbooks

Encrypted orderbooks attempt to hide order information until execution.

Orders are submitted in encrypted form:

E(order)

Where:

E() represents an encryption function.

The exchange infrastructure cannot read:

- price
- quantity
- direction

until the appropriate computation step.

---

## Fully Homomorphic Encryption

Fully homomorphic encryption (FHE) allows computation on encrypted values.

Given encrypted inputs:

E(a), E(b)

it is possible to compute:

E(a + b)

without decrypting the underlying values.

This property enables matching logic to operate on encrypted orders.

---

## Matching Logic

In a traditional orderbook:

Orders are sorted by price.

Encrypted markets require a different approach.

Possible strategies include:

1. batch auctions
2. encrypted comparison operations
3. deferred price revelation

Batch auctions are particularly attractive because they reduce ordering
dependencies.

---

## Information Leakage

Even if order values are encrypted, some information may still leak through:

- timing of submissions
- order cancellation patterns
- gas usage
- transaction ordering

Designing a secure encrypted market requires minimizing these side channels.

---

## Performance Constraints

FHE operations are computationally expensive.

Tradeoffs include:

- latency
- throughput
- gas costs
- verification complexity

This makes encrypted orderbooks better suited for:

- low-frequency markets
- batch auctions
- privacy-sensitive trading

rather than high-frequency environments.

---

## Comparison with AMMs

Encrypted orderbooks differ fundamentally from automated market makers.

AMMs:

- deterministic pricing functions
- constant liquidity
- public reserves

Encrypted orderbooks:

- discrete orders
- participant-driven liquidity
- hidden pricing information

Each model has different advantages depending on market structure.

---

## Open Questions

Several research questions remain open:

- how to implement efficient encrypted comparisons
- how to minimize information leakage
- how to maintain fairness in transaction ordering
- how encrypted markets interact with AMMs
