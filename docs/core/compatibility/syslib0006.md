---
title: AVERTISSEMENT SYSLIB0006
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0006.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 222b669a8a0260713e85721e6031144bb7bda5cc
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440658"
---
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="377fb-103">SYSLIB0006 : thread. Abort n’est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="377fb-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="377fb-104">Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="377fb-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="377fb-105">L’utilisation de ces API génère un avertissement `SYSLIB0006` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="377fb-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="377fb-106">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="377fb-106">Workarounds</span></span>

<span data-ttu-id="377fb-107">Utilisez un <xref:System.Threading.CancellationToken> pour abandonner le traitement d’une unité de travail au lieu d’appeler <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="377fb-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="377fb-108">L’exemple suivant illustre l’utilisation de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="377fb-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="377fb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="377fb-109">See also</span></span>

- [<span data-ttu-id="377fb-110">Thread. Abort est obsolète-modification avec rupture</span><span class="sxs-lookup"><span data-stu-id="377fb-110">Thread.Abort is obsolete - breaking change</span></span>](3.1-5.0.md#threadabort-is-obsolete)
- [<span data-ttu-id="377fb-111">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="377fb-111">Cancellation in managed threads</span></span>](../../standard/threading/cancellation-in-managed-threads.md)
