---
title: Retourner une requête à partir d’une méthode
description: Comment retourner une requête.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972524"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="59b0d-103">Comment retourner une requête à partir d’une méthodeC# (Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="59b0d-103">How to return a query from a method (C# Programming Guide)</span></span>
<span data-ttu-id="59b0d-104">Cet exemple montre comment retourner une requête à partir d’une méthode en tant que valeur de retour et en tant que paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="59b0d-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="59b0d-105">Les objets de requête sont composables, ce qui signifie que vous pouvez retourner une requête à partir d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="59b0d-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="59b0d-106">Les objets qui représentent des requêtes ne stockent pas la collection résultante, mais plutôt les étapes pour générer les résultats lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="59b0d-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="59b0d-107">L’avantage de retourner des objets de requête à partir de méthodes est qu’il est possible de les composer ou modifier encore.</span><span class="sxs-lookup"><span data-stu-id="59b0d-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="59b0d-108">Par conséquent, toute valeur de retour ou paramètre `out` d’une méthode qui retourne une requête doit également avoir ce type.</span><span class="sxs-lookup"><span data-stu-id="59b0d-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="59b0d-109">Si une méthode matérialise une requête en un type <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concret, elle est considérée comme retournant les résultats de la requête plutôt que la requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="59b0d-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="59b0d-110">Une variable de requête retournée à partir d’une méthode peut encore être composée ou modifiée.</span><span class="sxs-lookup"><span data-stu-id="59b0d-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b0d-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="59b0d-111">Example</span></span>  
 <span data-ttu-id="59b0d-112">Dans l’exemple suivant, la première méthode retourne une requête comme valeur de retour et la seconde méthode retourne une requête comme paramètre `out`.</span><span class="sxs-lookup"><span data-stu-id="59b0d-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="59b0d-113">Notez que, dans les deux cas, une requête est retournée et non pas les résultats d’une requête.</span><span class="sxs-lookup"><span data-stu-id="59b0d-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="59b0d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59b0d-114">See also</span></span>

- [<span data-ttu-id="59b0d-115">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="59b0d-115">Language Integrated Query (LINQ)</span></span>](index.md)
