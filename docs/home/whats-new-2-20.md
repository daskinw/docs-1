# What’s New in Version 2.20

## **Release Content** <date>

* [Deprecation notifications](#deprecation-notifications)  

## Researchers

## Enhanced workload status visibility

- Users can now gain better insights into workloads with a "Failed" and status. By hovering over the status, you can view details of why the workload has not been scheduled. (requires a minimum cluster version of TBD) - Alon

- Users can now gain better insights into workloads with a "Initialization" status. By hovering over the status, you can view details of why the workload is not running. (requires a minimum cluster version of TBD) - Alon

### Stop/Run actions for distributed workloads

You can now stop and run distributed workloads directly from the UI. This new capability enhances control over distributed workloads, enabling greater flexibility and resource management. (requires a minimum cluster version of TBD) - Alon

### Windows OS support for CLI v2

CLI v2 now supports Windows operating systems, enabling you to leverage the full capabilities of the CLI. (requires a minimum cluster version of TBD) - Alon

### Visibility into idle GPU devices

Added idle GPU device column to the Workloads table. The column displays allocated GPU devices that have been idle for more than 5 minutes, offering enhanced visibility into resource utilization and supporting more efficient workload management. Alon

### Unified command structure for consistency

To align with the Run:ai UI, we’ve unified the `distributed` command into the `training` command. The `training` command now includes a new sub-command to support distributed workloads, ensuring a more consistent and streamlined user experience across both the CLI and UI. (requires a minimum cluster version of TBD) - Alon

### Improved command line interface autocompletion

CLI V2 now autocompletes nouns such as project names and workload names for better data consistency with the UI, auto-upgrades, and interactive mode. Alon (was in 2.19)

### Pod deletion policy for terminal workloads

Administrators can now specify which pods should be deleted when a distributed workload reaches a terminal state (completed/failed) using cleanPodPolicy in CLI V2 and API. This enhancement provides greater control over resource cleanup and helps maintain a more organized and efficient cluster environment. - Alon

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

  Additional metrics and telemetry are available via the API. For more details, see [Metrics API](../developer/metrics/metrics-api.md): Alon 

* Metrics (over time)  
    * Project  
        * GPU_QUOTA 
        * CPU_QUOTA_MILLICORES
        * CPU_MEMORY_QUOTA_MB
        * GPU_ALLOCATION
        * CPU_ALLOCATION_MILLICORES
        * CPU_MEMORY_ALLOCATION_MB 
    * Department  
        * GPU_QUOTA 
        * CPU_QUOTA_MILLICORES
        * CPU_MEMORY_QUOTA_MB
        * GPU_ALLOCATION
        * CPU_ALLOCATION_MILLICORES
        * CPU_MEMORY_ALLOCATION_MB 

* Telemetry (current time)  
    * Project  
        * GPU_QUOTA 
        * CPU_QUOTA 
        * MEMORY_QUOTA
        * GPU_ALLOCATION
        * CPU_ALLOCATION
        * MEMORY_ALLOCATION
        * GPU_ALLOCATION_NON_PREEMPTIBLE
        * CPU_ALLOCATION_NON_PREEMPTIBLE
        * MEMORY_ALLOCATION_NON_PREEMPTIBLE 
    * Department    
        * GPU_QUOTA 
        * CPU_QUOTA 
        * MEMORY_QUOTA
        * GPU_ALLOCATION
        * CPU_ALLOCATION
        * MEMORY_ALLOCATION
        * GPU_ALLOCATION_NON_PREEMPTIBLE
        * CPU_ALLOCATION_NON_PREEMPTIBLE
        * MEMORY_ALLOCATION_NON_PREEMPTIBLE 

## Platform Administrator

### New Reports feature for Analytics

The new Reports enables users to generate and organize large data in a structured, CSV-formatted layout. With this feature, users can monitor resource consumption, identify trends, and make informed decisions to optimize their AI workloads with greater efficiency. Alon

### Enhanced metrics and details for node pools
The DETAILS tab for node pools has been upgraded to include enhanced metric graphs, providing deeper insights into resource utilization. These enhancements allow users to better monitor and manage resource usage within their node pools, optimizing performance and efficiency. The following metrics are now available: Alon

* Node GPU Allocation: View how GPUs are distributed across nodes. 
* GPU Utilization Distribution: Understand the spread of GPU usage across workloads. 
* GPU Utilization: Monitor overall GPU usage for better workload optimization. 
* GPU Memory Utilization: Track memory usage on GPUs to prevent bottlenecks. 
* CPU Utilization: Gain visibility into CPU resource usage across nodes. 
* CPU Memory Utilization: Analyze memory consumption for efficient node management. 



## Infrastructure Administrator 

### Configuration and Installation

* Run:ai now supports Kubernetes version 1.32.
* Run:ai now supports OpenShift version 4.17.

### Custom labels for Build-In Alerts
Administrators can now add their own custom labels to the built-in alerts from Prometheus by setting [add flag] in their cluster. This update provides greater flexibility for administrators to tailor alerting configurations to their needs.

### Enhanced Configuration Flexibility for Cluster Replica Management
We’ve introduced a standardized and simplified approach to replica management for supported Run:AI services. Administrators can now use a global `replicaCount` configuration for each service, enabling high availability (HA) across the cluster. This enhancement minimizes downtime during node failures and improves overall system resilience, ensuring a more robust and reliable infrastructure.

## Deprecation notifications

Alon

### API support and endpoint deprecations

Alon
