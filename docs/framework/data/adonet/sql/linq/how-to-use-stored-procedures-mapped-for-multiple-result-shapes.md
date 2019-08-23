---
title: 'Procédure : Utiliser des procédures stockées mappées pour plusieurs formes de résultats'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 22614be8e53d975c4efdf7004f41906c58639c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938695"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="ea799-102">Procédure : Utiliser des procédures stockées mappées pour plusieurs formes de résultats</span><span class="sxs-lookup"><span data-stu-id="ea799-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="ea799-103">Lorsqu'une procédure stockée peut retourner plusieurs formes de résultats, le type de retour ne peut pas être fortement typé en une forme de projection unique.</span><span class="sxs-lookup"><span data-stu-id="ea799-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="ea799-104">Bien [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] que puisse générer tous les types de projection possibles, il ne peut pas connaître l’ordre dans lequel ils sont retournés.</span><span class="sxs-lookup"><span data-stu-id="ea799-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="ea799-105">Comparez ce scénario avec les procédures stockées qui produisent plusieurs formes de résultats de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="ea799-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="ea799-106">Pour plus d’informations, consultez [Guide pratique pour Utilisez des procédures stockées mappées pour des formes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)de résultats séquentielles.</span><span class="sxs-lookup"><span data-stu-id="ea799-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="ea799-107">L'attribut <xref:System.Data.Linq.Mapping.ResultTypeAttribute> est appliqué aux procédures stockées qui retournent plusieurs types de résultats pour spécifier l'ensemble de types que la procédure peut retourner.</span><span class="sxs-lookup"><span data-stu-id="ea799-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea799-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea799-108">Example</span></span>  
 <span data-ttu-id="ea799-109">Dans l'exemple de code SQL suivant, la forme du résultat dépend de l'entrée (`shape =1` ou `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="ea799-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="ea799-110">Vous ne savez pas quelle sera la première projection retournée.</span><span class="sxs-lookup"><span data-stu-id="ea799-110">You do not know which projection will be returned first.</span></span>  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ea799-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea799-111">Example</span></span>  
 <span data-ttu-id="ea799-112">Vous pouvez utiliser un code semblable à celui qui suit pour exécuter cette procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ea799-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea799-113">Vous devez utiliser le modèle <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pour obtenir un énumérateur du type approprié, basé sur votre connaissance de la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="ea799-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ea799-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea799-114">See also</span></span>

- [<span data-ttu-id="ea799-115">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="ea799-115">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
