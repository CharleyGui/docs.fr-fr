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
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="e6073-102">Procédure : masquer des ToolStripMenuItems à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="e6073-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="e6073-103">Le masquage des éléments de menu est un moyen de contrôler l’interface utilisateur de votre application et de restreindre les commandes utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6073-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="e6073-104">Souvent, vous pouvez masquer un menu entier lorsque tous les éléments de menu qu’il contient sont indisponibles.</span><span class="sxs-lookup"><span data-stu-id="e6073-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="e6073-105">Cela présente moins de distractions pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6073-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="e6073-106">En outre, vous souhaiterez peut-être masquer et désactiver le menu ou l’élément de menu, car le masquage seul n’empêche pas l’utilisateur d’accéder à une commande de menu à l’aide d’une touche de raccourci.</span><span class="sxs-lookup"><span data-stu-id="e6073-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="e6073-107">Pour plus d’informations sur la désactivation des éléments [de menu, consultez Procédure: Désactivez des ToolStripMenuItems à](how-to-disable-toolstripmenuitems-using-the-designer.md)l’aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="e6073-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="e6073-108">Pour masquer un menu du plus haut niveau et ses éléments de sous-menu</span><span class="sxs-lookup"><span data-stu-id="e6073-108">To hide a top-level menu and its submenu items</span></span>

1. <span data-ttu-id="e6073-109">Sélectionnez l’élément de menu de niveau supérieur et affectez <xref:System.Windows.Forms.ToolStripItem.Available%2A> à `false`sa <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriété ou la valeur.</span><span class="sxs-lookup"><span data-stu-id="e6073-109">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>

     <span data-ttu-id="e6073-110">Quand vous masquez l’élément de menu de niveau supérieur, tous les éléments de menu de ce menu sont également masqués.</span><span class="sxs-lookup"><span data-stu-id="e6073-110">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="e6073-111">Si vous cliquez ailleurs que sur le <xref:System.Windows.Forms.MenuStrip> `false`paramètre <xref:System.Windows.Forms.ToolStripItem.Visible%2A> après, la totalité de l’élément de menu de niveau supérieur et ses éléments de sous-menu disparaissent de votre formulaire, ce qui vous indique l’effet d’exécution de votre action.</span><span class="sxs-lookup"><span data-stu-id="e6073-111">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="e6073-112">Pour afficher l’élément de menu de niveau supérieur masqué au moment du design, cliquez <xref:System.Windows.Forms.MenuStrip> sur dans la **barre d’état des composants**, dans la structure du **document**ou en haut de la grille des propriétés.</span><span class="sxs-lookup"><span data-stu-id="e6073-112">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>

> [!NOTE]
> <span data-ttu-id="e6073-113">Vous allez rarement masquer un menu entier, à l’exception des menus enfants d’interface multidocument (MDI) dans un scénario de fusion.</span><span class="sxs-lookup"><span data-stu-id="e6073-113">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>

## <a name="to-hide-a-submenu-item"></a><span data-ttu-id="e6073-114">Pour masquer un élément de sous-menu</span><span class="sxs-lookup"><span data-stu-id="e6073-114">To hide a submenu item</span></span>

1. <span data-ttu-id="e6073-115">Sélectionnez l’élément de sous-menu et <xref:System.Windows.Forms.ToolStripItem.Visible%2A> affectez `false`à sa propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="e6073-115">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>

     <span data-ttu-id="e6073-116">Quand vous masquez un élément de sous-menu, il reste visible dans votre formulaire au moment de la conception, ce qui vous permet de le sélectionner facilement pour un travail supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="e6073-116">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="e6073-117">Elle sera en fait masquée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6073-117">It will actually be hidden at run time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6073-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6073-118">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="e6073-119">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="e6073-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="e6073-120">Guide pratique : Désactiver des ToolStripMenuItems à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="e6073-120">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
