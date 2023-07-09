# Capacity planning
* [krossboard.app]
  *  https://krossboard.app/
  *  https://github.com/2-alchemists/krossboard-kubernetes-operator
* [Opencost]
  * https://www.opencost.io/
  * https://github.com/opencost/opencost
* [Kubecost]
  * https://docs.kubecost.com/architecture/user-metrics
  * https://github.com/kubecost/cost-analyzer-helm-chart
* [run.ai]
  * https://www.run.ai/gpu-optimization
* [Others]
  * https://github.com/dastergon/awesome-sre#capacity-planning


# nvidia-metering ( nvidia-smi only )
```
export NVIDIA_CUDA_IMG="nvidia/cuda" 
export NVIDIA_CUDA_IMG_TAG="11.6.2-base-ubuntu20.04"

export NVIDIA_QUERY_GPU="timestamp,serial,name,mig.mode.current,utilization.gpu,memory.total,memory.used,utilization.memory" 
export NVIDIA_FORMAT="csv,nounits,noheader" 

export NVIDIA_SMI_QUERY_OUTPUT="$(nvidia-smi --query-gpu=${NVIDIA_QUERY_GPU} --format=${NVIDIA_FORMAT})" 
```

# Accounting for each worker node
```
sudo nvidia-smi -am 1
Enabled Accounting Mode for GPU 00000000:13:00.0.
Enabled Accounting Mode for GPU 00000000:37:00.0.
Enabled Accounting Mode for GPU 00000000:D8:00.0.
All done.
```

```
# From nvidia-smi doc
--query-compute-apps=
 List of currently active compute processes. Call --help-query-com-
 pute-apps for more info.
 --query-accounted-apps=
 List of accounted compute processes. Call --help-query-accounted-apps
 for more info.
 --query-retired-pages=
 List of GPU device memory pages that have been retired. Call
 --help-query-retired-pages for more info.

```

```
export QUERY_ACCOUNTED_APPS="pid,gpu_serial,gpu_name,gpu_utilization,time"

nvidia-smi  --query-accounted-apps=${QUERY_ACCOUNTED_APPS} --format=${FORMAT}
```

```
nvidia-smi -q -d ACCOUNTING

==============NVSMI LOG==============

Timestamp                                 : Mon Jul  3 10:50:43 2023
Driver Version                            : 525.60.13
CUDA Version                              : 12.0

Attached GPUs                             : 3
GPU 00000000:13:00.0
    Accounting Mode                       : Enabled
    Accounting Mode Buffer Size           : 4000
    Accounted Processes                   : None

GPU 00000000:37:00.0
    Accounting Mode                       : Enabled
    Accounting Mode Buffer Size           : 4000
    Accounted Processes                   : None

GPU 00000000:D8:00.0
    Accounting Mode                       : Enabled
    Accounting Mode Buffer Size           : 4000
    Accounted Processes                   : None


```


