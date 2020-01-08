---
title: Méthodes d'extension
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: KrzysztofCwalina
ms.openlocfilehash: ad78bae2dc7a3000b67224da6f1a8c578053087f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347031"
---
# <a name="extension-methods"></a>Méthodes d'extension
Les méthodes d’extension sont une fonctionnalité de langage qui permet d’appeler des méthodes statiques à l’aide de la syntaxe d’appel de méthode d’instance. Ces méthodes doivent accepter au moins un paramètre, qui représente l’instance sur laquelle la méthode doit fonctionner.  
  
 La classe qui définit ces méthodes d’extension est appelée classe « sponsor » et doit être déclarée comme static. Pour utiliser des méthodes d’extension, vous devez importer l’espace de noms définissant la classe sponsor.  
  
 **X AVOID** leurs intentions soient amicales définissant les méthodes d’extension, en particulier sur les types que vous ne possédez pas.  
  
 Si vous disposez d’un code source de type, envisagez plutôt d’utiliser des méthodes d’instance normales. Si vous ne possédez pas et que vous souhaitez ajouter une méthode, soyez très vigilant. La libéralisation de l’utilisation des méthodes d’extension risque d’encombrer les API de types qui n’ont pas été conçues pour avoir ces méthodes.  
  
 **✓ CONSIDER** à l’aide des méthodes d’extension dans un des scénarios suivants :  
  
- Pour fournir des fonctionnalités d’assistance relatives à chaque implémentation d’une interface, si cette fonctionnalité peut être écrite en termes d’interface principale. Cela est dû au fait que les implémentations concrètes ne peuvent pas être assignées à des interfaces. Par exemple, les opérateurs de `LINQ to Objects` sont implémentés en tant que méthodes d’extension pour tous les types de <xref:System.Collections.Generic.IEnumerable%601>. Ainsi, toute implémentation de `IEnumerable<>` est automatiquement compatible LINQ.  
  
- Quand une méthode d’instance introduit une dépendance sur un certain type, mais une telle dépendance rompt les règles de gestion des dépendances. Par exemple, une dépendance de <xref:System.String> à <xref:System.Uri?displayProperty=nameWithType> n’est probablement pas souhaitable, donc `String.ToUri()` méthode d’instance qui retourne `System.Uri` serait la mauvaise conception d’une perspective de gestion des dépendances. Une méthode d’extension statique `Uri.ToUri(this string str)` retourner `System.Uri` serait une conception bien meilleure.  
  
 **X AVOID** définition des méthodes d’extension sur <xref:System.Object?displayProperty=nameWithType>.  
  
 Visual Basic les utilisateurs ne seront pas en mesure d’appeler ces méthodes sur des références d’objet à l’aide de la syntaxe de méthode d’extension. Visual Basic ne prend pas en charge l’appel de telles méthodes, car, dans Visual Basic, la déclaration d’une référence en tant qu’objet force la liaison tardive de tous les appels de méthode sur celui-ci (le membre réel appelé est déterminé au moment de l’exécution), tandis que les liaisons aux méthodes d’extension sont déterminées à au moment de la compilation (liaison anticipée).  
  
 Notez que l’instruction s’applique à d’autres langages où le même comportement de liaison est présent, ou où les méthodes d’extension ne sont pas prises en charge.  
  
 **X DO NOT** méthodes d’extension dans le même espace de noms en tant que le type étendu est utilisée pour ajouter des méthodes aux interfaces ou pour la gestion des dépendances.  
  
 **X AVOID** définissant deux ou plusieurs méthodes d’extension avec la même signature, même s’ils résident dans différents espaces de noms.  
  
 **✓ CONSIDER** définition des méthodes d’extension dans le même espace de noms en tant que le type étendu si le type est une interface et si les méthodes d’extension sont destinés à être utilisés dans la plupart des cas.  
  
 **X DO NOT** définir des méthodes d’extension mise en œuvre d’une fonctionnalité dans les espaces de noms normalement avec d’autres fonctionnalités. Au lieu de cela, définissez-les dans l’espace de noms associé à la fonctionnalité à laquelle ils appartiennent.  
  
 **X AVOID** générique d’affectation de noms d’espaces de noms dédié aux méthodes d’extension (par exemple, « Extensions »). Utilisez un nom descriptif (par exemple, « routage ») à la place.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
