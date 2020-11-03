# Learning-to-Generalise-in-Sparse-Reward-Navigation-Environments
Code for "Learning to Generalise in Sparse Reward Navigation Environments" to be pubished in SACAIR 2020 Springer CCIS

**Dependancies**

- Python

- Unity ML-Agents refer to https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md for installation instructions

To install the python package run:

> pip3 install mlagents

**Training**

-Unzip Environment.Zip

-Train agents using the mlagents-learn command: Refer to https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-Configuration-File.md for further details

-mlagents-learn config/myconfig.yaml  --env=env/TEMP/TestFixedRoller --run-id=<run-identifier> --env-args=FIXED_CURIOSITY

-Hypeparameters can be adjusted in myconfig.yaml

--env refers to the location of the environment executable

--run-id allocates a unique training ID

--env-args allows for the specification of custom training settings i..e to train using one of the 3 algorihtms (curriculum, curiosity and hybrid)

-string must contain "CURRICULUM" for training under the curriculum setting 

-string must contain "CURIOSITY" for training under the curiosity setting 

-string must contain "CURIOSITY_CURRICULUM" for training under the hybrid setting 

-Additionally, reward shaping may be used

-string must contain "RAY_DIRECTED" to reward agents for moving in the direction of open rays i.e. with no obstacles in said direction

-string must contain "DISTANCE_DIRECTED" to reward agents for moving closer to the target
