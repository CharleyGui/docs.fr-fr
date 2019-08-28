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
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="e2657-102">Procédure : désactiver des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="e2657-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="e2657-103">Vous pouvez limiter ou élargir les commandes qu’un utilisateur peut effectuer en activant et en désactivant les éléments de menu en réponse aux activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e2657-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="e2657-104">Les éléments de menu sont activés par défaut lorsqu’ils sont créés, mais cela peut être <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> ajusté par le biais de la propriété.</span><span class="sxs-lookup"><span data-stu-id="e2657-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="e2657-105">Vous pouvez manipuler cette propriété au moment de la conception dans la fenêtre **Propriétés** ou par programmation en la définissant dans le code.</span><span class="sxs-lookup"><span data-stu-id="e2657-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="e2657-106">Pour désactiver un élément de menu par programmation</span><span class="sxs-lookup"><span data-stu-id="e2657-106">To disable a menu item programmatically</span></span>  
  
- <span data-ttu-id="e2657-107">Dans la méthode où vous définissez les propriétés de l’élément de menu, ajoutez du code pour <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> affecter à `false`la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="e2657-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
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
    > <span data-ttu-id="e2657-108">La désactivation du premier ou de l’élément de menu de niveau supérieur dans un menu masque tous les éléments de menu contenus dans le menu, mais ne les désactive pas.</span><span class="sxs-lookup"><span data-stu-id="e2657-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="e2657-109">De même, la désactivation d’un élément de menu qui contient des éléments de sous-menu masque les éléments de sous-menu, mais ne les désactive pas.</span><span class="sxs-lookup"><span data-stu-id="e2657-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="e2657-110">Si toutes les commandes d’un menu donné ne sont pas disponibles pour l’utilisateur, il est considéré comme une bonne pratique de programmation de masquer et de désactiver l’ensemble du menu, car cela présente une interface utilisateur propre.</span><span class="sxs-lookup"><span data-stu-id="e2657-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="e2657-111">Vous devez masquer et désactiver le menu, et désactiver chaque élément et élément de sous-menu dans le menu, car le masquage seul n’empêche pas l’accès à une commande de menu via une touche de raccourci.</span><span class="sxs-lookup"><span data-stu-id="e2657-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="e2657-112">Affectez <xref:System.Windows.Forms.ToolStripItem.Visible%2A> `false` à la propriété d’un élément de menu de niveau supérieur la valeur pour masquer tout le menu.</span><span class="sxs-lookup"><span data-stu-id="e2657-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2657-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2657-113">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="e2657-114">Guide pratique : Masquer des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="e2657-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="e2657-115">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="e2657-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
