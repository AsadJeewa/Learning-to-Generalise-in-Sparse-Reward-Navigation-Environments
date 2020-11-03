# Learning-to-Generalise-in-Sparse-Reward-Navigation-Environments
Code for *Learning to Generalise in Sparse Reward Navigation Environments* to be pubished in *SACAIR 2020 Springer CCIS*

**Dependancies**

- Python

- Unity ML-Agents refer to https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md for installation instructions

To install the python package run:

> pip3 install mlagents

Code was tested on ml-agents version 0.16.0.

> pip3 install mlagents==0.16.0

**Training**

- Unzip Environment.Zip

- Train agents using the mlagents-learn command: Refer to https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-Configuration-File.md for further details

> mlagents-learn config/myconfig.yaml  --env=env/Environment --run-id=<run-identifier> --env-args=CURRICULUM

- Hypeparameters can be adjusted in myconfig.yaml

- --env refers to the location of the environment executable

- --run-id allocates a unique training ID

- --env-args allows for the specification of custom training settings 

  - Specify the training algorithm i.e. curriculum, curiosity or hybrid

    - String must contain "CURRICULUM" (any case) for training under the curriculum setting 

    - String must contain "CURIOSITY" for training under the curiosity setting 

    - String must contain "CURIOSITY_CURRICULUM" for training under the hybrid setting 

  - Additionally, reward shaping may be used

    - String must contain "RAY_DIRECTED" to reward agents for moving in the direction of open rays i.e. with no obstacles in said direction

    - String must contain "DISTANCE_DIRECTED" to reward agents for moving closer to the target
