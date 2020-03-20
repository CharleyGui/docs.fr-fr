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
ms.openlocfilehash: d960eaae2aa479e0be74e9a5e4fdbfec8ff411c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182178"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Comment : identifier le nœud de TreeView sur lequel un clic est effectué (Windows Forms)
Lorsque vous travaillez <xref:System.Windows.Forms.TreeView> avec le contrôle des formulaires Windows, une tâche commune est de déterminer quel nœud a été cliqué, et de répondre de manière appropriée.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Pour déterminer quel nœud TreeView a été cliqué  
  
1. Utilisez <xref:System.EventArgs> l’objet pour retourner une référence à l’objet de nœuds cliqué.  
  
2. Déterminer quel nœud a <xref:System.Windows.Forms.TreeViewEventArgs> été cliqué en vérifiant la classe, qui contient des données relatives à l’événement.  
  
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
    > Comme alternative, vous pouvez <xref:System.Windows.Forms.MouseEventArgs> utiliser <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> le de <xref:System.Drawing.Point.X%2A> l’événement ou pour obtenir les valeurs et <xref:System.Drawing.Point.Y%2A> coordonner l’endroit <xref:System.Drawing.Point> où le clic s’est produit. Ensuite, utilisez <xref:System.Windows.Forms.TreeView> la <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> méthode du contrôle pour déterminer quel nœud a été cliqué.  
  
## <a name="see-also"></a>Voir aussi

- [Contrôle TreeView](treeview-control-windows-forms.md)
