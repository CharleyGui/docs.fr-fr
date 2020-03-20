---
title: <behavior>de <serviceBehaviors> flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152318"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<comportement> de \<serviceBehaviors> de flux de travail
**L’élément comportemental** contient une collection de paramètres pour le comportement d’un service. Chaque comportement est indexé par son **nom**. Les services peuvent se lier à chaque comportement à travers ce nom en utilisant l’attribut **de comportementconfiguration** du point de [ \<terminaison>](../wcf/endpoint-element.md) élément. Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Système. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportements>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comportement>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan"
                           leaseTimeout="TimeSpan"
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String"
                                  hostLockRenewalPeriod="TimeSpan"
                                  instanceCompletionAction="DeleteNothing/DeleteAll"
                                  instanceEncodingAction="None/GZip"
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan"
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne unique qui contient le nom de configuration du comportement. Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<>tamponReceive](bufferreceive.md)|Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.|  
|[\<routage>](../wcf/routing-of-servicebehavior.md)|Comportement de service qui permet à un service d'utiliser le suivi ETW à l'aide d'un objet  <xref:System.Activities.Tracking.EtwTrackingParticipant>.|  
|[\<envoyerMessageChannelCache>](sendmessagechannelcache.md)|Comportement de service qui permet de personnaliser les niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux, pour les flux de travail qui envoient des messages aux points de terminaison de service par le biais d'activités de messagerie Send.|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|Comportement de service qui vous permet de configurer la fonctionnalité <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, qui prend en charge les informations d'état persistantes pour les instances de service du flux de travail dans une base de données SQL Server 2005 ou SQL Server 2008.|  
|[\<workflowIdle>](workflowidle.md)|Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|Collection d’éléments de comportement de service.|
