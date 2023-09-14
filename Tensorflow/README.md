# An example of Running Tensorflow `tf.distributed.MirroredStrategy` Framework on Bridges-2

Here we show an example of running Tensorflow `tf.distributed.MirroredStrategy` data parallelism framework.
This examples that train ResNet50 models with either Imagenet/Imagenet-mini dataset or mock images generated with random pixels.
A slurm script is included to show how to set up the environment and structure the slurm script  for running on Bridges-2 GPU nodes.

## Interactive Session
Here we give example commands of running this example with 4 GPUs (node type not specified) with the GPU-shared partition for an hour:

#### With `singularity exec`
```bash
interact --partition GPU-shared --gres=gpu:v100:4
singularity exec --nv /ocean/containers/ngc/tensorflow/tensorflow_latest.sif python tensorflow_dist.py
```

#### With `singularity shell`
```bash
interact --partition GPU-shared --gres=gpu:v100:4
singularity shell --nv /ocean/containers/ngc/tensorflow/tensorflow_latest.sif
python tensorflow_dist.py
```

#### With AI module
```bash
interact --partition GPU-shared --gres=gpu:v100:4
module load AI/tensorflow_23.02-2.10.0-py3  
python tensorflow_dist.py
```

## Batch Mode
After modifying the script to include the correct allocation account and working directory, submit the batch job by typing:
```bash
sbatch tf_single_node.sbatch
```
