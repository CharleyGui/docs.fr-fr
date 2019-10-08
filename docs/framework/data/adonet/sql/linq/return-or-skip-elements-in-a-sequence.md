---
title: "Comment : retourner ou ignorer des éléments d'une séquence"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 7c98681493738b4e94ed14417fa1437efb6c12ac
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003312"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="f8078-102">Comment : retourner ou ignorer des éléments d'une séquence</span><span class="sxs-lookup"><span data-stu-id="f8078-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="f8078-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Take%2A> pour retourner un nombre donné d'éléments dans une séquence et ignorer le reste.</span><span class="sxs-lookup"><span data-stu-id="f8078-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="f8078-104">Utilisez l'opérateur <xref:System.Linq.Queryable.Skip%2A> pour ignorer un nombre donné d'éléments dans une séquence et retourner le reste.</span><span class="sxs-lookup"><span data-stu-id="f8078-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8078-105"><xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A> sont soumis à certaines limites lorsqu'ils sont utilisés dans des requêtes SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="f8078-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="f8078-106">Pour plus d’informations, consultez l’entrée « ignorer et prendre des exceptions dans SQL Server 2000 » dans [résolution des problèmes](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="f8078-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f8078-107">traduit <xref:System.Linq.Queryable.Skip%2A> en utilisant une sous-requête avec la clause SQL `NOT EXISTS`.</span><span class="sxs-lookup"><span data-stu-id="f8078-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="f8078-108">Cette traduction présente les limites suivantes :</span><span class="sxs-lookup"><span data-stu-id="f8078-108">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="f8078-109">L’argument doit être un jeu.</span><span class="sxs-lookup"><span data-stu-id="f8078-109">The argument must be a set.</span></span> <span data-ttu-id="f8078-110">Les multijeux ne sont pas pris en charge, même s'ils sont ordonnés.</span><span class="sxs-lookup"><span data-stu-id="f8078-110">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="f8078-111">La requête générée peut être beaucoup plus complexe que celle qui est générée pour la requête de base sur laquelle <xref:System.Linq.Queryable.Skip%2A> est appliqué.</span><span class="sxs-lookup"><span data-stu-id="f8078-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="f8078-112">Cette complexité peut entraîner une dégradation des performances ou un délai d'expiration.</span><span class="sxs-lookup"><span data-stu-id="f8078-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8078-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8078-113">Example</span></span>  
 <span data-ttu-id="f8078-114">L'exemple suivant utilise `Take` pour sélectionner les cinq premiers `Employees` embauchés.</span><span class="sxs-lookup"><span data-stu-id="f8078-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="f8078-115">Notez que la collection est d’abord triée par `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="f8078-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="f8078-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8078-116">Example</span></span>  
 <span data-ttu-id="f8078-117">L'exemple suivant utilise <xref:System.Linq.Queryable.Skip%2A> pour sélectionner tous les `Products` exceptés les dix produits les plus chers.</span><span class="sxs-lookup"><span data-stu-id="f8078-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="f8078-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8078-118">Example</span></span>  
 <span data-ttu-id="f8078-119">L'exemple suivant combine les méthodes <xref:System.Linq.Queryable.Skip%2A> et <xref:System.Linq.Queryable.Take%2A> pour ignorer les cinquante premiers enregistrements et retourner les dix suivants.</span><span class="sxs-lookup"><span data-stu-id="f8078-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="f8078-120">Les opérations <xref:System.Linq.Queryable.Take%2A> et <xref:System.Linq.Queryable.Skip%2A> sont bien définies uniquement sur les jeux ordonnés.</span><span class="sxs-lookup"><span data-stu-id="f8078-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="f8078-121">La sémantique des jeux ou des multijeux non ordonnés n'est pas définie.</span><span class="sxs-lookup"><span data-stu-id="f8078-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="f8078-122">Du fait des limitations de classement dans SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tente de déplacer le classement de l'argument de l'opérateur <xref:System.Linq.Queryable.Take%2A> ou <xref:System.Linq.Queryable.Skip%2A> vers le résultat de l'opérateur.</span><span class="sxs-lookup"><span data-stu-id="f8078-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8078-123">La traduction est différente pour SQL Server 2000 et SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="f8078-123">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="f8078-124">Si vous envisagez d’utiliser <xref:System.Linq.Queryable.Skip%2A> avec une requête de toute complexité, utilisez SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="f8078-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="f8078-125">Prenons la requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suivante pour SQL Server 2000 :</span><span class="sxs-lookup"><span data-stu-id="f8078-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f8078-126">déplace le classement à la fin du code SQL, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f8078-126">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="f8078-127">Lorsque <xref:System.Linq.Queryable.Take%2A> et <xref:System.Linq.Queryable.Skip%2A> sont enchaînés, l'ensemble du classement spécifié doit être cohérent.</span><span class="sxs-lookup"><span data-stu-id="f8078-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="f8078-128">Si ce n'est pas le cas, les résultats ne sont pas définis.</span><span class="sxs-lookup"><span data-stu-id="f8078-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="f8078-129">Pour les arguments intégraux constants non négatifs basés sur la spécification SQL, <xref:System.Linq.Queryable.Take%2A> et <xref:System.Linq.Queryable.Skip%2A> sont bien définis.</span><span class="sxs-lookup"><span data-stu-id="f8078-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8078-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8078-130">See also</span></span>

- [<span data-ttu-id="f8078-131">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="f8078-131">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="f8078-132">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="f8078-132">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
