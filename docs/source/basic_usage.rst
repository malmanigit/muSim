Basic Usage for Monkey Cycling Task
-----------------------------------
-----------------------------------

To train the muSim controller for the monkey cycling task, run the following in terminal:

   ``python append_musculo_targets.py``

   ``python find_init_pose.py --config configs/configs.txt``

   ``python main.py --config configs/configs.txt``

   This will save the controller in the ./checkpoint file with training iterations. The highest reward should reach >= 55000 for kinematic accuracy.

   The episode reward with iterations should look like this for successfull training:

   .. figure:: ./reward_curve.png
