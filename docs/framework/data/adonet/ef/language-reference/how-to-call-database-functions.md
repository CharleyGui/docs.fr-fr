---
title: 'Procédure : Appeler des fonctions de base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: c9cb8d32227447d3808dc250a39fef0867257a77
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250778"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="0aece-102">Procédure : Appeler des fonctions de base de données</span><span class="sxs-lookup"><span data-stu-id="0aece-102">How to: Call Database Functions</span></span>
<span data-ttu-id="0aece-103">La classe <xref:System.Data.Objects.SqlClient.SqlFunctions> contient des méthodes qui exposent les fonctions SQL Server à utiliser dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0aece-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="0aece-104">Lorsque vous utilisez des méthodes <xref:System.Data.Objects.SqlClient.SqlFunctions> dans les requêtes LINQ to Entities, les fonctions de base de données correspondantes sont exécutées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="0aece-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0aece-105">Les fonctions de base de données qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique (également appelées fonctions de base de données d'agrégation) peuvent être appelées directement.</span><span class="sxs-lookup"><span data-stu-id="0aece-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="0aece-106">Les autres fonctions canoniques peuvent être appelées uniquement dans le cadre d'une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0aece-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="0aece-107">Pour appeler directement une fonction d'agrégation, vous devez passer un objet <xref:System.Data.Objects.ObjectQuery%601> à la fonction.</span><span class="sxs-lookup"><span data-stu-id="0aece-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="0aece-108">Pour plus d'informations, consultez le second exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0aece-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0aece-109">Les méthodes dans la classe <xref:System.Data.Objects.SqlClient.SqlFunctions> sont spécifiques aux fonctions SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0aece-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="0aece-110">Des classes semblables qui exposent des fonctions de base de données peuvent être disponibles via d'autres fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="0aece-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aece-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="0aece-111">Example</span></span>  
 <span data-ttu-id="0aece-112">L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="0aece-112">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="0aece-113">L'exemple exécute une requête LINQ to Entities qui utilise la méthode <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> pour retourner tous les contacts dont le nom commence par « Si » :</span><span class="sxs-lookup"><span data-stu-id="0aece-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="0aece-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="0aece-114">Example</span></span>  
 <span data-ttu-id="0aece-115">L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="0aece-115">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="0aece-116">L'exemple appelle directement la méthode d'agrégation <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aece-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="0aece-117">Notez qu'un <xref:System.Data.Objects.ObjectQuery%601> est passé à la fonction, ce qui lui permet d'être appelée même si elle ne figure pas dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0aece-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0aece-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aece-118">See also</span></span>

- [<span data-ttu-id="0aece-119">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0aece-119">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="0aece-120">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0aece-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
