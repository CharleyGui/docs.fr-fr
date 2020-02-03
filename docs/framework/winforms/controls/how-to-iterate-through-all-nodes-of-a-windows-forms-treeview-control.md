---
title: Itérer au sein de tous les nœuds du contrôle TreeView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
ms.openlocfilehash: 010932fa3fdfaa907325b9934682dcbf889265c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736367"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="78a9b-102">Comment : itérer au sein de tous les nœuds d'un contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78a9b-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="78a9b-103">Il est parfois utile d’examiner chaque nœud dans un contrôle de Windows Forms <xref:System.Windows.Forms.TreeView> afin d’effectuer des calculs sur les valeurs de nœud.</span><span class="sxs-lookup"><span data-stu-id="78a9b-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="78a9b-104">Cette opération peut être effectuée à l’aide d’une procédure récursive (méthode récursive en C# et C++) qui procède à une itération au sein de chaque nœud dans chaque collection de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="78a9b-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="78a9b-105">Chaque objet <xref:System.Windows.Forms.TreeNode> dans une arborescence possède des propriétés que vous pouvez utiliser pour naviguer dans l’arborescence : <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>et <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span><span class="sxs-lookup"><span data-stu-id="78a9b-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="78a9b-106">La valeur de la propriété <xref:System.Windows.Forms.TreeNode.Parent%2A> est le nœud parent du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="78a9b-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="78a9b-107">Les nœuds enfants du nœud actuel, le cas échéant, sont répertoriés dans sa propriété <xref:System.Windows.Forms.TreeNode.Nodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="78a9b-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="78a9b-108">Le contrôle <xref:System.Windows.Forms.TreeView> possède lui-même la propriété <xref:System.Windows.Forms.TreeView.TopNode%2A>, qui est le nœud racine de l’intégralité de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="78a9b-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="78a9b-109">Pour procéder à une itération au sein de tous les nœuds d’un contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="78a9b-109">To iterate through all nodes of the TreeView control</span></span>  
  
1. <span data-ttu-id="78a9b-110">Créez une procédure récursive (méthode récursive en C# et C++) pour tester chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="78a9b-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2. <span data-ttu-id="78a9b-111">Appelez la procédure.</span><span class="sxs-lookup"><span data-stu-id="78a9b-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="78a9b-112">L’exemple suivant montre comment imprimer la propriété <xref:System.Windows.Forms.TreeNode.Text%2A> de chaque objet <xref:System.Windows.Forms.TreeNode> :</span><span class="sxs-lookup"><span data-stu-id="78a9b-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="78a9b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78a9b-113">See also</span></span>

- [<span data-ttu-id="78a9b-114">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="78a9b-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="78a9b-115">Procédures récursives</span><span class="sxs-lookup"><span data-stu-id="78a9b-115">Recursive Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
