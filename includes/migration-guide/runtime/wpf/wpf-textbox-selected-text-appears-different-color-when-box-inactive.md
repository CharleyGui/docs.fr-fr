---
ms.openlocfilehash: c01705002ad87a12389078d75ffd0f91f934d36e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496356"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="ea386-101">Le texte sélectionné dans la zone de texte WPF sélectionnée s’affiche dans une autre couleur quand la zone de texte est inactive</span><span class="sxs-lookup"><span data-stu-id="ea386-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="ea386-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ea386-102">Details</span></span>

<span data-ttu-id="ea386-103">Dans .NET Framework 4.5, quand un contrôle de zone de texte WPF est inactif (c’est-à-dire qu’il n’a pas le focus), le texte sélectionné dans la zone s’affiche dans une couleur différente de celle utilisée quand le contrôle est actif.</span><span class="sxs-lookup"><span data-stu-id="ea386-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ea386-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ea386-104">Suggestion</span></span>

<span data-ttu-id="ea386-105">Vous pouvez restaurer le comportement précédent (.NET Framework 4.0) en affectant la valeur <code>false</code> à la propriété <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported>.</span><span class="sxs-lookup"><span data-stu-id="ea386-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="ea386-106">Name</span><span class="sxs-lookup"><span data-stu-id="ea386-106">Name</span></span>    | <span data-ttu-id="ea386-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="ea386-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ea386-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="ea386-108">Scope</span></span>   |<span data-ttu-id="ea386-109">Edge</span><span class="sxs-lookup"><span data-stu-id="ea386-109">Edge</span></span>|
|<span data-ttu-id="ea386-110">Version</span><span class="sxs-lookup"><span data-stu-id="ea386-110">Version</span></span>|<span data-ttu-id="ea386-111">4,5</span><span class="sxs-lookup"><span data-stu-id="ea386-111">4.5</span></span>|
|<span data-ttu-id="ea386-112">Type</span><span class="sxs-lookup"><span data-stu-id="ea386-112">Type</span></span>|<span data-ttu-id="ea386-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="ea386-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ea386-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="ea386-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
