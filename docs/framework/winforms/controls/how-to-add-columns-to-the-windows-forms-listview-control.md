---
title: Ajouter des colonnes au contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: dd438ffbadddfc37ec9eb15e59a908bb58472a45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744586"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="b9118-102">Comment : ajouter des colonnes au contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9118-102">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="b9118-103">Dans le mode Détails, le contrôle <xref:System.Windows.Forms.ListView> peut afficher plusieurs colonnes pour chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="b9118-103">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="b9118-104">Vous pouvez utiliser les colonnes pour afficher à l’utilisateur plusieurs types d’informations sur chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="b9118-104">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="b9118-105">Par exemple, une liste de fichiers peut afficher le nom du fichier, le type de fichier, la taille et la date de la dernière modification du fichier.</span><span class="sxs-lookup"><span data-stu-id="b9118-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="b9118-106">Pour plus d’informations sur le remplissage des colonnes après leur création, consultez [Comment : afficher des sous-éléments dans des colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b9118-106">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="b9118-107">Pour ajouter des colonnes par programmation</span><span class="sxs-lookup"><span data-stu-id="b9118-107">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="b9118-108">Affectez à la propriété <xref:System.Windows.Forms.ListView.View%2A> du contrôle la valeur <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="b9118-108">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="b9118-109">Utilisez la méthode <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ListView.Columns%2A> de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="b9118-109">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="b9118-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9118-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="b9118-111">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b9118-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="b9118-112">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b9118-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
