---
title: 'Procédure : Utiliser des procédures stockées mappées pour plusieurs formes de résultats'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 26cc30790da26949fba889106d060cdef89013a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185000"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="e42f0-102">Procédure : Utiliser des procédures stockées mappées pour plusieurs formes de résultats</span><span class="sxs-lookup"><span data-stu-id="e42f0-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>

<span data-ttu-id="e42f0-103">Lorsqu'une procédure stockée peut retourner plusieurs formes de résultats, le type de retour ne peut pas être fortement typé en une forme de projection unique.</span><span class="sxs-lookup"><span data-stu-id="e42f0-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="e42f0-104">Bien que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] puisse générer tous les types de projection possibles, il ne peut pas connaître l’ordre dans lequel ils sont retournés.</span><span class="sxs-lookup"><span data-stu-id="e42f0-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="e42f0-105">Comparez ce scénario avec les procédures stockées qui produisent plusieurs formes de résultats de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="e42f0-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="e42f0-106">Pour plus d’informations, consultez [Comment : utiliser des procédures stockées mappées pour des formes de résultats séquentielles](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="e42f0-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="e42f0-107">L'attribut <xref:System.Data.Linq.Mapping.ResultTypeAttribute> est appliqué aux procédures stockées qui retournent plusieurs types de résultats pour spécifier l'ensemble de types que la procédure peut retourner.</span><span class="sxs-lookup"><span data-stu-id="e42f0-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e42f0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e42f0-108">Example</span></span>  

 <span data-ttu-id="e42f0-109">Dans l'exemple de code SQL suivant, la forme du résultat dépend de l'entrée (`shape =1` ou `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="e42f0-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="e42f0-110">Vous ne savez pas quelle sera la première projection retournée.</span><span class="sxs-lookup"><span data-stu-id="e42f0-110">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="e42f0-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="e42f0-111">Example</span></span>  

 <span data-ttu-id="e42f0-112">Vous pouvez utiliser un code semblable à celui qui suit pour exécuter cette procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="e42f0-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e42f0-113">Vous devez utiliser le modèle <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pour obtenir un énumérateur du type approprié, basé sur votre connaissance de la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="e42f0-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e42f0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e42f0-114">See also</span></span>

- [<span data-ttu-id="e42f0-115">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="e42f0-115">Stored Procedures</span></span>](stored-procedures.md)
