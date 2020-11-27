---
title: <Assembly> , Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
ms.openlocfilehash: 9d1556d8d414386d3f350a96396381bd7b66ffc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251124"
---
# <a name="assembly-element-net-native"></a>\<Assembly> , Élément (.NET Native)

Applique la stratégie de réflexion runtime à tous les types dans un assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Assembly Name="assembly_name"
          Activate="policy_setting"  
          Browse="policy_setting"  
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
|`Name`|Général|Attribut requis. Spécifie le nom simple d'un assembly.|  
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les types dans l'assembly ou l'énumération de ceux-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.|  
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
|*assembly_name*|Nom simple de l’assembly, sans son extension de fichier. Cet attribut correspond à la propriété <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>. Par exemple, le nom d’un assembly nommé Extensions.dll est « Extensions ».<br /><br /> Vous pouvez également spécifier la chaîne littérale `*Application*` pour appliquer la stratégie à tous les assemblys dans votre package d'application, que ces assemblys soient chargés ou non. `*Application*` n'applique jamais la stratégie aux assemblys .NET Framework.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Le paramètre s'applique à ce type de stratégie pour tous les types dans l'assembly. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Namespace>](namespace-element-net-native.md)|Applique la stratégie de réflexion à tous les types dans un espace de noms enfant.|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie de réflexion à un type.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. L' [\<Application>](application-element-net-native.md) élément peut avoir zéro, un ou plusieurs `<Assembly>` éléments.|  
|[\<Library>](library-element-net-native.md)|Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. L' [\<Library>](library-element-net-native.md) élément peut avoir zéro ou un `<Assembly>` élément.|  
  
## <a name="remarks"></a>Notes  

 L'élément `<Assembly>` définit la stratégie runtime pour tous les types dans un assembly. Il diffère de l' [\<Library>](library-element-net-native.md) élément, qui spécifie une bibliothèque, mais qui dépend de ses éléments enfants pour définir la stratégie de réflexion du Runtime. L'élément `<Assembly>` s'applique à tous les types dans un assembly, sauf si elles sont remplacées par un élément enfant.  
  
 L’exemple suivant montre comment vous pouvez appliquer une stratégie runtime à tous les types dans les assemblys au sein de votre package d’application en affectant la valeur « *Application\* » à l’attribut `Name`. L' `<Assembly>` élément doit être un enfant de l' [\<Application>](application-element-net-native.md) élément.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>  
```  
  
 Les attributs `Activate`, `Browse`, `Dynamic` et `Serialize` sont tous facultatifs. Toutefois, l'élément `<Assembly>` doit contenir au moins un de ces attributs.  
  
## <a name="see-also"></a>Voir aussi

- [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
