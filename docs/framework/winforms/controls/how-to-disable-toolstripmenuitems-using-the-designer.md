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
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="9d0d4-102">Procédure : désactiver des ToolStripMenuItems à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="9d0d4-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="9d0d4-103">Vous pouvez limiter ou élargir les commandes qu’un utilisateur peut effectuer en activant et en désactivant les éléments de menu en réponse aux activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="9d0d4-104">Les éléments de menu sont activés par défaut lorsqu’ils sont créés, mais cela peut être <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> ajusté par le biais de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="9d0d4-105">Vous pouvez manipuler cette propriété au moment de la conception dans la fenêtre **Propriétés** ou par programmation en la définissant dans le code.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="9d0d4-106">Pour plus d’informations, consultez [Guide pratique pour Désactivez des ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="9d0d4-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>

## <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="9d0d4-107">Pour désactiver un élément de menu au moment du design</span><span class="sxs-lookup"><span data-stu-id="9d0d4-107">To disable a menu item at design time</span></span>

1. <span data-ttu-id="9d0d4-108">Avec l’élément de menu sélectionné dans le formulaire, affectez <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> à `false`la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-108">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>

    > [!TIP]
    >  <span data-ttu-id="9d0d4-109">La désactivation du premier ou de l’élément de menu de niveau supérieur dans un menu désactive tous les éléments de menu contenus dans le menu.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-109">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="9d0d4-110">De même, la désactivation d’un élément de menu qui contient des éléments de sous-menu désactive les éléments de sous-menu.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-110">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="9d0d4-111">Si toutes les commandes d’un menu donné ne sont pas disponibles pour l’utilisateur, il est considéré comme une bonne pratique de programmation de masquer et de désactiver l’ensemble du menu, car cela présente une interface utilisateur propre.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-111">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="9d0d4-112">Vous devez masquer et désactiver le menu, car le masquage seul n’empêche pas l’accès à une commande de menu via une touche de raccourci.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-112">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="9d0d4-113">Affectez <xref:System.Windows.Forms.ToolStripItem.Visible%2A> `false` à la propriété d’un élément de menu de niveau supérieur la valeur pour masquer tout le menu.</span><span class="sxs-lookup"><span data-stu-id="9d0d4-113">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d0d4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d0d4-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="9d0d4-115">Guide pratique pour Masquer des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="9d0d4-115">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="9d0d4-116">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="9d0d4-116">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
