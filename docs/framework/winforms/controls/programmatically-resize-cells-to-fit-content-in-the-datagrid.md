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
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a>Comment : redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms
Vous pouvez utiliser les méthodes du contrôle <xref:System.Windows.Forms.DataGridView> pour redimensionner des lignes, des colonnes et des en-têtes pour qu'ils affichent leurs valeurs entières sans coupure. Vous pouvez utiliser ces méthodes pour redimensionner des éléments <xref:System.Windows.Forms.DataGridView> quand bon vous semble. En guise d'alternative, vous pouvez configurer le contrôle pour redimensionner automatiquement ces éléments chaque fois que le contenu est modifié. Toutefois, cette opération peut être inefficace quand vous travaillez avec grands jeux de données ou quand vos données changent fréquemment. Pour plus d’informations, consultez [options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 En général, vous ajustez par programmation les éléments <xref:System.Windows.Forms.DataGridView> en fonction de leur contenu uniquement quand vous chargez de nouvelles données à partir d'une source de données ou quand l'utilisateur a modifié une valeur. Cela est utile pour optimiser les performances, mais aussi quand vous souhaitez permettre aux utilisateurs de redimensionner manuellement des lignes et des colonnes avec la souris.  
  
 L'exemple de code suivant illustre les options disponibles pour le redimensionnement par programmation.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

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
- [Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
