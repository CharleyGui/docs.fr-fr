---
ms.openlocfilehash: 61749f59f9379a6d18bb013b2612a07cb7822b3a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497034"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="b96c6-101">Nouvelles valeurs enum dans le PageRangeSelection de WPF</span><span class="sxs-lookup"><span data-stu-id="b96c6-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="b96c6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b96c6-102">Details</span></span>

<span data-ttu-id="b96c6-103">Deux nouveaux membres (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> et <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) ont été ajoutés à l’énumération <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b96c6-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b96c6-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b96c6-104">Suggestion</span></span>

<span data-ttu-id="b96c6-105">Dans la plupart des cas, ces modifications n’affectent pas le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b96c6-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="b96c6-106">Le code qui dépend d’un certain nombre d’éléments existants dans les appels de <xref:System.Enum.GetNames(System.Type)> et de <xref:System.Enum.GetValues(System.Type)> sur le type <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> doit cependant être modifié.</span><span class="sxs-lookup"><span data-stu-id="b96c6-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="b96c6-107">Name</span><span class="sxs-lookup"><span data-stu-id="b96c6-107">Name</span></span>    | <span data-ttu-id="b96c6-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="b96c6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b96c6-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="b96c6-109">Scope</span></span>   |<span data-ttu-id="b96c6-110">Edge</span><span class="sxs-lookup"><span data-stu-id="b96c6-110">Edge</span></span>|
|<span data-ttu-id="b96c6-111">Version</span><span class="sxs-lookup"><span data-stu-id="b96c6-111">Version</span></span>|<span data-ttu-id="b96c6-112">4,5</span><span class="sxs-lookup"><span data-stu-id="b96c6-112">4.5</span></span>|
|<span data-ttu-id="b96c6-113">Type</span><span class="sxs-lookup"><span data-stu-id="b96c6-113">Type</span></span>|<span data-ttu-id="b96c6-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="b96c6-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b96c6-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="b96c6-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.PageRangeSelection`

-->
