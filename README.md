# Bayesian Networks for Student Math Performance Analysis

This project utilizes Bayesian networks to model and analyze factors influencing student math performance, using the UCI Student Performance dataset. The goal is to identify key relationships between student attributes (e.g., study time, absences, internet access) and their final grades.

## Dataset

The [UCI Student Performance dataset](https://archive.ics.uci.edu/dataset/320/student+performance) contains information about secondary school students' performance in math and Portuguese language courses. The project focuses on the math course data.

## Bayesian Networks
The networks were constructed with three different techniques:

1.  **PC Algorithm (Spirtes et al., 1991):**
    * A constraint-based structure learning algorithm that infers the network structure based on conditional independence tests.
    * Strengths: Can handle large datasets and identify causal relationships.
    * Weaknesses: Sensitive to the choice of significance level and may produce incorrect structures with limited data.
    ![PC network](/img/pc-bn.png)

2.  **Tree Search (Chow and Liu, 1968):**
    * A score-based structure learning technique that finds the optimal tree-structured Bayesian network.
    * Strengths: Computationally efficient and guarantees an optimal tree structure.
    * Weaknesses: Restricts the network structure to a tree, which may not capture complex dependencies.
    ![Tree network](/img/tree-bn.png)

3.  **Expert-Defined Network:**
    * A manually defined network structure based on domain knowledge and prior understanding of the factors influencing student performance.
    ![Expert-defined network](/img/expert-bn.png)

## Queries
The Bayesian networks were queried, via variable elimination, about:
1. How absences and the amount of study time influence the final grade.
2. If having a long travel time from home to school affects students' health.
3. If having internet access at home is helpful in studying or does it allow for more distractions.

## Results

### 1. Influence of Absences and Study Time on Final Grade
All three networks agree that having fewer absences with less study time is more likely to lead to better math grades than having more absences with more studytime. The expert-defined network was significantly faster in producing the result thanks to the re-binning.

### 2. Impact of Travel Time on Health
All three networks agree that long travel times from home to school do not significantly affect students' health; the conditioned and unconditioned health probabilities are equivalent.

### 3. Helpfulness vs. Distraction of Internet Access
For the PC network, because G3 is independent of the internet variable, the distributions are equivalent and the plots match. However, the Tree Search and the expert-defined network distributions suggest that having internet access at home is helpful for students. With internet access, the probabilities of scoring higher grades are higher than with no internet at home and, conversely, the probabilities of scoring worse grades are lower.
![grades-internet](/img/grades-internet.png)