---
title: Ajouter et enlever les nœuds avec le contrôle TreeView
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
ms.openlocfilehash: f1e74e6d2f827167c32a6955b3010b59cb2f85b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142210"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms
Le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms stocke les <xref:System.Windows.Forms.TreeView.Nodes%2A> nœuds de haut niveau de sa collection. Chacun <xref:System.Windows.Forms.TreeNode> a également <xref:System.Windows.Forms.TreeNode.Nodes%2A> sa propre collection pour stocker ses nœuds pour enfants. Les deux propriétés <xref:System.Windows.Forms.TreeNodeCollection>de collecte sont de type , qui fournit des membres de collecte standard qui vous permettent d’ajouter, enlever et réorganiser les nœuds à un seul niveau de la hiérarchie des nœuds.  
  
### <a name="to-add-nodes-programmatically"></a>Pour ajouter des nœuds programmatiquement  
  
1. Utilisez <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> la méthode de la <xref:System.Windows.Forms.TreeView.Nodes%2A> propriété de la vue sur l’arbre.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Pour enlever les nœuds programmatiquement  
  
1. Utilisez <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> la méthode de la <xref:System.Windows.Forms.TreeView.Nodes%2A> propriété de la vue d’arbre pour enlever un seul nœud, ou la <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> méthode pour effacer tous les nœuds.  
  
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

- [Contrôle TreeView](treeview-control-windows-forms.md)
- [Vue d’ensemble du contrôle TreeView](treeview-control-overview-windows-forms.md)
- [Guide pratique pour définir des icônes pour le contrôle TreeView Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Comment : identifier le nœud de TreeView sur lequel un clic est effectué](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
