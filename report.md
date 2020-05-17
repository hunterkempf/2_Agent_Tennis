# Report

## Algorithm chosen

For this Project I chose the DDPG (Deep Deterministic Policy Gradients) algorithm outlined in the following paper https://arxiv.org/abs/1509.02971. 

The basic idea of DDPG is to have both an Actor network and a Critic Network that allows one network to focus on the Q-values (Critic) and the other network to focus on the State to Action mapping (Actor). This was the same type of model I used for the Reacher Continuous Control model.

## Training Results

<div style="text-align:center"><img src="/TrainingScores.png" /></div>

My implementation took 670 episodes for the 100 episode rolling average to meet the threshold of .5 which on my computer took 334.00 minutes to run. You can notice that there are huge spikes of scores around 1 and 2.5 when the agents would go on a really good run. These gave the score disributions a strong right skew and thus the median scores were well below 0.5 despite the rolling average getting to 0.5

## Best Model Implementation

Actor (3 fully connected layers first 2 with relu activations and the last with tanh activation):

State Vector (24) --> fully connected layer(FC1) (24->256) --> relu (256 -> 256) --> fully connected layer(FC2) (256 -> 256) --> relu (256 -> 256) --> fully connected layer (256 -> 4) --> tanh (4 -> 4) --> Action Vector (2)

Critic (3 fully connected layers first 2 with relu activations and the last linear activation):

State Vector (24) --> fully connected layer(FC1) (24->256) --> relu (256 -> 256) + add in the action values -->  fully connected layer(FC2) (260->256) --> relu (256 -> 256) --> fully connected layer (256 -> 1) --> Expected Reward Vector (1)


## Future Improvements

I used the DDPG algorithm to solve this problem which has the benefit of being more simple to understand and code but it does not allow individual agents to learn on their own and thus wastes some of the potential of the 2 agent environment. To improve this algorithm I would explore a dynamic weight for the soft update parameter TAU (larger at the beginning and smaller at the end) to potentially learn faster and still stablize well in later stages. I also think changing the model number of connected layers and neurons could yeild improved performance.

Algorithms like PPO, A3C, and D4PG that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience would be a really interesting future improvement to this project.