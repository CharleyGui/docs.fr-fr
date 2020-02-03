---
title: Définir les modes de redimensionnement du contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738392"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Comment : définir les modes de redimensionnement du contrôle DataGridView Windows Forms
Les procédures suivantes montrent des scénarios courants de personnalisation et de combinaison des options de dimensionnement disponibles pour le contrôle <xref:System.Windows.Forms.DataGridView> et pour certaines colonnes des contrôles.  
  
### <a name="to-create-a-fixed-width-column"></a>Pour créer une colonne de largeur fixe  
  
- Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, la propriété <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> sur <xref:System.Windows.Forms.DataGridViewTriState.False>, la propriété <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> sur `true`, et la propriété <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> sur une valeur appropriée.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Pour créer une colonne dont la taille s'ajuste au contenu  
  
- Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> sur un mode de dimensionnement basé sur le contenu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Pour créer des colonnes avec mode de remplissage pour les valeurs de taille et d'importance variables  
  
- Définissez la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> sur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> pour définir le mode de dimensionnement de toutes les colonnes qui ne substituent pas cette valeur. Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> des colonnes sur des valeurs qui soient proportionnelles à leur largeur moyenne de contenu. Définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> des colonnes importantes pour garantir un affichage partiel du contenu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code complet suivant est une démonstration d'application qui peut vous aider à comprendre les options de dimensionnement décrites dans cette rubrique.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Pour utiliser cette démonstration d'application :  
  
- Modifiez la taille du formulaire. Observez comment les colonnes avec mode de remplissage changent tout en conservant les proportions indiquées par les valeurs de propriétés <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>. Observez comment la <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> d'une colonne empêche celle-ci de changer quand le formulaire est trop petit.  
  
- Modifiez les tailles des colonnes en faisant glisser les séparateurs de colonnes avec la souris. Observez comment certaines colonnes ne peuvent pas être redimensionnées et comment les colonnes redimensionnables ne peuvent pas devenir plus étroites que leur largeur minimale.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
