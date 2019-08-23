---
title: 'Procédure : implémenter la validation avec le contrôle DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 8ae651b3085b39673a51cf8d5f65e9bfb9da87d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962038"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Procédure : implémenter la validation avec le contrôle DataGrid
Le <xref:System.Windows.Controls.DataGrid> contrôle vous permet d’effectuer une validation à la fois au niveau de la cellule et de la ligne. Avec la validation au niveau de la cellule, vous validez les propriétés individuelles d’un objet de données liées lorsqu’un utilisateur met à jour une valeur. Avec la validation au niveau des lignes, vous validez des objets de données entiers lorsqu’un utilisateur valide les modifications apportées à une ligne. Vous pouvez également fournir des commentaires visuels personnalisés pour les erreurs de validation, ou utiliser les commentaires visuels <xref:System.Windows.Controls.DataGrid> par défaut fournis par le contrôle.  
  
 Les procédures suivantes décrivent comment appliquer des règles de <xref:System.Windows.Controls.DataGrid> validation aux liaisons et comment personnaliser les commentaires visuels.  
  
### <a name="to-validate-individual-cell-values"></a>Pour valider des valeurs de cellules individuelles  
  
- Spécifiez une ou plusieurs règles de validation sur la liaison utilisée avec une colonne. Cela est similaire à la validation des données dans des contrôles simples, comme décrit dans [vue d’ensemble](../data/data-binding-overview.md)de la liaison de données.  
  
     L’exemple suivant montre un <xref:System.Windows.Controls.DataGrid> contrôle avec quatre colonnes liées à différentes propriétés d’un objet métier. Trois des colonnes spécifient le <xref:System.Windows.Controls.ExceptionValidationRule> en affectant <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> à `true`la propriété la valeur.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Lorsqu’un utilisateur entre une valeur non valide (comme un entier non entier dans la colonne ID de cours), une bordure rouge apparaît autour de la cellule. Vous pouvez modifier ces commentaires de validation par défaut comme décrit dans la procédure suivante.  
  
### <a name="to-customize-cell-validation-feedback"></a>Pour personnaliser les commentaires sur la validation des cellules  
  
- Affectez à la <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> propriété de la colonne un style approprié pour le contrôle d’édition de la colonne. Étant donné que les contrôles d’édition sont créés au moment de l’exécution <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> , vous ne pouvez pas utiliser la propriété jointe comme vous le feriez avec des contrôles simples.  
  
     L’exemple suivant met à jour l’exemple précédent en ajoutant un style d’erreur partagé par les trois colonnes avec des règles de validation. Quand un utilisateur entre une valeur non valide, le style modifie la couleur d’arrière-plan de la cellule et ajoute une info-bulle. Notez l’utilisation d’un déclencheur pour déterminer s’il existe une erreur de validation. Cela est nécessaire, car il n’existe actuellement aucun modèle d’erreur dédié pour les cellules.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Vous pouvez implémenter une personnalisation plus poussée en remplaçant <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> le utilisé par la colonne.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Pour valider plusieurs valeurs sur une seule ligne  
  
1. Implémentez <xref:System.Windows.Controls.ValidationRule> une sous-classe qui vérifie plusieurs propriétés de l’objet de données lié. Dans votre <xref:System.Windows.Controls.ValidationRule.Validate%2A> implémentation de méthode, effectuez `value` un cast de la <xref:System.Windows.Data.BindingGroup> valeur de paramètre en une instance. Vous pouvez ensuite accéder à l’objet de données <xref:System.Windows.Data.BindingGroup.Items%2A> via la propriété.  
  
     L’exemple suivant illustre ce processus pour valider si la `StartDate` valeur de propriété d' `Course` un objet est antérieure à `EndDate` sa valeur de propriété.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Ajoutez la règle de validation à <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> la collection. La <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriété fournit un accès direct à <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> la propriété d' <xref:System.Windows.Data.BindingGroup> une instance de qui regroupe toutes les liaisons utilisées par le contrôle.  
  
     L’exemple suivant définit la <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriété en XAML. La <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> propriété a la <xref:System.Windows.Controls.ValidationStep.UpdatedValue> valeur afin que la validation se produise uniquement après la mise à jour de l’objet de données liées.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Lorsqu’un utilisateur spécifie une date de fin antérieure à la date de début, un point d’exclamation rouge (!) apparaît dans l’en-tête de ligne. Vous pouvez modifier ces commentaires de validation par défaut comme décrit dans la procédure suivante.  
  
### <a name="to-customize-row-validation-feedback"></a>Pour personnaliser les commentaires de validation de ligne  
  
- définir la propriété <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> ; Cette propriété vous permet de personnaliser les commentaires de validation de <xref:System.Windows.Controls.DataGrid> ligne pour les contrôles individuels. Vous pouvez également affecter plusieurs contrôles à l’aide d’un style de ligne implicite pour définir la <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> propriété.  
  
     L’exemple suivant remplace les commentaires de validation de ligne par défaut par un indicateur plus visible. Lorsqu’un utilisateur entre une valeur non valide, un cercle rouge avec un point d’exclamation blanc s’affiche dans l’en-tête de ligne. Cela se produit pour les erreurs de validation des lignes et des cellules. Le message d’erreur associé s’affiche dans une info-bulle.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Exemples  
 L’exemple suivant fournit une démonstration complète de la validation de cellule et de ligne. La `Course` classe fournit un exemple <xref:System.ComponentModel.IEditableObject> d’objet de données qui implémente pour prendre en charge les transactions. Le <xref:System.Windows.Controls.DataGrid> contrôle interagit avec <xref:System.ComponentModel.IEditableObject> pour permettre aux utilisateurs de rétablir les modifications en appuyant sur ÉCHAP.  
  
> [!NOTE]
> Si vous utilisez Visual Basic, dans la première ligne de MainWindow. xaml, remplacez `x:Class="DataGridValidation.MainWindow"` par. `x:Class="MainWindow"`  
  
 Pour tester la validation, essayez ce qui suit:  
  
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
- [Liaison de données](../data/data-binding-wpf.md)
- [Implémenter la validation de la liaison](../data/how-to-implement-binding-validation.md)
- [Implémenter une logique de validation sur des objets personnalisés](../data/how-to-implement-validation-logic-on-custom-objects.md)
