---
title: 'Procédure : regrouper des éléments dans un contrôle ListView Windows Forms'
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
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966629"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="3489e-102">Procédure : regrouper des éléments dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3489e-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="3489e-103">Avec la fonctionnalité de regroupement du <xref:System.Windows.Forms.ListView> contrôle, vous pouvez afficher des jeux d’éléments associés dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="3489e-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="3489e-104">Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontaux qui contiennent les titres des groupes.</span><span class="sxs-lookup"><span data-stu-id="3489e-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="3489e-105">Vous pouvez utiliser <xref:System.Windows.Forms.ListView> des groupes pour faciliter la navigation dans des listes volumineuses en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique.</span><span class="sxs-lookup"><span data-stu-id="3489e-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="3489e-106">L’illustration suivante montre des éléments groupés.</span><span class="sxs-lookup"><span data-stu-id="3489e-106">The following image shows some grouped items.</span></span>  
  
 ![Capture d’écran des groupes de ListView impaires et pairs.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 <span data-ttu-id="3489e-108">Pour activer le regroupement, vous devez d’abord créer un ou plusieurs groupes dans le concepteur ou par programme.</span><span class="sxs-lookup"><span data-stu-id="3489e-108">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="3489e-109">Une fois qu’un groupe a été défini, vous <xref:System.Windows.Forms.ListView> pouvez assigner des éléments à des groupes.</span><span class="sxs-lookup"><span data-stu-id="3489e-109">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="3489e-110">Vous pouvez également déplacer des éléments d’un groupe à un autre par programmation.</span><span class="sxs-lookup"><span data-stu-id="3489e-110">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3489e-111"><xref:System.Windows.Forms.ListView>les groupes sont disponibles uniquement [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] sur lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> la méthode.</span><span class="sxs-lookup"><span data-stu-id="3489e-111"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3489e-112">Sur les systèmes d’exploitation antérieurs, tout code relatif aux groupes n’a aucun effet et les groupes n’apparaissent pas.</span><span class="sxs-lookup"><span data-stu-id="3489e-112">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="3489e-113">Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3489e-113">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="3489e-114">Pour ajouter des groupes</span><span class="sxs-lookup"><span data-stu-id="3489e-114">To add groups</span></span>  
  
1. <span data-ttu-id="3489e-115">Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A> .</span><span class="sxs-lookup"><span data-stu-id="3489e-115">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="3489e-116">Pour supprimer des groupes</span><span class="sxs-lookup"><span data-stu-id="3489e-116">To remove groups</span></span>  
  
1. <span data-ttu-id="3489e-117">Utilisez la <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> méthode <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> ou de la <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="3489e-117">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="3489e-118">La <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> méthode supprime un seul groupe; la <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode supprime tous les groupes de la liste.</span><span class="sxs-lookup"><span data-stu-id="3489e-118">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3489e-119">La suppression d’un groupe ne supprime pas les éléments de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="3489e-119">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="3489e-120">Pour affecter des éléments à des groupes ou déplacer des éléments entre des groupes</span><span class="sxs-lookup"><span data-stu-id="3489e-120">To assign items to groups or move items between groups</span></span>  
  
1. <span data-ttu-id="3489e-121">Définissez la <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriété des éléments individuels.</span><span class="sxs-lookup"><span data-stu-id="3489e-121">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="3489e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3489e-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [<span data-ttu-id="3489e-123">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="3489e-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="3489e-124">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="3489e-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="3489e-125">Guide pratique pour Ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3489e-125">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
