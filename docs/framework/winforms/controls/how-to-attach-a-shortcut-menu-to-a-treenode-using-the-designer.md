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
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Procédure : attacher un menu contextuel à un TreeNode à l’aide du concepteur
Le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms affiche une hiérarchie de nœuds, comme les fichiers et les dossiers affichés dans le volet gauche de la fonctionnalité Explorateur Windows dans les systèmes d’exploitation Windows. En définissant <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> la propriété, vous pouvez fournir des opérations contextuelles à l’utilisateur lorsqu’il clique <xref:System.Windows.Forms.TreeView> avec le bouton droit sur le contrôle. En associant un <xref:System.Windows.Forms.ContextMenuStrip> composant à des <xref:System.Windows.Forms.TreeNode> éléments individuels, vous pouvez ajouter un niveau personnalisé de fonctionnalité de menu contextuel à vos <xref:System.Windows.Forms.TreeView> contrôles.

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Pour associer un menu contextuel à un TreeNode au moment du design

1. Ajoutez un <xref:System.Windows.Forms.TreeView> contrôle à votre formulaire, puis ajoutez des nœuds <xref:System.Windows.Forms.TreeView> au en fonction des besoins. Pour plus d'informations, voir [Procédure : Ajoutez et supprimez des nœuds avec le](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)contrôle TreeView Windows Forms.

2. Ajoutez un <xref:System.Windows.Forms.ContextMenuStrip> composant à votre formulaire, puis ajoutez des éléments de menu au menu contextuel qui représentent les opérations au niveau du nœud que vous souhaitez rendre disponibles au moment de l’exécution. Pour plus d’informations, consultez [Guide pratique pour Ajouter des éléments de menu à](how-to-add-menu-items-to-a-contextmenustrip.md)un ContextMenuStrip.

3. Rouvrez la boîte de dialogue **TreeNodeEditor** pour le <xref:System.Windows.Forms.TreeView> contrôle, sélectionnez le nœud à modifier, puis définissez sa <xref:System.Windows.Forms.ContextMenuStrip> propriété sur le menu contextuel que vous avez ajouté.

4. Lorsque cette propriété est définie, le menu contextuel s’affiche lorsque vous cliquez avec le bouton droit sur le nœud.

     En outre, vous souhaiterez peut-être écrire du code <xref:System.Windows.Forms.ToolStripItem.Click> pour gérer les événements de ces éléments de menu.

## <a name="see-also"></a>Voir aussi

- [TreeView, contrôle](treeview-control-windows-forms.md)
- [Vue d’ensemble du contrôle TreeView](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip, contrôle](contextmenustrip-control.md)
