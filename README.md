# dqn_carla
Package Description: This package containes the code implemented for deep Q learning. Deep Q learning assisted by waypoints is used to make the vehicle in Carla Urban simulator learn how to drive itself without collide. 

Policy Description: No traffic and line following rules are applied to this training and testing.

Sorfware installation:

Python: need to use python3. i have python3.8: sudo apt install python3.8

Carla version: 0.9.6. Use the following link to download Carla Urba Simulator:
https://github.com/carla-simulator/carla/releases/tag/0.9.6
I use linux system, so i download CARLA_0.9.6.tar.gz from my end. 

Tensorflow: version need to be above 2.0: sudo apt install Tensorflow

Carla usage:
To use the Carla simulator, cd into the Carla package directory where the CarlaUE4.sh located. Type the command ./CarlaUE4.sh in the terminal to run carla simulator.

Code usage:
refined_dqn.py is the python file where i implement the DQN algorithms and build the carla agent and environemnt. Refined_dqn.py is used to train and agent.
To apply the policy trained by refined_dqn.py and see it in carla simulator. Run agent.py file.

Training process:
Before training, ./CarlaUE4 need to be typed in the terminal to run the simulator. Meanwhile, run the refined_dqn.py. You can also see the performance during the training process, you can make one of the parameter called: SHOW_PREVIEW to be true. After training, self.log_dir file shows in the same directory where refined_dqn.py located. cd in it and use tensorboard --logdir ./ to see the plots results for eplision(randomness) and rewards vs episodes. The trained policy should be stored into a file called Model also in the same directory as refined_dqn.py at. 

Show Agent in Carla with trained policy:
Run Carla simulator and agent.py at the same time.

Best Trained policy:
https://drive.google.com/file/d/15gvw7sJG5bHWrBxXhyx4UzRxd7rhfx9-/view?usp=sharing

DQN algorithms:
The target pipeline is to make spawned vehicle learn the environment and drive itself without collide under no traffic or line following rules. To save the randomness time, guided waypoints are generated near the spawned location and add them to reward function. 

Rewards:
Reward policy1: give huge penalty to collision (around -200 to 500)
Reward policy2: give reward for driving to the watpoints location (around 50 to 100)
Reward policy3: give reward for non-collision case (around 20)
Reward policy4: give penalty for the speed below 40 mph (around -5)

Data:
Collision sensor:
I add the collision sensor and camera at the front of the car. The collision sensor will detect the collision and send the message. I have a list called collision_list and is initialized to be an empty list. During the process, I will decide if there is a collision based on the collision list is empty or not. 

Camera:
Camera spawned in front of the car will provide RGB data input into the DQN network. 










