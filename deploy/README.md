## Tools

* [StackOverflow]([[https://www.pachyderm.com](https://stackoverflow.com/questions/55901375/is-this-possible-to-schedule-cronjob-to-execute-on-each-of-kubernetes-nodes)]())
  * Using the parallelism to run multiple Job PODs, with topologySpreadConstraints to spread/schedule the PODs on all the nodes.
* [Kubebuilder]([https://www.dvc.org](https://github.com/kubernetes-sigs/kubebuilder#kubebuilder))
  * An example of using kubebuilder 

```
kubectl explain --api-version="batch/v1beta1" cronjobs.spec
```

