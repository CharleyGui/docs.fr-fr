---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620479"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="73031-101">Le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut</span><span class="sxs-lookup"><span data-stu-id="73031-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="73031-102">Détails</span><span class="sxs-lookup"><span data-stu-id="73031-102">Details</span></span>

<span data-ttu-id="73031-103">Dans .NET Framework 4.5, le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut (dans .NET Framework 4.0, ce nombre était illimité).</span><span class="sxs-lookup"><span data-stu-id="73031-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="73031-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="73031-104">Suggestion</span></span>

<span data-ttu-id="73031-105">Si ce nombre n’est pas suffisant, vous pouvez définir explicitement cette valeur avec <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="73031-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="73031-106">Nom</span><span class="sxs-lookup"><span data-stu-id="73031-106">Name</span></span>    | <span data-ttu-id="73031-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="73031-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="73031-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="73031-108">Scope</span></span>   |<span data-ttu-id="73031-109">Edge</span><span class="sxs-lookup"><span data-stu-id="73031-109">Edge</span></span>|
|<span data-ttu-id="73031-110">Version</span><span class="sxs-lookup"><span data-stu-id="73031-110">Version</span></span>|<span data-ttu-id="73031-111">4,5</span><span class="sxs-lookup"><span data-stu-id="73031-111">4.5</span></span>|
|<span data-ttu-id="73031-112">Type</span><span class="sxs-lookup"><span data-stu-id="73031-112">Type</span></span>|<span data-ttu-id="73031-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="73031-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73031-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="73031-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
