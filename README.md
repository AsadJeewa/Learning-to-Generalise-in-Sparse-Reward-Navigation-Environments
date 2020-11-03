# Learning-to-Generalise-in-Sparse-Reward-Navigation-Environments
Code for *Learning to Generalise in Sparse Reward Navigation Environments* to be pubished in *SACAIR 2020 Springer CCIS*

Note that the environments here run on **Windows**. The algorithms from the paper were run on a high performance computer (https://www.chpc.ac.za/) on a Linux environment.

**Dependancies**

- Python

- Unity ML-Agents refer to https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md for installation instructions

To install the python package run:

> pip3 install mlagents

Code was tested on ml-agents version 0.16.0 so we recommend running

> pip3 install mlagents==0.16.0

- This will create an ml-agents folder referred to as *HOME*

**Training**

- Hypeparameters can be adjusted in config/config.yaml. **NB:** Place config/config.yaml in *HOME*/ folder 

- Train agents using the mlagents-learn command: Refer to https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-Configuration-File.md for further details

> mlagents-learn config/config.yaml  --env=env/Environment --run-id=<run-identifier> --env-args=CURIOSITY

- To train using the curriculum, specify the location of the curriculum file with the --curriculum arg. **NB:** Place curiculua/curriculum.yaml in *HOME*/ folder 

> mlagents-learn config/config.yaml  --env=env/Environment --run-id=<run-identifier> --curriculum=config/curricula/curriculum.yaml --env-args=CURRICULUM

- **--env** refers to the location of the environment executable. **NB:** Unzip Environment.zip and place contents in *HOME*/env/ 

- **--run-identifier** allocates a unique identifier for the run

- **--env-args** allows for the specification of custom training settings 

  - Specify the training algorithm i.e. curriculum, curiosity or hybrid. This will sample training environemnts accrdingly.

    - String must contain "CURRICULUM", case insensitive, for training under the curriculum setting 

    - String must contain "CURIOSITY" for training under the curiosity setting. Note that the curisoity signal still needs to be specified in *HOME*/config/config.yaml (uncomment the exisiting parameters)

    - String must contain "CURIOSITY_CURRICULUM" for training under the hybrid setting 

  - Additionally, reward shaping may be used

    - String must contain "RAY_DIRECTED" to reward agents for moving in the direction of open rays i.e. with no obstacles in said direction

    - String must contain "DISTANCE_DIRECTED" to reward agents for moving closer to the target
    
**Testing**
- **NB:** To run in inference mode, copy the pretrained models to *HOME*/models/

- Use the mlagents-learn command

> mlagents-learn config/config.yaml  --env=env/Environment --run-id=<run-identifier> --curriculum=config/curricula/curriculum.yaml --env-args=TEST_OBSTACLE_ENV
  
  - String must contain "TEST" to specify testing mode to evaluate pretrained models. (Default mode is training mode)
  
  - Thereafter, additional parameters need to be specified. The environment sets need to be specified:

    - String must contain "TRAIN_ENV" to evaluate on the *training* environments

    - String must contain "STANDARD_ORIENTATION_ENV" to evaluate on the *standard orientation* environments

    - String must contain "STANDARD_NEW_ENV" to evaluate on the *standard new* environments

    - String must contain "DIFFICULT_ORIENTATION_ENV" to evaluate on the *difficult orientation* environments 
    
    - String must contain "DIFFICULT_NEW_ENV" to evaluate on the *difficult new* environments 
  
  - The testing mode can be specified:
  
    - String can contain "RANDOM" to sample enviroments from the specified category randomly, as per the paper

    - String must contain "SEQUENTIAL" to sample enviroments from the specified category sequentially
  
  -The raw scores will be placed in a textfile in you *HOME* folder
