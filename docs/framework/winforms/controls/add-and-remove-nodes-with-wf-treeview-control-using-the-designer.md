---
title: Ajouter et supprimer des nœuds avec le contrôle TreeView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 7edf09539719ec76fa3f650254c5c84ff0bc3af7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732241"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="6db6c-102">Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="6db6c-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="6db6c-103">Étant donné que le contrôle Windows Forms <xref:System.Windows.Forms.TreeView> affiche des nœuds de façon hiérarchique, lorsque vous ajoutez un nœud, vous devez prêter attention à ce qu’est son nœud parent.</span><span class="sxs-lookup"><span data-stu-id="6db6c-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="6db6c-104">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6db6c-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="6db6c-105">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6db6c-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="6db6c-106">Pour ajouter ou supprimer des nœuds dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="6db6c-106">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="6db6c-107">Sélectionnez le contrôle <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6db6c-107">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="6db6c-108">Dans la fenêtre **Propriétés** , cliquez sur les **points de suspension** (![le bouton de sélection (...) du bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="6db6c-108">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="6db6c-109">L' **éditeur TreeNode** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6db6c-109">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="6db6c-110">Pour ajouter des nœuds, un nœud racine doit exister. s’il n’en existe pas, vous devez d’abord ajouter une racine en cliquant sur le bouton **Ajouter une racine** .</span><span class="sxs-lookup"><span data-stu-id="6db6c-110">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="6db6c-111">Vous pouvez ensuite ajouter des nœuds enfants en sélectionnant la racine ou n’importe quel autre nœud, puis en cliquant sur le bouton **Ajouter un enfant** .</span><span class="sxs-lookup"><span data-stu-id="6db6c-111">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="6db6c-112">Pour supprimer des nœuds, sélectionnez le nœud à supprimer, puis cliquez sur le bouton **supprimer** .</span><span class="sxs-lookup"><span data-stu-id="6db6c-112">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="6db6c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6db6c-113">See also</span></span>

- [<span data-ttu-id="6db6c-114">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="6db6c-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="6db6c-115">Vue d’ensemble du contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="6db6c-115">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="6db6c-116">Guide pratique pour définir des icônes pour le contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6db6c-116">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="6db6c-117">Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6db6c-117">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="6db6c-118">Guide pratique pour identifier le nœud de TreeView sur lequel un clic est effectué</span><span class="sxs-lookup"><span data-stu-id="6db6c-118">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="6db6c-119">Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6db6c-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
