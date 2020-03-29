# CS285 - HW1
Homework1 solution. 

In the code you can find an agent that learn, using imitation learning and the DAgger algorithm, from expert policy to do several tasks (such as making a juman run in the mujoco environment).
The agent's policy in this case is a simple NN (you can control the parameters).

<!-- The solution -->
I will present the general steps of the solution. Youcan find a deeper explanation with some mathematical notations in the lectures [http://rail.eecs.berkeley.edu/deeprlcourse/](http://rail.eecs.berkeley.edu/deeprlcourse/) 
The skelaton of the solution:
1. First train on expert data - a regression problem, fitting the agent's policy to the expert actions
2. This will lead us to a solution but (as seen in lecture 2) the error of the solution with respect to the expert policy will behave as <MATH>O(T^2)</MATH>, where T is the time since the beginning of the run.
3. In order to fix this problem we use, after the first fitting iteration, the DAgger algorithm:
3.1 Get a trajectory from the current agents policy
3.2 Re-lable the trajectory with the experts policy
3.3 Fit the agents policy

<!-- Running the code -->
# Running the code
Run the code (with dagger) with:
```sh
python cs285/scripts/run_hw1_behavior_cloning.py --expert_policy_file cs285/policies/experts/Ant.pkl --env_name Ant-v2 --exp_name test_dagger_ant --n_iter 10 --do_dagger --expert_data cs285/expert_data/expert_data_Ant-v2.pkl
```
View the results with:
```sh
cd cs285/data/<your_log_dir>
tensorboard --logdir 
```

<!-- CONTACT -->
# CONTACT
Zohar Rimon - zohar.rimon@campus.technion.ac.il

Project Link: [https://github.com/zoharri/CS285](https://github.com/zoharri/CS285)





