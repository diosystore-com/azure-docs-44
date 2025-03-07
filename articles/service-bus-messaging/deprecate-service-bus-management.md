---
title: Azure messaging services - Service Manager to Resource Manager
description: This article provides mapping of deprecated Azure Service Manager REST API & PowerShell cmdlets to Resource Manager REST API & PowerShell cmdlets.
ms.topic: article
ms.date: 04/10/2023
---

# Deprecation of Azure Service Manager support for Azure Service Bus, Relay, and Event Hubs

Resource Manager, our next-generation cloud infrastructure stack, is fully replacing the "classic" Azure Service Management model (classic deployment model). As a result, classic deployment model REST APIs for Service Bus, Relay, and Event Hubs will be retired on December 1, 2021. This deprecation was first announced on a [Microsoft Tech Community announcement](https://techcommunity.microsoft.com/t5/Service-Bus-blog/Deprecating-Service-Management-support-for-Azure-Service-Bus/ba-p/370909). For easy identification, these APIs have `management.core.windows.net` in their URI. Refer to the following table for a list of the deprecated APIs and their Azure Resource Manager API version that you should now use.

To continue using Service Bus, Relay, and Event Hubs, move to Resource Manager by November 30, 2021. We encourage all customers who are still using old APIs to make the switch soon to take advantage of the extra benefits of Resource Manager, which include resource grouping, tags, a streamlined deployment and management process, and fine-grained access control using Azure role-based access control (Azure RBAC).

For more information on Service Manager and Resource Manager APIs for Azure Service Bus, Relay and Event Hubs, see our REST API documentation:

- [Azure Service Bus](/rest/api/servicebus/)
- [Azure Event Hubs](/rest/api/eventhub/)
- [Azure Relay](/rest/api/relay/)

## Service Manager REST API - Resource Manager REST API

| Service Manager APIs (Deprecated) | Resource Manager - Service Bus API | Resource Manager - Event Hubs API | Resource Manager - Relay API |
| --------------- | ----------------- | ----------------- | ----------------- | 
| **Namespaces-GetNamespaceAsync** <br/>[Service Bus Get Namespace](/rest/api/servicebus/get-namespace)<br/>[Event Hubs Get Namespace](/rest/api/eventhub/get-event-hub)<br/>[Relay Get Namespace](/rest/api/servicebus/get-relays)<br/> ```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}``` | [get](/rest/api/servicebus/stable/namespaces/get) | [get](/rest/api/eventhub/stable/namespaces/get) | [get](/rest/api/relay/namespaces/get) |
| **ConnectionDetails-GetConnectionDetails**<br/>Service Bus/Event Hub/Relay GetConnectionDetals<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/ConnectionDetails``` | [listkeys](/rest/api/servicebus/stable/namespaces-authorization-rules/list-keys) | [listkeys](/rest/api/eventhub/stable/authorization-rules-event-hubs/list-keys) | [listkeys](/rest/api/relay/namespaces/listkeys) |
| **Topics-GetTopicsAsync**<br/>Service Bus<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/topics? $skip={skip}&$top={top}``` | [list](/rest/api/servicebus/stable/topics/listbynamespace) | &nbsp; | &nbsp; | 
| **Queues-GetQueueAsync** <br/>Service Bus<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/queues/{queueName}``` | [get](/rest/api/servicebus/stable/queues/get) | &nbsp; | &nbsp; | 
| **Relays-GetRelaysAsync**<br/>[Get Relays](/rest/api/servicebus/get-relays)<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/relays? $skip={skip}&$top={top}```| &nbsp; | &nbsp; | [list](/rest/api/relay/wcfrelays/listbynamespace) | 
| **NamespaceAuthorizationRules-GetNamespaceAuthorizationRuleAsync**<br/>Service Bus/Event Hub/Relay GetNamespaceAuthRule<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/authorizationrules?``` | [getauthorizationrule](/rest/api/servicebus/stable/namespaces-authorization-rules/get-authorization-rule) | [getauthorizationrule](/rest/api/eventhub/stable/authorization-rules-namespaces/get-authorization-rule) | [getauthorizationrule](/rest/api/relay/namespaces/getauthorizationrule) |
| **Namespaces-DeleteNamespaceAsync**<br/>[Service Bus Delete Namespace](/rest/api/servicebus/delete-namespace)<br/>[Event Hubs Delete Namespace](/rest/api/eventhub/delete-event-hub)<br/>[Relays Delete Namespace](/rest/api/servicebus/delete-namespace)<br/> ```DELETE	https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}``` | [delete](/rest/api/servicebus/stable/namespaces/delete) | [delete](/rest/api/eventhub/stable/namespaces/delete) | [delete](/rest/api/relay/namespaces/delete) | 
| **MessagingSKUPlan-GetPlanAsync**<br/>Service Bus/Event Hub/Relay Get Namespace<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/MessagingPlan``` | [get](/rest/api/servicebus/stable/namespaces/get) | [get](/rest/api/eventhub/stable/namespaces/get) | [get](/rest/api/relay/namespaces/get) |
| **MessagingSKUPlan-UpdatePlanAsync**<br/>Service Bus/Event Hub/Relay Get Namespace<br/>```PUT https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/MessagingPlan``` | [createorupdate](/rest/api/servicebus/stable/namespaces/createorupdate) | [createorupdate](/rest/api/eventhub/stable/namespaces/createorupdate) | [createorupdate](/rest/api/relay/namespaces/createorupdate) |
| **NamespaceAuthorizationRules-UpdateNamespaceAuthorizationRuleAsync**<br/>Service Bus/Event Hub/Relay Get Namespace<br/>```PUT https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/AuthorizationRules/{rule name}``` | [createorupdate](/rest/api/servicebus/stable/namespaces/createorupdate) | [createorupdateauthorizationrule](/rest/api/eventhub/stable/authorization-rules-event-hubs/create-or-update-authorization-rule) | [createorupdateauthorizationrule](/rest/api/relay/namespaces/createorupdateauthorizationrule) | 
| **NamespaceAuthorizationRules-CreateNamespaceAuthorizationRuleAsync**<br/> 
Service Bus/Event Hub/Relay<br/>```PUT https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/AuthorizationRules/{rule name}``` |[createorupdate](/rest/api/servicebus/stable/namespaces/createorupdate) | [createorupdateauthorizationrule](/rest/api/eventhub/stable/authorization-rules-event-hubs/create-or-update-authorization-rule) | [createorupdateauthorizationrule](/rest/api/relay/namespaces/createorupdateauthorizationrule) |
| **NamespaceProperties-GetNamespacePropertiesAsync**<br/>[Service Bus Get Namespace](/rest/api/servicebus/get-namespace)<br/>[Event Hubs Get Namespace](/rest/api/eventhub/get-event-hub)<br/>[Relay Get Namespace](/rest/api/servicebus/get-relays)<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}``` | [get](/rest/api/servicebus/stable/namespaces/get) | [get](/rest/api/eventhub/stable/namespaces/get) | [get](/rest/api/relay/namespaces/get) |
| **RegionCodes-GetRegionCodesAsync**<br/>Service Bus/EventHub/Relay Get Namespace<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}``` | &nbsp; | &nbsp; | &nbsp; | 
| **NamespaceProperties-UpdateNamespacePropertyAsync**<br/>Service Bus/EventHub/Relay<br/>```GET	https://management.core.windows.net/{subscription ID}/services/ServiceBus/Regions/``` | [createorupdate](/rest/api/servicebus/stable/namespaces/createorupdate) | [createorupdate](/rest/api/eventhub/stable/namespaces/createorupdate) | [createorupdate](/rest/api/relay/namespaces/createorupdate) |
| **EventHubsCrud-ListEventHubsAsync**<br/>[List Event Hubs](/rest/api/eventhub/list-event-hubs)<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/eventhubs?$skip={skip}&$top={top}``` | &nbsp; | [list](/rest/api/eventhub/preview/event-hubs/list-by-namespace) | &nbsp; | 
| **EventHubsCrud-GetEventHubAsync**<br/>[Get Event Hubs](/rest/api/eventhub/get-event-hub)<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/eventhubs/{eventHubPath}``` | &nbsp; | [get](/rest/api/eventhub/get-event-hub) | &nbsp; | 
| **NamespaceAuthorizationRules-DeleteNamespaceAuthorizationRuleAsync**<br/>Service Bus/Event Hub/Relay<br/>```DELETE https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/AuthorizationRules/{rule name}``` | [deleteauthorizationrule](/rest/api/servicebus/stable/namespaces-authorization-rules/delete-authorization-rule) | [deleteauthorizationrule](/rest/api/eventhub/stable/authorization-rules-namespaces/delete-authorization-rule) | [deleteauthorizationrule](/rest/api/relay/namespaces/deleteauthorizationrule) |
| **NamespaceAuthorizationRules-GetNamespaceAuthorizationRulesAsync**<br/>Service Bus/EventHub/Relay<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/AuthorizationRules``` | [listauthorizationrules](/rest/api/servicebus/stable/namespaces-authorization-rules/list-authorization-rules) | [listauthorizationrules](/rest/api/eventhub/stable/authorization-rules-namespaces/list-authorization-rules) | [listauthorizationrules](/rest/api/relay/namespaces/listauthorizationrules) |
| **NamespaceAvailability-IsNamespaceAvailable**<br/>[Service Bus Namespace Availability](/rest/api/servicebus/check-namespace-availability)<br/>```GET	https://management.core.windows.net/{subscription ID}/services/ServiceBus/CheckNamespaceAvailability/?namespace=<namespaceValue>``` | [checknameavailability](/rest/api/servicebus/stable/namespaces-check-name-availability/check-name-availability) | [checknameavailability](/rest/api/eventhub/stable/check-name-availability-namespaces/check-name-availability) | [checknameavailability](/rest/api/relay/namespaces/checknameavailability) |
| **Namespaces-CreateOrUpdateNamespaceAsync**<br/>Service Bus/Event Hub/Relay<br/>```PUT https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}``` | [createorupdate](/rest/api/servicebus/stable/namespaces/createorupdate) | [createorupdate](/rest/api/eventhub/stable/namespaces/createorupdate) | [createorupdate](/rest/api/relay/namespaces/createorupdate) | 
| **Topics-GetTopicAsync**<br/>```GET https://management.core.windows.net/{subscription ID}/services/ServiceBus/Namespaces/{namespace name}/topics/{topicPath}``` | [get](/rest/api/servicebus/stable/topics/get) | &nbsp; | &nbsp; |

## Service Manager PowerShell - Resource Manager PowerShell
| Service Manager PowerShell command (Deprecated) | New Resource Manager  Commands | Newer Resource Manager Command |
| ----- | ----- | ----- | 
| Get-AzureSBAuthorizationRule | [Get-AzureRmServiceBusAuthorizationRule](/powershell/module/azurerm.servicebus/get-azurermservicebusauthorizationrule) | [Get-AzServiceBusAuthorizationRule](/powershell/module/az.servicebus/get-azservicebusauthorizationrule) |
| Get-AzureSBLocation | [Get-AzureRmServiceBusGeoDRConfiguration](/powershell/module/azurerm.servicebus/get-azurermservicebusgeodrconfiguration) | [Get-AzServiceBusGeoDRConfiguration](/powershell/module/az.servicebus/get-azservicebusgeodrconfiguration) |
| Get-AzureSBNamespace | [Get-AzureRmServiceBusNamespace](/powershell/module/azurerm.servicebus/get-azurermservicebusnamespace) | [Get-AzServiceBusNamespace](/powershell/module/az.servicebus/get-azservicebusnamespace) |
| New-AzureSBAuthorizationRule | [New-AzureRmServiceBusAuthorizationRule](/powershell/module/azurerm.servicebus/new-azurermservicebusauthorizationrule) | [New-AzServiceBusAuthorizationRule](/powershell/module/az.servicebus/new-azservicebusauthorizationrule) |
| New-AzureSBNamespace | [New-AzureRmServiceBusNamespace](/powershell/module/azurerm.servicebus/new-azurermservicebusnamespace) | [New-AzServiceBusNamespace](/powershell/module/az.servicebus/new-azservicebusnamespace) |
| Remove-AzureSBAuthorizationRule | [Remove-AzureRmServiceBusAuthorizationRule](/powershell/module/azurerm.servicebus/remove-azurermservicebusauthorizationrule) | [Remove-AzServiceBusAuthorizationRule](/powershell/module/az.servicebus/remove-azservicebusauthorizationrule) |
| Remove-AzureSBNamespace | [Remove-AzureRmServiceBusNamespace](/powershell/module/azurerm.servicebus/remove-azurermservicebusnamespace) | [Remove-AzServiceBusNamespace](/powershell/module/az.servicebus/remove-azservicebusnamespace) |
| Set-AzureSBAuthorizationRule | [Set-AzureRmServiceBusAuthorizationRule](/powershell/module/azurerm.servicebus/set-azurermservicebusauthorizationrule) | [Set-AzServiceBusAuthorizationRule](/powershell/module/az.servicebus/set-azservicebusauthorizationrule) |

## Next steps
See the following documentation: 

- Latest REST API documentation
    - [Azure Service Bus](/rest/api/servicebus/)
    - [Azure Event Hubs](/rest/api/eventhub/)
    - [Azure Relay](/rest/api/relay/)
- Latest PowerShell documentation
    - [Azure Service Bus](/powershell/module/azurerm.servicebus/#service_bus)
    - [Azure Event Hubs](/powershell/module/azurerm.eventhub/#event_hub)
    - [Azure Event Grid](/powershell/module/azurerm.eventgrid/#event_grid)
