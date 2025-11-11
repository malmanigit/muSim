Post-Training Qualitative Modules
=================================

We have provided the following post-training qualitative modules for the trained muSim controller.

Kinematics Visualization
------------------------
To visualize the kinematics for the training and testing conditions, see ``visualize_kinematics.ipynb``

PCA
---

To visualize the uSim controller’s population trajectories in PCA subspace, run:

``python collective_pca.py``

Fixed-Point Analysis
--------------------

Clone the fixed-point-finder in ./Analysis, ``https://github.com/mattgolub/fixed-point-finder``

Run the following command in terminal:

``python find_fp.py``

The fixed point analysis is based on the original implementation: ``https://github.com/mattgolub/fixed-point-finder``. Refer to the github repo for further information.


Rotational Dynamics
-------------------
.. note: jPCA analysis is based on MM Churchland’s original implementation and required *MATLAB*. Please see it for further details ``https://www.dropbox.com/scl/fo/duf5zbwcibsux467c6oc9/AIN-ZiFsy2Huyh8h7VMdL7g?rlkey=3o5axmq5hirel4cij7g64jc0r&e=1&dl=0``

See and run ``jpca_nusim.m``

**Important for jPCA analysis:**

1. Make sure that ./Analyses/jPCA_ForDistribution is included in the MATLAB path alongwith all sub-directories

2. Make sure that usim test_data folder is included in the MATLAB path. test_data folder is where the jpca data is saved during usim test

