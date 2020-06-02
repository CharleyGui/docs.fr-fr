---
title: "Comment : utiliser des fonctions table définies par l'utilisateur"
description: Utilisez ces exemples pour apprendre à créer une fonction table, qui retourne un ensemble de lignes unique. Utilisez une telle fonction table comme une table.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 44866367393e321d7dd2db965e2fad8a2e6b63e9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286324"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="202ca-104">Comment : utiliser des fonctions table définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="202ca-104">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="202ca-105">Une fonction table retourne un jeu de lignes unique (contrairement aux procédures stockées qui peuvent retourner plusieurs formes de résultats).</span><span class="sxs-lookup"><span data-stu-id="202ca-105">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="202ca-106">Étant donné que le type de retour d’une fonction table est `Table`, vous pouvez utiliser une fonction table à tout endroit dans SQL où il est possible d’utiliser une table.</span><span class="sxs-lookup"><span data-stu-id="202ca-106">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="202ca-107">Vous pouvez également utiliser la fonction table comme une table.</span><span class="sxs-lookup"><span data-stu-id="202ca-107">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="202ca-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="202ca-108">Example</span></span>  
 <span data-ttu-id="202ca-109">La fonction SQL suivante déclare explicitement qu'elle retourne un `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="202ca-109">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="202ca-110">Par conséquent, la structure de jeu de lignes retournée est définie implicitement.</span><span class="sxs-lookup"><span data-stu-id="202ca-110">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="202ca-111">mappe la fonction comme suit :</span><span class="sxs-lookup"><span data-stu-id="202ca-111">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="202ca-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="202ca-112">Example</span></span>  
 <span data-ttu-id="202ca-113">Le code SQL suivant montre que vous pouvez spécifier la jointure à la table que la fonction retourne et l'utiliser également comme n'importe quelle autre table :</span><span class="sxs-lookup"><span data-stu-id="202ca-113">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="202ca-114">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la requête serait restituée comme suit :</span><span class="sxs-lookup"><span data-stu-id="202ca-114">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="202ca-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="202ca-115">See also</span></span>

- [<span data-ttu-id="202ca-116">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="202ca-116">User-Defined Functions</span></span>](user-defined-functions.md)
