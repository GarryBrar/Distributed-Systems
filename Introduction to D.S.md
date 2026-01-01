---

---

> "A distributed system is one in which the failure of a computer you didn't even know existed can render your own computer unusable."
> 										- Leslie Lamport

In layman terms, a **Distributed System** is a group of nodes that cooperate by exchanging messages over communication links to achieve some task.

Why bother with Distributed Systems?
- Reliability - avoiding single node failures.
- Workload - ability to handle high workloads
- Some Systems are *Distributed by Nature*.

### 1.1) Communication
A major challenge with Distributed Systems is the communication between the nodes over the network. Although most communication is thought to be abstracted away, *abstract leaks* can occur, and understanding how networking works is key when this arises.

See [The Law of Leaky Abstractions](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/).

### 1.2) Coordination
How can we ensure synchronization and coordination across our nodes that will achieve a coherent and reliable outcome? These nodes do not have shared clocks, have network latency and may be attempting to solve a problem that requires concurrency. 

### 1.3) Scalability

*Load* is defined as anything that consumes the system's resources suhc as CPU, memory, and network bandwidth. 

The performance of an application represents how efficiently it can handle load, in other words, how well it can scale to handle increasing load.

Performance is typically measured in terms of throughput and response time.
	- *Throughput* is the number of requests processed per second by the application.
	- *Response Time* is the the time elapsed in seconds between sending a request to the application, and receiving a response.

Eventually, applications will reach their *capacity*, and the performance will either degrade or plateau, as shown in the figure below. 

![[Pasted image 20260101053717.png|center|350x300]]

### 1.4) Resiliency
Resiliency is measured on how well an application can perform while failures happen. 

This is often measured in *Availability*, which is the ratio defined as the amount of time the application can serve requests (*uptime*) divided by the total time measured (*uptime* plus *downtime*).

See the chart below to see how Availability is often described with nines. 

![[Pasted image 20260101054534.png|center|400x200]]

### 1.5) Maintainability

Majority of cost of software is spent after it's initial development int he form of fixing bugs, adding new features and operation. 

Applications often have teams dedicated to maintainability, which will be discussed in detail in later sections.

### 1.6) Anatomy of Distributed Systems

In the context of these notes, we will discuss distributed systems that implement some kind of business logic by having backend applications running on some commodity machines. Thus, you could say a distributed system is a group of software processes that communicate via *inter-process communication* (ICP) mechanisms. 

A *Service* implements one specific part of an overall system's capabilities.

At the core of a service, sits the *business logic* which exposes interfaces to communicate with the outside world.

Since processes can't call each other's interfaces directly *adapters* are required to connect IPC Mechanisms to service interfaces. This is done via APIs, *Application Programming Interfaces.*

