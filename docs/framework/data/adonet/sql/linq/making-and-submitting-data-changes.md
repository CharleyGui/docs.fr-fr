---
title: Apport et soumission de modifications de données
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 23dc45c990763e69b41608f6c3ec15a8db17bf23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743007"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="5ed0d-102">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="5ed0d-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="5ed0d-103">Les rubriques de cette section décrivent comment effectuer et transmettre des modifications à la base de données et comment gérer des conflits d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ed0d-104">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="5ed0d-105">Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5ed0d-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="5ed0d-106">Les développeurs qui utilisent Visual Studio peuvent utiliser le concepteur objet/relationnel pour développer des procédures stockées dans le même but.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ed0d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ed0d-107">In This Section</span></span>  
 [<span data-ttu-id="5ed0d-108">Guide pratique : Insérer des lignes dans la base de données</span><span class="sxs-lookup"><span data-stu-id="5ed0d-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="5ed0d-109">Explique comment insérer des lignes dans la base de données en ajoutant des objets au modèle objet.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="5ed0d-110">Guide pratique pour Mettre à jour des lignes dans la base de données</span><span class="sxs-lookup"><span data-stu-id="5ed0d-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="5ed0d-111">Explique comment mettre à jour des lignes dans la base de données en mettant à jour des objets du modèle objet.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="5ed0d-112">Guide pratique : Supprimer des lignes de la base de données</span><span class="sxs-lookup"><span data-stu-id="5ed0d-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="5ed0d-113">Explique comment supprimer des lignes de la base de données en supprimant des objets du modèle objet.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="5ed0d-114">Guide pratique : Soumettre des modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="5ed0d-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="5ed0d-115">Explique comment envoyer des modifications de modèle objet à la base de données.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="5ed0d-116">Guide pratique : Envoi de données entre parenthèses à l’aide de Transactions</span><span class="sxs-lookup"><span data-stu-id="5ed0d-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="5ed0d-117">Explique comment inclure des opérations dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="5ed0d-118">Guide pratique : Créer dynamiquement une base de données</span><span class="sxs-lookup"><span data-stu-id="5ed0d-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="5ed0d-119">Explique comment générer dynamiquement des bases de données et des scénarios classiques pour cette approche.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="5ed0d-120">Guide pratique pour Gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="5ed0d-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="5ed0d-121">Propose des techniques pour traiter les problèmes d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="5ed0d-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
