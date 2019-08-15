---
title: 'Procédure : désactiver des ToolStripMenuItems à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040268"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Procédure : désactiver des ToolStripMenuItems à l’aide du concepteur
Vous pouvez limiter ou élargir les commandes qu’un utilisateur peut effectuer en activant et en désactivant les éléments de menu en réponse aux activités de l’utilisateur. Les éléments de menu sont activés par défaut lorsqu’ils sont créés, mais cela peut être <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> ajusté par le biais de la propriété. Vous pouvez manipuler cette propriété au moment de la conception dans la fenêtre **Propriétés** ou par programmation en la définissant dans le code. Pour plus d’informations, consultez [Guide pratique pour Désactivez des ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).

## <a name="to-disable-a-menu-item-at-design-time"></a>Pour désactiver un élément de menu au moment du design

1. Avec l’élément de menu sélectionné dans le formulaire, affectez <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> à `false`la propriété la valeur.

    > [!TIP]
    >  La désactivation du premier ou de l’élément de menu de niveau supérieur dans un menu désactive tous les éléments de menu contenus dans le menu. De même, la désactivation d’un élément de menu qui contient des éléments de sous-menu désactive les éléments de sous-menu. Si toutes les commandes d’un menu donné ne sont pas disponibles pour l’utilisateur, il est considéré comme une bonne pratique de programmation de masquer et de désactiver l’ensemble du menu, car cela présente une interface utilisateur propre. Vous devez masquer et désactiver le menu, car le masquage seul n’empêche pas l’accès à une commande de menu via une touche de raccourci. Affectez <xref:System.Windows.Forms.ToolStripItem.Visible%2A> `false` à la propriété d’un élément de menu de niveau supérieur la valeur pour masquer tout le menu.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Guide pratique pour Masquer des ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
