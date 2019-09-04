---
title: 'Procédure : Appeler des fonctions canoniques'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 3ad4576a5c7a3f2be4b68e4060df191932ceeb19
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250827"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="4051e-102">Procédure : Appeler des fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="4051e-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="4051e-103">La classe <xref:System.Data.Objects.EntityFunctions> contient des méthodes qui exposent les fonctions canoniques à utiliser dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4051e-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="4051e-104">Pour plus d’informations sur les fonctions canoniques, consultez [Fonctions canoniques](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4051e-104">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4051e-105">Les méthodes <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> et <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> dans la classe <xref:System.Data.Objects.EntityFunctions> n'ont pas d'équivalents de fonction canonique.</span><span class="sxs-lookup"><span data-stu-id="4051e-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="4051e-106">Les fonctions canoniques qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique (également appelées fonctions canoniques d'agrégation) peuvent être appelées directement.</span><span class="sxs-lookup"><span data-stu-id="4051e-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="4051e-107">Les autres fonctions canoniques peuvent être appelées uniquement dans le cadre d'une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4051e-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="4051e-108">Pour appeler directement une fonction d'agrégation, vous devez passer un objet <xref:System.Data.Objects.ObjectQuery%601> à la fonction.</span><span class="sxs-lookup"><span data-stu-id="4051e-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="4051e-109">Pour plus d'informations, consultez le second exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="4051e-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="4051e-110">Vous pouvez appeler certaines fonctions canoniques en utilisant des méthodes CLR (Common Language Runtime) dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4051e-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="4051e-111">Pour obtenir la liste des méthodes CLR qui mappent aux fonctions canoniques, consultez [méthode CLR pour le mappage de fonction canonique](clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="4051e-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4051e-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="4051e-112">Example</span></span>  
 <span data-ttu-id="4051e-113">L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="4051e-113">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="4051e-114">L'exemple exécute une requête LINQ to Entities qui utilise la méthode <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> pour retourner tous les produits pour lesquels la différence entre `SellEndDate` et `SellStartDate` est inférieure à 365 jours :</span><span class="sxs-lookup"><span data-stu-id="4051e-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="4051e-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="4051e-115">Example</span></span>  
 <span data-ttu-id="4051e-116">L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="4051e-116">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="4051e-117">L'exemple appelle directement la méthode <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> d'agrégation pour retourner l'écart type des sous-totaux `SalesOrderHeader`.</span><span class="sxs-lookup"><span data-stu-id="4051e-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="4051e-118">Notez qu'un <xref:System.Data.Objects.ObjectQuery%601> est passé à la fonction, ce qui lui permet d'être appelée même si elle ne figure pas dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="4051e-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4051e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4051e-119">See also</span></span>

- [<span data-ttu-id="4051e-120">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4051e-120">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="4051e-121">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4051e-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
