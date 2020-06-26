# Reinforcement Learning(RL)
RL is known as a semi-supervised learning model in machine learning, 
is a technique to learn by interacting with its environment. The agent receives rewards by performing correctly and penalties for performing incorrectly. 
The agent learns without intervention from a human by maximizing its reward and minimizing its penalty. 
RL is usually modeled as a Markov Decision Process (MDP).
![Github](https://miro.medium.com/max/1400/1*-0G8EIeG24OYTbt5KZSalQ.png)
>source: [Reinforcement Learning:An Introduction](http://incompleteideas.net/book/bookdraft2017nov5.pdf)


RL is used in different applications:resources management in computer clusters, traffic light control, web system configuration, games.
The most famous one must be AlphaGo and AlphaGo Zero.
# Scheduling with Reinforcement Learning
## Introduction
In recent years, some people have begun to use reinforcement learning for factory and semiconductor plant scheduling.

Take [this paper](https://www.semanticscholar.org/paper/A-REINFORCEMENT-LEARNING-APPROACH-TO-SCHEDULING-Roh-Lee/b61d28e723b9b29b876813226a21d55088c4cdef) 
as an example, with the development in the semiconductor manufacturing industry, quality issues have been considered in the wafer manufacturing process 
In order to avoid quality problems caused by batch production, the cluster tool process one wafer at a time is be used in the semiconductor industry.

The cluster tool consists of serval chambers and one transport robot and only one wafer is processed at a time in each chamber.
The transport robot changes the wafers inside the cluster tool.
When the wafer is completed in the chamber,the wafer is moved to the next chamber by a robot. 
The transport robot repeats the process of loading the wafer to appropriate chamber and unloading the completed wafer from the chamber.
Because the cluster tool only has a transport robot, the wafers can't be changed at any time. If serval chambers had already finished the wafer,the cluster tools
can't move all complete wafers at the same time.
## Methdology
Roh and Lee developed a model using Markov Decision Process (MDP), and the model can handle time variants in the cluster tools.
First, the state and action will be defined. The state is set to (𝑊, 𝐶1, 𝐶2, … , 𝐶𝑛 , 𝑅, 𝑆1, 𝑆2, 𝑍1, 𝑍2, … , 𝑍𝑛 ),
