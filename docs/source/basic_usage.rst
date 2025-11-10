Basic Usage for Monkey Cycling Task
-----------------------------------
-----------------------------------

1. To train the controller, run the following in terminal:

   ``python append_musculo_targets.py``

   ``python find_init_pose.py --config configs/configs.txt``

   ``python main.py --config configs/configs.txt``

   This will save the controller in the ./checkpoint file with training iterations. The highest reward should reach >= 55000 for kinematic accuracy.

   The episode reward with iterations should look like this:
   (There may be slight variations due to random seed but trend should look similar)
