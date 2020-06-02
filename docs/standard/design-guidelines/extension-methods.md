---
title: Méthodes d’extension
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 77c012d7838ae2fa1f62163bc58520db67c64ce5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289757"
---
# <a name="extension-methods"></a>Méthodes d’extension

Les méthodes d’extension sont une fonctionnalité de langage qui permet d’appeler des méthodes statiques à l’aide de la syntaxe d’appel de méthode d’instance. Ces méthodes doivent accepter au moins un paramètre, qui représente l’instance sur laquelle la méthode doit fonctionner.

 La classe qui définit une méthode d’extension est appelée classe « sponsor » et doit être déclarée comme `static` . Pour utiliser des méthodes d’extension, vous devez importer l’espace de noms qui définit la classe sponsor.

 ❌Évitez l’utilisation excessive des méthodes d’extension, en particulier sur les types dont vous n’êtes pas propriétaire.

 Si vous disposez d’un code source de type, envisagez plutôt d’utiliser des méthodes d’instance normales. Si vous ne possédez pas le code source et que vous souhaitez ajouter une méthode, soyez très vigilant. La libéralisation de l’utilisation des méthodes d’extension risque d’encombrer les API de types qui n’ont pas été conçues pour avoir ces méthodes.

 ✔️ envisagez d’utiliser des méthodes d’extension dans l’un des scénarios suivants :

- Pour fournir des fonctionnalités d’assistance relatives à chaque implémentation d’une interface, si cette fonctionnalité peut être écrite en termes d’interface principale. Cela est dû au fait que les implémentations concrètes ne peuvent pas être assignées à des interfaces. Par exemple, les opérateurs LINQ to Objects sont implémentés en tant que méthodes d’extension pour tous les <xref:System.Collections.Generic.IEnumerable%601> types. Ainsi, toutes les `IEnumerable<>` implémentations sont automatiquement compatibles LINQ.

- Quand une méthode d’instance introduit une dépendance sur un certain type, mais une telle dépendance rompt les règles de gestion des dépendances. Par exemple, une dépendance de <xref:System.String> à <xref:System.Uri?displayProperty=nameWithType> n’est probablement pas souhaitable. par conséquent, `String.ToUri()` la méthode d’instance qui retourne `System.Uri` serait la mauvaise conception du point de vue de la gestion des dépendances. Le retour d’une méthode d’extension statique `Uri.ToUri(this string str)` `System.Uri` est une bien meilleure conception.

 ❌Évitez de définir des méthodes d’extension sur <xref:System.Object?displayProperty=nameWithType> .

 Visual Basic les utilisateurs ne seront pas en mesure d’appeler ces méthodes sur des références d’objet à l’aide de la syntaxe de méthode d’extension. Dans Visual Basic, la déclaration d’une référence comme `Object` force la liaison tardive de tous les appels de méthode sur celui-ci (ce qui signifie que le membre réel appelé est déterminé au moment de l’exécution). Les liaisons aux méthodes d’extension sont déterminées au moment de la compilation (liaison anticipée).

 Cette règle s’applique aux autres langages où le même comportement de liaison est présent ou où les méthodes d’extension ne sont pas prises en charge.

 ❌NE placez pas les méthodes d’extension dans le même espace de noms que le type étendu, sauf s’il s’agit d’ajouter des méthodes aux interfaces ou pour la gestion des dépendances.

 ❌Évitez de définir deux ou plusieurs méthodes d’extension avec la même signature, même si elles se trouvent dans des espaces de noms différents.

 ✔️ ENVISAGER de définir des méthodes d’extension dans le même espace de noms que le type étendu si le type est une interface et si les méthodes d’extension sont destinées à être utilisées dans la plupart ou dans tous les cas.

 ❌NE définissez pas de méthodes d’extension implémentant une fonctionnalité dans les espaces de noms généralement associés à d’autres fonctionnalités. Au lieu de cela, définissez-les dans l’espace de noms associé à la fonctionnalité à laquelle ils appartiennent.

 ❌Évitez les noms génériques des espaces de noms dédiés aux méthodes d’extension (par exemple, « extensions »). Utilisez un nom descriptif (par exemple, « routage ») à la place.

 *Parties &copy; 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)
