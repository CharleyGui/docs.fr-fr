---
title: Spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742934"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Comment : spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms
Vous pouvez rendre l’entrée de données plus pratique lorsque l’application remplit les valeurs par défaut pour les nouvelles lignes ajoutées. Avec la classe <xref:System.Windows.Forms.DataGridView>, vous pouvez remplir les valeurs par défaut avec l’événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>. Cet événement est déclenché lorsque l’utilisateur entre la ligne pour les nouveaux enregistrements. Lorsque votre code gère cet événement, vous pouvez remplir les cellules souhaitées avec les valeurs de votre choix.  
  
 L’exemple de code suivant montre comment spécifier des valeurs par défaut pour les nouvelles lignes à l’aide de l’événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- Fonction `NewCustomerId` pour générer des valeurs de `CustomerID` uniques.  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
