---
title: 'Procédure : Désactiver le chargement différé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781655"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="a3d36-102">Procédure : Désactiver le chargement différé</span><span class="sxs-lookup"><span data-stu-id="a3d36-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="a3d36-103">Vous pouvez désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.</span><span class="sxs-lookup"><span data-stu-id="a3d36-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="a3d36-104">Pour plus d’informations, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="a3d36-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3d36-105">Le chargement différé est désactivé lorsque le suivi d'objet est désactivé.</span><span class="sxs-lookup"><span data-stu-id="a3d36-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="a3d36-106">Pour plus d’informations, consultez [Guide pratique pour Récupérez les informations en lecture](how-to-retrieve-information-as-read-only.md)seule.</span><span class="sxs-lookup"><span data-stu-id="a3d36-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3d36-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3d36-107">Example</span></span>  
 <span data-ttu-id="a3d36-108">L'exemple suivant montre comment désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.</span><span class="sxs-lookup"><span data-stu-id="a3d36-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a3d36-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3d36-109">See also</span></span>

- [<span data-ttu-id="a3d36-110">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="a3d36-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="a3d36-111">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="a3d36-111">Querying the Database</span></span>](querying-the-database.md)
