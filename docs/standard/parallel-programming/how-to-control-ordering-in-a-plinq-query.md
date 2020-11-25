---
title: 'Procédure : contrôler l’ordre dans une requête PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: 945a1e882c473ec9926e60a9e3e513d4949a6717
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700910"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="16bc7-102">Procédure : contrôler l’ordre dans une requête PLINQ</span><span class="sxs-lookup"><span data-stu-id="16bc7-102">How to: Control Ordering in a PLINQ Query</span></span>

<span data-ttu-id="16bc7-103">Ces exemples montrent comment contrôler le classement d’une requête PLINQ à l’aide de la méthode d’extension <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.</span><span class="sxs-lookup"><span data-stu-id="16bc7-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="16bc7-104">Ces exemples, principalement destinés à illustrer l'utilisation, peuvent ou non s'exécuter plus rapidement que les requêtes LINQ to Objects séquentielle équivalentes.</span><span class="sxs-lookup"><span data-stu-id="16bc7-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16bc7-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="16bc7-105">Example</span></span>  

 <span data-ttu-id="16bc7-106">L’exemple suivant conserve l’ordre de la séquence source.</span><span class="sxs-lookup"><span data-stu-id="16bc7-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="16bc7-107">Cela est parfois nécessaire, par exemple si certains opérateurs de requête nécessitent une séquence source classée pour produire des résultats corrects.</span><span class="sxs-lookup"><span data-stu-id="16bc7-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="16bc7-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="16bc7-108">Example</span></span>  

 <span data-ttu-id="16bc7-109">L’exemple suivant montre certains opérateurs de requête dont la séquence source est probablement prévue pour être classée.</span><span class="sxs-lookup"><span data-stu-id="16bc7-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="16bc7-110">Ces opérateurs fonctionneront sur les séquences non classées, mais ils peuvent produire des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="16bc7-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="16bc7-111">Pour exécuter cette méthode, collez-la dans la classe PLINQDataSample du projet [Exemple de données PLINQ](plinq-data-sample.md), puis appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="16bc7-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16bc7-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="16bc7-112">Example</span></span>  

 <span data-ttu-id="16bc7-113">L’exemple suivant montre comment conserver le classement pour la première partie d’une requête, comment supprimer le classement afin d’augmenter les performances d’une clause join, puis comment réappliquer le classement à la séquence de résultat finale.</span><span class="sxs-lookup"><span data-stu-id="16bc7-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="16bc7-114">Pour exécuter cette méthode, collez-la dans la classe PLINQDataSample du projet [Exemple de données PLINQ](plinq-data-sample.md), puis appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="16bc7-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bc7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16bc7-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="16bc7-116">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="16bc7-116">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
