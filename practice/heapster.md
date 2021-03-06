# Heapster

Heapster作为kubernetes安装过程中默认安装的一个插件，见[安装heapster插件](practice/heapster-addon-installation.md)。这对于集群监控十分有用，同时在[Horizontal Pod Autoscaling](../concepts/horizontal-pod-autoscaling.md)中也用到了，HPA将Heapster作为`Resource Metrics API`，向其获取metric，做法是在`kube-controller-manager` 中配置`--api-server`指向[kube-aggregator](https://github.com/kubernetes/kube-aggregator)，也可以使用heapster来实现，通过在启动heapster的时候指定`--api-server=true`。

Heapster可以收集Node节点上的cAdvisor数据，还可以按照kubernetes的资源类型来集合资源，比如Pod、Namespace域，可以分别获取它们的CPU、内存、网络和磁盘的metric。默认的metric数据聚合时间间隔是1分钟。