---
title: Attributs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: ff38cfdc228fd1eae1ace734ed2688c62c66499a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709554"
---
# <a name="attributes"></a>Attributs
<xref:System.Attribute?displayProperty=nameWithType> est une classe de base utilisée pour définir des attributs personnalisés.  
  
 Les attributs sont des annotations qui peuvent être ajoutées aux éléments de programmation tels que les assemblys, les types, les membres et les paramètres. Elles sont stockées dans les métadonnées de l’assembly et sont accessibles au moment de l’exécution à l’aide des API de réflexion. Par exemple, l’infrastructure définit le <xref:System.ObsoleteAttribute>, qui peut être appliqué à un type ou un membre pour indiquer que le type ou le membre a été déconseillé.  
  
 Les attributs peuvent avoir une ou plusieurs propriétés qui contiennent des données supplémentaires relatives à l’attribut. Par exemple, `ObsoleteAttribute` peut contenir des informations supplémentaires sur la version dans laquelle un type ou un membre a été déconseillé et la description des nouvelles API qui remplacent l’API obsolète.  
  
 Certaines propriétés d’un attribut doivent être spécifiées quand l’attribut est appliqué. Ils sont appelés propriétés requises ou arguments requis, car ils sont représentés en tant que paramètres de constructeur positionnel. Par exemple, la propriété <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> de la <xref:System.Diagnostics.ConditionalAttribute> est une propriété obligatoire.  
  
 Les propriétés qui n’ont pas nécessairement besoin d’être spécifiées lors de l’application de l’attribut sont appelées propriétés facultatives (ou arguments facultatifs). Elles sont représentées par des propriétés définissables. Les compilateurs fournissent une syntaxe spéciale pour définir ces propriétés lorsqu’un attribut est appliqué. Par exemple, la propriété <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> représente un argument facultatif.  
  
 **✓ DO** nommez des classes d’attributs personnalisés avec le suffixe « Attribut ».  
  
 **✓ DO** appliquer le <xref:System.AttributeUsageAttribute> à des attributs personnalisés.  
  
 **✓ DO** fournir les propriétés définissables pour les arguments facultatifs.  
  
 **✓ DO** fournissent des propriétés get uniquement pour les arguments requis.  
  
 **✓ DO** fournissent des paramètres du constructeur pour initialiser les propriétés qui correspondent aux arguments requis. Chaque paramètre doit avoir le même nom (mais avec une casse différente) que la propriété correspondante.  
  
 **X AVOID** fournissant les paramètres du constructeur pour initialiser les propriétés qui correspondent aux arguments facultatifs.  
  
 En d’autres termes, les propriétés ne peuvent pas être définies avec un constructeur et un accesseur Set. Cette recommandation rend très explicite les arguments facultatifs et obligatoires, et évite d’avoir deux façons de faire la même chose.  
  
 **X AVOID** surcharge des constructeurs d’attribut personnalisé.  
  
 Le fait de n’avoir qu’un seul constructeur communique clairement à l’utilisateur les arguments requis et ceux qui sont facultatifs.  
  
 **✓ DO** sceller des classes d’attributs personnalisés, si possible. La recherche de l’attribut est ainsi plus rapide.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
