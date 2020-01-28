---
title: Ajouter et supprimer des nœuds avec le contrôle TreeView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: 02b3a7286798c6f2a6426e09c8fc6c18b74a6bf0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731963"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.TreeView> stocke les nœuds de niveau supérieur dans sa collection <xref:System.Windows.Forms.TreeView.Nodes%2A>. Chaque <xref:System.Windows.Forms.TreeNode> possède également sa propre collection <xref:System.Windows.Forms.TreeNode.Nodes%2A> pour stocker ses nœuds enfants. Les deux propriétés de collection sont de type <xref:System.Windows.Forms.TreeNodeCollection>, qui fournit des membres de collection standard qui vous permettent d’ajouter, de supprimer et de réorganiser les nœuds à un seul niveau de la hiérarchie de nœuds.  
  
### <a name="to-add-nodes-programmatically"></a>Pour ajouter des nœuds par programmation  
  
1. Utilisez la méthode <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> de l’arborescence.  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a>Pour supprimer des nœuds par programmation  
  
1. Utilisez la méthode <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> de l’arborescence pour supprimer un seul nœud, ou la méthode <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> pour effacer tous les nœuds.  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [TreeView, contrôle](treeview-control-windows-forms.md)
- [Vue d’ensemble du contrôle TreeView](treeview-control-overview-windows-forms.md)
- [Guide pratique pour définir des icônes pour le contrôle TreeView Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Guide pratique pour identifier le nœud de TreeView sur lequel un clic est effectué](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
