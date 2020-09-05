---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497595"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="7ade8-101">Le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut</span><span class="sxs-lookup"><span data-stu-id="7ade8-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="7ade8-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7ade8-102">Details</span></span>

<span data-ttu-id="7ade8-103">Dans .NET Framework 4.5, le nombre maximal d’annulations d’opérations pour une zone de texte WPF est de 100 par défaut (dans .NET Framework 4.0, ce nombre était illimité).</span><span class="sxs-lookup"><span data-stu-id="7ade8-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7ade8-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7ade8-104">Suggestion</span></span>

<span data-ttu-id="7ade8-105">Si ce nombre n’est pas suffisant, vous pouvez définir explicitement cette valeur avec <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="7ade8-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="7ade8-106">Name</span><span class="sxs-lookup"><span data-stu-id="7ade8-106">Name</span></span>    | <span data-ttu-id="7ade8-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="7ade8-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7ade8-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="7ade8-108">Scope</span></span>   |<span data-ttu-id="7ade8-109">Edge</span><span class="sxs-lookup"><span data-stu-id="7ade8-109">Edge</span></span>|
|<span data-ttu-id="7ade8-110">Version</span><span class="sxs-lookup"><span data-stu-id="7ade8-110">Version</span></span>|<span data-ttu-id="7ade8-111">4,5</span><span class="sxs-lookup"><span data-stu-id="7ade8-111">4.5</span></span>|
|<span data-ttu-id="7ade8-112">Type</span><span class="sxs-lookup"><span data-stu-id="7ade8-112">Type</span></span>|<span data-ttu-id="7ade8-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="7ade8-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7ade8-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="7ade8-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
