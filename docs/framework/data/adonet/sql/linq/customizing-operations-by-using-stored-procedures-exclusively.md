---
title: Personnalisation d'opérations à l'aide de procédures stockées uniquement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 78db5cf448a19056d7265ab84d97d055748c3faa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164322"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="1358e-102">Personnalisation d'opérations à l'aide de procédures stockées uniquement</span><span class="sxs-lookup"><span data-stu-id="1358e-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>

<span data-ttu-id="1358e-103">L'accès aux données se fait couramment à l'aide de procédures stockées uniquement.</span><span class="sxs-lookup"><span data-stu-id="1358e-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1358e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="1358e-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1358e-105">Description</span><span class="sxs-lookup"><span data-stu-id="1358e-105">Description</span></span>  

 <span data-ttu-id="1358e-106">Vous pouvez modifier l’exemple fourni dans [Personnalisation des opérations à l’aide de procédures stockées](customizing-operations-by-using-stored-procedures.md) en remplaçant même la première requête (qui provoque une exécution SQL dynamique) par un appel de méthode qui encapsule une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="1358e-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="1358e-107">Supposons que `CustomersByCity` est la méthode, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1358e-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1358e-108">Code</span><span class="sxs-lookup"><span data-stu-id="1358e-108">Code</span></span>  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="1358e-109">Le code suivant s'exécute sans SQL dynamique.</span><span class="sxs-lookup"><span data-stu-id="1358e-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="1358e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1358e-110">See also</span></span>

- [<span data-ttu-id="1358e-111">Responsabilités du développeur en matière de substitution du comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="1358e-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)
