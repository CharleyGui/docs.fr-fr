---
title: Classes de base pour l'implémentation d'abstractions
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: b22923338f8488b6f7684e565f62d9afc16e6aa0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741781"
---
# <a name="base-classes-for-implementing-abstractions"></a>Classes de base pour l'implémentation d'abstractions
Strictement parlant, une classe devient une classe de base lorsqu’une autre classe en est dérivée. Dans le cadre de cette section, toutefois, une classe de base est une classe conçue principalement pour fournir une abstraction commune ou pour d’autres classes afin de réutiliser une implémentation par défaut via l’héritage. Les classes de base se trouvent généralement au milieu des hiérarchies d’héritage, entre une abstraction à la racine d’une hiérarchie et plusieurs implémentations personnalisées en bas.

 Elles servent d’assistance d’implémentation pour l’implémentation d’abstractions. Par exemple, l’une des abstractions de l’infrastructure pour les collections ordonnées d’éléments est l’interface <xref:System.Collections.Generic.IList%601>. L’implémentation de <xref:System.Collections.Generic.IList%601> n’est pas simple, et par conséquent, l’infrastructure fournit plusieurs classes de base, telles que <xref:System.Collections.ObjectModel.Collection%601> et <xref:System.Collections.ObjectModel.KeyedCollection%602>, qui servent d’assistance pour l’implémentation des collections personnalisées.

 Les classes de base ne sont généralement pas adaptées à des abstractions, car elles ont tendance à contenir un trop grand nombre d’implémentations. Par exemple, la classe de base `Collection<T>` contient un grand nombre d’implémentations liées au fait qu’elle implémente l’interface de `IList` non générique (pour une intégration optimale avec les collections non génériques) et au fait qu’il s’agit d’une collection d’éléments stockés en mémoire dans l’un de ses champs.

 Comme indiqué précédemment, les classes de base peuvent fournir une aide précieuse pour les utilisateurs qui doivent implémenter des abstractions, mais en même temps, elles peuvent être une responsabilité significative. Ils ajoutent de la surface d’exposition et augmentent la profondeur des hiérarchies d’héritage. par conséquent, le concept complique le Framework. Par conséquent, les classes de base doivent être utilisées uniquement si elles fournissent une valeur significative aux utilisateurs de l’infrastructure. Elles doivent être évitées si elles fournissent la valeur uniquement aux implémenteurs de l’infrastructure, auquel cas la délégation à une implémentation interne au lieu d’un héritage à partir d’une classe de base doit être fortement prise en compte.

 ✔️ ENVISAGER de rendre les classes de base abstraites même si elles ne contiennent pas de membres abstraits. Cela communique clairement aux utilisateurs que la classe est conçue pour être héritée uniquement.

 ✔️ envisagez de placer les classes de base dans un espace de noms distinct des types de scénario principaux. Par définition, les classes de base sont destinées aux scénarios d’extensibilité avancée et, par conséquent, ne sont pas intéressantes pour la majorité des utilisateurs.

 ❌ éviter de nommer les classes de base avec un suffixe « base » si la classe est destinée à être utilisée dans des API publiques.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
