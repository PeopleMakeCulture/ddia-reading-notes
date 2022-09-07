# Designing Data Intensive Applications

## Ch 4 - data encoding and dataflow

#### Thesis

#### Summary (139)

Data needs to be encoded as bytes on disk. 

Encoding methods affect application architecure 

Programming language specific encoding langauges are not good for forward/backward compatibility -- which is why others emerged

Text-based: JSON, XML, CSV are widespread
Cons: vague about datatypes

Binary, schema-driven: Trift, Protocol Buffers, Avro
- compact && efficient
Pros: clearly defined forward/backward compatibility 
Cons: needs to be decoded for humans  

Data flows!!

-  dbs: direct encode on write, process reading from db will decode on read

- with RPC (remote procedure calls) and REST (REpresentational State Transfer) APIs, client encodes request, server decodes req and encodes response, client decodes response

- async msg passing (brokers or actors) sender encodes, recipient decodes, nodes communicate via encoded msgs

## But Wait!

Two encodings:
- in memory (usually pointers)
- over network (byte sequence)

Lang-spec: python has pickle library

#### Thrift && Protocol - Jing 117 (diagram 4-1)

- modificication of binary encodings for JSON/XML like MessagePack
- user specifics schema in an IDL (interface definition language) - struct/msg that defines the schema

- Thrift: efficiency comes from not encoding the schema

- Thrift CompactProtocol: 
- like above, but: 
- fieldtag && fieldtype encoded into 1 byte
- ints are encoded
- sub tag/types in lists are also encoded in 1 byte

Protocol Buffers
