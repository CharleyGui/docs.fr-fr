---
title: 'Procédure : Désactiver le chargement différé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938674"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="89847-102">Procédure : Désactiver le chargement différé</span><span class="sxs-lookup"><span data-stu-id="89847-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="89847-103">Vous pouvez désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.</span><span class="sxs-lookup"><span data-stu-id="89847-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="89847-104">Pour plus d’informations, consultez [différé et chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="89847-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89847-105">Le chargement différé est désactivé lorsque le suivi d'objet est désactivé.</span><span class="sxs-lookup"><span data-stu-id="89847-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="89847-106">Pour plus d’informations, consultez [Guide pratique pour Récupérez les informations en lecture](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)seule.</span><span class="sxs-lookup"><span data-stu-id="89847-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89847-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="89847-107">Example</span></span>  
 <span data-ttu-id="89847-108">L'exemple suivant montre comment désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.</span><span class="sxs-lookup"><span data-stu-id="89847-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="89847-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89847-109">See also</span></span>

- [<span data-ttu-id="89847-110">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="89847-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="89847-111">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="89847-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
