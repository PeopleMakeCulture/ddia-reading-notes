# Designing Data Intensive Applications

## Ch 1 - Reliable, Scalable, Maintainable Applications (pp3 - 23)

#### Thesis

 *Applications use data systems to store, stash, search, and process data (dbs, caches, search indexes, stream processing, and batch processing).These underlying data systems strive to be reliable, scalable, and maintainable*

#### Summary

- applications must meet _functional requirements_ (what it should do, eg store, search, retrieve, process) and _non-functional requirements_ (how it should be, eg secure, compliant, *R*eliable, *Scalable*, *Maintainable*)

- It's hard to make things RSM, but there are some patterns, which this book will discuss

- **Reliable**: _Faults_ happen due to _hardware_ (hard disk crash, power blackouts, etc can be addressed w/ redundancy), _software_, and _human_ errors. Good data systems apply **fault tolerance techniques** to hide these from the end user. 

- **Scalable**: Good systems maintain performance as load increases

- **Maintainable**: Good systems make life easier for future engineers

## But Wait, There's More!

### Reliability (pp6-11)
- software bugs and human errors are best mitigated w/ good design && testing??

### Scalability (pp10-18)
- _load parameters_ quantify system load
- _throughput_, eg num_records_processed_per_second, is a common load parameter for batch processing
- _response time_, as measured in percentiles, may be prefered for web apps
- _scaling up vs scaling out_ a system can either move to a more powerful machine or spread load accross more machines (p17)
- _elastic_ systems dynamically size up or down depending on load (17)

### Maintainability (pp189-22)


### Further reading 

Kreps, Getting Real About Distributed System Reliability: https://blog.empathybox.com/post/19574936361/getting-real-about-distributed-system-reliability (Coda: DSOps is hard, but Distributed Systems as a Service DSaaS (eg Kafka) means most developers don't really need to think about it)


