# Designing Data Intensive Applications

## Ch 1 - Data Models and Query Languages (pp27 - 63)

### Thesis


### Summary (63-64)

- 3 Modern data models
    1. Relational DBs - classic SQL, good for many to many relationships, eg business data processing (sales, inventory)
    2. Document DBs - best for large self-contained documents where relationships between documents are rare (e.g. medical records?)
    3. Graph data - everything can be related to everything (eg facebook?) no enforced data schema

- Even DBs that don't require explicit data schemas still assume some structure; it's handled implicitly at read instead of explicitly at write (implicit schemas can lead to type-errors)

49 - data stores for large haldron colllider (petbytes^2) custom hardware solutions
 
### BWTM!

- Relational Model vs Document Model (SQL vs NoSQL)
    - relationshal model - SQL  - Edgar Codd in 1970 [1]
    - data is organized into _relations_ eg _tables_
- Birth of NoSQL
    - challenges: SQL dbs choke on too much data/too fast
    - challenge: relational dbs sometimes too prescriptive; some apps benefit from a more dynamic/expressive data model [5??]
- Object Relational Mismatch
    - object oriented programing requires an awkward intermediate layer (ORM) to turn relations from tables/rows/columns into objects

Examples:
Linked In profiles in SQL and NOSQL

- Many-to-1 and Many-to-Many Relationships
    - DB **normalization** is a cool thing relational dbs can do(33)
    - joining is easy in a relational db
    - joining is hard in a document db 

- Are Document DBs repeating history?
    - a "relation"(table) is simply a list of tuples"rows"(37)
    - query optimizers decide which parts to execute in what order and what indexes to use

    - see [18] for research regarding developing query optimizers

- Relational vs Document DBs Today (38)
    - convergence w/ XML? (41)

Query Langs for Data (42)

    - queries are relational algebra 
    SQL is built over relational algebra, it's declarative (i want this result), not imperative(i want this process executed)
    - declarative queries can be run in parallel - order of operations is not guaranteed

- Declarative Queries on the Web (skip)
    - CSS and web stuff

- MapReduce Querying (skip)
    - MongoDB's mapreduce is somewhere between declarative SQL and imperative programming API

Graphlike Data Models (49)
    - vertices (nodes, eg people, webpages), edges (connections, links)
    - (58) semantic web && triple stores (this is pretty esoteric)

- Property Graphs
- Cypher Query Lang
- Graph Queries in SQL
- Triple Stores in SPARQL
- The DataLog (Foundation)
    - manuel uses datalog
    - manuel implemented a naive datalog

### References


# Discussion Qs:
- What are benefits of SQL/NoSQL 
- What do we want to think about if we're designing linkedin?
- p34 has some more good discussion Qs:
    - design a DB for organizations/schools as entitites
    - design a Data model update to allow recommendations on LinkedIn
- What buzzy new DBs are folks hearing about lately? How do they fit into or challenge this model?

Recursive Query - SPARQL - can query 

- might want to use db for querying even if you don't need to presist the data

- graph QL is more like an API for getting data

**if you want some great SQL books, look up joe celko's books**

- elastic search as document database for `tretreecenter.com`