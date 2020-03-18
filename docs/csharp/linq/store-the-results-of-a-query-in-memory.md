---
title: Stocker les résultats d’une requête dans la mémoire
description: Comment enregistrer les résultats.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633568"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="ae479-103">Stocker les résultats d’une requête dans la mémoire</span><span class="sxs-lookup"><span data-stu-id="ae479-103">Store the results of a query in memory</span></span>

<span data-ttu-id="ae479-104">Une requête est en fait un ensemble d’instructions permettant de récupérer et d’organiser des données.</span><span class="sxs-lookup"><span data-stu-id="ae479-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="ae479-105">Les requêtes sont exécutées de manière différée, à mesure que chaque élément dans le résultat est demandé.</span><span class="sxs-lookup"><span data-stu-id="ae479-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="ae479-106">Lorsque vous utilisez `foreach` pour effectuer une itération sur les résultats, les éléments sont retournés lorsque vous y accédez.</span><span class="sxs-lookup"><span data-stu-id="ae479-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="ae479-107">Pour évaluer une requête et stocker ses résultats sans exécuter une boucle `foreach`, appelez simplement l’une des méthodes suivantes sur la variable de requête :</span><span class="sxs-lookup"><span data-stu-id="ae479-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="ae479-108">Lorsque vous stockez les résultats de requête, nous vous recommandons d’assigner l’objet de collection retourné à une nouvelle variable, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ae479-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="ae479-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ae479-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="ae479-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae479-110">See also</span></span>

- [<span data-ttu-id="ae479-111">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ae479-111">Language Integrated Query (LINQ)</span></span>](index.md)
