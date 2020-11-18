---
title: Conception de classes abstraites
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 6903e10c8695376d8ac5961461796c5413307f90
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821643"
---
# <a name="abstract-class-design"></a>Conception de classes abstraites

❌ NE définissez pas de constructeurs internes publics ou protégés dans les types abstraits.

 Les constructeurs doivent être publics uniquement si les utilisateurs doivent créer des instances du type. Étant donné que vous ne pouvez pas créer d’instances d’un type abstrait, un type abstrait avec un constructeur public n’est pas correctement conçu et trompe les utilisateurs.

 ✔️ Définissez un constructeur protégé ou interne dans des classes abstraites.

 Un constructeur protégé est plus courant et permet simplement à la classe de base d’effectuer sa propre initialisation lors de la création de sous-types.

 Un constructeur interne peut être utilisé pour limiter les implémentations concrètes de la classe abstraite à l’assembly qui définit la classe.

 ✔️ fournissez au moins un type concret qui hérite de chaque classe abstraite que vous livrez.

 Cela permet de valider la conception de la classe abstraite. Par exemple,  <xref:System.IO.FileStream?displayProperty=nameWithType> est une implémentation de la <xref:System.IO.Stream?displayProperty=nameWithType> classe abstraite.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de type](type.md)
- [Directives de conception d’infrastructure](index.md)
