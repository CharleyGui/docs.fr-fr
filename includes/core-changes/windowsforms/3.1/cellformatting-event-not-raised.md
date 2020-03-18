---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567371"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="eba30-101">CellFormatting événement non soulevé si tooltip est montré</span><span class="sxs-lookup"><span data-stu-id="eba30-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="eba30-102">A <xref:System.Windows.Forms.DataGridView> affiche maintenant les outils texte et erreur d’une cellule lorsqu’il est plané par une souris et lorsqu’il est sélectionné via le clavier.</span><span class="sxs-lookup"><span data-stu-id="eba30-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="eba30-103">Si un tooltip est <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> montré, l’événement n’est pas soulevé.</span><span class="sxs-lookup"><span data-stu-id="eba30-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eba30-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="eba30-104">Change description</span></span>

<span data-ttu-id="eba30-105">Avant .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> un <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> qui `true` avait la propriété réglée pour montrer une pointe d’outils pour le texte d’une cellule et les erreurs lorsque la cellule a été planée par une souris.</span><span class="sxs-lookup"><span data-stu-id="eba30-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="eba30-106">Les outils n’ont pas été montrés lorsqu’une cellule a été sélectionnée via le clavier (par exemple, en utilisant la clé Tab, les touches de raccourci ou la navigation fléchée).</span><span class="sxs-lookup"><span data-stu-id="eba30-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="eba30-107">Si l’utilisateur a édité une <xref:System.Windows.Forms.DataGridView> cellule, puis, alors que le était encore <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> en mode <xref:System.Windows.Forms.DataGridView.CellFormatting> d’édition, planait au-dessus d’une cellule qui n’avait pas l’ensemble de propriété, un événement a été soulevé pour formater le texte de la cellule pour l’affichage dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="eba30-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="eba30-108">Pour répondre aux normes d’accessibilité, à partir <xref:System.Windows.Forms.DataGridView> de .NET Core 3.1, un qui a la <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriété définie pour `true` afficher les outils pour le texte d’une cellule et les erreurs non seulement lorsque la cellule est planée, mais aussi quand il est sélectionné via le clavier.</span><span class="sxs-lookup"><span data-stu-id="eba30-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="eba30-109">En conséquence de ce <xref:System.Windows.Forms.DataGridView.CellFormatting> changement, l’événement *n’est* pas <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> soulevé lorsque les <xref:System.Windows.Forms.DataGridView> cellules qui n’ont pas l’ensemble de propriété sont planées pendant que le est en mode d’édition.</span><span class="sxs-lookup"><span data-stu-id="eba30-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="eba30-110">L’événement n’est pas soulevé parce que le contenu de la cellule planée est montré comme un tooltip au lieu d’être affiché dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="eba30-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eba30-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="eba30-111">Version introduced</span></span>

<span data-ttu-id="eba30-112">3.1</span><span class="sxs-lookup"><span data-stu-id="eba30-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eba30-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="eba30-113">Recommended action</span></span>

<span data-ttu-id="eba30-114">Refactor tout code qui <xref:System.Windows.Forms.DataGridView.CellFormatting> dépend <xref:System.Windows.Forms.DataGridView> de l’événement pendant que le mode d’édition est en mode d’édition.</span><span class="sxs-lookup"><span data-stu-id="eba30-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="eba30-115">Category</span><span class="sxs-lookup"><span data-stu-id="eba30-115">Category</span></span>

<span data-ttu-id="eba30-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eba30-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eba30-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="eba30-117">Affected APIs</span></span>

<span data-ttu-id="eba30-118">Non détectable par l’analyse de l’API.</span><span class="sxs-lookup"><span data-stu-id="eba30-118">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
