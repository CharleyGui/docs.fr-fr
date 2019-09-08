---
title: 'Procédure : Récupérer des informations sur les conflits entre entités'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 766ede90b14f07e2799c2715daf62aaeeeaa83f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782238"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="6a075-102">Procédure : Récupérer des informations sur les conflits entre entités</span><span class="sxs-lookup"><span data-stu-id="6a075-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="6a075-103">Vous pouvez utiliser des objets de la classe <xref:System.Data.Linq.ObjectChangeConflict> pour fournir des informations sur des conflits révélés par des exceptions <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="6a075-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="6a075-104">Pour plus d’informations, [consultez accès concurrentiel optimiste : Vue](optimistic-concurrency-overview.md)d’ensemble.</span><span class="sxs-lookup"><span data-stu-id="6a075-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a075-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a075-105">Example</span></span>  
 <span data-ttu-id="6a075-106">L'exemple suivant itère au sein d'une liste de conflits cumulés.</span><span class="sxs-lookup"><span data-stu-id="6a075-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6a075-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a075-107">See also</span></span>

- [<span data-ttu-id="6a075-108">Guide pratique pour Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="6a075-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
