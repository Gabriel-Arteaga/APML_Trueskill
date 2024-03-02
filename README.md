## Trueskill Project - Advanced Probabilistic Machine Learning
This repository presents our solution for a project assigned during the Advanced Probabilistic Machine Learning course (7.5 ECTS - [1RT003](https://www.uu.se/en/study/syllabus?query=43945)) at Uppsala University.

## Table Of Contents
 * [Trueskill](#Trueskill)
 * [How it works](#How-it-works)
 * [Technical Details](#Technical-details)
 * [Application and Results](#app-results)
 * [Project Members](#Project-memberrs)
## Trueskill
[TrueSkill](https://www.microsoft.com/en-us/research/publication/trueskill-through-time-revisiting-the-history-of-chess/) is a **Bayesian skill rating system** designed to estimate the skills of players in competitive games and sports.  In TrueSkill, each player’s skill is represented as a **probability distribution**, capturing the **uncertainty** associated with their true ability. TrueSkill can handle any number of competing entities and infer individual skills from team results. 
## How it works
1. **Representation of Player Skill**: Each player's skill is initially represented as a probability distribution, typically a Gaussian distribution. These distributions serve as our prior beliefs about the players' abilities.
2. **Computing Win Probabilities**: We calculate the probabilities of a player winning conditioned on their skill levels.
3. **Updating Posterior Distribution**: Evidence is collected from the game by observing its outcome. We then update the posterior distribution by combining the probabilities derived from the observed outcome and our prior beliefs of the players' skills.
   
## Technical Details
To update our posterior distribution, we employed two distinct techniques:
1. **Monte Carlo Methods with Assumed Density Filtering:**  
   This technique involves utilizing Monte Carlo methods, more specifically *Gibbs Sampling*, to approximate the posterior distribution. Specifically, we employed a method known as Assumed Density Filtering (ADF). ADF allows for the approximation of complex posterior distributions by iteratively updating the parameters of simpler distributions until convergence is reached.
2. **Factor Graphs and Expectation Propagation**  
   The second technique leveraged factor graphs and the message passing algorithm to perform Expectation Propagation (EP). Factor graphs provide a graphical representation of the probabilistic model, making it easier to understand and manipulate. EP is an iterative algorithm that efficiently updates the beliefs about the variables in the graph based on observed data, allowing for the computation of posterior distributions.
<p align="center">
  <img src="/data/images/Screenshot 2024-03-02 201641.png" width="80%" height="400" alt="Naive ensemble method" />
</p>
<p align="center">
<em> Factor graph visualizing the message passing algorithm. </em>
</p>

## Application and Results
We first tasked to **estimate the skills of football teams in the Italian Serie A** using Assumed Density Filtering (ADF). The table below showcases the outcomes of this estimation, displaying the mean (µ) and standard deviation (σ) of skill estimates, along with the predicted skill ratings and actual final standings for each team.
<div align="center">

| Team      | µ     | σ     | Skill rating | Final standing |
|-----------|-------|-------|------------------|--------------|
| **Juventus**  | 0.506 | 0.092 |         1        |      1       |
| **Napoli**    | 0.409 | 0.078 |         2        |      2       |
| **Atalanta**  | 0.352 | 0.097 |         3        |      3       |
| **Inter**     | 0.339 | 0.095 |         4        |      4       |
| **Milan**     | 0.315 | 0.095 |         5        |      5       |
| **Roma**      | 0.301 | 0.098 |         6        |      6       |
| **Torino**    | 0.159 | 0.098 |         7        |      7       |
| Sampdoria | 0.078 | 0.077 |         8        |      9       |
| Spal      | 0.071 | 0.08  |         9        |      13      |
| Genoa     | 0.067 | 0.111 |         10       |      17      |
| Bologna   | 0.059 | 0.078 |         11       |      10      |
| Lazio     | -0.002| 0.082 |         12       |      8       |
| Empoli    | -0.044| 0.077 |         13       |      18      |
| Udinese   | -0.105| 0.077 |         14       |      12      |
| **Cagliari**  | -0.157| 0.079 |         15       |      15      |
| Parma     | -0.2  | 0.096 |         16       |      14      |
| Fiorentina| -0.243| 0.105 |         17       |      16      |
| Sassuolo  | -0.277| 0.129 |         18       |      11      |
| **Frosinone** | -0.46 | 0.094 |         19       |      19      |
| **Chievo**    | -0.978| 0.131 |         20       |      20      |
</div>
Our estimates closely mirrored the final standings for 10 out of the 20 teams. Notably, teams with average performances throughout the season tended to diverge more from the predicted skill levels. This trend suggests a higher level of uncertainty in estimating the skills of these teams.   


In addition to estimating Serie A skill levels, we were tasked with applying the TrueSkill approach to another problem of our choosing. We opted to estimate the skill levels of teams in the popular game League of Legends (LoL). Moreover, we were required to utilize **Bayesian Linear Regression** to predict game outcomes based on these teams' skill levels. We implemented two models: one without incorporating any prior beliefs and another where we introduced prior knowledge.

In LoL, there exists a slight advantage for the team starting as the blue team. To incorporate this prior knowledge, we added a constant of 0.03 to the mean skill level of the team beginning as the blue team. Remarkably, this adjustment led to an improvement in our predictions from **56.9%** without prior knowledge to **61.3%** with the inclusion of prior information. For more details of our results please read our [report](project_report.pdf) and check our [solution notebook](project_solutions.ipynb). 

## Project members
[Gabriel Arteaga](https://github.com/Gabriel-Arteaga)  
[Inga Wohlert](https://github.com/IngaKristin)  
[Alexander Sabelström](https://github.com/Sabelz)
