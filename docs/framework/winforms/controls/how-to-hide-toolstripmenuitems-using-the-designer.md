---
title: 'Procédure : masquer des ToolStripMenuItems à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 0e1cd7d1868adabd4d3eec9510f6ee567ba3867d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966617"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Procédure : masquer des ToolStripMenuItems à l’aide du concepteur
Le masquage des éléments de menu est un moyen de contrôler l’interface utilisateur de votre application et de restreindre les commandes utilisateur. Souvent, vous pouvez masquer un menu entier lorsque tous les éléments de menu qu’il contient sont indisponibles. Cela présente moins de distractions pour l’utilisateur. En outre, vous souhaiterez peut-être masquer et désactiver le menu ou l’élément de menu, car le masquage seul n’empêche pas l’utilisateur d’accéder à une commande de menu à l’aide d’une touche de raccourci. Pour plus d’informations sur la désactivation des éléments [de menu, consultez Procédure: Désactivez des ToolStripMenuItems à](how-to-disable-toolstripmenuitems-using-the-designer.md)l’aide du concepteur.

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Pour masquer un menu du plus haut niveau et ses éléments de sous-menu

1. Sélectionnez l’élément de menu de niveau supérieur et affectez <xref:System.Windows.Forms.ToolStripItem.Available%2A> à `false`sa <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriété ou la valeur.

     Quand vous masquez l’élément de menu de niveau supérieur, tous les éléments de menu de ce menu sont également masqués. Si vous cliquez ailleurs que sur le <xref:System.Windows.Forms.MenuStrip> `false`paramètre <xref:System.Windows.Forms.ToolStripItem.Visible%2A> après, la totalité de l’élément de menu de niveau supérieur et ses éléments de sous-menu disparaissent de votre formulaire, ce qui vous indique l’effet d’exécution de votre action. Pour afficher l’élément de menu de niveau supérieur masqué au moment du design, cliquez <xref:System.Windows.Forms.MenuStrip> sur dans la **barre d’état des composants**, dans la structure du **document**ou en haut de la grille des propriétés.

> [!NOTE]
> Vous allez rarement masquer un menu entier, à l’exception des menus enfants d’interface multidocument (MDI) dans un scénario de fusion.

## <a name="to-hide-a-submenu-item"></a>Pour masquer un élément de sous-menu

1. Sélectionnez l’élément de sous-menu et <xref:System.Windows.Forms.ToolStripItem.Visible%2A> affectez `false`à sa propriété la valeur.

     Quand vous masquez un élément de sous-menu, il reste visible dans votre formulaire au moment de la conception, ce qui vous permet de le sélectionner facilement pour un travail supplémentaire. Elle sera en fait masquée au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
- [Guide pratique : Désactiver des ToolStripMenuItems à l’aide du concepteur](how-to-disable-toolstripmenuitems-using-the-designer.md)
