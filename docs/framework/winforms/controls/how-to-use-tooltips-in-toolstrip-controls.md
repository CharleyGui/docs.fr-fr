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
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Procédure : utiliser des info-bulles dans des contrôles ToolStrip
Vous pouvez afficher un <xref:System.Windows.Forms.ToolTip> pour le <xref:System.Windows.Forms.ToolStrip> contrôle souhaité en affectant à `true`la propriété <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> du contrôle la valeur.  
  
### <a name="to-display-a-tooltip"></a>Pour afficher une info-bulle  
  
- Affectez <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> à `true`la propriété du contrôle la valeur.  
  
     La valeur par défaut <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> de `true`est, et la valeur par défaut <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> de `false`et de <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> est.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Pour utiliser la propriété ToolTipText pour le texte info-bulle d’un ToolStripButton  
  
1. Affectez <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> à `true`la propriété du bouton la valeur.  
  
2. Affectez <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> à `false`la propriété du bouton la valeur.  
  
     La `AutoToolTip` propriété est `true` par défaut pour <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>et. <xref:System.Windows.Forms.ToolStripSplitButton>  
  
     Un <xref:System.Windows.Forms.ToolStripButton> utilise sa `Text` propriété pour le <xref:System.Windows.Forms.ToolTip> texte par défaut. Utilisez cette procédure pour afficher du texte personnalisé dans <xref:System.Windows.Forms.ToolStripButton>un <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
> Si vous affectez <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> à <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>la valeur <xref:System.Windows.Forms.ToolStripItemDisplayStyle> ou, aucun texte n’apparaît sur le bouton, mais l’info-bulle apparaît toujours.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
