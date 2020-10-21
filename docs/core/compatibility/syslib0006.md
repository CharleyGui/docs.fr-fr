---
title: AVERTISSEMENT SYSLIB0006
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0006.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 45d2d8ec6ad99996f8b8f46d0c2e0ac2e02cf450
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333303"
---
# <a name="syslib0006-threadabort-is-not-supported"></a>SYSLIB0006 : thread. Abort n’est pas pris en charge

Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0. L’utilisation de ces API génère un avertissement `SYSLIB0006` au moment de la compilation.

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workaround"></a>Solution de contournement

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

## <a name="see-also"></a>Voir aussi

- [Thread. Abort est obsolète-modification avec rupture](3.1-5.0.md#threadabort-is-obsolete)
- [Annulation dans les threads managés](../../standard/threading/cancellation-in-managed-threads.md)
