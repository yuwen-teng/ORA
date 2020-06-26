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

First, the state and action will be defined. The state is set to (𝑊, 𝐶1, 𝐶2, … , 𝐶𝑛 , 𝑅, 𝑆1, 𝑆2, 𝑍1, 𝑍2, … , 𝑍𝑛 ),where W is the number of wafers remaining in the loadlock.
𝐶𝑖 is the state of the chamber, which represents whether the 𝑖 th chamber is empty ( 𝐶𝑖 = 0), full ( 𝐶𝑖 = 1), or completed processing (𝐶𝑖 = 2) for 𝑖 ∈ {1, 2, … , 𝑛}.
𝑅 is the number of wafers held by the transport robot. 𝑆1 𝑎𝑛𝑑 𝑆2 are the next process steps of the wafers held by the robot. 𝑍𝑖 is the expected remaining process time of the
𝑖th chamber for 𝑖 ∈ {1, 2, … , 𝑛}. The action is set to {𝑊𝑎𝑖𝑡, 𝑈𝑗 , 𝐿𝑗 , 𝑆𝑊𝑖 } , where 𝑗 ∈ {0 ,1, 2, … , 𝑛} 𝑎𝑛𝑑 𝑖 ∈ {1, 2, … , 𝑛}. They all represent the robot tasks: 𝑈𝑗, 𝐿𝑗, and 𝑆𝑊𝑖 indicate unload, load, and swap operations on the 𝑗 th or 𝑖 th chamber. Accroding to figure 1, the state is (𝑊 = 3, 𝐶1 = 2, 𝐶2 = 1, 𝐶3 =
1, 𝐶4 = 2, 𝑅 = 1, 𝑆1 = 2, 𝑆2 = 0, 𝑍1 = 0, 𝑍2 = 4, 𝑍3 = 4, 𝑍4 = 0).Suppose that the black and white wafers indicate that they are in the first and second process steps, respectively, and the hatched wafer indicates that the process is in progress (Roh and Lee,2017).
[figure 1: A Dual-armed Cluster Tool with Four Chambers](https://github.com/yuwen-teng/ORA/blob/master/A%20Dual-armed%20Cluster%20Tool%20with%20Four%20Chambers.PNG)

Second, the invalid action and deadlock action will be eliminate. To eliminate the invalid action for the current state, the agent requests theenvironment for the results for all the actions, then holds valid actions. After agent takes the valid action, cause the next state does't has the valid state, is called deadlock action.

Third, the agent will take the Q-learning algorithm to find the best action for each state.

