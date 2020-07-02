---
title: Mettre en forme des données dans le contrôle DataGridView
description: Découvrez comment mettre en forme des valeurs de cellule à l’aide de la propriété DefaultCellStyle d’un contrôle DataGridView Windows Forms et de colonnes spécifiques dans un contrôle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622807"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms
Les procédures suivantes illustrent la mise en forme de base des valeurs de cellule à l’aide <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> de la propriété d’un <xref:System.Windows.Forms.DataGridView> contrôle et de colonnes spécifiques dans un contrôle. Pour plus d’informations sur la mise en forme de données avancée, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Pour mettre en forme des valeurs de devise et de date  
  
- Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>. L’exemple de code suivant définit le format des colonnes spécifiques à l’aide <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la propriété des colonnes. Les valeurs de la `UnitPrice` colonne s’affichent dans le format monétaire propre à la culture actuel, avec des valeurs négatives placées entre parenthèses. Les valeurs de la `ShipDate` colonne s’affichent dans le format de date abrégé propre à la culture actuel. Pour plus d’informations sur les <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> valeurs, consultez [mise en forme des types](../../../standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Pour personnaliser l’affichage de valeurs de base de données null  
  
- Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>. L’exemple de code suivant utilise la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriété pour afficher « aucune entrée » dans toutes les cellules contenant des valeurs égales à <xref:System.DBNull.Value?displayProperty=nameWithType> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Pour activer la fonction de retour automatique à la cellule dans des cellules textuelles  
  
- Affectez <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> à la propriété d’un <xref:System.Windows.Forms.DataGridViewCellStyle> la valeur de l’une des <xref:System.Windows.Forms.DataGridViewTriState> valeurs d’énumération. L’exemple de code suivant utilise la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriété pour définir le mode de retour à la ligne pour l’ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>Pour spécifier l’alignement du texte des cellules DataGridView  
  
- Affectez <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> à la propriété d’un <xref:System.Windows.Forms.DataGridViewCellStyle> la valeur de l’une des <xref:System.Windows.Forms.DataGridViewContentAlignment> valeurs d’énumération. L’exemple de code suivant définit l’alignement d’une colonne spécifique à l’aide <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la propriété de la colonne.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ces exemples requièrent les éléments suivants :  
  
- Un <xref:System.Windows.Forms.DataGridView> contrôle nommé `dataGridView1` qui contient une colonne nommée `UnitPrice` , une colonne nommée `ShipDate` et une colonne nommée `CustomerName` .  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Pour une extensibilité maximale, vous devez partager des <xref:System.Windows.Forms.DataGridViewCellStyle> objets sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles plutôt que de définir séparément les propriétés de style de chaque élément. Pour plus d'informations, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Mise en forme de données dans le contrôle DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [Mise en forme des types](../../../standard/base-types/formatting-types.md)
