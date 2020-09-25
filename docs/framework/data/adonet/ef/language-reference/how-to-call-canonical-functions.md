---
title: 'Comment : appeler des fonctions de chaînes canoniques'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: acfbdbaf21fe1d454b68dfef5bf4f88d8020ea65
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204448"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="3b02b-102">Comment : appeler des fonctions de chaînes canoniques</span><span class="sxs-lookup"><span data-stu-id="3b02b-102">How to: Call Canonical Functions</span></span>

<span data-ttu-id="3b02b-103">La classe <xref:System.Data.Objects.EntityFunctions> contient des méthodes qui exposent les fonctions canoniques à utiliser dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3b02b-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="3b02b-104">Pour plus d’informations sur les fonctions canoniques, consultez [Fonctions canoniques](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3b02b-104">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b02b-105">Les méthodes <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> et <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> dans la classe <xref:System.Data.Objects.EntityFunctions> n'ont pas d'équivalents de fonction canonique.</span><span class="sxs-lookup"><span data-stu-id="3b02b-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="3b02b-106">Les fonctions canoniques qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique (également appelées fonctions canoniques d'agrégation) peuvent être appelées directement.</span><span class="sxs-lookup"><span data-stu-id="3b02b-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="3b02b-107">Les autres fonctions canoniques peuvent être appelées uniquement dans le cadre d'une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3b02b-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="3b02b-108">Pour appeler directement une fonction d'agrégation, vous devez passer un objet <xref:System.Data.Objects.ObjectQuery%601> à la fonction.</span><span class="sxs-lookup"><span data-stu-id="3b02b-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="3b02b-109">Pour plus d'informations, consultez le second exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3b02b-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="3b02b-110">Vous pouvez appeler certaines fonctions canoniques en utilisant des méthodes CLR (Common Language Runtime) dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3b02b-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="3b02b-111">Pour obtenir la liste des méthodes CLR qui mappent aux fonctions canoniques, consultez [méthode CLR pour le mappage de fonction canonique](clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3b02b-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b02b-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b02b-112">Example</span></span>  

 <span data-ttu-id="3b02b-113">L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="3b02b-113">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="3b02b-114">L'exemple exécute une requête LINQ to Entities qui utilise la méthode <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> pour retourner tous les produits pour lesquels la différence entre `SellEndDate` et `SellStartDate` est inférieure à 365 jours :</span><span class="sxs-lookup"><span data-stu-id="3b02b-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="3b02b-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b02b-115">Example</span></span>  

 <span data-ttu-id="3b02b-116">L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="3b02b-116">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="3b02b-117">L'exemple appelle directement la méthode <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> d'agrégation pour retourner l'écart type des sous-totaux `SalesOrderHeader`.</span><span class="sxs-lookup"><span data-stu-id="3b02b-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="3b02b-118">Notez qu'un <xref:System.Data.Objects.ObjectQuery%601> est passé à la fonction, ce qui lui permet d'être appelée même si elle ne figure pas dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="3b02b-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3b02b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b02b-119">See also</span></span>

- [<span data-ttu-id="3b02b-120">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3b02b-120">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="3b02b-121">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3b02b-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
