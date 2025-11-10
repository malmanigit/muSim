Task Information
================

Kinematics:
-----------

Experimental Kinematics
~~~~~~~~~~~~~~~~~~~~~~~

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



Sensory Feedback Preprocessing:
-------------------------------

