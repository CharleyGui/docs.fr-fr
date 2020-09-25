---
title: Exécution distante et exécution locale
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: c99e726902192fc8324e77441b80aa4519c55ddc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196947"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="61dd6-102">Exécution distante et exécution locale</span><span class="sxs-lookup"><span data-stu-id="61dd6-102">Remote vs. Local Execution</span></span>

<span data-ttu-id="61dd6-103">Vous pouvez décider d'exécuter vos requêtes à distance (autrement dit, le moteur de base de données exécute la requête sur la base de données) ou localement ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exécute la requête sur un cache local).</span><span class="sxs-lookup"><span data-stu-id="61dd6-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="61dd6-104">Communication à distance</span><span class="sxs-lookup"><span data-stu-id="61dd6-104">Remote Execution</span></span>  

 <span data-ttu-id="61dd6-105">Considérez la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="61dd6-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="61dd6-106">Si votre base de données contient des milliers de lignes de commandes, vous ne souhaitez pas toutes les récupérer pour traiter un petit sous-ensemble.</span><span class="sxs-lookup"><span data-stu-id="61dd6-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="61dd6-107">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la classe <xref:System.Data.Linq.EntitySet%601> implémente l'interface <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="61dd6-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="61dd6-108">Cette approche permet de s'assurer que de telles requêtes peuvent être exécutées à distance.</span><span class="sxs-lookup"><span data-stu-id="61dd6-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="61dd6-109">Deux avantages majeurs découlent de cette technique :</span><span class="sxs-lookup"><span data-stu-id="61dd6-109">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="61dd6-110">Les données inutiles ne sont pas récupérées.</span><span class="sxs-lookup"><span data-stu-id="61dd6-110">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="61dd6-111">Une requête exécutée par le moteur de base de données est souvent plus efficace en raison des index de la base de données.</span><span class="sxs-lookup"><span data-stu-id="61dd6-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="61dd6-112">Exécution locale</span><span class="sxs-lookup"><span data-stu-id="61dd6-112">Local Execution</span></span>  

 <span data-ttu-id="61dd6-113">Dans d'autres situations, vous pouvez souhaiter disposer du jeu complet d'entités connexes dans le cache local.</span><span class="sxs-lookup"><span data-stu-id="61dd6-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="61dd6-114">Pour cela, <xref:System.Data.Linq.EntitySet%601> fournit la méthode <xref:System.Data.Linq.EntitySet%601.Load%2A> pour charger explicitement tous les membres de <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="61dd6-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="61dd6-115">Si un <xref:System.Data.Linq.EntitySet%601> est déjà chargé, les requêtes suivantes sont exécutées localement.</span><span class="sxs-lookup"><span data-stu-id="61dd6-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="61dd6-116">Cette approche est utile pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="61dd6-116">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="61dd6-117">Si le jeu complet doit être utilisé localement ou plusieurs fois, vous pouvez éviter des requêtes distantes et des latences associées.</span><span class="sxs-lookup"><span data-stu-id="61dd6-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="61dd6-118">L'entité peut être sérialisée comme une entité complète.</span><span class="sxs-lookup"><span data-stu-id="61dd6-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="61dd6-119">Le fragment de code suivant illustre comment obtenir l'exécution locale :</span><span class="sxs-lookup"><span data-stu-id="61dd6-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="61dd6-120">Comparaison</span><span class="sxs-lookup"><span data-stu-id="61dd6-120">Comparison</span></span>  

 <span data-ttu-id="61dd6-121">Ces deux fonctions fournissent une combinaison puissante d'options : communication à distance pour les grandes collections et exécution locale pour les petites collections ou lorsque la collection complète est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="61dd6-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="61dd6-122">Implémentez la communication à distance via <xref:System.Linq.IQueryable> et l'exécution locale sur une collection <xref:System.Collections.Generic.IEnumerable%601> en mémoire.</span><span class="sxs-lookup"><span data-stu-id="61dd6-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="61dd6-123">Pour forcer l’exécution locale (autrement dit, <xref:System.Collections.Generic.IEnumerable%601> ), consultez [convertir un type en IEnumerable générique](convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="61dd6-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="61dd6-124">Requêtes sur des jeux non ordonnés</span><span class="sxs-lookup"><span data-stu-id="61dd6-124">Queries Against Unordered Sets</span></span>  

 <span data-ttu-id="61dd6-125">Notez la différence importante entre une collection locale qui implémente <xref:System.Collections.Generic.List%601> et une collection qui fournit des requêtes distantes exécutées sur des *jeux non ordonnés* dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="61dd6-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="61dd6-126">Les méthodes <xref:System.Collections.Generic.List%601> telles que celles qui utilisent des valeurs d'index requièrent des sémantiques de liste que l'on ne peut généralement pas obtenir via une requête distante sur un jeu non ordonné.</span><span class="sxs-lookup"><span data-stu-id="61dd6-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="61dd6-127">Pour cette raison, de telles méthodes chargent implicitement le <xref:System.Data.Linq.EntitySet%601> pour autoriser l'exécution locale.</span><span class="sxs-lookup"><span data-stu-id="61dd6-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61dd6-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61dd6-128">See also</span></span>

- [<span data-ttu-id="61dd6-129">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="61dd6-129">Query Concepts</span></span>](query-concepts.md)
