---
title: Délégués fortement typés
description: Découvrez comment utiliser des types délégués génériques pour déclarer des types personnalisés lors de la création d’une fonctionnalité nécessitant des délégués.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 798e8b597389bc99d10e587ec417a4e717f28abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146201"
---
# <a name="strongly-typed-delegates"></a>Délégués fortement typés

[Précédent](delegate-class.md)

Dans l’article précédent, vous avez vu que vous pouviez créer des types délégués spécifiques à l’aide du mot clé `delegate`.

La classe abstraite Delegate fournit l’infrastructure pour l’invocation et le couplage faible. Les types délégués concrets deviennent beaucoup plus utiles en adoptant et en appliquant la sécurité de type pour les méthodes qui sont ajoutées à la liste d’invocation d’un objet délégué. Quand vous utilisez le mot clé `delegate` et que vous définissez un type délégué concret, le compilateur génère ces méthodes.

Dans la pratique, cela conduirait à la création de types délégués chaque fois que vous avez besoin d’une signature de méthode différente. Ce travail peut devenir fastidieux au bout d’un moment. Chaque nouvelle fonctionnalité nécessite de nouveaux types délégués.

Heureusement, cela n’est pas nécessaire. Le framework .NET Core contient plusieurs types que vous pouvez réutiliser chaque fois que vous avez besoin de types délégués. Il s’agit de définitions [génériques](programming-guide/generics/index.md). Vous pouvez ainsi déclarer des personnalisations quand vous avez besoin de nouvelles déclarations de méthode.

Le premier de ces types est le type <xref:System.Action> et plusieurs variantes :

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

Le modificateur `in` sur l’argument de type générique est traité dans l’article sur la covariance.

Il existe des variantes du délégué `Action` qui contiennent jusqu’à 16 arguments, comme <xref:System.Action%6016>.
Il est important que ces définitions utilisent différents arguments génériques pour chacun des arguments de délégués : cela offre une flexibilité maximale. Les arguments de méthode ne doivent pas obligatoirement être du même type, mais il peuvent l’être.

Utilisez l’un des types `Action` pour tout type délégué ayant un type de retour void.

Le framework inclut également plusieurs types délégués génériques que vous pouvez utiliser pour les types délégués qui retournent des valeurs :

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

Le modificateur `out` sur l’argument de type générique de résultat est traité dans l’article sur la covariance.

Il existe des variantes du délégué `Func` qui contiennent jusqu’à 16 arguments d’entrée, comme <xref:System.Func%6017>.
Par convention, le type du résultat est toujours le dernier paramètre de type dans toutes les déclarations `Func`.

Utilisez l’un des types `Func` pour tout type délégué qui retourne une valeur.

Il y a aussi une<xref:System.Predicate%601>
type pour un délégué qui retourne un test sur une seule valeur :

```csharp
public delegate bool Predicate<in T>(T obj);
```

Vous remarquerez que pour tout type `Predicate`, il existe un type `Func` structurellement équivalent, par exemple :

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Ces deux types peuvent vous sembler équivalents, mais ils ne le sont pas.
Ces deux variables ne sont pas interchangeables. Une variable d’un type ne peut pas être assignée à l’autre type. Le système de type C# utilise les noms des types définis, pas la structure.

Toutes ces définitions de types délégués dans la bibliothèque .NET Core doivent signifier que vous n’avez pas besoin de définir un nouveau type délégué pour toute nouvelle fonctionnalité que vous créez et qui nécessite des délégués. Ces définitions génériques doivent fournir tous les types délégués dont vous avez besoin dans la plupart des situations. Il vous suffit d’instancier l’un de ces types avec les paramètres de type nécessaires. Dans le cas des algorithmes qui peuvent être rendus génériques, ces délégués peuvent être utilisés en tant que types génériques.

Cela devrait vous procurer un gain de temps et réduire le nombre de nouveaux types que vous devez créer pour travailler avec des délégués.

Dans l’article suivant, vous verrez plusieurs schémas d’utilisation courants des délégués.

[Suivant](delegates-patterns.md)
