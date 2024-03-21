# iclr-blog2024-primacy-bias
Supporting code for "It's Time to Move On: Primacy Bias and Why It Helps to Forget", part of the ICLR 2024 Blog Post Track

# Motivation

1. Maximize sample efficiency has become a popular trend in reinforcement learning. Increasing the replay ratio is one way to do this. This can sometimes work but risks causing catastrophic memorization. Weight resets are a clever solution first published by Nikishin et al. [1] in 2022. Intuitively, this problem should be related to the degree of stationarity in the environment. Applications might extend beyond reinforcement learning to impact life-long learning agents. These experiments hope to tinker with the idea. 


2. There is an [old talk on clustering that enjoy by Leland McInnes](https://www.youtube.com/watch?v=ayZQj4llUSU). One point that resonated with me described how data analysis typically takes different time horizons:

	- Interactive
	- Over coffee
	- Over lunch
	- Over night

A lot of reinforcement learning research falls in the "over night" (or longer) bucket, but I'm not convinced that's always necessary.

[1] https://arxiv.org/pdf/2205.07802.pdf


# Run Instructions

- Colab link:
	- Contains slight modifications to avoid install any additional dependencies
- Experiment notebook: 
- Graphing notebook: @TODO

A single run of 1000 crossings with a replay ratio of 1 completes in about 5s on Colab. Runtime increases linearly with replay ratio.

The main hyper-parameter search discussed in the blogpost was 1875 total trials (5 learning rates, 3 replay ratios, 5 reset frequencies, 25 seeds) and completed in under 2 hours fully utilizing a 32-core 5950X CPU.
