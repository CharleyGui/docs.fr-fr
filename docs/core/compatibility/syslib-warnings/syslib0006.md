---
title: AVERTISSEMENT SYSLIB0006
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0006.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: c1eecade9280ac37917bc24aa2973756c7f08d87
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596495"
---
# <a name="syslib0006-threadabort-is-not-supported"></a>SYSLIB0006 : thread. Abort n’est pas pris en charge

Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0. L’utilisation de ces API génère un avertissement `SYSLIB0006` au moment de la compilation.

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a>Solutions de contournement

Utilisez un <xref:System.Threading.CancellationToken> pour abandonner le traitement d’une unité de travail au lieu d’appeler <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> . L’exemple suivant illustre l’utilisation de <xref:System.Threading.CancellationToken> .

```csharp
void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
{
    if (QueryIsMoreWorkPending())
    {
        // If the CancellationToken is marked as "needs to cancel",
        // this will throw the appropriate exception.
        cancellationToken.ThrowIfCancellationRequested();

        WorkItem work = DequeueWorkItem();
        ProcessWorkItem(work);
    }
}
```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Voir aussi

- [Thread.Abort est obsolète](../core-libraries/5.0/thread-abort-obsolete.md)
- [Annulation dans les threads managés](../../../standard/threading/cancellation-in-managed-threads.md)
