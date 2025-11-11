Perturbation Modules
====================

We have provided the following perturbation modules for analyzing the trained muSim controller robustly under altered conditions:

Selective Feedback Elimination (SFE)
------------------------------------

Specify the part of the sensory feedback to be eliminated in ``./SAC/perturbation_specs.py`` using ``sf_elim`` variable. 

Run:

``python main --config configs/configs.txt --mode SFE --visualize True``

Sensory Perturbation
--------------------

Specify the perturbation vector to be added to the selected sensory feedback in ``./SAC/perturbation_specs.py``, e.g. ``muscle_lengths_pert``. 

Run:

``python main.py --config configs/configs.txt --mode sensory_pert --visualize True``

Neural Perturbation
-------------------

The neural perturbation will add the given perturbation to the nodes of the uSim/nuSim controller’s RNN.

Specify the neural perturbation vector in ``./SAC/perturbation_specs.py`` using ``neural_pert`` variable. 

Run:

``python main.py --config configs/configs.txt --mode neural_pert --visualize True``

Change Musculoskeletal Properties
---------------------------------

To test the trained muSim controller under changed musculoskeletal properties:

1. Go to the folder ‘./musculoskeletal_model/’. Copy and paste the xml model ‘musculo_targets.xml’. Rename the copied model as ‘musculo_targets_pert.xml’.

2. Change the desired musculoskeletal properties in xml model ‘musculo_targets_pert.xml’.

3. Run:

``python main.py --config configs/configs.txt --mode musculo_properties --visualize True``

All the above perturbation analyses will change the post training analyses files in place. To run the post training analyses after perturbation see :doc:`qualitative_modules` and :doc:`quantitative_modules` section.
