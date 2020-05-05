---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888115"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="656a7-101">Événement CellFormatting non déclenché si l’info-bulle est affichée</span><span class="sxs-lookup"><span data-stu-id="656a7-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="656a7-102">Un <xref:System.Windows.Forms.DataGridView> affiche maintenant le texte et les info-bulles d’erreur d’une cellule lorsqu’elle est survolée par une souris et lorsqu’elle est sélectionnée via le clavier.</span><span class="sxs-lookup"><span data-stu-id="656a7-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="656a7-103">Si une info-bulle est affichée <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> , l’événement n’est pas déclenché.</span><span class="sxs-lookup"><span data-stu-id="656a7-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="656a7-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="656a7-104">Change description</span></span>

<span data-ttu-id="656a7-105">Avant .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> dont la <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> propriété a été définie pour `true` montrer une info-bulle pour le texte d’une cellule et des erreurs quand la cellule a été pointée par une souris.</span><span class="sxs-lookup"><span data-stu-id="656a7-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="656a7-106">Les info-bulles n’étaient pas affichées lorsqu’une cellule a été sélectionnée à l’aide du clavier (par exemple, en utilisant la touche Tab, les touches de raccourci ou la navigation vers la flèche).</span><span class="sxs-lookup"><span data-stu-id="656a7-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="656a7-107">Si l’utilisateur a modifié une cellule, puis que le <xref:System.Windows.Forms.DataGridView> était toujours en mode édition, pointé sur une cellule pour laquelle la <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> propriété n’a pas été définie, un <xref:System.Windows.Forms.DataGridView.CellFormatting> événement a été déclenché pour mettre en forme le texte de la cellule en vue de son affichage dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="656a7-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="656a7-108">Pour répondre aux normes d’accessibilité, à compter de .NET Core <xref:System.Windows.Forms.DataGridView> 3,1, dont <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> la propriété a `true` la valeur affiche des info-bulles pour le texte d’une cellule et des erreurs non seulement lorsque la cellule est survolée, mais également quand elle est sélectionnée via le clavier.</span><span class="sxs-lookup"><span data-stu-id="656a7-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="656a7-109">En raison de cette <xref:System.Windows.Forms.DataGridView.CellFormatting> modification, l’événement n’est *pas* déclenché lorsque des cellules qui n’ont <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> pas la propriété définie sont pointées <xref:System.Windows.Forms.DataGridView> pendant que le est en mode édition.</span><span class="sxs-lookup"><span data-stu-id="656a7-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="656a7-110">L’événement n’est pas déclenché, car le contenu de la cellule survolée est affiché sous la forme d’une info-bulle au lieu d’être affiché dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="656a7-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="656a7-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="656a7-111">Version introduced</span></span>

<span data-ttu-id="656a7-112">3.1</span><span class="sxs-lookup"><span data-stu-id="656a7-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="656a7-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="656a7-113">Recommended action</span></span>

<span data-ttu-id="656a7-114">Refactorisez tout code qui dépend de l' <xref:System.Windows.Forms.DataGridView.CellFormatting> événement lorsque <xref:System.Windows.Forms.DataGridView> est en mode édition.</span><span class="sxs-lookup"><span data-stu-id="656a7-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="656a7-115">Category</span><span class="sxs-lookup"><span data-stu-id="656a7-115">Category</span></span>

<span data-ttu-id="656a7-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="656a7-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="656a7-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="656a7-117">Affected APIs</span></span>

<span data-ttu-id="656a7-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="656a7-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
