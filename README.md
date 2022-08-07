# Docker GPU check

## Docker based

`docker run --gpus all -it --rm tensorflow/tensorflow:latest-gpu    python -c "import tensorflow as tf;
import time;
assert tf.test.is_gpu_available(cuda_only=False, min_cuda_compute_capability=None), 'GPU not found';
start = time.time();
print(tf.reduce_sum(tf.random.normal([10, 1000, 1000])));
end = time.time();
print('Took', end - start, 'seconds');
assert end - start < 0.2, 'Took more than 0.2 sec, typical max time is 0.15 sec';"`

## Compose based

`docker compose up`

## Nvidia smi check

`docker run -it --runtime=nvidia nvidia/cuda:11.4.0-base-ubuntu20.04 nvidia-smi`

## How to fix this?

If above checks are failing, you may follow steps in tensorflow docker page to install the required packages,
https://www.tensorflow.org/install/docker


