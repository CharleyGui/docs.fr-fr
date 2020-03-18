---
title: Parallel LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
ms.openlocfilehash: 1ea880c6403a5fc8b26ba67fe21dfce79c4683db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140037"
---
# <a name="parallel-linq-plinq"></a><span data-ttu-id="9eb09-102">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9eb09-102">Parallel LINQ (PLINQ)</span></span>
<span data-ttu-id="9eb09-103">Parallel LINQ (PLINQ) est une implémentation parallèle de LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="9eb09-103">Parallel LINQ (PLINQ) is a parallel implementation of LINQ to Objects.</span></span> <span data-ttu-id="9eb09-104">PLINQ implémente le jeu complet d’opérateurs de requête standard LINQ comme méthodes d’extension pour l’espace de noms <xref:System.Linq> et inclut des opérateurs supplémentaires pour les opérations parallèles.</span><span class="sxs-lookup"><span data-stu-id="9eb09-104">PLINQ implements the full set of LINQ standard query operators as extension methods for the <xref:System.Linq> namespace and has additional operators for parallel operations.</span></span> <span data-ttu-id="9eb09-105">PLINQ combine la simplicité et la lisibilité de la syntaxe LINQ à la puissance de la programmation parallèle.</span><span class="sxs-lookup"><span data-stu-id="9eb09-105">PLINQ combines the simplicity and readability of LINQ syntax with the power of parallel programming.</span></span> <span data-ttu-id="9eb09-106">Comme le code qui cible la bibliothèque parallèle de tâches, les requêtes PLINQ sont mises à l’échelle dans le degré de concurrence basé sur les fonctionnalités de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="9eb09-106">Just like code that targets the Task Parallel Library, PLINQ queries scale in the degree of concurrency based on the capabilities of the host computer.</span></span>  
  
 <span data-ttu-id="9eb09-107">Dans de nombreux scénarios, PLINQ peut considérablement augmenter la vitesse des requêtes LINQ to Objects en utilisant plus efficacement tous les cœurs disponibles sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="9eb09-107">In many scenarios, PLINQ can significantly increase the speed of LINQ to Objects queries by using all available cores on the host computer more efficiently.</span></span> <span data-ttu-id="9eb09-108">Ces performances accrues apportent une puissance informatique hautes performances sur le Bureau.</span><span class="sxs-lookup"><span data-stu-id="9eb09-108">This increased performance brings high-performance computing power onto the desktop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9eb09-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9eb09-109">In This Section</span></span>  
 [<span data-ttu-id="9eb09-110">Introduction à PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-110">Introduction to PLINQ</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [<span data-ttu-id="9eb09-111">Fonctionnement de l'accélération dans PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-111">Understanding Speedup in PLINQ</span></span>](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [<span data-ttu-id="9eb09-112">Conservation de l'ordre en PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-112">Order Preservation in PLINQ</span></span>](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [<span data-ttu-id="9eb09-113">Options de fusion en PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-113">Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [<span data-ttu-id="9eb09-114">Comment : créer et exécuter une requête PLINQ simple</span><span class="sxs-lookup"><span data-stu-id="9eb09-114">How to: Create and Execute a Simple PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [<span data-ttu-id="9eb09-115">Comment : contrôler l'ordre dans une requête PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-115">How to: Control Ordering in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [<span data-ttu-id="9eb09-116">Comment : combiner des requêtes LINQ parallèles et séquentielles</span><span class="sxs-lookup"><span data-stu-id="9eb09-116">How to: Combine Parallel and Sequential LINQ Queries</span></span>](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [<span data-ttu-id="9eb09-117">Comment : gérer des exceptions dans une requête PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-117">How to: Handle Exceptions in a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [<span data-ttu-id="9eb09-118">Comment : annuler une requête PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-118">How to: Cancel a PLINQ Query</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [<span data-ttu-id="9eb09-119">Comment : écrire une fonction d'agrégation PLINQ personnalisée</span><span class="sxs-lookup"><span data-stu-id="9eb09-119">How to: Write a Custom PLINQ Aggregate Function</span></span>](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [<span data-ttu-id="9eb09-120">Comment : spécifier le mode d'exécution en PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-120">How to: Specify the Execution Mode in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [<span data-ttu-id="9eb09-121">Comment : spécifier des options de fusion en PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-121">How to: Specify Merge Options in PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [<span data-ttu-id="9eb09-122">Comment : itérer les répertoires de fichiers avec PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-122">How to: Iterate File Directories with PLINQ</span></span>](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [<span data-ttu-id="9eb09-123">Comment : mesurer les performances de requêtes PLINQ</span><span class="sxs-lookup"><span data-stu-id="9eb09-123">How to: Measure PLINQ Query Performance</span></span>](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [<span data-ttu-id="9eb09-124">Données PLINQ, exemple</span><span class="sxs-lookup"><span data-stu-id="9eb09-124">PLINQ Data Sample</span></span>](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a><span data-ttu-id="9eb09-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eb09-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="9eb09-126">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="9eb09-126">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="9eb09-127">LINQ (Language-Integrated Query) - C#</span><span class="sxs-lookup"><span data-stu-id="9eb09-127">Language-Integrated Query (LINQ) - C#</span></span>](../../csharp/programming-guide/concepts/linq/index.md)  
- [<span data-ttu-id="9eb09-128">LINQ (Language-Integrated Query) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9eb09-128">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)  
