---
title: Utiliser le modèle de ligne pour personnaliser les lignes dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728383"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Comment : utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> utilise le modèle de ligne comme base pour toutes les lignes qu’il ajoute au contrôle via une liaison de données ou lorsque vous appelez la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> sans spécifier de ligne existante à utiliser.  
  
 Le modèle de ligne vous donne un meilleur contrôle sur l’apparence et le comportement des lignes que la propriété <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> fournit. Avec le modèle de ligne, vous pouvez définir toutes les propriétés de <xref:System.Windows.Forms.DataGridViewRow>, y compris les <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Dans certains cas, vous devez utiliser le modèle de ligne pour obtenir un effet particulier. Par exemple, les informations de hauteur de ligne ne peuvent pas être stockées dans un <xref:System.Windows.Forms.DataGridViewCellStyle>. vous devez donc utiliser un modèle de ligne pour modifier la hauteur par défaut utilisée par toutes les lignes. Le modèle de ligne est également utile lorsque vous créez vos propres classes dérivées de <xref:System.Windows.Forms.DataGridViewRow> et que vous souhaitez que votre type personnalisé soit utilisé lorsque de nouvelles lignes sont ajoutées au contrôle.  
  
> [!NOTE]
> Le modèle de ligne est utilisé uniquement lors de l’ajout de lignes. Vous ne pouvez pas modifier les lignes existantes en modifiant le modèle de ligne.  
  
### <a name="to-use-the-row-template"></a>Pour utiliser le modèle de ligne  
  
- Définissez les propriétés de l’objet récupéré à partir de la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
