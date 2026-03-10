# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** Bhagya Sri 
**Student ID    :** 2310040100
**Date Submitted:** 10/3/26

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
[The fitness() function returns the total value of the selected items in a chromosome if the total weight does not exceed the knapsack capacity. If the total weight is greater than the allowed limit, the function returns 0 as a penalty. This ensures that invalid (overweight) solutions are not selected during evolution and encourages the algorithm to search for feasible solutions.]
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
[ tournament_select() randomly selects a small group of individuals from the population and chooses the one with the highest fitness as the parent. This method gives better solutions a higher probability of being selected because they are more likely to win the tournament. As a result, strong solutions pass their genes to the next generation. ]
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
[ This line copies the best chromosome from the current generation into the next generation. The [:] creates a copy so the original chromosome is not modified accidentally. This technique is called elitism, and it ensures that the best solution found so far is never lost during crossover or mutation.]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations | 50|
| Best value at generation 1 |60 |
| Final best value |77 |
| Total weight of best solution (kg) |14.4 |
| Is solution valid (Yes / No) |Yes |

**Copy the printed packing list here:**
```
[ ================================================
  EXPERIMENT 1 - Baseline
================================================

  Best Packing List
--------------------------------------
  + Water bottle
  + First aid kit
  + Sleeping bag
  + Torch
  + Energy bars (x6)
  + Rain jacket
  + Map & compass
  + Cooking stove
  + Rope (10 m)
  + Sunscreen
  + Power bank
--------------------------------------]
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
[ The graph shows how the best value improves across generations. The biggest improvement occurs during the early generations when the algorithm quickly discovers better combinations of items. After several generations, the curve begins to flatten, indicating that the algorithm has converged and is no longer finding significantly better solutions. ]
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate|Final best value| Weight (kg) | Valid? | Shape of curve |
|--------------|----------------|-------------|--------|----------------|
| 0.01         |    75          | 14.9/15.0   |   Yes  |Slow improvement, converges early|
| 0.05         |    77          | 14.4/15.0   |   Yes  |Smooth convergence  |
| 0.30         |    78          | 14.1/15.0   |   Yes  | More fluctuations but finds better solution |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
[ When the mutation rate is very low (0.01), the population does not change much and the algorithm may get stuck in a local optimum. When the mutation rate is very high (0.30), too many genes flip randomly, which destroys good solutions and makes the search unstable. The balanced mutation rate (0.05) provides a good trade-off between exploration and stability. It allows the algorithm to discover better solutions while preserving strong chromosomes. ]
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
[ The mutation rate of 0.05 produced the best result. This value maintains a good balance between exploration and exploitation. It introduces enough randomness to explore new solutions while still preserving high-quality solutions across generations.]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 |77 |The genetic algorithm quickly improved the solution and converged to a stable value around 77 |
| 2 — Mutation rate | mutation_rate = 0.30 |78 |Increasing the mutation rate introduced more diversity and helped discover a slightly better solution  |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
[ From this experiment, I learned how Genetic Algorithms search for optimal solutions using selection, crossover, and mutation. The algorithm gradually improves the quality of solutions across generations by keeping the best individuals. Mutation plays an important role in maintaining diversity in the population. If mutation is too low, the algorithm may get stuck in local optima, and if it is too high, the search becomes random. Therefore, choosing a balanced mutation rate is important for good performance. ]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
