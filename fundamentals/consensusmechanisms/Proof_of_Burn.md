# Proof of Burn (PoB) Consensus Mechanism
## Core Concept
Miners demonstrate commitment by permanently destroying **("burning")** cryptocurrency, earning the right to mine proportionally.

## Technical Implementation
- **Burn Address**: Cryptographically unspendable address
- **Burn Verification**: Network verifies coins are permanently destroyed
- **Mining Rights**: Burning grants mining power for extended period

## Process Flow
1. **Coin Burning**: Miner sends coins to verifiably unspendable address
2. **Power Calculation**: Mining power proportional to burned coins
3. **Block Mining**: Miner participates in consensus like PoW
4. **Power Decay**: Mining power decreases over time
5. **Reburning**: Miner may burn more coins to maintain power

## Economic Model
- **Sunk Cost**: Burned coins represent irreversible investment
- **Opportunity Cost**: Miner forgoes current value for future rewards
- **Deflationary Pressure**: Continuous coin removal from supply

## Security Model
- **Economic Commitment**: Attack cost equals value of burned coins
- **Long-term Incentives**: Aligned with network success
- **Sybil Resistance**: Each identity requires separate burning

## Advantages
- **Energy Efficient**: No ongoing computational waste
- **Fair Distribution**: No special hardware advantages
- **Deflationary**: Reduces circulating supply

## Disadvantages
- **Wealth Concentration**: Favors early adopters with capital
- **Inefficient Capital**: Locked value cannot be used productively
- **Perception Issues**: "Wasting" resources may deter adoption

## Implementations
- **Slimcoin**: First implementation of PoB
- **Counterparty**: Bitcoin-based platform using PoB
- **Various Tokens**: Many projects use burning mechanisms