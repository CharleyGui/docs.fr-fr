---
title: Conception de classes statiques
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 104fa204a95ef31d34e224348068e3a6505aded5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743598"
---
# <a name="static-class-design"></a>Conception de classes statiques
Une classe statique est définie en tant que classe qui contient uniquement des membres statiques (bien entendu, outre les membres d’instance hérités de <xref:System.Object?displayProperty=nameWithType> et éventuellement un constructeur privé). Certains langages fournissent une prise en charge intégrée des classes statiques. Dans C# 2,0 et versions ultérieures, lorsqu’une classe est déclarée comme étant statique, elle est sealed, abstract, et aucun membre d’instance ne peut être substitué ou déclaré.

 Les classes statiques sont un compromis entre une conception pure orientée objet et une simplicité. Elles sont généralement utilisées pour fournir des raccourcis vers d’autres opérations (telles que <xref:System.IO.File?displayProperty=nameWithType>), des détenteurs de méthodes d’extension ou des fonctionnalités pour lesquelles un wrapper orienté objet complet n’est pas justifié (comme <xref:System.Environment?displayProperty=nameWithType>).

 ✔️ utiliser des classes statiques avec modération.

 Les classes statiques doivent être utilisées uniquement comme classes de prise en charge pour le noyau orienté objet de l’infrastructure.

 ❌ ne traitent pas les classes statiques comme un compartiment divers.

 ❌ ne déclarez pas ou ne substituez pas de membres d’instance dans des classes statiques.

 ✔️ déclarez des classes statiques comme sealed, abstract et ajoutez un constructeur d’instance privé si votre langage de programmation n’a pas de prise en charge intégrée des classes statiques.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
