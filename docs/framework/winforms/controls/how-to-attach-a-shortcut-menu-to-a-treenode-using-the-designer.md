---
title: 'Procédure : attacher un menu contextuel à un TreeNode à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040448"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="9e77c-102">Procédure : attacher un menu contextuel à un TreeNode à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="9e77c-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="9e77c-103">Le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms affiche une hiérarchie de nœuds, comme les fichiers et les dossiers affichés dans le volet gauche de la fonctionnalité Explorateur Windows dans les systèmes d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="9e77c-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="9e77c-104">En définissant <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> la propriété, vous pouvez fournir des opérations contextuelles à l’utilisateur lorsqu’il clique <xref:System.Windows.Forms.TreeView> avec le bouton droit sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="9e77c-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="9e77c-105">En associant un <xref:System.Windows.Forms.ContextMenuStrip> composant à des <xref:System.Windows.Forms.TreeNode> éléments individuels, vous pouvez ajouter un niveau personnalisé de fonctionnalité de menu contextuel à vos <xref:System.Windows.Forms.TreeView> contrôles.</span><span class="sxs-lookup"><span data-stu-id="9e77c-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="9e77c-106">Pour associer un menu contextuel à un TreeNode au moment du design</span><span class="sxs-lookup"><span data-stu-id="9e77c-106">To associate a shortcut menu with a TreeNode at design time</span></span>

1. <span data-ttu-id="9e77c-107">Ajoutez un <xref:System.Windows.Forms.TreeView> contrôle à votre formulaire, puis ajoutez des nœuds <xref:System.Windows.Forms.TreeView> au en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="9e77c-107">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="9e77c-108">Pour plus d'informations, voir [Procédure : Ajoutez et supprimez des nœuds avec le](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)contrôle TreeView Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9e77c-108">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>

2. <span data-ttu-id="9e77c-109">Ajoutez un <xref:System.Windows.Forms.ContextMenuStrip> composant à votre formulaire, puis ajoutez des éléments de menu au menu contextuel qui représentent les opérations au niveau du nœud que vous souhaitez rendre disponibles au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9e77c-109">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="9e77c-110">Pour plus d’informations, consultez [Guide pratique pour Ajouter des éléments de menu à](how-to-add-menu-items-to-a-contextmenustrip.md)un ContextMenuStrip.</span><span class="sxs-lookup"><span data-stu-id="9e77c-110">For more information, see [How to: Add Menu Items to a ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>

3. <span data-ttu-id="9e77c-111">Rouvrez la boîte de dialogue **TreeNodeEditor** pour le <xref:System.Windows.Forms.TreeView> contrôle, sélectionnez le nœud à modifier, puis définissez sa <xref:System.Windows.Forms.ContextMenuStrip> propriété sur le menu contextuel que vous avez ajouté.</span><span class="sxs-lookup"><span data-stu-id="9e77c-111">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>

4. <span data-ttu-id="9e77c-112">Lorsque cette propriété est définie, le menu contextuel s’affiche lorsque vous cliquez avec le bouton droit sur le nœud.</span><span class="sxs-lookup"><span data-stu-id="9e77c-112">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>

     <span data-ttu-id="9e77c-113">En outre, vous souhaiterez peut-être écrire du code <xref:System.Windows.Forms.ToolStripItem.Click> pour gérer les événements de ces éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="9e77c-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e77c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e77c-114">See also</span></span>

- [<span data-ttu-id="9e77c-115">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="9e77c-115">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="9e77c-116">Vue d’ensemble du contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="9e77c-116">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="9e77c-117">ContextMenuStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="9e77c-117">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
