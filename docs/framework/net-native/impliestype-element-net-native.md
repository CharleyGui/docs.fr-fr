---
title: <ImpliesType>Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181013"
---
# <a name="impliestype-element-net-native"></a>\<ImpliesType> Element (.NET Native)
Applique la stratégie à un type, si cette stratégie a été appliquée à la méthode ou au type conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
             Browse="policy_type"  
             Dynamic="policy_type"  
             Serialize="policy_type"
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
|`Name`|Général|Attribut requis. Spécifie le nom du type.|  
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.|  
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*type_name*|Nom du type. Si le type représenté par cet élément `<ImpliesType>` se trouve dans le même espace de noms que son élément `<Type>` conteneur, *type_name* peut inclure le nom du type sans son espace de noms. Dans le cas contraire, *type_name* doit inclure le nom de type complet.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
|[\<Méthode>](method-element-net-native.md)|Applique la stratégie de réflexion à une méthode.|  
  
## <a name="remarks"></a>Notes   
 L'élément `<ImpliesType>` est essentiellement conçu pour une utilisation par des bibliothèques. Il traite le scénario suivant :  
  
- Si une routine a besoin de réfléchir un type, elle doit nécessairement réfléchir un second type.  
  
- Sinon, les métadonnées de l'instanciation implicite du second type sont indisponibles, car l'analyse statique n'indique pas qu'elles sont nécessaires.  
  
 En règle générale, les deux types sont des instanciations génériques partageant des arguments de type.  
  
 L'élément `<ImpliesType>` a été défini en partant du principe que la nécessité de réfléchir le type spécifié par son élément parent implique la nécessité de réfléchir le type spécifié par l'élément `<ImpliesType>`. Par exemple, les directives de réflexion suivantes s'appliquent aux deux types `Explicit<T>` et `Implicit<T>`.  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 Cette directive n'a d'effet que si une instanciation d'`Explicit` possède un paramètre de stratégie `Dynamic` défini. Par exemple, si c'est le cas pour `Explicit<Int32>`, `Implicit<Int32>` est instancié avec ses membres publics associés à une racine, et leurs métadonnées sont accessibles pour une programmation dynamique.  
  
 Voici un exemple concret qui s'applique à au moins un sérialiseur. Les directives saisissent l’exigence selon `IList<`laquelle la réflexion sur quelque chose dactylographie comme *quelque chose* `>` consiste également à réfléchir sur le type `List<` *de quelque chose* `>` correspondant sans exiger aucune annotation par application.  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 L'élément `<ImpliesType>` peut également apparaître dans un élément `<Method>`, car dans certains cas l'instanciation d'une méthode générique implique la réflexion d'une instanciation de type. Par exemple, imaginez une méthode générique `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` à laquelle une bibliothèque donnée accède dynamiquement, ainsi qu’aux types <xref:System.Collections.Generic.List%601> et <xref:System.Array> associés. Cela peut être exprimé sous la forme :  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
- [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md)
