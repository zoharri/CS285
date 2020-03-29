# CS285 - HW2
Policy gradient 

In the code you can find an agent that learn, without expert data, and only using interaction with the evironment, using Policy gradient method.
The policy in this case is a simple NN (you can control the parameters).


# THE SOLUTION


I will present the general steps of the solution. You can find a deeper explanation with some mathematical notations in the lectures [http://rail.eecs.berkeley.edu/deeprlcourse/](http://rail.eecs.berkeley.edu/deeprlcourse/) 
The skelaton of the solution:
1. Our goal is t maximize the expectancy of the total reward under the agents policy (and the transition dynamics that are not known)
2. The vanilla algorithm is to directly calculate the gradient (and approximating the mean with ampiric mean) and use gradient ascent on a nerual network. This will result in high variance
3. In order to reduce variance:
    1. Use the causality property of the environment (reward from previous actions shouldn't effect our current action choice) and thus we use "reward to go" 
    2. Consider the approach that near future rewards are more important than far future rewards (teaching our agent the consept of "fear of death") thus we can use discounting
    3. Use baselines => approximate the average reward and take actions that are better than it (calculate advantages) by fitting a baseline neural network

# RUNNING THE CODE
Run the code with all of the features:
```sh
python run_hw2_policy_gradient.py --env_name HalfCheetah-v2 --ep_len 150 --discount 0.95 -n 100 -l 2 -s 32 -b <b> -lr <r> --video_log_freq -1 --reward_to_go --nn_baseline --exp_name hc_b<b>_lr<r>_nnbaseline
```


View the results with:
```sh
cd cs285/data/<your_log_dir>
tensorboard --logdir 
```
For more running options please reffer to the pdf uncluded in the HW2 folder

<!-- CONTACT -->
# CONTACT
Zohar Rimon - zohar.rimon@campus.technion.ac.il

Project Link: [https://github.com/zoharri/CS285](https://github.com/zoharri/CS285)
