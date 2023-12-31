# Capacity planning
* OpsRamp
  * https://docs.opsramp.com/integrations/gpu-monitoring/nvidia-gpu-monitor/
* Datadog
  * https://docs.datadoghq.com/integrations/nvml/
  * https://blog.searce.com/nvidia-a100-migs-gpu-monitoring-using-datadog-7c3d2378184f
* [krossboard.app]  CNCF  ???
  *  https://krossboard.app/
  *  https://github.com/2-alchemists/krossboard-kubernetes-operator
* [Opencost] CNCF ->  https://landscape.cncf.io/card-mode?category=continuous-optimization&grouping=category
  * https://www.opencost.io/
  * https://github.com/opencost/opencost
* [Kubecost]  CNCF ->  https://landscape.cncf.io/card-mode?category=continuous-optimization&grouping=category
  * Made from Opencost : https://docs.kubecost.com/architecture/opencost-product-comparison
  * https://docs.kubecost.com/architecture/user-metrics
  * https://github.com/kubecost/cost-analyzer-helm-chart
* [kube-opex-analytics]
  * https://github.com/rchakode/kube-opex-analytics
* [run.ai]
  * https://www.run.ai/gpu-optimization
* [Others]
  * https://github.com/dastergon/awesome-sre#capacity-planning

# nvidia GPU operator install
* https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/getting-started.html#option-2-auto-upgrade-crd-using-helm-hook
```
helm repo add nvidia https://helm.ngc.nvidia.com/nvidia    && helm repo update
helm upgrade --install gpu-operator nvidia/gpu-operator -n gpu-operator --create-namespace --set operator.upgradeCRD=true --disable-openapi-validation 
```

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


