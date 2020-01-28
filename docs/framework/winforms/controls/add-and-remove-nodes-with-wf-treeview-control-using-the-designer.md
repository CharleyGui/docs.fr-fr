---
title: Ajouter et supprimer des nœuds avec le contrôle TreeView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 7edf09539719ec76fa3f650254c5c84ff0bc3af7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732241"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms à l’aide du concepteur

Étant donné que le contrôle Windows Forms <xref:System.Windows.Forms.TreeView> affiche des nœuds de façon hiérarchique, lorsque vous ajoutez un nœud, vous devez prêter attention à ce qu’est son nœud parent.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.TreeView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Pour ajouter ou supprimer des nœuds dans le concepteur

1. Sélectionnez le contrôle <xref:System.Windows.Forms.TreeView>.

2. Dans la fenêtre **Propriétés** , cliquez sur les **points de suspension** (![le bouton de sélection (...) du bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A>.

     L' **éditeur TreeNode** s’affiche.

3. Pour ajouter des nœuds, un nœud racine doit exister. s’il n’en existe pas, vous devez d’abord ajouter une racine en cliquant sur le bouton **Ajouter une racine** . Vous pouvez ensuite ajouter des nœuds enfants en sélectionnant la racine ou n’importe quel autre nœud, puis en cliquant sur le bouton **Ajouter un enfant** .

4. Pour supprimer des nœuds, sélectionnez le nœud à supprimer, puis cliquez sur le bouton **supprimer** .

## <a name="see-also"></a>Voir aussi

- [TreeView, contrôle](treeview-control-windows-forms.md)
- [Vue d’ensemble du contrôle TreeView](treeview-control-overview-windows-forms.md)
- [Guide pratique pour définir des icônes pour le contrôle TreeView Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Guide pratique pour identifier le nœud de TreeView sur lequel un clic est effectué](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
