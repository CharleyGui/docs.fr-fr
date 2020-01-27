---
title: Permettre aux utilisateurs de copier plusieurs cellules dans le presse-papiers à partir du contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: 2bb74a1f0c59b28ab496ce9c89c1c1b5f9d8147b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745781"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Comment : permettre aux utilisateurs de copier plusieurs cellules dans le Presse-papiers à partir du contrôle DataGridView Windows Forms
Quand vous activez la copie des cellules, vous rendez les données de votre contrôle <xref:System.Windows.Forms.DataGridView> facilement accessibles à d'autres applications via le <xref:System.Windows.Forms.Clipboard>. Les valeurs des cellules sélectionnées sont converties en chaînes et ajoutées au Presse-papiers sous forme de texte délimité par des tabulations en vue d'être collées dans des applications, telles que le Bloc-notes et Excel, et sous forme d'un tableau au format HTML en vue d'être collées dans des applications telles que Word.  
  
 Vous pouvez configurer la copie de cellules pour copier uniquement les valeurs des cellules, pour inclure le texte des en-têtes de ligne et de colonne dans les données du Presse-papiers ou pour inclure le texte des en-têtes uniquement quand les utilisateurs sélectionnent des lignes et des colonnes entières.  
  
 Selon le mode de sélection, les utilisateurs peuvent sélectionner plusieurs groupes de cellules non connectés. Quand un utilisateur copie des cellules dans le Presse-papiers, les lignes et les colonnes qui ne contiennent pas de cellules sélectionnées ne sont pas copiées. Toutes les autres lignes ou colonnes deviennent des lignes et des colonnes de la table de données copiée dans le Presse-papiers. Les cellules non sélectionnées de ces lignes ou colonnes sont copiées comme des espaces réservés dans le Presse-papiers.  
  
### <a name="to-enable-cell-copying"></a>Pour activer la copie de cellule  
  
- définir la propriété <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> ;  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code complet suivant montre comment les cellules sont copiées vers le Presse-papiers. Cet exemple inclut un bouton qui copie les cellules sélectionnées dans le Presse-papiers à l'aide de la méthode <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> et affiche le contenu du Presse-papiers dans une zone de texte.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ce code nécessite :  
  
- Des références aux assemblys N:System et N:System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
