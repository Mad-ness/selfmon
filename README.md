# selfmon
Provides overall health status of nodes over a distributed system without decentralization

## Purpose
This project is an aim to build a decentralized solution in a distributed system.

## How it works
Every node of a distributed system works as a client. In order to tell others some details about itself and provide required data, each node writes its data to a key-value store. Those which required such data just request the data from the key-value store. This approarch eliminates the need to walk throughout each client node and clients report its data when it is needed.

### Example of usage
This is designed for a distributed system such as CDN. CDN has multiple cache nodes. In order to pass traffic on them, a router should known a status of each one. So every cache system reports its state into a key-value storage and a router just takes that data. If no updates have been uploaded from a node, that node is excluded from a service.

## Components
A core of that solution is a key-value storage Etcd. Etcd is registered to DNS servers, so clients of that store do not care about how many members Etcd has and their hostnames, or ip addresses. 
Every client node runs a program which reports performance data to the key-value store.
