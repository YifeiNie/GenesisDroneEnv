# Genesis Drone Environment
This repository contains example RL environment for Drones. This project has been included in the **official** [Genesis](https://github.com/Genesis-Embodied-AI/Genesis) repository and [documentation](https://genesis-world.readthedocs.io/en/latest/user_guide/getting_started/hover_env.html). This repository will continue to provide examples and may be **updated with more complex features** in the future.

## Installations

It's recommended to use a virtual environment, such as conda:

```bash
conda create -n genesis_drone python=3.11 # Requires Python >= 3.10, <3.13
conda activate genesis_drone
```

Ensure you have installed the latest version of [Genesis](https://github.com/Genesis-Embodied-AI/Genesis). And then install the repo:

```bash
git clone https://github.com/KafuuChikai/GenesisDroneEnv.git
pip install -e .
```

## Demos

### An tracking task
#### Evaluate the pretrained model
``` bash
python scripts/eval/track_eval.py
```
#### Use the provided training script to start training the policy.
``` bash
python scripts/train/track_rsl.py 
```

### Use RC control FPV in Genesis
- Flash HEX file in `./utils/modified_BF_firmware/betaflight_4.4.0_STM32H743_forRC.hex` to your FCU (for STM32H743)
- Use Type-c to power the FCU, and connect UART port (on FCU) and USB port (on PC) through USB2TTL module, like:
- <img src="./docs/hardware.png"  width="300" /> <br>
- Connect the FC and use mavlink to send FC_data from FCU to PC
- Use `ls /dev/tty*` to check the port id and modified param `USB_path` in `./config/flight.yaml`
- Do this since the default mavlink frequence for rc_channle is too low
- Connect the FC and use mavlink to send FC_data from FCU to PC
- Use FC to control the sim drone by:
``` bash
python scripts/eval/rc_FPV_eval.py.py
```

### Position controller test
- Try to get the target with no planning, thus **has poor performance**
``` bash
python scripts/pos_ctrl_eval.py
```

If you enable the visualization, you will see:

<img src="docs/training.gif" alt="training" width="70%"/>

To monitor the training process, launch `TensorBoard`:

```bash
bash scripts/shell/launch_tb.bash
```


By following this tutorial, you’ll be able to train and evaluate a basic drone hovering policy using Genesis. Have fun and enjoy!

## Acknowledgement

This repository is inspired by the following work:

1. [Champion-level drone racing using deep reinforcement learning (Nature 2023)](https://www.nature.com/articles/s41586-023-06419-4.pdf)

We acknowledge the contributions of these and future works that inspire and enhance the development of this repository.
