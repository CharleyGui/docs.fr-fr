---
title: Mise en forme et style de base dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731997"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a>Mises en forme et styles de base dans le contrôle DataGridView Windows Forms
Le contrôle `DataGridView` permet de définir facilement l’apparence de base des cellules et le format d’affichage des valeurs de cellule. Vous pouvez définir l’apparence et les styles de mise en forme pour des cellules individuelles, pour des cellules dans des colonnes et des lignes spécifiques, ou pour toutes les cellules du contrôle en définissant les propriétés des objets `DataGridViewCellStyle` accessibles par le biais de différentes propriétés de contrôle `DataGridView`. En outre, vous pouvez modifier ces styles de manière dynamique en fonction de facteurs tels que la valeur de la cellule en gérant l’événement `CellFormatting`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour modifier les styles de bordures et de quadrillage dans le contrôle DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 Décrit comment définir des propriétés de `DataGridView` qui définissent l’apparence de la bordure du contrôle et les lignes limites entre les cellules.  
  
 [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)  
 Décrit la classe `DataGridViewCellStyle` et la manière dont les propriétés de ce type interagissent pour définir le mode d’affichage des cellules dans le contrôle.  
  
 [Guide pratique pour définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser des propriétés de `DataGridViewCellStyle` pour définir l’apparence par défaut des cellules dans des lignes et des colonnes spécifiques et dans le contrôle entier.  
  
 [Guide pratique pour mettre en forme des données dans le contrôle DataGridView Windows Forms](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 Décrit comment mettre en forme les valeurs d’affichage des cellules à l’aide de `DataGridViewCellStyle` propriétés.  
  
 [Guide pratique pour définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser la propriété `DefaultCellStyle` pour définir les caractéristiques d’affichage de base pour toutes les cellules du contrôle.  
  
 [Guide pratique pour définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 Décrit comment créer un effet de type comptabilité dans le contrôle à l’aide de lignes en alternance qui s’affichent différemment.  
  
 [Guide pratique pour utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 Décrit comment utiliser la propriété `RowTemplate` pour définir les propriétés de ligne qui seront utilisées pour toutes les lignes du contrôle.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 Fournit une documentation de référence pour la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 Fournit une documentation de référence pour l’événement <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.  
  
## <a name="related-sections"></a>Sections connexes  
 [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent la peinture personnalisée des cellules et des lignes <xref:System.Windows.Forms.DataGridView> et la création de types de lignes, de colonnes et de cellules dérivés.  
  
 [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Fournit des rubriques qui décrivent les propriétés de cellule, de ligne et de colonne couramment utilisées.  
  
## <a name="see-also"></a>Voir aussi

- [DataGridView, contrôle](datagridview-control-windows-forms.md)
