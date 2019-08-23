---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: e7e82117304ac133e5e84c0fc36b987560bcef96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933809"
---
# <a name="pnrppeerresolver"></a>\<pnrpPeerResolver>
Spécifie que le programme de résolution PNRP (Peer Name Resolution Protocol) doit être utilisé comme un programme de résolution. Cet élément est facultatif parce que PNRP est le programme de résolution par défaut.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<pnrpResolver>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|resolverType|Chaîne qui spécifie le programme de résolution à utiliser. Cet attribut est facultatif. S'il n'est pas défini ou s'il a pour valeur une chaîne vide, PNRP est utilisé.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="example"></a>Exemples  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Programmes de résolution d’homologue](../../../wcf/feature-details/peer-resolvers.md)
