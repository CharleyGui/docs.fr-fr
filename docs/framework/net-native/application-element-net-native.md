---
title: <Application> , Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
ms.openlocfilehash: a7f2eca5a5bb5cfb7b9827f2463454a17fc128cb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288136"
---
# <a name="application-element-net-native"></a>\<Application> , Élément (.NET Native)

Sert de conteneur pour les types à l'échelle de l'application et pour les membres de type dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution, et applique la stratégie de réflexion runtime à tous les éléments de programme dans une application.  
  
 Élément \<Directives>  
\<Application> , Élément (rd.xml)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Application Activate="policy_setting"  
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

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents. Dans le tableau Éléments enfants, la stratégie fait référence au type de métadonnées rendues disponibles pour des éléments de programme spécifiques au moment de l'exécution.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les types ou l'énumération de ceux-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.|  
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Stratégie de contrôles pour le marshaling de structures en code natif.|  
  
## <a name="all-attributes"></a>Tous les attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre de cette stratégie à appliquer aux types dans l'application. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|Applique la stratégie à tous les types d'un assembly particulier.|  
|[\<Namespace>](namespace-element-net-native.md)|Applique la stratégie à tous les types d'un espace de noms particulier.|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie à un type particulier, tel qu'une classe ou une structure.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie à un type générique construit. Par exemple, un [\<TypeInstantiation>](typeinstantiation-element-net-native.md) élément peut être utilisé pour définir la stratégie d’un `List<String>` type.|  
|[\<Method>](method-element-net-native.md)|Applique la stratégie à une méthode sur un type particulier.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Applique la stratégie à une méthode générique construite.|  
|[\<Property>](property-element-net-native.md)|Applique la stratégie à une propriété sur un type particulier.|  
|[\<Field>](field-element-net-native.md)|Applique la stratégie à un champ sur un type particulier.|  
|[\<Event>](event-element-net-native.md)|Applique la stratégie à un événement sur un type particulier.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|Élément racine d'un fichier de directives de runtime.|  
  
## <a name="remarks"></a>Notes  

 L' [\<Directives>](directives-element-net-native.md) élément peut contenir zéro ou un `<Application>` élément. Un même fichier de directives de réflexion ne peut pas contenir plusieurs éléments `<Application>`.  
  
 Un élément `<Application>` peut être utilisé de deux manières différentes :  
  
- En tant que conteneur pour définir des éléments de programme dont les métadonnées sont nécessaires au moment de l'exécution. Dans ce cas, l'élément `<Application>` n'a pas besoin d'attributs. Au moment de la compilation, les outils du compilateur recherchent dans toutes les bibliothèques, y compris les bibliothèques principales du .NET Framework, les éléments de programme identifiés par les éléments enfants de l'élément `<Application>`. En revanche, les outils du compilateur recherchent uniquement la bibliothèque désignée par l' [\<Library>](library-element-net-native.md) élément pour les éléments de programme identifiés par les éléments enfants de [\<Library>](library-element-net-native.md) .  
  
- En tant qu'élément qui définit la stratégie à l'échelle de l'application pour la réflexion, la sérialisation et l'interopérabilité. Les attributs de l' `<Application>` élément définissent la stratégie au niveau de l’application, qui peut être substituée par les éléments enfants définis par l' `<Application>` [\<Library>](library-element-net-native.md) élément ou.  
  
## <a name="see-also"></a>Voir aussi

- [\<Library> Appartient](library-element-net-native.md)
- [\<Directives> Appartient](directives-element-net-native.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
