---
title: Afficher des images dans les cellules du contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740277"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Comment : afficher des images dans les cellules du contrôle DataGridView Windows Forms
Une image ou un graphique est l’une des valeurs que vous pouvez afficher dans une ligne de données. Souvent, ces graphiques prennent la forme de la photographie d’un employé ou d’un logo d’entreprise.  
  
 L’incorporation d’images est simple lorsque vous affichez des données dans le contrôle <xref:System.Windows.Forms.DataGridView>. Le contrôle <xref:System.Windows.Forms.DataGridView> gère en mode natif tout format d’image pris en charge par la classe <xref:System.Drawing.Image>, ainsi que le format d’image OLE utilisé par certaines bases de données.  
  
 Si la source de données du contrôle <xref:System.Windows.Forms.DataGridView> possède une colonne d’images, elles sont automatiquement affichées par le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 L’exemple de code suivant montre comment extraire une icône d’une ressource incorporée et la convertir en bitmap pour l’afficher dans chaque cellule d’une colonne d’image. Pour obtenir un autre exemple qui remplace les valeurs de cellules textuelles par les images correspondantes, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- Une ressource icône incorporée nommée `tree.ico`.  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Guide pratique pour personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
