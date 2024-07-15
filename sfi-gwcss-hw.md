---
layout: page
title: 
permalink: /sfi-gwcss-hw/
---

# Norm-Changing and Code-Switching
#### Modeling norms as adaptable edge attributes

Gülşah Akçakır and Benjamin Freixas Emery


#### Context

During the Santa Fe Institute's 2024 Graduate Workshop on Computational Social Science, we were given two days to produce a solution to the following problem.  

##### Consider the following situation:



<p>
<nl>

A society changes a pre-existing norm.  Without references to previous models:

<li> Model, using whatever techniques you wish, the above scenario.
<p>
<ul>
   <li> Explicitly state your model and key assumptions.
   <li> Summarize key results.
   <li> Suggest some potentially interesting future directions and
questions for the model.
</ul>
<p>
<li>Suggest at least one "easy" norm transition that your model could capture.
<li> Suggest at least one "hard" norm transition that your model could capture.
</nl>


#### Our Approach

We consider the following properties of a class of social norms:

- Norms are exhibited via interactions between individuals.
- An individual continually chooses whether to practice a norm at each instance of an interaction. In cases where a person uses certain norms with some of their groups and different norms with others, this is known as "code-switching". 
- Individuals are more likely to reciprocate a behavior than they are to exhibit it to others in their circle.

Because of this, we model norms as continually updating edge attributes.


#### Motivation
Consider the simple example of three American college students. Student 0 returns from study abroad in France and begins greeting their friends with two kisses, as was customary in their previous country of residence. We denote this change in expression of a norm by changing the respective edges to red.


<!-- :-------------------------:|:-------------------------:
![](three-nodes.png)  |  ![](three-nodes-1.png) -->
|  |                                        |
:-----------:|:------------------------------------------------------:
|<img src="https://raw.githubusercontent.com/dbemerydt/dbemerydt.github.io/master/images/three-nodes.png" alt="drawing" width="200" class=/>|<img src="https://raw.githubusercontent.com/dbemerydt/dbemerydt.github.io/master/images/three-nodes-1.png" alt="drawing" width="200" class=/>|



Students 1 and 2 may or may not reciprocate this behavior to Student 0, but they are even less likely to start exhibiting this norm change with each other.

|  |                                        |
:-----------:|:------------------------------------------------------:
|<img src="https://raw.githubusercontent.com/dbemerydt/dbemerydt.github.io/master/images/three-nodes-2.png" alt="drawing" width="200" class=/>|<img src="https://raw.githubusercontent.com/dbemerydt/dbemerydt.github.io/master/images/three-nodes-3.png" alt="drawing" width="200" class=/>|
<!-- <img src="three-nodes-2.png" alt="drawing" width="400"/><img src="three-nodes-3.png" alt="drawing" width="400"/> -->

#### The model

To capture these heuristics, we define a simple model with the following properties:
- A norm is coded as edge attribute with the possible values {0,1}, where 0 indicates the old norm and 1 indicates the new.

- We define two parameters:
| parameter | interpretation                                       |
|-----------|------------------------------------------------------|
| $\phi$         | preference for reflecting behavior in an interaction |
| $\theta$         | openness to adopting a new norm (state 1)            | 


- An edge from *i* to *j* takes the state 1 if 
$$ \phi \text{state}(j,i) + \frac{\phi}{|N_i|}\sum_{k\in N_i}\text{state}(k,i) > \theta. $$

- When an edge changes states, we allow all the out-edges of the target node to update on the next step.

Here's an example of how this may play out on a familiar empirical social network:

|                                          |
|-----------------------------------------------------------------|
|<img src="https://raw.githubusercontent.com/dbemerydt/dbemerydt.github.io/master/images/animated-schematic.gif" alt="animation" width="700"/>|


#### Experimental results

We began our investigation of the dynamics of our model at a global scale. In the preliminary analyses, our primary outcome of interest was the proportion of edges that adopted the new norm $(= 1)$. For the initial set of analyses, we represented the underlying relationship and communication structure with a directed Small-World network (Milgram, 1967; Watts & Strogatz, 1998), incorporating reciprocal edges between any two connected nodes. This choice was made to ensure comparable degrees across all nodes in the network, thereby allowing us to isolate the model's behavior without accounting for dependencies on the initial seed selection and network topology.
We constructed the network with $N=50$, $k=4$, and rewired 50 edges at random. We then tested our model with $n=10$, tuning both $\phi$ and $\theta$ within the range $[0, 1]$, with increments of 0.1. 

<!-- We run a sweep over the possible values of the two parameters on a small world network with
$$n=50,k=4,p=0.1.$$ -->

We consider two initial condition cases where a subset of 10 nodes is selected and all of their out-edges are flipped to 1, with the rest of the edges starting at 0.

| initial condition | interpretation                                       |
|-----------|------------------------------------------------------|
| random nodes         | "study-abroad" experiment |
| continous block of nodes         | "in-group slang" experiment           | 

We consider the simulation to have ended when a timestep passes with no changes. The final proportion of adoption over all edges is shown for each parameter value-pair in the heatmaps below.

|  |                                        |
:-----------:|:------------------------------------------------------:
|<img src="https://raw.githubusercontent.com/dbemerydt/dbemerydt.github.io/master/images/heatmap-randseed.png" alt="drawing" width="400"/>|<img src="https://raw.githubusercontent.com/dbemerydt/dbemerydt.github.io/master/images/heatmap-blockseed.png" alt="drawing" width="400"/>|

In both experiments, we have three major regions. The bottom-left triangle indicates that for sufficiently low values of both $\theta$ and $\phi$, the new norm necessarily spreads to the entire network. The shallowness of the triangle shows that for low enough $\theta$, we reach full saturation for nearly all values of $\phi$. The upper-right triangle indicates that high-$\theta$ low $\phi$ pairs result in the nearly everyone returning to the old norm. The third major region, bound by the right boundary and diagonals traversing upward and downward to the left, is the region where the new norm doesn't spread much farther than the initial seed.

The random-seed version allows for higher amounts of spreading across all regions.

#### Future direction

The egalitarian approach we used for network initialization, in terms degree centrality, may not fully capture real-world network properties, such as preferential attachment (often referred to as the "rich-get-richer" dynamics), which are prevalent in certain types of relationships. Consequently, extending the network topology to allow for greater variation in the number of connections and clustering could enhance our understanding of the model's dynamics under different circumstances. In addition, we could assess how the norm-shifting behavior captured in our model depends on who the early adopters are.

Furthermore, reciprocity of edges across all pairs accounts for relationships like friendship, but this is not a necessary condition for norm shifting in society. In today’s world, the prevalence and influence of social media on behavioral change, especially among young adults, is undeniable. Connections between people on social media, or at least the influence patterns, are usually one-sided. Therefore, as a next step, we plan to investigate the dynamics on networks with non-reciprocal edges between nodes. This approach will allow us to capture influence patterns similar to follower-followee relationships on social media.

Our current model focuses exclusively on dyadic-level interactions. However, this approach has its limitations, as it does not account for the dynamics present in group settings. Group interactions, which involve multiple participants, are more representative of real-world scenarios where code-switching is commonly observed. In a group setting, the dynamics of code-switching become more complex due to various factors such as group size and social hierarchies
By broadening our scope to include higher order dynamics, we can gain a more comprehensive understanding of code-switching behavior and norm shifting.

#### References
- Watts, D., Strogatz, S. Collective dynamics of ‘small-world’ networks. *Nature 393*, 440–442 (1998). https://doi.org/10.1038/30918

- S. Milgram. The small world problem. *Psychology Today 1*(1), 60–67 (1967).


```python

```
