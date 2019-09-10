---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855095"
---
# <a name="namespacetable"></a>\<namespaceTable>

Représente une section de configuration qui permet de définir un ensemble d’éléments contenant des mappages espace de noms-préfixe qui peuvent ensuite être utilisés dans des filtres XPath pour le routage.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun

### <a name="child-elements"></a>Éléments enfants

|     | Description |
| --- | ----------- |
| [ **\<filter>** ](filter.md) | Définit un mappage préfixe-espace de noms utilisé pour les expressions XPath. |

### <a name="parent-elements"></a>Éléments parents

|     | Description |
| --- | ----------- |
| [ **\<routing>** ](routing.md) | Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond. |

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
