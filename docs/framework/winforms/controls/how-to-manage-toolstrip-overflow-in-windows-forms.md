---
title: 'Comment : gérer le dépassement de capacité de contrôles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736145"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Comment : Gérer le dépassement de capacité de contrôles ToolStrip dans les Windows Forms

Lorsque tous les éléments d’un contrôle <xref:System.Windows.Forms.ToolStrip> ne tiennent pas dans l’espace alloué, vous pouvez activer la fonctionnalité de dépassement de capacité sur le <xref:System.Windows.Forms.ToolStrip> et déterminer le comportement de dépassement de <xref:System.Windows.Forms.ToolStripItem>spécifiques.

Lorsque vous ajoutez des <xref:System.Windows.Forms.ToolStripItem>qui requièrent plus d’espace que ce qui est alloué à la <xref:System.Windows.Forms.ToolStrip> en fonction de la taille actuelle du formulaire, un <xref:System.Windows.Forms.ToolStripOverflowButton> s’affiche automatiquement sur le <xref:System.Windows.Forms.ToolStrip>. Le <xref:System.Windows.Forms.ToolStripOverflowButton> s’affiche, et les éléments avec dépassement de capacité sont déplacés dans le menu déroulant de dépassement de capacité. Cela vous permet de personnaliser et de hiérarchiser la façon dont vos éléments de <xref:System.Windows.Forms.ToolStrip> s’ajustent correctement à différentes tailles de formulaire. Vous pouvez également modifier l’apparence de vos éléments lorsqu’ils entrent dans le débordement à l’aide des propriétés <xref:System.Windows.Forms.ToolStripItem.Placement%2A> et <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> et de l’événement <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>. Si vous agrandissez le formulaire au moment de la conception ou de l’exécution, davantage de <xref:System.Windows.Forms.ToolStripItem>s peuvent être affichés sur le <xref:System.Windows.Forms.ToolStrip> principal et le <xref:System.Windows.Forms.ToolStripOverflowButton> peut même disparaître jusqu’à ce que vous réduisiez la taille du formulaire.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>Pour activer le dépassement de capacité sur un contrôle ToolStrip

- Assurez-vous que la propriété <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> n’est pas définie sur `false` pour le <xref:System.Windows.Forms.ToolStrip>. La valeur par défaut est `True`,

     Lorsque <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> est `True` (valeur par défaut), un <xref:System.Windows.Forms.ToolStripItem> est envoyé au menu déroulant de dépassement de capacité lorsque le contenu du <xref:System.Windows.Forms.ToolStripItem> dépasse la largeur d’un <xref:System.Windows.Forms.ToolStrip> horizontal ou la hauteur d’un <xref:System.Windows.Forms.ToolStrip>vertical.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Pour spécifier le comportement de dépassement de capacité d’un ToolStripItem spécifique

- Affectez la valeur souhaitée à la propriété <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> du <xref:System.Windows.Forms.ToolStripItem>. Les possibilités sont `Always`, `Never`et `AsNeeded`. La valeur par défaut est `AsNeeded`,

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architecture du contrôle ToolStrip](toolstrip-control-architecture.md)
- [Résumé de la technologie ToolStrip](toolstrip-technology-summary.md)
