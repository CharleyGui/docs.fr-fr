---
title: Éléments de directive runtime
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb3ad0d39d47297b7d26a5c28cfbbc269ce99e44
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052412"
---
# <a name="runtime-directive-elements"></a>Éléments de directive runtime
Le format du fichier de directives runtime (rd.xml) prend en charge les éléments de directive runtime suivants. Pour voir une représentation hiérarchique, consultez [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md)  
 Applique la stratégie de réflexion runtime à tous les types utilisés par l'application et sert de conteneur pour les types à l'échelle de l'application et pour les membres de type dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution. Il s’agit d’un enfant de l’élément [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md).  
  
 [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Applique la stratégie runtime à tous les types dans un assembly. Il s’agit d’un enfant des éléments [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) et [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Si sa directive [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) conteneur est un attribut, applique la stratégie runtime aux éléments de code auxquels cet attribut est appliqué.  
  
 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md)  
 L’élément racine dans chaque fichier de directives runtime pour .NET Native. Ses éléments enfants sont [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) et [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Event>](../../../docs/framework/net-native/event-element-net-native.md)  
 Applique la stratégie runtime à un événement. Il s’agit d’un enfant des éléments [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) et [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Field>](../../../docs/framework/net-native/field-element-net-native.md)  
 Applique la stratégie runtime à un champ. Il s’agit d’un enfant des éléments [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) et [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Applique la stratégie runtime au type de paramètre d'un type ou d'une méthode générique.  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 Applique la stratégie runtime à un type, si cette stratégie a été appliquée à la méthode ou au type conteneur.  
  
 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)  
 Applique la stratégie runtime à tous les types dans un assembly. Il s’agit d’un enfant des éléments [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) et [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Method>](../../../docs/framework/net-native/method-element-net-native.md)  
 Applique la stratégie runtime à une méthode. Il s’agit d’un enfant des éléments [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) et [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Applique la stratégie runtime à une méthode générique construite. Il s’agit d’un enfant des éléments [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) et [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Applique la stratégie runtime à tous les types d'un espace de noms.  
  
 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Applique la stratégie runtime au type de l’argument passé à une méthode.  
  
 [\<Property>](../../../docs/framework/net-native/property-element-net-native.md)  
 Applique la stratégie runtime à une propriété. Il s’agit d’un enfant des éléments [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) et [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Applique la stratégie runtime à toutes les classes héritées du type conteneur.  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 Applique la stratégie runtime à un type.  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Applique la stratégie runtime à un type générique construit.  
  
 [\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Applique la stratégie runtime au type représenté par un argument <xref:System.Type> passé à une méthode.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de référence du fichier de configuration rd.xml](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
