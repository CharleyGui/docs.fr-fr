---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: fb974492dee6b2a4244cedc06e3f5e40334dd02a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399983"
---
# <a name="resolver"></a>\<resolver>
Spécifie un programme de résolution d'homologue utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds d'homologues représentant plusieurs nœuds faisant partie de la maille.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> du programme de résolution**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`mode`|Chaîne qui spécifie si l'instance du programme de résolution d'homologue associée à ce service est spécifique au PNRP, à un programme de résolution personnalisé ou si elle est déterminée automatiquement. Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.|  
|`referralPolicy`|Chaîne qui spécifie la manière dont les références sont partagées parmi des homologues. Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Définit toutes les fonctions de liaison de l' [ \<> NetPeerTcpBinding](netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Notes  
 Un programme de résolution de nom d'homologue est un service de découverte utilisé par les canaux homologues afin de rechercher des nœuds d'homologues faisant partie d'une maille d'homologues. Il est également utilisé pour « inscrire » un nœud avec un maillage d'homologue, le mécanisme par lequel le nœud homologue est connu et disponible à partir du maillage d'homologue. Pour plus d’informations sur les programmes de résolution d’homologue, consultez programmes de [résolution d’homologue](../../../wcf/feature-details/peer-resolvers.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [Programmes de résolution d’homologue](../../../wcf/feature-details/peer-resolvers.md)
- [Ajout d’un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
