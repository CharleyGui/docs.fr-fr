---
title: 'Procédure : Insérer des lignes dans la base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 8186b90a666a7b75ce626cccb7cc28af38de7c5b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781860"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="80933-102">Procédure : Insérer des lignes dans la base de données</span><span class="sxs-lookup"><span data-stu-id="80933-102">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="80933-103">Vous insérez des lignes dans une base de données en ajoutant des [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objets à la collection associée <xref:System.Data.Linq.Table%601> , puis en soumettant les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="80933-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="80933-104">traduit vos modifications en commandes SQL `INSERT` appropriées.</span><span class="sxs-lookup"><span data-stu-id="80933-104">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="80933-105">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="80933-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="80933-106">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="80933-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="80933-107">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.</span><span class="sxs-lookup"><span data-stu-id="80933-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="80933-108">Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="80933-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="80933-109">Pour plus d'informations, voir [Procédure : Connectez-vous à](how-to-connect-to-a-database.md)une base de données.</span><span class="sxs-lookup"><span data-stu-id="80933-109">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="80933-110">Pour insérer une ligne dans la base de données</span><span class="sxs-lookup"><span data-stu-id="80933-110">To insert a row into the database</span></span>

1. <span data-ttu-id="80933-111">Créez un objet qui inclut les données de colonne à soumettre.</span><span class="sxs-lookup"><span data-stu-id="80933-111">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="80933-112">Ajoutez le nouvel objet à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associée à la table cible dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="80933-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="80933-113">Soumettez la modification à la base de données.</span><span class="sxs-lookup"><span data-stu-id="80933-113">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="80933-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="80933-114">Example</span></span>

<span data-ttu-id="80933-115">L'exemple de code suivant crée un objet de type `Order` et le remplit avec les valeurs appropriées.</span><span class="sxs-lookup"><span data-stu-id="80933-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="80933-116">Il ajoute ensuite le nouvel objet à la collection `Order`.</span><span class="sxs-lookup"><span data-stu-id="80933-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="80933-117">Enfin, il soumet la modification à la base de données comme une nouvelle ligne de la table `Orders`.</span><span class="sxs-lookup"><span data-stu-id="80933-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="80933-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80933-118">See also</span></span>

- [<span data-ttu-id="80933-119">Guide pratique pour Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="80933-119">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="80933-120">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="80933-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="80933-121">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="80933-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="80933-122">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="80933-122">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
