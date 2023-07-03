## Tools

* [StackOverflow]
  * Using the parallelism to run multiple Job PODs, with topologySpreadConstraints to spread/schedule the PODs on all the nodes. (https://stackoverflow.com/questions/55901375/is-this-possible-to-schedule-cronjob-to-execute-on-each-of-kubernetes-nodes)
* [Kubebuilder]
  * An example of using kubebuilder (https://github.com/kubernetes-sigs/kubebuilder#kubebuilder)

```
kubectl explain --api-version="batch/v1beta1" cronjobs.spec
kubectl explain --api-version="batch/v1" cronjobs.spec

```
