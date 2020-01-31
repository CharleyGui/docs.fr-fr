---
title: Vue d’ensemble du contrôle Panel
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 3ea86e898e8a3e1ca90ba8e0a6240414702a1a73
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744305"
---
# <a name="panel-control-overview-windows-forms"></a>Vue d'ensemble du contrôle Panel (Windows Forms)
Les contrôles de <xref:System.Windows.Forms.Panel> Windows Forms sont utilisés pour fournir un regroupement identifiable pour d’autres contrôles. En règle générale, vous utilisez des panneaux pour subdiviser un formulaire par fonction. Par exemple, vous pouvez avoir un formulaire de commande qui spécifie des options de publipostage, telles que le transporteur de nuit à utiliser. Le regroupement de toutes les options dans un panneau donne à l’utilisateur un indice visuel logique. Au moment du design, tous les contrôles peuvent être facilement déplacés : lorsque vous déplacez le contrôle <xref:System.Windows.Forms.Panel>, tous les contrôles qu’il contient se déplacent également. Les contrôles regroupés dans un volet sont accessibles par le biais de sa propriété <xref:System.Windows.Forms.Control.Controls%2A>. Cette propriété retourne une collection d’instances de <xref:System.Windows.Forms.Control>, donc vous devez généralement effectuer un cast d’un contrôle récupéré de cette façon vers son type spécifique.  
  
## <a name="panel-versus-groupbox"></a>Panel et GroupBox  
 Le contrôle <xref:System.Windows.Forms.Panel> est semblable au contrôle <xref:System.Windows.Forms.GroupBox> ; Toutefois, seul le contrôle <xref:System.Windows.Forms.Panel> peut avoir des barres de défilement, et seul le contrôle <xref:System.Windows.Forms.GroupBox> affiche une légende.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Pour afficher les barres de défilement, affectez à la propriété <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> la valeur `true`. Vous pouvez également personnaliser l’apparence du panneau en définissant les propriétés <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>et <xref:System.Windows.Forms.Panel.BorderStyle%2A>. Pour plus d’informations sur les propriétés <xref:System.Windows.Forms.Control.BackColor%2A> et <xref:System.Windows.Forms.Control.BackgroundImage%2A>, consultez [Comment : définir l’arrière-plan d’un panneau](how-to-set-the-background-of-a-windows-forms-panel.md). La propriété <xref:System.Windows.Forms.Panel.BorderStyle%2A> détermine si le panneau est entouré d’aucune bordure visible (<xref:System.Windows.Forms.BorderStyle.None>), d’une ligne simple (<xref:System.Windows.Forms.BorderStyle.FixedSingle>) ou d’une ligne ombrée (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Panel>
- [GroupBox, contrôle](groupbox-control-windows-forms.md)
- [Guide pratique pour grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur](group-controls-with-wf-panel-control-using-the-designer.md)
- [Guide pratique pour définir l'arrière-plan d'un contrôle Panel Windows Forms à l'aide du concepteur](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
