---
title: Définir des icônes pour le contrôle TreeView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737267"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Comment : définir des icônes pour le contrôle TreeView Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.TreeView> peut afficher des icônes en regard de chaque nœud. Les icônes sont positionnées à gauche du texte du nœud. Pour afficher ces icônes, vous devez associer l’arborescence à un contrôle de <xref:System.Windows.Forms.ImageList>. Pour plus d’informations sur les listes d’images, consultez [composant ImageList](imagelist-component-windows-forms.md) et [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
> Un bogue dans Microsoft .NET Framework version 1,1 empêche les images d’apparaître sur des nœuds de <xref:System.Windows.Forms.TreeView> lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Pour contourner ce bogue, appelez <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> dans votre méthode `Main` immédiatement après l’appel de <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Ce bogue est résolu dans .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Pour afficher des images dans une arborescence  
  
1. Affectez à la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> du contrôle <xref:System.Windows.Forms.TreeView> le contrôle de <xref:System.Windows.Forms.ImageList> existant que vous souhaitez utiliser.  
  
     Ces propriétés peuvent être définies dans le concepteur avec l’Fenêtre Propriétés, ou dans le code.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. Définissez les propriétés <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> et <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> du nœud. La propriété <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> détermine l’image affichée pour les États normal et développé du nœud, tandis que la propriété <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> détermine l’image affichée pour l’état sélectionné du nœud.  
  
     Ces propriétés peuvent être définies dans le code ou dans l’éditeur TreeNode. Pour ouvrir l’éditeur TreeNode, cliquez sur le bouton de sélection (![le bouton de sélection (...) dans la Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> sur le Fenêtre Propriétés.  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle TreeView](treeview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Guide pratique pour identifier le nœud de TreeView sur lequel un clic est effectué](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
