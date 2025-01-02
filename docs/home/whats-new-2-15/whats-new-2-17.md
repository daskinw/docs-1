---
title: Version 2.17
summary: This article describes new features and functionality in the version.
authors:
  - Jason Novich
date: 2024-Apr-14
---

# Version 2.17

### Release Content - April 14, 2024

* [Deprecation notifications](whats-new-2-17.md#deprecation-notifications)
* [Breaking changes](whats-new-2-17.md#breaking-changes)

#### Researcher

**Scheduler**

* Added functionality to configure over provisioning ratios for node pools running any kind of workload. Over provisioning assumes that workloads are either under utilizing or intermittently using GPUs. This indicates that the real utilization is lower than the actual GPU allocation requested. Over provisioning allows the administrator to condense more workloads on a single GPU than what the workload required. For more information, see \[Optimize performance with Node Level Scheduler]\(../Researcher/scheduling/node-level-scheduler.md).
* Added the _GPU Resource Optimization_ feature to the UI. Now you can enable and configure _GPU Portion (Fraction) limit_ and _GPU Memory Limit_ from the UI. For more information, see [Compute resources UI with Dynamic Fractions](../../Researcher/scheduling/dynamic-gpu-fractions.md#compute-resources-ui-with-dynamic-fractions-support).
* Added the ability to set Run:ai as the default scheduler for any project or namespace. This provides the administrator the ability to ensure that all workloads in a project or namespace are scheduled using the Run:ai scheduler. For more information, see \[Setting Run:ai as default scheduler]\(../platform-admin/aiinitiatives/org/projects.md).

**Jobs, Workloads, and Workspaces**

* Added to the workload details view, the ability to filter by pod. You can now filter metrics and logs per pod or all the pods. Also, the \*Workloads\* table now has additional columns including connections and preemtability adding more at a glance information about the workload. In addition, using the \*Copy & edit\* button, you can submit a new workload via CLI based on the selected workload. For more information, see \[Workloads]\(../platform-admin/workloads/workload-overview.md#workloads-view).
* Added \*Inference\* to workload types. \*Inference\* workloads can now be created and managed from the unified \*Workloads\* table. The \*Deployments\* workload type has been deprecated, and replaced with \*Inference\* workloads which are submitted using the workload form. For more information, see \[Inference]\(../Researcher/workloads/inference-overview.md) and for submitting an \*Inference\* workload, see \[Submitting workloads]\(../platform-admin/workloads/overviews/managing-workloads.md).
*   Added functionality that supports a single workloads submission selection. Now you can submit workloads by pressing \*+ New workloads\* in the \*Workloads\* table. You can submit the following workloads from this table:

    ```
    * Workspace
    * Training
    * Inference
    ```

    This improvement phases out the previous version's _Workspace_ and _Jobs_ tables. The _Jobs_ table and submission forms have been deprecated and can be reactivated. To reenable the _Jobs_ table and forms, press _Tools & settings_, then _General_, then _Workloads_, and then Toggle the _Jobs view_ and the _Jobs submission_ buttons. For more information, see [Submitting workloads](../../platform-admin/workloads/overviews/managing-workloads.md).
* Added the ability to configure a Kubernetes readiness probe. The readiness probe detects resources and workloads that are ready to receive traffic.

**Assets**

* Added the capability to use a ConfigMap as a data source. The ability to use a ConfigMap as a data source can be configured in the \*Data sources\* UI, the CLI, and as part of a policy. For more information, see \[Setup a ConfigMap as a data source]\(../Researcher/workloads/assets/datasources.md#configmap), \[Setup a ConfigMap as a volume using the CLI]\(../Researcher/cli-reference/runai-submit.md#-configmap-volume-namepath).
* Added a \*Status\* column to the \*Credentials\* table, and the \*Data sources\* table. The \*Status\* column displays the state of the resource and provides troubleshooting information about that asset. For more information, see the \[Credentials table]\(../platform-admin/workloads/assets/credentials.md#credentials-table) and the \[Data sources table]\(../Researcher/workloads/assets/datasources.md#data-sources-table).
* Added functionality for asset creation that validates the asset based on version compatibility of the cluster or the control plane within a specific scope. At time of asset creation, invalid scopes will appear greyed out and will show a pop-up with the reason for the invalidation. This improvement is designed to increase the confidence that an asset is created properly and successfully.

#### Run:ai Administrator

**Configuration and Administration**

*   Introducing a new \*Tools & Settings\* menu. The new \*Tools & Settings\* menu provides a streamlined UI for administrators to configure the Run:ai environment. The new UI is divided into categories that easily identify the areas where the administrator can change settings. The new categories include:

    * Analytics—features related to analytics and metrics.
    * Resources—features related to resource configuration and allocation.
    * Workloads—features related to configuration and submission of workloads.
    * Security—features related to configuration of SSO (Single Sign On).
    * Notifications—used for system notifications.
    * Cluster authentication—snippets related to Researcher authentication.

    Some features are now labeled either _Experimental_ or _Legacy_. _Experimental_ features are new features in the environment, that may have certain instabilities and may not perform as expected. _Legacy_ features are features that are in the process of being deprecated, and may be removed in future versions.

**Clusters**

* Added new columns to the \*Clusters\* table to show Kubernetes distribution and version. This helps administrators view potential compatibility issues that may arise.
*   Improved the location of the cluster filter. The cluster filter has been relocated to filter bar and the drop down cluster filter in the header of the page has been removed. This improvement creates the following:

    * Filter assets by cluster in the following tables:
      * Data sources
      * Environments
      * Computer resources
      * Templates
      * Credentials
    * Creating a new asset, will automatically display only the scope of the selected cluster.
    * Prevention of account (top most level in the _Scope_) from being selected when creating assets.
    * Enforcement a cluster specific scope. This increases the confidence that an asset is created properly and successfully.

    !!! Note This feature is only applicable if the all the clusters are version 2.17 and above.

**Monitoring and Analytics**

* Improved GPU Overview dashboard. This improvement provides rich and extensive GPU allocation and performance data and now has interactive tiles that provide direct links to the \*Nodes\*, \*Workloads\*, and \*Departments\* tables. Hover over tiles with graphs to show rich data in the selected time frame filter. Tiles with graphs can be downloaded as CSV files. The new dashboard is enabled by default. Use the \*Go back to legacy view\* to return to the previous dashboard style. For more information, see \[Dashboard analysis]\(../platform-admin/performance/dashboard-analysis.md).
*   Updated the knative and autoscaler metrics. Run:ai currently supports the following metrics:

    * Throughput
    * Concurrency

    For more information, see [Autoscaling metrics](../../Researcher/workloads/inference-overview.md#autoscaling).
* Improved availability of metrics by using Run:ai APIs. Using the API endpoints is now the preferred method to retrieve metrics for use in any application. For more information, see \[Metrics]\(../developer/metrics/metrics.md#changed-metrics-and-api-mapping).

**Authentication and Authorization**

* Added new functionality to SAML 2.0 identity provider configuration in the \*Security\* category of the \*General\* settings. The added functionality assists with troubleshooting SSO configuration and authentication issues that may arise. Now administrators now have the ability to:
  * View and edit the identity provider settings for SAML 2.0
  * Upload or download the SAML 2.0 identity provider metadata XML file.

For more information, see [SSO UI configuration](../../admin/authentication/authentication-overview.md#single-sign-on-sso).

### Deprecation Notifications

Deprecation notifications allow you to plan for future changes in the Run:ai Platform.

#### Feature deprecations

Deprecated features will be available for **two** versions ahead of the notification. For questions, see your Run:ai representative. The following features have been marked for deprecation:

* Jobs—the _Jobs_ feature (submission form and view) has been moved to the category of _Legacy_. To enable them, go to _Tools & Settings_, _General_, open the _Workloads_ pane, and then toggle the _Jobs view_ and _Job submission_ switch to the enabled position.
* Deployments—the _Deployments_ feature has been removed. It has been replaced by _Inference_ workloads. For more information, see [Jobs, Workloads, and Workspaces](whats-new-2-17.md#jobs-workloads-and-workspaces) above.
* Workspaces view—the _Workspaces_ menu has been removed. You can now submit a _Workspace_ workload using the _+ New workload_ form from the _Workloads_ table.

#### API support and endpoint deprecations

The endpoints and parameters specified in the API reference are the ones that are officially supported by Run:ai. For more information about Run:ai's API support policy and deprecation process, see [Developer overview](../../developer/overview-developer.md#runai-rest-api).

**Deprecated APIs and API fields**

The following list of API endpoints and fields that have been marked for deprecation:

**Jobs and Pods API**

| Deprecated                                | Replacement                         |
| ----------------------------------------- | ----------------------------------- |
| /v1/k8s/clusters/{uuid}/jobs              | /api/v1/workloads                   |
| /v1/k8s/clusters/{uuid}/jobs/count        | /api/v1/workloads/count             |
| /v1/k8s/clusters/{uuid}/jobs/{jobId}/pods | /api/v1/workloads/{workloadId}/pods |
| /v1/k8s/clusters/{uuid}/pods              | /api/v1/workloads/pods              |

**Clusters API**

| Deprecated                             | Replacement                            |
| -------------------------------------- | -------------------------------------- |
| /v1/k8s/clusters/{clusterUuid}/metrics | /api/v1/clusters/{clusterUuid}/metrics |

**Authorization and Authentication API**

| Deprecated                                                              | Replacement                        |
| ----------------------------------------------------------------------- | ---------------------------------- |
| /v1/k8s/auth/token/exchange                                             | /api/v1/token                      |
| /v1/k8s/auth/oauth/tokens/refresh                                       | /api/v1/token                      |
| /v1/k8s/auth/oauth/apptoken                                             | /api/v1/token                      |
| /v1/k8s/users/roles                                                     | /api/v1/authorization/roles        |
| /v1/k8s/users                                                           | /api/v1/users                      |
| /v1/k8s/users/{userId}                                                  | /api/v1/users/{userId}             |
| /v1/k8s/users/{userId}/roles                                            | /api/v1/authorization/access-rules |
| /v1/k8s/apps                                                            | /api/v1/apps                       |
| /v1/k8s/apps/{clientId}                                                 | /api/v1/apps/{appId}               |
| /v1/k8s/groups                                                          | /api/v1/authorization/access-rules |
| /v1/k8s/groups/{groupName}                                              | /api/v1/authorization/access-rules |
| /v1/k8s/clusters/{clusterId}/departments/{department-id}/access-control | /api/v1/authorization/access-rules |
| /api/v1/authorization/access-rules - `subjectIdFilter` field            | Use `filterBy` / `sortBy` fields   |
| /api/v1/authorization/access-rules - `scopeType` field                  | Use `filterBy` / `sortBy` fields   |
| /api/v1/authorization/access-rules - `roleId` field                     | Use `filterBy` / `sortBy` fields   |

**Projects API**

| Deprecated                                                         | Replacement                        |
| ------------------------------------------------------------------ | ---------------------------------- |
| /v1/k8s/clusters/{clusterId}/projects - `permissions` field        | /api/v1/authorization/access-rules |
| /v1/k8s/clusters/{clusterId}/projects - `resources` field          | Use `nodePoolResources` field      |
| /v1/k8s/clusters/{clusterId}/projects - `deservedGpus` field       | Use `nodePoolResources` field      |
| /v1/k8s/clusters/{clusterId}/projects - `maxAllowedGpus` field     | Use `nodePoolResources` field      |
| /v1/k8s/clusters/{clusterId}/projects - `gpuOverQuotaWeight` field | Use `nodePoolResources` field      |

**Departments API**

| Deprecated                                                        | Replacement                   |
| ----------------------------------------------------------------- | ----------------------------- |
| /v1/k8s/clusters/{clusterId}/departments - `resources` field      | Use `nodePoolResources` field |
| /v1/k8s/clusters/{clusterId}/departments - `deservedGpus` field   | Use `nodePoolResources` field |
| /v1/k8s/clusters/{clusterId}/departments - `allowOverQuota` field | Use `nodePoolResources` field |
| /v1/k8s/clusters/{clusterId}/departments - `maxAllowedGpus` field | Use `nodePoolResources` field |

**Policy API**

| Deprecated               | Replacement               |
| ------------------------ | ------------------------- |
| /api/v1/policy/workspace | /api/v2/policy/workspaces |
| /api/v1/policy/training  | /api/v2/policy/trainings  |

**Logo API**

| Deprecated                     | Replacement  |
| ------------------------------ | ------------ |
| /v1/k8s/tenant/{tenantId}/logo | /api/v1/logo |

**Removed APIs and API fields (completed deprecation)**

The following list of API endpoints and fields that have completed their deprecation process and therefore will be changed as follows:

**Assets API**

| Endpoint              | Change                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /api/v1/asset/compute | <p><code>gpuRequest</code> field was removed and is replaced by the following fields:<br>* <code>gpuDevicesRequest</code> (New and mandatory)<br>* <code>gpuRequestType</code> (New and mandatory if <code>gpuDevicesRequest=1</code> otherwise optional for values 0 or greater than 1)<br>* <code>gpuPortion</code> was changed to <code>gpuPortionRequest</code> and accepts values between 0 and 1 (for example 0.75)<br>* <code>gpuPortionLimit</code> (New and optional)<br>* <code>gpuMemory</code> was changed to <code>gpuMemoryRequest</code><br>* <code>gpuMemoryLimit</code> (New and optional)</p> |

#### Metrics deprecations

The following metrics are deprecated and replaced by API endpoints. For details about the replacement APIs, see [Changed Metrics](../../developer/metrics/metrics.md#changed-metrics-and-api-mapping):

| Metric                                                  |
| ------------------------------------------------------- |
| runai\_active\_job\_cpu\_requested\_cores               |
| runai\_active\_job\_memory\_requested\_bytes            |
| runai\_cluster\_cpu\_utilization                        |
| runai\_cluster\_memory\_utilization                     |
| runai\_gpu\_utilization\_per\_pod\_per\_gpu             |
| runai\_gpu\_utilization\_per\_workload                  |
| runai\_job\_requested\_gpu\_memory                      |
| runai\_gpu\_memory\_used\_mebibytes\_per\_workload      |
| runai\_gpu\_memory\_used\_mebibytes\_per\_pod\_per\_gpu |
| runai\_active\_job\_cpu\_limits                         |
| runai\_job\_cpu\_usage                                  |
| runai\_active\_job\_memory\_limits                      |
| runai\_job\_memory\_used\_bytes                         |

Run:ai does not recommend using API endpoints and fields marked as deprecated and will not add functionality to them. Once an API endpoint or field is marked as deprecated, Run:ai will stop supporting it after 2 major releases for self-hosted deployments, and after 6 months for SaaS deployments.

For a full explanation of the API Deprecation policy, see the [Run:ai API Policy](../../developer/admin-rest-api/overview.md#api-lifecycle-and-deprecation)

### Breaking changes

Breaking changes notifications allow you to plan around potential changes that may interfere your current workflow when interfacing with the Run:ai Platform.

#### Metrics

Be aware that some names of metrics have been changed. For more information, see [Changed Metrics](../../developer/metrics/metrics.md#changed-metrics-and-api-mapping).
