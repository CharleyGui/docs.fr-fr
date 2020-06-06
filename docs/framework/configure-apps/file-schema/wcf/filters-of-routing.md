---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855237"
---
# <a name="filters-of-routing"></a>\<filters> de \<routing>

Représente une section de configuration pour la définition d’un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants.

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucune

### <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [**\<filter>**](filter.md) | Contient un filtre de routage qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> sera utilisé lors de l’évaluation des messages entrants. |

### <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [**\<routing>**](routing.md) | Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtre correspond. |

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
