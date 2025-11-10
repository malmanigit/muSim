Biological Constraints
======================

Biological constraints are implemented as neural regularizations or constraints on muscle effort utilized.

Neural Regularizations
----------------------

Specifications for Neural Regularizations with the policy network or the muSim controller.

Specify the weightings with various neural regularizations used in muSim/nuSim

**alpha_usim**

weighting with loss term enforcing simple neural dynamics for muSim/nuSim

**beta_usim = 0.01**

weighting with loss term enforcing minimization of the neural activations for muSim/nuSim

**gamma_usim**

weighting with loss term minimizing the synaptic weights for muSim/nuSim

**zeta_nusim**

weighting with loss for nuSim constraining a sub-population of RNN units to experimentally recorded neurons for nuSim
