---
title: 'Comment : identifier le nœud de TreeView sur lequel un clic est effectué'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 7a0e2b69bbec0eb03d40bee2c8e2d4bc9c3558f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742015"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Comment : identifier le nœud de TreeView sur lequel un clic est effectué (Windows Forms)
Lorsque vous travaillez avec le contrôle Windows Forms <xref:System.Windows.Forms.TreeView>, une tâche courante consiste à déterminer le nœud sur lequel l’utilisateur a cliqué et à réagir de manière appropriée.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Pour identifier le nœud de TreeView sur lequel l’utilisateur a cliqué  
  
1. Utilisez l’objet <xref:System.EventArgs> pour retourner une référence à l’objet de nœud cliqué.  
  
2. Déterminez le nœud sur lequel l’utilisateur a cliqué en vérifiant la classe <xref:System.Windows.Forms.TreeViewEventArgs>, qui contient les données relatives à l’événement.  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    > En guise d’alternative, vous pouvez utiliser la <xref:System.Windows.Forms.MouseEventArgs> de l’événement <xref:System.Windows.Forms.Control.MouseDown> ou <xref:System.Windows.Forms.Control.MouseUp> pour récupérer le <xref:System.Drawing.Point.X%2A> et <xref:System.Drawing.Point.Y%2A> valeurs de coordonnées du <xref:System.Drawing.Point> où le clic s’est produit. Ensuite, utilisez la méthode <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> du contrôle <xref:System.Windows.Forms.TreeView> pour déterminer le nœud sur lequel l’utilisateur a cliqué.  
  
## <a name="see-also"></a>Voir aussi

- [TreeView, contrôle](treeview-control-windows-forms.md)
