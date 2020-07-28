---
title: 'Procédure : implémenter la validation avec le contrôle DataGrid'
description: Découvrez comment le contrôle DataGrid Windows Presentation Foundation peut effectuer une validation à la fois au niveau de la cellule et de la ligne et fournir des commentaires pour les erreurs de validation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: a6fe3693f94c3f554e96bc167b572cf854a1a34a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167603"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Procédure : implémenter la validation avec le contrôle DataGrid
Le <xref:System.Windows.Controls.DataGrid> contrôle vous permet d’effectuer une validation à la fois au niveau de la cellule et de la ligne. Avec la validation au niveau de la cellule, vous validez les propriétés individuelles d’un objet de données liées lorsqu’un utilisateur met à jour une valeur. Avec la validation au niveau des lignes, vous validez des objets de données entiers lorsqu’un utilisateur valide les modifications apportées à une ligne. Vous pouvez également fournir des commentaires visuels personnalisés pour les erreurs de validation, ou utiliser les commentaires visuels par défaut fournis par le <xref:System.Windows.Controls.DataGrid> contrôle.  
  
 Les procédures suivantes décrivent comment appliquer des règles de validation aux <xref:System.Windows.Controls.DataGrid> liaisons et comment personnaliser les commentaires visuels.  
  
### <a name="to-validate-individual-cell-values"></a>Pour valider des valeurs de cellules individuelles  
  
- Spécifiez une ou plusieurs règles de validation sur la liaison utilisée avec une colonne. Cela est similaire à la validation des données dans des contrôles simples, comme décrit dans [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.  
  
     L’exemple suivant montre un <xref:System.Windows.Controls.DataGrid> contrôle avec quatre colonnes liées à différentes propriétés d’un objet métier. Trois des colonnes spécifient le <xref:System.Windows.Controls.ExceptionValidationRule> en affectant <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> à la propriété la valeur `true` .  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Lorsqu’un utilisateur entre une valeur non valide (comme un entier non entier dans la colonne ID de cours), une bordure rouge apparaît autour de la cellule. Vous pouvez modifier ces commentaires de validation par défaut comme décrit dans la procédure suivante.  
  
### <a name="to-customize-cell-validation-feedback"></a>Pour personnaliser les commentaires sur la validation des cellules  
  
- Affectez à la propriété de la colonne <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> un style approprié pour le contrôle d’édition de la colonne. Étant donné que les contrôles d’édition sont créés au moment de l’exécution, vous ne pouvez pas utiliser la <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> propriété jointe comme vous le feriez avec des contrôles simples.  
  
     L’exemple suivant met à jour l’exemple précédent en ajoutant un style d’erreur partagé par les trois colonnes avec des règles de validation. Quand un utilisateur entre une valeur non valide, le style modifie la couleur d’arrière-plan de la cellule et ajoute une info-bulle. Notez l’utilisation d’un déclencheur pour déterminer s’il existe une erreur de validation. Cela est nécessaire, car il n’existe actuellement aucun modèle d’erreur dédié pour les cellules.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Vous pouvez implémenter une personnalisation plus poussée en remplaçant le <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> utilisé par la colonne.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Pour valider plusieurs valeurs sur une seule ligne  
  
1. Implémentez une <xref:System.Windows.Controls.ValidationRule> sous-classe qui vérifie plusieurs propriétés de l’objet de données lié. Dans votre <xref:System.Windows.Controls.ValidationRule.Validate%2A> implémentation de méthode, effectuez un cast de la `value` valeur de paramètre en une <xref:System.Windows.Data.BindingGroup> instance. Vous pouvez ensuite accéder à l’objet de données via la <xref:System.Windows.Data.BindingGroup.Items%2A> propriété.  
  
     L’exemple suivant illustre ce processus pour valider si la `StartDate` valeur de propriété d’un `Course` objet est antérieure à sa `EndDate` valeur de propriété.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Ajoutez la règle de validation à la <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection. La <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriété fournit un accès direct à la <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> propriété d’une <xref:System.Windows.Data.BindingGroup> instance de qui regroupe toutes les liaisons utilisées par le contrôle.  
  
     L’exemple suivant définit la <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriété en XAML. La <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> propriété a la valeur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> afin que la validation se produise uniquement après la mise à jour de l’objet de données liées.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Lorsqu’un utilisateur spécifie une date de fin antérieure à la date de début, un point d’exclamation rouge ( !) apparaît dans l’en-tête de ligne. Vous pouvez modifier ces commentaires de validation par défaut comme décrit dans la procédure suivante.  
  
### <a name="to-customize-row-validation-feedback"></a>Pour personnaliser les commentaires de validation de ligne  
  
- définir la propriété <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> ; Cette propriété vous permet de personnaliser les commentaires de validation de ligne pour les <xref:System.Windows.Controls.DataGrid> contrôles individuels. Vous pouvez également affecter plusieurs contrôles à l’aide d’un style de ligne implicite pour définir la <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> propriété.  
  
     L’exemple suivant remplace les commentaires de validation de ligne par défaut par un indicateur plus visible. Lorsqu’un utilisateur entre une valeur non valide, un cercle rouge avec un point d’exclamation blanc s’affiche dans l’en-tête de ligne. Cela se produit pour les erreurs de validation des lignes et des cellules. Le message d’erreur associé s’affiche dans une info-bulle.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant fournit une démonstration complète de la validation de cellule et de ligne. La `Course` classe fournit un exemple d’objet de données qui implémente <xref:System.ComponentModel.IEditableObject> pour prendre en charge les transactions. Le <xref:System.Windows.Controls.DataGrid> contrôle interagit avec <xref:System.ComponentModel.IEditableObject> pour permettre aux utilisateurs de rétablir les modifications en appuyant sur ÉCHAP.  
  
> [!NOTE]
> Si vous utilisez Visual Basic, dans la première ligne de MainWindow. xaml, remplacez `x:Class="DataGridValidation.MainWindow"` par `x:Class="MainWindow"` .  
  
 Pour tester la validation, essayez ce qui suit :  
  
- Dans la colonne ID du cours, entrez une valeur non entière.  
  
- Dans la colonne Date de fin, entrez une date antérieure à la date de début.  
  
- Supprimez la valeur de l’ID du cours, de la date de début ou de la date de fin.  
  
- Pour annuler une valeur de cellule non valide, replacez le curseur dans la cellule et appuyez sur la touche ÉCHAP.  
  
- Pour annuler les modifications apportées à une ligne entière lorsque la cellule active est en mode édition, appuyez deux fois sur la touche ÉCHAP.  
  
- Lorsqu’une erreur de validation se produit, placez le pointeur de la souris sur l’indicateur dans l’en-tête de ligne pour afficher le message d’erreur associé.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Implémenter la validation de liaison](../data/how-to-implement-binding-validation.md)
- [Implémenter une logique de validation sur des objets personnalisés](../data/how-to-implement-validation-logic-on-custom-objects.md)
