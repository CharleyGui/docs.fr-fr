---
title: Mise en forme de données dans le contrôle DataGridView Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 5966f16238999655d6072c1127e5bf16aefde5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969184"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Mise en forme de données dans le contrôle DataGridView Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle assure la conversion automatique entre les valeurs de cellule et les types de données affichés par les colonnes parentes. Les colonnes de zone de texte, par exemple, affichent des représentations sous forme de chaîne de valeurs de date, d’heure, de nombre et d’énumération, et convertissent les valeurs de chaîne entrées par l’utilisateur en types requis par le magasin de données.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Mise en forme avec la classe DataGridViewCellStyle  
 Le <xref:System.Windows.Forms.DataGridView> contrôle fournit la mise en forme des données de base des <xref:System.Windows.Forms.DataGridViewCellStyle> valeurs de cellule par le biais de la classe. Vous pouvez utiliser la <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriété pour mettre en forme les valeurs de date, d’heure, de nombre et d’énumération pour la culture par défaut actuelle à l’aide des spécificateurs de format décrits dans [types de mise en forme](../../../standard/base-types/formatting-types.md). Vous pouvez également mettre en forme ces valeurs pour des cultures <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> spécifiques à l’aide de la propriété. Le format spécifié est utilisé à la fois pour afficher les données et pour analyser les données que l’utilisateur entre dans le format spécifié.  
  
 La <xref:System.Windows.Forms.DataGridViewCellStyle> classe fournit des propriétés de mise en forme supplémentaires pour la WordWrap, l’alignement du texte et l’affichage personnalisé des valeurs de base de données null. Pour plus d’informations, consultez [Guide pratique pour Mettez en forme les données dans le](how-to-format-data-in-the-windows-forms-datagridview-control.md)contrôle DataGridView Windows Forms.  
  
## <a name="formatting-with-the-cellformatting-event"></a>Mise en forme avec l’événement CellFormatting  
 Si la mise en forme de base ne répond pas à vos besoins, vous pouvez fournir une mise en forme de données <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> personnalisée dans un gestionnaire pour l’événement. Le <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passé au gestionnaire a une <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriété qui contient initialement la valeur de la cellule. Normalement, cette valeur est automatiquement convertie en type d’affichage. Pour convertir la valeur vous-même, <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> affectez à la propriété une valeur du type d’affichage.  
  
> [!NOTE]
> Si une chaîne de format est en vigueur pour la cellule, elle remplace la modification de la valeur <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> de la propriété, sauf si <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> vous affectez à `true`la propriété la valeur.  
  
 L' <xref:System.Windows.Forms.DataGridView.CellFormatting> événement est également utile lorsque vous souhaitez définir <xref:System.Windows.Forms.DataGridViewCellStyle> des propriétés pour des cellules individuelles en fonction de leurs valeurs. Pour plus d’informations, consultez [Guide pratique pour Personnaliser la mise en forme des données dans le](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)contrôle DataGridView Windows Forms.  
  
 Si l’analyse par défaut des valeurs spécifiées par l’utilisateur ne répond pas à vos besoins, vous <xref:System.Windows.Forms.DataGridView.CellParsing> pouvez gérer l' <xref:System.Windows.Forms.DataGridView> événement du contrôle pour fournir une analyse personnalisée.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Guide pratique : Mettre en forme les données dans le contrôle DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
