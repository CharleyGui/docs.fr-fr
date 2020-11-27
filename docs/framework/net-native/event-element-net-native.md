---
title: <Event> , Élément (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: b1cf2239e58839c5026bc375ba04568227881bdd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288097"
---
# <a name="event-element-net-native"></a>\<Event> , Élément (.NET Native)

Applique la stratégie de réflexion runtime à un événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Spécifie le nom de l'événement.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur l'événement ou l'énumération de celui-ci, mais ne permet pas d'effectuer un accès dynamique au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'événement au moment de l'exécution pour autoriser la programmation dynamique. Cette stratégie garantit qu'un événement peut être géré dynamiquement au moment de l'exécution.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*method_name*|Nom de l'événement. Le type de l’événement est défini par l' [\<Type>](type-element-net-native.md) élément parent ou [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*policy_setting*|Paramètre à appliquer à ce type de stratégie pour l'événement. Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Notes  

 Si la stratégie d'un événement n'est pas définie explicitement, elle hérite la stratégie runtime de son élément parent.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](runtime-directive-elements.md)
- [Paramètres de stratégie de directive runtime](runtime-directive-policy-settings.md)
