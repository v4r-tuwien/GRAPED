# GRAPED (GRAsp, Pose Estimation and object Detection) (Title not final)

This repository serves as a central hub for multiple grasp estimators, object detectors and pose estimators. And heavily based on [DOPE](https://github.com/lexihaberl/DOPE.git).

- PUT YCBV DATASET IN datasets
- smth regarding prepare templates stuff for zs6d
- smth regarding setup.sh for cnos

## Cloning the repository

To clone this repository with all its submodules:
```bash
git clone --recurse-submodules git@github.com:v4r-tuwien/GRAPED.git
```

If you have already cloned the repository without the submodules, you can initialize and update them with:
```bash
git submodule update --init --recursive
```

## Downloading model weights
### yolov8 and gdrnpp
You can download the pretrained model weights with the following command:
```bash
bash scripts/download_weights.sh
```
Double check the files got correctly copied to `data/datasets` and `data/weights` as this command can fail, when the folders have been prior created by another user.


## Building and running the containers

GRAPED includes numerous other GitHub repositories. The goal of GRAPED is to have a collection of docker compose files, which can easily be start from here. In order to start the containers, use the docker compose files provided in the `docker_compose` folder instead of the corresponding repositories. 

TODO: Weights of sub repos -> Saved in data or their respective repo?

## Config setup
TODO

### yolov8 and gdrnpp
Start the containers with the following command:
```bash
xhost local:docker
DATASET=ycbv CONFIG=params_sasha.yaml docker compose -f docker_compose/gdrnpp_yolov8.yml up
```
For YCB-ichores:
```bash
xhost local:docker
DATASET=ycb_ichores CONFIG=params_sasha.yaml docker compose -f docker_compose/gdrnpp_yolov8.yml up
```

To test Gdr-net:
```bash
xhost local:docker
DATASET=ycbv CONFIG=params_sasha.yaml docker compose -f docker_compose/gdrnpp_yolov8_test.yml up
```

### cnos and zs6d
Start the containers with the following command:
```bash
xhost local:docker
docker compose -f docker_compose/cnos_zs6d.yml up
```

## Contact Graspnet
Start the containers with the following command:
```bash
xhost local:docker
CONFIG=params_sasha.yaml docker compose -f docker_compose.yml up
```
TODO: Add download of models to the download_weights.sh script

