---
title: 'Procédure : Récupérer des informations sur les conflits entre entités'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: e8c548ac632454d9c488ebd5f7b471f6759418fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155872"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="ffcda-102">Procédure : Récupérer des informations sur les conflits entre entités</span><span class="sxs-lookup"><span data-stu-id="ffcda-102">How to: Retrieve Entity Conflict Information</span></span>

<span data-ttu-id="ffcda-103">Vous pouvez utiliser des objets de la classe <xref:System.Data.Linq.ObjectChangeConflict> pour fournir des informations sur des conflits révélés par des exceptions <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="ffcda-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="ffcda-104">Pour plus d’informations, consultez [accès concurrentiel optimiste : vue d’ensemble](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ffcda-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffcda-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="ffcda-105">Example</span></span>  

 <span data-ttu-id="ffcda-106">L'exemple suivant itère au sein d'une liste de conflits cumulés.</span><span class="sxs-lookup"><span data-stu-id="ffcda-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ffcda-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffcda-107">See also</span></span>

- [<span data-ttu-id="ffcda-108">Procédure : Gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="ffcda-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
