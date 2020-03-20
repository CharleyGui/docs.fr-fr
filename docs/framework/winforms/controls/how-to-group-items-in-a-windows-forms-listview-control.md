---
title: Articles de groupe dans le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141989"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="afb88-102">Comment : grouper des éléments dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="afb88-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="afb88-103">Avec la fonction de <xref:System.Windows.Forms.ListView> regroupement du contrôle, vous pouvez afficher des ensembles d’éléments connexes en groupes.</span><span class="sxs-lookup"><span data-stu-id="afb88-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="afb88-104">Ces groupes sont séparés à l’écran par des en-têtes de groupe horizontaux qui contiennent les titres de groupe.</span><span class="sxs-lookup"><span data-stu-id="afb88-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="afb88-105">Vous pouvez <xref:System.Windows.Forms.ListView> utiliser des groupes pour faciliter la navigation sur de grandes listes en groupant les éléments par ordre alphabétique, par date ou par tout autre groupement logique.</span><span class="sxs-lookup"><span data-stu-id="afb88-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="afb88-106">L’image suivante montre certains éléments groupés.</span><span class="sxs-lookup"><span data-stu-id="afb88-106">The following image shows some grouped items.</span></span>  
  
 ![Capture d’écran de groupes ListView impairs et même.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 <span data-ttu-id="afb88-108">Pour permettre le regroupement, vous devez d’abord créer un ou plusieurs groupes soit dans le concepteur ou programmatiquement.</span><span class="sxs-lookup"><span data-stu-id="afb88-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="afb88-109">Une fois qu’un groupe <xref:System.Windows.Forms.ListView> a été défini, vous pouvez attribuer des éléments à des groupes.</span><span class="sxs-lookup"><span data-stu-id="afb88-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="afb88-110">Vous pouvez également déplacer des éléments d’un groupe à un autre programmatiquement.</span><span class="sxs-lookup"><span data-stu-id="afb88-110">You can also move items from one group to another programmatically.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="afb88-111">Pour ajouter des groupes</span><span class="sxs-lookup"><span data-stu-id="afb88-111">To add groups</span></span>  
  
1. <span data-ttu-id="afb88-112">Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A> .</span><span class="sxs-lookup"><span data-stu-id="afb88-112">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="afb88-113">Supprimer les groupes</span><span class="sxs-lookup"><span data-stu-id="afb88-113">To remove groups</span></span>  
  
1. <span data-ttu-id="afb88-114">Utilisez <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> la <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode <xref:System.Windows.Forms.ListView.Groups%2A> ou la méthode de la collection.</span><span class="sxs-lookup"><span data-stu-id="afb88-114">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="afb88-115">La <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> méthode supprime un seul groupe; la <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode supprime tous les groupes de la liste.</span><span class="sxs-lookup"><span data-stu-id="afb88-115">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="afb88-116">La suppression d’un groupe ne supprime pas les éléments de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="afb88-116">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="afb88-117">Attribuer des articles à des groupes ou déplacer des éléments entre les groupes</span><span class="sxs-lookup"><span data-stu-id="afb88-117">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="afb88-118">Réglez la <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriété des objets individuels.</span><span class="sxs-lookup"><span data-stu-id="afb88-118">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="afb88-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb88-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="afb88-120">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="afb88-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="afb88-121">Vue d'ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="afb88-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="afb88-122">Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="afb88-122">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
