---
title: Sceller
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: a54c68efb4ac114fe0e5a5712eca877bef35c103
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290108"
---
# <a name="sealing"></a>Sceller
L’une des fonctionnalités des frameworks orientés objet est que les développeurs peuvent les étendre et les personnaliser de manière inattendue par les concepteurs de Framework. Il s’agit de la puissance et du danger de la conception extensible. Lorsque vous concevez votre infrastructure, il est donc très important de concevoir soigneusement l’extensibilité quand vous le souhaitez, et de limiter l’extensibilité quand elle est dangereuse.

 Mécanisme puissant qui empêche la fermeture de l’extensibilité. Vous pouvez sceller la classe ou des membres individuels. La fermeture d’une classe empêche les utilisateurs d’hériter de la classe. La fermeture d’un membre empêche les utilisateurs de se substituer à un membre particulier.

 ❌NE scellez pas les classes sans avoir une bonne raison de le faire.

 Sceller une classe parce que vous ne pouvez pas considérer un scénario d’extensibilité n’est pas une bonne raison. Les utilisateurs de l’infrastructure aiment hériter des classes pour différentes raisons qui ne sont pas évidentes, comme l’ajout de membres de commodité. Consultez [classes non scellées](unsealed-classes.md) pour obtenir des exemples de raisons non évidentes que les utilisateurs souhaitent hériter d’un type.

 Les bonnes raisons pour sceller une classe sont les suivantes :

- La classe est une classe statique. Consultez [conception de classes statiques](static-class.md).

- La classe stocke des secrets sensibles à la sécurité dans les membres protégés hérités.

- La classe hérite de nombreux membres virtuels et le coût de leur scellement individuellement compenserait les avantages de laisser la classe non scellée.

- La classe est un attribut qui nécessite une recherche très rapide au moment de l’exécution. Les attributs scellés ont des niveaux de performances légèrement supérieurs à ceux des attributs non scellés. Consultez [attributs](attributes.md).

 ❌NE déclarez pas de membres protégés ou virtuels sur des types sealed.

 Par définition, les types sealed ne peuvent pas être hérités de. Cela signifie que les membres protégés sur les types sealed ne peuvent pas être appelés, et les méthodes virtuelles sur les types sealed ne peuvent pas être substituées.

 ✔️ envisagez de sceller les membres que vous substituez.

 Les problèmes qui peuvent résulter de l’introduction de membres virtuels (décrits dans [membres virtuels](virtual-members.md)) s’appliquent également aux remplacements, bien qu’à un degré légèrement moindre. Le scellage d’un remplacement vous protège de ces problèmes à partir de ce point dans la hiérarchie d’héritage.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Conception en vue de l’extensibilité](designing-for-extensibility.md)
- [Classes non scellées](unsealed-classes.md)
