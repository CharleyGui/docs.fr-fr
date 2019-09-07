---
title: <behavior>de <serviceBehaviors> Workflow
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 65bde45ffdd4af166d5b44308162c23257659802
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398888"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<> de comportement \<de la > serviceBehaviors du flux de travail
L’élément **Behavior** contient une collection de paramètres pour le comportement d’un service. Chaque comportement est indexé par son **nom**. Les services peuvent être liés à chaque comportement via ce nom à l’aide de l’attribut **behaviorConfiguration** de l' [ \<élément de point de terminaison >](../wcf/endpoint-element.md) . Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de comportement**  
  
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
|[\<bufferReceive>](bufferreceive.md)|Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|Comportement de service qui permet à un service d’utiliser le suivi ETW <xref:System.Activities.Tracking.EtwTrackingParticipant>à l’aide d’un.|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|Comportement de service qui permet la personnalisation des niveaux de partage du cache, les paramètres du cache de la fabrique de canaux et les paramètres du cache de canaux pour les flux de travail qui envoient des messages aux points de terminaison de service à l’aide d’activités de messagerie d’envoi.|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|Comportement de service qui vous permet de configurer la <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> fonctionnalité, qui prend en charge la persistance des informations d’État pour les instances de service de workflow dans une base de données SQL Server 2005 ou SQL Server 2008.|  
|[\<workflowIdle>](workflowidle.md)|Comportement de service qui contrôle à quel moment les instances de workflow inactives sont déchargées et rendues persistantes.|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|Comportement de service qui vous permet de spécifier des paramètres qui contrôlent le mode d'exécution des instances de flux de travail, notamment la persistance, le comportement d'exception non prise en charge et le comportement inactif.|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|Comportement de service qui vous permet de spécifier l'action à exécuter lorsqu'une exception non prise en charge est levée dans un service de workflow.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|Collection d’éléments de comportement de service.|
