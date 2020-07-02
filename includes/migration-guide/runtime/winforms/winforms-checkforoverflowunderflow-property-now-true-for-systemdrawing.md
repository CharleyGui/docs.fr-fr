---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620443"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="e080c-101">La propriété CheckForOverflowUnderflow de WinForm est désormais true pour System.Drawing</span><span class="sxs-lookup"><span data-stu-id="e080c-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="e080c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e080c-102">Details</span></span>

<span data-ttu-id="e080c-103">La propriété CheckForOverflowUnderflow pour l’assembly System.Drawing.dll est définie sur true.</span><span class="sxs-lookup"><span data-stu-id="e080c-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e080c-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e080c-104">Suggestion</span></span>

<span data-ttu-id="e080c-105">Auparavant, en cas de dépassement de capacité, le résultat était tronqué automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e080c-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="e080c-106">Désormais, une exception <xref:System.OverflowException?displayProperty=fullName> est levée.</span><span class="sxs-lookup"><span data-stu-id="e080c-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="e080c-107">Nom</span><span class="sxs-lookup"><span data-stu-id="e080c-107">Name</span></span>    | <span data-ttu-id="e080c-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="e080c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e080c-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="e080c-109">Scope</span></span>   |<span data-ttu-id="e080c-110">Edge</span><span class="sxs-lookup"><span data-stu-id="e080c-110">Edge</span></span>|
|<span data-ttu-id="e080c-111">Version</span><span class="sxs-lookup"><span data-stu-id="e080c-111">Version</span></span>|<span data-ttu-id="e080c-112">4,5</span><span class="sxs-lookup"><span data-stu-id="e080c-112">4.5</span></span>|
|<span data-ttu-id="e080c-113">Type</span><span class="sxs-lookup"><span data-stu-id="e080c-113">Type</span></span>|<span data-ttu-id="e080c-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="e080c-114">Runtime</span></span>|
