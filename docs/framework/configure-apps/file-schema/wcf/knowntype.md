---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397873"
---
# <a name="knowntype"></a>\<knownType>
Indique un type devant être utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation. L'élément indique un « type connu » renvoyé par un champ ou une propriété d'un « type déclaré ». Pour plus d’informations, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownType >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a>Type  
 `string`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|type|Indique le type (espace de noms compris), le nom de l'assembly, la version, la culture et le jeton de clé publique.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|Indique un index de paramètre lorsque le type déclaré est générique.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|Ajoute un type déclaré à la collection de types déclarés.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les types connus, consultez [types connus](../../../wcf/feature-details/data-contract-known-types.md) de <xref:System.Runtime.Serialization.DataContractSerializer>contrat de données et.  
  
 Pour obtenir un exemple d’utilisation de cet élément, consultez la [ \<> DataContractSerializer](datacontractserializer-element.md) .  
  
## <a name="example"></a>Exemple  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Types connus de contrats de données](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
