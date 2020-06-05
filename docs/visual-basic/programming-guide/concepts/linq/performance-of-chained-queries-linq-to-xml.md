---
title: Performances des requêtes chaînées (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 6b87f2744f663ebd45dceb036dcaac71b80765fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396387"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="a5826-102">Performances des requêtes chaînées (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5826-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="a5826-103">L'un des principaux avantages de LINQ (et LINQ to XML) est que les requêtes chaînées peuvent offrir la même performance qu'une requête unique plus grande et plus complexe.</span><span class="sxs-lookup"><span data-stu-id="a5826-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="a5826-104">Une requête chaînée est une requête qui utilise une autre requête comme source.</span><span class="sxs-lookup"><span data-stu-id="a5826-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="a5826-105">Par exemple, dans le code simple suivant, `query2` utilise `query1` comme source :</span><span class="sxs-lookup"><span data-stu-id="a5826-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="a5826-106">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a5826-106">This example produces the following output:</span></span>

```console
4
```

<span data-ttu-id="a5826-107">Cette requête chaînée offre le même profil de performance que l'itération sur une liste liée.</span><span class="sxs-lookup"><span data-stu-id="a5826-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="a5826-108">L'axe <xref:System.Xml.Linq.XContainer.Elements%2A> offre essentiellement la même performance qu'une itération sur une liste liée.</span><span class="sxs-lookup"><span data-stu-id="a5826-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="a5826-109"><xref:System.Xml.Linq.XContainer.Elements%2A> est implémenté en tant qu'itérateur avec exécution différée.</span><span class="sxs-lookup"><span data-stu-id="a5826-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="a5826-110">Cela signifie qu'en plus de l'itération sur la liste liée, il effectue certaines tâches comme l'allocation de l'objet itérateur et le suivi de l'état d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a5826-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="a5826-111">Ces tâches peuvent être divisées en deux catégories : les tâches effectuées lors de la configuration de l'itérateur et les tâches effectuées à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="a5826-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="a5826-112">Les tâches de configuration représentent une part réduite et fixe du travail, tandis que les tâches effectuées à chaque itération sont proportionnelles au nombre d'éléments de la collection source.</span><span class="sxs-lookup"><span data-stu-id="a5826-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="a5826-113">Dans `query1`, la clause `Where` indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5826-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="a5826-114">Cette méthode est également implémentée en tant qu'itérateur.</span><span class="sxs-lookup"><span data-stu-id="a5826-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="a5826-115">Les tâches de configuration se composent de l'instanciation du délégué qui fera référence à l'expression, en plus de la configuration normale d'un itérateur.</span><span class="sxs-lookup"><span data-stu-id="a5826-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="a5826-116">A chaque itération, le délégué est appelé pour exécuter le prédicat.</span><span class="sxs-lookup"><span data-stu-id="a5826-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="a5826-117">Les tâches de configuration et les tâches effectuées à chaque itération sont similaires aux tâches effectuées lors de l'itération sur l'axe.</span><span class="sxs-lookup"><span data-stu-id="a5826-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="a5826-118">Dans `query1`, la clause select indique que la requête doit appeler la méthode <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5826-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="a5826-119">Cette méthode fournit le même profil de performance que la méthode <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5826-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="a5826-120">Dans `query2`, la clause `Where` et la `Select` clause ont toutes deux le même profil de performance que dans `query1`.</span><span class="sxs-lookup"><span data-stu-id="a5826-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="a5826-121">L'itération sur `query2` est donc directement proportionnelle au nombre d'éléments de la source de la première requête, en d'autres termes, elle suit un algorithme linéaire.</span><span class="sxs-lookup"><span data-stu-id="a5826-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5826-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5826-122">See also</span></span>

- [<span data-ttu-id="a5826-123">Performances (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5826-123">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)
