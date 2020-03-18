---
title: Annulation de threads de façon coopérative
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 1d1433ecf39974bf9e68fe07b9d0818ac16fb544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138125"
---
# <a name="canceling-threads-cooperatively"></a>Annulation de threads de façon coopérative

Avant .NET Framework 4, .NET Framework n’offrait aucune fonction intégrée permettant d’annuler, de manière coopérative, un thread après son démarrage. À compter de .NET Framework 4, vous pouvez utiliser un jeton <xref:System.Threading.CancellationToken?displayProperty=nameWithType> pour annuler des threads, tout comme vous pouvez les utiliser pour annuler des objets <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ou des requêtes PLINQ. Bien que la classe <xref:System.Threading.Thread?displayProperty=nameWithType> n’offre pas de prise en charge intégrée pour les jetons d’annulation, vous pouvez transmettre un jeton à une procédure de thread à l’aide du constructeur <xref:System.Threading.Thread> qui prend un délégué <xref:System.Threading.ParameterizedThreadStart>. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des threads et du threading](using-threads-and-threading.md)
