---
title: 'Procédure : Appeler des fonctions inline définies par l’utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 26eafb9a6ea1a0b416d205e94b0e420b0f4059d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941070"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="51bac-102">Procédure : Appeler des fonctions inline définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="51bac-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="51bac-103">Bien que vous puissiez appeler des fonctions inline définies par l'utilisateur, les fonctions incluses dans une requête dont l'exécution est différée ne sont pas exécutées tant que la requête n'est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="51bac-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="51bac-104">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="51bac-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="51bac-105">Lorsque vous appelez la même fonction à l'extérieur d'une requête, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée une requête simple à partir de l'expression d'appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="51bac-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="51bac-106">La syntaxe SQL (le paramètre `@p0` est lié à la constante passée) se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="51bac-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="51bac-107">crée les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="51bac-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="51bac-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="51bac-108">Example</span></span>  
 <span data-ttu-id="51bac-109">Dans la requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suivante, vous pouvez voir un appel Inline à la méthode `ReverseCustName`de fonction définie par l’utilisateur générée.</span><span class="sxs-lookup"><span data-stu-id="51bac-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="51bac-110">La fonction n'est pas exécutée immédiatement, car l'exécution de la requête est différée.</span><span class="sxs-lookup"><span data-stu-id="51bac-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="51bac-111">Le SQL généré pour cette requête se traduit en un appel à la fonction définie par l'utilisateur dans la base de données (consultez le code SQL suivant la requête).</span><span class="sxs-lookup"><span data-stu-id="51bac-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="51bac-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51bac-112">See also</span></span>

- [<span data-ttu-id="51bac-113">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="51bac-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
