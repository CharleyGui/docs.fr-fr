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
# <a name="syslib0006-threadabort-is-not-supported"></a><span data-ttu-id="8268c-103">SYSLIB0006 : thread. Abort n’est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="8268c-103">SYSLIB0006: Thread.Abort is not supported</span></span>

<span data-ttu-id="8268c-104">Les API suivantes sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="8268c-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="8268c-105">L’utilisation de ces API génère un avertissement `SYSLIB0006` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8268c-105">Use of these APIs generates warning `SYSLIB0006` at compile time.</span></span>

- <xref:System.Threading.Thread.Abort?displayProperty=nameWithType>
- <xref:System.Threading.Thread.Abort(System.Object)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="8268c-106">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="8268c-106">Workarounds</span></span>

<span data-ttu-id="8268c-107">Utilisez un <xref:System.Threading.CancellationToken> pour abandonner le traitement d’une unité de travail au lieu d’appeler <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8268c-107">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8268c-108">L’exemple suivant illustre l’utilisation de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="8268c-108">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8268c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8268c-109">See also</span></span>

- [<span data-ttu-id="8268c-110">Thread.Abort est obsolète</span><span class="sxs-lookup"><span data-stu-id="8268c-110">Thread.Abort is obsolete</span></span>](../core-libraries/5.0/thread-abort-obsolete.md)
- [<span data-ttu-id="8268c-111">Annulation dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="8268c-111">Cancellation in managed threads</span></span>](../../../standard/threading/cancellation-in-managed-threads.md)
