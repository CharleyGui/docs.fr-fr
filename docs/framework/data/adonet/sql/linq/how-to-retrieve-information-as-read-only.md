---
title: 'Procédure : Récupérer des informations en lecture seule'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 0a6853ef5d0b67e5efb95731adb5a106e8701e0f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155833"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="a7266-102">Procédure : Récupérer des informations en lecture seule</span><span class="sxs-lookup"><span data-stu-id="a7266-102">How to: Retrieve Information As Read-Only</span></span>

<span data-ttu-id="a7266-103">Lorsque vous ne projetez pas de modifier les données, vous pouvez augmenter les performances des requêtes en recherchant des résultats en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="a7266-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="a7266-104">Implémentez le traitement en lecture seule en affectant la valeur <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> à `false`.</span><span class="sxs-lookup"><span data-stu-id="a7266-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7266-105">Lorsque la valeur <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> est affectée à `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a implicitement la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="a7266-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7266-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7266-106">Example</span></span>  

 <span data-ttu-id="a7266-107">Le code suivant récupère une collection en lecture seule de dates d’embauche d’employés.</span><span class="sxs-lookup"><span data-stu-id="a7266-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a7266-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7266-108">See also</span></span>

- [<span data-ttu-id="a7266-109">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="a7266-109">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="a7266-110">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="a7266-110">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="a7266-111">Comparaison entre le chargement différé et le chargement immédiat</span><span class="sxs-lookup"><span data-stu-id="a7266-111">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
