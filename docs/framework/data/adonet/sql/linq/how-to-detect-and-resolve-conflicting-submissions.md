---
title: 'Procédure : Détecter et résoudre des soumissions en conflit'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ff33196f83e2c0d8d759e4ffc3fb7442e8ba0e3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940092"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="99287-102">Procédure : Détecter et résoudre des soumissions en conflit</span><span class="sxs-lookup"><span data-stu-id="99287-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="99287-103">fournit de nombreuses ressources pour détecter et résoudre des conflits issus de modifications effectuées par plusieurs utilisateurs dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="99287-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="99287-104">Pour plus d'informations, voir [Procédure : Gérer les conflits](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)de modification.</span><span class="sxs-lookup"><span data-stu-id="99287-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99287-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="99287-105">Example</span></span>  
 <span data-ttu-id="99287-106">L’exemple suivant montre un `try` / `catch` bloc qui intercepte <xref:System.Data.Linq.ChangeConflictException> une exception.</span><span class="sxs-lookup"><span data-stu-id="99287-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="99287-107">La fenêtre de console affiche des informations sur les entités et les membres de chaque conflit.</span><span class="sxs-lookup"><span data-stu-id="99287-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99287-108">Vous devez inclure la directive `using System.Reflection` (`Imports System.Reflection` dans Visual Basic) pour prendre en charge la récupération d'informations.</span><span class="sxs-lookup"><span data-stu-id="99287-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="99287-109">Pour plus d'informations, consultez <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="99287-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="99287-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99287-110">See also</span></span>

- [<span data-ttu-id="99287-111">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="99287-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="99287-112">Guide pratique pour Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="99287-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
