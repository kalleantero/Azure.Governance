# Azure Platform Governance

Azure Platform Governance is a strategic enabler which determines guidelines, processes and technologies how to build a secure Azure environment according to best practices and organization requirements. Azure Platform Governance document gathers all these requirements to a single document. Azure Platform Governance ensures that all services developed by multiple teams across multiple subscriptions are created according to commonly agreed guidelines.

Azure Platform Governance has the following focus areas
- Ensure secure solutions
- Ensure operation effectiveness
- Ensure unified way of creating/developing services
- Ensure operational excellency
- Ensure business continuity

> Note! Azure Platform Governance should be evaluated periodically.

## Template

> Note! This is not a complete template. It's a simplified version which evolves.

This repository contains a sample template for Azure platform governance document which can be found from [here](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md). Template has defined structure which contains eight main policies which are introduced below. Requirements for all these main policies should be determined per organization. Template also has some recommendations and best practices.

This template has got influences from the [Microsoft Cloud Adoption Framework for Azure (CAF)](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/) and [Microsoft Azure Well-Architected Framework (WAF)](https://learn.microsoft.com/en-us/azure/architecture/framework/) which are key frameworks for cloud adoption.

Template contains the following main policies:

### [Management policy](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md#20-management-hierarchy)

Management hierarchy policy determines organization's guidelines how to produce Management groups & Azure subscriptions and how to model Resource Groups.

### [Naming convention policy](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md#30-naming-convention)

Naming convention policy ensures standardized and unified naming for all Azure Resources across multiple subscriptions.

### [Compliency policy](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md#40-compliency)

Typically organizations have many compliency related requirements. Compliency policy determines things like where data or services can be located and how logging should be configured across services.

### [Recommendations for specific Azure resources](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md#50-recommendations-for-specific-azure-resources)

This section contains Azure resourcetype specific recommendations.

### [Security policy](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md#60-security)

Security policy determines best practices how services must be developed to Azure platform to ensure hardened security.

### [Operational excellency policy](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md#70-operational-excellency)

Operational excellency policy defines what kind of tools and processes teams must implement and follow to ensure that production environment is working and if something happens then team is notified about the situation.

### [Disaster Recovery policy](https://github.com/kalleantero/Azure.Governance/blob/main/Azure-Platform-Governance.md#80-disaster-recovery)

Disaster recovery focuses on business continuity and ensuring that environment and applications are up and running as soon as possible after disaster situation.
