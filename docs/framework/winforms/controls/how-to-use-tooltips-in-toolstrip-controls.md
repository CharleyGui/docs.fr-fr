---
title: 'Procédure : utiliser des info-bulles dans des contrôles ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939730"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="bcee1-102">Procédure : utiliser des info-bulles dans des contrôles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bcee1-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="bcee1-103">Vous pouvez afficher un <xref:System.Windows.Forms.ToolTip> pour le <xref:System.Windows.Forms.ToolStrip> contrôle souhaité en affectant à `true`la propriété <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> du contrôle la valeur.</span><span class="sxs-lookup"><span data-stu-id="bcee1-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="bcee1-104">Pour afficher une info-bulle</span><span class="sxs-lookup"><span data-stu-id="bcee1-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="bcee1-105">Affectez <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> à `true`la propriété du contrôle la valeur.</span><span class="sxs-lookup"><span data-stu-id="bcee1-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="bcee1-106">La valeur par défaut <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> de `true`est, et la valeur par défaut <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> de `false`et de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> est.</span><span class="sxs-lookup"><span data-stu-id="bcee1-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="bcee1-107">Pour utiliser la propriété ToolTipText pour le texte info-bulle d’un ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="bcee1-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="bcee1-108">Affectez <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> à `true`la propriété du bouton la valeur.</span><span class="sxs-lookup"><span data-stu-id="bcee1-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="bcee1-109">Affectez <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> à `false`la propriété du bouton la valeur.</span><span class="sxs-lookup"><span data-stu-id="bcee1-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="bcee1-110">La `AutoToolTip` propriété est `true` par défaut pour <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>et. <xref:System.Windows.Forms.ToolStripSplitButton></span><span class="sxs-lookup"><span data-stu-id="bcee1-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="bcee1-111">Un <xref:System.Windows.Forms.ToolStripButton> utilise sa `Text` propriété pour le <xref:System.Windows.Forms.ToolTip> texte par défaut.</span><span class="sxs-lookup"><span data-stu-id="bcee1-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="bcee1-112">Utilisez cette procédure pour afficher du texte personnalisé dans <xref:System.Windows.Forms.ToolStripButton>un <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="bcee1-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcee1-113">Si vous affectez <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> à <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>la valeur <xref:System.Windows.Forms.ToolStripItemDisplayStyle> ou, aucun texte n’apparaît sur le bouton, mais l’info-bulle apparaît toujours.</span><span class="sxs-lookup"><span data-stu-id="bcee1-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcee1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcee1-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="bcee1-115">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bcee1-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
