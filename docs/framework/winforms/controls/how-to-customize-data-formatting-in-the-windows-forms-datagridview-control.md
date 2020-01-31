---
title: Personnaliser la mise en forme des données dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 6bc1a65b876df842df322db165dc08fcc0c931dc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746779"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3cbc2-102">Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cbc2-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3cbc2-103">L'exemple de code suivant montre comment implémenter un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> qui modifie le mode d'affichage des cellules en fonction de leurs colonnes et de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="3cbc2-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="3cbc2-104">Les cellules de la colonne `Balance` qui contiennent des nombres négatifs ont un arrière-plan rouge.</span><span class="sxs-lookup"><span data-stu-id="3cbc2-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="3cbc2-105">Vous pouvez également appliquer la mise en forme « Monnaie » à ces cellules pour afficher les valeurs négatives entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="3cbc2-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="3cbc2-106">Pour plus d’informations, consultez [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3cbc2-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="3cbc2-107">Les cellules de la colonne `Priority` affichent des images au lieu des valeurs de cellules textuelles correspondantes.</span><span class="sxs-lookup"><span data-stu-id="3cbc2-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="3cbc2-108">La propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> de <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> sert à obtenir la valeur de la cellule textuelle et à définir la valeur d'affichage d'image correspondante.</span><span class="sxs-lookup"><span data-stu-id="3cbc2-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cbc2-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cbc2-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cbc2-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3cbc2-110">Compiling the Code</span></span>  
 <span data-ttu-id="3cbc2-111">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3cbc2-111">This example requires:</span></span>  
  
- <span data-ttu-id="3cbc2-112">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3cbc2-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="3cbc2-113">des images <xref:System.Drawing.Bitmap> nommées `highPri.bmp`, `mediumPri.bmp` et `lowPri.bmp` résidant dans le même répertoire que le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="3cbc2-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbc2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cbc2-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="3cbc2-115">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cbc2-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3cbc2-116">Guide pratique pour mettre en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cbc2-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3cbc2-117">Styles de cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cbc2-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3cbc2-118">Mise en forme de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cbc2-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
