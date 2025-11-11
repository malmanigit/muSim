Movement Feasibility using Inverse Kinematics and Evolutionary Algorithms
=========================================================================

.. note:

These steps are not optional. muSim training will not proceed if the targets are not appended to the xml file (see 1., 2.)

Inverse Kinematics
------------------

1. **Append the xml model with targets:**

   Run:

   ``python append_musculo_targets.py``

   This will append targets to the musculoskeletal xml file that will follow the preprocessed markers kinematics during simulation.

2. **Find the initial pose for xml model using CMA-ES and Inverse Kinematics:**

   a. Run the following command in the terminal:

      ``python find_init_pose.py --config configs/configs.txt --visualize True``

      This will use inverse kinematics (IK) to find the initial pose for the xml model to match the initial timepoint of the target kinematics.

      If you see the output, ‘Initial Pose found and saved’, skip ii.

   b. Run:

      ``python find_init_pose_ik_cma.py --config configs/configs.txt --visualize True``

      This will use CMA-ES optimization with IK to find a good initial pose for the xml model. 

      If you see, ‘Initial Pose found and saved using CMA-ES and Inverse Kinematics’, proceed to the next step. 
    
      Otherwise, provide a good inital pose for the xml model that preferably starts nearer to the inital marker/target position.
    
3. **Visualize the targets/markers trajectories using randomly initialized uSim network:**

   Run

   ``python main --config configs/configs.txt --visualize True --mode test``

   This will visualize the target trajectories using a randomly initialized muSim controller network. Make sure target trajectories look as desired. Otherwise, change the kinematic preprocessing parameters (e.g. trajectory_scaling, center) in the :doc:`task_information` file.

4. **Visualize the musculoskeletal model trajectory and save the corresponding sensory feedback:**

   Run:

   ``python visualize_trajectories_ik.py --config configs/configs.txt --visualize True``
    
    
   This will visualize the xml model following/tracking the training target trajectories. Before proceeding, make sure that the target trajectories are feasible and lie within the bounds of the xml model. Otherwise, adjust the target trajectories using the kinematics preprocessing parameters as indicated in :doc:`task_information`

   This will also save the generated sensory feedback in ``./test_data/sensory_feedback_ik.pkl`` as Python dict object: 

   ``<key: int>`` corresponds to the integer index of the corresponding training condition
   ``<value: numpy.ndarray>`` with shape: ``[timepoints, num_of_state_feedback_variables]``

This can be used to get Proprioception for further analyses.
