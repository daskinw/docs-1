---
title: Version 2.16
summary: This article describes new features and functionality in the version.
authors:
  - Jason Novich
date: 2023-Dec-4
---

# Version 2.16

### Release Content - January 25, 2024

#### Researcher

* Added enterprise level security for researcher tools such as Jupyter Notebooks, VSCode, or any other URL associated with the workload. Using this feature, anyone within the organization requesting access to a specific URL will be redirected to the login page to be authenticated and authorized. This results in protected URLs which cannot be reached from outside the organization. Researchers can enhance the URL privacy by using the \*Private\* toggle which means that only the researcher who created the workload can is authorized to access it. The Private toggle is available per tool that uses an external URL as a connection type and is located in the workload creation from in the UI in the environment section. This toggle sets a flag of \`isPrivate\` in the \`connections\` section of a policy for the connection type \`ExternalUrl\`. For more information, see \[Creating a new Workspace]\(../Researcher/workloads/workspaces/workspace-v2.md).

**Jobs, Workloads, and Workspaces**

* Added the capability view and edit policies directly in the project submission form. Pressing on \*Policy\* will open a window that displays the effective policy. For more information, see \[Viewing Project Policies]\(../platform-admin/aiinitiatives/org/projects.md#viewing-a-projects-policy).
*   Running machine learning workloads effectively on Kubernetes can be difficult, but Run:ai makes it easy. The new \*Workloads\* experience introduces a simpler and more efficient way to manage machine learning workloads, which will appeal to data scientists and engineers alike. The \*Workloads\* experience provides a fast, reliable, and easy to use unified interface.

    * Fast-query of data from the new workloads service.
    * Reliable data retrieval and presentation in the CLI, UI, and API.
    * Easy to use single unified view with all workload types in one place.

    For more information, see [Workloads Overview](../../platform-admin/workloads/workload-overview.md).
* Changed the workload default \*auto deletion time after completion\* value from \`Never\` to \`90 days\`. This ensures that environments will be cleaned from old data. This field is editable by default, allowing researchers the ability to change the value while submitting a workload. Using workload policies, administrators can increase, decrease, set the default value to \`never\`, or even lock access to this value so researchers can not edit it when they submit workloads.

**Assets**

* When creating an asset such as data sources, credentials, or others, the scope is limited to the cluster selected at the top of the UI.

#### Run:ai Administrator

* Added the capability for administrators to configure messages to users when they log into the platform. Messages are configured using the \*Message Editor\* screen. For more information, see \[Administrator Messages]\(../admin//config/admin-messages.md).

**Monitoring and Analytics**

*   Added to the dashboard updated GPU and CPU resource availability.

    ```
    * Added a chart displaying the number of free GPUs per node. Free GPU are GPUs that have not been allocated to a workload.
    * Added a dashlet that displays the total vs. ready resources for GPUs and CPUs. The dashlet indicates how many total nodes are in the platform, and how many are available. 
    ```
*   Added additional columns to the consumption report for both \*Projects\* and \*Departments\* tables. The new columns are:

    ```
    * GPU Idle allocated hours&mdash;the portion of time the GPUs spend idle from the total allocation hours.
    * CPU usage hours&mdash;the actual usage time of CPU.
    * Memory usage time&mdash;the actual usage time of CPU memory.
    ```

    For more information, see [Consumption Dashboard](../../platform-admin/performance/dashboard-analysis.md#consumption-dashboard).

**Authentication and Authorization**

* SSO users who have logged into the system will now be visible in the \*Users\* table. In addition, added a column to the \*Users\* table for the type of user that was created (Local or SSO). For more information, see \[Adding, Updating, and Deleting Users]\(../admin/authentication/users.md).

**Policies**

* Added new \*Policy Manager. The new \*Policy Manager\* provides administrators the ability to impose restrictions and default values on system resources. The new \*Policy Manager\* provides a YAML editor for the configuration of the policies. Administrators can easily add both \*Workspace\* or \*Training\* policies. The editor makes it easy to see the configuration that has been applied and provides a quick and easy method to edit the policies. The new \*Policy Editor\* brings other important policy features such as the ability to see non-compliant resources in workloads. For more information, see \[Policies]\(../platform-admin/workloads/policies/workspaces-policy.md#viewing-a-policy).
* Added a new policy manager. Enabling the \*New Policy Manager\* provides new tools to discover how resources are not compliant. Non-compliant resources and will appear greyed out and cannot be selected. To see how a resource is not compliant, press on the clipboard icon in the upper right hand corner of the resource. Policies can also be applied to specific scopes within the Run:ai platform. For more information, see \[Viewing Project Policies]\(../platform-admin/aiinitiatives/org/projects.md#adding-a-new-project).

#### Control and Visibility

* Improved the clarity of the status column in the \*Clusters\* view. Now users have more insight about the actual status of Run:ai on the cluster. Users can now see extended details about the state of the Run:ai installation and services on the cluster, and its connectivity state. For more information, see \[Cluster status]\(../admin/runai-setup/cluster-setup/cluster-install.md#cluster-status).

### Deprecation Notifications

Deprecation notifications allow you to plan for future changes in the Run:ai Platform. Deprecated features will be available for **two** versions ahead of the notification. For questions, see your Run:ai representative.

#### Project migration

* Run:ai will be deprecating the migration of projects between departments. This affects:
  * API—the `departmentId` field will be marked as deprecated in the`put` endpoint in the `projects` category.
  * User Interface—there will no longer be an option to:
    * migrate projects to another department, when deleting departments.
    * change departments, when editing a project.

#### API deprecations

**Removed APIs and API fields (completed deprecation)**

The following list of API endpoints and fields that have completed their deprecation process and therefore will be changed as follows:

| Endpoint                | Change                                                              |
| ----------------------- | ------------------------------------------------------------------- |
| /v1/k8s/clusters        | The endpoint was removed and is replaced by /api/v1/clusters        |
| /v1/k8s/clusters/{uuid} | The endpoint was removed and is replaced by /api/v1/clusters/{uuid} |

Run:ai does not recommend using API endpoints and fields marked as deprecated and will not add functionality to them. Once an API endpoint or field is marked as deprecated, Run:ai will stop supporting it after 2 major releases for self-hosted deployments, and after 6 months for SaaS deployments.

For a full explanation of the API Deprecation policy, see the [Run:ai API Policy](../../developer/admin-rest-api/overview.md#api-lifecycle-and-deprecation)
