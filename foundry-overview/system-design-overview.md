---
description: Overview of the Foundry Message-oriented middleware (MoM) system
---

# System Design Overview

#### System design <a id="129408862"></a>

Message-oriented middleware \(MoM\) systems such as Apache ActiveMQ allow designing loosely coupled distributed systems that can run in heterogeneous distributed computer environments. Use of MoM in Foundry allows horizontal scaling of the system by adding new consumer nodes on demand for increased load. It allows for event-driven, reactive workflow management orchestrated by messages sent/received from consumers that are self-contained processing units \(microservices\) to/from a message dispatcher component. The persistent message queues also make the system resilient to computer crashes and outages, as unfinished messages resulting from a computer failure on a consumer node remain in the message queue and are either picked up by another consumer node \(if any are running\) or reprocessed when the consumer node restarts.

The overall system consists of a dispatcher, one or more consumer container\(s\) and a command-line manager interface. The dispatcher listens to the dispatcher message queue for incoming messages from consumer container instance\(s\). Using its configured workflow, it dispatches messages to the message queue for the listening consumer container\(s\). The consumer container coordinates a set of configured consumers that perform predefined operation\(s\) of a document indicated by the message they receive from the dispatcher and ingestors. The harvesters/ingestors are specialized consumers that are responsible for the retrieval of the original data as configured by a harvest descriptor JSON file of the corresponding source. They are triggered by the manager application. These component interactions are summarized in Figure 1 and an example of a specific pipeline is given in the section below.

![Figure 1: Foundry dispatcher and consumer container unified modeling language activity diagram.](../.gitbook/assets/image%20%2812%29.png)

