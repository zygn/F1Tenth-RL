# F1Tenth PPO

This repository contains all our code as well as an F1Tenth Gym repository fork, as a submodule. You can find the [documentation](https://f1tenth-gym.readthedocs.io/en/latest/) of the F1Tenth Gym environment here.

This is an implementation of a simple reinforcement learning (RL) algorithm for teaching an F1Tenth car to race using a simple proximal policy optimization (PPO) algorithm. Random race tracks are used to help the agent adapt to different environments.

## Quickstart

#### 1. Cloning the repository

```bash
$ git clone --recurse-submodules https://github.com/FT-Autonomous/Team-1.git
$ cd Team-1
```

**N.B.** Don't forget to include the ```--recurse-submodules``` argument when cloning our repo, or else the F1Tenth Gym won't be cloned!

#### 2. Running the Docker container

You can build and run the environment in Docker, alongside **Stable Baselines 3** (our choice of RL library), by running the corresponding command for your OS below. Make sure you are in the main ```Team-1``` directory, the same place as the Dockerfile, when you run these commands.

**Note:** The first time you run the command it will download and build your image, which will take a while.

- ##### Windows

  ```bash
  $ call scripts/docker-windows.bat
  ```
  Then open **XLaunch**, the same software used in David's [Docker Setup Guide](https://github.com/FT-Autonomous/Autonomous_Crash_Course/tree/main/docker-setup)

- ##### Linux

  ```bash
  $ source scripts/docker-linux.sh
  ```
To build the GPU version of the Stable Baselines 3 container, append ```--gpu``` to the end of the above commands

| Version |    Size     |
| ------- | :---------: |
| CPU     | 3.41 **GB** |
| GPU     | 6.86 **GB** |

#### 3. Testing the installation

To test the installations of Stable Baselines 3 and F1Tenth Gym, along with the F1Tenth Gym visuals, run these commands inside the Docker container :

```bash
$ cd /home/formula/Team-1
$ python3 simple_example.py
```

#### 4. Writing code

You will need VS Code with the ```Remote - Containers``` extension installed, full extension name is ```ms-vscode-remote.remote-containers```

- Start the Docker container as per the previous instructions, then open VS Code
  - Open the VS Code command palette with the keyboard shortcut ```ctrl-shift-p``` 
  - Search for and run the command ```Remote-Containers: Attach to Running Container```
  - Choose the ```f110-rl-container```
- To get code auto-completion working you will need to install the Python extension ```ms-python.python``` once VS Code has connected to the running container. You should also right click on the extension and click ```Add to devcontainer.json``` to load the extension automatically when you attach to the container. You can install any extensions you'd like inside the container but it will take up extra space.

#### 5. Training and testing example

You can do some initial training of an agent using the ```simple-example.py``` script; the first half trains an agent (poorly) and the second half runs the trained agent on the F1Tenth environment and renders it for you to see!

Have a look at this file and change the training steps, models, and policies to try and improve the car's performance around the track. You can change the reward function by looking at the ```step(self, action)``` function in ```wrappers.py``` 

# Acknowledgements
Thanks to [Eoin Gogarty](https://github.com/avantgarda) as the lead developer of the F1Tenth Gym training and evaluation framework, and [Charlie Maguire](https://github.com/maguic11) and [Manus McAuliffe](https://github.com/mmcaulif) for contributing ideas and parts towards development.

# F1TENTH
If you find F1Tenth Gym as interesting to use as we did, you can cite them and include the licenses in your code. Bibtex citation below.
```
@inproceedings{okelly2020f1tenth,
  title={F1TENTH: An Open-source Evaluation Environment for Continuous Control and Reinforcement Learning},
  author={O’Kelly, Matthew and Zheng, Hongrui and Karthik, Dhruv and Mangharam, Rahul},
  booktitle={NeurIPS 2019 Competition and Demonstration Track},
  pages={77--89},
  year={2020},
  organization={PMLR}
}
```