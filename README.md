# Running a Single Trial and Rerunning Experiments

## Executing a Single Trial

To execute a single trial of the SIR model simulation with a specific seed set, infection probability, and recovery probability, you can follow these steps:

1. **Define the Graph:** Load your network graph using the `getGraph` function by providing the path to your edgelist file.

    ```python
    G = getGraph("path/to/your/edgelist/file")
    ```

2. **Select Initial Infected Seeds:** Choose the initial seed nodes for the simulation. This can be a predefined list or randomly selected nodes from your graph.

    ```python
    infected_seeds = [0, 1, 2]  # Example seed nodes
    ```

3. **Set Infection and Recovery Probabilities:** Define the probabilities for infection (`p`) and recovery (`r`).

    ```python
    p = 0.1  # Infection probability
    r = 1    # Recovery probability
    ```

4. **Run the Simulation:** Execute the SIR simulation using the `SIRsimulation` function with the graph, seed nodes, and probabilities.

    ```python
    results = SIRsimulation(G, infected_seeds, p, r)
    print(results)
    ```

This will perform a single trial of the SIR model on the specified graph with the given parameters.

## Rerunning the Entire Experiment

To rerun the entire experiment, including the greedy algorithm for selecting a seed set and running multiple simulations for different scenarios, follow these steps:

1. **Prepare the Graph:** Load your network graph as described in the previous section.

2. **Generate Random Candidate Sets:** For each run of the experiment, generate a new random candidate set of nodes from your graph.

    ```python
    import random
    candidate_set = random.sample(list(G.nodes()), 7)  # Example: select 7 random nodes
    ```

3. **Define Experiment Parameters:** Set the values of infection probability (`p`), recovery probability (`r`), and the number of trials (`sigma`) for average spread calculation.

    ```python
    p_values = [0.1, 0.5]
    r = 1
    sigma = 5
    ```

4. **Run the Greedy Algorithm:** For each combination of parameters and candidate sets, execute the greedy algorithm to select the optimal seed set and calculate the spread.

    ```python
    for p in p_values:
        for _ in range(3):  # Three random candidate sets
            seeds, spreads = greedy(p, G, candidate_set, k=5, r, verbose=True, sigma)
    ```

5. **Save and Analyze Results:** After running the simulations, save the results to a CSV file and plot them as described in the previous sections.

By following these steps, you can rerun the entire experiment to explore the effects of different seed sets and infection probabilities on the spread of the SIR model in your network.
"""
