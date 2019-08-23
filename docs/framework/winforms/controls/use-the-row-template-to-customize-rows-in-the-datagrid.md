---
title: 'Procédure : utiliser le modèle de ligne pour personnaliser des lignes dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966502"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Procédure : utiliser le modèle de ligne pour personnaliser des lignes dans le contrôle DataGridView Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle utilise le modèle de ligne comme base pour toutes les lignes qu’il ajoute au contrôle via une liaison de données ou lorsque vous appelez <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> la méthode sans spécifier de ligne existante à utiliser.  
  
 Le modèle de ligne vous donne un meilleur contrôle sur l’apparence et le comportement des <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> lignes que la propriété fournit. Avec le modèle de ligne, vous pouvez définir <xref:System.Windows.Forms.DataGridViewRow> toutes les propriétés <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>, y compris.  
  
 Dans certains cas, vous devez utiliser le modèle de ligne pour obtenir un effet particulier. Par exemple, les informations de hauteur de ligne ne peuvent <xref:System.Windows.Forms.DataGridViewCellStyle>pas être stockées dans un. vous devez donc utiliser un modèle de ligne pour modifier la hauteur par défaut utilisée par toutes les lignes. Le modèle de ligne est également utile lorsque vous créez vos propres classes dérivées de <xref:System.Windows.Forms.DataGridViewRow> et que vous souhaitez que votre type personnalisé soit utilisé lorsque de nouvelles lignes sont ajoutées au contrôle.  
  
> [!NOTE]
> Le modèle de ligne est utilisé uniquement lors de l’ajout de lignes. Vous ne pouvez pas modifier les lignes existantes en modifiant le modèle de ligne.  
  
### <a name="to-use-the-row-template"></a>Pour utiliser le modèle de ligne  
  
- Définissez les propriétés sur l’objet récupéré à <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> partir de la propriété.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
