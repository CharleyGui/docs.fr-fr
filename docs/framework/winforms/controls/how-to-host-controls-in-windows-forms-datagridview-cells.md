---
title: Contrôles hôtes dans les cellules DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a64521a15a272ca8140302f39d15e7f17e0c423b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736540"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Comment : héberger des contrôles dans des cellules DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs types de colonnes, ce qui permet à vos utilisateurs d'entrer et de modifier des valeurs de plusieurs façons. Toutefois, si ces types de colonnes ne répondent pas à vos besoins de saisie de données, vous pouvez créer vos propres types de colonnes avec des cellules qui hébergent les contrôles de votre choix. Pour cela, vous devez définir des classes qui dérivent de <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewCell>. Vous devez aussi définir une classe qui dérive de <xref:System.Windows.Forms.Control> et implémente l'interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
 L'exemple de code suivant montre comment créer une colonne de calendrier. Les cellules de cette colonne affichent des dates dans des cellules de zone de texte ordinaires, mais quand l'utilisateur modifie une cellule, un contrôle <xref:System.Windows.Forms.DateTimePicker> apparaît. Pour éviter de devoir réimplémenter une fonctionnalité d'affichage de zone de texte, la classe `CalendarCell` dérive de la classe <xref:System.Windows.Forms.DataGridViewTextBoxCell> au lieu d'hériter directement de la classe <xref:System.Windows.Forms.DataGridViewCell>.  
  
> [!NOTE]
> Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage. Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple suivant nécessite :  
  
- des références aux assemblys System et System.Windows.Forms ;  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Architecture du contrôle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
