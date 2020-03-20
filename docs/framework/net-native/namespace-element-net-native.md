---
title: <Namespace>Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
ms.openlocfilehash: 06d88a7b0f95c7c1dbe98818b847c92e08a57a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180954"
---
# <a name="namespace-element-net-native"></a>\<Namespace> Element (.NET Native)
Applique la stratégie de réflexion runtime à tous les types dans un espace de noms spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Namespace Name="namespace_name"
           Activate="policy_type"
           Browse="policy_type"  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Spécifie le nom de l'espace de noms.|  
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.|  
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Stratégie de contrôles pour le marshaling de structures en code natif.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*namespace_name*|L'espace de noms. Si \<l’élément Namespace> est un [ \< ](application-element-net-native.md)enfant d’une [ \< ](library-element-net-native.md)application>, bibliothèque>, ou [ \<l’élément>d’assemblage,](assembly-element-net-native.md) *namespace_name* doit être un nom de nom entièrement qualifié. Si l’élément \<Namespace> est un enfant d’un autre élément \<Namespace>, *nom_espace_de_noms* doit être un nom d’espace de noms relatif.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Le paramètre s'applique à ce type de stratégie pour tous les types dans l'espace de noms. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`<Namespace>`|Applique la stratégie de réflexion runtime à tous les types dans un espace de noms parent.|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie de réflexion à un type.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<>d’application](application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. [ \<L’élément>d’application](application-element-net-native.md) peut avoir zéro, un ou plusieurs [ \<éléments>d’assemblage.](assembly-element-net-native.md)|  
|[\<>de l’Assemblée](assembly-element-net-native.md)|Applique la stratégie de réflexion runtime à tous les types dans un assembly spécifié.|  
|[\<>de bibliothèque](library-element-net-native.md)|Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. [ \<L’élément>bibliothèque](library-element-net-native.md) peut avoir zéro ou un [ \<élément>d’assemblage.](assembly-element-net-native.md)|  
|`<Namespace>`|Applique la stratégie de réflexion à tous les types dans un espace de noms parent.|  
  
## <a name="remarks"></a>Notes   
 Les attributs `Activate`, `Browse`, `Dynamic` et `Serialize` sont tous facultatifs. Si aucun n'est présent, l'élément `<Namespace>` sert uniquement de conteneur pour les éléments enfants. S'ils sont présents, l'élément `<Namespace>` applique la stratégie de réflexion runtime à tous les types dans l'espace de noms spécifié.  
  
 Lorsqu’il s’agit d’un enfant de `<Namespace>` [ \<l’Assemblée>](assembly-element-net-native.md) élément, l’élément l’emporte sur la politique de réflexion sur le temps d’exécution définie par [ \<l’Assemblée>](assembly-element-net-native.md) élément.  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md)
- [Informations de référence sur le fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
