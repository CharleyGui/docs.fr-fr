---
title: 'Procédure : Mettre à jour des lignes dans la base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: 2819cd5d2533e8e289735c3df2b39df952968e66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938735"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="ba1c6-102">Procédure : Mettre à jour des lignes dans la base de données</span><span class="sxs-lookup"><span data-stu-id="ba1c6-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="ba1c6-103">Vous pouvez mettre à jour des lignes dans une base de données en modifiant les valeurs de membre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] des objets associés à la <xref:System.Data.Linq.Table%601> collection, puis en soumettant les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ba1c6-104">traduit vos modifications en commandes SQL `UPDATE` appropriées.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba1c6-105">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="ba1c6-106">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ba1c6-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="ba1c6-107">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="ba1c6-108">Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="ba1c6-109">Pour plus d'informations, voir [Procédure : Connectez-vous à](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)une base de données.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="ba1c6-110">Pour mettre à jour une ligne dans la base de données</span><span class="sxs-lookup"><span data-stu-id="ba1c6-110">To update a row in the database</span></span>  
  
1. <span data-ttu-id="ba1c6-111">Interrogez la base de données concernant la ligne à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-111">Query the database for the row to be updated.</span></span>  
  
2. <span data-ttu-id="ba1c6-112">Apportez les modifications souhaitées aux valeurs de membre dans l'objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obtenu.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3. <span data-ttu-id="ba1c6-113">Soumettez les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba1c6-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba1c6-114">Example</span></span>  
 <span data-ttu-id="ba1c6-115">L'exemple suivant interroge la base de données concernant la commande 11000, puis modifie les valeurs de `ShipName` et `ShipVia` dans l'objet `Order` obtenu.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="ba1c6-116">Enfin, les modifications apportées à ces valeurs de membre sont soumises à la base de données comme modifications dans les colonnes `ShipName` et `ShipVia`.</span><span class="sxs-lookup"><span data-stu-id="ba1c6-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ba1c6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba1c6-117">See also</span></span>

- [<span data-ttu-id="ba1c6-118">Guide pratique : Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="ba1c6-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="ba1c6-119">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="ba1c6-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="ba1c6-120">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="ba1c6-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
