---
title: 'Comment : synchroniser des opérations simultanées avec un objet Barrier'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: 2e13dfb277807eb0a9f256f74c2845f5a4d2a047
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279295"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="ee6e7-102">Comment : synchroniser des opérations simultanées avec un objet Barrier</span><span class="sxs-lookup"><span data-stu-id="ee6e7-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="ee6e7-103">L’exemple suivant montre comment synchroniser des tâches simultanées avec un objet <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee6e7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee6e7-104">Example</span></span>  
 <span data-ttu-id="ee6e7-105">L’objectif du programme suivant est de compter le nombre d’itérations (ou phases) nécessaires pour permettre à deux threads de trouver leur moitié de la solution sur la même phase à l’aide d’un algorithme aléatoire qui remélange les mots.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="ee6e7-106">Une fois que chaque thread a mélangé ses mots, l’opération post-phase de cloisonnement compare les deux résultats pour vérifier si la phrase complète a été restituée dans l’ordre correct des mots.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="ee6e7-107">Un objet <xref:System.Threading.Barrier> est un objet qui empêche des tâches individuelles d’une opération parallèle de se poursuivre tant que toutes les tâches n’ont pas atteint le cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="ee6e7-108">Cela est utile quand une opération parallèle se produit en plusieurs phases, et que chaque phase exige une synchronisation entre les tâches.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="ee6e7-109">Dans cet exemple, l’opération est exécutée en deux phases.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="ee6e7-110">Durant la première phase, chaque tâche remplit sa section de la mémoire tampon avec des données.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="ee6e7-111">Quand chaque tâche a terminé de remplir sa section, elle signale au cloisonnement qu’elle est prête à se poursuivre, puis elle attend.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="ee6e7-112">Quand toutes les tâches ont signalé au cloisonnement qu’elles sont prêtes, elles sont débloquées et la deuxième phase démarre.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="ee6e7-113">Le cloisonnement est nécessaire, car la deuxième phase requiert que chaque tâche ait accès à toutes les données qui ont été générées à ce stade.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="ee6e7-114">Sans le cloisonnement, les premières tâches à effectuer pourraient tenter de lire des mémoires tampons qui n'ont pas encore été remplies par d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="ee6e7-115">Vous pouvez synchroniser ainsi un nombre quelconque de phases.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6e7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee6e7-116">See also</span></span>

- [<span data-ttu-id="ee6e7-117">Structures de données pour la programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="ee6e7-117">Data Structures for Parallel Programming</span></span>](../parallel-programming/data-structures-for-parallel-programming.md)
