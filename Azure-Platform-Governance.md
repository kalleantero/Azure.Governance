# Azure Platform Governance template

## Change history

|   v1.0   |   20.12.2022   |   Kalle Marjokorpi   |   Initial version created

## 1.0 Introduction

This document contains Azure Platform Governance. Azure Platform Governance is a strategic enabler which determines guidelines, process and technologies how to build a secure Azure environment according to best practices and organization requirements.

Read also Microsoft Cloud Adoption Framework for Azure (CAF) and Microsoft Azure Well-Architected Framework (WAF) which are key frameworks for cloud adoption (see links below). This Azure platform Governance template contains parts from the both of those frameworks but it's simplified version and focuses more to technical aspects for organizations which already have experience about Azure cloud platform.

> [Microsoft Cloud Adoption Framework for Azure (CAF)](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework)
>
> Microsoft Cloud Adoption Framework for Azure (CAF) is concentrating more how to transform and preparate organization to cloud.
 
> [Microsoft Azure Well-Architected Framework (WAF)](https://learn.microsoft.com/en-us/azure/architecture/framework/)
> 
> Microsoft Azure Well-Architected Framework (WAF) focuses best practices how to develope and manage cloud application securely and cost-effectively.

Note! This is not a complete template.

### 1.2 Target audience

IT pro, developers and architects in organizations which already have experience about Azure.

### 1.3 Scope of the document

Azure AD / Identity management related governance is out scoped from this document. Also separate complete disaster recovery plan is advisable to create.

## 2.0 Management hierarchy

Management in Azure is divided to four levels / hierarchies and this section describes how management is handled in this organization.

> Read more: [Cloud Adoption Framework: Management levels and hierarcy](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-setup-guide/organize-resources#management-levels-and-hierarchy)

### 2.1 Management groups

Management group is a tool in Azure to help manage policies, access and compliency related configurations across multiple subscriptions.

> Read more: [Cloud Adoption Framework - Organize your Azure resources effectively](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-setup-guide/organize-resources#management-levels-and-hierarchy)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 2.2 Subscriptions

Subscription is a container where resource groups and resources are associated in Azure. Subscription has some limits which typically leads to separating subscription by environment and ex. product.

> Read more: [Cloud Adoption Framework - Organize your Azure resources effectively](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-setup-guide/organize-resources#management-levels-and-hierarchy)

> **Recommendations**
>
> - Create Azure subscription per product/domain especially if you're operating in large scale environment.
> - Create a separate Azure subscription for test environment because it can save costs when subscription is determined to test/dev purpose.
> - Consider to create a separate Azure subscription for shared services and resources

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 2.3 Resource Groups

Resource group is a container which enables to group resources based on rules what you have defined. Typically ex. microservices are separated so that each microservice has own resource group.

> Read more: [Cloud Adoption Framework - Organize your Azure resources effectively](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-setup-guide/organize-resources#management-levels-and-hierarchy)

> **Recommendations**
>
> - If microservice environment is applied consider creating resource group per microservice
> - Group shared resources by the function to same Resource Group (ex. operations related resource to same Resource Group)
> - Consider resource sharebility (ex. sharing compute resource for multiple microservice)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

## 3.0 Naming convention

Naming convention policy ensures standardized and unified naming for all Azure resouces across multiple subscriptions.

> Ream more: [Cloud Adoption Framework: Define your naming convention](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming)

### 3.1 Azure Subscriptions

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 3.2 Resource Groups

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 3.3 Resources

> Read more: [Cloud Adoption Framework - Abbreviation examples for Azure resources](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 3.4 Exceptions

Exceptions to general naming convention are described here.

#### 3.4.1 Storage Accounts

Storage Account doesn't support adding separator characters in name. Use general naming convention but if it contains separator characters remove them.

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 3.5 Tagging Strategy

Resource tagging enables a powerful way to mark resources/system component over resource groups or subscriptions.

> Read more: [Cloud Adoption Framework - Define your tagging strategy](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-tagging)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

## 4.0 Compliency

Compliency requirements of the organization are described in this section.

### 4.1 Data residency

Organization might have requirements that data must be located only ex. in EU area. These requirements are described here.

#### 4.1.1 Allowed regions

> **Recommendations**
>
> - Pay attention to GDPR requirements
> - Use Azure Policy to allow resource creation to only specific regions

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 4.1.2 Allowed global services

> **Recommendations**
>
> - Pay attention to GDPR requirements
> - Use Azure Policy to restrict resource creation by the type

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 4.2 Logging

#### 4.2.1 Administrative access activity

The Azure Activity Log is a subscription log that provides insight into subscription-level events. Activity log provides audit information what operations were taken to resource (who, when and what). By default activity log data is persisted for 90 days.

> [Read more: Azure Monitor activity log](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/activity-log)

> **Recommendations**
>
> - Configure active log data export to longer term storage or integration to SIEM system.
> - Restrict access to longer term storage of activity log data

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 4.2.2 Application insights

Application Insights is an extension of Azure Monitor and it provides tools for monitor applications and services.

> [Read more: Application Insights overview](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview?tabs=net)

> **Recommendations**
> - Application Insight must be created when ever it's possible (App Services, Function Apps etc.).
> - Configure Application Insights to Workspace mode bacause classic version will be deprated.
> - Configure extended data retention time if necessary (default is 90 days)
> - Locate Application Insight to same resource group where related ingesting resource is located.

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 4.2.3 Diagnostics logs

Resource level diagnostics logs provides resource specific operation logs. Content of diagnostics logs varies by resource type (ex. App Service provides Http Logs, IPSecurity Audit logs etc.)

> **Recommendations**
>
> - Configure diagnostics log data export to longer term storage if necessary. Diagnostic data can be exported to EventHub, Storage Account or Log Analytics
> - Create a separate resource group where data is persisted
> - Configure Azure policy for this

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

## 5.0 Recommendations for specific Azure resources

### 5.1 Azure App Configuration

Azure App Configuration enables central management of application settings and feature flags.

> **Recommendations**
> - You can deploy one free instance of Azure App Configuration per subscription
> - Consider using Private endpoint if applicable
> - Consider connecting KeyVault to App Configuration

> Read more: [What is Azure App Configuration?](https://learn.microsoft.com/en-us/azure/azure-app-configuration/overview)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 5.2 Azure App Service / Azure Function App

> **Recommendations**
> - Create Azure Policy which doesn't allow FTP
> - Create Azure Policy which doesn't allow using App Service or Function without HTTPS

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

## 6.0 Security

### 6.1 Microsoft Defender for Cloud

Microsoft Defender for Cloud provides recommendations and advises how to configure your Azure platform to use latest security best practices. 

> Read more: [What is Microsoft Defender for Cloud?](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)

> **Recommendations**
>
> - Enable Defender for Cloud
> - Enable Defender for SQL

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 6.2 Application secrets and certificate handling

This section describes how application secrets and certificates are handled in Azure platform.

#### 6.2.1 Azure KeyVault

Azure KeyVault is a key/secret/certificate management system in Azure platform.

> Read more: [About Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/overview) and [Azure Key Vault developer's guide](https://learn.microsoft.com/en-us/azure/key-vault/general/developers-guide)

> **Recommendations**
>
> - Allow access to Azure KeyVault only from the VNET or specific IP addresses
> - Create a separate KeyVault resource for operation/maintenance related things
> - Do not use [KeyVault reference for App Services and Azure Functions](https://learn.microsoft.com/en-us/azure/app-service/app-service-key-vault-references?tabs=azure-cli) if team has access to Kudu. Kudu reveals KeyVault secrets even user does not have access to KeyVault in Azure portal
> - Enable Azure role-based access control for KeyVault
> - Restrict Access to KeyVault
> - Enable soft delete for KeyVault
> - Plan how to backup KeyVault secrets (disaster recovery situation)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.2.2 Managed identity

Managed identity enables secure communication between Azure services.

> Read more: [What are managed identities for Azure resources?
](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview)

> **Recommendations**
>
> - Prefer always Managed Identity based authentication ex. to Azure SQL database instead of using SQL login

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.2.3 Application secrets and credentials

This section describes a policy how secrets and credentials must be stored in organization's Azure platform.

> **Recommendations**
>
> - Prefer always Managed Identity
> - All secrets and credentials must be stored to Azure KeyVault

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.2.4 Certificates

> **Recommendations**
>
> - All certificates must be stored to Azure KeyVault

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.2.5 Certificates renewal automation

> **Recommendations**
>
> - Use Azure Managed certificates in test environment which are automatically renewed
> - If Azure Managed certificates are not applicable consider using Let's Encrypt certificates. Note! certificate renewal automation must be built by yourself.

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 6.3 Secret rotating policy

It's highly recommended to periodically rotate client secrets.

> **Recommendations**
>
> - Create automation for rotating secrets

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 6.4 Customer managed keys

> Read more: [Key management in Azure](https://learn.microsoft.com/en-us/azure/security/fundamentals/key-management)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 6.5 Network

#### 6.5.1 Web application firewall

Web application firewall (WAF) protects application from exploits and vulnerabilities.

> Read more: [What is Azure Web Application Firewall on Azure Application Gateway?](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview)

> **Recommendations**
>
> - Add Web application firewall to your Hub Azure subscription

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.5.2 Virtual networks

Virtual network in Azure enables secure and isolated network connectivity for applications.

> Read more: [Virtual Network documentation](https://learn.microsoft.com/en-us/azure/virtual-network/)

> **Recommendations**
>
> - All services must be added to virtual network

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.5.3 Private endpoint

> Read more: [What is Azure Private Link?](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview)

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 6.6 Data protection

This section describes recommendations how you should protect data storages in your organization's Azure platform.

#### 6.6.1 Azure SQL databases

> **Recommendations**
>
> - Disable public access
> - Disable access from Azure services
> - Follow Microsoft Defender for Cloud recommandations
> - Enable private endpoint if applicable

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.6.2 Azure Cosmos DB

> **Recommendations**
>
> - Disable public access
> - Enable Microsoft Defender for Azure Cosmos DB
> - Enable private endpoint if applicable

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 6.6.3 Azure Storage Accounts

> **Recommendations**
>
> - Rotate access keys periodically
> - Use Shared Access Signatures with IP restriction if applicable
> - Disable public access
> - Follow Microsoft Defender for Cloud recommandations
> - Enable private endpoint if applicable

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

## 7.0 Operational excellency

### 7.1 Monitoring

#### 7.1.1 Availability tests

System component specific availability test ensures that team is immediately notified if health of component is degraded.

> **Recommendations**
>
> - Enable .NET Core health check point on each system component and configure Availaibility test to ping that endpoint

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 7.1.2 Service Health

Azure monitor provides a Service health functionality which shows and delivers alert event about service outages in Azure platform.

> **Recommendations**
>
> - Enable service health alerts from Azure Monitor

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

#### 7.1.3 Alerting

> **Recommendations**
>
> - Create generic a Logic App implementation which can handle metric and other alerts initated by Azure Monitor

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 7.2 Dashboards

Azure Dashboards and workbooks visualize state of the application.

> Read more: [Create a dashboard in the Azure portal](https://learn.microsoft.com/en-us/azure/azure-portal/azure-portal-dashboards) and [Azure Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)

> **Recommendations**
>
> - Create a separate resource group for dashboards and workbooks
> - Create a shared dashboard for each system component

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 7.3 Cost management

This section contains information how to monitor costs of the Azure platform.

7.3.1 Budget alerts

> **Recommendations**
>
> - Monitor costs especially if you use serverless services

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

## 8.0 Disaster Recovery

Disaster recovery focuses on business continuity and ensuring that environment and applications are up and running as soon as possible after disaster situation.

This section describes the disaster recovery process and how services should be created to Azure platform to minimize outage.

### 8.1 Infrastructure as a code (IaC) policy

Infrastructure as Code (IaC) policy determines how Azure resources and infrastructure are created through code instead of using manual processes.

#### 8.1.1 Chosen IaC technology

Infrastructure as a code can be implemented using different technologies in Azure platform. This section describes which technology (ARM, Bicep, Terraform) should be used in your organization to implement IaC in Azure platform.

> **Recommendations**
>
> - Use Bicep instead of creating plain ARM-templates

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 8.2 Resource locks

Resource locks enable you to restrict deleting or modifying resources.

> Read more: [Lock your resources to protect your infrastructure](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json)

> **Recommendations**
>
> - Create Azure policy for resource locks which includes most critical infrastructure ex. virtual networks, gateways etc.

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 8.3 Soft delete

Soft delete helps mitigate the impact of accidentally deleting critical data.

> **Recommendations**
>
> - Create Azure policy for soft delete

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]

### 8.4 Database backups

[REPLACE THIS PLACEHOLDER WITH YOUR POLICY]
