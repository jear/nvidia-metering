# nvidia-metering
```
export NVIDIA_CUDA_IMG="nvidia/cuda"
export NVIDIA_CUDA_IMG_TAG=11.6.2-base-ubuntu20.04
export NVIDIA_QUERY_GPU="timestamp,serial,name,mig.mode.current,utilization.gpu,memory.total,memory.used,utilization.memory"
export NVIDIA_FORMAT="csv,nounits,noheader"

docker run --rm --runtime=nvidia --gpus all ${NVIDIA_CUDA_IMG}:${NVIDIA_CUDA_IMG_TAG} nvidia-smi --query-gpu=${NVIDIA_QUERY_GPU} --format=${NVIDIA_FORMAT}
2023/07/03 10:33:55.204, 1562220007789, Tesla T4, [N/A], 0, 15360, 6, 0

```
