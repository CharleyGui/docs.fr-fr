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
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="e6585-102">Procédure : Déterminer le nœud de TreeView sur lequel l’utilisateur a cliqué (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e6585-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="e6585-103">Lors de l’utilisation du <xref:System.Windows.Forms.TreeView> contrôle Windows Forms, une tâche courante consiste à déterminer le nœud sur lequel l’utilisateur a cliqué et à réagir de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="e6585-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="e6585-104">Pour identifier le nœud de TreeView sur lequel l’utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="e6585-104">To determine which TreeView node was clicked</span></span>  
  
1. <span data-ttu-id="e6585-105">Utilisez l' <xref:System.EventArgs> objet pour retourner une référence à l’objet de nœud cliqué.</span><span class="sxs-lookup"><span data-stu-id="e6585-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2. <span data-ttu-id="e6585-106">Déterminez le nœud sur lequel l’utilisateur a <xref:System.Windows.Forms.TreeViewEventArgs> cliqué en vérifiant la classe, qui contient les données relatives à l’événement.</span><span class="sxs-lookup"><span data-stu-id="e6585-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    > <span data-ttu-id="e6585-107">En guise d’alternative, vous pouvez <xref:System.Windows.Forms.MouseEventArgs> utiliser le <xref:System.Windows.Forms.Control.MouseDown> de <xref:System.Windows.Forms.Control.MouseUp> l’événement ou <xref:System.Drawing.Point> pour <xref:System.Drawing.Point.X%2A> récupérer <xref:System.Drawing.Point.Y%2A> les valeurs de coordonnées et du où le clic s’est produit.</span><span class="sxs-lookup"><span data-stu-id="e6585-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="e6585-108">Ensuite, utilisez la <xref:System.Windows.Forms.TreeView> méthode du <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> contrôle pour déterminer sur quel nœud l’utilisateur a cliqué.</span><span class="sxs-lookup"><span data-stu-id="e6585-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6585-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6585-109">See also</span></span>

- [<span data-ttu-id="e6585-110">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="e6585-110">TreeView Control</span></span>](treeview-control-windows-forms.md)
