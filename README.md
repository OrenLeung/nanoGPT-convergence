## nvidia
```
sudo docker run --rm -it --gpus all --ipc=host --shm-size=192G -v $pwd:/workspace nvcr.io/nvidia/pytorch:24.12-py3
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
