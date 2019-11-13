# Reach out
[![License](https://img.shields.io/badge/License-MIT-brightgreen.svg)](LICENSE) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/1d6d58ddc5f4445492172f9b349668bc)](https://www.codacy.com/manual/fg/drlnd-p2-continuous-control?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=frgfm/drlnd-p2-continuous-control&amp;utm_campaign=Badge_Grade) [![CircleCI](https://circleci.com/gh/frgfm/drlnd-p2-continuous-control.svg?style=shield)](https://circleci.com/gh/frgfm/drlnd-p2-continuous-control)

This repository is an implementation of DDPG agent for the continuous control project of Udacity Deep Reinforcement Learning nanodegree, in the reacher environment provided by unity.

![reacher-gif](https://video.udacity-data.com/topher/2018/June/5b1ea778_reacher/reacher.gif)



## Table of Contents

- [Environment](#environment)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Credits](#credits)
- [License](#license)



## Environment

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

The task is episodic, and in order to solve the environment, your agent must get an average score of +30 over 100 consecutive episodes.



## Getting started

### Prerequisites

- Python 3.6 (or more recent)
- [pip](https://pip.pypa.io/en/stable/)
- [ml-agents](https://github.com/Unity-Technologies/ml-agents) v0.4 (check this [release](https://github.com/Unity-Technologies/ml-agents/releases/tag/0.4.0b) if you encounter issues)

### Installation

You can install the project requirements as follows:

```shell
git clone https://github.com/frgfm/drlnd-p2-continuous-control.git
cd drlnd-p2-continuous-control
pip install -r requirements.txt
```

Download the environment build corresponding to your OS

- Linux: [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
- Mac OSX: [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip)
- Windows (32-bit): [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86.zip)
- Windows (64-bit): [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)

Then extract the archive in the project folder.



If you wish to use the agent trained by repo owner, you can download the model parameters as follows:

```shell
wget https://github.com/frgfm/drlnd-p2-continuous-control/releases/download/v0.1.0/ddpg_actor.pt
```



## Usage

### Training

All training arguments can be found using the `--help` flag:

```shell
python train.py --help
```

Below you can find an example to train your agent:

```shell
python train.py --deterministic --no-graphics
```

### Evaluation

You can use an existing model's checkpoint to evaluate your agent as follows:

```shell
python evaluate.py --checkpoint ./ddpg_actor.pt
```



## Credits

This implementation is vastly based on the following papers:

- [Asynchronous Actor Critic](https://arxiv.org/pdf/1602.01783.pdf)

- [Proximal Policy Optimization](https://arxiv.org/pdf/1707.06347.pdf)
- [DDPG](https://openreview.net/pdf?id=SyZipzbCb)



## License

Distributed under the MIT License. See `LICENSE` for more information.