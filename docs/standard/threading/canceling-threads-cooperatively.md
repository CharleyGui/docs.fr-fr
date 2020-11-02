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
ms.openlocfilehash: 36de18e976401dd0cde878852c064aa982b8acde
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188495"
---
# <a name="canceling-threads-cooperatively"></a>Annulation de threads de façon coopérative

Avant le .NET Framework 4, .NET n’offrait aucune méthode intégrée pour annuler un thread de manière coopérative après son démarrage. Toutefois, à partir de .NET Framework 4, vous pouvez utiliser un <xref:System.Threading.CancellationToken?displayProperty=nameWithType> pour annuler les threads, tout comme vous pouvez les utiliser pour annuler des <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objets ou des requêtes PLINQ. Bien que la classe <xref:System.Threading.Thread?displayProperty=nameWithType> n’offre pas de prise en charge intégrée pour les jetons d’annulation, vous pouvez transmettre un jeton à une procédure de thread à l’aide du constructeur <xref:System.Threading.Thread> qui prend un délégué <xref:System.Threading.ParameterizedThreadStart>. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de threads et de threads](using-threads-and-threading.md)
