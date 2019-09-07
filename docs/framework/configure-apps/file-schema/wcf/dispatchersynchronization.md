---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397999"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization>
  
Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dispatcherSynchronization >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>Type  
  
`Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
  
Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs

| Attribut               | Description       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | Valeur booléenne qui indique si un comportement d'envoi asynchrone est activé. |
| `maxPendingReceives`    | Entier qui spécifie le nombre de réceptions simultanées qui peuvent être émises sur le canal.<br /><br /> Cette valeur doit être configurée uniquement après avoir correctement configuré le comportement de limitation de service. |

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison. |

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
