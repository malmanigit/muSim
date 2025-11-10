Installation
============

.. note:: We highly recommend a linux system for easy installation.

** INSTALLATION **

1. Create a new environment using conda:

    `conda env create --name nusim --file=requirements.yml`

2. Activate the conda environment:

    `conda activate nusim`


If facing errors
----------------

** Install MuJoCo 3.0 before proceeding **

1. If you are on linux (and may apply to Mac as well), there will likely be additional packages necessary. Here is a list of possible packages:

    * patchelf
    * python3-dev
    * build-essential
    * libssl-dev
    * libffi-dev
    * libxml2-dev
    * libxslt1-dev
    * zlib1g-dev
    * libglew1.5
    * libglew-dev
    * libosmesa6-dev
    * libgl1-mesa-glx
    * libglfw3

2. Lastly, within the conda environment there are additional packages necessary to ensure the training can run:

    * cython
    * matplotlib
    * scipy
    * torch
    * PyYaml
    * configargparse
    * numpy
    * gym
    * pandas
    * pyquaternion
    * scikit-video
