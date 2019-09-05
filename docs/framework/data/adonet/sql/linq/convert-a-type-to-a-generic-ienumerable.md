---
title: 'Comment : convertir un type en IEnumerable générique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c92f65c22fe4b4128a171c757bb9e9c0ccbc3fee
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247730"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="fd9ca-102">Comment : convertir un type en IEnumerable générique</span><span class="sxs-lookup"><span data-stu-id="fd9ca-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="fd9ca-103">Utilisez <xref:System.Linq.Enumerable.AsEnumerable%2A> pour retourner l'argument typé comme un `IEnumerable` générique.</span><span class="sxs-lookup"><span data-stu-id="fd9ca-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd9ca-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd9ca-104">Example</span></span>  
 <span data-ttu-id="fd9ca-105">Dans cet exemple, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (à l'aide du `Query` générique par défaut) tente de convertir la requête en SQL et de l'exécuter sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fd9ca-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="fd9ca-106">Toutefois, la clause `where` fait référence à une méthode côté client définie par l'utilisateur (`isValidProduct`) qui ne peut pas être convertie en SQL.</span><span class="sxs-lookup"><span data-stu-id="fd9ca-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="fd9ca-107">La solution consiste à spécifier l'implémentation <xref:System.Collections.Generic.IEnumerable%601> générique côté client de `where` pour remplacer le <xref:System.Linq.IQueryable%601> générique.</span><span class="sxs-lookup"><span data-stu-id="fd9ca-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="fd9ca-108">Vous pouvez pour cela appeler l'opérateur <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd9ca-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="fd9ca-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd9ca-109">See also</span></span>

- [<span data-ttu-id="fd9ca-110">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="fd9ca-110">Query Examples</span></span>](query-examples.md)
