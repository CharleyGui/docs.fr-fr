---
title: Conception de structures
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: 7bb7e63004df2eb7541ba8d4f1118ea2272db126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730901"
---
# <a name="struct-design"></a>Conception de structures

Le type de valeur à usage général est le plus souvent appelé struct, son mot clé C#. Cette section fournit des instructions pour la conception générale des structs.

 ❌ NE fournissez pas de constructeur sans paramètre pour un struct.

 Le respect de cette règle permet de créer des tableaux de structs sans avoir à exécuter le constructeur sur chaque élément du tableau. Notez que C# n’autorise pas les structs à avoir des constructeurs sans paramètre.

 ❌ NE définissez pas de types valeur mutable.

 Les types valeur mutable présentent plusieurs problèmes. Par exemple, lorsqu’un accesseur Get de propriété retourne un type valeur, l’appelant reçoit une copie. Étant donné que la copie est créée implicitement, les développeurs peuvent ne pas savoir qu’ils font muter la copie, et non la valeur d’origine. En outre, certains langages (Dynamic Languages, en particulier) rencontrent des problèmes lors de l’utilisation des types valeur mutables, car même les variables locales, lorsqu’elles sont déréférencées, provoquent une copie.

 ✔️ Assurez-vous qu’un État dans lequel toutes les données d’instance est définie sur zéro, false ou null (selon le cas) est valide.

 Cela empêche la création accidentelle d’instances non valides lorsqu’un tableau de structs est créé.

 ✔️ implémenter <xref:System.IEquatable%601> sur des types valeur.

 La <xref:System.Object.Equals%2A?displayProperty=nameWithType> méthode sur les types valeur provoque un boxing, et son implémentation par défaut n’est pas très efficace, car elle utilise la réflexion. <xref:System.IEquatable%601.Equals%2A> peut offrir de meilleures performances et peut être implémentée pour ne pas provoquer de conversion boxing.

 ❌ N’étendez pas explicitement <xref:System.ValueType> . En fait, la plupart des langues l’empêchent.

 En général, les structs peuvent être très utiles, mais ne doivent être utilisés que pour des valeurs petites, uniques et immuables qui ne seront pas converties fréquemment.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de type](type.md)
- [Directives de conception d’infrastructure](index.md)
- [Choix entre classe et structure](choosing-between-class-and-struct.md)
