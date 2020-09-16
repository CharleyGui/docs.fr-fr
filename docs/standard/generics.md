---
title: Vue d’ensemble des types génériques (génériques)
description: Découvrez dans quelle mesure les génériques peuvent faire office de modèles de code qui vous permettent de définir des structures de données de type sécurisé sans vous limiter à un type de données réel.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 5f6e84e23b5bcdcb3dcd742823d83728fb43d195
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557942"
---
# <a name="generic-types-overview"></a>Vue d’ensemble des types génériques

Les développeurs utilisent tout le temps des génériques dans .NET, implicitement ou explicitement. Quand vous utilisez LINQ dans .NET, avez-vous déjà remarqué que vous utilisez <xref:System.Collections.Generic.IEnumerable%601> ? Ou si vous avez déjà vu un exemple en ligne d’un « référentiel générique » pour communiquer avec les bases de données à l’aide de Entity Framework, Saviez-vous que la plupart des méthodes retournent `IQueryable<T>` ? Vous vous êtes peut-être demandé ce que signifie le **T** dans ces exemples et pourquoi il s’y trouve.

Les génériques introduits dans .NET Framework 2.0 sont essentiellement un « modèle de code » qui permet aux développeurs de définir des structures de données [de type sécurisé](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) sans se limiter à un type de données réel. Par exemple, <xref:System.Collections.Generic.List%601> est une [collection générique](xref:System.Collections.Generic) qui peut être déclarée et utilisée avec n’importe quel type, tel que `List<int>` , `List<string>` ou `List<Person>` .

Pour comprendre en quoi les génériques sont utiles, nous devons jeter un œil à une classe spécifique avant et après l’ajout de génériques : <xref:System.Collections.ArrayList>. Dans .NET Framework 1.0, les éléments `ArrayList` étaient de type <xref:System.Object>. Tout élément ajouté à la collection a été converti en mode silencieux en `Object` . Cela se produit lors de la lecture d’éléments de la liste. Ce processus est appelé [boxing et unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), et il a un impact sur le niveau de performance. Toutefois, il n’existe aucun moyen de déterminer le type de données dans la liste au moment de la compilation, ce qui crée un code fragile. Les génériques résolvent ce problème en définissant le type de données que chaque instance de la liste contiendra. Par exemple, vous pouvez ajouter uniquement des entiers à `List<int>` et uniquement des personnes à `List<Person>`.

Les génériques sont également disponibles au moment de l’exécution. Le runtime sait quel type de structure de données vous utilisez et peut le stocker dans la mémoire plus efficacement.

L’exemple suivant est un petit programme qui illustre l’efficacité de la connaissance du type de structure de données au moment de l’exécution :

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

La première chose que vous pouvez remarquer ici est que le tri de la liste générique est beaucoup plus rapide que le tri de la liste non générique. Vous pouvez également noter que le type de la liste générique est différent ([System.Int32]), alors que le type de la liste non générique est généralisé. Étant donné que le runtime sait que le générique `List<int>` est de type <xref:System.Int32> , il peut stocker les éléments de liste dans un tableau d’entiers sous-jacent en mémoire, tandis que le non générique `ArrayList` doit effectuer un cast de chaque élément de liste en un objet. Dans cet exemple, les transtypages supplémentaires prennent du temps et ralentissent le tri de la liste.

Un autre avantage de la connaissance du type de votre générique par le runtime est une meilleure expérience de débogage. Quand vous déboguez un générique en C#, vous connaissez le type de chaque élément dans votre structure de données. Sans les génériques, vous ne pourriez pas connaître le type de chaque élément.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C# - Génériques](../csharp/programming-guide/generics/index.md)
