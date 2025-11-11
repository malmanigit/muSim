muSim Training
==============

Training the uSim Controller using DRL
--------------------------------------

.. note: 
Make sure DRL algorithm related parameters are specified correctly in :doc:`training_specs`

1. To train the muSim controller using the selected DRL algorithm, run:

   ``python main.py --config configs/configs.txt``
    
2. To continue the training from the previous session, run:

   ``python main.py --config configs/configs.txt --load_saved_nets_for_training True``
