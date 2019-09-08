---
title: Interrogation de la base de données
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: 3c48879d8e3ae699ef749fc14923358174010aae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782070"
---
# <a name="querying-the-database"></a><span data-ttu-id="53925-102">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="53925-102">Querying the Database</span></span>
<span data-ttu-id="53925-103">Ce groupe de rubriques décrit comment développer et exécuter des requêtes dans les projets [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53925-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53925-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="53925-104">In This Section</span></span>  
 [<span data-ttu-id="53925-105">Guide pratique pour Demander des informations</span><span class="sxs-lookup"><span data-stu-id="53925-105">How to: Query for Information</span></span>](how-to-query-for-information.md)  
 <span data-ttu-id="53925-106">Montre brièvement comment les requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] s'apparentent généralement aux requêtes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53925-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="53925-107">Guide pratique pour Récupérer les informations en lecture seule</span><span class="sxs-lookup"><span data-stu-id="53925-107">How to: Retrieve Information As Read-Only</span></span>](how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="53925-108">Explique comment augmenter les performances des requêtes lorsqu'aucune modification des données n'est planifiée.</span><span class="sxs-lookup"><span data-stu-id="53925-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="53925-109">Guide pratique : Contrôler la quantité de données liées récupérées</span><span class="sxs-lookup"><span data-stu-id="53925-109">How to: Control How Much Related Data Is Retrieved</span></span>](how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="53925-110">Explique comment contrôler le type de données connexes récupérées avec la cible principale.</span><span class="sxs-lookup"><span data-stu-id="53925-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="53925-111">Guide pratique pour Filtrer les données associées</span><span class="sxs-lookup"><span data-stu-id="53925-111">How to: Filter Related Data</span></span>](how-to-filter-related-data.md)  
 <span data-ttu-id="53925-112">Explique comment récupérer les données connexes à l'aide d'une sous-requête.</span><span class="sxs-lookup"><span data-stu-id="53925-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="53925-113">Guide pratique : Désactiver le chargement différé</span><span class="sxs-lookup"><span data-stu-id="53925-113">How to: Turn Off Deferred Loading</span></span>](how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="53925-114">Explique comment désactiver le chargement différé.</span><span class="sxs-lookup"><span data-stu-id="53925-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="53925-115">Guide pratique pour Exécuter directement des requêtes SQL</span><span class="sxs-lookup"><span data-stu-id="53925-115">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="53925-116">Explique comment soumettre des requêtes en utilisant le langage SQL.</span><span class="sxs-lookup"><span data-stu-id="53925-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="53925-117">Guide pratique pour Stocker et réutiliser des requêtes</span><span class="sxs-lookup"><span data-stu-id="53925-117">How to: Store and Reuse Queries</span></span>](how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="53925-118">Explique comment compiler une requête une fois et l'utiliser plusieurs fois avec des paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="53925-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="53925-119">Guide pratique pour Gérer les clés composites dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="53925-119">How to: Handle Composite Keys in Queries</span></span>](how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="53925-120">Explique comment inclure plusieurs colonnes dans une requête où l’opérateur accepte uniquement un argument.</span><span class="sxs-lookup"><span data-stu-id="53925-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="53925-121">Guide pratique pour Récupérer plusieurs objets à la fois</span><span class="sxs-lookup"><span data-stu-id="53925-121">How to: Retrieve Many Objects At Once</span></span>](how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="53925-122">Explique comment utiliser <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="53925-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="53925-123">Guide pratique : Filtrer au niveau du DataContext</span><span class="sxs-lookup"><span data-stu-id="53925-123">How to: Filter at the DataContext Level</span></span>](how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="53925-124">Décrit une autre utilisation de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="53925-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="53925-125">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="53925-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="53925-126">Fournit de nombreux exemples de requêtes.</span><span class="sxs-lookup"><span data-stu-id="53925-126">Provides many examples of queries.</span></span>
