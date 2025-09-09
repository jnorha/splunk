---
Title: PLA1539 Best Practices for ITSI and Observability
---

## PLA1539 Best Practices 

#### ITSI

Best Practices from last year
* Keep your kpi numbers small
* keep focus on golden patterns for true trouble detection
* Base searches
* Check statistical processes that are actually happening behind the searches - efficiency focus
* Content pack for monitoring and Alerting
* Take out the default NEAP from the defaults. 

* Deep dive to give additional information about the incident or service health. If they lane doesnt help with the help description, rip it out.

<br>
Entity based alerting vs Aggregate. Use Aggregate when you can since it's the overall view. 
<br>
Future future will be per entity based thresholds. Right now, thresholds are the same for every entity and cannot be adaptive. 
<br>
Per Entity in preview 4.19 and includes entity level adaptive thresholds. 

* have to be considerate of resource usage and scale since these will be happening for every entity now - not just the aggregate. 

#### ITSI COnfiguration Assistant 
Help you find misconfigured KPI's. 

* suggests optimization based on how much time they are not normal
* will give AI recommendations for thresholds
* Entity duplication GGAAHAHHHHHAAAAAAAAAAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH
    * maybe fix up the current retirement policy? 
* Speed up the aggregation portion against the notable event, correlation search optimization- Explain later to Z (not real time)
* KPI time adjustment. Daylight Savings, etc. Can be done in bulk. 
* ITSI is based on a lot of Queue's - new config helper can refresh queue's with changes
    * Stored in KV stores.
    * ITSI refresh Queue
    * Notable Event Actions Queue
* Queue Stuff really depends on how much action you're taking
* This is done through the Splunk Lookup Editor. The actions are saved in the event Actions Lookup. 
* Check out the Refresh Queue explorer to see how many refreshes are occuring 

#### AI Use in ITSI
Python for Scientific Learning, MLTK, Java
<br>
Is this a splunk specific model? f
<br>

**Drift Detection** - as KPI's are retrained adaptively over time this can be a big problem. Configuring Drift Detection to create notable events for admins to then go and visit how the thresholds have been changing over time. 

<br>

Bi-Directional Ticketing: cool thing that we will never do cause we too scared to enable touching across the systems. Helpdesk API - do actions. <br>
This is a setting that you can enable to boost up the action in the NEAP. Episode config and control. 

<br>


#### For Us

1. Entity duplication fixing and automatic understanding/mediating - can we have it understand training environments??????
2. Update KPI's in bulk through config Assitant
3. **Help me build up the notable event aggregation policies to link drilldowns and deep dives the the appropriate episodes!**
4. Integrate the MLTK for extra config assistant help and extra machine learning models for specific use cases. 