---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620467"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="e2fe7-101">Le texte sélectionné dans la zone de texte WPF sélectionnée s’affiche dans une autre couleur quand la zone de texte est inactive</span><span class="sxs-lookup"><span data-stu-id="e2fe7-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="e2fe7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e2fe7-102">Details</span></span>

<span data-ttu-id="e2fe7-103">Dans .NET Framework 4.5, quand un contrôle de zone de texte WPF est inactif (c’est-à-dire qu’il n’a pas le focus), le texte sélectionné dans la zone s’affiche dans une couleur différente de celle utilisée quand le contrôle est actif.</span><span class="sxs-lookup"><span data-stu-id="e2fe7-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e2fe7-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e2fe7-104">Suggestion</span></span>

<span data-ttu-id="e2fe7-105">Vous pouvez restaurer le comportement précédent (.NET Framework 4.0) en affectant la valeur <code>false</code> à la propriété <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported>.</span><span class="sxs-lookup"><span data-stu-id="e2fe7-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="e2fe7-106">Nom</span><span class="sxs-lookup"><span data-stu-id="e2fe7-106">Name</span></span>    | <span data-ttu-id="e2fe7-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="e2fe7-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2fe7-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="e2fe7-108">Scope</span></span>   |<span data-ttu-id="e2fe7-109">Edge</span><span class="sxs-lookup"><span data-stu-id="e2fe7-109">Edge</span></span>|
|<span data-ttu-id="e2fe7-110">Version</span><span class="sxs-lookup"><span data-stu-id="e2fe7-110">Version</span></span>|<span data-ttu-id="e2fe7-111">4,5</span><span class="sxs-lookup"><span data-stu-id="e2fe7-111">4.5</span></span>|
|<span data-ttu-id="e2fe7-112">Type</span><span class="sxs-lookup"><span data-stu-id="e2fe7-112">Type</span></span>|<span data-ttu-id="e2fe7-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="e2fe7-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2fe7-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="e2fe7-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
