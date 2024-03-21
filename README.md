# iclr-blog2024-primacy-bias
Supporting code for "It's Time to Move On: Primacy Bias and Why It Helps to Forget", part of the ICLR 2024 Blog Post Track.

Code is derived from [CleanRL](https://github.com/vwxyzjn/cleanrl/blob/master/cleanrl/dqn.py), so if you aren't specifically interested in primacy bias on Frozen Lake I would go there.

The main differences are:
- Removed the StableBaselines dependency but implementing our own simple replay buffer
- Removed Tyro dependency, accepting this is a research notebook
- Removed environment parallelization with Gym and instead parallelize with Dask only when necessary

# Motivation

1. Maximize sample efficiency has become a popular trend in reinforcement learning. Increasing the replay ratio is one way to do this. This can sometimes work but risks causing catastrophic memorization. Weight resets are a clever solution first published by [Nikishin et al. in 2022](https://arxiv.org/pdf/2205.07802.pdf). Intuitively, this problem should be related to the degree of stationarity in the environment. Applications might extend beyond reinforcement learning to impact life-long learning agents and transfer learning. These experiments hope to tinker with the idea. 

2. There is an old talk on clustering that enjoy by [Leland McInnes](https://www.youtube.com/watch?v=ayZQj4llUSU). One point that resonated with me described how data analysis typically takes different time horizons:

	- Interactive
	- Over coffee
	- Over lunch
	- Over night

A lot of reinforcement learning research is "over night" (or longer), but I'm not convinced that's always necessary.



# Run Instructions

- [Colab link](https://colab.research.google.com/drive/1FFHW8Nogc124rDoIQzAuVHAr96iTn3tD#scrollTo=49af6305-9809-41d2-b54d-5cb875351b98)
	- Contains slight modifications to avoid install any additional dependencies
- [Experiment notebook](https://github.com/mkielo3/iclr-blog2024-primacy-bias/blob/main/FrozenLake-PrimacyBias-DQN.ipynb)
- Graphing notebook: @TODO

A single run of 1000 crossings with a replay ratio of 1 completes in about 5s on Colab. Runtime increases linearly with replay ratio.

The main hyper-parameter search discussed in the blogpost was 1875 total trials (5 learning rates, 3 replay ratios, 5 reset frequencies, 25 seeds) and completed in under 2 hours fully utilizing a 32-core 5950X CPU.
