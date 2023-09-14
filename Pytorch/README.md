# An example of Running PyTorch `DistributedDataParallel` Framework on Bridges-2

Here we show an example of running PyTorch `DistributedDataParallel` data parallelism framework.
This examples that train ResNet50 models with either Imagenet/Imagenet-mini dataset or mock images generated with random pixels.
A slurm script is included to show how to set up the environment and structure the slurm script  for running on Bridges-2 GPU nodes.

## Interactive Session
Here we give example commands of running this example with 4 GPUs (node type not specified) with the GPU-shared partition for an hour:

#### With `singularity exec`
```bash
interact --partition GPU-shared --gres=gpu:v100:4
singularity exec --nv /ocean/containers/ngc/pytorch/pytorch_latest.sif torchrun --nnodes=1 --nproc_per_nod=4 pytorch_ddp.py
```

#### With `singularity shell`
```bash
interact --partition GPU-shared --gres=gpu:v100:4
singularity shell --nv /ocean/containers/ngc/pytorch/pytorch_latest.sif
torchrun --nnodes=1 --nproc_per_nod=4 pytorch_ddp.py
```

#### With AI module
```bash
interact --partition GPU-shared --gres=gpu:v100:4
module load AI/pytorch_23.02-1.13.1-py3 
torchrun --nnodes=1 --nproc_per_nod=4 pytorch_ddp.py
```

## Batch Mode
After modifying the script to include the correct allocation account and working directory, submit the batch job by typing:
```bash
sbatch pytorch_ddp_single_node.sbatch
```



