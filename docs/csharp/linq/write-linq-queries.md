---
title: Écrire des requêtes LINQ en C#
description: Découvrez comment écrire des requêtes LINQ en C#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: ed32543b0422e0664a8577f2c27f7c7c00a719a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632874"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="1d4f1-103">Écrire des requêtes LINQ en C\#</span><span class="sxs-lookup"><span data-stu-id="1d4f1-103">Write LINQ queries in C\#</span></span>

<span data-ttu-id="1d4f1-104">Cet article présente les trois façons d’écrire une requête LINQ en C# :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="1d4f1-105">Utilisez la syntaxe de requête.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-105">Use query syntax.</span></span>

2. <span data-ttu-id="1d4f1-106">Utilisez la syntaxe de méthode.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-106">Use method syntax.</span></span>

3. <span data-ttu-id="1d4f1-107">Utilisez une combinaison de syntaxe de requête et de syntaxe de méthode.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="1d4f1-108">Les exemples suivants montrent des requêtes LINQ simples en utilisant chaque approche répertoriée précédemment.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="1d4f1-109">En général, la règle consiste à utiliser (1) dès que possible et à utiliser (2) et (3) dès que cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="1d4f1-110">Ces requêtes fonctionnent sur les collections simples en mémoire ; toutefois, la syntaxe de base est identique à celle utilisée dans LINQ to Entities et LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="1d4f1-111">Exemple – Syntaxe de requête</span><span class="sxs-lookup"><span data-stu-id="1d4f1-111">Example - Query syntax</span></span>

<span data-ttu-id="1d4f1-112">La méthode recommandée pour écrire la plupart des requêtes consiste à utiliser la *syntaxe de requête* pour créer des *expressions de requête*.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="1d4f1-113">L’exemple suivant présente trois expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-113">The following example shows three query expressions.</span></span> <span data-ttu-id="1d4f1-114">La première expression de requête montre comment filtrer ou restreindre des résultats en appliquant des conditions avec une clause `where`.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="1d4f1-115">Tous les éléments de la séquence source dont la valeur est supérieure à 7 ou inférieure à 3 sont retournés.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="1d4f1-116">La deuxième expression montre comment classer les résultats retournés.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="1d4f1-117">La troisième expression montre comment regrouper des résultats en fonction d’une clé.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="1d4f1-118">Cette requête retourne deux groupes en fonction de la première lettre du mot.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="1d4f1-119">Notez que le type des requêtes est <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1d4f1-120">Toutes ces requêtes pourraient être écrites à l’aide de `var`, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="1d4f1-121">Dans chacun des exemples précédents, les requêtes ne s’exécutent pas réellement tant vous n’avez pas itéré la variable de requête dans une instruction `foreach` ou une autre instruction.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="1d4f1-122">Pour plus d’informations, voir [Introduction aux requêtes LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="1d4f1-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="1d4f1-123">Exemple – Syntaxe de méthode</span><span class="sxs-lookup"><span data-stu-id="1d4f1-123">Example - Method syntax</span></span>

<span data-ttu-id="1d4f1-124">Certaines opérations de requête doivent être exprimées comme un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="1d4f1-125">Les plus répandues de ces méthodes retournent des valeurs numériques uniques, telles que <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="1d4f1-126">Ces méthodes doivent toujours être appelées en dernier dans toutes les requêtes, car elles ne représentent qu’une valeur unique et ne peuvent pas servir de source pour une opération de requête supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="1d4f1-127">L’exemple suivant présente un appel de méthode dans une expression de requête :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="1d4f1-128">Si la méthode a des paramètres Action ou Func, ceux-ci sont fournis sous la forme d’une expression [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="1d4f1-129">Dans les requêtes précédentes, seule la requête 4 s’exécute immédiatement.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="1d4f1-130">Cela s’explique par le fait qu’elle retourne une valeur unique et non une collection <xref:System.Collections.Generic.IEnumerable%601> générique.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="1d4f1-131">La méthode elle-même doit utiliser `foreach` pour calculer sa valeur.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="1d4f1-132">Chacune des requêtes précédentes peut être écrite en utilisant des types implicites avec [var](../language-reference/keywords/var.md), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="1d4f1-133">Exemple – Syntaxe de méthode et de requête mixte</span><span class="sxs-lookup"><span data-stu-id="1d4f1-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="1d4f1-134">Cet exemple montre comment utiliser la syntaxe de méthode sur les résultats d’une clause de requête.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="1d4f1-135">Encadrez simplement l’expression de requête entre parenthèses, puis appliquez l’opérateur point et appelez la méthode.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="1d4f1-136">Dans l’exemple suivant, la requête 7 retourne les nombres dont la valeur est comprise entre 3 et 7.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="1d4f1-137">Toutefois, il est généralement préférable d’utiliser une deuxième variable pour stocker le résultat de l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="1d4f1-138">De cette manière, il est moins probable que la requête ne soit confondue avec les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="1d4f1-139">Comme la requête 7 retourne une valeur unique et non une collection, la requête s’exécute immédiatement.</span><span class="sxs-lookup"><span data-stu-id="1d4f1-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="1d4f1-140">La requête précédente peut être écrite en utilisant des types implicites avec `var`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="1d4f1-141">Elle peut être écrite dans la syntaxe de méthode comme suit :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="1d4f1-142">Elle peut être écrite en utilisant des types explicites, comme suit :</span><span class="sxs-lookup"><span data-stu-id="1d4f1-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="1d4f1-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d4f1-143">See also</span></span>

- [<span data-ttu-id="1d4f1-144">Procédure pas à pas : écriture de requêtes en C#</span><span class="sxs-lookup"><span data-stu-id="1d4f1-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="1d4f1-145">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1d4f1-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="1d4f1-146">où la clause</span><span class="sxs-lookup"><span data-stu-id="1d4f1-146">where clause</span></span>](../language-reference/keywords/where-clause.md)
