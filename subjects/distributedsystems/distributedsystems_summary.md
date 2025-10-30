# Distributed Systems Quiz Summary

## 🌐 Core Concepts

### Distributed System Characteristics
- **Distribution**: Components on networked computers
- **Concurrency**: Simultaneous execution
- **No Global Clock**: Coordination challenges
- **Independent Failures**: Partial system failures

### Key Challenges
- **Network**: Latency, bandwidth, unreliability
- **Failures**: Node crashes, network partitions
- **Scalability**: Growing with load/users
- **Consistency**: Maintaining correct state

## 📊 CAP Theorem
**Can only guarantee 2 of 3:**
- **Consistency**: All nodes see same data
- **Availability**: System remains operational  
- **Partition Tolerance**: Works despite network failures

**System Types:**
- **CP**: MongoDB, HBase (sacrifice availability)
- **AP**: Cassandra, DynamoDB (sacrifice consistency)
- **CA**: Traditional RDBMS (sacrifice partition tolerance)

## 🔄 Consistency Models

### Strong Consistency
- **Linearizability**: Operations appear atomic
- **Sequential**: Operations in total order
- **Benefits**: Simple programming model
- **Cost**: Higher latency, lower availability

### Weak Consistency
- **Eventual**: Converges after updates stop
- **Causal**: Causally related operations ordered
- **Benefits**: Higher availability, lower latency
- **Cost**: Complex programming model

## 🗳️ Consensus Algorithms

### Paxos
- **Roles**: Proposer, Acceptor, Learner
- **Phases**: Prepare (Phase 1), Accept (Phase 2)
- **Properties**: Safety, liveness with majority
- **Multi-Paxos**: Optimization for multiple decisions

### Raft
- **Roles**: Leader, Follower, Candidate
- **Components**: Leader election, log replication, safety
- **Terms**: Logical time periods
- **Simpler**: More understandable than Paxos

### Byzantine Fault Tolerance
- **Problem**: Malicious/arbitrary failures
- **pBFT**: Practical Byzantine Fault Tolerance
- **Requirement**: f failures tolerated with 3f+1 nodes

## ⚖️ Load Balancing

### Algorithms
- **Round Robin**: Sequential distribution
- **Least Connections**: Route to least loaded
- **Weighted**: Consider server capacity
- **IP Hash**: Consistent client routing

### Types
- **Layer 4**: Transport layer (TCP/UDP)
- **Layer 7**: Application layer (HTTP)
- **Hardware vs Software**: Dedicated vs commodity

## 💾 Replication

### Strategies
- **Master-Slave**: Single writer, multiple readers
- **Master-Master**: Multiple writers, conflict resolution
- **Quorum**: R + W > N for consistency

### Consistency Patterns
- **Synchronous**: Wait for all replicas (strong consistency)
- **Asynchronous**: Background replication (eventual consistency)
- **Semi-sync**: Wait for some replicas

## 🗄️ Partitioning/Sharding

### Horizontal Partitioning
- **Range-based**: Partition by value ranges
- **Hash-based**: Use hash function
- **Directory-based**: Lookup service
- **Challenges**: Rebalancing, cross-shard queries

### Vertical Partitioning
- **Column splitting**: Different columns on different nodes
- **Service splitting**: Different features on different services

## 🕒 Time and Ordering

### Logical Clocks
- **Lamport Timestamps**: Happened-before relation
- **Vector Clocks**: Causal ordering detection
- **Usage**: Distributed debugging, consistency

### Physical Clocks
- **NTP**: Network Time Protocol
- **Challenges**: Clock drift, synchronization
- **GPS/Atomic**: High precision sources

## 🔄 Distributed Transactions

### Two-Phase Commit (2PC)
- **Phase 1**: Prepare (vote yes/no)
- **Phase 2**: Commit/Abort based on votes
- **Problems**: Blocking, coordinator failure

### Saga Pattern
- **Long-running**: Sequence of local transactions
- **Compensation**: Rollback with compensating actions
- **Types**: Choreography vs Orchestration

## 🎯 Patterns & Architectures

### Microservices Patterns
- **Database per Service**: Separate data stores
- **API Gateway**: Single entry point
- **Circuit Breaker**: Prevent cascade failures
- **Bulkhead**: Isolate resources

### Event-Driven Architecture
- **Event Sourcing**: Store events, not state
- **CQRS**: Separate read/write models
- **Pub/Sub**: Decoupled communication

## 🛡️ Fault Tolerance

### Failure Types
- **Fail-stop**: Detectable halting
- **Fail-slow**: Performance degradation
- **Byzantine**: Malicious/arbitrary behavior
- **Network Partition**: Communication failure

### Resilience Patterns
- **Circuit Breaker**: Fail fast on downstream failures
- **Retry**: Exponential backoff with jitter
- **Timeout**: Prevent hanging operations
- **Bulkhead**: Resource isolation

## 📈 Scalability Patterns

### Horizontal Scaling
- **Stateless Services**: No server-side state
- **Load Balancing**: Distribute requests
- **Sharding**: Partition data
- **Caching**: Reduce backend load

### Vertical Scaling
- **More Resources**: CPU, RAM, storage
- **Limitations**: Hardware constraints
- **Easier**: No distribution complexity

## 🔐 Security in Distributed Systems

### Authentication & Authorization
- **Distributed Identity**: SSO, OAuth, JWT
- **Service-to-Service**: mTLS, API keys
- **Zero Trust**: Never trust, always verify

### Network Security
- **TLS**: Encrypted communication
- **Network Segmentation**: Isolate components
- **VPN/Private Networks**: Secure connectivity

## 📊 Key Metrics

### Performance
- **Latency**: Response time (P50, P95, P99)
- **Throughput**: Requests per second
- **Little's Law**: L = λ × W

### Reliability
- **Availability**: Uptime percentage
- **MTBF**: Mean Time Between Failures
- **MTTR**: Mean Time To Recovery

## 🎓 Quiz Tips
- Remember CAP theorem trade-offs
- Know consensus algorithm differences (Paxos vs Raft)
- Understand consistency models and their trade-offs
- Know common failure modes and resilience patterns
- Remember partitioning strategies and challenges
- Understand distributed transaction problems (2PC blocking)
- Know time synchronization challenges