---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400463"
---
# \<custom>
Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`address`|URI indiquant l'adresse de point de terminaison du nœud homologue qui héberge le service de programme de résolution d'homologue personnalisé.|  
|`resolverType`|Chaîne contenant le type du service de programme de résolution d'homologue personnalisé.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Indique l'identité des programmes de résolution d'homologue personnalisés configurés avec cet élément. Cet élément est de type <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<headers>](headers-element.md)|Collection d’en-têtes d’adresse utilisée pour les messages SOAP gérés par le programme de résolution d’homologue personnalisé.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|Un programme de résolution d'homologue est utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds homologues représentant plusieurs nœuds faisant partie de la maille.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément définit les paramètres de base pour un service de programme de résolution d'homologue personnalisé, y compris l'adresse de point de terminaison de l'homologue qui héberge le service et tous les paramètres de liaison spécifiques. Pour plus d’informations sur la création d’un programme de résolution personnalisé, consultez [Ajout d’un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [Programmes de résolution d'homologue](../../../wcf/feature-details/peer-resolvers.md)
- [Ajout d'un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
