---
Title: PLA1405 Splunk MCP Server
---

## PLA1405 Building AI agents with Splunk MCP Server

#### Agent Architecture

Multi agent architecture to have an agent that controls other agents and thier actions. <br>
Buidling an agent:

* Set Objective: Security, data, itops, analyst
* choose the LLM based on systmeneeds and requirements
* add tools: web, apis, mcp servers for the LLM to use
* Define the type, simple, reflex agents to advanced learning and decision agents. 
* Loop: Percieve --> Reason --> Act --> Observe --> 
* Keys are:
    * Context
    * Cognition
    * Action

<br>

Agent Control flow: Router vs Fully Autonomous. Autonomous needs guardrails for how it's using tools and its decision points. Router you can control tool executions and times to call/use. Actions against these tools and enpoints.

<br>

Function calling vs Intent Classification. Intent classification would be better to allow LLM to choose which tool is best for the user needs. Also can pass more advanced params using teh Intent Classification. 
<br>
Memory is important for these intent based decisions so it doesn't repeat actions or impede itself in it's resource usage. 

<br>
Feedback and Learning loops can be helpful to "train" agent on good responses vs bad responses. 
<br>
Horizontal vs Vertical architectures - A2A communication (agent to agent). A2A server is collection of Agent Cards which describe what they do, Tools and APIs are included in the MCP layer. Control token usage and other resource factors on MCP layer. 
<br>

Make sure to also include drift monitoring for the Guardrails on an agent. Over time they may go cray cray. 
<br>
LangSmith & Otel for collection to O11y Cloud for genAI and monitoring the actual agents themselves. Langraph is used for the Demo.  
<br>
PydanticAI, OpenAI, LLama Index... all good agent building platforms. Really depends on what the agent wants to do. 
<br>
Can have input/output guardrails specified in Agent build. 
<br>
Run Search, Get Knowledge Objects, Get Indexes, etc. 
<br>
Splunk Cloud you can use SCS (EKS) - uses the SCS Gateway if you want to build your own interface. Can also use splunk web & Rest API. Configuration based for Splunk Cloud. 
<br>

Can **integrate with the MLTK** to take off resource load and arm your AI agent with additional models it can use to gain context rather than execute huge searches itself. 
<br>

Demo code is available in git. 

<br>

Demo breakdown
1. Incident Analsis - analyzes any incoming incidents
2. Splunk Search - MCP executes searches to gain additional context
3. Threat Assessment - reviews context to assess threat level
4. Automated Response based on Threat Level - low level threat maybe just ticket, high level teams message or automated action against other security tools. 
5. Context Persistence: saves complete workflow to history database

<br>

Agent is just a python script. 

<br>


#### For Us
Tools: Splunk Cloud, CCD, Helpdesk for ticket history?, can we also have it summarize incident etc to then build the HDR?, Manx <br>
We could build an incident or some sort of summary index that the "leader" node has access to and builds actions against the conten in those events. Real time monitoring of that index? Event Actions...?

