---
title: 'Procédure : Utiliser des procédures stockées mappées pour des formes de résultats séquentielles'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: bae10e823a274304f21292cf55947a4d4eaccc10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781455"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="aafa1-102">Procédure : Utiliser des procédures stockées mappées pour des formes de résultats séquentielles</span><span class="sxs-lookup"><span data-stu-id="aafa1-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="aafa1-103">Ce type de procédure stockée peut générer plusieurs formes de résultats, mais vous savez dans quel ordre les résultats sont retournés.</span><span class="sxs-lookup"><span data-stu-id="aafa1-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="aafa1-104">Comparez ce scénario à celui dans lequel vous ne connaissez pas la séquence des retours.</span><span class="sxs-lookup"><span data-stu-id="aafa1-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="aafa1-105">Pour plus d'informations, voir [Procédure : Utilisez des procédures stockées mappées pour plusieurs formes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)de résultats.</span><span class="sxs-lookup"><span data-stu-id="aafa1-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aafa1-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="aafa1-106">Example</span></span>  
 <span data-ttu-id="aafa1-107">Le T-SQL d'une procédure stockée qui retourne plusieurs formes de résultats de manière séquentielle est présenté ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="aafa1-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="aafa1-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="aafa1-108">Example</span></span>  
 <span data-ttu-id="aafa1-109">Vous pouvez utiliser un code semblable à celui qui suit pour exécuter cette procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="aafa1-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="aafa1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aafa1-110">See also</span></span>

- [<span data-ttu-id="aafa1-111">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="aafa1-111">Stored Procedures</span></span>](stored-procedures.md)
