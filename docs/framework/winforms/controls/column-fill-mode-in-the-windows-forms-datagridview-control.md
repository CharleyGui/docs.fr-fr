---
title: Mode de remplissage de colonne dans le contrôle DataGridView
description: Découvrez comment le contrôle DataGridView Windows Forms en mode de remplissage de colonne redimensionne automatiquement ses colonnes pour qu’elles remplissent la largeur de la zone d’affichage disponible.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: 766a58954250d78ce6e44404730332b3158e1fad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622820"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms
En mode de remplissage de colonne, le contrôle <xref:System.Windows.Forms.DataGridView> redimensionne automatiquement ses colonnes pour qu'elles remplissent la largeur de la zone d'affichage disponible. Le contrôle n'affiche pas de barre de défilement horizontale, sauf quand cela est nécessaire pour faire en sorte que la largeur de chaque colonne soit supérieure ou égale à la valeur de sa propriété <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
 Le comportement de dimensionnement de chaque colonne dépend de sa propriété <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>. La valeur de cette propriété est héritée de la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> de la colonne ou de la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> du contrôle si la valeur de la colonne est <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (valeur par défaut).  
  
 Chaque colonne peut avoir un mode de taille différent, mais toutes les colonnes ayant le mode de taille <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> partagent la largeur de la zone d'affichage qui n'est pas utilisée par les autres colonnes. Cette largeur est divisée entre les colonnes en mode de remplissage dans des proportions relatives à leurs valeurs de propriété <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>. Par exemple, si deux colonnes ont des valeurs de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> égales à 100 et 200, la première colonne sera moitié moins large que la deuxième colonne.  
  
## <a name="user-resizing-in-fill-mode"></a>Redimensionnement par l'utilisateur en mode de remplissage  
 Contrairement aux modes de dimensionnement qui redimensionnement en fonction du contenu de la cellule, le mode de remplissage n'empêche pas les utilisateurs de redimensionner les colonnes qui ont des valeurs de propriété <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> égales à `true`. Quand un utilisateur redimensionne une colonne en mode de remplissage, toutes les colonnes en mode de remplissage qui figurent après la colonne redimensionnée (à droite si <xref:System.Windows.Forms.Control.RightToLeft%2A> est `false` ; sinon, à gauche) sont également redimensionnées pour compenser le changement de largeur disponible. S'il n'y a pas de colonne en mode de remplissage après la colonne redimensionnée, toutes les autres colonnes en mode de remplissage dans le contrôle sont redimensionnées pour compenser. S'il n'y a pas d'autre colonne en mode de remplissage dans le contrôle, le redimensionnement est ignoré. Si une colonne qui n'est pas en mode de remplissage est redimensionnée, toutes les colonnes en mode de remplissage dans le contrôle changent de taille pour compenser.  
  
 Après le redimensionnement d'une colonne en mode de remplissage, les valeurs <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> de toutes les colonnes qui ont changé sont ajustées proportionnellement. Par exemple, si quatre colonnes en mode de remplissage ont des valeurs de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> égales à 100 et que vous redimensionnez la deuxième colonne à la moitié de sa largeur d'origine, les valeurs de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> seront 100, 50, 125 et 125. Le fait de redimensionner une colonne qui n'est pas en mode de remplissage ne change pas les valeurs de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, car les colonnes en mode de remplissage seront simplement redimensionnées tout en conservant les mêmes proportions.  
  
## <a name="content-based-fillweight-adjustment"></a>Réglage de FillWeight basé sur le contenu  
 Vous pouvez initialiser les valeurs de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> pour les colonnes en mode de remplissage à l'aide des méthodes de redimensionnement automatique de <xref:System.Windows.Forms.DataGridView>, telles que la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>. Cette méthode calcule d'abord les largeurs nécessaires pour que les colonnes affichent leur contenu. Ensuite, le contrôle ajuste les valeurs de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> pour toutes les colonnes en mode de remplissage pour que leurs proportions correspondent à celles des largeurs calculées. Pour finir, le contrôle redimensionne les colonnes en mode de remplissage à l'aide des nouvelles proportions de <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> pour que toutes les colonnes du contrôle remplissent l'espace horizontal disponible.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 En affectant des valeurs appropriées aux propriétés <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> et <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>, vous pouvez personnaliser le comportement de dimensionnement des colonnes dans de nombreux scénarios.  
  
 Le code de démonstration suivant vous permet d'expérimenter avec différentes valeurs pour les propriétés <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> et <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> de différentes colonnes. Dans cet exemple, un contrôle <xref:System.Windows.Forms.DataGridView> est lié à sa propre collection <xref:System.Windows.Forms.DataGridView.Columns%2A>  et une colonne est liée à chacune des propriétés <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> et <xref:System.Windows.Forms.DataGridViewColumn.Width%2A>. Chacune des colonnes est également représentée par une ligne dans le contrôle et la modification des valeurs sur une ligne met à jour les propriétés de la colonne correspondante pour que vous puissiez voir comment les valeurs interagissent.  
  
### <a name="code"></a>Code  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>Commentaires  
 Pour utiliser cette application de démonstration  
  
- Modifiez la taille du formulaire. Observez comment la largeur des colonnes change tout en conservant les proportions indiquées par les valeurs de propriétés <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.  
  
- Modifiez les tailles des colonnes en faisant glisser les séparateurs de colonnes avec la souris. Observez comment les valeurs <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> changent.  
  
- Modifiez la valeur <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> d'une colonne, puis faites glisser pour redimensionner le formulaire. Observez comment, quand vous affectez au formulaire une taille suffisamment petite, les valeurs de <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> ne vont pas en dessous des valeurs de <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
- Affectez des valeurs <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> élevées pour toutes les colonnes pour que les valeurs combinées dépassent la largeur du contrôle. Observez l'apparition de la barre de défilement horizontale.  
  
- Modifiez les valeurs de <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> de certaines colonnes. Observez l'effet quand vous redimensionnez des colonnes ou le formulaire.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>
- [Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
