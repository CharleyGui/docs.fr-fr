---
title: <synchronousReceive> (élément)
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 2073d115dd87d513a6e48b8b585fed4b49d5bb32
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157172"
---
# <a name="synchronousreceive-element"></a>\<synchronousReceive>, élément

Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service. Il n'a aucun attribut ou élément enfant.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## <a name="remarks"></a>Notes  

 Utilisez ce comportement pour indiquer à l'écouteur de canal d'utiliser une réception synchrone au lieu de celle par défaut (asynchrone). Windows Communication Foundation (WCF) émet un nouveau thread pour pomper chaque canal accepté. Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
