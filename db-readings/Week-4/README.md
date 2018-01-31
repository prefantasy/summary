
## <a name='system-design'> Classic System Design

* [A History and Evaluation of System R](http://www.cs.ubc.ca/~rap/teaching/504/2010/readings/history-of-system-r.pdf) (1981): There were System R from IBM and Ingres from Berkeley, two systems that showed relational database was feasible. This paper describes System R. It is impressive and scary to note that the internals of relational database systems in 2012 look a lot like System R in 1981.

* [The Google File System](http://research.google.com/archive/gfs.html) (2003) and [Bigtable: A Distributed Storage System for Structured Data](http://research.google.com/archive/bigtable.html) (2006): Two core components of Google's data infrastructure. GFS is an append-only distributed file system for large sequential reads (data-intensive applications). BigTable is high-performance distributed data store that builds on GFS. One way to think about it is that GFS is optimized for high throughput, and BigTable explains how to build a low-latency data store on top of GFS. Some of these might have been replaced by newer proprietary technologies internal to Google, but the ideas stand.

* [Chord: A Scalable Peer-to-peer Lookup Service for Internet Applications](http://www.cs.berkeley.edu/~rxin/db-papers/Chord-DHT.pdf) (2001) and [Dynamo: Amazon’s Highly Available Key-value Store](http://www.cs.berkeley.edu/~rxin/db-papers/Dynamo.pdf) (2007): Chord was born in the days when distributed hash tables was a hot research. It does one thing, and does it really well: how to look up the location of a key in a completely distributed setting (peer-to-peer) using consistent hashing. The Dynamo paper explains how to build a distributed key-value store using Chord. Note some design decisions change from Chord to Dynamo, e.g. finger table O(logN) vs O(N), because in Dynamo's case, Amazon has more control over nodes in a data center, while Chord assumes peer-to-peer nodes in wide area networks.