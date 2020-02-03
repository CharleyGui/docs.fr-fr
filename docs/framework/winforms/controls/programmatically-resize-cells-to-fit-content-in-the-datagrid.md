---
title: Redimensionner des cellules par programme pour ajuster le contenu dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: df3b378a8ba358fa0bfe549a7901b3d59d53f556
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742451"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2bcd4-102">Comment : redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bcd4-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2bcd4-103">Vous pouvez utiliser les méthodes du contrôle <xref:System.Windows.Forms.DataGridView> pour redimensionner des lignes, des colonnes et des en-têtes pour qu'ils affichent leurs valeurs entières sans coupure.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="2bcd4-104">Vous pouvez utiliser ces méthodes pour redimensionner des éléments <xref:System.Windows.Forms.DataGridView> quand bon vous semble.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="2bcd4-105">En guise d'alternative, vous pouvez configurer le contrôle pour redimensionner automatiquement ces éléments chaque fois que le contenu est modifié.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="2bcd4-106">Toutefois, cette opération peut être inefficace quand vous travaillez avec grands jeux de données ou quand vos données changent fréquemment.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="2bcd4-107">Pour plus d’informations, consultez [options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2bcd4-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="2bcd4-108">En général, vous ajustez par programmation les éléments <xref:System.Windows.Forms.DataGridView> en fonction de leur contenu uniquement quand vous chargez de nouvelles données à partir d'une source de données ou quand l'utilisateur a modifié une valeur.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="2bcd4-109">Cela est utile pour optimiser les performances, mais aussi quand vous souhaitez permettre aux utilisateurs de redimensionner manuellement des lignes et des colonnes avec la souris.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="2bcd4-110">L'exemple de code suivant illustre les options disponibles pour le redimensionnement par programmation.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bcd4-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bcd4-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2bcd4-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2bcd4-112">Compiling the Code</span></span>  
 <span data-ttu-id="2bcd4-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="2bcd4-113">This example requires:</span></span>  
  
- <span data-ttu-id="2bcd4-114">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2bcd4-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcd4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bcd4-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="2bcd4-116">Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bcd4-116">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2bcd4-117">Options de dimensionnement dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bcd4-117">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2bcd4-118">Guide pratique pour redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bcd4-118">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
