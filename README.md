## nvidia
```
sudo docker run --rm -it --gpus all --ipc=host --shm-size=192G -v $pwd:/workspace nvcr.io/nvidia/pytorch:24.12-py3
```

## amd
```
docker run -it --device /dev/dri --device /dev/kfd --network host --ipc host --group-add video --cap-add SYS_PTRACE --security-opt seccomp=unconfined --privileged -v .:/workspace/reprod --name training-dev-env rocm/training:20250116 /bin/bash
```

## install

```
pip install torch numpy transformers datasets tiktoken wandb tqdm
```



## download data
```sh
python data/openwebtext/prepare.py
```


## run

```sh
torchrun --standalone --nproc_per_node=8 train.py config/train_gpt2.py
```
