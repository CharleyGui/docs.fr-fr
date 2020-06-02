---
title: 'Comment : insérer des lignes dans la base de données'
description: Apprenez à insérer des lignes dans une base de données en ajoutant des objets LINQ to SQL à une collection liée à une table. LINQ to SQL traduit les ajouts en commandes SQL INSERT.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286350"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="123fc-104">Comment : insérer des lignes dans la base de données</span><span class="sxs-lookup"><span data-stu-id="123fc-104">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="123fc-105">Vous insérez des lignes dans une base de données en ajoutant des objets à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection associée, puis en soumettant les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="123fc-105">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="123fc-106">traduit vos modifications en commandes SQL appropriées `INSERT` .</span><span class="sxs-lookup"><span data-stu-id="123fc-106">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="123fc-107">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="123fc-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="123fc-108">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="123fc-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="123fc-109">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.</span><span class="sxs-lookup"><span data-stu-id="123fc-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="123fc-110">Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="123fc-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="123fc-111">Pour plus d’informations, consultez [Comment : se connecter à une base de données](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="123fc-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="123fc-112">Pour insérer une ligne dans la base de données</span><span class="sxs-lookup"><span data-stu-id="123fc-112">To insert a row into the database</span></span>

1. <span data-ttu-id="123fc-113">Créez un objet qui inclut les données de colonne à soumettre.</span><span class="sxs-lookup"><span data-stu-id="123fc-113">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="123fc-114">Ajoutez le nouvel objet à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associée à la table cible dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="123fc-114">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="123fc-115">Soumettez la modification à la base de données.</span><span class="sxs-lookup"><span data-stu-id="123fc-115">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="123fc-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="123fc-116">Example</span></span>

<span data-ttu-id="123fc-117">L'exemple de code suivant crée un objet de type `Order` et le remplit avec les valeurs appropriées.</span><span class="sxs-lookup"><span data-stu-id="123fc-117">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="123fc-118">Il ajoute ensuite le nouvel objet à la collection `Order`.</span><span class="sxs-lookup"><span data-stu-id="123fc-118">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="123fc-119">Enfin, il soumet la modification à la base de données comme une nouvelle ligne de la table `Orders`.</span><span class="sxs-lookup"><span data-stu-id="123fc-119">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="123fc-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="123fc-120">See also</span></span>

- [<span data-ttu-id="123fc-121">Comment : gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="123fc-121">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="123fc-122">Méthode DataContext (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="123fc-122">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="123fc-123">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="123fc-123">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="123fc-124">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="123fc-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
