Kubecost Core Architecture Overview
===================================

Below are the major components deployed with the [Kubecost helm chart](http://docs.kubecost.com/install), excluding certain Enterprise components such a durable storage:

1. **Kubecost Cost-Analyzer Pod**  
    a. Frontend -- runs Nginx and handles routing to Kubecost backend + Prometheus/Grafana  
    b. Kubecost server -- backend for API calls  
    c. Cost-model -- provides cost allocation calculations and metrics, both reads and writes to Prometheus  
2. **Prometheus**  
    a. Prometheus server -- time-series data store for cost & health metrics  
    b. Kube-state-metrics -- provides Kubernetes API metrics, e.g. resource requests  
    c. Node-exporter -- provides node-level utilization metrics for right-sizing recommendations and cluster utilization  [Optional]  
    d. Pushgateway -- provides the ability for users to push new metrics to Prometheus [Optional]  
    e. Alertmanager -- used for custom alerts  [Optional] 
3. **Network costs** -- optional DaemonSet for collecting network metrics [learn more](https://github.com/kubecost/docs/blob/master/network-allocation.md)
4. **Grafana** -- provides supporting dashboards for Kubecost product 

Today, the core Kubecost product can be run with just components 1, 3a, and 3b.

See an overview of core components in this diagram:

![Architecture Overview](https://raw.githubusercontent.com/kubecost/docs/master/images/arch.png)


# Enterprise architecture overview

The most common implementation of durable storage in the Kubecost application application is with [Thanos](https://thanos.io/). Below is a high-level reference for required components. More information on each Thanos component can be found [here](https://thanos.io/tip/components/).

![Thanos Overview](https://raw.githubusercontent.com/kubecost/docs/main/images/thanos-architecture.png)

Edit this doc on [Github](https://github.com/kubecost/docs/blob/main/architecture.md)

<!--- {"article":"4407595922711","section":"4402829033367","permissiongroup":"1500001277122"} --->