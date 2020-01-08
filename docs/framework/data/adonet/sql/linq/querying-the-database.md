---
title: Interrogation de la base de données
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: 6ca402600d43eb84c31c499d3f93aca95d4ea1d9
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634311"
---
# <a name="querying-the-database"></a><span data-ttu-id="b08e7-102">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="b08e7-102">Querying the Database</span></span>
<span data-ttu-id="b08e7-103">Ce groupe de rubriques décrit comment développer et exécuter des requêtes dans les projets [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b08e7-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b08e7-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b08e7-104">In This Section</span></span>  
 [<span data-ttu-id="b08e7-105">Guide pratique pour demander des informations</span><span class="sxs-lookup"><span data-stu-id="b08e7-105">How to: Query for Information</span></span>](how-to-query-for-information.md)  
 <span data-ttu-id="b08e7-106">Montre brièvement comment [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requêtes sont fondamentalement les mêmes que les requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="b08e7-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as LINQ queries generally.</span></span>  
  
 [<span data-ttu-id="b08e7-107">Guide pratique pour récupérer des informations en lecture seule</span><span class="sxs-lookup"><span data-stu-id="b08e7-107">How to: Retrieve Information As Read-Only</span></span>](how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="b08e7-108">Explique comment augmenter les performances des requêtes lorsqu'aucune modification des données n'est planifiée.</span><span class="sxs-lookup"><span data-stu-id="b08e7-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="b08e7-109">Guide pratique pour contrôler la quantité de données liées récupérées</span><span class="sxs-lookup"><span data-stu-id="b08e7-109">How to: Control How Much Related Data Is Retrieved</span></span>](how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="b08e7-110">Explique comment contrôler le type de données connexes récupérées avec la cible principale.</span><span class="sxs-lookup"><span data-stu-id="b08e7-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="b08e7-111">Guide pratique pour filtrer des données liées</span><span class="sxs-lookup"><span data-stu-id="b08e7-111">How to: Filter Related Data</span></span>](how-to-filter-related-data.md)  
 <span data-ttu-id="b08e7-112">Explique comment récupérer les données connexes à l'aide d'une sous-requête.</span><span class="sxs-lookup"><span data-stu-id="b08e7-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="b08e7-113">Guide pratique pour désactiver le chargement différé</span><span class="sxs-lookup"><span data-stu-id="b08e7-113">How to: Turn Off Deferred Loading</span></span>](how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="b08e7-114">Explique comment désactiver le chargement différé.</span><span class="sxs-lookup"><span data-stu-id="b08e7-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="b08e7-115">Guide pratique pour exécuter directement des requêtes SQL</span><span class="sxs-lookup"><span data-stu-id="b08e7-115">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="b08e7-116">Explique comment soumettre des requêtes en utilisant le langage SQL.</span><span class="sxs-lookup"><span data-stu-id="b08e7-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="b08e7-117">Guide pratique pour stocker et réutiliser des requêtes</span><span class="sxs-lookup"><span data-stu-id="b08e7-117">How to: Store and Reuse Queries</span></span>](how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="b08e7-118">Explique comment compiler une requête une fois et l'utiliser plusieurs fois avec des paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="b08e7-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="b08e7-119">Guide pratique pour gérer les clés composites dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="b08e7-119">How to: Handle Composite Keys in Queries</span></span>](how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="b08e7-120">Explique comment inclure plusieurs colonnes dans une requête où l’opérateur accepte uniquement un argument.</span><span class="sxs-lookup"><span data-stu-id="b08e7-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="b08e7-121">Guide pratique pour récupérer plusieurs objets à la fois</span><span class="sxs-lookup"><span data-stu-id="b08e7-121">How to: Retrieve Many Objects At Once</span></span>](how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="b08e7-122">Explique comment utiliser <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="b08e7-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="b08e7-123">Guide pratique pour filtrer au niveau du DataContext</span><span class="sxs-lookup"><span data-stu-id="b08e7-123">How to: Filter at the DataContext Level</span></span>](how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="b08e7-124">Décrit une autre utilisation de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="b08e7-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="b08e7-125">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="b08e7-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="b08e7-126">Fournit de nombreux exemples de requêtes.</span><span class="sxs-lookup"><span data-stu-id="b08e7-126">Provides many examples of queries.</span></span>
