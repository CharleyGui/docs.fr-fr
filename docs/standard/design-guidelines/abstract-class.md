---
title: Conception de classes abstraites
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 19482199648a8fb9c4b2c796fb1ab5d62c896abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709593"
---
# <a name="abstract-class-design"></a>Conception de classes abstraites
**X DO NOT** définir des constructeurs internes publiques ou protégées dans les types abstraits.  
  
 Les constructeurs doivent être publics uniquement si les utilisateurs doivent créer des instances du type. Étant donné que vous ne pouvez pas créer d’instances d’un type abstrait, un type abstrait avec un constructeur public n’est pas correctement conçu et trompe les utilisateurs.  
  
 **✓ DO** définir un document protégé ou un constructeur interne dans les classes abstraites.  
  
 Un constructeur protégé est plus courant et permet simplement à la classe de base d’effectuer sa propre initialisation lors de la création de sous-types.  
  
 Un constructeur interne peut être utilisé pour limiter les implémentations concrètes de la classe abstraite à l’assembly qui définit la classe.  
  
 **✓ DO** fournir au moins un type concret qui hérite de chaque classe abstraite qui vous sont fournis.  
  
 Cela permet de valider la conception de la classe abstraite. Par exemple, <xref:System.IO.FileStream?displayProperty=nameWithType> est une implémentation de la classe abstraite <xref:System.IO.Stream?displayProperty=nameWithType>.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
