---
title: Attributs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 12a67d75a5f9642408cca69b2e3764a67f101549
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280580"
---
# <a name="attributes"></a>Attributs

<xref:System.Attribute?displayProperty=nameWithType>est une classe de base utilisée pour définir des attributs personnalisés.

 Les attributs sont des annotations qui peuvent être ajoutées aux éléments de programmation tels que les assemblys, les types, les membres et les paramètres. Elles sont stockées dans les métadonnées de l’assembly et sont accessibles au moment de l’exécution à l’aide des API de réflexion. Par exemple, .NET définit l' <xref:System.ObsoleteAttribute> attribut, qui peut être appliqué à un type ou un membre pour indiquer que le type ou le membre a été déconseillé.

 Les attributs peuvent avoir une ou plusieurs propriétés qui contiennent des données supplémentaires relatives à l’attribut. Par exemple, `ObsoleteAttribute` peut contenir des informations supplémentaires sur la version dans laquelle un type ou un membre a été déconseillé et une description de la nouvelle API qui remplace l’API obsolète.

 Certaines propriétés d’un attribut doivent être spécifiées quand l’attribut est appliqué. Ils sont appelés propriétés requises ou arguments requis, car ils sont représentés en tant que paramètres de constructeur positionnel. Par exemple, la <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> propriété de <xref:System.Diagnostics.ConditionalAttribute> est une propriété obligatoire.

 Les propriétés qui n’ont pas nécessairement besoin d’être spécifiées lors de l’application de l’attribut sont appelées propriétés facultatives (ou arguments facultatifs). Elles sont représentées par des propriétés définissables. Les compilateurs fournissent une syntaxe spéciale pour définir ces propriétés lorsqu’un attribut est appliqué. Par exemple, la <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriété représente un argument facultatif.

 ✔️ Nommez les classes d’attributs personnalisés avec le suffixe « Attribute ».

 ✔️ appliquez à des <xref:System.AttributeUsageAttribute> attributs personnalisés.

 ✔️ fournissez des propriétés définissables pour les arguments facultatifs.

 ✔️ fournissez des propriétés d’extraction uniquement pour les arguments requis.

 ✔️ fournissez des paramètres de constructeur pour initialiser les propriétés correspondant aux arguments requis. Chaque paramètre doit avoir le même nom (mais avec une casse différente) que la propriété correspondante.

 ❌Évitez de fournir des paramètres de constructeur pour initialiser les propriétés correspondant aux arguments facultatifs.

 En d’autres termes, les propriétés ne peuvent pas être définies avec un constructeur et un accesseur Set. Cette recommandation rend très explicite les arguments facultatifs et obligatoires, et évite d’avoir deux façons de faire la même chose.

 ❌Évitez de surcharger les constructeurs d’attributs personnalisés.

 Le fait de n’avoir qu’un seul constructeur communique clairement à l’utilisateur les arguments requis et ceux qui sont facultatifs.

 ✔️ scellent les classes d’attributs personnalisés, si possible. La recherche de l’attribut est ainsi plus rapide.

 *Parties &copy; 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions d’utilisation](usage-guidelines.md)
