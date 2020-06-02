---
title: 'Comment : mettre à jour des lignes dans la base de données'
description: Apprenez à mettre à jour des lignes dans une base de données en modifiant des objets LINQ to SQL dans une collection liée à une table. LINQ to SQL traduit les ajouts dans les commandes de mise à jour SQL.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286337"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="7e212-104">Comment : mettre à jour des lignes dans la base de données</span><span class="sxs-lookup"><span data-stu-id="7e212-104">How to: Update Rows in the Database</span></span>

<span data-ttu-id="7e212-105">Vous pouvez mettre à jour des lignes dans une base de données en modifiant les valeurs de membre des objets associés à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection, puis en soumettant les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="7e212-105">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7e212-106">traduit vos modifications en commandes SQL appropriées `UPDATE` .</span><span class="sxs-lookup"><span data-stu-id="7e212-106">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="7e212-107">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="7e212-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="7e212-108">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7e212-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="7e212-109">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.</span><span class="sxs-lookup"><span data-stu-id="7e212-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="7e212-110">Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="7e212-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="7e212-111">Pour plus d’informations, consultez [Comment : se connecter à une base de données](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="7e212-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="7e212-112">Pour mettre à jour une ligne dans la base de données</span><span class="sxs-lookup"><span data-stu-id="7e212-112">To update a row in the database</span></span>

1. <span data-ttu-id="7e212-113">Interrogez la base de données concernant la ligne à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="7e212-113">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="7e212-114">Apportez les modifications souhaitées aux valeurs de membre dans l'objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obtenu.</span><span class="sxs-lookup"><span data-stu-id="7e212-114">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="7e212-115">Soumettez les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="7e212-115">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="7e212-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e212-116">Example</span></span>

<span data-ttu-id="7e212-117">L'exemple suivant interroge la base de données concernant la commande 11000, puis modifie les valeurs de `ShipName` et `ShipVia` dans l'objet `Order` obtenu.</span><span class="sxs-lookup"><span data-stu-id="7e212-117">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="7e212-118">Enfin, les modifications apportées à ces valeurs de membre sont soumises à la base de données comme modifications dans les colonnes `ShipName` et `ShipVia`.</span><span class="sxs-lookup"><span data-stu-id="7e212-118">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="7e212-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e212-119">See also</span></span>

- [<span data-ttu-id="7e212-120">Comment : gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="7e212-120">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="7e212-121">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="7e212-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="7e212-122">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="7e212-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
