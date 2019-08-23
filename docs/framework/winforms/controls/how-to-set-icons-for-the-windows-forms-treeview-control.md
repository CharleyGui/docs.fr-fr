---
title: 'Procédure : définir des icônes pour le contrôle TreeView Windows Forms'
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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909807"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Procédure : définir des icônes pour le contrôle TreeView Windows Forms
Le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms peut afficher des icônes en regard de chaque nœud. Les icônes sont positionnées à gauche du texte du nœud. Pour afficher ces icônes, vous devez associer l’arborescence à un <xref:System.Windows.Forms.ImageList> contrôle. Pour plus d’informations sur les listes d’images, consultez [ [composant ImageList](imagelist-component-windows-forms.md) et procédure: Ajoutez ou supprimez des images avec le composant](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)ImageList Windows Forms.  
  
> [!NOTE]
> Un bogue dans Microsoft .NET Framework version 1,1 empêche les images d' <xref:System.Windows.Forms.TreeView> apparaître sur les nœuds <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>lorsque votre application appelle. Pour contourner ce bogue, <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> appelez dans `Main` votre méthode immédiatement après <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>l’appel de. Ce bogue est résolu dans .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Pour afficher des images dans une arborescence  
  
1. Définissez la <xref:System.Windows.Forms.TreeView> propriété du <xref:System.Windows.Forms.TreeView.ImageList%2A> contrôle sur le contrôle <xref:System.Windows.Forms.ImageList> existant que vous souhaitez utiliser.  
  
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
  
2. Définissez les propriétés et <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> du nœud. La <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> propriété détermine l’image affichée pour les États normal et développé du nœud, et la <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriété détermine l’image affichée pour l’état sélectionné du nœud.  
  
     Ces propriétés peuvent être définies dans le code ou dans l’éditeur TreeNode. Pour ouvrir l’éditeur TreeNode, cliquez sur le bouton de ![sélection (...) dans le fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la <xref:System.Windows.Forms.TreeView.Nodes%2A> propriété sur le fenêtre Propriétés.  
  
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
- [Guide pratique pour Ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Guide pratique pour Itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Guide pratique : Déterminer le nœud de TreeView sur lequel l’utilisateur a cliqué](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Guide pratique pour Ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
