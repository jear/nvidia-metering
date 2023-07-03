# nvidia-metering
```
# Accounting for each worker node
sudo nvidia-smi -am 1
Enabled Accounting Mode for GPU 00000000:13:00.0.
Enabled Accounting Mode for GPU 00000000:37:00.0.
Enabled Accounting Mode for GPU 00000000:D8:00.0.
All done.

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
