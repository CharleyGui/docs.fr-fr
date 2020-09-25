---
title: 'Procédure : Utiliser des fonctions scalaires définies par l’utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: faf8d6e94c88575f6cb73003fa5bed87650d7d54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196934"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="4fd20-102">Procédure : Utiliser des fonctions scalaires définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="4fd20-102">How to: Use Scalar-Valued User-Defined Functions</span></span>

<span data-ttu-id="4fd20-103">Vous pouvez mapper une méthode cliente définie sur une classe à une fonction définie par l'utilisateur à l'aide de l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4fd20-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="4fd20-104">Notez que le corps de la méthode construit une expression qui capture l'intention de l'appel de méthode et passe cette expression au <xref:System.Data.Linq.DataContext> pour la traduire et l'exécuter.</span><span class="sxs-lookup"><span data-stu-id="4fd20-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fd20-105">L'exécution directe se produit uniquement si la fonction est appelée à l'extérieur d'une requête.</span><span class="sxs-lookup"><span data-stu-id="4fd20-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="4fd20-106">Pour plus d’informations, consultez [Comment : appeler des fonctions définies par l’utilisateur Inline](how-to-call-user-defined-functions-inline.md).</span><span class="sxs-lookup"><span data-stu-id="4fd20-106">For more information, see [How to: Call User-Defined Functions Inline](how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fd20-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="4fd20-107">Example</span></span>  

 <span data-ttu-id="4fd20-108">Le code SQL suivant présente une fonction scalaire `ReverseCustName()` définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4fd20-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 <span data-ttu-id="4fd20-109">Vous pouvez mapper une méthode cliente telle que la méthode suivante pour ce code :</span><span class="sxs-lookup"><span data-stu-id="4fd20-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4fd20-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fd20-110">See also</span></span>

- [<span data-ttu-id="4fd20-111">Fonctions définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4fd20-111">User-Defined Functions</span></span>](user-defined-functions.md)
