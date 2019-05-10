---
title: 'Procédure : utiliser des info-bulles dans des contrôles ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: b009d19ed949edbd52ec02252ba1e2271e4cb738
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750559"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="e6484-102">Procédure : utiliser des info-bulles dans des contrôles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e6484-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="e6484-103">Vous pouvez afficher un <xref:System.Windows.Forms.ToolTip> pour le <xref:System.Windows.Forms.ToolStrip> contrôle souhaité en définissant le contrôle <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="e6484-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="e6484-104">Pour afficher une info-bulle</span><span class="sxs-lookup"><span data-stu-id="e6484-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="e6484-105">Définir le <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriété du contrôle à `true`.</span><span class="sxs-lookup"><span data-stu-id="e6484-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="e6484-106">La valeur par défaut <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> est `true`et la valeur par défaut de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> et <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> est `false`.</span><span class="sxs-lookup"><span data-stu-id="e6484-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="e6484-107">Pour utiliser la propriété ToolTipText pour le texte d’info-bulle d’un ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="e6484-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="e6484-108">Définir le <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> propriété du bouton `true`.</span><span class="sxs-lookup"><span data-stu-id="e6484-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="e6484-109">Définir le <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> propriété du bouton `false`.</span><span class="sxs-lookup"><span data-stu-id="e6484-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="e6484-110">Le `AutoToolTip` propriété est `true` par défaut pour <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, et <xref:System.Windows.Forms.ToolStripSplitButton>.</span><span class="sxs-lookup"><span data-stu-id="e6484-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="e6484-111">Un <xref:System.Windows.Forms.ToolStripButton> utilise son `Text` propriété pour la <xref:System.Windows.Forms.ToolTip> texte par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6484-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="e6484-112">Utilisez cette procédure pour afficher un texte personnalisé dans un <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="e6484-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6484-113">Si vous définissez <xref:System.Windows.Forms.ToolStripItemDisplayStyle> à <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, aucun texte n’apparaît sur le bouton, mais l’info-bulle apparaît toujours.</span><span class="sxs-lookup"><span data-stu-id="e6484-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6484-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6484-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="e6484-115">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e6484-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
