# What’s New in Version 2.20

## **Release Content** <date>

* [Deprecation notifications](#deprecation-notifications)  

## Researchers

## Enhanced Workload Status Visibility

- Improved visibility into "failed" workloads.
For workloads with the status "Failed," the user can hover over the status to view details of why the workload hasn’t been scheduled. (requires a minimum cluster version of TBD) - Alon

- Improved visibility into "Initializing" workloads.
For workloads with the status "Initializing" the user can hover over the status to view details of why the workload is not running. (requires a minimum cluster version of TBD) - Alon

### Suspend/Resume Actions for Distributed Workloads

You can now suspend and resume distributed workloads directly from the UI. This new capability enhances control over distributed workloads, enabling greater flexibility and resource management during operations. - Alon

### Windows OS Support for CLI v2

CLI v2 now supports Windows operating systems. This update ensures a seamless experience for Windows users, enabling them to leverage the full capabilities of the CLI on their preferred platform. (requires a minimum cluster version of TBD) - Alon

### Added Idle GPU device in workloads table**

A new Idle GPU device column was added to show the allocated GPU devices that have been idle for more than 5 minutes.

### Unified Command Structure for Consistency

To align with the Run:ai UI, we’ve unified the `distributed` command into the `training` command. The `training` command now includes a new sub-command to support distributed workloads, ensuring a more consistent and streamlined user experience across both the CLI and UI. (requires a minimum cluster version of TBD) - Alon

### Pod Deletion Policy for Terminal Workloads

Administrators can now specify which pods should be deleted when a distributed workload reaches a terminal state (Completed/Failed) using cleanPodPolicy in CLI V2 and API. This enhancement provides greater control over resource cleanup and helps maintain a more organized and efficient cluster environment. - Alon

### Configurable Workload Completion with Multiple Runs
You can now define the number of runs a workload must complete to be considered finished. This enhancement improves the reliability and validity of training results by allowing multiple runs. When the number of runs is set above 1, you can also configure how many runs can be scheduled in parallel, with the parallel runs value limited to the total number of runs. This provides greater flexibility and control over workload execution and resource utilization.

### Configurable Grace Period for Workload Preemption
You can now set a grace period for workload preemption, providing a buffer time for preempted workloads to reach a safe checkpoint before being forcibly preempted. The grace period can be configured between 0 seconds and 5 minutes, enabling more controlled and seamless preemption processes.

### User applications for API Authentication

User applications are now available for API integrations with Run:AI. Each application includes client credentials which can be used to obtain an authentication token and utilize for subsequent API calls. 

TBD: add changes to Applications and deprecation notice.

## ML Engineers

Add all inference

## Run:ai Developer

### Metrics and telemetry

  Additional metrics and telemetry are available via the API. For more information, see the details below and in [Metrics API](../developer/metrics/metrics-api.md): Alon TBD

* Metrics (over time)  
    * Cluster  
        * TOTAL_GPU_NODES  
        * GPU_UTILIZATION_DISTRIBUTION  
        * UNALLOCATED_GPU  
    * Nodepool  
        * TOTAL_GPU_NODES   
        * GPU_UTILIZATION_DISTRIBUTION   
        * UNALLOCATED_GPU  
    * Workload  
        * GPU_ALLOCATION  
    * Node  
        * GPU_UTILIZATION_PER_GPU  
        * GPU_MEMORY_UTILIZATION_PER_GPU  
        * GPU_MEMORY_USAGE_BYTES_PER_GPU  
        * CPU_USAGE_CORES  
        * CPU_UTILIZATION  
        * CPU_MEMORY_USAGE_BYTES  
        * CPU_MEMORY_UTILIZATION  
* Telemetry (current time)  
    * Node  
        * ALLOCATED_GPUS  
        * TOTAL_CPU_CORES  
        * USED_CPU_CORES  
        * ALLOCATED_CPU_CORES  
        * TOTAL_GPU_MEMORY_BYTES  
        * USED_GPU_MEMORY_BYTES  
        * TOTAL_CPU_MEMORY_BYTES  
        * USED_CPU_MEMORY_BYTES  
        * ALLOCATED_CPU_MEMORY_BYTES  
        * IDLE_ALLOCATED_GPUS

## Platform Administrator

### TBD Reports
Added Reports under Analytics to allow users to access and organize large amounts of data in a clear, CSV-formatted layout. Reports enable users to monitor resource consumption, analyze trends, and make data-driven decisions to optimize their AI workloads effectively. Alon

### TBD Node pools
Enhanced DETAILS tab for node pools to present metric graphs for the following: Alon

* Node GPU allocation
* GPU Utilization Distribution
* GPU Utilization
* GPU Memory Utilization
* CPU Utilization
* CPU Memory Utilization 


## Infrastructure Administrator 

### Configuration and Installation

* Run:ai now supports Kubernetes version 1.32.
* Run:ai now supports OpenShift version 4.17.

### Custom labels for Build-In Alerts
Administrators can now add their own custom labels to the built-in alerts from Prometheus by setting [add flag] in their cluster. This update provides greater flexibility for administrators to tailor alerting configurations to their needs.

### Enhanced Configuration Flexibility for Cluster Replica Management
We’ve introduced a standardized and simplified approach to replica management for supported Run:AI services. Administrators can now use a global `replicaCount` configuration for each service, enabling high availability (HA) across the cluster. This enhancement minimizes downtime during node failures and improves overall system resilience, ensuring a more robust and reliable infrastructure.

## Deprecation notifications


### API support and endpoint deprecations
