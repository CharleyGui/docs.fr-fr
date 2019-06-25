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
ms.openlocfilehash: c7c801242c7d5958cce9826a5f60d13a0b257add
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348054"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Procédure : définir des icônes pour le contrôle TreeView Windows Forms
Les formulaires Windows <xref:System.Windows.Forms.TreeView> contrôle peut afficher des icônes en regard de chaque nœud. Les icônes sont positionnées à gauche du texte de nœud. Pour afficher ces icônes, vous devez associer l’arborescence avec un <xref:System.Windows.Forms.ImageList> contrôle. Pour plus d’informations sur les listes d’images, consultez [composant ImageList](imagelist-component-windows-forms.md) et [Comment : Ajouter ou supprimer des Images avec les Windows Forms composant ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Un bogue dans Microsoft .NET Framework version 1.1 empêche l’affichage sur des images <xref:System.Windows.Forms.TreeView> nœuds lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Pour contourner ce bogue, appelez <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> dans votre `Main` méthode immédiatement après l’appel <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Ce bogue est résolu dans .NET Framework 2.0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Pour afficher des images dans une arborescence  
  
1. Définir le <xref:System.Windows.Forms.TreeView> du contrôle <xref:System.Windows.Forms.TreeView.ImageList%2A> propriété existant <xref:System.Windows.Forms.ImageList> contrôle que vous souhaitez utiliser.  
  
     Ces propriétés peuvent être définies dans le concepteur avec la fenêtre Propriétés ou dans le code.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. Définir le nœud <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> et <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriétés. Le <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> propriété détermine l’image affichée pour les États de normal et développé du nœud et le <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriété détermine l’image affichée pour l’état du nœud sélectionné.  
  
     Ces propriétés peuvent être définies dans le code ou dans l’Éditeur TreeNode. Pour ouvrir l’Éditeur TreeNode, cliquez sur le bouton de sélection ( ![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) à côté du <xref:System.Windows.Forms.TreeView.Nodes%2A> propriété dans la fenêtre Propriétés.  
  
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
- [Guide pratique pour Effectuer une itération dans tous les nœuds d’un contrôle de TreeView Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Guide pratique pour Déterminer l’utilisateur a cliqué sur le nœud de TreeView](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Guide pratique pour Ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
