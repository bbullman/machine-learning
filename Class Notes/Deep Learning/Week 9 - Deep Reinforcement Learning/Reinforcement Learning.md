* Deep reinforcement learning is standard reinforcmeentl earning where a deep neural network is used to approximate either a policy or a value function.
* Deep neural networks require lots of real and simulated interaction with their environment.
* Lots of trials/interactions are possible in simulated environments.
* We can easily parallelize the trials/interactions in simulated environments.
* We cannot do this with robotics (no simulations) because action execution takes time, accidents/failures are expensive and there are safety concerns.

## Philosophical Motivation for DRL

* Takeaway from Supervised Learning

## Markov Decision Process

Finite State Transducer applied at every timestep will become a Markov Decision Process.

![[lesson09_finite_state_transducer.png]]

Markov Property: Current state completely characterizes the state of the world:
* State Space
* Action Space
* Transition Function
* Reward Function

* Short term gain vs. Longterm value: we apply a Discount Factor [0, 1]
* We want to be greedy but not impulsive
* Implicitly takes uncertainty in dynamics into account
* Mathematically: y < 1 allows infinite horizon returns.

Example: Simple MDP with Grid World

![[lesson09_gridworld.png]]

* Random Policy: traditional algorithms will do a search.
* Optimal Policy is what we will do.

![[lesson09_MDP_Algorithm.png]]

* This involves dynamic programming.
* At each timestep there's astochastic policy mapping from states to probabilities selecting each possible action. 

* **State-Value Functions**
	* Value functions are defined with respect to the policy
	* If the current state is s, the policy is pi, what is the expected value we'll get?
	* The value of the terminal state is always zero.
* **Action-Value Function**
	* The value q(s,a) of taking action a in state s under a policy pi is defined as the expected return starting from s1, taking the action and therefore following the policy pi.
* **Bellman Equation**
	* Bellman is the inventor of dynamic programming.
	* The equation expresses the relationship between the value of a state s and the values of successor states
	* The value of the next state must equal the discounted value of the expected next state plus the sum 
	* The value of state s is the expected value of the sum of time-discounted rewards ( starting at current state) given the current state s
	* This is expected value of r plus the sum of time-discounted rewards (starting at successor state) over all successor states s^1 and all the next rewards r and over all possible actions a in current state s

* Throughout Grid World we want to use Exploration vs. Exploitation
	* Exploitation: Use everything from the past
	* Exploration: Use all our options
	* The balance between this is epsilon decay
	* Epsilon-Greedy policy: 
		* At each time step the agent selects an action
		* The agent follows the greedy strategy with probability 1-epsilon
		* The agent selects a random action with probability epsilon
		* With Q-learning, the greedy strategy is the action A that maximizes Q given St+1

## Deep Q-Learning Network

* DQN is somewhat stable because it stores the agent's data in experience replay memory so that it can be randomly sampled from different time steps
* Policy Gradients can be used.
* Deep Q learning doesn't work with a large or continuous action space
* Policy gradients deal directly with choosing actions (tweaking policy function)
* No need to compute precise values for each state

## Other Types of Reinforcement Learning

* Combined with CNNs
* Epsilon Greedy
* Experience Replay
* Fixed Q-targets
* Dueling Networks