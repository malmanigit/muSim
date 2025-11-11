muSim Training
==============

Training the uSim Controller using DRL
--------------------------------------

.. note: 
Make sure DRL/SAC related parameters are specified correctly in the ``./configs/configs.txt`` file

1. To train the uSim controller using the provided DRL algorithm, run:

   ``python main.py --config configs/configs.txt``
    
2. To continue the training from the previous session, run:

   ``python main.py --config configs/configs.txt --load_saved_nets_for_training True``
