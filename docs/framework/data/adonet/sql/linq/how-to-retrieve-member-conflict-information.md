---
title: 'Procédure : Récupérer des informations sur les conflits entre membres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 9d63b0b2c7d513d9f4db526b88a7c4e852637343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928629"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="32589-102">Procédure : Récupérer des informations sur les conflits entre membres</span><span class="sxs-lookup"><span data-stu-id="32589-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="32589-103">Vous pouvez utiliser la classe <xref:System.Data.Linq.MemberChangeConflict> pour récupérer des informations sur des membres individuels en conflit.</span><span class="sxs-lookup"><span data-stu-id="32589-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="32589-104">Dans ce contexte, vous pouvez assurer la gestion personnalisée du conflit pour un membre quelconque.</span><span class="sxs-lookup"><span data-stu-id="32589-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="32589-105">Pour plus d’informations, [consultez accès concurrentiel optimiste: Vue](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)d’ensemble.</span><span class="sxs-lookup"><span data-stu-id="32589-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32589-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="32589-106">Example</span></span>  
 <span data-ttu-id="32589-107">Le code suivant itère au sein des objets <xref:System.Data.Linq.ObjectChangeConflict>.</span><span class="sxs-lookup"><span data-stu-id="32589-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="32589-108">Pour chacun de ces objets, il itère ensuite au sein des objets <xref:System.Data.Linq.MemberChangeConflict>.</span><span class="sxs-lookup"><span data-stu-id="32589-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32589-109">Incluez <xref:System.Reflection> pour fournir des informations <xref:System.Data.Linq.MemberChangeConflict.Member%2A>.</span><span class="sxs-lookup"><span data-stu-id="32589-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="32589-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32589-110">See also</span></span>

- [<span data-ttu-id="32589-111">Guide pratique pour Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="32589-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
