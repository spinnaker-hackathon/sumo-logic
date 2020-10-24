# Sumo Logic

Sumo Logic is collaborating with the Spinnaker community to add out-of-the-box support for Spinnaker to Sumo Logic's Software Development Optimization (SDO) Solution. This new solution developed by Sumo Logic allows organizations to benchmark and optimize their software development and deployment performance in real time via actionable insights computed by the logs and events that are emitted by your DevOps toolchain.

The solution currently contains support for Jenkins pipelines, but augmenting the solution to support a Spinnaker-powered CD pipeline enables teams to get even better visibility into their deployments. By adding support for Spinnaker, teams can immediately measure their deployment frequency, lead time, change failure rate and MTTR by repository, service, team, product, environment and more. In addition, Sumo Logic's analytics platform automatically ensures that all metrics are backed by their corresponding raw logs from Spinnaker and other tools, allowing teams to quickly pinpoint bottlenecks and resolve customer-facing incidents.

## Background

Spinnaker and Sumo Logic have an existing integration, the Spinnaker App for Sumo Logic, documented by [Sumo Logic](https://www.sumologic.com/application/spinnaker/) and [Armory](https://docs.armory.io/docs/armory-admin/integrations-sumologic/). It provides insights into the deployments of a Spinnaker-managed SDLC. However, the insights are driven directly from logs and events ingested by Spinnaker.

The SDO Solution has a different architecture. Tools that are feeding data to the SDO Solution are parsed and mapped to a common schema via Sumo Logic's Field Extraction Rules (FERs). The dashboards installed by the SDO solution are hydrated by the normalized data that is created by the FERs. This method of decoupling logs from dashboards (again, via our common schema) is what allows the solution to be extended to support any software in the DevOps toolchain.

## Objective

We are excited to present this challenge in the form of milestones. Challenge rewards are broken up into milestones, allowing teams to claim rewards for each milestone. The milestones for this Sumo Logic challenge are as follows:

1. (Easy) Uncover the appropriate FERs required to map Spinnaker data to our common schema that will then power all of the deployment-related insights for the SDO Solution.
2. (Medium) Update the solution's Terraform template with support for Spinnaker so that the FERs are automatically installed in Sumo Logic when Terraform applies the configuration.
3. (Expert) Extend the [Spinnaker log collection process](https://docs.armory.io/docs/armory-admin/integrations-sumologic/#collect-logs-for-spinnaker) to allow for the injection of arbitrary metadata (e.g. key/value pairs). For example, users may want to note that a deployment is going to an integration, staging or production environment. Instrumenting the pipeline and injecting this metadata allows for users in the Sumo Logic platform to filter insights by such metadata. 

## Getting Started

The best way to get started on the challenge is to provision your own Spinnaker environment, sign up for a Sumo Logic free trial (if you don't already have an account) and install the existing Spinnaker/Armory app, documented by [Sumo Logic](https://www.sumologic.com/application/spinnaker/) and [Armory](https://docs.armory.io/docs/armory-admin/integrations-sumologic/). This process gets Spinnaker data feeding into Sumo (but does not get processed by any FERs that the SDO Solution may use). Users less familiar with Sumo Logic can also check out our [Certifications and Training portal](https://www.sumologic.com/learn/certifications/).

After getting the Spinnaker App for Sumo Logic working, the next step is to get familiar with the [Software Development Optimization Solution](https://help.sumologic.com/Other_Solutions/Software_Development_Optimization_Solution). We recommend installing the solution manually per the documentation as it is gives first time contributors a better understanding of the relationship between FERs, the common schema and the dashboards. Installing the Jenkins FERs should give you a good understanding of how Jenkins' unstructured logs are mapped to the build and deploy phases of the SDLC, and can reveal hints about how an FER for Spinnaker could map spinnaker logs to the deploy phase.

With a proper FER in place that maps Spinnaker logs to the deployment dashboards, the next milestone would be to review the [Terraform solution template](https://github.com/SumoLogic/sumologic-solution-templates) and extend it for Spinnaker support. Feel free to fork this repo and explore!

## Submissions

### Milestone 1
Please fork this repo and submit a SOLUTION-1.md file via pull request.

### Milestone 2
Please fork this repo and submit a SOLUTION-2.md file with a link to a pull request that you have created for the solution's Terraform template

### Milestone 3
Please for this repo and submit a SOLUTION-3.md file with a 1-2 sentence description of your proposed solution and the corresponding Spinnaker yaml/config files that contain an example of arbitrary metadata being injected into the spinnaker pipeline and sent up to Sumo Logic. Please also include a SCREENSHOT.png screenshot of the metadata in Sumo Logic by conducting a log search for the injected metadata.

We see great opportunity in extending the integration and hope everyone enjoys the challenges!