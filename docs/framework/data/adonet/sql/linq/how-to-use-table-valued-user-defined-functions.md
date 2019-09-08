---
title: 'Procédure : Utiliser des fonctions tables définies par l’utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 31797ae7d0fe23227cc4af733fbceac5d474f779
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781443"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="c01cf-102">Procédure : Utiliser des fonctions tables définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c01cf-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="c01cf-103">Une fonction table retourne un jeu de lignes unique (contrairement aux procédures stockées qui peuvent retourner plusieurs formes de résultats).</span><span class="sxs-lookup"><span data-stu-id="c01cf-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="c01cf-104">Étant donné que le type de retour d’une fonction table est `Table`, vous pouvez utiliser une fonction table à tout endroit dans SQL où il est possible d’utiliser une table.</span><span class="sxs-lookup"><span data-stu-id="c01cf-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="c01cf-105">Vous pouvez également utiliser la fonction table comme une table.</span><span class="sxs-lookup"><span data-stu-id="c01cf-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c01cf-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="c01cf-106">Example</span></span>  
 <span data-ttu-id="c01cf-107">La fonction SQL suivante déclare explicitement qu'elle retourne un `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="c01cf-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="c01cf-108">Par conséquent, la structure de jeu de lignes retournée est définie implicitement.</span><span class="sxs-lookup"><span data-stu-id="c01cf-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c01cf-109">mappe la fonction comme suit :</span><span class="sxs-lookup"><span data-stu-id="c01cf-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c01cf-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="c01cf-110">Example</span></span>  
 <span data-ttu-id="c01cf-111">Le code SQL suivant montre que vous pouvez spécifier la jointure à la table que la fonction retourne et l'utiliser également comme n'importe quelle autre table :</span><span class="sxs-lookup"><span data-stu-id="c01cf-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="c01cf-112">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la requête serait restituée comme suit :</span><span class="sxs-lookup"><span data-stu-id="c01cf-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c01cf-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c01cf-113">See also</span></span>

- [<span data-ttu-id="c01cf-114">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c01cf-114">User-Defined Functions</span></span>](user-defined-functions.md)
