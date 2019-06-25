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
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="a21da-102">Procédure : définir des icônes pour le contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a21da-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="a21da-103">Les formulaires Windows <xref:System.Windows.Forms.TreeView> contrôle peut afficher des icônes en regard de chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="a21da-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="a21da-104">Les icônes sont positionnées à gauche du texte de nœud.</span><span class="sxs-lookup"><span data-stu-id="a21da-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="a21da-105">Pour afficher ces icônes, vous devez associer l’arborescence avec un <xref:System.Windows.Forms.ImageList> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a21da-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="a21da-106">Pour plus d’informations sur les listes d’images, consultez [composant ImageList](imagelist-component-windows-forms.md) et [Comment : Ajouter ou supprimer des Images avec les Windows Forms composant ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="a21da-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a21da-107">Un bogue dans Microsoft .NET Framework version 1.1 empêche l’affichage sur des images <xref:System.Windows.Forms.TreeView> nœuds lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a21da-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a21da-108">Pour contourner ce bogue, appelez <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> dans votre `Main` méthode immédiatement après l’appel <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="a21da-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="a21da-109">Ce bogue est résolu dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a21da-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="a21da-110">Pour afficher des images dans une arborescence</span><span class="sxs-lookup"><span data-stu-id="a21da-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="a21da-111">Définir le <xref:System.Windows.Forms.TreeView> du contrôle <xref:System.Windows.Forms.TreeView.ImageList%2A> propriété existant <xref:System.Windows.Forms.ImageList> contrôle que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="a21da-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="a21da-112">Ces propriétés peuvent être définies dans le concepteur avec la fenêtre Propriétés ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="a21da-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="a21da-113">Définir le nœud <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> et <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="a21da-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="a21da-114">Le <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> propriété détermine l’image affichée pour les États de normal et développé du nœud et le <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriété détermine l’image affichée pour l’état du nœud sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a21da-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="a21da-115">Ces propriétés peuvent être définies dans le code ou dans l’Éditeur TreeNode.</span><span class="sxs-lookup"><span data-stu-id="a21da-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="a21da-116">Pour ouvrir l’Éditeur TreeNode, cliquez sur le bouton de sélection ( ![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) à côté du <xref:System.Windows.Forms.TreeView.Nodes%2A> propriété dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="a21da-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a21da-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a21da-117">See also</span></span>

- [<span data-ttu-id="a21da-118">Vue d’ensemble du contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="a21da-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="a21da-119">Guide pratique pour Ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a21da-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="a21da-120">Guide pratique pour Effectuer une itération dans tous les nœuds d’un contrôle de TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a21da-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="a21da-121">Guide pratique pour Déterminer l’utilisateur a cliqué sur le nœud de TreeView</span><span class="sxs-lookup"><span data-stu-id="a21da-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="a21da-122">Guide pratique pour Ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a21da-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
