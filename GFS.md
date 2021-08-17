[TOC]
# GFS

## why is it hard?

when we want to get a good aggregate performance we eventually hit with CAP theorem.

```mermaid
flowchart TD
performance -> sharding
sharding -> tolerance
tolerance -> replication
replication -> inconsistency
inconsistency -> low performance
```
a good consistency is as if we are communicating to a single server for a particular distributed system.all operation as if they are executed sequentially one at a time and requests sees data that reflects all the previous operation in order. a bad replication design would be servers received multiple request and process them with different sequence, ie server A process request 1 then request 2 and server B process request 2 then request 1.

## how GFS address this?
