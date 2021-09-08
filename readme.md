# DL HPE Acceleration on MultiGPU #
we use docker container which is a kind of virtualization because of 5G MEC environment.
## Prerequisite ##
docker, nvidia-docker, python, aioRTC, pytorch, etc.

## Docker Run Commandline (mandatory arguments) ##
```docker run --gpus all -it --net host --ipc=host dlckdgk/kaist:vrar-LATEST /bin/bash```
