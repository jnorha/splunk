---
Title: PLA1100 What the HEC? Disposable Indexers, Optimizing Platform Usage
---

## PLA1100 Elastic SHCs and DIsposable Indexers

#### Arcitecture BYO AWS 

`compressed = true`: heavy forwarder config on TCP connections to reduce the amount of traffic between Splunk and Splunk,  Heavy Forwarder to Indexers. Compression can also reduce the fluctuations in volume on your indexers. 
<br>
Compression also increased the indexer idle time - so they had less stress.
<br>
Network load balancers vs Application Load Balancers. Network Load Balancers can do tls verification now which can be used inplace of ssl on the Application Load Balancers. Network load balancers are also much more stable and consistent on connections. 
<br>
Intelligent clients is an important part to buffer your ingest nodes. Otherwise they may get TCP stuck and laser beam of death to crazy thruput. 
<br>
Turning off search head cluster nodes when you don't need them (This is my presto thing!!!)
<br>
Turning off search heads is very hard. Really only works in a fully automated environment where you are hyper aware of the needs and usage. They automate out reports every 15 minutes which provide everything the "searchers" need from the data collection. 
<br>
Have to have search head captain to control the cluster. Code is available to enable the lifecycle hook. 

#### For us

**This one's crazy** - want to do presto or ephemeral splunk look at this code and dig into using AWS as an option. Commented code on how it spins up/spins down the cluster. Check out the load balancing options though. 