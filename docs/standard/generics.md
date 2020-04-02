---
title: Vue d’ensemble des types génériques (génériques)
description: Découvrez dans quelle mesure les génériques peuvent faire office de modèles de code qui vous permettent de définir des structures de données de type sécurisé sans vous limiter à un type de données réel.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 0188e620a45462e7cc31391406ade9d57b1b0220
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588483"
---
# <a name="generic-types-overview"></a><span data-ttu-id="c45dc-103">Vue d’ensemble des types génériques</span><span class="sxs-lookup"><span data-stu-id="c45dc-103">Generic types overview</span></span>

<span data-ttu-id="c45dc-104">Les développeurs utilisent tout le temps des génériques dans .NET, implicitement ou explicitement.</span><span class="sxs-lookup"><span data-stu-id="c45dc-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="c45dc-105">Quand vous utilisez LINQ dans .NET, avez-vous déjà remarqué que vous utilisez <xref:System.Collections.Generic.IEnumerable%601> ?</span><span class="sxs-lookup"><span data-stu-id="c45dc-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="c45dc-106">Ou si vous avez déjà vu un échantillon en ligne d’un « référentiel générique `IQueryable<T>`» pour parler à des bases de données à l’aide de Cadre d’entité, avez-vous vu que la plupart des méthodes reviennent ?</span><span class="sxs-lookup"><span data-stu-id="c45dc-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="c45dc-107">Vous vous êtes peut-être demandé ce que signifie le **T** dans ces exemples et pourquoi il s’y trouve.</span><span class="sxs-lookup"><span data-stu-id="c45dc-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="c45dc-108">Les génériques introduits dans .NET Framework 2.0 sont essentiellement un « modèle de code » qui permet aux développeurs de définir des structures de données [de type sécurisé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) sans se limiter à un type de données réel.</span><span class="sxs-lookup"><span data-stu-id="c45dc-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="c45dc-109">Par <xref:System.Collections.Generic.List%601> exemple, est une [collection générique](xref:System.Collections.Generic) qui peut être `List<int>`déclaré `List<string>`et `List<Person>`utilisé avec n’importe quel type, comme , ou .</span><span class="sxs-lookup"><span data-stu-id="c45dc-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="c45dc-110">Pour comprendre en quoi les génériques sont utiles, nous devons jeter un œil à une classe spécifique avant et après l’ajout de génériques : <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="c45dc-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="c45dc-111">Dans .NET Framework 1.0, les éléments `ArrayList` étaient de type <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c45dc-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="c45dc-112">Cela signifie que n’importe quel élément ajouté était converti en `Object` en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="c45dc-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="c45dc-113">La même chose se produirait lors de la lecture des éléments de la liste.</span><span class="sxs-lookup"><span data-stu-id="c45dc-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="c45dc-114">Ce processus est appelé [boxing et unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), et il a un impact sur le niveau de performance.</span><span class="sxs-lookup"><span data-stu-id="c45dc-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="c45dc-115">Qui plus est, il n’y a cependant aucun moyen de déterminer le type de données dans la liste au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c45dc-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="c45dc-116">Cela fragilise parfois le code.</span><span class="sxs-lookup"><span data-stu-id="c45dc-116">This makes for some fragile code.</span></span> <span data-ttu-id="c45dc-117">Les génériques résolvent ce problème en définissant le type de données que chaque instance de la liste contiendra.</span><span class="sxs-lookup"><span data-stu-id="c45dc-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="c45dc-118">Par exemple, vous pouvez ajouter uniquement des entiers à `List<int>` et uniquement des personnes à `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="c45dc-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="c45dc-119">Les génériques sont également disponibles à l’heure de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c45dc-119">Generics are also available at run time.</span></span> <span data-ttu-id="c45dc-120">Cela signifie que le runtime sait quel type de structure de données vous utilisez et peut les stocker plus efficacement dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c45dc-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="c45dc-121">L’exemple suivant est un petit programme qui illustre l’efficacité de connaître le type de structure de données au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="c45dc-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

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

<span data-ttu-id="c45dc-122">Ce programme produit une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c45dc-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="c45dc-123">La première chose que vous pouvez remarquer ici est que le tri de la liste générique est beaucoup plus rapide que le tri de la liste non générique.</span><span class="sxs-lookup"><span data-stu-id="c45dc-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="c45dc-124">Vous pouvez également noter que le type de la liste générique est différent ([System.Int32]), alors que le type de la liste non générique est généralisé.</span><span class="sxs-lookup"><span data-stu-id="c45dc-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="c45dc-125">Parce que le temps `List<int>` d’exécution sait que le générique est de type, <xref:System.Int32>il peut stocker `ArrayList` les éléments de liste dans un tableau d’intégration sous-jacent dans la mémoire, tandis que le non-générique doit jeter chaque élément de liste à un objet.</span><span class="sxs-lookup"><span data-stu-id="c45dc-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="c45dc-126">Dans cet exemple, les transtypages supplémentaires prennent du temps et ralentissent le tri de la liste.</span><span class="sxs-lookup"><span data-stu-id="c45dc-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="c45dc-127">Un autre avantage de la connaissance du type de votre générique par le runtime est une meilleure expérience de débogage.</span><span class="sxs-lookup"><span data-stu-id="c45dc-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="c45dc-128">Quand vous déboguez un générique en C#, vous connaissez le type de chaque élément dans votre structure de données.</span><span class="sxs-lookup"><span data-stu-id="c45dc-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="c45dc-129">Sans les génériques, vous ne pourriez pas connaître le type de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="c45dc-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="c45dc-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c45dc-130">See also</span></span>

- [<span data-ttu-id="c45dc-131">Guide de programmation C# - Génériques</span><span class="sxs-lookup"><span data-stu-id="c45dc-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
