Training Specifications
=======================

Specify the following parameters in the ``./configs/configs.txt`` file for the specification of the training algorithm.

**model**

The neural network model to use in the agent, can be ['rnn', 'gru']

**hidden_size**

The number of hidden units in the layers of the agent's neural network

**mode**

The mode of simulation can be [train, test, SFE, sensory_pert, neural_pert, musculo_properties]

**RL_algorithm = 'SAC'**

The RL algorithm can be either [SAC, DDPG, TD3] (Standard DRL algorithms)

**cuda = True/False**
Utilize GPU for training.

** Other DRL specific parameters **
gamma = 0.99
tau = 0.005
lr = 0.0003
alpha = 0.20
automatic_entropy_tuning = True
seed = 123456
policy_batch_size = 8
policy_replay_size = 4000
multi_policy_loss = True
batch_iters = 1
total_episodes = 1000000
condition_selection_strategy = "reward"

** For the TD3 algorithm, the following parameters must be specified((
target_noise = .2
target_noise_clip = .5
policy_delay = 2
