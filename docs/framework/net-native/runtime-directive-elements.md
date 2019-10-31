---
title: Éléments de directive runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128171"
---
# <a name="runtime-directive-elements"></a>Éléments de directive runtime
Le format du fichier de directives runtime (rd.xml) prend en charge les éléments de directive runtime suivants. Pour voir une représentation hiérarchique, consultez [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
 [\<Application>](application-element-net-native.md)  
 Applique la stratégie de réflexion runtime à tous les types utilisés par l'application et sert de conteneur pour les types à l'échelle de l'application et pour les membres de type dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. Il s’agit d’un enfant de l’élément [\<Directives>](directives-element-net-native.md).  
  
 [\<Assembly>](assembly-element-net-native.md)  
 Applique la stratégie runtime à tous les types dans un assembly. Il s’agit d’un enfant des éléments [\<Application>](application-element-net-native.md) et [\<Library>](library-element-net-native.md).  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 Si sa directive [\<Type>](type-element-net-native.md) conteneur est un attribut, applique la stratégie runtime aux éléments de code auxquels cet attribut est appliqué.  
  
 [\<Directives>](directives-element-net-native.md)  
 Élément racine dans chaque fichier de directives Runtime pour .NET Native. Ses éléments enfants sont [\<Application>](application-element-net-native.md) et [\<Library>](library-element-net-native.md).  
  
 [\<Event>](event-element-net-native.md)  
 Applique la stratégie runtime à un événement. Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<Field>](field-element-net-native.md)  
 Applique la stratégie runtime à un champ. Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 Applique la stratégie runtime au type de paramètre d'un type ou d'une méthode générique.  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 Applique la stratégie runtime à un type, si cette stratégie a été appliquée à la méthode ou au type conteneur.  
  
 [\<Library>](library-element-net-native.md)  
 Applique la stratégie runtime à tous les types dans un assembly. Il s’agit d’un enfant des éléments [\<Application>](application-element-net-native.md) et [\<Library>](library-element-net-native.md).  
  
 [\<Method>](method-element-net-native.md)  
 Applique la stratégie runtime à une méthode. Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 Applique la stratégie runtime à une méthode générique construite. Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<Namespace>](namespace-element-net-native.md)  
 Applique la stratégie runtime à tous les types d'un espace de noms.  
  
 [\<Parameter>](parameter-element-net-native.md)  
 Applique la stratégie runtime au type de l’argument passé à une méthode.  
  
 [\<Property>](property-element-net-native.md)  
 Applique la stratégie runtime à une propriété. Il s’agit d’un enfant des éléments [\<Type>](type-element-net-native.md) et [\<TypeInstantiation>](typeinstantiation-element-net-native.md).  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 Applique la stratégie runtime à toutes les classes héritées du type conteneur.  
  
 [\<Type>](type-element-net-native.md)  
 Applique la stratégie runtime à un type.  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 Applique la stratégie runtime à un type générique construit.  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 Applique la stratégie runtime au type représenté par un argument <xref:System.Type> passé à une méthode.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration rd.xml](runtime-directives-rd-xml-configuration-file-reference.md)
