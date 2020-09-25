---
title: 'Procédure : Afficher un ensemble de modifications ou ChangeSet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 288920567db75dc1d4c7273f698467063af52ed6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180775"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="255cc-102">Procédure : Afficher un ensemble de modifications ou ChangeSet</span><span class="sxs-lookup"><span data-stu-id="255cc-102">How to: Display a ChangeSet</span></span>

<span data-ttu-id="255cc-103">Vous pouvez consulter des modifications suivies par un <xref:System.Data.Linq.DataContext> à l'aide de <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span><span class="sxs-lookup"><span data-stu-id="255cc-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="255cc-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="255cc-104">Example</span></span>  

 <span data-ttu-id="255cc-105">L'exemple suivant récupère des clients dont la ville est Londres, remplace la ville par Paris et soumet les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="255cc-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="255cc-106">La sortie de ce code semble similaire aux éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="255cc-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="255cc-107">Notez que le résumé de fin indique que huit modifications ont été apportées.</span><span class="sxs-lookup"><span data-stu-id="255cc-107">Note that the summary at the end shows that eight changes were made.</span></span>  

 ```console
CustomerID: AROUT
   Original value: London
   Updated value: Paris
CustomerID: BSBEV
   Original value: London
   Updated value: Paris
CustomerID: CONSH
   Original value: London
   Updated value: Paris
CustomerID: EASTC
   Original value: London
   Updated value: Paris
CustomerID: NORTS
    Original value: London
    Updated value: Paris
CustomerID: PARIS
    Original value: London
    Updated value: Paris
CustomerID: SEVES
    Original value: London
    Updated value: Paris
CustomerID: SPECD
    Original value: London
    Updated value: Paris
Total changes: {Added: 0, Removed: 0, Modified: 8}
```
  
## <a name="see-also"></a><span data-ttu-id="255cc-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="255cc-108">See also</span></span>

- [<span data-ttu-id="255cc-109">Prise en charge du débogage</span><span class="sxs-lookup"><span data-stu-id="255cc-109">Debugging Support</span></span>](debugging-support.md)
