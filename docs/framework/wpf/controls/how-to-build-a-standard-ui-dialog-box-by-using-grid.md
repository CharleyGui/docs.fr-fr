---
title: 'Procédure : Générer une boîte de dialogue d’interface utilisateur standard à l’aide d’une grille'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923422"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="7a932-102">Procédure : Générer une boîte de dialogue d’interface utilisateur standard à l’aide d’une grille</span><span class="sxs-lookup"><span data-stu-id="7a932-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="7a932-103">Cet exemple montre comment créer une boîte de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogue standard à l’aide <xref:System.Windows.Controls.Grid> de l’élément.</span><span class="sxs-lookup"><span data-stu-id="7a932-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a932-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a932-104">Example</span></span>  
 <span data-ttu-id="7a932-105">L’exemple suivant crée une boîte de dialogue telle que la boîte de dialogue **exécuter** dans le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="7a932-105">The following example creates a dialog box like the **Run** dialog box in the Windows operating system.</span></span>  
  
 <span data-ttu-id="7a932-106">L’exemple crée un <xref:System.Windows.Controls.Grid> et utilise les <xref:System.Windows.Controls.ColumnDefinition> classes <xref:System.Windows.Controls.RowDefinition> et pour définir cinq colonnes et quatre lignes.</span><span class="sxs-lookup"><span data-stu-id="7a932-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="7a932-107">L’exemple ajoute et positionne ensuite un <xref:System.Windows.Controls.Image>, `RunIcon.png`, pour représenter l’image trouvée dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7a932-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="7a932-108">L’image est placée sur la première colonne et ligne de <xref:System.Windows.Controls.Grid> (l’angle supérieur gauche).</span><span class="sxs-lookup"><span data-stu-id="7a932-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="7a932-109">Ensuite, l’exemple ajoute un <xref:System.Windows.Controls.TextBlock> élément à la première colonne, qui s’étend sur les colonnes restantes de la première ligne.</span><span class="sxs-lookup"><span data-stu-id="7a932-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="7a932-110">Elle ajoute un <xref:System.Windows.Controls.TextBlock> autre élément à la deuxième ligne de la première colonne, pour représenter la zone de texte **ouverte** .</span><span class="sxs-lookup"><span data-stu-id="7a932-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="7a932-111">Le <xref:System.Windows.Controls.TextBlock> suivant, qui représente la zone d’entrée de données.</span><span class="sxs-lookup"><span data-stu-id="7a932-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="7a932-112">Enfin, l’exemple ajoute trois <xref:System.Windows.Controls.Button> éléments à la dernière ligne, qui représentent les événements **OK**, **Annuler**et **Parcourir** .</span><span class="sxs-lookup"><span data-stu-id="7a932-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7a932-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a932-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="7a932-114">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="7a932-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="7a932-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="7a932-115">How-to Topics</span></span>](grid-how-to-topics.md)
