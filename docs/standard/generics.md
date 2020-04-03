---
title: Vue d’ensemble des types génériques (génériques)
description: Découvrez dans quelle mesure les génériques peuvent faire office de modèles de code qui vous permettent de définir des structures de données de type sécurisé sans vous limiter à un type de données réel.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: f51d69088b0d5c798f3aa3a6c1f5b62b3ea81d39
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635283"
---
# <a name="generic-types-overview"></a>Vue d’ensemble des types génériques

Les développeurs utilisent tout le temps des génériques dans .NET, implicitement ou explicitement. Quand vous utilisez LINQ dans .NET, avez-vous déjà remarqué que vous utilisez <xref:System.Collections.Generic.IEnumerable%601> ? Ou si vous avez déjà vu un échantillon en ligne d’un « référentiel générique `IQueryable<T>`» pour parler à des bases de données à l’aide de Cadre d’entité, avez-vous vu que la plupart des méthodes reviennent ? Vous vous êtes peut-être demandé ce que signifie le **T** dans ces exemples et pourquoi il s’y trouve.

Les génériques introduits dans .NET Framework 2.0 sont essentiellement un « modèle de code » qui permet aux développeurs de définir des structures de données [de type sécurisé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) sans se limiter à un type de données réel. Par <xref:System.Collections.Generic.List%601> exemple, est une [collection générique](xref:System.Collections.Generic) qui peut être `List<int>`déclaré `List<string>`et `List<Person>`utilisé avec n’importe quel type, comme , ou .

Pour comprendre en quoi les génériques sont utiles, nous devons jeter un œil à une classe spécifique avant et après l’ajout de génériques : <xref:System.Collections.ArrayList>. Dans .NET Framework 1.0, les éléments `ArrayList` étaient de type <xref:System.Object>. Tout élément ajouté à la collection a `Object`été converti silencieusement en . Il en serait de même lorsque l’on litait des éléments de la liste. Ce processus est appelé [boxing et unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), et il a un impact sur le niveau de performance. Mis à part les performances, cependant, il n’y a aucun moyen de déterminer le type de données dans la liste au moment de la compilation, ce qui rend pour un code fragile. Les génériques résolvent ce problème en définissant le type de données que chaque instance de la liste contiendra. Par exemple, vous pouvez ajouter uniquement des entiers à `List<int>` et uniquement des personnes à `List<Person>`.

Les génériques sont également disponibles à l’heure de l’exécution. Le temps d’exécution sait quel type de structure de données vous utilisez et peut le stocker en mémoire plus efficacement.

L’exemple suivant est un petit programme qui illustre l’efficacité de connaître le type de structure de données au moment de l’exécution :

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

Ce programme produit une sortie similaire à ce qui suit :

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

La première chose que vous pouvez remarquer ici est que le tri de la liste générique est beaucoup plus rapide que le tri de la liste non générique. Vous pouvez également noter que le type de la liste générique est différent ([System.Int32]), alors que le type de la liste non générique est généralisé. Parce que le temps `List<int>` d’exécution sait que le générique est de type, <xref:System.Int32>il peut stocker `ArrayList` les éléments de liste dans un tableau d’intégration sous-jacent dans la mémoire, tandis que le non-générique doit jeter chaque élément de liste à un objet. Dans cet exemple, les transtypages supplémentaires prennent du temps et ralentissent le tri de la liste.

Un autre avantage de la connaissance du type de votre générique par le runtime est une meilleure expérience de débogage. Quand vous déboguez un générique en C#, vous connaissez le type de chaque élément dans votre structure de données. Sans les génériques, vous ne pourriez pas connaître le type de chaque élément.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C# - Génériques](../../docs/csharp/programming-guide/generics/index.md)
