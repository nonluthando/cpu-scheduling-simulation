# cpu-scheduling-simulation
Java-based simulation comparing FCFS and SJF scheduling algorithms, analysing waiting time, turnaround time, and response time under varying system load.

## Overview

This project extends a provided coursework codebase to run an experimental comparison of two classic CPU scheduling algorithms: First Come First Served (FCFS) and Shortest Job First (SJF).

The original code supplied a basic bar-themed concurrency model. The extensions added in this project enable scheduling behaviour, coordinated simulation execution, metric collection, and experimental analysis under varying system load.


## Project Goals
	•	Enable a runnable scheduling simulation using the provided framework
	•	Implement and compare FCFS and SJF scheduling strategies
	•	Collect standard operating systems performance metrics
	•	Analyse how scheduling behaviour changes as system load increases


## Simulation 

The simulation represents a single-server system:
	•	Patrons represent processes arriving over time
	•	DrinkOrders represent individual units of work (CPU bursts)
	•	The Barman represents the CPU
	•	A shared queue represents the ready queue

Patrons arrive at staggered times, submit one or more drink orders, and wait until all orders have been processed.


## Scheduling Algorithms

### First Come First Served (FCFS)

FCFS processes drink orders strictly in order of arrival.
Implemented using a FIFO LinkedBlockingQueue.

### Shortest Job First (SJF)

SJF prioritises drink orders with the shortest execution time.
Implemented using a PriorityBlockingQueue ordered by execution time.

The scheduling policy is selected at runtime, allowing the same execution logic to support multiple algorithms.


## Extensions and Contributions

The following functionality was added to the provided coursework code:
	•	Scheduling behaviour using concurrent queue selection
	•	Thread start coordination using CountDownLatch
	•	Metric collection for turnaround time, waiting time, and response time
	•	File-based logging of experimental results
	•	Repeated experimental runs under varying patron counts

## Concurrency and Synchronisation
	•	All threads synchronise at startup to avoid bias from thread creation order
	•	Blocking queues manage safe communication between patrons and the server
	•	File output is synchronised to prevent race conditions
	•	Execution time is simulated using controlled thread sleeping


## Metrics Collected

For each patron, the following metrics are recorded:
	•	Turnaround Time: time from order submission to final completion
	•	Waiting Time: turnaround time minus total execution time
	•	Response Time: time from arrival to completion of the first order


## Results Summary

Shortest Job First consistently achieved lower average waiting time and turnaround time than First Come First Served, particularly as system load increased. Response time differences were minimal in this simulation, illustrating the trade-off between fairness and efficiency in scheduling systems.


## Limitations
	•	Single-server simulation only
	•	No preemptive scheduling
	•	No context-switch overhead modelling
	•	Starvation in SJF is not mitigated

## Technologies Used
	•	Java
	•	Thread-based concurrency
	•	Blocking queues and synchronisation primitives

## Academic Context

This project was completed as part of an Operating Systems course using a provided starter codebase. The work presented here focuses on extending that code to support experimental evaluation and analysis of scheduling algorithms.

