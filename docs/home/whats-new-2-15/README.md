---
title: What's New 2.15 - December 3, 2023
summary: This article is a summary of new and improved features in the Run:ai platform.
authors:
  - Jason Novich
date: 2023-Dec-3
---

# Release Content

## Researcher

### Jobs, Workloads, Trainings, and Workspaces

*   Added support to run distributed workloads via the training view in the UI. You can configure distributed training on the following:

    * Trainings form
    * Environments form

    You can select `single` or `multi-node (distributed)` training. When configuring distributed training, you will need to select a framework from the list. Supported frameworks now include:

    * PyTorch
    * Tensorflow
    * XGBoost
    * MPI

    For _Trainings_ configuration, see [Adding trainings](../../Researcher/workloads/trainings.md#adding-trainings). See your Run:ai representative to enable this feature. For _Environments_ configuration, see [Creating an Environment](../../Researcher/workloads/assets/environments.md#adding-a-new-environment).
*   Preview the new \*Workloads\* view. \*Workloads\* is a new view for jobs that are running in the AI cluster. The \*Workloads\* view provides a more advanced UI than the previous \*Jobs\* UI. The new table format provides:

    * Improved views of the data
    * Improved filters and search
    * More information

    Use the toggle at the top of the _Jobs_ page to switch to the _Workloads_ view. For more information.
* Improved support for Kubeflow Notebooks. Run:ai now supports the scheduling of Kubeflow notebooks with fractional GPUs. Kubeflow notebooks are identified automatically and appear with a dedicated icon in the \*Jobs\* UI.
* Improved the \*Trainings\* and \*Workspaces\* forms. Now the runtime field for \*Command\* and \*Arguments\* can be edited directly in the new \*Workspace\* or \*Training\* creation form.
* Added new functionality to the Run:ai CLI that allows submitting a workload with multiple service types at the same time in a CSV style format. Both the CLI and the UI now offer the same functionality. For more information, see \[runai submit]\(../Researcher/cli-reference/runai-submit.md#-s-service-type-string).
* Improved functionality in the \`runai submit\` command so that the port for the container is specified using the \`nodeport\` flag. For more information, see \`runai submit\` \[--service-type]\(../Researcher/cli-reference/runai-submit.md#-s-service-type-string) \`nodeport\`.

### Credentials

* Improved \*Credentials\* creation. A Run:ai scope can now be added to credentials. For more information, see \[Credentials]\(../platform-admin/workloads/assets/credentials.md).

### Environments

* Added support for workload types when creating a new or editing existing environments. Select from \`single-node\` or \`multi-node (distributed)\` workloads. The environment is available only on feature forms which are relevant to the workload type selected.

### Volumes and Storage

* Added support for Ephemeral volumes in \*Workspaces\*. Ephemeral storage is temporary storage that gets wiped out and lost when the workspace is deleted. Adding Ephemeral storage to a workspace ties that storage to the lifecycle of the \*Workspace\* to which it was added. Ephemeral storage is added to the \*Workspace\* configuration form in the \*Volume\* pane. For configuration information, see \[Create a new workspace]\(../Researcher/workloads/workspaces/workspace-v2.md).

### Templates

* Added support for Run:ai a \*Scope\* in the template form. For configuration information, see \[Creating templates]\(../platform-admin/workloads/assets/templates.md#adding-a-new-workspace-template).

### Deployments

* Improvements in the New \*Deployment\* form include:
  * Support for _Tolerations_. _Tolerations_ guide the system to which node each pod can be scheduled to or evicted by matching between rules and taints defined for each Kubernetes node.
  * Support for _Multi-Process Service (MPS)_. _MPS_ is a service which allows the running of parallel processes on the same GPU, which are all run by the same userid. To enable _MPS_ support, use the toggle switch on the _Deployments_ form. !!! Note If you do not use the same userid, the processes will run in serial and could possibly degrade performance.

### Auto Delete Jobs

* Added new functionality to the UI and CLI that provides configuration options to automatically delete jobs after a specified amount of time upon completion. Auto-deletion provides more efficient use of resources and makes it easier for researchers to manage their jobs. For more configuration options in the UI, see \*Auto deletion\* (Step 9) in \[Create a new workspace]\(../Researcher/workloads/workspaces/workspace-v2.md). For more information on the CLI flag, see \[--auto-deletion-time-after-completion]\(../Researcher/cli-reference/runai-submit.md#-auto-deletion-time-after-completion).

## Run:ai Administrator

### Authorization

* Run:ai has now revised and updated the \*Role Based Access Control (RBAC)\* mechanism, expanding the scope of Kubernetes. Using the new \*RBAC\* mechanism makes it easier for administrators to manage access policies across multiple clusters and to define specific access rules over specific scopes for specific users and groups. Along with the revised \*RBAC\* mechanism, new user interface views are introduced to support the management of users, groups, and access rules. For more information, see \[Role based access control]\(../admin/authentication/roles.md).

### Policies

* During Workspaces and Training creation, assets that do not comply with policies cannot be selected. These assets are greyed out and have a button on the cards when the item does not comply with a configured policy. The button displays information about which policies are non-compliant.
* Added configuration options to \*Policies\* in order to prevent the submission of workloads that use data sources of type \`host path\`. This prevents data from being stored on the node, so that data is not lost when a node is deleted. For configuration information, see \[Prevent Data Storage on the Node]\(../platform-admin/workloads/policies/old-policies.md#prevent-data-storage-on-the-node).
* Improved flexibility when creating policies which provide the ability to allocate a \`min\` and a \`max\` value for CPU and GPU memory. For configuration information, see \[GPU and CPU memory limits]\(../platform-admin/workloads/policies/old-policies.md#gpu-and-cpu-memory-limits) in \*Configuring policies\*.

### Nodes and Node Pools

* Node pools are now enabled by default. There is no need to enable the feature in the settings.

### Quotas and Over-Quota

* Improved control over how over-quota is managed by adding the ability to block over-subscription of the quota in \*Projects\* or \*Departments\*. For more information, see \[Limit Over-Quota]\(../Researcher/scheduling/the-runai-scheduler.md#over-quota).
* Improved the scheduler fairness for departments using the \`over quota priority\` switch (in Settings). When the feature flag is disabled, over-quota weights are equal to the deserved quota and any excess resources are divided in the same proportion as the in-quota resources. For more information, see \[Over Quota Priority]\(../Researcher/scheduling/the-runai-scheduler.md#over-quota-priority).
* Added new functionality to always guarantee in-quota workloads at the expense of inter-Department fairness. Large distributed workloads from one department may preempt in-quota smaller workloads from another department. This new setting in the `RunaiConfig` file preserves in-quota workloads, even if the department quota or over-quota-fairness is not preserved. For more information, see [Scheduler Fairness](../../Researcher/scheduling/the-runai-scheduler.md#fairness-fair-resource-distribution).

## Control and Visibility

### Dashboards

* To ease the management of AI CPU and cluster resources, a new CPU focused dashboard was added for CPU based environments. The dashboards display specific information for CPU based nodes, node-pools, clusters, or tenants. These dashboards also include additional metrics that are specific to CPU based environments. This will help optimize visual information eliminating the views of empty GPU dashlets. For more information see \[CPU Dashboard]\(../platform-admin/performance/dashboard-analysis.md#cpu-dashboard).
* Improved the Consumption report interface by moving the Cost settings to the \*General\* settings menu.
* Added table to the Consumption dashboard that displays the consumption and cost per department. For more information, see \[Consumption dashboard]\(../platform-admin/performance/dashboard-analysis.md#consumption-dashboard).

### Nodes

* Improved the readability of the \*Nodes\* table to include more detailed statuses and descriptions. The added information in the table makes it easier to inspect issues that may impact resource availability in the cluster. For more information, see \[Node and Node Pool Status]\(../platform-admin/aiinitiatives/resources/node-pools.md#node-pools-table).

### UI Enhancements

* Added the ability to download a CSV file from any page that contains a table. Downloading a CSV provides a snapshot of the page's history over time, and helps with compliance tracking. All the columns that are selected (displayed) in the table are downloaded to the file.

## Installation and Configuration

### Cluster Installation and configuration

* New cluster wizard for adding and installing new clusters to your system.

### OpenShift Support

* Added support for \`restricted\` policy for \[Pod Security Admission]\(https://kubernetes.io/docs/concepts/security/kubernetes-pod-security-admission/){target=\_blank} (PSA) on OpenShift only. For more information, see \[Pod security admission]\(../admin/runai-setup/cluster-setup/
* Added the ability, in OpenShift environments, to configure cluster routes created by Run:ai instead of using the OpenShift certificate. For more information, see the table entry \[Dedicated certificate for the researcher service route]\(../admin/runai-setup/cluster-setup/customize-cluster-install.md#configurations).
