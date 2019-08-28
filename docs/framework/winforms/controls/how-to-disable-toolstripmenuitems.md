---
title: 'Procédure : désactiver des ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046224"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Procédure : désactiver des ToolStripMenuItems
Vous pouvez limiter ou élargir les commandes qu’un utilisateur peut effectuer en activant et en désactivant les éléments de menu en réponse aux activités de l’utilisateur. Les éléments de menu sont activés par défaut lorsqu’ils sont créés, mais cela peut être <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> ajusté par le biais de la propriété. Vous pouvez manipuler cette propriété au moment de la conception dans la fenêtre **Propriétés** ou par programmation en la définissant dans le code.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>Pour désactiver un élément de menu par programmation  
  
- Dans la méthode où vous définissez les propriétés de l’élément de menu, ajoutez du code pour <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> affecter à `false`la propriété la valeur.  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    > La désactivation du premier ou de l’élément de menu de niveau supérieur dans un menu masque tous les éléments de menu contenus dans le menu, mais ne les désactive pas. De même, la désactivation d’un élément de menu qui contient des éléments de sous-menu masque les éléments de sous-menu, mais ne les désactive pas. Si toutes les commandes d’un menu donné ne sont pas disponibles pour l’utilisateur, il est considéré comme une bonne pratique de programmation de masquer et de désactiver l’ensemble du menu, car cela présente une interface utilisateur propre. Vous devez masquer et désactiver le menu, et désactiver chaque élément et élément de sous-menu dans le menu, car le masquage seul n’empêche pas l’accès à une commande de menu via une touche de raccourci. Affectez <xref:System.Windows.Forms.ToolStripItem.Visible%2A> `false` à la propriété d’un élément de menu de niveau supérieur la valeur pour masquer tout le menu.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Guide pratique : Masquer des ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Vue d'ensemble du contrôle MenuStrip](menustrip-control-overview-windows-forms.md)
