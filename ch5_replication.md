# Designing Data Intensive Applications

# Part 2 distributed data

Q: Why distribute data across >1 machines?

- scalability
	- while vertical scaling (more CPU/RAM), one OS 
	- horizontal scaling required coordination btwn nodes at software level 
		- subtopic: 
			- cloud computing
			- VMs
- fault tolerance
- latency
- availability

Q: What are methods for distributing data across multiple nodes?
- Replication
	- copies of same data maintained on several different nodes
	- provides redundancy, fault tolerance, availability, low latency 
- Partitioning 
	- a big data set is split into subsets, (partitions) via sharding
NOTE: Replication and Partitioning often go together;
Ch 5 discussion replication of 1 complete data set ONLY

## Ch 5 - Replication (p151)

#### Thesis

- replication is hard because data will change and things will go wrong
	- All sorts of nasty concurrency bugs
	- What if a node goes offline?
	- What if there's a network interruption?

#### Summary

Three approaches:

1. Single-leader replication
	- only leader writes
	- replicas read from a replication log (aka change stream) to update
	```	
		- BUT clients can read from leader OR from replica
		Q: ** wait what if the leader has updated but relica has not?? ** 
		A: transaction is not complete (eg client not given ok, reads not permitted to other users) until [all?] synchronous  followers respond w/ OK
		- Q: are we assuming that reads are ONLY from leader or sync followers, and async followers (eg eventual consistency) are NOT read from?
	```
	- some tradeoffs:
		- fully async followers cannot guarantee data is durable - if there's a node or network failure before a change is made in a replica, that data is lost
		- however that may still b pref. b/c fully async = faster writes
		(more tradeoffs on 161 - replication lag) 
	(for consistency and consensus, see Ch 9)

	- not just DBs, also msg queus, msg brokers (Kafka)

	- write ahead logs
	- 163 read after write consistency
	- 165 monotonic reads - a guarantee that reading from two replicas will result in the same result (sometimes ensured by saying reader X can only read from replica Y)
	- consistent prefix reads (p166 - baseball paper) - prevent replication lag anomolies w/ 3 parties, where an observer misses the direction of causation b/c of time lags



2. Mutli-leader replication (168)zzzz
3. Leaderless replication



- What are the trade-offs?
	- consistency guarantees?

~~
Maybe we'll have time to talk about eventual consistency, etc, but let's not focus there for today
- with async replication there is Replication Lag

### Sync vs Async Replication
 


#### There's more!

Leaders and Followers

Problems w/ Replication Lag

Multi-Leader Replication

Leaderless Replication

References:


