# Learning to run

NIP 2017 "Learning to run" OpenAI competition.

https://medium.com/mlreview/our-nips-2017-learning-to-run-approach-b80a295d3bb5

> The task was to write a program that activates legs muscles in order to maximize the number of meters passed in 1000 timesteps. The score is the number of meters pelvis.x moved from the initial position. In the reinforcement learning setting, one would say that an action has 18 float values from 0 to 1, corresponding to muscle activations

> A typical program will read the current observation (positions, velocities and so on) and output an action, activating some muscles. The simulator will update its state and return the observation for the next timestep + a reward (distance passed) for the previous timestep.

> we used PPO trained on 80 cores in a couple of days with manually prepared observation vector + a bit of reward hacking

> Speeding up network libraries (TensorFlow) or using GPU didn’t bring any value since OpenSim simulator took ~99% of the time.

> Initially used DDPG from keras-rl, the average score during training was fluctuating a lot and what’s worse — sometimes it could just massively drop and stay like that. We tried to tune hyperparams, without any gain though.

Switched to using PPO, out-of-the-box parallelizable on multiple CPUs (with MPI), and the average score didn't fluctuate or suddenly drop like it did with DDPG.

OpenSim had a memory leak, RAM consumption grew constantly, after a day it could take 30GB for a single process. Switched to a combination of Python 2 + older version of OpenSim that didn’t leak.

> In the beginning we used our laptops, 4 cores each. The computing power was close to zero and it was horrible to hear the fan during the night. Then a lucky thing happened. We got an access to a machine with… 80 cores (Intel Xeon). That was a game changer. Now we could run dozens of experiments. To feed 8M timesteps of data into learning algorithm, it took about 24 hours, on 40 cores.

> renting c5.9xlarge (1.728$/h) and c4.8xlarge (1.811$/h) both having 32 cores. About 86$ per 24h. Yikes. We wanted to use some instances with more cores, but all of the beefier ones had some default limit set to… 0. For any region. So, one could submit a ticket… for each instance type… and wait. Who would have thought that “on-demand” meant “on-demand after 4 days after sending a ticket”.

> We found another interesting OpenAI blog post (all of them are great) about Evolution Strategies. We had 80 cores instead of 720, but we thought that maybe this was enough, even if it would be 90x slower.

> What we liked about ES is simplicity (compared to PPO), they are embarrassingly parallel.

> Ok, we had PPO from baselines running on 80 cores. We got some improvement when we extended the observation vector. 41 was already a lot, however it didn’t have all the velocities. Nor any accelerations. And RL algorithms work well if observation is Markovian, i.e. you can predict what happens next just from the given observation (in other words, you can forget about the past). So we added the remaining velocities and accelerations. 

> Another important thing were obstacles. Original observation only had only information about the next obstacle. It’s helpful to make an agent “remember” more, e.g. the previous one as well. Otherwise he would “forget” about the one underneath it when seeing the next one. Original observations also didn’t have the force with which feet touch the ground. So we added an approximation of that. In the end we had 82 observations instead of 41.

> To have more insight into what’s going on, we logged the mean and std (standard deviation) of all the observations, to see if the normalization is done well. Because normalization is one of 10 things that can easily go wrong.

> By default, PPO code uses a filter, which automatically normalizes every feature. For every feature, it keeps its running mean with std and does normalization by subtracting the mean and dividing by std. This works for most of the features. However, imagine a constant, like the strength of psoas (a muscle). The std is 0. The code in that case was just passing this value as it is. The magnitude of that value is treated as an importance when passed to a network. If it’s big, it will saturate all the other smaller inputs (which may be more important).

> Another problem was that the very first strength of psoas (due to a bug, later fixed) had some different value than the others. So that filter would calculate some arbitrary mean + std and later use them. Another problem are spiky features. Take velocity for example. Most of the time it’s quite low, but there is a moment it shoots up and it probably is an important moment. On one hand you want it big enough, so that the network picks it up, but not enormously huge, so that it doesn’t saturate other features. Because all of this problems, we skipped the auto normalizing and just manually normalized every feature. We would run our model, collect means with std and visualize:

![Visualising mean and std dev](blog-posts/visualising-mean-and-stddev.png)

> If we saw that some value was not “in line” (mean not close to 0, std not close to 1), we would tweak the code and repeat. We ended up with something not ideal, but probably good enough so that the network can at least “see” all the given observations.

> Another important thing was to use relative positions, not absolute. All our positions were relative to pelvis. Thanks to that similar poses were represented by a similiar observations.

> during training it’s worth to use a different reward than the one used during grading (the distance in meters). First reward hack came from DeepMind’s “Emergence of Locomotion Behaviours in Rich Environment” research paper. They used velocity instead of distance, which is better. Using velocity as a reward puts emphasis on passing the same distance in less timesteps.

> Using distance doesn’t, no matter if you passed 10 meters in 10 or 1000 timesteps. Problem we got was that lots of experiments got stuck in local maxima, which resembled jumping in place. So, we added a small reward for every timestep “survived”. This helped it to take the first step and get out of local maximum.

> We were hesitant to adding more reward hacking throughout the challenge, it’s a bit ugly, we hoped for a more general solution.

> The nice thing about reward hacking is that the changes are quickly visible in training and they are easy to implement. However one could end up exploring not enough.

> In the end we added two more. The first one was: “keep pelvis.x behind head.x”. It was causing it to lean a bit forward, because it’s obvious you must do that when running, but our models were not discovering it, they liked to wobble the head back and forth. The second one was a penalty for straight legs. Our models all the time had two legs straight (or one in the best case).

> We tried many other things, for example reducing action to only 9 values for the right leg and copying them over to the left leg. We hoped to produce a fast hopper, kangaroo-like (with a simpler network). Our PPO however couldn’t train it well, skeleton was poor on obstacles.

> In hindsight, we started to tweak the hyperparams of DDPG and PPO too early. It took a long time and almost all that work went to the bin, because we abandoned DDPG and in PPO we changed features and rewards (so we needed to tweak hyperparams again). In the end we used the original PPO parameters, 2 hidden layers with 64 neurons.

> It may be that we too early abandoned DDPG. Some participants were using it. We could have tried with baselines DDPG implementation, especially after OpenAI injected noise in the parameters to improve exploration. We also feel that ES option still has big potential. We saw TRPO, but PPO seems like improved TRPO, that’s why we didn’t explore that option.

> When taking some new algorithm, it will be better if we first replicate it on some easy/known environment first and check with known results. To be sure that we got it working + we gain a knowledge of how it runs. Then, we can plug in our complex environment. Because if we can’t learn the easier environment, we won’t learn the harder one for sure.

> This manual normalization also took very long. Now it seems it might be faster to use auto normalization for most of the features but only normalize manually a few chosen ones.

> I would implement logging earlier, to gain as much insight into that black-box as possible. That was our biggest problem I would say, lack of visibility of what’s going on during the learning. We could spend more time to learn TensorBoard or similar perhaps.

