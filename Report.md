# Project report

This report details the experiments the repo owner has made to solve the continuous control project of Udacity Deep Reinforcement Learning nanodegree.



## Learning algorithm

In order to have room for improvements, the agent was trained using DDPG with experience replay. DDPG uses two networks:
- the actor approximates the optimal policy deterministically $argmax_a Q(s, a)$
- the critic learns to evaluate the optimal action value function with actor's best believed action: $Q(s, \mu(s; \theta_\mu); \theta_Q)$

In DQN, you have two copies of the network (regular and target) and target network is updated every N steps.

In DDPG, target networks (one for actor, one for critic) are updated using soft updates strategy: every step, 99.99% of target and 0.01% of regular network



**Model architecture**

The model architecture is a succession of 3 fully connected layers (128 input/output features for actor's hidden layers and 64 for critic's hidden layers), with SELU activations. Optionally, batch normalization and dropout layers can be added after penultimate layers. This was added to prevent potential overfitting, which did not turn out to be a problem to reach the target score. Batch norm layers were added to the actor model until the penultimate layers.



**Hyperparameters**

With default parameters, reaching the target score of `+30.0` would take ~500 episodes. 

```python
buffer_size = 1e5 # number of experiences that can be stored in buffer
batch_size = 128 # number of experiences that are sampled by the buffer
lr = 5e-4
lr_steps = 100 * 1000 # number of learning steps between each scheduler step
lr_gamma = 0.5 # LR multiplier applied at each scheduler step
gamma = 0.9
tau = 5e-4
noise_mean = 0. # mean of Ornstein-Uhlenbeck noise
noise_theta = 0.15 # theta parameter of Ornstein-Uhlenbeck process
noise_sigma = 0.12 # sigma parameter of Ornstein-Uhlenbeck process
grad_clip = 0. # Gradient clipping (disabled at 0.)
```



In order to speed up to training, buffer size was kept at `1e5`.  However the training is still unstable and depending on the seed, results may not be similar.



## Results

Using the training setup described in the previous section, the training script is able to yield a consistent solving of the environment under 600 episodes. Below are the score statistics of the training run:

![ddpg_target_scores](static/images/ddpg_training_scores.png)

Now, the evaluation script uses the state dictionary of the trained agent to evaluate it in a non-training environment and the overall score remains consistently above `+30.0`, as shown in the evaluation run below:

![dqn_fixed_target_eval](static/images/ddpg_eval.gif)

Trained model parameters can be downloaded from this repository [release attachments](https://github.com/frgfm/drlnd-p2-continuous-control/tags).



## Further improvements

- Implement [Prioritized Experience replay](https://arxiv.org/abs/1511.05952) to improve the experience sampling by the buffer.
- Improve exploration robustness with hyperparameter tuning

