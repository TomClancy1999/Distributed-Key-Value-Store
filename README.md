# Distributed Key-Value Store

A fault-tolerant distributed key-value store built in Go using the Raft consensus protocol. The system provides strongly consistent replicated storage, automatic leader election, log replication, snapshot-based state compaction, and dynamic shard migration across distributed nodes.

## Overview

This project implements a distributed storage system based on the replicated state machine model. Client requests are routed through a Raft leader and replicated across multiple nodes to ensure consistency and fault tolerance. The storage layer supports dynamic shard assignment and reconfiguration, allowing the cluster to rebalance load and migrate data transparently as membership changes.

### Key Features

- **Raft Consensus**
  - Leader election
  - Log replication
  - Heartbeat management
  - Safety and consistency guarantees

- **Fault Tolerance**
  - Automatic leader failover
  - Recovery after node crashes
  - Network partition handling
  - Consistent state recovery

- **Snapshotting**
  - Log compaction
  - Persistent state recovery
  - Reduced storage overhead

- **Sharded Storage**
  - Dynamic shard allocation
  - Transparent shard migration
  - Load balancing across nodes
  - Cluster reconfiguration support

- **Concurrent Request Processing**
  - Parallel client request handling
  - High-throughput replication pipeline
  - Consistent request execution under failures

## Architecture

Client requests are submitted to the current Raft leader. The leader appends operations to its replicated log and propagates them to follower nodes. Once a majority of replicas acknowledge the entry, the operation is committed and applied to the state machine.

The storage layer partitions data into shards that can be reassigned between replica groups. During reconfiguration, shard ownership is transferred while preserving consistency and availability.

## Technical Highlights

- Implemented replicated state machines using the Raft consensus algorithm
- Designed leader election, log replication, snapshotting, and recovery mechanisms
- Built a sharded key-value storage architecture with dynamic reconfiguration
- Supported shard migration and load balancing across distributed nodes
- Validated correctness under node failures, leader failover, and network partitions
- Sustained high request throughput during fault-injection and cluster reconfiguration testing

## Technology Stack

- Go
- Raft
- RPC
- Sharding
- Distributed Systems

## Testing

The system was validated through extensive fault-injection testing, including:

- Leader crashes and failover scenarios
- Follower recovery
- Network partitions and rejoin events
- Snapshot installation and state restoration
- Shard migration during cluster reconfiguration

These tests verify that the cluster maintains consistency, availability, and correct operation under adverse conditions.

## Learning Outcomes

This project provided hands-on experience with:

- Distributed consensus
- Replicated state machines
- Fault-tolerant system design
- Consistency and availability trade-offs
- Cluster reconfiguration
- Data partitioning and migration
- Concurrent system implementation

## Future Improvements

- Metrics and observability dashboard
- gRPC-based communication layer
- Multi-Raft optimization
- Persistent storage engine integration
- Automated deployment with container orchestration

## License

This project is intended for educational and research purposes.
