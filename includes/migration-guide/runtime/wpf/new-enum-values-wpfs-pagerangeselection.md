---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620455"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="ff45e-101">Nouvelles valeurs enum dans le PageRangeSelection de WPF</span><span class="sxs-lookup"><span data-stu-id="ff45e-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="ff45e-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ff45e-102">Details</span></span>

<span data-ttu-id="ff45e-103">Deux nouveaux membres (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> et <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) ont été ajoutés à l’énumération <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ff45e-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ff45e-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ff45e-104">Suggestion</span></span>

<span data-ttu-id="ff45e-105">Dans la plupart des cas, ces modifications n’affectent pas le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ff45e-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="ff45e-106">Le code qui dépend d’un certain nombre d’éléments existants dans les appels de <xref:System.Enum.GetNames(System.Type)> et de <xref:System.Enum.GetValues(System.Type)> sur le type <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> doit cependant être modifié.</span><span class="sxs-lookup"><span data-stu-id="ff45e-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="ff45e-107">Nom</span><span class="sxs-lookup"><span data-stu-id="ff45e-107">Name</span></span>    | <span data-ttu-id="ff45e-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff45e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ff45e-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="ff45e-109">Scope</span></span>   |<span data-ttu-id="ff45e-110">Edge</span><span class="sxs-lookup"><span data-stu-id="ff45e-110">Edge</span></span>|
|<span data-ttu-id="ff45e-111">Version</span><span class="sxs-lookup"><span data-stu-id="ff45e-111">Version</span></span>|<span data-ttu-id="ff45e-112">4,5</span><span class="sxs-lookup"><span data-stu-id="ff45e-112">4.5</span></span>|
|<span data-ttu-id="ff45e-113">Type</span><span class="sxs-lookup"><span data-stu-id="ff45e-113">Type</span></span>|<span data-ttu-id="ff45e-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="ff45e-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ff45e-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="ff45e-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
