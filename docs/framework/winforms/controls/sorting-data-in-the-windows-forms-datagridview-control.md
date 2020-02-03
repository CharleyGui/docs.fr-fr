---
title: Tri des données dans le contrôle DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742946"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>Tri des données dans le contrôle DataGridView Windows Forms

Par défaut, les utilisateurs peuvent trier les données d’un contrôle <xref:System.Windows.Forms.DataGridView> en cliquant sur l’en-tête d’une colonne de zone de texte (ou en appuyant sur F3 quand une cellule de zone de texte est axée sur .NET Framework 4.7.2 et versions ultérieures). Vous pouvez modifier la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode> de colonnes spécifiques pour permettre aux utilisateurs de trier par d’autres types de colonnes lorsqu’il est logique de le faire. Vous pouvez également trier les données par programmation par n’importe quelle colonne ou par plusieurs colonnes.

## <a name="in-this-section"></a>Contenu de cette section

[Modes de tri des colonnes du contrôle DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
Décrit les options de tri des données dans le contrôle.

[Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
Décrit comment permettre aux utilisateurs de trier par par défaut des colonnes qui ne peuvent pas être triées.

[Guide pratique pour personnaliser le tri dans le contrôle DataGridView Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
Décrit comment trier des données par programmation et comment personnaliser le tri à l’aide de l’événement <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> ou en implémentant l’interface <xref:System.Collections.IComparer>.

## <a name="reference"></a>Référence

<xref:System.Windows.Forms.DataGridView>  
Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
Fournit une documentation de référence pour la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>.

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>.

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
Fournit une documentation de référence pour l’énumération <xref:System.Windows.Forms.DataGridViewColumnSortMode>.

## <a name="see-also"></a>Voir aussi

- [DataGridView, contrôle](datagridview-control-windows-forms.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
