# COVID-19 Modeling in Supermarkets

By: Rebecca Flash and Daniel Quinteros

2. We plan to investigate the spread of COVID-19 in supermarkets via simulations of people shopping, some of whom might be infectious, and how to best mitigate the spread. We will mostly be referencing our main paper’s [source code](https://www.semanticscholar.org/reader/17a2627fca7585df99f9d214831992a3756ed772)

3. [**Modeling COVID-19 transmission in supermarkets using an agent-based model**](https://www.semanticscholar.org/reader/17a2627fca7585df99f9d214831992a3756ed772) by Fabian Ying, Neave O’Clery

In this paper, the authors investigate how COVID is transmitted within a supermarket, and use their model to determine the most effective interventions to decrease spread. In their primary experiment, they model a small supermarket using a graph, where each node is a place where a customer would stop and interact with the shelves, register, or other important point. They then create agents to represent customers, each with a random path through the store and time spent at each location. Infection risk is estimated by the amount of time a susceptible agent spends in proximity to an infected agent. They find that transmission risk is increased by bottleneck points, like the registers, and that limiting the number of customers in the store is an effective way to reduce transmission.

4. We plan to replicate the experiment that models the supermarket and tracks COVID risk. The paper's source code is available online, so we will be using that as a starting place. For our replication, we are planning to get their code working and then modify it to use a more current understanding of COVID transmission and produce different visualizations. 

We will run modified iterations of the simulation in which the following changes are made:
- Control the rate of customer arrival
- Restrict the maximum number of customers in the store
- Implement face mask policy
- One-way aisle store layout

A possible extension is to run the simulation in a layout of an Olin building, such as the dining hall, rather than a supermarket. Another route would be replicating the long-staying air borne property of covid-19 and making some nodes in the graph “infected” after an infected person stays there.

5. ![expected_results_sketch (2)](https://github.com/RebeccaFlach/covid-modeling/assets/47285707/54c7595f-0f55-4f01-b93b-a93c34377e65)

6. The paper focuses on the total amount of time that a susceptible person is within range of an infected person, so we will use that as our primary measure to compare with the original paper. 

7. Because the source code for the paper is already available online, our project will probably be more focused on extension than replication, so an area of concern is our ability to create a bigger extension. We are also still unsure how much work it will be to get the source code working, so we are unsure what our replication will be like. 

8. In the next week, we plan to look through the source code, try to understand it, and get it running. Then, we will begin looking at simple modifications and extensions we can make. 
