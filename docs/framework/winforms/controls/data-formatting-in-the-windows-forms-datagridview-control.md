---
title: Mise en forme des données dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: a041bcc5e1b65afb3123f1f42e0f1b5a479b5764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743983"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Mise en forme de données dans le contrôle DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> fournit une conversion automatique entre les valeurs de cellule et les types de données affichés par les colonnes parentes. Les colonnes de zone de texte, par exemple, affichent des représentations sous forme de chaîne de valeurs de date, d’heure, de nombre et d’énumération, et convertissent les valeurs de chaîne entrées par l’utilisateur en types requis par le magasin de données.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Mise en forme avec la classe DataGridViewCellStyle  
 Le contrôle <xref:System.Windows.Forms.DataGridView> fournit la mise en forme des données de base des valeurs de cellule par le biais de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>. Vous pouvez utiliser la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> pour mettre en forme les valeurs de date, d’heure, de nombre et d’énumération pour la culture par défaut actuelle à l’aide des spécificateurs de format décrits dans [types de mise en forme](../../../standard/base-types/formatting-types.md). Vous pouvez également mettre en forme ces valeurs pour des cultures spécifiques à l’aide de la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>. Le format spécifié est utilisé à la fois pour afficher les données et pour analyser les données que l’utilisateur entre dans le format spécifié.  
  
 La classe <xref:System.Windows.Forms.DataGridViewCellStyle> fournit des propriétés de mise en forme supplémentaires pour la WordWrap, l’alignement du texte et l’affichage personnalisé des valeurs de base de données null. Pour plus d’informations, consultez [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Mise en forme avec l’événement CellFormatting  
 Si la mise en forme de base ne répond pas à vos besoins, vous pouvez fournir une mise en forme de données personnalisée dans un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. L' <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passé au gestionnaire a une propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> qui contient initialement la valeur de la cellule. Normalement, cette valeur est automatiquement convertie en type d’affichage. Pour convertir la valeur vous-même, affectez à la propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> la valeur du type d’affichage.  
  
> [!NOTE]
> Si une chaîne de format est en vigueur pour la cellule, elle remplace la modification de la valeur de la propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A>, sauf si vous affectez à la propriété <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> la valeur `true`.  
  
 L’événement <xref:System.Windows.Forms.DataGridView.CellFormatting> est également utile lorsque vous souhaitez définir des propriétés <xref:System.Windows.Forms.DataGridViewCellStyle> pour des cellules individuelles en fonction de leurs valeurs. Pour plus d’informations, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Si l’analyse par défaut des valeurs spécifiées par l’utilisateur ne répond pas à vos besoins, vous pouvez gérer l’événement <xref:System.Windows.Forms.DataGridView.CellParsing> du contrôle <xref:System.Windows.Forms.DataGridView> pour fournir une analyse personnalisée.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour mettre en forme des données dans le contrôle DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
