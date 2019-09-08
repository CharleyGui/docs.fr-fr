---
title: Apport et soumission de modifications de données
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 18468c9a2018a28e85d87155d98b0853854013fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792967"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="75616-102">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="75616-102">Making and Submitting Data Changes</span></span>

<span data-ttu-id="75616-103">Les rubriques de cette section décrivent comment effectuer et transmettre des modifications à la base de données et comment gérer des conflits d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="75616-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="75616-104">Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.</span><span class="sxs-lookup"><span data-stu-id="75616-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="75616-105">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="75616-105">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="75616-106">Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.</span><span class="sxs-lookup"><span data-stu-id="75616-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="75616-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="75616-107">In This Section</span></span>

<span data-ttu-id="75616-108">[Guide pratique : Insérer des lignes dans la base de données](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="75616-108">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="75616-109">Explique comment insérer des lignes dans la base de données en ajoutant des objets au modèle objet.</span><span class="sxs-lookup"><span data-stu-id="75616-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="75616-110">[Guide pratique pour Mettre à jour des lignes dans la base de données](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="75616-110">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="75616-111">Explique comment mettre à jour des lignes dans la base de données en mettant à jour des objets du modèle objet.</span><span class="sxs-lookup"><span data-stu-id="75616-111">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="75616-112">[Guide pratique pour Supprimer des lignes de la base de données](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="75616-112">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="75616-113">Explique comment supprimer des lignes de la base de données en supprimant des objets du modèle objet.</span><span class="sxs-lookup"><span data-stu-id="75616-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="75616-114">[Guide pratique pour Envoyer les modifications à la base de données](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="75616-114">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="75616-115">Explique comment envoyer des modifications de modèle objet à la base de données.</span><span class="sxs-lookup"><span data-stu-id="75616-115">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="75616-116">[Guide pratique pour Mettre en fourchette les envois de données à l’aide de transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="75616-116">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="75616-117">Explique comment inclure des opérations dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="75616-117">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="75616-118">[Guide pratique pour Créer dynamiquement une base de données](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="75616-118">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="75616-119">Explique comment générer dynamiquement des bases de données et des scénarios classiques pour cette approche.</span><span class="sxs-lookup"><span data-stu-id="75616-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="75616-120">[Guide pratique pour Gérer les conflits de modification](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="75616-120">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="75616-121">Propose des techniques pour traiter les problèmes d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="75616-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
