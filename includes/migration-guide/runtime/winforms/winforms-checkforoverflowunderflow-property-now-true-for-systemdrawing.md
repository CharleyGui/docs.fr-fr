---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496699"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="076fe-101">La propriété CheckForOverflowUnderflow de WinForm est désormais true pour System.Drawing</span><span class="sxs-lookup"><span data-stu-id="076fe-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="076fe-102">Détails</span><span class="sxs-lookup"><span data-stu-id="076fe-102">Details</span></span>

<span data-ttu-id="076fe-103">La propriété CheckForOverflowUnderflow pour l’assembly System.Drawing.dll est définie sur true.</span><span class="sxs-lookup"><span data-stu-id="076fe-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="076fe-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="076fe-104">Suggestion</span></span>

<span data-ttu-id="076fe-105">Auparavant, en cas de dépassement de capacité, le résultat était tronqué automatiquement.</span><span class="sxs-lookup"><span data-stu-id="076fe-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="076fe-106">Désormais, une exception <xref:System.OverflowException?displayProperty=fullName> est levée.</span><span class="sxs-lookup"><span data-stu-id="076fe-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="076fe-107">Name</span><span class="sxs-lookup"><span data-stu-id="076fe-107">Name</span></span>    | <span data-ttu-id="076fe-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="076fe-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="076fe-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="076fe-109">Scope</span></span>   |<span data-ttu-id="076fe-110">Edge</span><span class="sxs-lookup"><span data-stu-id="076fe-110">Edge</span></span>|
|<span data-ttu-id="076fe-111">Version</span><span class="sxs-lookup"><span data-stu-id="076fe-111">Version</span></span>|<span data-ttu-id="076fe-112">4,5</span><span class="sxs-lookup"><span data-stu-id="076fe-112">4.5</span></span>|
|<span data-ttu-id="076fe-113">Type</span><span class="sxs-lookup"><span data-stu-id="076fe-113">Type</span></span>|<span data-ttu-id="076fe-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="076fe-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="076fe-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="076fe-115">Affected APIs</span></span>

<span data-ttu-id="076fe-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="076fe-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
