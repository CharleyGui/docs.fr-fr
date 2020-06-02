---
title: 'Procédure : annuler une boucle Parallel.For ou ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288223"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Procédure : annuler une boucle Parallel.For ou ForEach
Les méthodes <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> prennent en charge l'annulation via l'utilisation de jetons d'annulation. Pour plus d'informations sur l'annulation en général, consultez [Annulation](../threading/cancellation-in-managed-threads.md). Dans une boucle parallèle, vous fournissez <xref:System.Threading.CancellationToken> à la méthode dans le paramètre <xref:System.Threading.Tasks.ParallelOptions> et vous joignez l’appel parallèle dans un bloc try-catch.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment annuler un appel à <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Vous pouvez appliquer la même approche à un appel <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Si le jeton qui signale l’annulation est le même jeton que celui spécifié dans l’instance <xref:System.Threading.Tasks.ParallelOptions>, alors la boucle parallèle lève une seule exception <xref:System.OperationCanceledException> lors de l’annulation. Si un autre jeton provoque l’annulation, la boucle lève une exception <xref:System.AggregateException> avec une exception <xref:System.OperationCanceledException> comme InnerException.  
  
## <a name="see-also"></a>Voir aussi

- [Parallélisme des données](data-parallelism-task-parallel-library.md)
- [Expressions lambda dans PLINQ et TPL](lambda-expressions-in-plinq-and-tpl.md)
