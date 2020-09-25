---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 2ef674dc8601bc9afaf6b547265988bb8a99f943
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170166"
---
# \<parameter>

Indique le paramètre générique lorsqu'un type déclaré est générique.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|index|Lorsque le type déclaré est générique, spécifie le paramètre générique qui renverra le type connu.|  
|type|Chaîne décrivant le type connu utilisé pour la sérialisation et la désérialisation.|  
  
## <a name="index-attribute"></a>Indexer l'Attribut  
  
|Valeur|Description|  
|-----------|-----------------|  
|"0"|Premier paramètre du type générique. Par exemple, <xref:System.Collections.Generic.List%601> dispose d'un seul paramètre. S'il est utilisé comme type déclaré, l'index a la valeur « 0 ».|  
|"1"|Second paramètre d'un type générique. Par exemple, <xref:System.Collections.Generic.Dictionary%602> dispose de deux paramètres. Si le type connu est renvoyé par le second paramètre, affectez à l'attribut d'index la valeur « 1 ».|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|Spécifie un type connu pouvant être renvoyé par un champ ou une propriété du type déclaré.|  
  
## <a name="remarks"></a>Notes  

 Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)Pour obtenir un exemple d’utilisation de cet élément, consultez.  
  
 Cet élément de configuration ne peut pas contenir les deux attributs simultanément. Si c'est le cas, un <xref:System.Configuration.ConfigurationErrorsException> survient.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Types connus de contrats de données](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
