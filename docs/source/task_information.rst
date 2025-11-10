Task Information
================

Kinematics:
-----------

Experimental/Task Kinematics
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Save the experimental kinematics in ``./kinematics_data/kinematics.pkl`` as a Python dict object with the following format

.. code-block::

    
   dict{
    
      <'marker_names'> : <['marker_name_1', ..., 'marker_name_n']>,

      <'train'> : <dict_train>,

      <'test'> : <dict_test>

   }

2. ``<marker_names>`` contain a list of names of the experimental markers that were recorded. The marker_name must correspond to a body name in the musculoskeletal model xml file. 

3. ``<dict_train>`` and ``<dict_test>`` are Python dictionary objects that contain kinematics in the following format

.. code-block::


   { 

      <key> :   <value>,

      <key>:   <value>,

      .
      .
      .

      <key>: <value>

   }

``<key: int>`` is the integer index of the corresponding condition. (starts from 0 for the first condition for both the training and testing conditions) 

``<value: numpy.ndarray>`` contains the kinematics for the corresponding condition with shape: ``[num_markers/targets, num_coordinates = 3, timepoints]``. 

``num_markers`` are the number of experimental markers/bodies that are recorded. The order of the num_markers must correspond to the order in which the marker_names are listed. For example, if ``marker_names = [hand, elbow]``, ``num_marker= 0`` should contain the experimental kinematics for hand and ``num_marker=1`` should contain the experimental kinematics for elbow.

num_coordinates are the x [-->], y[↑] and z[ out of page] coordinates. Values of NaN for any coordinate will keep that coordinate locked. 

An example for saving the experimental kinematics for the cycling task is given in ``./exp_kin_cycling/saving_exp_kin.ipynb``

(The path to kinematics.pkl file can also be specified using *kinematics_path* param in configs.txt file) 

Kinematic Preprocessing:
------------------------
Adjust the following Kinematic Preprocessing Parameters in the ``./configs/configs.txt`` file:

**sim_dt**

The timestep for the simulation: Keep 0 for default simulation timestep

**frame_repeat**

The frames/timepoints for which the same action should be repeated during training of the muSim controller.

For finer movements user smaller frame_repeat. However, it will also sharply increase the training time.

**n_fixedsteps**

Number of fixedsteps in the beginning of the simulation. The target will remain at kinematic[timestep=0] for n_fixedsteps.

If a good initial position is found using CMA-ES / IK Optimization, n_fixedsteps = 25 is a good estimate. Otherwise increase if the starting reward does not increase with the training iterations.

**timestep_limit**

Timestep limit is max number of timesteps after which the episode will terminate.

Multiple cycles of the same condition will be simulated if the timestep_limit > number of timsteps for that condition.

**trajectory_scaling**

Adjusts/scales the length of the trajectory

Should be the same shape as num_markers/targets

**center**

Adjusts the starting point of the kinematics trajectory

Should be of the same shape as num_markers/targets, num_coords=3


Sensory Feedback Preprocessing:
-------------------------------

Adjust the following Sensory Feedback Preprocessing parameters in the ``./configs/configs.txt`` file:

**stimulus_feedback = True/False**

#Stimulus feedback consists of provided experimental stimulus data

**proprioceptive_feedback = True/False**

#Proprioceptive feedback consists of muscle lengths and velocities

**muscle_forces = True/False**

Muscle forces consist of appled muscle forces 

**joint_feedback = True/False**

Joint feedback consists of joint positions and velocities

**visual_feedback = True/False**

Visual feedback consists of x/y/z coordinates of the specified bodies in the model

If visual_feedback is True, specify the names of the bodies from musculoskeletal_model.xml for which the feedback should be included

**visual_feedback_bodies**

Append the musculo bodies from which visual feedback should be included

This list can also consist of targets/markers

Append targetn-1 for visual feedback from targets/markers in the kinematics.pkl file

'target0' corresponds to the visual feedback from the first target/marker, target1 to the second target/marker and so on

**visual_distance_bodies**

Specify the names of the bodies as tuples(separated by ; with no spaces) for which the visual distance should be included in the feedback

Leave blank if the visual distance is not to be included in the feedback

Visual distance between the bodies will be included

e.g visual_distance_bodies = [[hand;target0], [elbow;target0]] will include the distance between the hand/elbow and first marker in sensory feedback

**visual_velocity = []**

Specify the names of the bodies for which the visual velocity should be included in the feedback

Leave blank if the visual velocity is not to be included in the feedback

Appends the absolute musculo body velocity, e.g. visual_velocity = [hand, target0]

will include the xyz velocities of hand and target0

**sensory_delay_timepoints**

Specify the delay in the sensory feedback in terms of the timepoints


