---
title: Types imbriqués
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: dd13116b13ac8e2d7a3af6ef014eb4f393909515
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743702"
---
# <a name="nested-types"></a>Types imbriqués
Un type imbriqué est un type défini dans la portée d’un autre type, appelé type englobant. Un type imbriqué a accès à tous les membres de son type englobant. Par exemple, il a accès aux champs privés définis dans le type englobant et aux champs protégés définis dans tous les ascendants du type englobant.

 En général, les types imbriqués doivent être utilisés avec modération. et ce, pour plusieurs raisons. Certains développeurs ne sont pas entièrement familiarisés avec le concept. Ces développeurs peuvent, par exemple, rencontrer des problèmes avec la syntaxe de la déclaration de variables de types imbriqués. Les types imbriqués sont également très étroitement couplés avec leurs types englobants, et en tant que tels ne sont pas adaptés aux types à usage général.

 Les types imbriqués sont mieux adaptés à la modélisation des détails d’implémentation de leurs types englobants. L’utilisateur final doit rarement déclarer des variables d’un type imbriqué et, presque, ne doit jamais avoir à instancier explicitement des types imbriqués. Par exemple, l’énumérateur d’une collection peut être un type imbriqué de cette collection. Les énumérateurs sont généralement instanciés par leur type englobant, et étant donné que de nombreux langages prennent en charge l’instruction foreach, les variables d’énumérateur doivent rarement être déclarées par l’utilisateur final.

 ✔️ Utilisez des types imbriqués lorsque la relation entre le type imbriqué et son type externe est telle que la sémantique d’accessibilité des membres est souhaitable.

 ❌ n’utilisez pas les types imbriqués publics comme construction de regroupement logique ; Utilisez des espaces de noms pour ce.

 ❌ Évitez les types imbriqués exposés publiquement. La seule exception à cela est si les variables du type imbriqué doivent être déclarées uniquement dans des scénarios rares tels que le sous-classement ou d’autres scénarios de personnalisation avancée.

 ❌ n’utilisez pas de types imbriqués si le type est susceptible d’être référencé en dehors du type conteneur.

 Par exemple, une énumération passée à une méthode définie sur une classe ne doit pas être définie en tant que type imbriqué dans la classe.

 ❌ n’utilisez pas les types imbriqués s’ils doivent être instanciés par le code client.  Si un type a un constructeur public, il ne doit probablement pas être imbriqué.

 Si un type peut être instancié, cela semble indiquer que le type a un emplacement dans l’infrastructure proprement dit (vous pouvez le créer, l’utiliser et le détruire sans jamais utiliser le type externe), et ne doit donc pas être imbriqué. Les types internes ne doivent pas être largement réutilisés en dehors du type externe sans aucune relation au type externe.

 ❌ ne définissez pas un type imbriqué en tant que membre d’une interface. De nombreux langages ne prennent pas en charge ce type de construction.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
