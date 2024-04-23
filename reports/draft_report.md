# Investigating COVID-19 Transmission in Supermarkets

By: Rebecca Flach and Daniel Quinteros

## Abstract
In this paper, we use agent-based models to investigate risk factors for COVID transmission in supermarkets and similar environments.

## Methodology

We replicated the expirements conducted in **Modeling COVID-19 transmission in supermarkets using an agent-based model** [1], where the authors propose an agent-based model to calculate total exposure time, representing the duration customers spend near infected individuals, and estimate infection rates using a basic transmission model.

#### Store Graph

Supermarket layouts are depicted as networks, where nodes correspond to different zones categorized into four types: entrance, exit, till, and shelf.

![store_network](https://github.com/RebeccaFlach/covid-modeling/assets/47285707/3f6a30cc-4356-48cb-869a-645037e10851)

**Figure 1: Store network visualization**, with the nodes defined by:
| Zone Type | Node(s) |
| -------- | ------- |
| Entrance | 39, 40, 41 |
| Till | 33, 34, 35 |
| Exit | 42 |
| Shelf | All other undefined nodes |

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

After running 1000 simulations, each simulating a day in the synthetic store, our results provided us with the following metric:
| Metric | Mean |
| -------- | ------- |
| Total exposure time | 5.84 min |

With the total exposure time averaging 5.84 min/day, and the transmission rate β = 1.41e-9 per min, we can multiply the two to find the average number of infections per day.
| Metric | Mean |
| -------- | ------- |
| Number of Infections (per day) | 8.23e-9 |

Additionally, our model allows us to log the mean exposure time in each zone. From this heatmap, we can investigate any possible 'hotspots' that could be mitigated.

![initial_heatmap](https://github.com/RebeccaFlach/covid-modeling/assets/47285707/5bf27058-0087-4c44-b4f2-94ee5b296b73)

**Figure 2: Store network heatmap visualization** based on mean exposure time in each zone. The color ranges from black to bright red. The brighter the red, the higher the average exposure time is in that zone.

Following this, we explore some common COVID-19 exposure interventions such as:

* Controlling the rate of customer arrival
    * We perform a parameter sweep, varying the rate at which customers enter the store from 0 to 2.5 customers/min.

* Restricting maximum number of customers in the store
    * We perform a parameter sweep, varying the maximum store capacity from 1 to 30 customers.

* Face masks
    * We implement a face mask policy by reducing the transmission rate. In this case, we multiply the transmission rate by a factor of 0.17.

* One-way aisle layout
    * We change the store graph to a directed graph, where some edges are uni-directional. 

## Results

### Customer Arrival Rate

![arrival_rate_figure](https://github.com/RebeccaFlach/covid-modeling/assets/47285707/dce121a0-2e7c-43b0-a068-6aa552deaa68)

**Figure 3: Infections v. Infections v. Customer Arrival Rate**, representing the relationship between the average number of infections per day vs. the rate at which customers enter the store. We perform a parameter sweep to investigate the impacts of changing the arrival rate, ranging from 0.1 to 2.5. The remaining parameters are set to their default values.

### Store Maximum Capacity

![max_capacity_figure](https://github.com/RebeccaFlach/COVID-modeling/assets/47285707/37f0883e-f6d0-426b-85fe-17559ce86f73)

**Figure 4: Infections v. Maximum Capacity**, representing the relationship between the average number of infections per day vs. the maximum number of customers allowed in the store. We perform a parameter sweep to investigate the impacts of changing the maximum capacity in the store, ranging from 1 to 30. The remaining parameters are set to their default values.
### Face Masks

We implement a face mask policy by reducing the transmission rate. This decreases the number of average daily infections from 8.23e-9 to 1.4e-9.

| Metric | Mean |
| -------- | ------- |
| Number of Infections (per day) | 1.4e-9 |

### One-way Aisle Layout

We implement a one-way aisle layout by changing the store graph to a directed graph, where some edges are uni-directional.

[NOT COMPLETED]

## Interpretation

Our original simulation with no COVID-19 exposure interventions averages about 8.23e-9 infections per day.

When attempting to reduce COVID-19 exposure by controlling the customer arrival rate, we observe that the number of infections per day is quadratically proportional to the rate at which customers enter the store. This intuitively makes sense. So, the lower the customer arrival rate, the lower the average exposure time/infections.

When attempting to reduce COVID-19 exposure by controlling the maximum store capacity, we see that the number of infections per day is quadratically proportional to the maximum number of customers allowed in the store until that value reaches about 15, at which point it then levels off at about our original rate of 8.23e-9 infections per day. Upon closer inspection of our original simulation, we find that the store averaged around 15 customers at any given time. With that knowledge, there are two routes: either keep the maximum capacity below the current average of 15 customers or allow it to exceed 15 customers since, according to the model, there will not be an increase in infections.

When attempting to reduce COVID-19 exposure by implementing a face mask policy, we reduce the number of infections by a factor of 0.17. This decreases the number of average daily infections from 8.23e-9 to 1.4e-9. Based on our current results, this method seems to be the easiest to implement as it allows for the same number of customers to shop while dramatically decreasing the number of daily infections.

## Extension

For our extension, we recreate the same experiments with a space at Olin, rather than a synthetic store.

![extension_network](https://github.com/RebeccaFlach/covid-modeling/assets/47285707/8cc31e98-dc57-4858-a753-d8d0f2c2c09b)

**Figure 5: Olin space network visualization**, with the nodes defined by:
| Zone Type | Node(s) |
| -------- | ------- |
| Entrance | 0 |
| Till | 10 |
| Exit | 11 |
| Shelf | All other undefined nodes |

![extension_heatmap](https://github.com/RebeccaFlach/covid-modeling/assets/47285707/2e58b7ba-c71d-4f00-b588-e39dec872f6d)

**Figure 6: Olin space network heatmap visualization** based on mean exposure time in each zone. The color ranges from black to bright red. The brighter the red, the higher the average exposure time is in that zone.

## Causes for concern

7) Identify causes for concern.  Review the criteria for what makes a good project and identify any areas where your project might be problematic.

## Annotated Bibliography
[1] [**Modeling COVID-19 transmission in supermarkets using an agent-based model**](https://www.semanticscholar.org/reader/17a2627fca7585df99f9d214831992a3756ed772) by Fabian Ying, Neave O’Clery

In this paper, the authors investigate how COVID-19 is transmitted within a supermarket and use their model to determine the most effective interventions to decrease spread. In their primary experiment, they model a small supermarket using a graph, where each node is a place where a customer would stop and interact with the shelves, register, or other important points. They then create agents to represent customers, each with a random path through the store and time spent at each location. Infection risk is estimated by the amount of time a susceptible agent spends in proximity to an infected agent. They find that transmission risk is increased by bottleneck points, like the registers, and that limiting the number of customers in the store is an effective way to reduce transmission.

## Next steps

- Finalize one-way layout results
- Finalize extension simulations/results
- Finalize interpretations
- Migrate code to the repository

 
