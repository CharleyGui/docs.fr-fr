---
title: Effectuer des opérations de jointure à l'aide de clés composites (LINQ en C#)
description: Découvrez comment effectuer des opérations de jointure à l'aide de clés composites dans LINQ.
ms.date: 12/01/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: 460a52da7e0c0a47b77d4c64e76641bae9da7cd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659876"
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="33f9d-103">Effectuer des jointures à l’aide de clés composites</span><span class="sxs-lookup"><span data-stu-id="33f9d-103">Join by using composite keys</span></span>

<span data-ttu-id="33f9d-104">Cet exemple montre comment effectuer des opérations de jointure où vous voulez utiliser plusieurs clés pour définir une correspondance.</span><span class="sxs-lookup"><span data-stu-id="33f9d-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="33f9d-105">Ceci s’effectue à l’aide d’une clé composite.</span><span class="sxs-lookup"><span data-stu-id="33f9d-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="33f9d-106">Vous créez une clé composite en tant que type anonyme ou typé nommé avec les valeurs que vous voulez comparer.</span><span class="sxs-lookup"><span data-stu-id="33f9d-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="33f9d-107">Si la variable de requête doit être passée au-delà des limites de la méthode, utilisez un type nommé qui substitue <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> pour la clé.</span><span class="sxs-lookup"><span data-stu-id="33f9d-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="33f9d-108">Les noms des propriétés et l’ordre dans lequel elles se trouvent doivent être identiques dans chaque clé.</span><span class="sxs-lookup"><span data-stu-id="33f9d-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>

## <a name="example"></a><span data-ttu-id="33f9d-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="33f9d-109">Example</span></span>

<span data-ttu-id="33f9d-110">L’exemple suivant montre comment utiliser une clé composite pour joindre les données de trois tables :</span><span class="sxs-lookup"><span data-stu-id="33f9d-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

<span data-ttu-id="33f9d-111">L’inférence du type sur les clés composites dépend des noms des propriétés dans les clés et l’ordre dans lequel elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="33f9d-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="33f9d-112">Si les propriétés dans les séquences sources n’ont pas les mêmes noms, vous devez affecter de nouveaux noms dans les clés.</span><span class="sxs-lookup"><span data-stu-id="33f9d-112">If the properties in the source sequences don't have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="33f9d-113">Par exemple, si la table `Orders` et la table `OrderDetails` utilisent chacune des noms différents pour leurs colonnes, vous pouvez créer des clés composites en affectant des noms identiques dans les types anonymes :</span><span class="sxs-lookup"><span data-stu-id="33f9d-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

<span data-ttu-id="33f9d-114">Vous pouvez aussi utiliser des clés composites dans une clause `group`.</span><span class="sxs-lookup"><span data-stu-id="33f9d-114">Composite keys can be also used in a `group` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="33f9d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33f9d-115">See also</span></span>

- [<span data-ttu-id="33f9d-116">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="33f9d-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="33f9d-117">clause d’adhésion</span><span class="sxs-lookup"><span data-stu-id="33f9d-117">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="33f9d-118">group, clause</span><span class="sxs-lookup"><span data-stu-id="33f9d-118">group clause</span></span>](../language-reference/keywords/group-clause.md)
