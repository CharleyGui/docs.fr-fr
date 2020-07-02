---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616250"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="5ceef-101">Ajout de la propriété publique SelectionTextBrush à la sélection sans ornement pour TextBox/PasswordBox</span><span class="sxs-lookup"><span data-stu-id="5ceef-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="5ceef-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5ceef-102">Details</span></span>

<span data-ttu-id="5ceef-103">Dans les applications WPF utilisant la [sélection de texte sans ornement](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) pour <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.PasswordBox>, les développeurs peuvent maintenant définir la propriété SelectionTextBrush récemment ajoutée afin de modifier le rendu du texte sélectionné.</span><span class="sxs-lookup"><span data-stu-id="5ceef-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="5ceef-104">Par défaut, cette couleur change avec <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span><span class="sxs-lookup"><span data-stu-id="5ceef-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="5ceef-105">Si la sélection de texte sans ornement n’est pas activée, cette propriété ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="5ceef-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5ceef-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5ceef-106">Suggestion</span></span>

<span data-ttu-id="5ceef-107">Une fois que la sélection de texte sans ornement est activée, vous pouvez utiliser la propriété <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> et <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> pour changer l’apparence du texte sélectionné.</span><span class="sxs-lookup"><span data-stu-id="5ceef-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="5ceef-108">Pour ce faire, vous pouvez utiliser XAML :</span><span class="sxs-lookup"><span data-stu-id="5ceef-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="5ceef-109">Nom</span><span class="sxs-lookup"><span data-stu-id="5ceef-109">Name</span></span>    | <span data-ttu-id="5ceef-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="5ceef-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5ceef-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="5ceef-111">Scope</span></span>   | <span data-ttu-id="5ceef-112">Majeure</span><span class="sxs-lookup"><span data-stu-id="5ceef-112">Major</span></span>       |
| <span data-ttu-id="5ceef-113">Version</span><span class="sxs-lookup"><span data-stu-id="5ceef-113">Version</span></span> | <span data-ttu-id="5ceef-114">4.8</span><span class="sxs-lookup"><span data-stu-id="5ceef-114">4.8</span></span>         |
| <span data-ttu-id="5ceef-115">Type</span><span class="sxs-lookup"><span data-stu-id="5ceef-115">Type</span></span>    | <span data-ttu-id="5ceef-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="5ceef-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5ceef-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="5ceef-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="5ceef-118">System.Windows.Controls.TextBox</span><span class="sxs-lookup"><span data-stu-id="5ceef-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="5ceef-119">System.Windows.Controls.PasswordBox</span><span class="sxs-lookup"><span data-stu-id="5ceef-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)
