Experimental Data
=================

Neural Data (optional)
----------------------

1. Save the recorded neural data for the training and testing conditions in ‘./nusim_neural_data/neural_activity.pkl’ as a Python dict object

.. code-block::


   dict{

      <'train'> : <dict_train>,

      <'test'> : <dict_test>

   }

2. ``<dict_train>`` and ``<dict_test>`` are Python dictionary objects that contain the neural data in the following format:

   ``<key: int>`` is the integer index of the corresponding condition as in the kinematics file.

   ``<value: numpy.ndarray>`` is the numpy array that contains recorded firing rates with the following shape: ``[timepoints, num_neurons]``. num_neurons are the total number of recorded neurons.

.. note::

   If this step is omitted, various post-training *quantitative* analyses which require recorded neural data such as CCA, will not run. nuSim training will also not proceed (nusim_data_path can also be specified in the configs.txt file).

Stimulus Data (optional)
------------------------

Provide any experimental stimulus data in ``./stimulus_data/stimulus_data.pkl`` as a Python dict object:: 

   dict{

      <'train'> : <dict_train>,

      <'test'> : <dict_test>

   }

1. ``<dict_train>`` and ``<dict_test>`` are Python dictionary objects that contain the experimental stimulus data in the following format:

   ``<key: int>`` is the integer index of the corresponding condition as in the kinematics file.

   ``<value: numpy.ndarray>`` is the numpy array that contains recorded stimulus data with the following shape: ``[timepoints, num_features]``. num_features are the corresponding features in that stimulus.

Initial Pose Data (optional)
----------------------------

Save the initial pose (containing the qpos and qvel) as numpy arrays in ``./inital_pose/`` as qpos.npy and qvel.npy with shape ``[nq, ]``. nq is the number of joints in the xml model.

This step is optional. If omitted, the default initial pose for xml model will be used for CMA-ES and IK.

(initial_pose_path can also be specified in the ``./configs/configs.txt`` file)
