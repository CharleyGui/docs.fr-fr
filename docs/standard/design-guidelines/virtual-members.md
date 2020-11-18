---
title: Membres virtuels
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 22eb71ccfc1b9a3d359b0453e4ff47f3f41827f5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828398"
---
# <a name="virtual-members"></a>Membres virtuels
Les membres virtuels peuvent être remplacés, ce qui modifie le comportement de la sous-classe. Elles sont assez similaires aux rappels en termes d’extensibilité, mais elles sont préférables en termes de performances d’exécution et de consommation de mémoire. En outre, les membres virtuels s’apaisent plus naturellement dans les scénarios qui requièrent la création d’un type spécial de type existant (spécialisation).

 Les membres virtuels sont plus performants que les rappels et les événements, mais ne sont pas plus performants que les méthodes non virtuelles.

 Le principal inconvénient des membres virtuels est que le comportement d’un membre virtuel ne peut être modifié qu’au moment de la compilation. Le comportement d’un rappel peut être modifié au moment de l’exécution.

 Les membres virtuels, comme les rappels (et peut-être plus que les rappels), sont coûteux pour la conception, le test et la maintenance, car tout appel à un membre virtuel peut être substitué de manière imprévisible et peut exécuter du code arbitraire. En outre, un plus grand nombre d’efforts est généralement requis pour définir clairement le contrat des membres virtuels, de sorte que le coût de la conception et de la documentation est plus élevé.

 ❌ N’effectuez pas de membres virtuels, sauf si vous avez une bonne raison de le faire et que vous connaissez tous les coûts liés à la conception, au test et à la maintenance des membres virtuels.

 Les membres virtuels sont moins indulgent avec en termes de modifications qui peuvent être apportées sans interrompre la compatibilité. En outre, ils sont plus lents que les membres non virtuels, principalement parce que les appels aux membres virtuels ne sont pas Inline.

 ✔️ ENVISAGER de limiter l’extensibilité à ce qui est absolument nécessaire.

 ✔️ préférez l’accessibilité protégée par rapport à l’accessibilité publique pour les membres virtuels. Les membres publics doivent fournir une extensibilité (si nécessaire) en appelant dans un membre virtuel protégé.

 Les membres publics d’une classe doivent fournir le jeu de fonctionnalités approprié aux consommateurs directs de cette classe. Les membres virtuels sont conçus pour être remplacés dans les sous-classes et l’accessibilité protégée est un excellent moyen d’étendre l’ensemble des points d’extensibilité virtuels à l’emplacement où ils peuvent être utilisés.

 *Parties &copy; 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Conception en vue de l’extensibilité](designing-for-extensibility.md)
