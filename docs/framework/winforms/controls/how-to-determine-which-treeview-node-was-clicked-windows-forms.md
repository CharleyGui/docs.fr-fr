---
title: 'Procédure : Déterminer le nœud de TreeView sur lequel l’utilisateur a cliqué (Windows Forms)'
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
ms.openlocfilehash: ab93158daf987e2f19516b8fb3abf80bfe79a12c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967342"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Procédure : Déterminer le nœud de TreeView sur lequel l’utilisateur a cliqué (Windows Forms)
Lors de l’utilisation du <xref:System.Windows.Forms.TreeView> contrôle Windows Forms, une tâche courante consiste à déterminer le nœud sur lequel l’utilisateur a cliqué et à réagir de manière appropriée.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Pour identifier le nœud de TreeView sur lequel l’utilisateur a cliqué  
  
1. Utilisez l' <xref:System.EventArgs> objet pour retourner une référence à l’objet de nœud cliqué.  
  
2. Déterminez le nœud sur lequel l’utilisateur a <xref:System.Windows.Forms.TreeViewEventArgs> cliqué en vérifiant la classe, qui contient les données relatives à l’événement.  
  
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
    > En guise d’alternative, vous pouvez <xref:System.Windows.Forms.MouseEventArgs> utiliser le <xref:System.Windows.Forms.Control.MouseDown> de <xref:System.Windows.Forms.Control.MouseUp> l’événement ou <xref:System.Drawing.Point> pour <xref:System.Drawing.Point.X%2A> récupérer <xref:System.Drawing.Point.Y%2A> les valeurs de coordonnées et du où le clic s’est produit. Ensuite, utilisez la <xref:System.Windows.Forms.TreeView> méthode du <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> contrôle pour déterminer sur quel nœud l’utilisateur a cliqué.  
  
## <a name="see-also"></a>Voir aussi

- [TreeView, contrôle](treeview-control-windows-forms.md)
