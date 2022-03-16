# Comparative Study between DQN &amp; Dueling DDQN with PER on 2048 game env

# Project Motivation: 
In previous years there have been many breakthrough achievements using deep representations in reinforcement learning. While we were learning about convolutional networks, upon research we found out that the dueling architecture can be easily combined with other algorithmic improvements. In another research paper, prioritization of the experience replay has shown significant improvement in the performance of Atari games (Schaul et al., 2016).However, as dueling architecture and prioritization addresses altogether different aspects of the learning process, their amalgamation is awesome. Moreover, as published that the dueling architecture enables Reinforcement Learning agent to outperform the state-of-the-art on the Atari 2600 domain.Therefore, in our final experiment, we investigated the integration of the dueling architecture with prioritized experience replay and compared it with DQN implementation on 2048 in order to find the most efficient way to solve the 2048 game.
# Goal: 
Applying various deep Q techniques and finding the most efficient way to solve the 2048 game environment, which resulted in comparative study between DQN and Dueling DQN with prioritized experience replay on 2048.
Project Description & Algorithms: 
We investigated the various deep Q techniques and related concepts like DQN, Double DQN, Dueling DQN,Experience Replay, Prioritized Experience Replay to finalize the comparative study between two techniques DQN and Dueling DQN (with PER).
a)	Why on 2048 environment ? 2048 game environment has 4 random components which are categorized as the initial configuration of the game, after every move addition of random tiles,unavailability of moves and exploration of the agent. However these four random components raise an issue of inherent randomness in the 2048 game.  Therefore to solve this issue of inherent randomness, a prioritized experience replay buffer is used where the model trains to learn the best game-playing strategy from the experiences collected.
b)	DQN : is an algorithm which calculates TD error using the difference between the TD target and the current Q values.


# How To Run 
  1) go to project_directory
  2) execute command jupyter notebook
  3) run DQN.ipynb 
  4) run Dueling_DQN.ipynb
  
# Experiment:
 Plots for DQN on 2048 environment:
Below are the graphs for the DQN experiment 
![image](https://user-images.githubusercontent.com/79550954/158519254-6c0bb390-449c-410c-b0ca-b740229de263.png)

a) episode reward plot signifies the episode vs reward. 
b) loss plot signifies the episode vs loss. 
c) step plot signifies the episode vs episode length.
d) highest plot signifies the episode vs highest tile generated for the given episode.
  
  Plots for Dueling DQN on 2048 environment
  
  ![image](https://user-images.githubusercontent.com/79550954/158519349-cd0b1f5c-ecd6-4087-b432-85baafdb7b04.png)

The above graph signifies the episode vs reward graph. The orange line indicates the moving average of reward for 20 episodes. Reward over here is the maximum tile generated for the given episode. 

![image](https://user-images.githubusercontent.com/79550954/158519381-4e59680d-5a0b-4ce3-a48a-afe69e640103.png)

The above graph signifies the episode vs score graph. The orange line indicates the moving average of score for 20 episodes. Score over here is the sum of the scores generated for each of the moves for a given episode.

![image](https://user-images.githubusercontent.com/79550954/158519398-3a8f8427-ea25-438e-ae86-db49db1dd96d.png)

The above graph signifies the episode vs episode length graph. The orange line indicates the moving average of the episode length for 20 episodes. For the 2048 environment, the longer the episode length the better the agent

![image](https://user-images.githubusercontent.com/79550954/158519416-e4f0c7ba-66ff-47ac-8561-a1509ce3aa98.png)

The above graph signifies the episode vs loss of a graph. The orange line indicates the moving average of the loss for 20 episodes

# Results 
The key insight behind Dueling DQN is that it is not necessary to estimate the value of each action choice for many states which means that the dueling architecture can learn which states are valuable for each state without learning the effect of each action. In some states, it is of paramount importance to know which action to take, but in many other states the choice of action has no repercussions on what happens. This is particularly useful in states where its actions in no relevant way affect the environment. (which is the case with the 2048 environment). In addition to this, for a more stable optimization, we use an average baseline for Q evaluation. The dueling architecture and prioritization addresses different aspects of the learning process, however we intend to experiment their combination and the results were promising. The episodes were prioritized by the absolute value of each transition’s TD error. During the implementation we faced the issue where some of the transitions subsets were more frequently occuring, to resolve this issue we used a priority queue implemented by SumTree to do a stochastic sampling that interpolates between 60% of the prioritization on the TD error and 40% on the uniform random sampling. The results that we got were Dueling DQN with PER converges in 5000 episode length whereas DQN on 2048 env game tools around 40,000 episode length to converge.
