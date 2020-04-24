---
title: 'Comment : implémenter la validation avec le contrôle DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 38b4c9cd7679f0d8da9b18fb5bd6bb729d33ed54
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646099"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Comment : implémenter la validation avec le contrôle DataGrid
Le <xref:System.Windows.Controls.DataGrid> contrôle vous permet d’effectuer la validation au niveau de la cellule et de la rangée. Avec validation au niveau cellulaire, vous validez les propriétés individuelles d’un objet de données lié lorsqu’un utilisateur met à jour une valeur. Avec validation au niveau de la ligne, vous validez des objets de données entiers lorsqu’un utilisateur s’engage à modifier une ligne. Vous pouvez également fournir des commentaires visuels personnalisés pour les <xref:System.Windows.Controls.DataGrid> erreurs de validation, ou utiliser la rétroaction visuelle par défaut que le contrôle fournit.  
  
 Les procédures suivantes décrivent comment appliquer <xref:System.Windows.Controls.DataGrid> les règles de validation aux fixations et personnaliser la rétroaction visuelle.  
  
### <a name="to-validate-individual-cell-values"></a>Valider les valeurs cellulaires individuelles  
  
- Spécifier une ou plusieurs règles de validation sur la liaison utilisée avec une colonne. Ceci est similaire à la validation des données dans des contrôles simples, comme décrit dans [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).  
  
     L’exemple suivant <xref:System.Windows.Controls.DataGrid> montre un contrôle avec quatre colonnes liées à différentes propriétés d’un objet d’affaires. Trois des colonnes <xref:System.Windows.Controls.ExceptionValidationRule> spécifient le en fixant la <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriété à `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Lorsqu’un utilisateur entre dans une valeur invalide (comme un non-integer dans la colonne d’identification de cours), une bordure rouge apparaît autour de la cellule. Vous pouvez modifier cette rétroaction de validation par défaut telle que décrite dans la procédure suivante.  
  
### <a name="to-customize-cell-validation-feedback"></a>Personnaliser la rétroaction de validation cellulaire  
  
- Définissez la <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> propriété de la colonne à un style approprié pour le contrôle d’édition de la colonne. Étant donné que les commandes d’édition <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> sont créées au moment de l’exécution, vous ne pouvez pas utiliser la propriété ci-jointe comme vous le feriez avec des contrôles simples.  
  
     L’exemple suivant met à jour l’exemple précédent en ajoutant un style d’erreur partagé par les trois colonnes avec des règles de validation. Lorsqu’un utilisateur entre dans une valeur invalide, le style modifie la couleur de fond de la cellule et ajoute un ToolTip. Notez l’utilisation d’un déclencheur pour déterminer s’il y a une erreur de validation. Cela est nécessaire parce qu’il n’existe actuellement aucun modèle d’erreur dédié pour les cellules.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Vous pouvez implémenter une <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> personnalisation plus étendue en remplaçant l’utilisation par la colonne.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Valider plusieurs valeurs en une seule ligne  
  
1. Implémentez une <xref:System.Windows.Controls.ValidationRule> sous-classe qui vérifie plusieurs propriétés de l’objet de données lié. Dans <xref:System.Windows.Controls.ValidationRule.Validate%2A> votre implémentation de méthode, jetez la valeur de `value` paramètre à une <xref:System.Windows.Data.BindingGroup> instance. Vous pouvez ensuite accéder à <xref:System.Windows.Data.BindingGroup.Items%2A> l’objet de données via la propriété.  
  
     L’exemple suivant démontre ce processus `StartDate` pour valider si la valeur de propriété d’un `Course` objet est antérieure à sa `EndDate` valeur de propriété.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Ajoutez la règle <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> de validation à la collection. La <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriété donne un <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> accès <xref:System.Windows.Data.BindingGroup> direct à la propriété d’une instance qui regroupe toutes les liaisons utilisées par le contrôle.  
  
     L’exemple suivant <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> donne la propriété dans XAML. La <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> propriété est <xref:System.Windows.Controls.ValidationStep.UpdatedValue> définie pour que la validation ne se produise qu’après la mise à jour de l’objet de données lié.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Lorsqu’un utilisateur spécifie une date de fin antérieure à la date de début, un point d’exclamation rouge (!) apparaît dans l’en-tête de la ligne. Vous pouvez modifier cette rétroaction de validation par défaut telle que décrite dans la procédure suivante.  
  
### <a name="to-customize-row-validation-feedback"></a>Personnaliser la rétroaction de validation de ligne  
  
- définir la propriété <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> ; Cette propriété vous permet de personnaliser <xref:System.Windows.Controls.DataGrid> la rétroaction de validation de ligne pour les contrôles individuels. Vous pouvez également affecter plusieurs contrôles en utilisant <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> un style de ligne implicite pour définir la propriété.  
  
     L’exemple suivant remplace la rétroaction de validation de la ligne par défaut par un indicateur plus visible. Lorsqu’un utilisateur entre dans une valeur invalide, un cercle rouge avec un point d’exclamation blanc apparaît dans l’en-tête de la rangée. Cela se produit pour les erreurs de validation de la ligne et des cellules. Le message d’erreur associé s’affiche dans un ToolTip.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant fournit une démonstration complète pour la validation cellulaire et de ligne. La `Course` classe fournit un objet <xref:System.ComponentModel.IEditableObject> de données d’échantillons qui implémente pour soutenir les transactions. Le <xref:System.Windows.Controls.DataGrid> contrôle interagit avec <xref:System.ComponentModel.IEditableObject> pour permettre aux utilisateurs de revenir les changements en appuyant sur ESC.  
  
> [!NOTE]
> Si vous utilisez Visual Basic, dans la première ligne de `x:Class="DataGridValidation.MainWindow"` MainWindow.xaml, remplacez par `x:Class="MainWindow"`.  
  
 Pour tester la validation, essayez ce qui suit :  
  
- Dans la colonne d’identification de cours, entrez une valeur non-integer.  
  
- Dans la colonne Date de fin, entrez une date antérieure à la date de début.  
  
- Supprimer la valeur dans l’ID de cours, la date de début ou la date de fin.  
  
- Pour défaire une valeur cellulaire invalide, remettez le curseur dans la cellule et appuyez sur la clé ESC.  
  
- Pour annuler les modifications pour une ligne entière lorsque la cellule actuelle est en mode d’édition, appuyez deux fois sur la touche ESC.  
  
- Lorsqu’une erreur de validation se produit, déplacez votre pointeur de souris sur l’indicateur dans l’en-tête de la ligne pour voir le message d’erreur associé.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Mettre en œuvre la validation contraignante](../data/how-to-implement-binding-validation.md)
- [Implémenter la logique de validation sur les objets personnalisés](../data/how-to-implement-validation-logic-on-custom-objects.md)
