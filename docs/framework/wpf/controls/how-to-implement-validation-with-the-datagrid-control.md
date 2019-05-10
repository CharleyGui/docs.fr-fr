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
ms.openlocfilehash: 6175e60b1dbdbdb31500f484da24b0f94990b2d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663343"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Procédure : implémenter la validation avec le contrôle DataGrid
Le <xref:System.Windows.Controls.DataGrid> contrôle vous permet d’effectuer la validation au niveau de la cellule et la ligne. La validation au niveau de la cellule vous valider les propriétés individuelles d’un objet de données liées quand un utilisateur met à jour une valeur. La validation au niveau des lignes, vous validez les objets de données entier lorsqu’un utilisateur valide des modifications apportées à une ligne. Vous pouvez également fournir une rétroaction visuelle personnalisée pour les erreurs de validation, ou utiliser la rétroaction visuelle par défaut qui le <xref:System.Windows.Controls.DataGrid> fournit du contrôle.  
  
 Les procédures suivantes décrivent comment appliquer des règles de validation à <xref:System.Windows.Controls.DataGrid> liaisons et personnaliser la rétroaction visuelle.  
  
### <a name="to-validate-individual-cell-values"></a>Pour valider des valeurs de cellules  
  
- Spécifiez une ou plusieurs règles de validation sur la liaison utilisée avec une colonne. Cela revient à la validation des données dans des contrôles simples, comme décrit dans [vue d’ensemble de la liaison de données](../data/data-binding-overview.md).  
  
     L’exemple suivant montre un <xref:System.Windows.Controls.DataGrid> contrôle avec quatre colonnes liées à différentes propriétés d’un objet métier. Trois des colonnes spécifient la <xref:System.Windows.Controls.ExceptionValidationRule> en définissant le <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriété `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Lorsqu’un utilisateur entre une valeur non valide (par exemple, un non entier dans la colonne ID cours), une bordure rouge s’affiche autour de la cellule. Vous pouvez modifier ces commentaires de validation par défaut, comme décrit dans la procédure suivante.  
  
### <a name="to-customize-cell-validation-feedback"></a>Pour personnaliser les commentaires de validation de cellule  
  
- Définir la colonne <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> propriété à un style approprié pour la colonne d’édition du contrôle. Étant donné que les contrôles d’édition sont créés au moment de l’exécution, vous ne pouvez pas utiliser le <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> comme vous le feriez avec des contrôles simples de propriété jointe.  
  
     L’exemple suivant met à jour l’exemple précédent en ajoutant un style d’erreur partagé par les trois colonnes avec des règles de validation. Lorsqu’un utilisateur entre une valeur non valide, le style modifie la couleur d’arrière-plan de cellule et ajoute une info-bulle. Notez l’utilisation d’un déclencheur pour déterminer s’il existe une erreur de validation. Cela est nécessaire, car il n’existe actuellement aucun modèle d’erreur dédié pour les cellules.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Vous pouvez implémenter une personnalisation plus étendue en remplaçant le <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> utilisé par la colonne.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Pour valider les valeurs multiples dans une seule ligne  
  
1. Implémentez un <xref:System.Windows.Controls.ValidationRule> sous-classe qui vérifie plusieurs propriétés de l’objet de données liées. Dans votre <xref:System.Windows.Controls.ValidationRule.Validate%2A> effectuer un cast de l’implémentation de méthode, le `value` valeur de paramètre à un <xref:System.Windows.Data.BindingGroup> instance. Vous pouvez ensuite accéder à l’objet de données via le <xref:System.Windows.Data.BindingGroup.Items%2A> propriété.  
  
     L’exemple suivant montre le processus permettant de valider si la `StartDate` valeur de propriété pour un `Course` objet est antérieur à son `EndDate` valeur de propriété.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Ajouter la règle de validation pour le <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection. Le <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriété offre un accès direct à la <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> propriété d’un <xref:System.Windows.Data.BindingGroup> instance qui regroupe toutes les liaisons utilisées par le contrôle.  
  
     L’exemple suivant définit le <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriété dans XAML. Le <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> propriété est définie sur <xref:System.Windows.Controls.ValidationStep.UpdatedValue> afin que la validation se produit uniquement après que l’objet de données liées est mis à jour.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Lorsqu’un utilisateur spécifie une date de fin est antérieure à la date de début, un point d’exclamation rouge ( !) s’affiche dans l’en-tête de ligne. Vous pouvez modifier ces commentaires de validation par défaut, comme décrit dans la procédure suivante.  
  
### <a name="to-customize-row-validation-feedback"></a>Pour personnaliser les commentaires de validation de ligne  
  
- définir la propriété <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> ; Cette propriété vous permet de personnaliser les commentaires de validation de ligne de chaque <xref:System.Windows.Controls.DataGrid> contrôles. Vous pouvez également affecter plusieurs contrôles en utilisant un style de ligne implicite pour définir le <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> propriété.  
  
     L’exemple suivant remplace les commentaires de validation de ligne par défaut par un indicateur plus visible. Lorsqu’un utilisateur entre une valeur non valide, un cercle rouge avec un point d’exclamation blanc s’affiche dans l’en-tête de ligne. Cela se produit pour les erreurs de validation de ligne et cellule. Le message d’erreur associé s’affiche dans une info-bulle.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant fournit une démonstration complète pour la validation de cellule et de ligne. Le `Course` classe fournit un exemple d’objet de données qui implémente <xref:System.ComponentModel.IEditableObject> pour prendre en charge des transactions. Le <xref:System.Windows.Controls.DataGrid> contrôle interagit avec <xref:System.ComponentModel.IEditableObject> pour permettre aux utilisateurs d’annuler les modifications en appuyant sur ÉCHAP.  
  
> [!NOTE]
>  Si vous utilisez Visual Basic, dans la première ligne de MainWindow.xaml, remplacez `x:Class="DataGridValidation.MainWindow"` avec `x:Class="MainWindow"`.  
  
 Pour tester la validation, essayez ce qui suit :  
  
- Dans la colonne ID du cours, entrez une valeur non entière.  
  
- Dans la colonne de Date de fin, entrez une date antérieure à la Date de début.  
  
- Supprimer la valeur de l’ID du cours, Date de début ou Date de fin.  
  
- Pour annuler une valeur de cellule non valide, placez le curseur dans la cellule, appuyez sur la touche ÉCHAP.  
  
- Pour annuler les modifications pour une ligne entière lorsque la cellule active est en mode édition, appuyez deux fois sur la touche ÉCHAP.  
  
- Lorsqu’une erreur de validation se produit, placez votre pointeur de la souris sur l’indicateur dans l’en-tête de ligne pour afficher le message d’erreur associé.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Liaison de données](../data/data-binding-wpf.md)
- [Implémenter la validation de la liaison](../data/how-to-implement-binding-validation.md)
- [Implémenter une logique de validation sur des objets personnalisés](../data/how-to-implement-validation-logic-on-custom-objects.md)
