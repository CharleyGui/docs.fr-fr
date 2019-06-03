---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379700"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="0bd2a-101">La propriété CheckForOverflowUnderflow de WinForm est désormais true pour System.Drawing</span><span class="sxs-lookup"><span data-stu-id="0bd2a-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0bd2a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="0bd2a-102">Details</span></span>|<span data-ttu-id="0bd2a-103">La propriété CheckForOverflowUnderflow pour l’assembly System.Drawing.dll est définie sur true.</span><span class="sxs-lookup"><span data-stu-id="0bd2a-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="0bd2a-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="0bd2a-104">Suggestion</span></span>|<span data-ttu-id="0bd2a-105">Auparavant, en cas de dépassement de capacité, le résultat était tronqué automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0bd2a-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="0bd2a-106">Désormais, une exception <xref:System.OverflowException?displayProperty=name> est levée.</span><span class="sxs-lookup"><span data-stu-id="0bd2a-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="0bd2a-107">Portée</span><span class="sxs-lookup"><span data-stu-id="0bd2a-107">Scope</span></span>|<span data-ttu-id="0bd2a-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0bd2a-108">Edge</span></span>|
|<span data-ttu-id="0bd2a-109">Version</span><span class="sxs-lookup"><span data-stu-id="0bd2a-109">Version</span></span>|<span data-ttu-id="0bd2a-110">4.5</span><span class="sxs-lookup"><span data-stu-id="0bd2a-110">4.5</span></span>|
|<span data-ttu-id="0bd2a-111">Type</span><span class="sxs-lookup"><span data-stu-id="0bd2a-111">Type</span></span>|<span data-ttu-id="0bd2a-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="0bd2a-112">Runtime</span></span>|
