# Report on the Navigation project


## Learning Algorithm
	
The used learning agent is based on the Deep Q-Learning with fixed Target algorithm, illustrated on LunarLander environment.

Main adjustements were done on communicating between agent and Unity environment:
``sh
action = (int)(agent.act(state, eps))
#next_state, reward, done, _ = env.step(action) - was used in LunarLander
env_info = env.step(action)[brain_name]
next_state = env_info.vector_observations[0]   # get the next state
reward = env_info.rewards[0]                   # get the reward
done = env_info.local_done[0]                  # get the done

``
## Progress and hyperparameters estimation
	
First attempt was done with following model architecture:
`
input (37) -> ReLU -> fully connected layer (fcl) (100) -> ReLU -> fcl (80) -> output (4)
`

Hyperparameters were following:
``sh
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 10         # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR = 0.01               # learning rate 
UPDATE_EVERY = 4        # how often to update the network
``

The resulted learning progress was frustrating:
``sh
Episode 100	Average Score: -0.01
Episode 200	Average Score: 0.172
Episode 300	Average Score: -0.02
Episode 400	Average Score: -0.20
Episode 500	Average Score: -0.01
``
I interrupted the kernel, so there is no plot, but results are obvious anyway.

## Ideas for Future Work
	
 - Change the model architecture
 - Decrease the learning rate `LR`
 - Increase the interval for updating the target network `UPDATE_EVERY`
