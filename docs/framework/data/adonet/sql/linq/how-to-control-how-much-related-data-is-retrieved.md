---
title: 'Procédure : Contrôler la quantité de données associées récupérées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 77ac29eeeaa30ef438b635364dc8e883a0e4c158
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161332"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="c4d64-102">Procédure : Contrôler la quantité de données associées récupérées</span><span class="sxs-lookup"><span data-stu-id="c4d64-102">How to: Control How Much Related Data Is Retrieved</span></span>

<span data-ttu-id="c4d64-103">Utilisez la méthode <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> pour spécifier quelles données associées à votre cible principale doivent être récupérées simultanément.</span><span class="sxs-lookup"><span data-stu-id="c4d64-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="c4d64-104">Par exemple, si vous savez que vous aurez besoin d'informations relatives aux commandes des clients, vous pouvez utiliser <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> pour vous assurer que les informations relatives aux commandes sont récupérées en même temps que les informations relatives au client.</span><span class="sxs-lookup"><span data-stu-id="c4d64-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="c4d64-105">Cette approche permet de ne provoquer qu'un seul envoi à la base de données pour les deux ensembles d'informations.</span><span class="sxs-lookup"><span data-stu-id="c4d64-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4d64-106">Vous pouvez récupérer des données en rapport avec la cible principale de votre requête en récupérant un produit croisé sous forme d'une grande projection, par exemple en récupérant des commandes lorsque vous ciblez des clients.</span><span class="sxs-lookup"><span data-stu-id="c4d64-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="c4d64-107">Cependant, cette approche présente souvent des inconvénients.</span><span class="sxs-lookup"><span data-stu-id="c4d64-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="c4d64-108">Par exemple, les résultats sont uniquement des projections et non des entités qui peuvent être modifiées et être rendues persistantes par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4d64-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="c4d64-109">Et vous pouvez récupérer une grande quantité de données dont vous n'avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="c4d64-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4d64-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4d64-110">Example</span></span>  

 <span data-ttu-id="c4d64-111">Dans l'exemple suivant, toutes les `Orders` de tous les `Customers` dont la ville est London sont récupérés une fois la requête exécutée.</span><span class="sxs-lookup"><span data-stu-id="c4d64-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="c4d64-112">En conséquence, le fait d'accéder par la suite à la propriété `Orders` sur un objet `Customer` ne déclenche pas de nouvelle requête de la base de données.</span><span class="sxs-lookup"><span data-stu-id="c4d64-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c4d64-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4d64-113">See also</span></span>

- [<span data-ttu-id="c4d64-114">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="c4d64-114">Querying the Database</span></span>](querying-the-database.md)
