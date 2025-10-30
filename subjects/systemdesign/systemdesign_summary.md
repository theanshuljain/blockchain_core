# System Design Quiz Summary

## 🏗️ Core Fundamentals

### System Design Process
1. **Requirements Analysis**: Functional + Non-functional
2. **High-Level Design**: Architecture + components
3. **Detailed Design**: Implementation specifics
4. **Validation**: Requirements satisfaction
5. **Documentation**: Comprehensive docs

### Key Characteristics
- **Modularity**: Discrete, interchangeable components
- **Scalability**: Handle increased load gracefully
- **Reliability**: Perform correctly under conditions
- **Availability**: Remain operational when needed
- **Performance**: Meet timing/throughput requirements

## 📐 Design Principles

### SOLID Principles
- **S**ingle Responsibility: One reason to change
- **O**pen/Closed: Open for extension, closed for modification
- **L**iskov Substitution: Subclasses replaceable
- **I**nterface Segregation: Don't depend on unused interfaces
- **D**ependency Inversion: Depend on abstractions

### Other Key Principles
- **DRY**: Don't Repeat Yourself
- **KISS**: Keep It Simple, Stupid
- **YAGNI**: You Ain't Gonna Need It
- **Separation of Concerns**: Different aspects in different sections

## 🏛️ Architectural Patterns

### Monolithic Architecture
- **Single Unit**: All functionality in one deployment
- **Pros**: Simple, consistent, easy debugging
- **Cons**: Scaling issues, technology lock-in, team coordination

### Microservices Architecture
- **Independent Services**: Small, focused services
- **Pros**: Scalable, technology diversity, team independence
- **Cons**: Complexity, network latency, data consistency

### Event-Driven Architecture
- **Events**: First-class citizens for communication
- **Patterns**: Event sourcing, CQRS, pub/sub
- **Benefits**: Loose coupling, scalability, real-time processing

## 📊 Scalability & Performance

### Scaling Types
- **Horizontal**: Add more servers (scale out)
- **Vertical**: Add more power (scale up)
- **Trade-offs**: Complexity vs simplicity, cost vs performance

### Performance Metrics
- **Latency**: Time to process single request
- **Throughput**: Requests processed per time unit
- **Little's Law**: L = λ × W (queue length = arrival rate × wait time)

### Caching Strategies
- **Cache-Aside**: Application manages cache
- **Write-Through**: Synchronous cache updates
- **Write-Behind**: Asynchronous cache updates
- **Cache Patterns**: LRU, LFU, TTL eviction

## 🗄️ Database Design

### Database Types
- **RDBMS**: ACID, complex queries, structured data
- **NoSQL**: Scalable, flexible schema
  - **Document**: MongoDB (JSON documents)
  - **Key-Value**: Redis, DynamoDB (simple lookups)
  - **Column**: Cassandra (wide columns)
  - **Graph**: Neo4j (relationships)

### Database Scaling
- **Read Replicas**: Multiple read-only copies
- **Sharding**: Horizontal partitioning
- **Federation**: Split by function
- **Denormalization**: Trade storage for performance

## 🌐 Load Balancing

### Load Balancer Types
- **Layer 4**: TCP/UDP level (faster)
- **Layer 7**: HTTP level (more features)
- **Hardware vs Software**: Performance vs cost

### Algorithms
- **Round Robin**: Sequential distribution
- **Weighted**: Based on capacity
- **Least Connections**: Route to least loaded
- **IP Hash**: Consistent routing

## 🚀 API Design

### RESTful APIs
- **Resources**: Nouns in URLs
- **HTTP Methods**: GET, POST, PUT, DELETE, PATCH
- **Status Codes**: 2xx success, 4xx client error, 5xx server error
- **Stateless**: Each request self-contained

### Alternative Protocols
- **GraphQL**: Single endpoint, client-specified data
- **gRPC**: Binary protocol, high performance
- **WebSockets**: Real-time, bidirectional communication

## 📨 Message Queues

### Messaging Patterns
- **Point-to-Point**: One producer, one consumer
- **Pub/Sub**: One producer, many consumers
- **Request-Reply**: Synchronous-like over async

### Delivery Guarantees
- **At-most-once**: May lose messages
- **At-least-once**: May duplicate messages
- **Exactly-once**: Each message processed once (complex)

### Popular Systems
- **Apache Kafka**: High-throughput streaming
- **RabbitMQ**: Feature-rich traditional MQ
- **Redis Pub/Sub**: In-memory messaging

## 🔐 Security & Authentication

### Authentication Methods
- **Password-based**: Traditional username/password
- **Token-based**: JWT, API keys
- **OAuth 2.0**: Delegated authorization
- **Multi-factor**: Something you know/have/are

### Security Best Practices
- **HTTPS**: Encrypt in transit
- **Input Validation**: Sanitize all inputs
- **Authentication**: Verify identity
- **Authorization**: Control access
- **Rate Limiting**: Prevent abuse

## 📈 Monitoring & Observability

### Three Pillars
- **Metrics**: Time-series data (counters, gauges)
- **Logs**: Structured event records
- **Traces**: Request journey through system

### Key Metrics
- **RED**: Rate, Errors, Duration (services)
- **USE**: Utilization, Saturation, Errors (resources)
- **SLI/SLO**: Service Level Indicators/Objectives

## 🚢 Deployment & DevOps

### CI/CD Pipeline
- **CI**: Continuous Integration (build, test)
- **CD**: Continuous Deployment (automated release)
- **Stages**: Source → Build → Test → Deploy

### Deployment Strategies
- **Blue-Green**: Switch between environments
- **Canary**: Gradual traffic shifting
- **Rolling**: Sequential instance updates
- **Feature Flags**: Runtime feature control

### Containerization
- **Docker**: Application containerization
- **Kubernetes**: Container orchestration
- **Benefits**: Consistency, portability, scalability

## 📱 Mobile & Web Specific

### Mobile Considerations
- **Offline-First**: Work without connectivity
- **Push Notifications**: Re-engagement
- **Battery Optimization**: Efficient resource usage
- **Network Variability**: Handle poor connections

### Web Performance
- **CDN**: Content delivery networks
- **Caching**: Browser, proxy, application
- **Compression**: Reduce payload sizes
- **Progressive Loading**: Lazy loading, code splitting

## 🔢 Capacity Estimation

### Back-of-Envelope Calculations
- **Users**: DAU, MAU, concurrent users
- **QPS**: Queries per second (peak vs average)
- **Storage**: Data growth over time
- **Bandwidth**: Upload/download requirements

### Common Numbers
- **L1 cache**: 0.5 ns
- **RAM**: 100 ns
- **SSD**: 150 μs
- **Network**: 0.5 ms (same datacenter)
- **Disk**: 10 ms

## 🎓 Quiz Tips
- Know trade-offs between different architectural patterns
- Remember scalability strategies (horizontal vs vertical)
- Understand CAP theorem implications
- Know common caching patterns and when to use them
- Remember database types and their use cases
- Understand load balancing algorithms
- Know the difference between availability and reliability
- Remember the three pillars of observability
- Understand deployment strategies and their benefits
- Know capacity estimation techniques and common performance numbers