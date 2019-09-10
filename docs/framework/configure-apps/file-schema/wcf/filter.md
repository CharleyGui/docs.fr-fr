---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855259"
---
# <a name="filter"></a>\<filter>

Définit un filtre de routage qui détermine le type de Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les données de prise en charge ou les paramètres requis par le filtre.

[ **\<system.serviceModel>** ](system-servicemodel.md)\
&nbsp;&nbsp;[ **\<routing>** ](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtres >** ](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtre >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

| Attribut  | Description |
| ---------- | ----------- |
| customType | Chaîne qui contient le nom qualifié complet du type personnalisé à utiliser comme filtre. Si `filterType` a la `custom`valeur, cet attribut contient le nom de type qualifié complet de la classe à créer.  `filterData`peut également contenir des valeurs à utiliser pendant l’évaluation du filtre de type personnalisé. |
| filterData | Chaîne qui contient la données de filtre. Pour plus d'informations sur la spécification de cet attribut, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Chaîne qui contient le type de filtre. Cet attribut est de type <xref:System.ServiceModel.Routing.Configuration.FilterType>.  Pour plus d'informations sur l'utilisation de cet attribut avec l'attribut `filterData`, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Chaîne qui contient le nom unique de cet élément de filtre. |

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| ------- | ----------- |
| [\<routing>](routing.md) | Section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (<xref:System.ServiceModel.Dispatcher.MessageFilter> WCF) à utiliser lors de l’évaluation des messages entrants. |

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
