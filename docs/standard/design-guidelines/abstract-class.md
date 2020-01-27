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
ms.openlocfilehash: 018dd353024e75e9819f5a97008f2f422ecad291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739058"
---
# <a name="abstract-class-design"></a>Conception de classes abstraites

❌ ne définissez pas de constructeurs internes ou protégés internes dans des types abstraits.

 Les constructeurs doivent être publics uniquement si les utilisateurs doivent créer des instances du type. Étant donné que vous ne pouvez pas créer d’instances d’un type abstrait, un type abstrait avec un constructeur public n’est pas correctement conçu et trompe les utilisateurs.

 ✔️ Définissez un constructeur protégé ou interne dans des classes abstraites.

 Un constructeur protégé est plus courant et permet simplement à la classe de base d’effectuer sa propre initialisation lors de la création de sous-types.

 Un constructeur interne peut être utilisé pour limiter les implémentations concrètes de la classe abstraite à l’assembly qui définit la classe.

 ✔️ fournissez au moins un type concret qui hérite de chaque classe abstraite que vous livrez.

 Cela permet de valider la conception de la classe abstraite. Par exemple, <xref:System.IO.FileStream?displayProperty=nameWithType> est une implémentation de la classe abstraite <xref:System.IO.Stream?displayProperty=nameWithType>.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
