---
title: Désactiver les boutons dans une colonne de bouton dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 691781a43005d66e13029ab8110eb7f9daacc35f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745948"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Comment : désactiver des boutons d'une colonne de boutons dans le contrôle DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> inclut la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour l'affichage des cellules avec une interface utilisateur telle qu'un bouton. Toutefois, <xref:System.Windows.Forms.DataGridViewButtonCell> ne permet pas de désactiver l'apparence du bouton affiché par la cellule.  
  
 L'exemple de code suivant montre comment personnaliser la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour afficher des boutons qui peuvent apparaître désactivés. L'exemple définit un nouveau type de cellule, `DataGridViewDisableButtonCell`, qui dérive de <xref:System.Windows.Forms.DataGridViewButtonCell>. Ce type de cellule fournit une nouvelle propriété `Enabled` qui peut prendre la valeur `false` pour dessiner un bouton désactivé dans la cellule. L'exemple définit également un nouveau type de colonne, `DataGridViewDisableButtonColumn`, qui affiche des objets `DataGridViewDisableButtonCell`. Pour illustrer ce nouveau type de cellule et de colonne, la valeur actuelle de chaque <xref:System.Windows.Forms.DataGridViewCheckBoxCell> dans le <xref:System.Windows.Forms.DataGridView> parent détermine si la propriété  `Enabled` du `DataGridViewDisableButtonCell` sur la même ligne est `true` ou `false`.  
  
> [!NOTE]
> Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage. Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Drawing, System.Windows.Forms et System.Windows.Forms.VisualStyles.  
  
## <a name="see-also"></a>Voir aussi

- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Architecture du contrôle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
