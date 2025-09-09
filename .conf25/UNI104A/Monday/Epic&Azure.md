---
Title: Meeting with Azure 
---

## Meeting notes on Azure integration directions

#### Epic Q's

* Azure data lake, smart store, federated search - what can we do now and why should we? 

- blob storage is current one they're going with first, future Data Lake etc. 
- Data replay already available. To pull data for specific periods of time. 

* Data manager & Graph API: break down differences between entra, azure resources, hybrid resources.

* Otel in Azure - best way to approach and key benefits/resources with greatest W's

UCF - what Datamanager is currently built on vs older azure functions. More elastic like the azure functions vs the specific call times. 

<br>

Essentially OTEL managed K8s service running in splunk cloud 
<br>

Data Manager:
 
* data in flight
* data in destination

<br>

Federated search against Blob coming - should probably be how we do things. 

<br>

MSCS vs UCF: UCF reads partition number automatically to optimize throughput. 

<br>

`Otel`: best way to do it is EventHub will be for logs where as OTEL collector will do metrics and traces. <br>
Most people are using eventhub. Not necesarily better for App Insights - OTEL will be good for that but more specifically for application performance. OTEL does read directly from App Service API - gives traces & metrics automatically. App service trees will build automatically. ITSI can be built against Business service tree. 

<br>

Thousand Eyes as latency detection along all the hops through the whole service. Collect logs from these hops along the way (SD Wind routes around that). Thousand Eyes monitors the metrics you don't own - visibility outside. 

<br>

REST/GRAPH API with Entra will throttle and be bad, use UCF - O365 one Add-on is only real way to get that stuff, it will generally throttle. 

<br>

Splunk Add-on for microsoft secruity - Defender & Intune. Defender can write full timeline to eventhub and there is a CIM for it. Use UCF to read from eventhub. Intune is also best to use eventhub. Anything that integrates Azure Monitor will produce Azure Eventhub. <br>

Pipeline can do some pulling of GUID to resource ID etc. <br> 

ITSI is native connection for Thousand Eyes. O11y metrics can be read by ITSI. <br>
