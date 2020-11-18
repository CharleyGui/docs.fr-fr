---
title: Classes unsealed
ms.date: 10/22/2008
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: b2e14b435aa567f231230da34307014210d46ccb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828515"
---
# <a name="unsealed-classes"></a>Classes unsealed
Les classes sealed ne peuvent pas être héritées de, et elles empêchent l’extensibilité. En revanche, les classes qui peuvent être héritées de sont appelées « classes non scellées ».

 ✔️ envisagez d’utiliser des classes non scellées sans membres virtuels ou protégés comme un excellent moyen de fournir une extensibilité encore plus coûteuse à un Framework.

 Les développeurs souhaitent souvent hériter de classes non scellées afin d’ajouter des membres de commodité tels que des constructeurs personnalisés, de nouvelles méthodes ou des surcharges de méthode. Par exemple,  `System.Messaging.MessageQueue` est déscellée et permet ainsi aux utilisateurs de créer des files d’attente personnalisées qui sont par défaut vers un chemin d’accès de file d’attente particulier ou d’ajouter des méthodes personnalisées qui simplifient l’API pour des scénarios spécifiques.

 Les classes sont déscellées par défaut dans la plupart des langages de programmation, et il s’agit également de la valeur par défaut recommandée pour la plupart des classes dans les infrastructures. L’extensibilité offerte par les types non scellés est grandement appréciée par les utilisateurs du Framework et très peu coûteuse à fournir en raison des coûts de test relativement faibles associés aux types non scellés.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Conception en vue de l’extensibilité](designing-for-extensibility.md)
- [Sceller](sealing.md)
