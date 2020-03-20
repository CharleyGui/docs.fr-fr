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
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="9c4e1-102">Comment : identifier le nœud de TreeView sur lequel un clic est effectué (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9c4e1-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="9c4e1-103">Lorsque vous travaillez <xref:System.Windows.Forms.TreeView> avec le contrôle des formulaires Windows, une tâche commune est de déterminer quel nœud a été cliqué, et de répondre de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="9c4e1-104">Pour déterminer quel nœud TreeView a été cliqué</span><span class="sxs-lookup"><span data-stu-id="9c4e1-104">To determine which TreeView node was clicked</span></span>  
  
1. <span data-ttu-id="9c4e1-105">Utilisez <xref:System.EventArgs> l’objet pour retourner une référence à l’objet de nœuds cliqué.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2. <span data-ttu-id="9c4e1-106">Déterminer quel nœud a <xref:System.Windows.Forms.TreeViewEventArgs> été cliqué en vérifiant la classe, qui contient des données relatives à l’événement.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    > <span data-ttu-id="9c4e1-107">Comme alternative, vous pouvez <xref:System.Windows.Forms.MouseEventArgs> utiliser <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> le de <xref:System.Drawing.Point.X%2A> l’événement ou pour obtenir les valeurs et <xref:System.Drawing.Point.Y%2A> coordonner l’endroit <xref:System.Drawing.Point> où le clic s’est produit.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="9c4e1-108">Ensuite, utilisez <xref:System.Windows.Forms.TreeView> la <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> méthode du contrôle pour déterminer quel nœud a été cliqué.</span><span class="sxs-lookup"><span data-stu-id="9c4e1-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4e1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c4e1-109">See also</span></span>

- [<span data-ttu-id="9c4e1-110">Contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="9c4e1-110">TreeView Control</span></span>](treeview-control-windows-forms.md)
