# Hybrid Consensus Mechanisms
## Core Concept
Combining multiple consensus mechanisms to leverage their respective strengths while mitigating weaknesses.

## Popular Combinations
### PoW + PoS (Decred)
- **PoW Miners**: Create new blocks
- **PoS Voters**: Validate and approve blocks
- **Governance**: Stakeholders guide network development

### PoS + BFT (Tendermint)
- **Validator Set**: PoS determines who can participate
- **BFT Voting**: Validators vote on block finality
- **Immediate Finality**: No reorganizations after commitment

### PoW + PoSpace (Hybrid Miners)
- **Primary Security**: PoW provides base security
- **Supplementary**: PoSpace provides additional security layer
- **Flexible Mining**: Miners choose based on resources

## Design Considerations
- **Security Layering**: Multiple attack vectors required to compromise
- **Performance Optimization**: Leverage strengths of each mechanism
- **Governance Balance**: Distributed control among stakeholders

## Advantages
- **Enhanced Security**: Multiple independent security assumptions
- **Flexibility**: Can adapt to different use cases
- **Progressive Decentralization**: Start centralized, become decentralized

## Disadvantages
- **Complexity**: Multiple systems to implement and maintain
- **Potential Conflicts**: Different mechanisms may have opposing incentives
- **Implementation Overhead**: More components to secure and update

## Implementations
- **Decred**: PoW + PoS hybrid
- **Tendermint Core**: PoS + BFT
- **Various Projects**: Many custom hybrid implementations