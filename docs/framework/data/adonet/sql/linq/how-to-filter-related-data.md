---
title: 'Procédure : Filtrer les données associées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e8e63c139f38d6de46390925428e18682a65818d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793604"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="e5e4e-102">Procédure : Filtrer les données associées</span><span class="sxs-lookup"><span data-stu-id="e5e4e-102">How to: Filter Related Data</span></span>
<span data-ttu-id="e5e4e-103">Utilisez la méthode <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> pour spécifier des sous-requêtes afin de limiter la quantité de données récupérées.</span><span class="sxs-lookup"><span data-stu-id="e5e4e-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5e4e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5e4e-104">Example</span></span>  
 <span data-ttu-id="e5e4e-105">Dans l'exemple suivant, la méthode <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limite les `Orders` récupérées à celles qui n'ont pas encore été expédiées aujourd'hui.</span><span class="sxs-lookup"><span data-stu-id="e5e4e-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="e5e4e-106">Sans cette approche, toutes les `Orders` auraient été récupérées bien que seul un sous-ensemble soit désiré.</span><span class="sxs-lookup"><span data-stu-id="e5e4e-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e5e4e-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5e4e-107">See also</span></span>

- [<span data-ttu-id="e5e4e-108">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="e5e4e-108">Querying the Database</span></span>](querying-the-database.md)
