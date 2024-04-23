# COVID-19 Modeling in Supermarkets

By: Rebecca Flach and Daniel Quinteros

## Abstract
In this paper, we use agent based models to investigate risk factors for COVID transmission in supermarkets and similar environments. 

## Methodology

In the study we replicated [1], the authors propose an agent-based model to calculate total exposure time, representing the duration customers spend near infected individuals, and estimate infection rates using a basic transmission model.

#### Store Graph

Supermarket layouts are represented as networks, wherein nodes correspond to different zones categorized into four types: entrance, exit, till, and shelf.

#### Customer Mobility

Customers enter the store at a constant arrival rate λ, starting from the entrance node. Each customer is assigned a random path through the supermarket from a set of paths generated using synthetic data. At each node along their path, customers pause for a random duration T, representing the time spent selecting items from the shelf. After this waiting period, customers proceed to the next node in their path. Upon reaching the exit node, customers are removed from the simulation.

#### Virus Transmission

Upon entering the store, customers are either infectious or susceptible. The proportion of infectious customers is determined by probability p. Furthermore, the virus transmission rate is denoted by β. We assume that susceptible customers become infected in proportion to their total exposure time E, defined as the cumulative duration during which susceptible customers are in the same zone as infectious customers. Consequently, the number of infections is given by the transmission rate β multiplied by the total exposure time E.

For our initial simulation, our default parameters are as follows:
| Parameter | Default value |
| -------- | ------- |
| Arrival rate (λ) | 2.55 customer/min |
| Mean wait time at each node (τ) | 0.2 min |
| Percentage of infected customers (p) | 0.11% |
| Transmission rate (β) | 1.41e-9 per min |
| Length of opening hours (H) | 14 hours |

After running 1000 simulations, each of which simulates a day in the synthetic store, our results provided us with the following metric:
| Metric | Mean |
| -------- | ------- |
| Total exposure time | (FILL) |

With the total exposure time being on average (FILL) min/day, and the transmission rate β = 1.41e-9 per min, we can multiply the two to find that the average number of infections per day is (FILL).

Following this, we investigate some common COVID exposure interventions such as:

* Controlling the rate of customer arrival
    * Done by performing a parameter sweep, varying the rate at which customers enter the store from 0 to 2.55 customers/min.

* Restricting maximum number of customers in the store
    * Done by performing a parameter sweep, varying the maximum store capacity from 1 to 30 customers.

* Face masks
    * Done by implementing a fask mask policy via a reduction in the transmission rate. In this case, mulitply the transmission rate by a factor of 0.17. 

* One-way aisle layout
    * Done by changing the store graph to a directed graph, where some edges are uni-directional. 

## Results

![max_capacity_figure](https://github.com/RebeccaFlach/COVID-modeling/assets/47285707/37f0883e-f6d0-426b-85fe-17559ce86f73)

**Figure 1: Infections v. Maximum Capacity**, representing the relationship between the average number of infections per day vs the maximum number of customers allowed in the store. We performed a parameter sweep to investigate the impacts of changing the maximum capacity in the store, ranging from 1 to 30. The remaining parameters are set to their default values. 

### Interpretation



## Extension

![alt text](image.png)


## Causes for concern

7) Identify causes for concern.  Review the criteria for what makes a good project and identify any areas where your project might be problematic.

## Annotated Bibliography
[1] [**Modeling COVID-19 transmission in supermarkets using an agent-based model**](https://www.semanticscholar.org/reader/17a2627fca7585df99f9d214831992a3756ed772) by Fabian Ying, Neave O’Clery

In this paper, the authors investigate how COVID is transmitted within a supermarket, and use their model to determine the most effective interventions to decrease spread. In their primary experiment, they model a small supermarket using a graph, where each node is a place where a customer would stop and interact with the shelves, register, or other important point. They then create agents to represent customers, each with a random path through the store and time spent at each location. Infection risk is estimated by the amount of time a susceptible agent spends in proximity to an infected agent. They find that transmission risk is increased by bottleneck points, like the registers, and that limiting the number of customers in the store is an effective way to reduce transmission.

## Next steps
8) Outline next steps.  For each team member, what do you plan to work on immediately?  For the team, what do you think you can get done in the next week?  Consider using GitHub Projects to make a kanban board to track tasks.

 
