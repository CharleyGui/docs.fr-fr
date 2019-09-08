---
title: 'Procédure : Supprimer des lignes de la base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 421735567c527ac9a70cc5eefdbd7570599faac7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782007"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="59198-102">Procédure : Supprimer des lignes de la base de données</span><span class="sxs-lookup"><span data-stu-id="59198-102">How to: Delete Rows From the Database</span></span>

<span data-ttu-id="59198-103">Vous pouvez supprimer des lignes dans une base de données en [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supprimant les objets correspondants de leur collection liée à la table.</span><span class="sxs-lookup"><span data-stu-id="59198-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="59198-104">traduit vos modifications en commandes SQL `DELETE` appropriées.</span><span class="sxs-lookup"><span data-stu-id="59198-104">translates your changes to the appropriate SQL `DELETE` commands.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="59198-105">ne prend pas en charge ni ne reconnaît les opérations de suppression en cascade.</span><span class="sxs-lookup"><span data-stu-id="59198-105">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="59198-106">Si vous souhaitez supprimer une ligne dans une table comportant des contraintes sur cette suppression, vous devez terminer l'une des tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="59198-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>

- <span data-ttu-id="59198-107">Définissez la règle `ON DELETE CASCADE` dans la contrainte de clé étrangère dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="59198-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>

- <span data-ttu-id="59198-108">Utilisez votre propre code pour supprimer en premier les objets enfants qui empêchent la suppression de l'objet parent.</span><span class="sxs-lookup"><span data-stu-id="59198-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>

 <span data-ttu-id="59198-109">Sinon, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="59198-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="59198-110">Consultez le second exemple de code décrit plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="59198-110">See the second code example later in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="59198-111">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="59198-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="59198-112">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="59198-112">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="59198-113">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.</span><span class="sxs-lookup"><span data-stu-id="59198-113">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="59198-114">Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="59198-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="59198-115">Pour plus d’informations, consultez [Guide pratique pour Connectez-vous à](how-to-connect-to-a-database.md)une base de données.</span><span class="sxs-lookup"><span data-stu-id="59198-115">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="59198-116">Pour supprimer une ligne de la base de données</span><span class="sxs-lookup"><span data-stu-id="59198-116">To delete a row in the database</span></span>

1. <span data-ttu-id="59198-117">Interrogez la base de données concernant la ligne à supprimer.</span><span class="sxs-lookup"><span data-stu-id="59198-117">Query the database for the row to be deleted.</span></span>

2. <span data-ttu-id="59198-118">Appelez la méthode <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="59198-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>

3. <span data-ttu-id="59198-119">Soumettez la modification à la base de données.</span><span class="sxs-lookup"><span data-stu-id="59198-119">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="59198-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="59198-120">Example</span></span>

<span data-ttu-id="59198-121">Le premier exemple de code interroge la base de données à propos de détails de commande concernant la commande 11000, marque ces détails de commande pour suppression, et soumet ces modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="59198-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="59198-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="59198-122">Example</span></span>

<span data-ttu-id="59198-123">Dans ce second exemple, l'objectif est de supprimer une commande (10250).</span><span class="sxs-lookup"><span data-stu-id="59198-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="59198-124">Le code commence par examiner la table `OrderDetails` pour voir si la commande à supprimer y a des enfants.</span><span class="sxs-lookup"><span data-stu-id="59198-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="59198-125">Si la commande a des enfants, ces enfants sont marqués en vue de leur suppression, puis c'est au tour de la commande.</span><span class="sxs-lookup"><span data-stu-id="59198-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="59198-126">Le <xref:System.Data.Linq.DataContext> place les véritables suppressions dans l'ordre approprié afin que les commandes de suppression envoyées à la base de données se conforment aux contraintes de la base de données.</span><span class="sxs-lookup"><span data-stu-id="59198-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="59198-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59198-127">See also</span></span>

- [<span data-ttu-id="59198-128">Guide pratique pour Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="59198-128">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="59198-129">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="59198-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="59198-130">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="59198-130">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
