---
title: Méthodes d'extension
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 13f92470b23d138e0d30bed947ff1932f2605d28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741625"
---
# <a name="extension-methods"></a>Méthodes d'extension
Les méthodes d’extension sont une fonctionnalité de langage qui permet d’appeler des méthodes statiques à l’aide de la syntaxe d’appel de méthode d’instance. Ces méthodes doivent accepter au moins un paramètre, qui représente l’instance sur laquelle la méthode doit fonctionner.

 La classe qui définit ces méthodes d’extension est appelée classe « sponsor » et doit être déclarée comme static. Pour utiliser des méthodes d’extension, vous devez importer l’espace de noms définissant la classe sponsor.

 ❌ Évitez les frivolously définissant les méthodes d’extension, en particulier sur les types dont vous n’êtes pas propriétaire.

 Si vous disposez d’un code source de type, envisagez plutôt d’utiliser des méthodes d’instance normales. Si vous ne possédez pas et que vous souhaitez ajouter une méthode, soyez très vigilant. La libéralisation de l’utilisation des méthodes d’extension risque d’encombrer les API de types qui n’ont pas été conçues pour avoir ces méthodes.

 ✔️ envisagez d’utiliser des méthodes d’extension dans l’un des scénarios suivants :

- Pour fournir des fonctionnalités d’assistance relatives à chaque implémentation d’une interface, si cette fonctionnalité peut être écrite en termes d’interface principale. Cela est dû au fait que les implémentations concrètes ne peuvent pas être assignées à des interfaces. Par exemple, les opérateurs de `LINQ to Objects` sont implémentés en tant que méthodes d’extension pour tous les types de <xref:System.Collections.Generic.IEnumerable%601>. Ainsi, toute implémentation de `IEnumerable<>` est automatiquement compatible LINQ.

- Quand une méthode d’instance introduit une dépendance sur un certain type, mais une telle dépendance rompt les règles de gestion des dépendances. Par exemple, une dépendance de <xref:System.String> à <xref:System.Uri?displayProperty=nameWithType> n’est probablement pas souhaitable, donc `String.ToUri()` méthode d’instance qui retourne `System.Uri` serait la mauvaise conception d’une perspective de gestion des dépendances. Une méthode d’extension statique `Uri.ToUri(this string str)` retourner `System.Uri` serait une conception bien meilleure.

 ❌ éviter de définir des méthodes d’extension sur <xref:System.Object?displayProperty=nameWithType>.

 Visual Basic les utilisateurs ne seront pas en mesure d’appeler ces méthodes sur des références d’objet à l’aide de la syntaxe de méthode d’extension. Visual Basic ne prend pas en charge l’appel de telles méthodes, car, dans Visual Basic, la déclaration d’une référence en tant qu’objet force la liaison tardive de tous les appels de méthode sur celui-ci (le membre réel appelé est déterminé au moment de l’exécution), tandis que les liaisons aux méthodes d’extension sont déterminées à au moment de la compilation (liaison anticipée).

 Notez que l’instruction s’applique à d’autres langages où le même comportement de liaison est présent, ou où les méthodes d’extension ne sont pas prises en charge.

 ❌ ne placez pas de méthodes d’extension dans le même espace de noms que le type étendu, sauf s’il s’agit d’ajouter des méthodes aux interfaces ou pour la gestion des dépendances.

 ❌ éviter de définir au moins deux méthodes d’extension avec la même signature, même si elles se trouvent dans des espaces de noms différents.

 ✔️ ENVISAGER de définir des méthodes d’extension dans le même espace de noms que le type étendu si le type est une interface et si les méthodes d’extension sont destinées à être utilisées dans la plupart ou dans tous les cas.

 ❌ ne définissez pas de méthodes d’extension implémentant une fonctionnalité dans des espaces de noms généralement associés à d’autres fonctionnalités. Au lieu de cela, définissez-les dans l’espace de noms associé à la fonctionnalité à laquelle ils appartiennent.

 ❌ éviter la dénomination générique des espaces de noms dédiés aux méthodes d’extension (par exemple, « extensions »). Utilisez un nom descriptif (par exemple, « routage ») à la place.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
