---
title: Spécifier le mode d’édition pour le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743765"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Comment : spécifier le mode édition pour le contrôle DataGridView Windows Forms
Par défaut, les utilisateurs peuvent modifier le contenu de la cellule de zone de texte <xref:System.Windows.Forms.DataGridView> en cours en le tapant ou en appuyant sur F2. Cette commande met la cellule en mode édition si toutes les conditions suivantes sont remplies :  
  
- La source de données sous-jacente prend en charge la modification.  
  
- Le contrôle <xref:System.Windows.Forms.DataGridView> est activé.  
  
- La valeur de la propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A> n’est pas <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
- Les propriétés `ReadOnly` de la cellule, de la ligne, de la colonne et du contrôle ont toutes la valeur `false`.  
  
 En mode édition, l’utilisateur peut modifier la valeur de la cellule et appuyer sur entrée pour valider la modification ou sur ÉCHAP pour rétablir la valeur d’origine de la cellule.  
  
 Vous pouvez configurer un contrôle de <xref:System.Windows.Forms.DataGridView> afin qu’une cellule passe en mode édition dès qu’elle devient la cellule active. Le comportement des touches entrée et Échap est inchangé dans ce cas, mais la cellule reste en mode édition après que la valeur a été validée ou annulée. Vous pouvez également configurer le contrôle afin que les cellules entrent en mode édition uniquement lorsque les utilisateurs tapent dans la cellule ou uniquement quand les utilisateurs appuient sur F2. Enfin, vous pouvez empêcher les cellules d’entrer en mode édition, sauf lorsque vous appelez la méthode <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Pour modifier le mode d’édition d’un contrôle DataGridView  
  
- Affectez à la propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> l’énumération <xref:System.Windows.Forms.DataGridViewEditMode> appropriée.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System> et <xref:System.Windows.Forms>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
