# CS285 - HW3
Q learning and Actor Critic

In the code you can find an agent that learn, without expert data, and only using interaction with the evironment, using Q learning and Actor Critic methods. With relatively simple method we will achive satisfying results in some atari games, like Pong.
The policy in this case is a simple NN (you can control the parameters).


# THE ALGORITHM


I will present the general steps of the solution. You can find a deeper explanation with some mathematical notations in the lectures [http://rail.eecs.berkeley.edu/deeprlcourse/](http://rail.eecs.berkeley.edu/deeprlcourse/) 
The skelaton of the solution:
1. Q learning:
2. The vanilla algorithm is to directly calculate the gradient (and approximating the mean with ampiric mean) and use gradient ascent on a nerual network. This will result in high variance
3. In order to reduce variance:
    1. Use the causality property of the environment (reward from previous actions shouldn't effect our current action choice) and thus we use "reward to go" 
    2. Consider the approach that near future rewards are more important than far future rewards (teaching our agent the consept of "fear of death") thus we can use discounting
    3. Use baselines => approximate the average reward and take actions that are better than it (calculate advantages) by fitting a baseline neural network

# SOME RESULTS

Pong with DQN:

<p align="center">
  <img src="https://github.com/zoharri/CS285/blob/master/HW3%20-%20Q%20learning%20and%20Actor%20Critic/cs285/data/dqn_q1_PongNoFrameskip-v4_09-04-2020_21-44-30/gym/PongSum.gif">
</p>

Lunar Lander with DDQN:

<p align="center">
  <img src="https://github.com/zoharri/CS285/blob/master/HW3%20-%20Q%20learning%20and%20Actor%20Critic/cs285/data/dqn_double_q_q2_doubledqn_1_LunarLander-v2_10-04-2020_22-50-22/end_gif.gif">
</p>


# RUNNING THE CODE
Be aware of some extra setup steps that are required in oreder to get this code up and running. All of the extra steps (other than the once states in the main README) are presented in the assignment pdf.

Run the DQN for Pong, be aware that the full training time can reach 20 hours (tested with RTX2060):
```sh
python run_hw3_dqn.py --env_name PongNoFrameskip-v4 --exp_name q1
```
Run the DDQN for LunarLander, this one has a very short training time (few minutes):
```sh
python run_hw3_dqn.py --env_name LunarLander-v2 --exp_name q2_doubledqn_1 --double_q --seed 1
```
Run the Actor Critic for Half Cheetah:
```sh
python run_hw3_actor_critic.py --env_name HalfCheetah-v2 --ep_len 150 --discount 0.90 --scalar_log_freq 1 -n 150 -l 2 -s 32 -b 30000 -eb 1500 -lr 0.02 --exp_name 10_10 -ntu 10 -ngsptu 10 --video_log_freq 10
```

View the results with:
```sh
cd cs285/data/<your_log_dir>
tensorboard --logdir 
```
For more running options please reffer to the pdf included in the HW3 folder

<!-- CONTACT -->
# CONTACT
Zohar Rimon - zohar.rimon@campus.technion.ac.il

Project Link: [https://github.com/zoharri/CS285](https://github.com/zoharri/CS285)
