---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854962"
---
# <a name="timeouts"></a>\<timeOuts>
Représente un élément de configuration qui spécifie l'intervalle de temps pendant lequel l'ouverture ou la fermeture de l'hôte de service est autorisée.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<services >** ](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de service**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’hôte**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Délais d’expiration >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`closeTimeout`|Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel la fermeture de l'hôte de service est autorisée.|  
|`openTimeout`|Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel l'ouverture de l'hôte de service est autorisée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<host>](host.md)|Élément de configuration qui spécifie des paramètres pour un hôte de service.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Hébergement](../../../wcf/feature-details/hosting.md)
