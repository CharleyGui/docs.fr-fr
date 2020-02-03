---
title: Définir des icônes pour le contrôle TreeView
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
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737267"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="f8413-102">Comment : définir des icônes pour le contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8413-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="f8413-103">Le contrôle Windows Forms <xref:System.Windows.Forms.TreeView> peut afficher des icônes en regard de chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="f8413-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="f8413-104">Les icônes sont positionnées à gauche du texte du nœud.</span><span class="sxs-lookup"><span data-stu-id="f8413-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="f8413-105">Pour afficher ces icônes, vous devez associer l’arborescence à un contrôle de <xref:System.Windows.Forms.ImageList>.</span><span class="sxs-lookup"><span data-stu-id="f8413-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="f8413-106">Pour plus d’informations sur les listes d’images, consultez [composant ImageList](imagelist-component-windows-forms.md) et [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="f8413-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8413-107">Un bogue dans Microsoft .NET Framework version 1,1 empêche les images d’apparaître sur des nœuds de <xref:System.Windows.Forms.TreeView> lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f8413-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f8413-108">Pour contourner ce bogue, appelez <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> dans votre méthode `Main` immédiatement après l’appel de <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8413-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="f8413-109">Ce bogue est résolu dans .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f8413-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="f8413-110">Pour afficher des images dans une arborescence</span><span class="sxs-lookup"><span data-stu-id="f8413-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="f8413-111">Affectez à la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> du contrôle <xref:System.Windows.Forms.TreeView> le contrôle de <xref:System.Windows.Forms.ImageList> existant que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="f8413-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="f8413-112">Ces propriétés peuvent être définies dans le concepteur avec l’Fenêtre Propriétés, ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="f8413-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="f8413-113">Définissez les propriétés <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> et <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> du nœud.</span><span class="sxs-lookup"><span data-stu-id="f8413-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="f8413-114">La propriété <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> détermine l’image affichée pour les États normal et développé du nœud, tandis que la propriété <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> détermine l’image affichée pour l’état sélectionné du nœud.</span><span class="sxs-lookup"><span data-stu-id="f8413-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="f8413-115">Ces propriétés peuvent être définies dans le code ou dans l’éditeur TreeNode.</span><span class="sxs-lookup"><span data-stu-id="f8413-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="f8413-116">Pour ouvrir l’éditeur TreeNode, cliquez sur le bouton de sélection (![le bouton de sélection (...) dans la Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> sur le Fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="f8413-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8413-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8413-117">See also</span></span>

- [<span data-ttu-id="f8413-118">Vue d’ensemble du contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="f8413-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="f8413-119">Guide pratique pour ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8413-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="f8413-120">Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8413-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="f8413-121">Guide pratique pour identifier le nœud de TreeView sur lequel un clic est effectué</span><span class="sxs-lookup"><span data-stu-id="f8413-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="f8413-122">Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f8413-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
