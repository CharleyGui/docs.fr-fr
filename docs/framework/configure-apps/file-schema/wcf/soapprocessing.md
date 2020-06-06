---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399537"
---
# \<soapProcessing>

Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
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

Aucune

### <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | Spécifie un comportement de point de terminaison. |

## <a name="remarks"></a>Remarques

Le traitement SOAP est le processus par lequel les messages sont convertis entre des versions de message.

Le service de routage Windows Communication Foundation (WCF) peut convertir les messages d’un protocole à un autre. Si les versions des messages entrant et sortant sont différentes, un nouveau message est créé dans la version correcte. Le traitement des messages d'un <xref:System.ServiceModel.Channels.MessageVersion> à un autre est accompli en construisant un nouveau message WCF qui contient le corps et les en-têtes pertinents du message WCF entrant. Les en-têtes spécifiques à l'adressage ou reconnus au niveau du routeur ne sont pas utilisés pendant la création du nouveau message WCF car ils sont de versions différentes (dans le cas d'en-têtes d'adressage) ou ont été traités dans le cadre de la communication entre le client et le routeur.

Le placement d'un en-tête dans le message sortant dépend de son balisage comme étant compris au moment où il traverse la couche du canal entrant. Les en-têtes non reconnus (tels que les en-têtes personnalisés) ne sont pas supprimés et traversent donc le service de routage en étant copiés dans le message sortant. Le corps du message est copié dans le message sortant. Le message est ensuite envoyé via le canal de sortie ; les en-têtes et autres données d'enveloppe spécifiques à ce protocole de communication/transport sont alors créés et ajoutés.

Ces étapes de traitement s'exécutent lorsque le comportement de traitement SOAP est spécifié. Ce [\<soapProcessingExtension>](soapprocessing.md) comportement est un comportement de point de terminaison qui est appliqué à tous les points de terminaison client (sortants) au démarrage du service de routage. par défaut, le [\<routing>](routing-of-servicebehavior.md) comportement crée et attache un nouveau [\<soapProcessingExtension>](soapprocessing.md) comportement avec ayant la `processMessages` valeur `true` pour chaque point de terminaison client. Si vous utilisez un protocole non reconnu par le service de routage ou souhaitez remplacer le comportement de traitement par défaut, vous pouvez désactiver le traitement SOAP pour l'intégralité du service de routage ou pour des points de terminaison particuliers.  Pour désactiver le traitement SOAP pour l’intégralité du service de routage sur tous les points de terminaison, affectez `soapProcessing` à l’attribut du comportement la valeur [\<routing>](routing-of-servicebehavior.md) `false` . Pour désactiver le traitement SOAP pour un point de terminaison particulier, utilisez ce comportement et affectez à son attribut `processMessages` la valeur `false`, puis attachez ce comportement au point de terminaison au niveau duquel vous ne voulez pas exécuter le code de traitement par défaut.  Lorsque le [\<routing>](routing-of-servicebehavior.md) comportement configure le service de routage, il ne réapplique pas le comportement du point de terminaison puisqu’il en existe déjà un.
