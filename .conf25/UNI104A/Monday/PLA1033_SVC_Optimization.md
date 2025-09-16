---
Title: Optimizing SVC Performance
---

## SVC Optimization

#### Metrics Used

* Leading:
    * Ingest Queue Percentage. Blocked Queues, HEC 503
    * Search Latency: time it takes for search to be scheduled and to run
    * High search concurreny - splunk prioritizes ingest over search, so search can be a good indicator for smoke

* Lagging:
    * Smartbus Latency: highly scalable, durable, queueing and buffering system between typing and indexing pipelines
    * keep this smartbus latency low.
    * Skipped searches - occurs when capacity is fully utilized meaning scheduled searches are being prevented. 
    * CPU seconds by workload category
    * **normalized 1-min load average**. Represents how many tasks on average each CPU thread is being asked to process. Want this to be ~0.8

* Ingetest:
    * Dont have everyting written to disk at index time.
    * **Minimize Cache Turn** - amount of data physically sitting available in memory. Want to maximize the amount of data sitting in cache that is readily accessible. 

How old were these? On AWS?


`cofilter` - finds things firing together. 


#### For us

