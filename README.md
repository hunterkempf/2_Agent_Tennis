# 2 Agent Tennis Reinforcement Learning Model


<div style="text-align:center"><img src="/tennis.png" /></div>

## Background Information
For this Project I built a deep reinforcement learning model to train an two agents to play a cooperative game of table tennis where they are rewarded for the rally length they have.

In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

The task is episodic, and in order to solve the environment, the agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
This yields a single score for each episode.
The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.


## Download the Tennis Environment (Requires Unity installed to run)

Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)

## Before Training

<div style="text-align:center"><img src="/untrained.gif" /></div>

Before Training the agent takes random actions and may sometimes connect with a the ball by random chance but most of the time even the first drop is missed.

## After Training

<div style="text-align:center"><img src="/Trained.gif" /></div>

As you can see after training, the model achieves pretty good results and is able to track the ball and hit it over the net in most instances. Part of what makes this a non trivial problem is that there are many different speeds and directions that the ball may move and both agents have to work together to keep the ball up. A hard to reach hit from one agent will in turn make it less likely that the other agent can return the ball. 

## How to Install Requirements

This Project requires Python 3.6.3 due to the tensorflow 1.7.1 requirement in the requirements.txt file. Additionally it requires the Unity Environment and ml-agents package installed https://github.com/Unity-Technologies/ml-agents



# Future Improvements

I used the DDPG algorithm to solve this problem which has the benefit of being more simple to understand and code but it does not allow individual agents to learn on their own and thus wastes some of the potential of the 2 agent environment. 

Algorithms like PPO, A3C, and D4PG that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience would be a really interesting future improvement to this project.
