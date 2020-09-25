---
title: 'Procédure : Désactiver le chargement différé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: b2193e7e8bda396451274d2da96e7cb86774fd03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196960"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="6fd04-102">Procédure : Désactiver le chargement différé</span><span class="sxs-lookup"><span data-stu-id="6fd04-102">How to: Turn Off Deferred Loading</span></span>

<span data-ttu-id="6fd04-103">Vous pouvez désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.</span><span class="sxs-lookup"><span data-stu-id="6fd04-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="6fd04-104">Pour plus d’informations, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="6fd04-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fd04-105">Le chargement différé est désactivé lorsque le suivi d'objet est désactivé.</span><span class="sxs-lookup"><span data-stu-id="6fd04-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="6fd04-106">Pour plus d’informations, consultez [Comment : récupérer des informations en lecture seule](how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="6fd04-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd04-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="6fd04-107">Example</span></span>  

 <span data-ttu-id="6fd04-108">L'exemple suivant montre comment désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.</span><span class="sxs-lookup"><span data-stu-id="6fd04-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6fd04-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fd04-109">See also</span></span>

- [<span data-ttu-id="6fd04-110">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="6fd04-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="6fd04-111">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="6fd04-111">Querying the Database</span></span>](querying-the-database.md)
