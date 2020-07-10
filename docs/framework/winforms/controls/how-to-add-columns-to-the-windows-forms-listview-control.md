---
title: Ajouter des colonnes au contrôle ListView
description: Découvrez comment ajouter des colonnes au contrôle ListView Windows Forms pour afficher plusieurs types d’informations sur chaque élément de liste.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174560"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="c7035-103">Comment : ajouter des colonnes au contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7035-103">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="c7035-104">Dans le mode Détails, le <xref:System.Windows.Forms.ListView> contrôle peut afficher plusieurs colonnes pour chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="c7035-104">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="c7035-105">Vous pouvez utiliser les colonnes pour afficher à l’utilisateur plusieurs types d’informations sur chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="c7035-105">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="c7035-106">Par exemple, une liste de fichiers peut afficher le nom du fichier, le type de fichier, la taille et la date de la dernière modification du fichier.</span><span class="sxs-lookup"><span data-stu-id="c7035-106">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="c7035-107">Pour plus d’informations sur le remplissage des colonnes après leur création, consultez [Comment : afficher des sous-éléments dans des colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c7035-107">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="c7035-108">Pour ajouter des colonnes par programmation</span><span class="sxs-lookup"><span data-stu-id="c7035-108">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="c7035-109">Affectez à la propriété du contrôle la valeur <xref:System.Windows.Forms.ListView.View%2A> <xref:System.Windows.Forms.View.Details> .</span><span class="sxs-lookup"><span data-stu-id="c7035-109">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="c7035-110">Utilisez la <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> méthode de la propriété de la vue liste <xref:System.Windows.Forms.ListView.Columns%2A> .</span><span class="sxs-lookup"><span data-stu-id="c7035-110">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="c7035-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7035-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="c7035-112">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="c7035-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="c7035-113">Vue d'ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="c7035-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
