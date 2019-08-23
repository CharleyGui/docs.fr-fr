---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 678b1f71ac15d3ad30df28cec5abbe403fb08c95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937048"
---
# <a name="soapprocessing"></a>\<soapProcessing>

Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.

**\<system.ServiceModel>**    
&nbsp;&nbsp; **\<comportements >**    
&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointBehaviors>**    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<behavior>**    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<soapProcessing>**
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
  
Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|                   | Description |
| ----------------- | ----------- |
| `processMessages` | Valeur booléenne qui spécifie si les messages doivent être marshalés entre des versions de message SOAP. |

### <a name="child-elements"></a>Éléments enfants

Aucun

### <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [ **\<behavior>** ](behavior-of-endpointbehaviors.md) | Spécifie un comportement de point de terminaison. |

## <a name="remarks"></a>Notes

Le traitement SOAP est le processus par lequel les messages sont convertis entre des versions de message.

Le service de routage Windows Communication Foundation (WCF) peut convertir les messages d’un protocole à un autre. Si les versions des messages entrant et sortant sont différentes, un nouveau message est créé dans la version correcte. Le traitement des messages d'un <xref:System.ServiceModel.Channels.MessageVersion> à un autre est accompli en construisant un nouveau message WCF qui contient le corps et les en-têtes pertinents du message WCF entrant. Les en-têtes spécifiques à l'adressage ou reconnus au niveau du routeur ne sont pas utilisés pendant la création du nouveau message WCF car ils sont de versions différentes (dans le cas d'en-têtes d'adressage) ou ont été traités dans le cadre de la communication entre le client et le routeur.

Le placement d'un en-tête dans le message sortant dépend de son balisage comme étant compris au moment où il traverse la couche du canal entrant. Les en-têtes non reconnus (tels que les en-têtes personnalisés) ne sont pas supprimés et traversent donc le service de routage en étant copiés dans le message sortant. Le corps du message est copié dans le message sortant. Le message est ensuite envoyé via le canal de sortie ; les en-têtes et autres données d'enveloppe spécifiques à ce protocole de communication/transport sont alors créés et ajoutés.

Ces étapes de traitement s'exécutent lorsque le comportement de traitement SOAP est spécifié. [ Ce\<soapProcessingExtension >](soapprocessing.md) comportement est un comportement de point de terminaison qui est appliqué à tous les points de terminaison client (sortants) au démarrage du service de routage. par défaut, le comportement de [ \<> de routage](routing-of-servicebehavior.md) crée et attache un nouveau `processMessages` `true` [ \<comportement de > soapProcessingExtension](soapprocessing.md) avec la valeur pour chaque point de terminaison client. Si vous utilisez un protocole non reconnu par le service de routage ou souhaitez remplacer le comportement de traitement par défaut, vous pouvez désactiver le traitement SOAP pour l'intégralité du service de routage ou pour des points de terminaison particuliers.  Pour désactiver le traitement SOAP pour l’intégralité du service de routage sur tous les points `soapProcessing` de terminaison, affectez à `false`l’attribut [ \<](routing-of-servicebehavior.md) du comportement de > de routage la valeur. Pour désactiver le traitement SOAP pour un point de terminaison particulier, utilisez ce comportement et affectez à son attribut `processMessages` la valeur `false`, puis attachez ce comportement au point de terminaison au niveau duquel vous ne voulez pas exécuter le code de traitement par défaut.  Lorsque le comportement de [ \<> de routage](routing-of-servicebehavior.md) configure le service de routage, il ne réapplique pas le comportement du point de terminaison puisqu’il en existe déjà un.
