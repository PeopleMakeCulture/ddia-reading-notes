# Designing Data Intensive Applications

## Ch 3 - 

#### Data Structures that power your DB

#### Thesis:
logs are cool (append only sequence of records)

#### Hash Indexes

to save space, log-based key-value-(idx) stores periodically undergo compaction -- prev data seg is locked, only most recent value per key is written to new compacted segment

appending + segment merging are sequential writes, much faster than updating key-values in place, which is random writes;

concurrency and crash recovery are also simpler 

#### SortedStringTables && LogStructuredMerge-Trees

- hashmap limits to overcome:
	1. db must fit in memory
	2. range quiers are not efficient

What is it?
- key-value keys sorted by key NOT by chronology
- each key only appears once per segment (see: compaction)
- segments are merged using an algo similar to mergesort (refresher??)
- because keys are sorted strings, we no longer need to maintain an in-memory idex of ALL keys, just idexes for SOME keys (eg one per few kilobytes)

Q: how do we do sequential writes && still meet this req?

#### Constructing and Maintaining SSTables p78

4 steps:

1. use an in memory tree (_memtable_) to store key-val pairs (eg red black tree) [LINK: ]
2. when memtable hits some size threshold (a few MB?), write it out to a sorted string table (SSTable)
3. read requests first look in memory, then in reverse write order
4. merge, compact, and delete in background

for reliability, also keep log on disk of all writes that go into in memory tree


#### Making an LSMTree out of SSTables 78

Performance Optimizations
- what about keys that don't exist? - Bloom filters [15]

p84 issues - finite bandwidth split between compaction && write/read

Links: 2, 6, 7, 9 (Google's Bigtable Paper, which intros memtable, SSTable: https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf)