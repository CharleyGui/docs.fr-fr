---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399460"
---
# <a name="systemruntimeserialization"></a>\<system.runtime.serialization>
Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp; **\<System. Runtime. Serialization >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|Active l'ajout de types connus à utiliser lors de la désérialisation.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>, élément](../configuration-element.md)|Élément de niveau supérieur de la configuration.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization>
- [Utilisation de contrats de données](../../../wcf/feature-details/using-data-contracts.md)
- [Types connus de contrats de données](../../../wcf/feature-details/data-contract-known-types.md)
 