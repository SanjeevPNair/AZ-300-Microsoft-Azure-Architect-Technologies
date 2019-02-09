# Exam AZ-300 - Microsoft Azure Architect Technologies

## Overview

<https://www.microsoft.com/en-us/learning/exam-az-300.aspx>

- View video tutorials about the variety of question types - <https://www.microsoft.com/en-us/learning/certification-exams.aspx?types=true>
- How to Prepare for Microsoft Azure Exam AZ-300? - <https://www.whizlabs.com/blog/az-300-exam-preparation/>
- Another source of information <https://gregorsuttie.com/2018/10/02/azure-architect-design-az-300-exam/>

This exam is for the Azure Architect role. Candidates for this exam are Azure Solution Architects who advise stakeholders and translates business requirements into secure, scalable, and reliable solutions. Candidates should have advanced experience and knowledge across various aspects of IT operations, including networking, virtualization, identity, security, business continuity, disaster recovery, data management, budgeting, and governance. This role requires managing how decisions in each area affects an overall solution. Candidates must be proficient in Azure administration, Azure development, and DevOps, and have expert-level skills in at least one of those domains.

If a candidate does not get a passing score on this exam in the first time, he/she must wait at least 24 hours to retake the exam.
If this happens for the second time, the candidate must wait for at least 14 days to retake the exam. By this way, there is a maximum of 5 appearances allowed for an exam in a year.

- Number of questions: 40 - 60
- Exam time: 150 minutes
- Passing score: 700

Practice tests will be available in February or March 2019.

## Skills measured and links

- Deploy and Configure Infrastructure (25-30%)
  - Analyze resource utilization and consumption
    - Configure diagnostic settings on resources
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-logs-overview#diagnostic-settings>
      - Resource logs - these logs come from Azure services that deploy resources within an Azure subscription, such as Network Security Groups or Storage Accounts.
      - Resource diagnostic logs are configured using resource diagnostic settings. Tenant diagnostic logs are configured using a tenant diagnostic setting.
      - Where diagnostic logs and metrics are sent (Storage Account, Event Hubs, and/or Log Analytics).
      - Which log categories are sent and whether metric data is also sent.
      - How long each log category should be retained in a storage account. A retention of zero days means logs are kept forever. Otherwise, the value can be any number of days.
      - Collection of diagnostic logs can be enabled as part of creating a resource in a Resource Manager template or after a resource is created from that resource's page in the portal. You can also enable collection at any point using Azure PowerShell or CLI commands, or using the Azure Monitor REST API.
    - Create baseline for resources
      - **TODO**
    - Create and raise alerts
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-metric>
      - Metric alerts in Azure Monitor provide a way to get notified when one of your metrics cross a threshold. Metric alerts work on a range of multi-dimensional platform metrics, custom metrics, Application Insights standard and custom metrics.
      - ```az monitor metrics alert create -n {nameofthealert} -g {ResourceGroup} --scopes {VirtualMachineResourceID} --condition "avg Percentage CPU > 90" --description {descriptionofthealert}```
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-classic-portal>
      - Classic metric alerts in Azure Monitor provide a way to get notified when one of your metrics cross a threshold. Classic metric alerts is an older functionality that allows for alerting only on non-dimensional metrics. There is an existing newer functionality called Metric alerts which has improved functionality over classic metric alerts.
      - In the portal, locate the resource that you want to monitor, and then select it. In the MONITORING section, select Alerts (Classic).
      - ```az monitor alert create --name <alert name> --resource-group <group name> --action email <email1 email2 ...> --action webhook <URI> --target <target object ID> --condition "<METRIC> {>,>=,<,<=} <THRESHOLD> {avg,min,max,total,last} ##h##m##s"```
      - After you create an alert, you can select it and do one of the following tasks:
        - View a graph that shows the metric threshold and the actual values from the previous day.
        - Edit or delete it.
        - Disable or Enable it if you want to temporarily stop or resume receiving notifications for that alert.
    - Analyze alerts across subscription
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-metric>
      - In the Manage rules blade, you can view all your alert rules across subscriptions. You can further filter the rules using Resource group, Resource type and Resource. If you want to see only metric alerts, select Signal type as Metrics.
    - Analyze metrics across subscription
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/platform/metrics-charts>
      - If you have more than one Azure subscription, Metrics Explorer pulls out the resources across all subscriptions that are selected in the Portal Settings -> Filter by subscriptions list.
    - Create action groups
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/platform/action-groups>
      - An action group is a collection of notification preferences defined by the owner of an Azure subscription. Azure Monitor and Service Health alerts use action groups to notify users that an alert has been triggered. Various alerts may use the same action group or different action groups depending on the user's requirements.
      - Email / SMS / Push / Voice / Function / LogicApp / Webhook / ITSM / Runbook
    - Monitor for unused resources
      - <https://docs.microsoft.com/en-us/azure/advisor/advisor-overview>
      - Azure Advisor is a service that, among other things, identifies virtual machines with low utilization from a CPU or network usage standpoint. From there, you can decide to either shut down or resize the machine based on the estimated cost to continue running the machines. Advisor also provides recommendations for reserved instance purchases. The recommendations are based on your last 30 days of virtual machine usage. When acted on, the recommendations can help you reduce your spending.
    - Monitor spend
      - <https://docs.microsoft.com/en-us/azure/billing/billing-getting-started#ways-to-monitor-your-costs-when-using-azure-services>
      - You can use tags to group billing data for supported services. The tags show up throughout different cost reporting views.
      - Use billing API to programmatically get usage data. Use the RateCard API and the Usage API together to get your billed usage.
      - <https://docs.microsoft.com/en-us/azure/billing/billing-getting-started#costs>
      - You can see the current spend and burn rate in Azure portal.
      - Azure Portal -> Subscriptions -> see the cost breakdown and burn rate -> Cost analysis see the cost breakdown by resource. Wait 24 hours for the data to populate.
      - You can filter by different properties like tags, resource type, resource group, and timespan. You can download csv.
    - Report on spend
      - <https://docs.microsoft.com/en-us/azure/billing/billing-download-azure-invoice-daily-usage-date#download-usage>
      - Download usage as an EA customer, Azure portal -> Cost Management + Billing -> Usage + charges
      - <https://docs.microsoft.com/en-us/azure/billing/billing-understand-your-bill-ea#review-charges>
      - You must be an Enterprise Administrator, Enterprise portal -> Reports -> Usage Summary
    - Utilize Log Search query functions
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/log-query-overview>
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/functions>
      - Demo environment - <https://portal.loganalytics.io/demo>
      - Log data collected by Azure Monitor is stored in a Log Analytics workspace, which is based on Azure Data Explorer.
      - To use an query with another query you can save it as a function. This allows you to simplify complex queries by breaking them into parts and allows you to reuse common code with multiple queries.
      - Azure portal -> Save -> Save as Function
      - MyFunction | where Title contains "SQL"
    - View alerts in Log Analytics
      - <https://docs.microsoft.com/en-us/azure/azure-monitor/platform/alerts-overview#all-alerts-page>
      - Notify you when important conditions are found in your monitoring data. Azure Monitor, which now includes Log Analytics and Application Insights. Not classic alerts.
      - Alert Rule => Target+Metric+Treshold calls action-group+actions and monitor-condition+alert-state
  - Create and configure storage accounts
    - Configure network access to the storage account
      - <https://docs.microsoft.com/en-us/azure/storage/common/storage-network-security>
      - Configure storage accounts to deny access to traffic from all networks (including internet traffic) by default. Then grant access to traffic from specific VNets. This configuration enables you to build a secure network boundary for your applications. You can also grant access to public internet IP address ranges, enabling connections from specific internet or on-premises clients.
      - When network rules are configured, only applications requesting data from over the specified set of networks can access a storage account.
      - Network rules are enforced on all network protocols to Azure storage, including REST and SMB. To access the data with tools like Azure portal, Storage Explorer, and AZCopy, explicit network rules are required.
      - Virtual machine disk traffic (including mount and unmount operations, and disk IO) is not affected by network rules.
      - There are some cases where exceptions must be granted to enable full functionality. You can configure storage accounts with exceptions for trusted Microsoft services, and for access to storage analytics data.
      - ```az storage account update --resource-group "myresourcegroup" --name "mystorageaccount" --bypass Logging Metrics AzureServices```
      - <https://azure.microsoft.com/en-us/blog/virtual-network-service-endpoints-and-firewalls-for-azure-storage-now-generally-available/>
      - To enable VNet protection, first enable service endpoints for storage in the VNet. Virtual Network Service Endpoints allow you to secure your critical Azure service resource to only your virtual network. Service endpoints also provide optimal routing for Azure traffic over the Azure backbone in scenarios where Internet traffic is routed through virtual appliances or on-premises.
      - On the storage account you can select to allow access to one or more VNets. You may also configure to allow access to one or more public IP ranges.
    - Create and configure storage account
      - <https://docs.microsoft.com/en-us/azure/storage/common/storage-quickstart-create-account?tabs=azure-portal>
      - ```az storage account create --name storagequickstart --resource-group storage-quickstart-resource-group --location westus --sku Standard_LRS --kind StorageV2```
      - ```New-AzStorageAccount -ResourceGroupName $resourceGroup -Name "storagequickstart" -Location $location -SkuName Standard_LRS -Kind StorageV2```
    - Generate shared access signature
      - <https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-blobs>
      - Right-click the desired blob container, and - from the context menu - select Get Shared Access Signature.
    - Install and use Azure Storage Explorer
      - <https://azure.microsoft.com/en-us/features/storage-explorer/>
      - <https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-manage-with-storage-explorer?tabs=windows>
      - Easily manage Storage anywhere from Windows, macOS, and Linux
      - Access multiple accounts and subscriptions across Azure, Azure Stack, and the sovereign Cloud
      - Create, delete, view, and edit storage resources
      - View and edit Blob, Queue, Table, File, Cosmos DB storage and Data Lake Storage
      - Obtain shared access signature (SAS) keys
      - Available for Windows, Mac, and Linux
      - Gain easy access to manage your virtual machine disks
      - Work with either Azure Resource Manager or classic storage accounts, plus manage and configure cross-origin resource sharing (CORS) rules.
    - Manage access keys
      - <https://docs.microsoft.com/en-us/azure/storage/common/storage-dotnet-shared-access-signature-part-1>
      - Account key and Shared access signatures (SAS). Your storage account includes both a primary and secondary access key, both of which grant administrative access to your account, and all resources within it. Exposing either of these keys opens your account to the possibility of malicious or negligent use. Shared access signatures provide a safe alternative that allows clients to read, write, and delete data in your storage account according to the permissions you've explicitly granted, and without need for an account key.
      - A shared access signature provides delegated access to resources in your storage account. With a SAS, you can grant clients access to resources in your storage account, without sharing your account keys. This is the key point of using shared access signatures in your applications--a SAS is a secure way to share your storage resources without compromising your account keys.
      - Your storage account key is similar to the root password for your storage account. Always be careful to protect your account key. Avoid distributing it to other users, hard-coding it, or saving it anywhere in plaintext that is accessible to others. Regenerate your account key using the Azure portal if you believe it may have been compromised.
      - A SAS gives you granular control over the type of access you grant to clients who have the SAS, including:
        - The interval over which the SAS is valid, including the start time and the expiry time.
        - The permissions granted by the SAS. For example, a SAS for a blob might grant read and write permissions to that blob, but not delete permissions.
        - An optional IP address or range of IP addresses from which Azure Storage will accept the SAS. For example, you might specify a range of IP addresses belonging to your organization.
        - The protocol over which Azure Storage will accept the SAS. You can use this optional parameter to restrict access to clients using HTTPS.
      - You can create two types of shared access signatures:
        - Service SAS. The service SAS delegates access to a resource in just one of the storage services: the Blob, Queue, Table, or File service.
        - Account SAS. The account SAS delegates access to resources in one or more of the storage services. All of the operations available via a service SAS are also available via an account SAS. Additionally, with the account SAS, you can delegate access to operations that apply to a given service, such as Get/Set Service Properties and Get Service Stats. You can also delegate access to read, write, and delete operations on blob containers, tables, queues, and file shares that are not permitted with a service SAS.
    - Monitor activity log by using Log Analytics
      - **TODO**
    - Implement Azure storage replication
      - **TODO**
  - Create and configure a Virtual Machine (VM) for Windows and Linux
    - Configure high availability
      - **TODO**
    - Configure monitoring networking, storage, and virtual machine size
      - **TODO**
    - Deploy and configure scale sets
      - **TODO**
  - Automate deployment of Virtual Machines (VMs)
    - Modify Azure Resource Manager (ARM) template
      - **TODO**
    - Configure location of new VMs
      - **TODO**
    - Configure VHD template
      - **TODO**
    - Deploy from template
      - **TODO**
    - Save a deployment as an ARM template
      - **TODO**
    - Deploy Windows and Linux VMs
      - **TODO**
  - Create connectivity between virtual networks
    - Create and configure VNET peering
      - **TODO**
    - Create and configure VNET to VNET
      - **TODO**
    - Verify virtual network connectivity
      - **TODO**
    - Create virtual network gateway
      - **TODO**
  - Implement and manage virtual networking
    - Configure private and public IP addresses, network routes, network interface, subnets, and virtual network
      - **TODO**
  - Manage Azure Active Directory (AD)
    - Add custom domains
      - <https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/add-custom-domain>
      - Initial domain name, domainname.onmicrosoft.com. You can't change or delete
      - You must create your domain name with a domain registrar. You must include .com, .net, or any other top-level extension
      - Azure Portal -> AAD -> Custom domain names -> Add custom domain -> Add domain
      - Unverified domain is added and the page showing you your DNS info
      - You must return to your domain registrar and add the Azure AD DNS information from your copied TXT file. Creating this TXT record for your domain "verifies" ownership of your domain name
      - Set the TTL (time to live) to 3600 seconds (60 minutes), and then save the information
      - On the page, select Verify to make sure your custom domain is properly registered and is valid for Azure AD
    - Configure Azure AD Identity Protection
      - <https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/enable>
        - Get a consolidated view of flagged users and risk events detected using machine learning algorithms
        - Set risk-based Conditional Access policies to automatically protect your users
        - Improve security posture by acting on vulnerabilities
      - <https://docs.microsoft.com/en-us/azure/active-directory/identity-protection/overview>
      - Azure Portal -> Marketplace -> Azure AD Identity Protection -> Create
      - Feature of the Azure AD Premium P2 edition
    - Configure Azure AD Join
      - <https://docs.microsoft.com/en-us/azure/active-directory/devices/hybrid-azuread-join-managed-domains>
      - <https://aadguide.azurewebsites.net/aadjoin/>
      - Azure AD Connect -> Configure -> Configure device options -> Hybrid Azure AD join
    - Configure Azure AD Enterprise State Roaming
      - <https://docs.microsoft.com/en-us/azure/active-directory/devices/enterprise-state-roaming-enable>
      - Enterprise State Roaming is available to any organization with an Azure AD Premium or Enterprise Mobility + Security (EMS) license.
      - Azure Portal -> AAD -> Devices -> Enterprise State Roaming -> Select Users may sync settings and app data across devices
      - For a Windows 10 device to use the Enterprise State Roaming service, the device must authenticate using an Azure AD identity. For devices that are joined to Azure AD, the user’s primary sign-in identity is their Azure AD identity, so no additional configuration is required. For devices that use on-premises Active Directory, the IT admin must Configure hybrid Azure Active Directory joined devices.
    - Configure self-service password reset
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-sspr-pilot>
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-sspr-deployment>
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-howitworks>
      - Self-Service Password Reset/Change/Unlock with on-premises writeback is a premium feature of Azure AD. 
      - Standalone Office 365 licensing plans don't support "Self-Service Password Reset/Change/Unlock with on-premises writeback"
      - Self-service password reset portal located at <https://aka.ms/ssprsetup>
      - Self-service password reset portal <https://aka.ms/sspr>
      - Azure Portal -> AAD -> Password reset -> Properties -> Self Service Password Reset Enabled
      - Azure Portal -> AAD -> Password reset -> Authentication methods -> Number of methods required to reset to 2
      - Azure Portal -> AAD -> Password reset -> Notifications (Notify users on password resets, Notify all admins when other admins reset their password), Registration (Require users to register when signing in), Customization (Customize helpdesk link)
    - Implement conditional access policies
      - **TODO**
    - Manage multiple directories
      - **TODO**
    - Perform an access review
      - **TODO**
  - Implement and manage hybrid identities
    - Install and configure Azure AD Connect
      - **TODO**
    - Configure federation and single sign-on
      - **TODO**
    - Manage Azure AD Connect
      - **TODO**
    - Manage password sync and writeback
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-writeback>
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-sspr-writeback>
      - Self-Service Password Reset/Change/Unlock with on-premises writeback is a premium feature of Azure AD.
      - Standalone Office 365 licensing plans don't support "Self-Service Password Reset/Change/Unlock with on-premises writeback"
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-howitworks#write-back-passwords-to-your-on-premises-directory>
      - If the switch is set to Yes, then writeback is enabled, and federated, pass-through authentication, or password hash synchronized users are able to reset their passwords.

___

- Implement Workloads and Security (20-25%)
  - Migrate servers to Azure
    - Migrate by using Azure Site Recovery (ASR)
      - **TODO**
    - Migrate using P2V
      - **TODO**
    - Configure storage
      - **TODO**
    - Create a backup vault
      - **TODO**
    - Prepare source and target environments
      - **TODO**
    - Backup and restore data
      - **TODO**
    - Deploy Azure Site Recovery (ASR) agent
      - **TODO**
    - Prepare virtual network
      - **TODO**
  - Configure serverless computing
    - Create and manage objects
      - **TODO**
    - Manage a Logic App resource
      - **TODO**
    - Manage Azure Function app settings
      - **TODO**
    - Manage Event Grid
      - **TODO**
    - Manage Service Bus
      - **TODO**
  - Implement application load balancing
    - Configure application gateway and load balancing rules
      - **TODO**
    - Implement front end IP configurations
      - **TODO**
    - Manage application load balancing
      - **TODO**
  - Integrate on premises network with Azure virtual network
    - Create and configure Azure VPN Gateway
      - **TODO**
    - Create and configure site to site VPN
      - **TODO**
    - Configure Express Route
      - **TODO**
    - Verify on premises connectivity
      - **TODO**
    - Manage on-premise connectivity with Azure
      - **TODO**
  - Manage role-based access control (RBAC)
    - Create a custom role
      - **TODO**
    - Configure access to Azure resources by assigning roles
      - **TODO**
    - Configure management access to Azure
      - **TODO**
    - Troubleshoot RBAC
      - **TODO**
    - Implement RBAC policies
      - **TODO**
    - Assign RBAC roles
      - **TODO**
  - Implement Multi-Factor Authentication (MFA)
    - Enable MFA for an Azure tenant
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-getstarted>
      - Requires global administrator account in Azure AD tenant.
      - Correct licenses assigned to users
        - Multi-Factor Authentication for Office 365 Microsoft 365 Business - Works only for O365/M365 This version is part of an Office 365 or Microsoft 365 Business subscription.
        - Multi-Factor Authentication for Azure AD Administrators - Works only for Azure AD Global Administrator role at no additional cost.
        - Azure Multi-Factor Authentication - Full version. Additional configuration options via the Azure portal, advanced reporting, and support for a range of on-premises and cloud applications. Requires Azure Active Directory Premium, and can be deployed either in the cloud or on-premises.
      - Choose how to enable
        - Enabled by conditional access policy - the most flexible way to enable two-step verification for your users
        - Enabled by Azure AD Identity Protection - uses the Azure AD Identity Protection risk policy to require two-step verification based only on sign-in risk for all cloud applications
        - Enabled by changing user state - requires users to perform two-step verification every time they sign in and overrides conditional access policies
      - Enable at least one authentication method (best is Microsoft Authenticator)
      - Ask users to enroll https://aka.ms/mfasetup (ask users to register authentication methods beforehand)
      - Step 1: Azure Portal -> AAD -> Users -> Multi-Factor Authentication -> service settings -> verification options, check all of the boxes for methods available to users -> save
      - Step 2: Azure Portal -> AAD -> Conditional access -> New policy -> Include/Exclude users/groups, choose optionally conditions -> Grant Require multi-factor authentication -> Enable policy -> Create
    - Configure user accounts for MFA
      - See above.
    - Configure fraud alerts
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-mfasettings#fraud-alert>
      - Users can report fraudulent attempts to access their resources. Users can report fraud attempts by using the mobile app or through their phone. This feature is specific to MFA Server (on-premises).
      - Azure Portal -> AAD -> MFA -> Fraud alert -> Set the Allow users to submit fraud alerts setting to On -> Save
      - Options
        - Block user when fraud is reported (for 90 days or unblocked by Administrator)
        - Code to report fraud during initial greeting - phone call to perform two-step verification. To report fraud, the user enters a code before pressing #
      - View fraud reports: Azure Portal -> AAD -> Sign-ins
    - Configure bypass options
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-mfasettings#one-time-bypass>
      - One-time bypass - Allows a user to authenticate a single time without performing two-step verification. (temporary and expires after a specified number of seconds). The user needs to sign in before the one-time bypass expires.
      - Azure Active Directory -> MFA -> One-time bypass -> Add, username as username@domain.com enter the number of seconds and reason.
      - View one-time bypass reports: Azure Portal -> AAD -> MFA -> One-time bypass
    - Configure trusted IPs
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-mfasettings#trusted-ips>
      - Is used by administrators of a managed or federated tenant. Bypasses two-step verification for users who sign in from the company intranet. Only available in Full version of MFA and only IPv4.
      - Step 1: Azure Portal -> AAD -> Conditional access -> Named locations -> New location -> Mark as trusted location -> enter CIDR -> Create
      - Step 2: Azure Portal -> AAD -> Conditional access -> Named locations -> Configure MFA trusted IPs
        - Select -> For requests from a specific range of public IPs -> enter CIDR
        - Or Select -> For requests from federated users originating from my intranet (All federated users who sign in from the corporate network bypass two-step verification by using a claim that is issued by AD FS)
        - Save
      - Step 3: Azure Portal -> AAD -> MFA -> service settings -> Configure MFA trusted IPs
        - Select -> For requests from a specific range of public IPs -> enter CIDR
        - Or Select -> For requests from federated users originating from my intranet (All federated users who sign in from the corporate network bypass two-step verification by using a claim that is issued by AD FS)
        - Save
    - Configure verification methods
      - <https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-mfasettings#verification-methods>
      - When your users enroll for MFA, they choose their preferred verification method from enabled options.
        - Call to phone - user answers the call and presses #
        - Text message to phone - Sends a text message that contains a verification code.
        - Notification through mobile Microsoft Authenticator app - Sends a push notification to your device. The user views the notification and selects Verify to complete verification.
        - Verification code from mobile app or hardware token - Microsoft Authenticator app generates a new OATH verification code every 30 seconds
      - Azure Portal -> AAD -> Users and groups -> All users -> Multi-Factor Authentication -> service settings -> verification options -> select/unselect the methods -> Save
    - Manage role-based access control (RBAC)
      - **TODO**
    - Implement RBAC policies
      - **TODO**
    - Assign RBAC Roles
      - **TODO**
    - Create a custom role
      - **TODO**
    - Configure access to Azure resources by assigning roles
      - **TODO**
    - Configure management access to Azure
      - **TODO**

___

- Create and Deploy Apps (5-10%)
  - Create web apps by using PaaS
    - Create an Azure App Service Web App
      - **TODO**
    - Create documentation for the API
      - **TODO**
    - Create an App Service Web App for containers
      - **TODO**
    - Create an App Service background task by using WebJobs
      - **TODO**
    - Enable diagnostics logging
      - **TODO**
  - Design and develop apps that run in containers
    - Configure diagnostic settings on resources
      - **TODO**
    - Create a container image by using a Docker file
      - **TODO**
    - Create an Azure Container Service (ACS/AKS)
      - **TODO**
    - Publish an image to the Azure Container Registry
      - **TODO**
    - Implement an application that runs on an Azure Container Instance
      - **TODO**
    - Manage container settings by using code
      - **TODO**

___

- Implement Authentication and Secure Data (5-10%)
  - Implement authentication
    - Implement authentication by using certificates, forms-based authentication, tokens, or Windows-integrated authentication
      - **TODO**
    - Implement multi-factor authentication by using Azure AD
      - **TODO**
    - Implement OAuth2 authentication
      - **TODO**
    - Implement Managed Service Identity (MSI) Service Principal authentication
      - **TODO**
  - Implement secure data solutions
    - Encrypt and decrypt data at rest and in transit
      - **TODO**
    - Encrypt data with Always Encrypted
      - **TODO**
    - Implement Azure Confidential Compute and SSL/TLS communications
      - **TODO**
    - Create, read, update, and delete keys, secrets, and certificates by using the KeyVault API
      - **TODO**

___

- Develop for the Cloud (20-25%)
  - Configure a message-based integration architecture
    - Configure an app or service to send emails, Event Grid, and the Azure Relay Service
      - **TODO**
    - Create and configure Notification Hub, Event Hub, and Service Bus
      - **TODO**
    - Configure queries across multiple products
      - **TODO**
  - Develop for autoscaling
    - Implement autoscaling rules and patterns (schedule, operational/system metrics, code that addresses singleton application instances)
      - **TODO**
    - Implement code that addresses transient state
      - **TODO**
