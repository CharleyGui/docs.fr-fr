---
title: Performances des requêtes chaînées-LINQ to XML
description: En savoir plus sur les requêtes chaînées peuvent être exécutées, ainsi qu’une requête unique plus grande et plus complexe.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: c1dae1eaf008a1f17c6884ef6b8e67d042719ad9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552500"
---
# <a name="performance-of-chained-queries-linq-to-xml"></a><span data-ttu-id="23cb1-103">Performances des requêtes chaînées (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="23cb1-103">Performance of chained queries (LINQ to XML)</span></span>

<span data-ttu-id="23cb1-104">L’un des principaux avantages de LINQ (et LINQ to XML) est que les requêtes chaînées peuvent être exécutées ainsi qu’une requête unique plus grande et plus complexe que les requêtes chaînées.</span><span class="sxs-lookup"><span data-stu-id="23cb1-104">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single query that is larger and more complicated than the chained queries.</span></span>

<span data-ttu-id="23cb1-105">Une requête chaînée est une requête qui utilise une autre requête comme source.</span><span class="sxs-lookup"><span data-stu-id="23cb1-105">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="23cb1-106">Par exemple, dans le code simple suivant, `query2` utilise `query1` comme source :</span><span class="sxs-lookup"><span data-stu-id="23cb1-106">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="23cb1-107">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="23cb1-107">This example produces the following output:</span></span>

```output
4
```

<span data-ttu-id="23cb1-108">Cette requête chaînée offre le même profil de performance que l'itération sur une liste liée.</span><span class="sxs-lookup"><span data-stu-id="23cb1-108">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="23cb1-109">L'axe <xref:System.Xml.Linq.XContainer.Elements%2A> offre essentiellement la même performance qu'une itération sur une liste liée.</span><span class="sxs-lookup"><span data-stu-id="23cb1-109">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="23cb1-110"><xref:System.Xml.Linq.XContainer.Elements%2A> est implémenté en tant qu'itérateur avec exécution différée.</span><span class="sxs-lookup"><span data-stu-id="23cb1-110"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="23cb1-111">Cela signifie qu'en plus de l'itération sur la liste liée, il effectue certaines tâches comme l'allocation de l'objet itérateur et le suivi de l'état d'exécution.</span><span class="sxs-lookup"><span data-stu-id="23cb1-111">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="23cb1-112">Ces tâches peuvent être divisées en deux catégories : les tâches effectuées lors de la configuration de l'itérateur et les tâches effectuées à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="23cb1-112">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="23cb1-113">Les tâches de configuration représentent une part réduite et fixe du travail, tandis que les tâches effectuées à chaque itération sont proportionnelles au nombre d'éléments de la collection source.</span><span class="sxs-lookup"><span data-stu-id="23cb1-113">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>
- <span data-ttu-id="23cb1-114">Dans `query1` , la `where` clause ( `Where` en Visual Basic) entraîne l’appel de la méthode par la requête <xref:System.Linq.Enumerable.Where%2A> .</span><span class="sxs-lookup"><span data-stu-id="23cb1-114">In `query1`, the `where` clause (`Where` in Visual Basic) causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="23cb1-115">Cette méthode est également implémentée en tant qu'itérateur.</span><span class="sxs-lookup"><span data-stu-id="23cb1-115">This method is also implemented as an iterator.</span></span> <span data-ttu-id="23cb1-116">Les tâches de configuration se composent de l'instanciation du délégué qui fera référence à l'expression, en plus de la configuration normale d'un itérateur.</span><span class="sxs-lookup"><span data-stu-id="23cb1-116">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="23cb1-117">A chaque itération, le délégué est appelé pour exécuter le prédicat.</span><span class="sxs-lookup"><span data-stu-id="23cb1-117">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="23cb1-118">Le travail d’installation et le travail effectué lors de chaque itération sont similaires au travail effectué lors de l’itération sur l’axe.</span><span class="sxs-lookup"><span data-stu-id="23cb1-118">The setup work and the work done during each iteration is similar to the work done while iterating through the axis.</span></span>
- <span data-ttu-id="23cb1-119">Dans `query1`, la clause select indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="23cb1-119">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="23cb1-120">Cette méthode fournit le même profil de performance que la méthode <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="23cb1-120">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>
- <span data-ttu-id="23cb1-121">Dans `query2` , la `where` clause ( `Where` en Visual Basic) et la `select` clause ont le même profil de performance que dans `query1` .</span><span class="sxs-lookup"><span data-stu-id="23cb1-121">In `query2`, both the `where` clause (`Where` in Visual Basic) and the `select` clause have the same performance profile as in `query1`.</span></span>

<span data-ttu-id="23cb1-122">L'itération sur `query2` est donc directement proportionnelle au nombre d'éléments de la source de la première requête, en d'autres termes, elle suit un algorithme linéaire.</span><span class="sxs-lookup"><span data-stu-id="23cb1-122">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

<span data-ttu-id="23cb1-123">Pour plus d’informations sur les itérateurs, consultez [yield](../../csharp/language-reference/keywords/yield.md).</span><span class="sxs-lookup"><span data-stu-id="23cb1-123">For more information on iterators, see [yield](../../csharp/language-reference/keywords/yield.md).</span></span>

<span data-ttu-id="23cb1-124">Pour obtenir un didacticiel plus détaillé sur le chaînage des requêtes, consultez [Didacticiel : chaînes de requêtes (C#)](chain-queries-example.md).</span><span class="sxs-lookup"><span data-stu-id="23cb1-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chain queries together (C#)](chain-queries-example.md).</span></span>
