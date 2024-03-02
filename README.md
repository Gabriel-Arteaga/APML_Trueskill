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


## Project members
[Gabriel Arteaga](https://github.com/Gabriel-Arteaga)  
[Inga Wohlert](https://github.com/IngaKristin)  
[Alexander Sabelström](https://github.com/Sabelz)
