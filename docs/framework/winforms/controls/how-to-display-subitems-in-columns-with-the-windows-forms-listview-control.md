---
title: Afficher des sous-éléments en colonnes avec le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745548"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="578b1-102">Comment : afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="578b1-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="578b1-103">Le contrôle Windows Forms <xref:System.Windows.Forms.ListView> peut afficher du texte ou des sous-éléments supplémentaires pour chaque élément en mode Détails.</span><span class="sxs-lookup"><span data-stu-id="578b1-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="578b1-104">La première colonne affiche le texte de l’élément, par exemple un numéro d’employé.</span><span class="sxs-lookup"><span data-stu-id="578b1-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="578b1-105">Les colonnes deuxième, troisième et suivante affichent le premier, le deuxième, et les sous-éléments associés suivants.</span><span class="sxs-lookup"><span data-stu-id="578b1-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="578b1-106">Pour ajouter des sous-éléments à un élément de liste</span><span class="sxs-lookup"><span data-stu-id="578b1-106">To add subitems to a list item</span></span>  
  
1. <span data-ttu-id="578b1-107">Ajoutez toutes les colonnes nécessaires.</span><span class="sxs-lookup"><span data-stu-id="578b1-107">Add any columns needed.</span></span> <span data-ttu-id="578b1-108">Étant donné que la première colonne affiche la propriété de <xref:System.Windows.Forms.ListView.Text%2A> de l’élément, vous avez besoin d’une colonne de plus qu’il n’y a de sous-éléments.</span><span class="sxs-lookup"><span data-stu-id="578b1-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="578b1-109">Pour plus d’informations sur l’ajout de colonnes, consultez [Comment : ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="578b1-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2. <span data-ttu-id="578b1-110">Appelez la méthode <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> de la collection retournée par la propriété <xref:System.Windows.Forms.ListViewItem.SubItems%2A> d’un élément.</span><span class="sxs-lookup"><span data-stu-id="578b1-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="578b1-111">L’exemple de code ci-dessous définit le nom et le département de l’employé pour un élément de liste.</span><span class="sxs-lookup"><span data-stu-id="578b1-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="578b1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="578b1-112">See also</span></span>

- [<span data-ttu-id="578b1-113">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="578b1-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="578b1-114">Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="578b1-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="578b1-115">Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="578b1-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="578b1-116">Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="578b1-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="578b1-117">Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="578b1-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
